---
solution: Campaign Classic
product: campaign
title: ' Configuración general'
description: ' Configuración general'
audience: migration
content-type: reference
topic-tags: configuration
exl-id: 7aad0e49-8d9c-40c7-9d6a-42fee0ae5870
translation-type: tm+mt
source-git-commit: b0a1e0596e985998f1a1d02236f9359d0482624f
workflow-type: tm+mt
source-wordcount: '2786'
ht-degree: 0%

---

#  Configuración general{#general-configurations}

Esta sección detalla la configuración que se realizará en Adobe Campaign v7 si va a migrar desde una versión 5.11 o 6.02.

Además:

* Si migra desde la versión 5.11, también debe completar la configuración detallada en la sección [Configuraciones específicas en la sección v5.11](../../migration/using/specific-configurations-in-v5-11.md).
* Si migra desde la versión 6.02, también debe completar la configuración detallada en la sección [Configuraciones específicas en la sección v6.02](../../migration/using/specific-configurations-in-v6-02.md).

## Zonas horarias {#time-zones}

### Modo de zona horaria múltiple {#multi-time-zone-mode}

En la versión 6.02, el modo &quot;zona horaria múltiple&quot; solo estaba disponible para los motores de base de datos PostgreSQL. Ahora se ofrece independientemente del tipo de motor de base de datos que se utilice. Le recomendamos encarecidamente que transforme su base en una base de &quot;zona horaria múltiple&quot;.

Para utilizar el modo TIMESTAMP WITH TIMEZONE, también debe añadir la opción **-userTimestamptz:1** a la línea de comandos posterior a la actualización.

>[!IMPORTANT]
>
>Si el parámetro **-usetimestamptz:1** se utiliza con un motor de base de datos incompatible, la base de datos estará dañada y tendrá que restaurar una copia de seguridad de la base de datos y volver a ejecutar el comando anterior.

>[!NOTE]
>
>Es posible modificar la zona horaria después de la migración a través de la consola (nodo **[!UICONTROL Administration > Platform > Options > WdbcTimeZone]**).
>
>Para obtener más información sobre la administración de huso horario, consulte [esta sección](../../installation/using/time-zone-management.md).

### Oracle {#oracle}

Si recibe un error **ORA 01805** durante la actualización, significa que los archivos de zona horaria de Oracle entre el servidor de aplicaciones y el servidor de base de datos no están sincronizados. Para volver a sincronizarlos, siga los siguientes pasos:

