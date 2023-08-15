---
product: campaign
title: Configuraciones generales
description: Configuraciones generales
feature: Upgrade
badge-v7-only: label="v7" type="Informative" tooltip="Se aplica solo a Campaign Classic v7"
audience: migration
content-type: reference
topic-tags: configuration
hide: true
hidefromtoc: true
exl-id: 7aad0e49-8d9c-40c7-9d6a-42fee0ae5870
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: tm+mt
source-wordcount: '2632'
ht-degree: 1%

---

# Configuraciones generales{#general-configurations}



Esta sección detalla la configuración que se debe realizar en Adobe Campaign v7 al migrar desde una versión 5.11 o 6.02.

Además:

* Si migra desde la versión 5.11 de, también debe completar la configuración detallada en [esta sección](../../migration/using/configuring-your-platform.md#specific-configurations-in-v5-11).
* Si migra desde la versión 6.02, también debe completar la configuración detallada en [esta sección](../../migration/using/configuring-your-platform.md#specific-configurations-in-v6-02).

## Zonas horarias {#time-zones}

### Modo de zona horaria múltiple {#multi-time-zone-mode}

En la versión 6.02, el modo &quot;zona horaria múltiple&quot; solo estaba disponible para motores de base de datos PostgreSQL. Ahora se ofrece independientemente del tipo de motor de base de datos que se utilice. Le recomendamos encarecidamente que transforme su base a una base de &quot;zona horaria múltiple&quot;.

Para utilizar el modo TIMESTAMP WITH TIMEZONE, también debe añadir la variable **-userTimestamptz:1** a la línea de comandos posterior a la actualización.

>[!IMPORTANT]
>
>Si la variable **-usetimestamptz:1** se utiliza con un motor de base de datos incompatible, la base de datos estará dañada y tendrá que restaurar una copia de seguridad de la base de datos y volver a ejecutar el comando anterior.

>[!NOTE]
>
>Es posible modificar la zona horaria después de la migración a través de la consola (**[!UICONTROL Administration > Platform > Options > WdbcTimeZone]** node).
>
>Para obtener más información sobre la administración de zonas horarias, consulte [esta sección](../../installation/using/time-zone-management.md).

### Oracle {#oracle}

Si recibe una **ORA 01805** error durante la posactualización, lo que significa que los archivos de zona horaria de Oracle entre el servidor de aplicaciones y el servidor de base de datos no están sincronizados. Para volver a sincronizarlos, siga los siguientes pasos:

1. Para identificar el archivo de zona horaria utilizado, ejecute el siguiente comando:

   ```
   select * from v$timezone_file
   ```

   Los archivos de zona horaria generalmente se encuentran en **ORACLE_HOME/oracore/zoneinfo/** carpeta.

1. Asegúrese de que los archivos de zona horaria sean idénticos en ambos servidores.

Para obtener más información, visite: [https://docs.oracle.com/cd/E11882_01/server.112/e10729/ch4datetime.htm#NLSPG004](https://docs.oracle.com/cd/E11882_01/server.112/e10729/ch4datetime.htm#NLSPG004).

Una desalineación de zona horaria entre el cliente y el servidor también puede causar algunos retrasos. Por este motivo, se recomienda utilizar la misma versión de la biblioteca de Oracle en los lados del cliente y del servidor, ya que ambos husos horarios deben ser iguales.

Para comprobar si ambos lados están en las mismas zonas horarias:

1. Compruebe la versión del archivo de zona horaria del lado del cliente ejecutando el siguiente comando:

   ```
   genezi -v
   ```

   genezi es un binario encontrado en **$ORACLE_HOME/bin** repositorio.

1. Compruebe la versión del archivo de zona horaria en el servidor ejecutando el siguiente comando:

   ```
   select * from v$timezone_file
   ```

1. Para cambiar el archivo de zona horaria en el lado del cliente, utilice el **ORA_TZFILE** variable de entorno.

## Seguridad {#security}

### Zonas de seguridad {#security-zones}

>[!IMPORTANT]
>
>Por motivos de seguridad, la plataforma Adobe Campaign ya no es accesible de forma predeterminada: es necesario configurar las zonas de seguridad y, por lo tanto, recopilar las direcciones IP de los operadores.

Adobe Campaign v7 incluye el concepto de **zonas de seguridad**. Cada usuario debe estar asociado a una zona para poder iniciar sesión en una instancia, y su dirección IP debe incluirse en las direcciones o intervalos de direcciones definidos en la zona de seguridad. La configuración de las zonas de seguridad se puede realizar en el archivo de configuración del servidor de Adobe Campaign. La zona de seguridad a la que está asociado un usuario debe definirse en la consola (**[!UICONTROL Administration > Access management > Operators]**).

**Antes de la migración**, pídale al administrador de red que le ayude a definir las zonas de seguridad que se activarán después de la migración.

**Después de la posactualización** (antes de reiniciar el servidor), debe configurar las zonas de seguridad.

La configuración de zona de seguridad se encuentra en [esta sección](../../installation/using/security-zones.md).

### Contraseñas de usuario {#user-passwords}

En la versión 7, **interno** y **administrador** la conexión del operador debe estar protegida con una contraseña. Se recomienda encarecidamente asignar contraseñas a estas cuentas y a todas las cuentas de operador, **antes de la migración**. Si no ha especificado una contraseña para **interno**, no se podrá conectar. Para asignar una contraseña a **interno**, introduzca el siguiente comando:

```
nlserver config -internalpassword
```

>[!IMPORTANT]
>
>El **interno** la contraseña debe ser idéntica para todos los servidores de seguimiento. Para obtener más información, consulte [esta sección](../../installation/using/configuring-campaign-server.md#internal-identifier) y [esta sección](../../platform/using/access-management.md).

### Nuevas funciones de la versión 7 de {#new-features-in-v7}

* Los usuarios sin permisos de ya no pueden conectarse a Adobe Campaign. Sus permisos deben añadirse manualmente, por ejemplo, creando un permiso llamado **conectar**.

  Los usuarios afectados por esta modificación se identifican y enumeran durante la posactualización.

* El seguimiento ya no funciona si la contraseña está vacía. Si este es el caso, un mensaje de error le hará saber y le pedirá que vuelva a configurarlo.
* Las contraseñas de usuario ya no se almacenan en **xtk:sessionInfo** esquema.
* Los permisos de administración ahora son necesarios para utilizar **xtk:builder:EvaluateJavaScript** y **xtk:builder:EvaluateJavaScriptTemplate** funciones.

Se han modificado ciertos esquemas predeterminados y ahora, de forma predeterminada, solo se puede acceder a ellos con acceso de escritura para operadores con **administrador** permiso:

* ncm:publicar
* nl:monitorización
* nms:calendario
* xtk:builder
* xtk:conexiones
* xtk:dbInit
* xtk:entityBackupNew
* xtk:entityBackupOriginal
* xtk:entityOriginal
* xtk:formulario
* xtk:funcList
* xtk:fusion
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

En la versión 5, la variable **sessiontoken** Este parámetro funciona en ambos lados del cliente (lista de pantallas de tipo de información general, editor de vínculos, etc.) y del lado del servidor (aplicaciones web, informes, jsp, jsp, etc.). En la versión 7, solo funciona en el servidor. Si desea volver a la funcionalidad completa como en la versión 5, debe modificar los vínculos con este parámetro y pasar a través de la página de conexión:

Ejemplo de vínculo:

```
/view/recipientOverview?__sessiontoken=<trusted login>
```

Nuevo vínculo con la página de conexión:

```
/nl/jsp/logon.jsp?login=<trusted login>&action=submit&target=/view/recipientOverview
```

>[!IMPORTANT]
>
>Si utiliza un operador vinculado a una máscara IP de confianza, compruebe que tiene los derechos mínimos y que está en una zona de seguridad en **sessionTokenOnly** modo.

### Funciones SQL {#sql-functions}

Las llamadas de función SQL desconocidas ya no se envían de forma natural al servidor. Actualmente, todas las funciones SQL deben agregarse al **xtk:funcList** esquema (para obtener más información, consulte [esta sección](../../configuration/using/adding-additional-sql-functions.md)). Al migrar, se agrega una opción durante la posactualización que le permite mantener la compatibilidad con funciones SQL antiguas no declaradas. Si desea seguir utilizando estas funciones, compruebe que la variable **XtkPassUnknownSQLFunctionsToRDBMS** La opción está definida en **[!UICONTROL Administration > Platform > Options]** nivel de nodo.

>[!IMPORTANT]
>
>Recomendamos encarecidamente no utilizar esta opción debido a los riesgos de seguridad que presenta.

### JSSP {#jssp}

Si desea autorizar el acceso a determinadas páginas mediante el protocolo HTTP (no HTTPS) en sus aplicaciones web, por ejemplo, independientemente de la configuración realizada en las zonas de seguridad, debe especificar la variable **httpAllowed=&quot;true&quot;** en la regla de retransmisión correspondiente.

Si utiliza JSSP anónimos, debe agregar la variable **httpAllowed=&quot;true&quot;** en una regla de retransmisión para su JSSP (**[!UICONTROL serverConf.xml]** file):

Por ejemplo:

```
<url IPMask="" deny="" hostMask="" httpAllowed="true" relayHost="true" relayPath="true"
           status="blacklist" targetUrl="https://localhost:8080" timeout="" urlPath="*/cus/myPublicPage.jssp"/>
```

## Sintaxis {#syntax}

### JavaScript {#javascript}

Adobe Campaign v7 integra un intérprete de JavaScript más reciente. Sin embargo, esta actualización puede provocar que algunos scripts no funcionen correctamente. Como el motor anterior era más permisivo, ciertas sintaxis funcionarían, lo que ya no es el caso con la nueva versión del motor.

El **[!UICONTROL myObject.@attribute]** ahora, la sintaxis solo es válida para objetos XML. Esta sintaxis se puede utilizar para personalizar las entregas y la administración de contenido. Si ha utilizado este tipo de sintaxis en un objeto no XML, las funciones de personalización dejarán de funcionar.

Para todos los demás tipos de objetos, la sintaxis es ahora **[!UICONTROL myObject`[`&quot;attribute&quot;`]`]**. Por ejemplo, un objeto no XML que utilizó la siguiente sintaxis: **[!UICONTROL employee.@sn]**, ahora debe utilizar la sintaxis siguiente: **[!UICONTROL employee`[`&quot;sn&quot;`]`]**.

* Sintaxis anterior:

  ```
  employee.@sn
  ```

* Nueva sintaxis:

  ```
  employee["sn"]
  ```

Para cambiar un valor en un objeto XML, ahora debe empezar actualizando el valor antes de agregar el nodo XML:

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

Para reforzar la seguridad de las instancias, se ha introducido una nueva sintaxis en Adobe Campaign v7 para reemplazar la sintaxis basada en SQLData. Si utiliza estos elementos de código con esta sintaxis, debe modificarlos. Los principales elementos afectados son:

* Filtrado por subconsulta: la nueva sintaxis se basa en la variable `<subQuery>`  para definir una subconsulta
* Aggregates: la nueva sintaxis es &quot;aggregate function(collection)&quot;
* Filtrado por combinación: la nueva sintaxis es `[schemaName:alias:xPath]`

Se ha modificado el esquema queryDef (xtk:queryDef):

* una nueva `<subQuery>`  está disponible para reemplazar el elemento SELECT incluido en SQLData
* se introducen dos nuevos valores, &quot;IN&quot; y &quot;NOT IN&quot; para el atributo @setOperator
* una nueva `<where>`  , que es un elemento secundario del `<node>` element: esto permite realizar &quot;subselecciones&quot; en SELECT

Cuando se utiliza un atributo &quot;@expr&quot;, puede que SQLData esté presente. Se puede buscar los siguientes términos: &quot;SQLData&quot;, &quot;aliasSqlTable&quot;, &quot;sql&quot;.

Las instancias de Adobe Campaign v7 están protegidas de forma predeterminada. La seguridad se presenta en términos de definiciones de zonas de seguridad en el **[!UICONTROL serverConf.xml]** archivo: el **allowSQLInjection** administra la seguridad de sintaxis de SQL.

Si se produce un error de SQLData durante la ejecución posterior a la actualización, debe modificar este atributo para permitir temporalmente el uso de sintaxis basada en SQLData, lo que le permite reescribir el código. Para ello, se debe cambiar la siguiente opción en la **serverConf.xml** archivo:

```
allowSQLInjection="true"
```

Por lo tanto, reinicie la posactualización con el siguiente comando:

```
nlserver config -postupgrade -instance:<instance_name> -force
```

Debe configurar las zonas de seguridad (consulte [Seguridad](#security)) y, a continuación, reactive la seguridad cambiando la opción:

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

Función de agregado (colección)

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
  >Las uniones se llevan a cabo automáticamente para las funciones acumuladas. Ya no es necesario especificar la condición WHERE O0.iOperationId=iOperationId.
  >
  >Ya no es posible utilizar la función &quot;count(&#42;)&quot;. Debe utilizar &quot;count()&quot;.

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

En un `<subQuery>` , para hacer referencia a un campo &quot;field&quot; del elemento principal `<queryDef>`   utilice la sintaxis siguiente: `[../@field]`

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

La migración se realiza mediante una actualización posterior y los conflictos pueden aparecer en informes, formularios o aplicaciones web. Estos conflictos se pueden resolver desde la consola de.

Después de la sincronización de recursos, la variable **posterior a la actualización** El comando permite detectar si la sincronización genera errores o advertencias.

### Ver el resultado de la sincronización {#view-the-synchronization-result}

El resultado de la sincronización se puede ver de dos maneras:

* En la interfaz de la línea de comandos, los errores se materializan mediante un corchete triple **>>>** y la sincronización se detiene automáticamente. Las advertencias se materializan mediante comillas dobles **>>** y deben resolverse una vez finalizada la sincronización. Al final de la posactualización, se muestra un resumen en el símbolo del sistema. Por ejemplo:

  ```
  2013-04-09 07:48:39.749Z        00002E7A          1     info    log     =========Summary of the update==========
  2013-04-09 07:48:39.749Z        00002E7A          1     info    log     test instance, 6 warning(s) and 0 error(s) during the update.
  2013-04-09 07:48:39.749Z        00002E7A          1     warning log     The document with identifier 'mobileAppDeliveryFeedback' and type 'xtk:report' is in conflict with the new version.
  2013-04-09 07:48:39.749Z        00002E7A          1     warning log     The document with identifier 'opensByUserAgent' and type 'xtk:report' is in conflict with the new version.
  2013-04-09 07:48:39.750Z        00002E7A          1     warning log     The document with identifier 'deliveryValidation' and type 'nms:webApp' is in conflict with the new version.
  2013-04-09 07:48:39.750Z        00002E7A          1     warning log     Document of identifier 'nms:includeView' and type 'xtk:srcSchema' updated in the database and found in the file system. You will have to merge the two versions manually.
  ```

  Si la advertencia se refiere a un conflicto de recursos, se requiere la atención del operador para resolverlo.

* El **postupgrade_`<server version number>`_hora de postactualización`>`.log** contiene el resultado de la sincronización. Está disponible de forma predeterminada en el siguiente directorio: **directorio de instalación/var/`<instance>`posterior a la actualización**. Los errores y advertencias se indican mediante la variable **error** y **advertencia** atributos.

### Resolver un conflicto {#resolve-a-conflict}

La resolución de conflictos solo debe realizarla un operador avanzado y aquellos a los que se les hayan otorgado derechos de &#39;Administrador&#39;.

Para resolver un conflicto, siga el siguiente proceso:

1. En la estructura de árbol de Adobe Campaign, coloque el cursor sobre **[!UICONTROL Administration > Configuration > Package management > Edit conflicts]**.
1. Seleccione el conflicto que desea resolver en la lista.

Existen tres formas posibles de resolver un conflicto:

* **[!UICONTROL Declared as resolved]**: requiere la intervención previa del operador.
* **[!UICONTROL Accept the new version]**: recomendado si el usuario no ha cambiado los recursos proporcionados con Adobe Campaign.
* **[!UICONTROL Keep the current version]**: significa que la actualización se rechaza.

  >[!IMPORTANT]
  >
  >Si selecciona este modo de resolución, se arriesga a perder parches en la nueva versión. Por lo tanto, se recomienda encarecidamente que esta opción no se utilice ni se reserve únicamente para operadores expertos.

Si decide resolver manualmente el conflicto, siga este procedimiento:

1. En la sección inferior de la ventana, busque la variable **`_conflict_ string`** para localizar las entidades con conflictos. La entidad instalada con la nueva versión contiene el **nuevo** , la entidad que coincide con la versión anterior contiene el argumento **cus** argumento.

   ![](assets/s_ncs_production_conflict002.png)

1. Elimine la versión que no desee conservar. Elimine el **`_conflict_argument_ string`** de la entidad que mantiene.

   ![](assets/s_ncs_production_conflict003.png)

1. Vaya al conflicto que habría resuelto. Haga clic en **[!UICONTROL Actions]** y seleccione **[!UICONTROL Declare as resolved]**.
1. Guarde los cambios: el conflicto se ha resuelto.

## Tomcat {#tomcat}

La versión del servidor Tomcat integrado en Adobe Campaign v7 ha cambiado. Su carpeta de instalación (tomcat-6) también ha cambiado (tomcat 7). Después de la postactualización, asegúrese de comprobar que las rutas no están vinculadas a la carpeta actualizada (en el **[!UICONTROL serverConf.xml]** file):

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

**Antes de la posactualización**, debe eliminar todas las referencias de esquema de la versión 6.02 que ya no existirán en la versión 7.

* nms:emailOfferView
* nms:webOfferView
* nms:callCenterOfferView
* nms:mobileOfferView
* nms:paperOfferView

### Contenido de oferta {#offer-content}

En la versión 7, se ha movido el contenido de la oferta. En la versión 6.02, el contenido estaba en cada esquema de representación (**nms:emailOfferView**). En la versión 7, el contenido se encuentra ahora en el esquema de oferta. Después de la postactualización, el contenido no será visible en la interfaz. Después de la postactualización, se debe volver a crear el contenido de la oferta o desarrollar una secuencia de comandos que mueva automáticamente el contenido del esquema de representación al esquema de oferta.

>[!IMPORTANT]
>
>Si algunos envíos que utilizan ofertas configuradas se enviaban después de la migración, debe eliminar y volver a crear todos estos envíos en la versión 7. Si no puede hacerlo, se ofrece un &quot;modo de compatibilidad&quot;. No se recomienda este modo porque no se beneficiará de todas las nuevas funciones de Interaction v7. Se trata de un modo de transición que le permite completar campañas en curso antes de la migración real a la versión 6.1. Para obtener más información sobre este modo, póngase en contacto con nosotros.

Ejemplo de secuencia de comandos de movimiento (**interactionTo610_full_XX.js**) está disponible en el **Migración** dentro de la carpeta Adobe Campaign v7. Este archivo muestra un ejemplo de una secuencia de comandos para un cliente mediante una única representación de correo electrónico por oferta (la variable **[!UICONTROL htmlSource]** y **[!UICONTROL textSource]** campos). El contenido que estaba en **NmsEmailOfferView** se ha movido a la tabla de ofertas.

>[!NOTE]
>
>El uso de este script no le permite beneficiarse de las opciones de &quot;administración de contenido&quot; y &quot;funciones de renderización&quot;. Para beneficiarse de estas funciones, debe reconsiderar las ofertas del catálogo, especialmente los espacios de contenido de ofertas y configuración.

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

Este es el procedimiento que debe seguirse después de haber movido el contenido de la oferta si solo tiene un entorno. En este caso tomemos &quot;ENV&quot; como ejemplo.

1. En todos los espacios de ofertas de entorno &quot;ENV&quot;, actualice la lista de campos utilizados. Por ejemplo, para un espacio de oferta que solo utiliza la variable **[!UICONTROL htmlSource]**, debe agregar el **[!UICONTROL view/htmlSource]**.

   ![](assets/migration_interaction_2.png)

1. En el **[!UICONTROL Type of Environment]** dentro del campo **[!UICONTROL General]** pestaña, seleccione **[!UICONTROL Live]**.

   ![](assets/migration_interaction_3.png)

1. Cree un entorno de diseño (&quot;ENV_DESIGN&quot;, por ejemplo) y conéctelo al entorno en línea ENV.

   ![](assets/migration_interaction_4.png)

1. Implemente todos los espacios de ofertas de entorno &quot;ENV&quot; (haga clic con el botón derecho > **[!UICONTROL Actions > Deploy]**) y seleccione el entorno &quot;ENV_DESIGN&quot;.

   ![](assets/migration_interaction_5.png)

1. Haga lo mismo para todas las ofertas de entorno &quot;ENV&quot;.
1. Active todas las ofertas de entorno &quot;ENV_DESIGN&quot; en los canales relevantes.
1. Prueba de activación de una oferta. Si no encuentra ningún problema, ejecute las tareas pendientes en la última tarea del flujo de trabajo **[!UICONTROL Offer notification]** (offerMgt) para activar todas las ofertas.

   ![](assets/migration_interaction_6.png)

1. Realice pruebas exhaustivas.

   >[!NOTE]
   >
   >Los nombres de las categorías y las ofertas en línea se modifican después de su publicación. En el canal entrante, actualice todas las referencias a ofertas y categorías.

## Informes {#reports}

### Informes estándar {#standard-reports}

Todos los informes estándar utilizan actualmente el motor de renderización v6.x. Si ha añadido JavaScript a estos informes, es posible que algunos elementos ya no funcionen. De hecho, la versión antigua de JavaScript no es compatible con el motor de renderización v6.x. Por lo tanto, debe comprobar el código JavaScript y adaptarlo más adelante. Debe probar todos los informes, especialmente la función de exportación.

### Informes personalizados {#personalized-reports}

<!--If you want to have the blue banner from v7 (allowing you access to the tabs), you must republish reports. If you encounter problems, you can force the v6.0 rendering engine. To do this, go to **[!UICONTROL Properties]** within the report, click **[!UICONTROL Rendering]** and choose the **[!UICONTROL Version 6.0 (Flash & OpenOffice)]** rendering engine.

![](assets/migration_reports_1.png)
-->
Si desea beneficiarse de las nuevas funcionalidades de informes, debe volver a publicar los informes. En este caso, compruebe todos los scripts y cámbielos si es necesario. En cuanto a la exportación de PDF, si ha añadido una secuencia de comandos específica para Open Office, esto ya no funcionará con el nuevo motor de exportación de PDF (PhantomJS).

## Aplicaciones web {#web-applications}

Existen dos familias de aplicaciones web:

* aplicaciones web identificadas (vistas conjuntamente, formularios de aprobación, desarrollos internos de extranet),
* aplicaciones web anónimas (formularios web o de cuestionario).

### Aplicaciones web identificadas {#identified-web-applications}

Igual que para los informes ([obtenga más información](#reports)), si ha añadido JavaScript, debe comprobar y adaptar si es necesario. Si desea beneficiarse del banner azul v7 (que contiene las pestañas azules), debe volver a publicar la aplicación web.

Los métodos de conexión de la aplicación web han cambiado en la versión 7. Si encuentra algún problema de conexión en las aplicaciones web identificadas, debe activar temporalmente el **allowUserPassword** y **sessionTokenOnly** opciones en la **serverConf.xml** archivo. Después de la postactualización, modifique estos valores de opción:

```
allowUserPassword="true"
```

```
sessionTokenOnly="true"
```

Por lo tanto, reinicie la posactualización con el siguiente comando:

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

Si tiene algún problema, vuelva a publicar la aplicación web.
