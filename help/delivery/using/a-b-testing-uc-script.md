---
solution: Campaign Classic
product: campaign
title: Creación de la secuencia de comandos
description: Obtenga información sobre cómo realizar pruebas A/B mediante un caso de uso dedicado.
audience: delivery
content-type: reference
topic-tags: a-b-testing
exl-id: 4143d1b7-0e2b-4672-ad57-e4d7f8fea028
translation-type: ht
source-git-commit: 6854d06f8dc445b56ddfde7777f02916a60f2b63
workflow-type: ht
source-wordcount: '335'
ht-degree: 100%

---

# Creación de la secuencia de comandos {#step-5--creating-the-script}

La elección del contenido de entrega destinado a la población restante se calcula mediante una secuencia de comandos. Esta secuencia de comandos recupera la información relativa a la entrega con la mayor tasa de apertura y copia el contenido en la entrega final.

## Ejemplo de secuencia de comandos {#example-of-a-script}

La siguiente secuencia de comandos se puede utilizar como se encuentra en el flujo de trabajo de objetivos. Para obtener más información, consulte [Implementación](#implementation).

```
 // query the database to find the winner (best open rate)
   var winner = xtk.queryDef.create(
     <queryDef schema="nms:delivery" operation="get">
       <select>
         <node expr="@id"/>
         <node expr="@label"/>
         <node expr="[@operation-id]"/>
         <node expr="[@workflow-id]"/>
       </select>
       <where>
         <condition expr={"@FCP=0 and [@workflow-id]= " + instance.id}/>
       </where>
       <orderBy>
         <node expr="[indicators/@estimatedRecipientOpenRatio]" sortDesc="true"/>
       </orderBy>
     </queryDef>).ExecuteQuery()
   
   // create a new delivery object and initialize it by doing a copy of
   // the winner delivery
   var delivery = nms.delivery.create()
   delivery.Duplicate("nms:delivery|" + winner.@id)

   // append 'final' to the delivery label
   delivery.label = winner.@label + " final"

   // link the delivery to the operation to make sure it will be displayed in
   // the campaign dashboard. This attribute needs to be set manually here since 
   // the Duplicate() method has reset it to its default value => 0
   delivery.operation_id = winner.@["operation-id"]
   delivery.workflow_id = winner.@["workflow-id"]

   // adjust some delivery parameters to make it compatible with the 
   // "Prepare and start" option selected in the Delivery tab of this activity
   delivery.scheduling.validationMode = "manual"
   delivery.scheduling.delayed = 0
 
   // save the delivery in database
   delivery.save()
 
   // store the new delivery Id in event variables
   vars.deliveryId = delivery.id
```

Para obtener una explicación detallada del script, consulte [Detalles del script](#details-of-the-script).

## Implementación {#implementation}

1. Abra la actividad **[!UICONTROL JavaScript code]**.
1. Copie la secuencia de comandos ofrecida en [Ejemplo de secuencia de comandos](#example-of-a-script) en la ventana **[!UICONTROL JavaScript code]**.

   ![](assets/use_case_abtesting_configscript_002.png)

1. En el campo **[!UICONTROL Label]**, introduzca el nombre de la secuencia de comandos, por ejemplo.

   ```
   <%= vars.deliveryId %>
   ```

   ![](assets/use_case_abtesting_configscript_003.png)

1. Cierre la actividad **[!UICONTROL JavaScript code]**.
1. Guarde el flujo de trabajo.

## Detalles de la secuencia de comandos {#details-of-the-script}

En esta sección se detallan las distintas partes de la secuencia de comandos y su modo operativo.

* La primera parte de la secuencia de comandos es una consulta. El comando **queryDef** permite recuperar desde la tabla **NmsDelivery** los envíos creados ejecutando el flujo de trabajo objetivo y ordenarlos en función de su tasa estimada de apertura. A continuación, se recupera la información de la entrega con la mayor tasa de apertura.

   ```
   // query the database to find the winner (best open rate)
      var winner = xtk.queryDef.create(
        <queryDef schema="nms:delivery" operation="get">
          <select>
            <node expr="@id"/>
            <node expr="@label"/>
            <node expr="[@operation-id]"/>
          </select>
          <where>
            <condition expr={"@FCP=0 and [@workflow-id]= " + instance.id}/>
          </where>
          <orderBy>
            <node expr="[indicators/@estimatedRecipientOpenRatio]" sortDesc="true"/>
          </orderBy>
        </queryDef>).ExecuteQuery()
   ```

* Se duplica la entrega con la mayor tasa de apertura.

   ```
    // create a new delivery object and initialize it by doing a copy of
    // the winner delivery
   var delivery = nms.delivery.create()
   delivery.Duplicate("nms:delivery|" + winner.@id)
   ```

* La etiqueta de la entrega duplicado se modifica y la palabra **final** se añade a ella.

   ```
   // append 'final' to the delivery label
   delivery.label = winner.@label + " final"
   ```

* La entrega se copia en el tablero de campañas.

   ```
   // link the delivery to the operation to make sure it will be displayed in
   // the campaign dashboard. This attribute needs to be set manually here since 
   // the Duplicate() method has reset it to its default value => 0
   delivery.operation_id = winner.@["operation-id"]
   delivery.workflow_id = winner.@["workflow-id"]
   ```

   ```
   // adjust some delivery parameters to make it compatible with the 
   // "Prepare and start" option selected in the Delivery tab of this activity
   delivery.scheduling.validationMode = "manual"
   delivery.scheduling.delayed = 0
   ```

* La entrega se guarda en la base de datos.

   ```
   // save the delivery in database
   delivery.save()
   ```

* El identificador único de la entrega duplicado se almacena en la variable del flujo de trabajo.

   ```
   // store the new delivery Id in event variables
   vars.deliveryId = delivery.id
   ```

## Otros criterios de selección {#other-selection-criteria}

El ejemplo de arriba permite seleccionar el contenido de una entrega según la tasa de apertura de los correos electrónicos. Se puede adaptar para que poder basarse en otros indicadores específicos de entrega:

* Mejor rendimiento de los clics: `[indicators/@recipientClickRatio]`,
* Tasa máxima de reacción (correo electrónico abierto y clics en el mensaje): `[indicators/@reactivity]`,
* Tasa de quejas más baja: `[indicators/@refusedRatio]` (utilice el valor falso para el atributo sortDesc),
* Tasa máxima de conversión: `[indicators/@transactionRatio]`,
* Número de páginas visitadas después de la recepción de un mensaje: `[indicators/@totalWebPage]`,
* Tasa mínima de cancelación de suscripciones: `[indicators/@optOutRatio]`,
* Cantidad de transacciones: `[indicators/@amount]`.

Ahora puede definir el envío final (consulte [Paso 6: Defina el envío final](../../delivery/using/a-b-testing-uc-final-delivery.md)).
