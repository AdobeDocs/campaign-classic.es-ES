---
product: campaign
title: Actividad de flujo de trabajo de SMS entrante para infraestructura intermediaria
description: Actividad de flujo de trabajo de SMS entrante para infraestructura intermediaria
feature: Technote, SMS
badge-v7-only: label="v7" type="Informative" tooltip="Se aplica solo a Campaign Classic v7"
source-git-commit: 5667cb6b45742638f8c984d7eb9633660f64fc0f
workflow-type: tm+mt
source-wordcount: '430'
ht-degree: 2%

---

# Actividad de flujo de trabajo de SMS entrante para infraestructura intermediaria {#inbound-sms}

## Limitaciones {#limitations}

* Este caso de uso solo se aplica a la instancia de Marketing en la que recopila datos en SMS de las instancias intermediarias.
* No implemente este caso de uso en la instancia intermediaria.
* Solo un flujo de trabajo personalizado por cuenta intermediaria externa.

## Implementación {#implementation}

1. Añada una extensión a `nms:inSMS` en la instancia de Marketing. La extensión agregará un nuevo atributo a `nms:inSMS` y realizar un seguimiento de la clave principal de registro inSMS proveniente de la instancia intermediaria.

   ```
   <element img="nms:miniatures/mini-sms.png" label="Incoming SMS"
          labelSingular="Incoming SMS" name="inSMS">
   <dbindex name="midInSMSId" unique="false">
     <keyfield xpath="@extAccount-id"/>
     <keyfield xpath="@midInSMSId"/>
   </dbindex>
   
   <attribute label="External Mid SMS ID" name="midInSMSId" type="long"/>
   </element>
   ```

1. Para aplicar las modificaciones realizadas a los esquemas, inicie el asistente de actualización de bases de datos. Se puede acceder a este asistente mediante **Herramientas** > **Avanzadas** > **Actualizar estructura de base de datos**. Comprueba si la estructura física de la base de datos coincide con su descripción lógica y ejecuta los scripts de actualización de SQL. [Más información](../../configuration/using/updating-the-database-structure.md)

1. Detenga y haga una copia de seguridad del flujo de trabajo que contiene **Actividad de SMS entrante**.

   Haga una copia de seguridad del puntero de opción correspondiente con el siguiente formato `SMS_MO_INDEX_{internal name of the workflow}_{name of the insms workflow activity}_{internal name of the external account to access the mid}`.

[Más información sobre la copia de seguridad](../../production/using/backup.md)

1. (**OPCIONAL**) si ya está utilizando una actividad Scheduler, abra el flujo de trabajo y vuelva a configurarlo de la siguiente manera:

   1. Replicar la configuración actual desde el **Programación** pestaña de su **SMS entrantes** actividad en su **Planificador** actividad.

   1. Deshabilite la configuración actual en **Programación** pestaña de **SMS entrantes** actividad.

      ![](assets/inbound_sms_1.png)

1. Actualice el **SMS entrantes** script personalizado.

   Sustituya el bloque siguiente. Tenga en cuenta que esta secuencia de comandos puede variar si anteriormente personalizó este código.

   ```
   var lastSynchKey = getOption('SMS_MO_INDEX_WKF1105_inSmsUS_smsmidus');
   
   var smsId = application.getNewIds(1);
   
   xtk.session.Write(<inSMS xtkschema="nms:inSMS" _operation="insert"
       id={smsId}
       origin={smsMessage.origin}
       message={smsMessage.message}
       providerId={smsMessage.messageId}/>);
   
   return 2;
   ```

   Con el siguiente nuevo script personalizado para actualizar los datos en SMS en función de una clave compuesta, combinando la clave principal del registro intermediario y el ID de cuenta externa del enrutamiento SMS de marketing.
Siga los requisitos previos siguientes:

   * Introduzca el valor real de `<EXTERNAL_ACCOUNT_ID>`, por ejemplo, `var iExtAccountId=72733155`.
   * Asegúrese de mantener los siguientes elementos en el script personalizado:
      * `_operation="insertOrUpdate"`
      * `_key="@midInSMSId,@extAccount-id"`
      * `midInSMSId={smsMessage.id}`
      * `inSms.@["extAccount-id"] = iExtAccountId;{}`

   ```Javascript
   // please enter real external account ID to replace <EXTERNAL ACCOUNT ID>
   var iExtAccountId=<EXTERNAL_ACCOUNT_ID>;
   
   var inSms = <inSMS xtkschema="nms:inSMS" _operation="insertOrUpdate"
   
               _key="@midInSMSId,@extAccount-id"
               midInSMSId={smsMessage.id}
               message={smsMessage.message}
               origin={smsMessage.origin}
               providerId={smsMessage.providerId}
               alias={smsMessage.alias}
               messageDate = {smsMessage.messageDate}
               receivalDate = {smsMessage.receivalDate}
               deliveryDate = {smsMessage.deliveryDate}
               largeAccount = {smsMessage.largeAccount}
               countryCode = {smsMessage.countryCode}
               operatorCode = {smsMessage.operatorCode}
               linkedSmsId={smsMessage.linkedSmsId}
               separator = {smsMessage.separator}/>
   
   inSms.@["extAccount-id"] = iExtAccountId;
   
   xtk.session.Write(inSms);
   
   return 2;
   ```

1. Actualice el script de inicialización avanzado de Inbound SMS con el siguiente script.

   La secuencia de comandos restablecerá el puntero de clave principal a 24 horas antes. El flujo de trabajo intentará volver a procesar todos los datos de inSMS de la instancia de intermediario en las 24 horas anteriores y añadir los datos que falten a la instancia de marketing.

   ```
   // please enter real external account ID to replace <EXTERNAL_ACCOUNT_ID>
   // please enter real pointer option name to replace '<POINTER_OPTION_NAME>'
   // OPTION NAME format: SMS_MO_INDEX_{internal name of the workflow}_inSms_{internal name of the external account to access the mid}
   
   var queryDef = xtk.queryDef.create(
       <queryDef operation="getIfExists" schema="nms:inSMS" lineCount="1">
       <select>
           <node expr="@midInSMSId" alias="@midInSMSId"/>
       </select>
       <where>
           <condition expr="@midInSMSId != 0"/>
           <condition expr={"@created > SubHours(GetDate(), 24)"}/>
           <condition expr={"[@extAccount-id]=<EXTERNAL_ACCOUNT_ID>"}/>
       </where>
       <orderBy>
           <node expr="@midInSMSId"/>
       </orderBy>
       </queryDef>);
   
   var res = parseInt(queryDef.ExecuteQuery().@midInSMSId.toString());
   
   if( !isNaN(res) )
   setOption('<POINTER_OPTION_NAME>', res);
   ```

   >[!WARNING]
   >
   > * Si varias cuentas de enrutamiento SMS están vinculadas a la misma instancia de intermediario, solo se permite un flujo de trabajo único por instancia de intermediario.
   > * Puede utilizar cualquier ID de cuenta externa. La función de la clave externa es mantener la integridad de la reconciliación de datos en escenarios que impliquen distintos servidores intermediarios en los que el ID de SMS intermediario podría ser idéntico en otras instancias intermediarias.
   > * Si hay varios flujos de trabajo de SMS por instancia intermediaria, puede producirse una duplicación de datos, ya que el ID de SMS intermediario permanece constante mientras que los ID de cuenta externa varían.

1. Guarde y reinicie el flujo de trabajo.