1. Para identificar el archivo de zona horaria utilizado, ejecute el siguiente comando:

   ```
   select * from v$timezone_file
   ```

   Los archivos de zona horaria generalmente se encuentran en la carpeta **ORACLE_HOME/oracore/zoneinfo/**.

1. Asegúrese de que los archivos de zona horaria sean idénticos en ambos servidores.

Para obtener más información, visite: [https://docs.oracle.com/cd/E11882_01/server.112/e10729/ch4datetime.htm#NLSPG004](https://docs.oracle.com/cd/E11882_01/server.112/e10729/ch4datetime.htm#NLSPG004).

Un desajuste de zona horaria entre cliente y servidor también puede causar algunos desfases. Por este motivo, recomendamos utilizar la misma versión de la biblioteca de Oracle en el lado del cliente y del servidor, ya que ambas zonas horarias deben ser las mismas.

Para comprobar si ambos lados están en las mismas zonas horarias:

1. Compruebe la versión del archivo de zona horaria en el lado del cliente ejecutando el siguiente comando:

   ```
   genezi -v
   ```

   genezi es un binario que se encuentra en el repositorio **$ORACLE_HOME/bin**.

1. Compruebe la versión del archivo de zona horaria en el servidor ejecutando el siguiente comando:

   ```
   select * from v$timezone_file
   ```

1. Para cambiar el archivo de zona horaria en el lado del cliente, utilice la variable de entorno **ORA_TZFILE**.

## Seguridad {#security}

### Zonas de seguridad {#security-zones}

>[!IMPORTANT]
>
>Por motivos de seguridad, ya no se puede acceder a la plataforma Adobe Campaign de forma predeterminada: debe configurar las zonas de seguridad y, por lo tanto, recopilar las direcciones IP del operador.

Adobe Campaign v7 incluye el concepto de **zonas de seguridad**. Cada usuario debe estar asociado a una zona para iniciar sesión en una instancia y la dirección IP del usuario debe incluirse en las direcciones o intervalos de direcciones definidos en la zona de seguridad. La configuración de las zonas de seguridad se puede realizar en el archivo de configuración del servidor de Adobe Campaign. La zona de seguridad a la que está asociado un usuario debe definirse en la consola (**[!UICONTROL Administration > Access management > Operators]**).

**Antes de la migración**, pida al administrador de la red que le ayude a definir las zonas de seguridad que se activarán después de la migración.

**Después de la actualización posterior**  (antes del reinicio del servidor), debe configurar las zonas de seguridad.

La configuración de la zona de seguridad se encuentra en [esta sección](../../installation/using/security-zones.md).

### Contraseñas de usuario {#user-passwords}

En la versión 7, la conexión del operador **internal** y **admin** debe estar segura mediante una contraseña. Se recomienda encarecidamente asignar contraseñas a estas cuentas y todas las cuentas de operador, **antes de la migración**. Si no ha especificado una contraseña para **internal**, no podrá conectarse. Para asignar una contraseña a **internal**, introduzca el siguiente comando:

```
nlserver config -internalpassword
```

>[!IMPORTANT]
>
>La contraseña **internal** debe ser idéntica para todos los servidores de seguimiento. Para obtener más información, consulte [esta sección](../../installation/using/configuring-campaign-server.md#internal-identifier) y [esta sección](../../platform/using/access-management.md).

### Nuevas funciones de la versión 7 {#new-features-in-v7}

* Los usuarios sin permisos ya no pueden conectarse a Adobe Campaign. Sus permisos deben agregarse manualmente, por ejemplo, creando un permiso llamado **connect**.

   Los usuarios afectados por esta modificación se identifican y se enumeran durante la actualización posterior.

* El seguimiento ya no funciona si la contraseña está vacía. Si este es el caso, un mensaje de error le informará y le pedirá que lo reconfigure.
* Las contraseñas de usuario ya no se almacenan en el esquema **xtk:sessionInfo** .
* Los permisos de administración ahora son necesarios para utilizar las funciones **xtk:builder:EvaluateJavaScript** y **xtk:builder:EvaluateJavaScriptTemplate**.

Algunos esquemas predeterminados se han modificado y ahora solo se puede acceder de forma predeterminada con acceso de escritura para los operadores con el permiso **admin**:

* ncm:publishing
* nl:monitorización
* nms:calendar
* xtk:builder
* xtk:conexiones
* xtk:dbInit
* xtk:entityBackupNew
* xtk:entityBackupOriginal
* xtk:entityOriginal
* xtk:form
* xtk:funcList
* xtk:fusión
* xtk:image
* xtk:javascript
* xtk:jssp
* xtk:jst
* xtk:navtree
* xtk:operatorGroup
* xtk:package
* xtk:queryDef
* xtk:resourceMenu
* xtk:rights
* xtk:schema
* xtk:scriptContext
* xtk:specFile
* xtk:sql
* xtk:sqlSchema
* xtk:srcSchema
* xtk:strings
* xtk:xslt

### Parámetro Sessiontoken {#sessiontoken-parameter}

En la versión 5, el parámetro **sessiontoken** funcionaba en ambos lados del cliente (lista de pantallas de tipo de visión general, editor de vínculos, etc.) y del lado del servidor (aplicaciones web, informes, jsp, jssp, etc.). En la versión 7, solo funciona en el servidor. Si desea volver a la funcionalidad completa como en la versión 5, debe modificar los vínculos con este parámetro y pasar a través de la página de conexión:

Ejemplo de vínculo:

```
/view/recipientOverview?__sessiontoken=<trusted login>
```

Nuevo vínculo mediante la página de conexión:

```
/nl/jsp/logon.jsp?login=<trusted login>&action=submit&target=/view/recipientOverview
```

>[!IMPORTANT]
>
>Si utiliza un operador vinculado con una máscara IP de confianza, compruebe que tenga los derechos mínimos y que esté en una zona de seguridad en modo **sessionTokenOnly**.

### Funciones SQL {#sql-functions}

Las llamadas a funciones SQL desconocidas ya no se envían de forma natural al servidor. Actualmente, todas las funciones SQL deben agregarse al esquema **xtk:funcList** (para más información, consulte [esta sección](../../configuration/using/adding-additional-sql-functions.md)). Al migrar, se añade una opción durante la posactualización que permite mantener la compatibilidad con las antiguas funciones SQL no declaradas. Si desea seguir utilizando estas funciones, compruebe que la opción **XtkPassUnknownSQLFunctionsToRDBMS** esté definida en el nivel de nodo **[!UICONTROL Administration > Platform > Options]**.

>[!IMPORTANT]
>
>Recomendamos encarecidamente no utilizar esta opción debido a los riesgos de seguridad que introduce.

### JSSP {#jssp}

Si desea autorizar el acceso a ciertas páginas a través del protocolo HTTP (no HTTPS), en las aplicaciones web por ejemplo, independientemente de la configuración realizada en las zonas de seguridad, debe especificar el parámetro **httpAllowed=&quot;true&quot;** en la regla de retransmisión correspondiente.

Si utiliza JSSP anónimos, debe añadir el parámetro **httpAllowed=&quot;true&quot;** en una regla de retransmisión para su JSSP (archivo **[!UICONTROL serverConf.xml]**):

Por ejemplo:

```
<url IPMask="" deny="" hostMask="" httpAllowed="true" relayHost="true" relayPath="true"
           status="blacklist" targetUrl="https://localhost:8080" timeout="" urlPath="*/cus/myPublicPage.jssp"/>
