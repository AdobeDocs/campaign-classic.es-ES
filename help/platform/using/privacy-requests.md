---
title: Solicitudes de privacidad
description: Obtenga información sobre cómo administrar las solicitudes de privacidad
page-status-flag: never-activated
uuid: a044bbea-521d-4c1e-8aab-7d51a87fc94b
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: platform
content-type: reference
topic-tags: starting-with-adobe-campaign
discoiquuid: 14369acf-9149-4649-947a-c16289e35eb6
translation-type: tm+mt
source-git-commit: c2c7398c27f1bc7edf9adb0fc07409d2e525b168
workflow-type: tm+mt
source-wordcount: '2443'
ht-degree: 14%

---


# Administración de solicitudes de privacidad {#privacy-requests}

For a general presentation on Privacy Management, refer to [this section](../../platform/using/privacy-management.md).

Esta información se aplica al RGPD, la CCPA, la PDPA y la LGPD. Para obtener más información sobre estas normativas, consulte [esta sección](../../platform/using/privacy-management.md#privacy-management-regulations).

The opt-out for the Sale of Personal Information, which is specific to CCPA, is explained in [this section](#sale-of-personal-information-ccpa).

>[!IMPORTANT]
>
>Los procedimientos de instalación descritos en este documento son aplicables a partir del Campaign Classic 18.4 (compilación 8931+). If you are running on a previous version, refer to this [technote](https://helpx.adobe.com/es/campaign/kb/how-to-install-gdpr-package-on-legacy-versions.html).

## Acerca de las solicitudes de privacidad {#about-privacy-requests}

Para ayudarle a facilitar su preparación para la privacidad, Adobe Campaign le permite gestionar solicitudes de acceso y eliminación. El **derecho de acceso** y el **derecho a ser olvidado** (solicitud de supresión) se describen en [esta sección](../../platform/using/privacy-management.md#right-access-forgotten).

Veamos cómo puede crear solicitudes de acceso y eliminación, así como cómo las procesa Adobe Campaign.

### Principios {#principles}

Adobe Campaign ofrece a los controladores de datos dos posibilidades para realizar solicitudes de Acceso y Eliminación de privacidad:

* Via the **Adobe Campaign interface**: for each Privacy request, the Data Controller creates a new privacy request in Adobe Campaign. Consulte [esta sección](#create-privacy-request-ui).
* Via the **API**: Adobe Campaign provides an API that allows the automatic process of Privacy requests using SOAP. Consulte [esta sección](#automatic-privacy-request-api).

>[!NOTE]
>
>Para obtener más información sobre los datos personales y las distintas entidades que administran los datos (controlador de datos, procesador de datos y sujeto de datos), consulte [Datos personales y personas](../../platform/using/privacy-and-recommendations.md#personal-data).

### Requisitos previos {#prerequesites}

Adobe Campaign oferta las herramientas de los controladores de datos para crear y procesar solicitudes de privacidad de datos almacenados en Adobe Campaign. Sin embargo, es responsabilidad del controlador de datos administrar la relación con el sujeto de datos (correo electrónico, atención al cliente o un portal web).

Por ello, es responsabilidad del controlador de datos confirmar la identidad del sujeto de datos que realiza la solicitud y confirmar que la información devuelta al solicitante sea sobre el sujeto de datos.

### Installing the Privacy package {#install-privacy-package}

Para utilizar esta función, debe instalar el **[!UICONTROL Privacy Data Protection Regulation]** paquete mediante el menú **[!UICONTROL Tools]** > **[!UICONTROL Advanced]** > **[!UICONTROL Import package]** > **[!UICONTROL Adobe Campaign Package]** . Para obtener más información sobre cómo instalar paquetes, consulte la documentación [](../../installation/using/installing-campaign-standard-packages.md)detallada.

Se crean dos carpetas nuevas, específicas de Privacidad, en **[!UICONTROL Administration]** > **[!UICONTROL Platform]**:

* **[!UICONTROL Privacy Requests]**:: aquí es donde creará sus solicitudes de privacidad y rastreará su evolución.
* **[!UICONTROL Namespaces]**:: aquí es donde definirá el campo que se utilizará para identificar el asunto de datos en la base de datos de Adobe Campaign.

![](assets/privacy-folders.png)

En **[!UICONTROL Administration]** > **[!UICONTROL Production]** > **[!UICONTROL Technical workflows]**, se ejecutan tres flujos de trabajo técnicos cada día para procesar las solicitudes de privacidad.

![](assets/privacy-workflows.png)

* **[!UICONTROL Collect privacy requests]**:: este flujo de trabajo genera los datos del destinatario almacenados en Adobe Campaign y los pone a disposición para su descarga en la pantalla de la solicitud de privacidad.
* **[!UICONTROL Delete privacy requests data]**:: este flujo de trabajo elimina los datos del destinatario almacenados en Adobe Campaign.
* **[!UICONTROL Privacy request cleanup]**:: este flujo de trabajo borra los archivos de solicitud de acceso que tienen más de 90 días.

En **[!UICONTROL Administration]** > **[!UICONTROL Access Management]** > **[!UICONTROL Named rights]**, se ha añadido la **[!UICONTROL Privacy Data Right]** derecha con nombre. Se requiere este derecho con nombre para que los controladores de datos puedan utilizar las herramientas de privacidad. Esto les permite crear nuevas solicitudes, rastrear su evolución, utilizar la API, etc.

![](assets/privacy-right.png)

### Áreas de nombres {#namesspaces}

Antes de crear solicitudes de privacidad, debe definir la Área de nombres que utilizará. Ésta es la clave que se utilizará para identificar el asunto de los datos en la base de datos de Adobe Campaign.

Hay tres áreas de nombres predeterminadas disponibles: correo electrónico, teléfono y teléfono móvil. Si necesita una Área de nombres diferente (por ejemplo, un campo personalizado de destinatario), puede crear una nueva desde **[!UICONTROL Administration]** > **[!UICONTROL Platform]** > **[!UICONTROL Namespaces]**.

## Creación de una solicitud de privacidad {#create-privacy-request-ui}

La interfaz **de** Adobe Campaign le permite crear sus solicitudes de privacidad y rastrear su evolución. Para crear una nueva solicitud de privacidad, siga estas instrucciones:

1. Acceda a la carpeta de solicitud de privacidad en **[!UICONTROL Administration]** > **[!UICONTROL Platform]** > **[!UICONTROL Privacy Requests]**.

   ![](assets/privacy-requests-folder.png)

1. Esta pantalla le permite realizar la vista de todas las solicitudes de privacidad actuales, su estado y los registros. Haga clic en **[!UICONTROL New]** para crear una solicitud de privacidad.

   ![](assets/privacy-request-new.png)

1. Seleccione la opción **[!UICONTROL Regulation]** (GDPR, CCPA, PDPA o LGPD), **[!UICONTROL Request type]** (Acceso o Eliminar), seleccione una **[!UICONTROL Namespace]** e introduzca la **[!UICONTROL Reconciliation value]**. Si utiliza el correo electrónico como Área de nombres, escriba el correo electrónico del sujeto de datos.

   ![](assets/privacy-request-properties.png)

Los flujos de trabajo técnicos de privacidad se ejecutan una vez al día y procesan cada nueva solicitud:

* Eliminar solicitud: se borran los datos del destinatario almacenados en Adobe Campaign.
* Solicitudes de acceso: los datos del destinatario almacenados en Adobe Campaign se generan y se ponen a disposición como archivo XML en la parte izquierda de la pantalla de solicitud.

![](assets/privacy-request-download.png)

### Lista de los cuadros {#list-of-tables}

Al realizar una solicitud de privacidad de eliminación o acceso, Adobe Campaign busca todos los datos del sujeto de datos en función de los datos **[!UICONTROL Reconciliation value]** en todas las tablas que tienen un vínculo a la tabla de destinatario (tipo propio).

Esta es la lista de tablas integradas que se tienen en cuenta al realizar solicitudes de privacidad:

* Destinatarios (destinatario)
* Registro de envíos de destinatario (wideLogRcp)
* Registro de seguimiento de destinatario (trackingLogRcp)
* Registro de envíos de evento archivado (wideLogEventHisto)
* Contenido de lista de destinatario (rcpGrpRel)
* Propuesta de oferta de visitante (propositionVisitor)
* Visitantes (visitante)
* Historial de suscripciones (subHisto)
* Suscripciones (suscripción)
* Propuesta de oferta de destinatario (propositionRcp)

Si ha creado tablas personalizadas que tienen un vínculo a la tabla de destinatario (tipo propio), también se tendrán en cuenta. Por ejemplo, si tiene una tabla de transacciones vinculada a la tabla de destinatarios y una tabla de detalles de transacciones vinculada a la tabla de transacciones, ambas se tendrán en cuenta.

>[!IMPORTANT]
>
>Si realiza solicitudes por lotes de privacidad utilizando flujos de trabajo de eliminación de perfiles, tenga en cuenta las siguientes observaciones:
>* La eliminación de perfiles mediante flujos de trabajo no procesa las tablas secundarias.
>* Debe gestionar la eliminación de todas las tablas secundarias.
>* Adobe recomienda crear un flujo de trabajo de ETL que agregue las líneas que se eliminarán en la tabla Acceso a privacidad y que permita que el usuario **[!UICONTROL Delete privacy requests data]** realice la eliminación. Sugerimos limitar a 200 perfiles por día para eliminarlos por motivos de rendimiento.


### Estados de solicitud de privacidad {#privacy-request-statuses}

Estos son los distintos estados de las solicitudes de privacidad:

* **[!UICONTROL New]** / **[!UICONTROL Retry pending]**: en curso, el flujo de trabajo aún no ha procesado la solicitud.
* **[!UICONTROL Processing]** / **[!UICONTROL Retry in progress]**: el flujo de trabajo está procesando la solicitud.
* **[!UICONTROL Delete pending]**:: el flujo de trabajo ha identificado todos los datos de destinatario que se van a eliminar.
* **[!UICONTROL Delete in progress]**:: el flujo de trabajo está procesando la eliminación.
* **[!UICONTROL Delete Confirmation Pending]** (Eliminar solicitud en modo de proceso de 2 pasos): el flujo de trabajo ha procesado la solicitud de Access. Se solicita confirmación manual para realizar la eliminación. El botón está disponible durante 15 días.
* **[!UICONTROL Complete]**:: el procesamiento de la solicitud ha finalizado sin error.
* **[!UICONTROL Error]**:: el flujo de trabajo ha encontrado un error. The reason appears in the list of Privacy requests in the **[!UICONTROL Request status]** column. Por ejemplo, **[!UICONTROL Error data not found]** significa que en la base de datos no se han encontrado datos de destinatario que coincidan con los del sujeto de datos **[!UICONTROL Reconciliation value]** .

### Proceso de 2 pasos {#two-step-process}

By default, the **2-step process** is activated. Cuando se crea una nueva solicitud de eliminación con este modo, Adobe Campaign siempre realiza primero una solicitud de acceso. Esto le permite comprobar los datos antes de confirmar la eliminación.

Puede cambiar este modo desde la pantalla de edición de solicitud de privacidad. Haga clic en **[!UICONTROL Advanced settings]**.

![](assets/privacy-request-advanced-settings.png)

With the 2-step mode activated, the status of a new Delete request changes to **[!UICONTROL Confirm Delete Pending]**. Descargue el archivo XML generado desde la pantalla de solicitud de privacidad y compruebe los datos. Para confirmar la eliminación de datos, haga clic en el **[!UICONTROL Confirm delete data]** botón .

![](assets/privacy-request-delete-data.png)

### URL JSSP {#jspp-url}

Al procesar solicitudes de Access, Adobe Campaign genera un JSSP que recupera los datos del destinatario de la base de datos y los exporta a un archivo XML almacenado en el equipo local. La dirección URL de JSSP se define de la siguiente manera:

```
"$(serverUrl)+'/nms/gdpr.jssp?id='+@id"
```

donde @id es el ID de solicitud de privacidad.

Esta URL se almacena en el **[!UICONTROL "File location" (@urlFile)]** campo del **[!UICONTROL Privacy Requests (gdprRequest)]** esquema.

La información está disponible en la base de datos durante 90 días. Una vez que el flujo de trabajo técnico ha limpiado la solicitud, la información se elimina de la base de datos y la dirección URL queda obsoleta. Verifique que la dirección URL siga siendo válida antes de descargar los datos de una página web.

Este es un ejemplo del archivo de datos de un sujeto de datos:

![](assets/privacy-access-file.png)

Los controladores de datos pueden crear fácilmente una aplicación web que incluya la URL JSSP correspondiente para que el archivo de datos del sujeto de datos esté disponible desde una página web.

![](assets/privacy-gdpr-jssp.png)

Este es un fragmento de código que puede utilizar como ejemplo en la **[!UICONTROL Page]** actividad de la aplicación web.

![](assets/privacy-page-activity.png)

```
<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Transitional//EN" "http://www.w3.org/TR/xhtml1/DTD/xhtml1-transitional.dtd"> <html xmlns="http://www.w3.org/1999/xhtml"> <head> <meta http-equiv="Content-Language" content="en"> <meta http-equiv="Content-Type" content="text/html; charset=utf-8" /> <link rel="stylesheet" type="text/css" href="/nl/webForms/landingPage.css"/> <title>Clickthrough</title> <style type="text/css" media="all"> /* override formulary area */ .formulary { top: 200px; position: absolute; left: 0; } </style> </head> <body style="" class="">
<center>
<div id="wrap">
<div id="header"><img class="nlui-widget" alt="placeholder_header" src="/nms/img/contentModels/placeholder_header.png" unselectable="on" />
<div class="header-title center-title">DOWNLOAD GDPR DATA</div>
<div class="formulary center-formulary"><form>
<div class="button large-button"><a href=[SERVER_URL]/nms/gdpr.jssp?id=13000" data-nl-type="externalLink">CLICK TO DOWNLOAD</a></div>
</form></div>
</div>
<div id="content">
<div class="row">
<div class="info">
<div class="desc">
<div class="title">EFFICIENCY</div>
<div class="desc">Our service is guaranteed to improve your efficiency. Increase performance and use our high-technology service to implement even the most ambitious of projects.</div>
</div>
</div>
</div>
</div>
<div id="footer">
<div style="text-align: center;">
<div style="float: left;"><a href="#">Contact us</a></div>
<div style="float: right;">&copy; Copyrights</div>
<div><a href="#"><img title="facebook" class="nlui-widget" alt="facebook" src="/xtk/img/facebook.png" unselectable="on" /></a> <a href="#"><img title="Twitter" class="nlui-widget" alt="twitter" src="/xtk/img/twitter.png" unselectable="on" /></a> <a href="#"><img title="Google" class="nlui-widget" alt="google_plus" src="/xtk/img/google_plus.png" unselectable="on" /></a> <a href="#"><img title="Linkedin" class="nlui-widget" alt="Linkedin" src="/xtk/img/linkedin.png" unselectable="on" /></a></div>
</div>
</div>
</div>
</center>
</body> </html>
```

Dado que el acceso al archivo de datos del sujeto de datos está restringido, el acceso anónimo a la página web debe deshabilitarse. Solo el operador con el **[!UICONTROL Privacy Data Right]** nombre derecho puede iniciar sesión en la página y descargar los datos.

## Proceso de solicitud de privacidad automática {#automatic-privacy-request-api}

Adobe Campaign proporciona una **API** que le permite configurar un proceso automático de solicitud de privacidad.

Con la API, el proceso general de privacidad es el mismo que [usar la interfaz](#create-privacy-request-ui). La única diferencia es la creación de la solicitud de privacidad. En lugar de crear la solicitud en Adobe Campaign, se envía a la Campaña un POST que la contiene. Para cada solicitud, se agrega una nueva entrada en la **[!UICONTROL Privacy Requests]** pantalla. A continuación, los flujos de trabajo técnicos de privacidad procesan la solicitud, del mismo modo que para una solicitud agregada mediante la interfaz.

If you&#39;re using the API to submit Privacy requests, we recommend that you leave the **2-step process** activated for the first Delete requests, in order to test the returned data. Una vez finalizadas las pruebas, puede desactivar el proceso de 2 pasos para que el proceso de solicitud de eliminación se pueda ejecutar automáticamente.

The **[!UICONTROL CreateRequestByName]** JS API is defined as follows.

>[!NOTE]
>
>Si estaba utilizando la API **gdprRequest**, puede hacerlo, pero se recomienda utilizar la nueva API **privacyRequest**.

>[!IMPORTANT]
>
>Se requiere el **[!UICONTROL Privacy Data Right]** derecho con nombre para utilizar la API.

```
<method library="nms:gdpr.js" name="CreateRequestByName" static="true">
 <help>Create a new GDPR Request using namespace internal name</help>
 <parameters>
  <param name="namespaceName" type="string" desc="Namespace internal name"/>
  <param name="reconciliationValue" type="string" desc="Reconciliation value"/>
  <param name="type" type="long" desc="Reconciliation value"/>
  <param name="confirmDeletePending" type="boolean" desc="Request confirm before deleting data"/>
  <param name="regulation" type="long" desc="regulation of newly created request"/>
  <param name="id" type="long" inout="out" desc="ID of newly created request"/>
 </parameters>
</method>
```

>[!NOTE]
>
>El campo &quot;Regulación&quot; solo está disponible si utiliza Campaign Classic 20.2 (versión 9178+).
>
>Si migra a 20.2 y ya estaba utilizando la API, debe añadir el campo &quot;Regulación&quot; como se muestra arriba. Si está utilizando una versión anterior, puede seguir utilizando la API sin el campo &quot;regulación&quot;.

### Llamada a la API externamente {#invoking-api-externally}

A continuación se muestra un ejemplo de cómo puede invocar la API externamente (autenticación mediante la API y detalles específicos sobre la API de privacidad). Para obtener más información sobre la API de privacidad, consulte la documentación [de la](https://docs.adobe.com/content/help/en/campaign-classic/technicalresources/api/s-nms-privacyRequest.html)API. También puede consultar la documentación [de llamadas al servicio](../../configuration/using/web-service-calls.md)Web.

En primer lugar, debe realizar la autenticación mediante la API:

1. Descargue el WSDL **xtk:session** mediante esta dirección URL: **`<server url>`/nl/jsp/schemawsdl.jsp?esquema=xtk:session**.

1. Utilice el método &quot;Logon&quot; y pase un nombre de usuario y una contraseña como parámetros en la solicitud. Recibirá una respuesta que contenga un token de sesión. Este es un ejemplo de uso de SoapUI.

   ![](assets/privacy-api.png)

1. Utilice el testigo de sesión devuelto como autenticación para todas las llamadas de API posteriores. expira a las 24 horas.

A continuación, invoque la API de privacidad:

1. Download the WSDL from this URL: **`<server url>`/nl/jsp/schemawsdl.jsp?schema=nms:privacyRequest**.

1. Use **[!UICONTROL CreateRequestByName]** to create a specific Privacy request.

   Here is an example using the **[!UICONTROL CreateRequestByName]**. Observe cómo se utiliza el token de sesión proporcionado arriba como autenticación. La respuesta es el ID de la solicitud creada.

   ![](assets/privacy-api-2.png)

   Para ayudarle a realizar los pasos anteriores, tenga en cuenta lo siguiente:

   * You can use a **queryDef** on the **nms:gdprRequest** schema to check the status of the Access request.
   * You can use a **queryDef** on the **nms:gdprRequestData** schema to get the result of the Access request.
   * To be able to download the XML file from **&quot;$(serverUrl)&#39;/nms/gdpr.jssp?id=&#39;@id&quot;**, you must be logged in and accessing it from a whitelisted IP. Para ello, cree una aplicación web que le permita acceder al archivo generado por el JSSP.

### Invocación de la API desde un JS {#invoking-api-from-js}

A continuación se muestra un ejemplo de cómo puede invocar la API desde un JS dentro de Campaign Classic.

>[!NOTE]
>
>El campo &quot;Regulación&quot; solo está disponible si utiliza Campaign Classic 20.2 (versión 9178+).
>
>Si migra a 20.2 y ya estaba utilizando la API, debe añadir el campo &quot;Regulación&quot;. Si está utilizando una versión anterior, puede seguir utilizando la API sin el campo &quot;regulación&quot;.

* If you are **using a previous build (with GDPR package)**, you can continue to use the API without the ‘regulation’ field as shown below:

   ```
   loadLibrary("nms:gdpr.js");
   /**************************** 
   This code calls an API to create new Privay request on the DB.
   It requires 4 parameters below.
   Feel free to change parameter values.
   ****************************/
   // 1. Namespace internal name
   var namespaceName = "defaultNamespace1";
   // 2. Reconciliation value for privacy request
   var reconciliationValue = "example@adobe.com";
   // 3. Privacy request type
   // GDPR_REQUEST_TYPE_ACCESS = 1;
   // GDPR_REQUEST_TYPE_DELETE = 2;
   var requestType = GDPR_REQUEST_TYPE_ACCESS;
   // 4. Confirm deleting data required.
   // value : true or false
   var ConfirmDeletePending = true;
   // BEGIN
   var requestId = nms.privacyRequest.CreateRequestByName(namespaceName, reconciliationValue, requestType, ConfirmDeletePending);
   // User can use a simple queryDef with requestID as a parameter to check request status.
   ```

* If you are **migrating to 20.2** and if you were already using the API, you must add the ‘regulation’ field as shown below:

   ```
   loadLibrary("nms:gdpr.js");
   /**************************** 
   This code calls an API to create new Privay request on the DB.
   It requires 5 parameters below.
   Feel free to change parameter values.
   ****************************/
   // 1. Namespace internal name
   var namespaceName = "defaultNamespace1";
   // 2. Reconciliation value for privacy request
   var reconciliationValue = "example@adobe.com";
   // 3. Privacy request type
   // PRIVACY_REQUEST_TYPE_ACCESS = 1;
   // PRIVACY_REQUEST_TYPE_DELETE = 2;
   var requestType = PRIVACY_REQUEST_TYPE_ACCESS;
   // 4. Confirm deleting data required.
   // value : true or false
   var ConfirmDeletePending = true;
   // 5. Specify which regulation applies to newly created request. This is mandatory parameter.
   // GDPR = 1
   // CCPA = 2
   // PDPA = 3
   // LGPD = 4
   var regulation = 1;
   // BEGIN
   var requestId = nms.privacyRequest.CreateRequestByName(namespaceName, reconciliationValue, requestType, ConfirmDeletePending, regulation);
   // User can use a simple queryDef with requestID as a parameter to check request status.
   ```

* If you are **using Campaign Classic 20.2 (build 9178+) or above**, the &#39;regulation&#39; field is optional, as shown below:

   ```
   loadLibrary("nms:gdpr.js");
   /**************************** 
   This code calls an API to create new Privay request on the DB.
   It requires 5 parameters below.
   Feel free to change parameter values 
   ****************************/
   // 1. Namespace internal name
   var namespaceName = "defaultNamespace1";
   // 2. Reconciliation value for privacy request
   var reconciliationValue = "example@adobe.com";
   // 3. Privacy request type
   // PRIVACY_REQUEST_TYPE_ACCESS = 1;
   // PRIVACY_REQUEST_TYPE_DELETE = 2;
   var requestType = PRIVACY_REQUEST_TYPE_ACCESS;
   // 4. Confirm deleting data required.
   // value : true or false
   var ConfirmDeletePending = true;
   // 5. Specify which regulation applies to newly created request. This is optional parameter.
   // GDPR = 1
   // CCPA = 2
   // PDPA = 3
   // LGPD = 4
   var regulation = 1;
   // BEGIN
   var requestId = nms.privacyRequest.CreateRequestByName(namespaceName, reconciliationValue, requestType, ConfirmDeletePending, regulation);
   // User can use a simple queryDef with requestID as a parameter to check request status.
   ```

## Exclusión para la venta de información personal (CCPA) {#sale-of-personal-information-ccpa}

The **California Consumer Privacy Act** (CCPA) provides California residents new rights in regards to their personal information and imposes data protection responsibilities on certain entities whom conduct business in California.

La configuración y el uso de las solicitudes de acceso y eliminación son comunes al RGPD y a la CCPA. Esta sección presenta la exclusión de la venta de datos personales, que es específica de la CCPA.

In addition to the [Consent management](../../platform/using/privacy-management.md#consent-management) tools provided by Adobe Campaign, you have the possibility to track whether a consumer has opted-out for the sale of Personal Information.

Un consumidor decide, a través de su sistema, que no permite que su información personal se venda a un tercero. En Adobe Campaign, podrá almacenar y rastrear esta información.

For this to work, you need to extend the Profiles table and add an **[!UICONTROL Opt-Out for CCPA]** field.

>[!IMPORTANT]
>
>Como controlador de datos, es su responsabilidad recibir la solicitud del sujeto de datos y realizar un seguimiento de las fechas de solicitud para CCPA. Como proveedor de tecnología, sólo ofrecemos una manera de optar por la exclusión. Para obtener más información sobre su función como controlador de datos, consulte Datos [personales y Personas](../../platform/using/privacy-and-recommendations.md#personal-data).

### Requisito previo {#ccpa-prerequisite}

Para aprovechar esta información, debe crear este campo en Adobe Campaign Classic. Para ello, agregará un campo booleano a la **[!UICONTROL Recipient]** tabla. Cuando se crea un nuevo campo, se vuelve compatible con la API de Campaign de forma automática.

Si utiliza una tabla de destinatario personalizada, también deberá realizar esta operación.

Para más información sobre cómo crear un campo nuevo, consulte la [documentación de edición de esquema](../../configuration/using/about-schema-edition.md).

>[!IMPORTANT]
>
>La modificación de esquemas es una operación delicada que sólo deben realizar los usuarios expertos.

1. Vaya a **[!UICONTROL Tools]** > **[!UICONTROL Advanced]** > **[!UICONTROL Add new fields]**, seleccione **[!UICONTROL Recipients]** como **[!UICONTROL Document type]** y haga clic en **[!UICONTROL Next]**. For more on adding fields to a table, see [this section](../../configuration/using/new-field-wizard.md).

   ![](assets/privacy-ccpa-1.png)

1. For the **[!UICONTROL Field type]**, select **[!UICONTROL SQL field]**. Para la etiqueta, utilice **[!UICONTROL Opt-Out for CCPA]**. Seleccione el **[!UICONTROL 8-bit integer (boolean)]** tipo y defina la siguiente variable única **[!UICONTROL Relative path]**: @OPTOUTCCPA. Haga clic en **[!UICONTROL Finish]**.

   ![](assets/privacy-ccpa-2.png)

   Esto ampliará o creará el **[!UICONTROL Recipient (cus)]** esquema. Haga clic en él para comprobar que el campo se ha agregado correctamente.

   ![](assets/privacy-ccpa-3.png)

1. Haga clic en el nodo **[!UICONTROL Configuration]** > **[!UICONTROL Input forms]** del explorador. In **[!UICONTROL Recipient (nms)]**, under &quot;General Package&quot;, add an `<input>` element and use, for the xpath value, the relative path defined in step 2. For more on identifying a form, see [this section](../../configuration/using/identifying-a-form.md).

   ```
   <input  colspan="2" type="checkbox" xpath="@OPTOUTCCPA"/>
   ```

   ![](assets/privacy-ccpa-4.png)

1. Desconecte y vuelva a conectar. Siga los pasos descritos en la sección siguiente para comprobar que el campo está disponible en los detalles de un destinatario.

### Uso {#usage}

Es responsabilidad del controlador de datos llenar el valor del campo y seguir las directrices y normas de la CCPA relativas a la venta de datos.

Para rellenar estos valores, se pueden usar varios métodos:

* Uso de la interfaz de Campaign para editar los detalles del destinatario
* Utilización de la API
* a través de un flujo de trabajo de importación de datos.

A continuación, debe asegurarse de que nunca vende a terceros la información personal de los perfiles que han optado por la exclusión.

Para cambiar el estado de exclusión, vaya a **[!UICONTROL Profiles and Target]** > **[!UICONTROL Recipients]** y seleccione un destinatario. En la **[!UICONTROL General]** ficha, verá el campo configurado en la sección anterior.

![](assets/privacy-ccpa-5.png)

Configure la lista destinatarios para que muestre la columna de salida. Para obtener información sobre cómo configurar listas, consulte la documentación [](../../platform/using/adobe-campaign-workspace.md#configuring-lists)detallada.

![](assets/privacy-ccpa-6.png)

Puede hacer clic en la columna para ordenar los destinatarios según la información de exclusión. También puede crear un filtro para mostrar solo los destinatarios que han optado por no participar. For more on creating filters, see [this section](../../platform/using/creating-filters.md).

![](assets/privacy-ccpa-7.png)