```

## Sintaxis {#syntax}

### JavaScript {#javascript}

Adobe Campaign v7 integra un intérprete de JavaScript más reciente. Sin embargo, esta actualización puede provocar el fallo de ciertas secuencias de comandos. Como el motor anterior era más permisivo, ciertas sintaxis funcionarían, lo que ya no es el caso de la nueva versión del motor.

La sintaxis **[!UICONTROL myObject.@attribute]** ahora solo es válida para objetos XML. Esta sintaxis se puede utilizar para personalizar envíos y la administración de contenido. Si ha utilizado este tipo de sintaxis en un objeto no XML, las funciones de personalización dejarán de funcionar.

Para el resto de tipos de objetos, la sintaxis es ahora **[!UICONTROL myObject`[`&quot;attribute&quot;`]`]**. Por ejemplo, un objeto no XML que utilice la siguiente sintaxis: **[!UICONTROL employee.@sn]**, ahora debe utilizar la siguiente sintaxis: **[!UICONTROL employee`[`&quot;sn&quot;`]`]**.

* Sintaxis anterior:

   ```
   employee.@sn
   ```

* Nueva sintaxis:

   ```
   employee["sn"]
   ```

Para cambiar un valor en un objeto XML, ahora es necesario empezar por actualizar el valor antes de añadir el nodo XML:

* Código JavaScript antiguo:

   ```
   var cellStyle = node.style.copy();
   this.styles.appendChild(cellStyle);
   cellStyle.@width = column.@width;
   ```

* Nuevo código JavaScript:

   ```
   var cellStyle = node.style.copy();
   cellStyle.@width = column.@width;
   this.styles.appendChild(cellStyle);
   ```

Ya no se puede utilizar un atributo XML como clave de tabla.

* Sintaxis anterior:

   ```
   if(serverForm.activities[ctx.activityHistory.activity[0].@name].type !="end")
   ```

* Nueva sintaxis:

   ```
   if(serverForm.activities[String(ctx.activityHistory.activity[0].@name)].type !="end"
   ```

### SQLData {#sqldata}

Para reforzar la seguridad de las instancias, se ha introducido una nueva sintaxis en Adobe Campaign v7 para reemplazar la sintaxis basada en SQLData. Si utiliza estos elementos de código con esta sintaxis, debe modificarlos. Los principales elementos son:

* Filtrado por subconsulta: la nueva sintaxis se basa en el elemento `<subQuery>` para definir una subconsulta
* Agregados: la nueva sintaxis es &quot;aggregate function(collection)&quot;
* Filtrado por unión: la nueva sintaxis es `[schemaName:alias:xPath]`

Se ha modificado el esquema queryDef (xtk:queryDef) :

* hay un nuevo elemento `<subQuery>` disponible para reemplazar el SELECT incluido en SQLData
* se han introducido dos nuevos valores, &quot;IN&quot; y &quot;NOT IN&quot; para el atributo @setOperator
* un nuevo elemento `<where>`, que es un elemento secundario del elemento `<node>`: esto le permite realizar &quot;subselecciones&quot; en SELECT

Cuando se utiliza un atributo &quot;@expr&quot;, es posible que SQLData esté presente. Se puede buscar los términos siguientes: &quot;SQLData&quot;, &quot;aliasSqlTable&quot;, &quot;sql&quot;.

Las instancias de Adobe Campaign v7 están seguras de forma predeterminada. La seguridad viene en términos de definiciones de zonas de seguridad en el archivo **[!UICONTROL serverConf.xml]**: el atributo **allowSQLInjection** administra la seguridad de la sintaxis SQL.

Si se produce un error de SQLData durante la ejecución posterior a la actualización, debe modificar este atributo para permitir temporalmente el uso de sintaxis basadas en SQLData, lo que le permite reescribir el código. Para ello, se debe cambiar la siguiente opción en el archivo **serverConf.xml**:

```
allowSQLInjection="true"
```

Por lo tanto, reinicie el postupgrade con el siguiente comando:

```
nlserver config -postupgrade -instance:<instance_name> -force
```

Debe configurar las zonas de seguridad (consulte [Seguridad](#security)) y reactivar la seguridad cambiando la opción:

```
allowSQLInjection="false"
```

A continuación encontrará ejemplos comparativos entre la sintaxis antigua y la nueva.

**Filtrado por subconsultas**

* Sintaxis anterior:

   ```
   <condition expr="@id NOT IN ([SQLDATA[SELECT iOperatorId FROM XtkOperatorGroup WHERE iGroupId = $(../@owner-id)]])" enabledIf="$(/ignored/@ownerType)=1"/>
   ```

* Nueva sintaxis:

   ```
   <condition setOperator="NOT IN" expr="@id" enabledIf="$(/ignored/@ownerType)=1">
     <subQuery schema="xtk:operatorGroup">
        <select>
          <node expr="[@operator-id]" />
        </select>
        <where>
          <condition expr="[@group-id]=$long(../@owner-id)"/>
        </where>
      </subQuery>
   </condition>
   ```

* Sintaxis anterior:

   ```
   <queryFilter name="dupEmail" label="Emails duplicated in the folder" schema="nms:recipient">
       <where>
         <condition sql="sEmail in (select sEmail from nmsRecipient where iFolderId=$(folderId) group by sEmail having count(sEmail)>1)" internalId="1"/>
       </where>
       <folder _operation="none" name="nmsSegment"/>
     </queryFilter>
   ```

* Nueva sintaxis:

   ```
   <queryFilter name="dupEmail" label=" Emails duplicated in the folder " schema="nms:recipient">
       <where>
         <condition expr="@email" setOperator="IN" internalId="1">
           <subQuery schema="nms:recipient">
             <select><node expr="@email"/></select>
             <where><condition expr="[@folder-id]=$(folderId)"/></where>
             <groupBy><node expr="@email"/></groupBy>
             <having><condition expr="count(@email)>1"/></having>
           </subQuery>
         </condition>
       </where>
       <folder _operation="none" name="nmsSegment"/>
     </queryFilter>
   ```

**El agregado**

Aggregate function(collection)

* Sintaxis anterior:

   ```
   <node sql="(select count(*) from NmsNewsgroup WHERE O0.iOperationId=iOperationId)" alias="@nbMessages"/>
   ```

* Nueva sintaxis:

   ```
   <node expr="count([newsgroup/@id])" alias="../@nbMessages"/>
   ```

   >[!NOTE]
   >
   >Los enlaces se realizan automáticamente para las funciones de agregado. Ya no es necesario especificar la condición WHERE O0.iOperationId=iOperationId.
   >
   >Ya no es posible utilizar la función &quot;count(*)&quot;. Debe utilizar &quot;counheight()&quot;.

* Sintaxis anterior:

   ```
   <node sql="(select Sum(iToDeliver) from NmsDelivery WHERE O0.iOperationId=iOperationId AND iSandboxMode=0 AND iState>=45)" alias="@nbMessages"/>
   ```

* Nueva sintaxis:

   ```
   <node expr="Sum([delivery-linkedDelivery/properties/@toDeliver])" alias= "../@sumToDeliver">
                     <where><condition expr="[validation/@sandboxMode]=0 AND @state>=45" /></where></node>
   ```

**Filtros por uniones**

`[schemaName:alias:xPath]`

El alias es opcional

* Sintaxis anterior:

   ```
   <condition expr={"[" + joinPart.destination.nodePath + "] = [SQLDATA[W." + joinPart.source.SQLName + "]]"}
                                            aliasSqlTable={nodeSchemaRoot.SQLTable + " W"}/>
   ```

* Nueva sintaxis:

   ```
   <condition expr={"[" + joinPart.destination.nodePath + "] = [" + nodeSchema.id + ":" + joinPart.source.nodePath + "]]"}/>
   ```

**Sugerencias y trucos**

En un elemento `<subQuery>`, para hacer referencia a un campo &quot;field&quot; del `<queryDef>` principal   utilice la siguiente sintaxis: `[../@field]`

Ejemplo:

```
<queryDef operation="select" schema="xtk:jobLog" startPath="/" xtkschema="xtk:queryDef">
  <select>
    <node expr="[job/@pid]" alias="@pid"/>
    <node expr="@id" ordered="true"/>
    <node expr="@logType"/>
  </select>
  <where>
    <condition expr="[@job-id]=99"/>
    <condition expr="@logType" setOperator="IN">
      <subQuery schema="xtk:jobLog">
        <select><node expr="@logType"/></select>
        <where><condition expr="[@job-id]=[../job/@id]"/></where>
        <groupBy><node expr="@logType"/></groupBy>
        <having><condition expr="count(@logType)>1"/></having>
      </subQuery>
    </condition>
  </where>
</queryDef>
```

## Conflictos {#conflicts}

La migración se realiza a través de una actualización posterior y es posible que los conflictos aparezcan en informes, formularios o aplicaciones web. Estos conflictos se pueden resolver desde la consola.

Después de la sincronización de recursos, el comando **postupgrade** permite detectar si la sincronización genera errores o advertencias.

### Ver el resultado de la sincronización {#view-the-synchronization-result}

El resultado de la sincronización se puede ver de dos maneras:

* En la interfaz de la línea de comandos, los errores se materializan mediante una triple cadena **>>** y la sincronización se detiene automáticamente. Las advertencias se materializan mediante una cadena **>** doble y deben resolverse una vez finalizada la sincronización. Al final de la actualización posterior, se muestra un resumen en el símbolo del sistema. Por ejemplo:

   ```
   2013-04-09 07:48:39.749Z        00002E7A          1     info    log     =========Summary of the update==========
   2013-04-09 07:48:39.749Z        00002E7A          1     info    log     test instance, 6 warning(s) and 0 error(s) during the update.
   2013-04-09 07:48:39.749Z        00002E7A          1     warning log     The document with identifier 'mobileAppDeliveryFeedback' and type 'xtk:report' is in conflict with the new version.
   2013-04-09 07:48:39.749Z        00002E7A          1     warning log     The document with identifier 'opensByUserAgent' and type 'xtk:report' is in conflict with the new version.
   2013-04-09 07:48:39.750Z        00002E7A          1     warning log     The document with identifier 'deliveryValidation' and type 'nms:webApp' is in conflict with the new version.
   2013-04-09 07:48:39.750Z        00002E7A          1     warning log     Document of identifier 'nms:includeView' and type 'xtk:srcSchema' updated in the database and found in the file system. You will have to merge the two versions manually.
   ```

   Si la advertencia se refiere a un conflicto de recursos, es necesario que el operador preste atención para resolverlo.

* El archivo **postupgrade_`<server version number>`_time de postupgrade`>`.log** contiene el resultado de la sincronización. Está disponible de forma predeterminada en el siguiente directorio: **directorio de instalación/var/`<instance>`postupgrade**. Los errores y advertencias se indican mediante los atributos **error** y **warning**.

### Resolver un conflicto {#resolve-a-conflict}

La resolución de conflictos solo debe realizarlos operadores avanzados y los que tienen derechos de &quot;administrador&quot;.

Para resolver un conflicto, siga el siguiente proceso:

1. En la estructura de árbol de Adobe Campaign, coloque el cursor sobre **[!UICONTROL Administration > Configuration > Package management > Edit conflicts]**.
1. Seleccione el conflicto que desee resolver en la lista.

Hay tres maneras posibles de resolver un conflicto:

* **[!UICONTROL Declared as resolved]**: requiere la intervención previa del operador.
* **[!UICONTROL Accept the new version]**: recomendado si el usuario no ha cambiado los recursos proporcionados con Adobe Campaign.
* **[!UICONTROL Keep the current version]**: significa que la actualización se rechaza.

   >[!IMPORTANT]
   Si selecciona este modo de resolución, corre el riesgo de perder parches en la nueva versión. Por lo tanto, se recomienda encarecidamente que esta opción no se utilice o se reserve solo para operadores expertos.

Si decide resolver manualmente el conflicto, proceda de la siguiente manera:

1. En la sección inferior de la ventana, busque **`_conflict_ string`** para localizar las entidades con conflictos. La entidad instalada con la nueva versión contiene el argumento **new**, la entidad que coincide con la versión anterior contiene el argumento **cus**.

   ![](assets/s_ncs_production_conflict002.png)

1. Elimine la versión que no desee conservar. Elimine el **`_conflict_argument_ string`** de la entidad que mantiene.

   ![](assets/s_ncs_production_conflict003.png)

1. Vaya al conflicto que habría resuelto. Haga clic en el icono **[!UICONTROL Actions]** y seleccione **[!UICONTROL Declare as resolved]**.
1. Guarde los cambios: el conflicto ya está resuelto.

## Tomcat {#tomcat}

El servidor Tomcat integrado en Adobe Campaign v7 ha cambiado la versión. Por lo tanto, su carpeta de instalación (tomcat-6) también ha cambiado (tomcat 7). Después de la actualización, asegúrese de comprobar que las rutas sí se vinculan a la carpeta actualizada (en el archivo **[!UICONTROL serverConf.xml]**):

```
$(XTK_INSTALL_DIR)/tomcat-8/bin/bootstrap.jar 
$(XTK_INSTALL_DIR)/tomcat-8/bin/tomcat-juli.jar
$(XTK_INSTALL_DIR)/tomcat-8/lib/tomcat-util.jar
$(XTK_INSTALL_DIR)/tomcat-8/lib/tomcat-api.jar
$(XTK_INSTALL_DIR)/tomcat-8/lib/servlet-api.jar
$(XTK_INSTALL_DIR)/tomcat-8/lib/jsp-api.jar
$(XTK_INSTALL_DIR)/tomcat-8/lib/el-api.jar
```

## Interacción {#interaction}

### Requisitos previos {#prerequisites}

**Antes de la actualización** posterior, debe eliminar todas las referencias de esquema de la versión 6.02 que ya no existan en la versión 7.

* nms:emailOfferView
* nms:webOfferView
* nms:callCenterOfferView
* nms:mobileOfferView
* nms:paperOfferView

### Contenido de la oferta {#offer-content}

En la versión 7, el contenido de la oferta se ha movido. En la versión 6.02, el contenido estaba en cada esquema de representación (**nms:emailOfferView**). En la versión 7, el contenido ahora está en el esquema de oferta. Después de la actualización, el contenido no será visible en la interfaz. Después de la actualización, debe volver a crear el contenido de la oferta o desarrollar una secuencia de comandos que mueva automáticamente el contenido del esquema de representación al esquema de oferta.

>[!IMPORTANT]
Si algunas entregas que utilizan ofertas configuradas se enviaran después de la migración, debe eliminar y volver a crear todas estas entregas en v7. Si no puede hacerlo, se ofrece un &quot;modo de compatibilidad&quot;. No se recomienda este modo porque no se beneficiará de todas las nuevas funciones de Interaction v7. Este es un modo de transición que le permite completar las campañas en curso antes de la migración real a la versión 6.1. Para obtener más información sobre este modo, póngase en contacto con nosotros.

Hay disponible un ejemplo de secuencia de comandos de movimiento (**interactionTo610_full_XX.js**) en la carpeta **Migration** de la carpeta Adobe Campaign v7. Este archivo muestra un ejemplo de una secuencia de comandos para un cliente que utiliza una sola representación de correo electrónico por oferta (los campos **[!UICONTROL htmlSource]** y **[!UICONTROL textSource]** ). El contenido que estaba en la tabla **NmsEmailOfferView** se ha movido a la tabla de ofertas.

>[!NOTE]
El uso de esta secuencia de comandos no permite beneficiarse de las opciones &quot;gestión de contenido&quot; y &quot;funciones de renderización&quot;. Para beneficiarse de estas funciones, debe reconsiderar las ofertas del catálogo, especialmente el contenido de las ofertas y los espacios de configuración.

```
loadLibrary("/nl/core/shared/nl.js");

NL.require("/nl/core/shared/xtk.js");

// 1. Restore old emailOfferView schema
logInfo("Restoring old emailOfferView schema");
var oldOfferViewSchemas = <entities schema="xtk:srcSchema"/>;

oldOfferViewSchemas.appendChild(
  <srcSchema img="nms:offerView.png"
             label="Email offer representations"
             labelSingular="Email offer representation"
             name="emailOfferView" namespace="nlmig"
             genAccessors="false" implements="xtk:persist">
    <element name="emailOfferView" template="nms:offerView" sqltable="NmsEmailOfferView">
      <element name="offer" revLabel="Email representation" revIntegrity="owncopy"/>
      <element   name="htmlSource"      type="html" label="HTML content"  xml="true"/>
      <element   name="textSource"      type="CDATA" label="Text content" xml="true"/>
      <element   name="htmlSource_jst"  type="CDATA" label="HTML script"  desc="HTML content calculation script."  xml="true" advanced="true"/>
      <element   name="textSource_jst"  type="CDATA" label="Text script" desc="Text content calculation script." xml="true" advanced="true"/>
    </element>
  </srcSchema>);

var oldOfferViewsPkg = <builder><package buildNumber="*">{oldOfferViewSchemas}</package></builder>;
xtk.builder.InstallPackage(oldOfferViewsPkg);

// 2. Migrate data from old emailOfferView table to nms:offer
logInfo("Moving data from old EmailOfferView table to NmsOffer");
var OFFER_STATUS_VALIDATED = 3;

var queryDef = xtk.queryDef.create(
  <queryDef operation="select" schema="nlmig:emailOfferView">
    <select>
      <node expr="[@offer-id]"/>
      <node expr="[@space-id]"/>
      <node expr="htmlSource_jst"/>
      <node expr="textSource_jst"/>
    </select>
  </queryDef>);
var res = queryDef.ExecuteQuery();

var processedOffers = {};
for each( var emailOfferView in res.emailOfferView )
{
  if( processedOffers[String(emailOfferView.@["offer-id"])] != undefined )
  {
    logWarning("Found 2 or more eff fffffmail representations for offer " + String(emailOfferView.@["offer-id"]) + ". Only keep the first one here.");
    continue;
  }
  xtk.session.Write(
    <offer id={emailOfferView.@["offer-id"]} status={OFFER_STATUS_VALIDATED} xtkschema="nms:offer">
      <view>
        {emailOfferView.mdSource_jst}
        {emailOfferView.textSource_jst}
      </view>
    </offer>
  );
  processedOffers[String(emailOfferView.@["offer-id"])] = 1;
}

// 3. Get rid of emailOfferView schema now that data has been moved.
logInfo("Deleting EmailOfferView schema");
xtk.session.Write(<srcSchema xtkschema="xtk:srcSchema" name="emailOfferView" namespace="nlmig" _operation="delete"/>);

logInfo("Done");
```

### Pruebas y configuración {#tests-and-configuration}

Este es el procedimiento a seguir después de haber movido el contenido de la oferta si solo tiene un entorno. En este caso tomemos como ejemplo &quot;ENV&quot;.

1. En todos los espacios de oferta de entorno &quot;ENV&quot;, actualice la lista de campos utilizados. Por ejemplo, para un espacio de oferta que solo utilice el **[!UICONTROL htmlSource]**, debe agregar el **[!UICONTROL view/htmlSource]**.

   ![](assets/migration_interaction_2.png)

1. En el campo **[!UICONTROL Type of Environment]** dentro de la pestaña **[!UICONTROL General]**, seleccione **[!UICONTROL Live]**.

   ![](assets/migration_interaction_3.png)

1. Cree un entorno de diseño (&quot;ENV_DESIGN&quot;, por ejemplo) y conéctelo al entorno en línea ENV.

   ![](assets/migration_interaction_4.png)

1. Implemente todos los espacios de oferta de entorno &quot;ENV&quot; (haga clic con el botón derecho > **[!UICONTROL Actions > Deploy]**) y seleccione el entorno &quot;ENV_DESIGN&quot;.

   ![](assets/migration_interaction_5.png)

1. Haga lo mismo con todas las ofertas de entorno &quot;ENV&quot;.
1. Active todas las ofertas de entorno &quot;ENV_DESIGN&quot; en los canales relevantes.
1. Pruebe a poner en marcha una oferta. Si no encuentra ningún problema, ejecute las tareas pendientes en la última tarea de flujo de trabajo **[!UICONTROL Offer notification]** (offerMgt) para que todas las ofertas se activen.

   ![](assets/migration_interaction_6.png)

1. Realice pruebas exhaustivas.

   >[!NOTE]
   Los nombres de las categorías y ofertas en línea se modifican después de activarse. En el canal entrante, actualice todas las referencias a ofertas y categorías.

## Informes {#reports}

### Informes estándar {#standard-reports}

Todos los informes estándar utilizan actualmente el motor de renderización v6.x. Si ha añadido JavaScript a estos informes, es posible que algunos elementos ya no funcionen. De hecho, la versión antigua de JavaScript no es compatible con el motor de renderización v6.x. Por lo tanto, debe comprobar el código JavaScript y adaptarlo más adelante. Debe probar cada informe, especialmente la función de exportación.

### Informes personalizados {#personalized-reports}

<!--If you want to have the blue banner from v7 (allowing you access to the tabs), you must republish reports. If you encounter problems, you can force the v6.0 rendering engine. To do this, go to **[!UICONTROL Properties]** within the report, click **[!UICONTROL Rendering]** and choose the **[!UICONTROL Version 6.0 (Flash & OpenOffice)]** rendering engine.

![](assets/migration_reports_1.png)
-->
Si desea beneficiarse de las nuevas funcionalidades del informe, debe volver a publicar los informes. Para ello, edite el informe **[!UICONTROL Properties]**, haga clic en **[!UICONTROL Rendering]** y seleccione el motor de renderización v.6.x. En este caso, compruebe todos los scripts y cámbielos si es necesario. Con respecto a la exportación a PDF, si ha añadido una secuencia de comandos específica para Open Office, esto ya no funcionará con el nuevo motor de exportación a PDF (PhantomJS).

## Aplicaciones web {#web-applications}

Hay dos familias de aplicaciones web:

* aplicaciones web identificadas (vistas juntas, formularios de aprobación, desarrollos internos de extranet),
* aplicaciones web anónimas (formularios web o de cuestionario).

### Aplicaciones web identificadas {#identified-web-applications}

Al igual que para los informes ([más información](#reports)), si ha añadido JavaScript, debe comprobar y adaptar si es necesario. Si desea beneficiarse del banner azul v7 (que contiene las pestañas azules), debe volver a publicar la aplicación web. Si el código JavaScript está funcionando, puede seleccionar el motor de renderización v6.x. Si no es así, puede utilizar el motor de renderización v6.0 mientras adapta su código y, a continuación, utilizar el motor de renderización v6.x.

>[!NOTE]
Los pasos para seleccionar el motor de renderización son los mismos que para seleccionar informes. Consulte [Informes personalizados](#personalized-reports).

Los métodos de conexión de la aplicación web han cambiado en la versión 7. Si encuentra algún problema de conexión en sus aplicaciones web identificadas, debe activar temporalmente las opciones **allowUserPassword** y **sessionTokenOnly** en el archivo **serverConf.xml**. Después de la actualización, modifique estos valores de opción:

```
allowUserPassword="true"
```

```
sessionTokenOnly="true"
```

Por lo tanto, reinicie el postupgrade con el siguiente comando:

```
nlserver config -postupgrade -instance:<instance_name> -force
```

Pruebe las aplicaciones web en el motor de renderización v6.x antes de publicarlas. A continuación, desactive estas dos opciones.

```
allowUserPassword="false"
```

```
sessionTokenOnly="false"
```

### Aplicaciones web anónimas {#anonymous-web-applications}

Si tiene algún problema, vuelva a publicar la aplicación web. Si el problema persiste, puede seleccionar el motor de renderización v6.0. Si no ha añadido JavaScript, puede seleccionar el motor de renderización v6.x y beneficiarse de sus nuevas funciones.

>[!NOTE]
Los pasos para seleccionar el motor de renderización son los mismos que para seleccionar informes. Consulte [Informes personalizados](#personalized-reports).

## Red-Hat {#red-hat}

Si los esquemas predeterminados se han eliminado en las versiones 6.02 o 5.11, es posible que ya no pueda editar los esquemas después de la actualización. Si esto sucede, ejecute el comando:

```
su - neolane
nlserver config -postupgrade -instance:<instance name> -force
```
