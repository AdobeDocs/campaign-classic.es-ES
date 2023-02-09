---
product: campaign
title: Proceso de solicitud de privacidad automática
description: Obtenga información sobre cómo configurar un proceso de solicitud de privacidad automática
audience: platform
content-type: reference
topic-tags: starting-with-adobe-campaign
exl-id: a93bac61-f615-4178-bc12-0f056e48687d
source-git-commit: 42b420d7dae7d38e9f4df442146d3b484c25e831
workflow-type: tm+mt
source-wordcount: '652'
ht-degree: 100%

---

# Proceso de solicitud de privacidad automática {#automatic-privacy-request-api}

![](../../assets/v7-only.svg)

Adobe Campaign proporciona una **API** que le permite configurar un proceso automático de solicitud de privacidad.

Con la API, el proceso de privacidad general es el mismo que [usar la interfaz](privacy-requests-ui.md). La única diferencia es la creación de la solicitud de privacidad. En lugar de crear la solicitud en Adobe Campaign, se envía a Campaign un POST que la contiene. Para cada solicitud, se agrega una nueva entrada en la pantalla **[!UICONTROL Privacy Requests]**. Los flujos de trabajo técnicos de privacidad procesan entonces la solicitud, tal como lo harían con una solicitud añadida mediante la interfaz.

Si utiliza la API para enviar solicitudes de privacidad, recomendamos que deje activado el **proceso de 2 pasos** para las primeras solicitudes de eliminación para probar los datos devueltos. Cuando haya terminado las pruebas, puede desactivar el procesamiento en 2 pasos para que el proceso de eliminación de solicitudes se pueda ejecutar automáticamente.

La API de JS **[!UICONTROL CreateRequestByName]** se define de la siguiente manera.

>[!NOTE]
>
>Si estaba utilizando la API **gdprRequest**, puede hacerlo, pero se recomienda utilizar la nueva API **privacyRequest**.

>[!IMPORTANT]
>
>Se requiere el **[!UICONTROL Privacy Data Right]** nombrado para utilizar la API.

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

## Llamada a la API externamente {#invoking-api-externally}

Aquí se muestra un ejemplo de cómo puede invocar la API externamente (autenticación mediante la API y detalles específicos sobre la API de privacidad). Para obtener más información sobre la API de privacidad, consulte la [documentación de la API](https://experienceleague.adobe.com/developer/campaign-api/api/s-nms-privacyRequest.html?lang=es). También puede consultar la [documentación de llamadas al servicio web](../../configuration/using/web-service-calls.md).

En primer lugar, debe realizar la autenticación mediante la API:

1. Descargue el WSDL **xtk:session** mediante esta dirección URL: **`<server url>`/nl/jsp/schemawsdl.jsp?schema=xtk:session**.

1. Utilice el método &quot;Logon&quot; y pase un nombre de usuario y una contraseña como parámetros en la solicitud. Recibirá una respuesta que contenga un token de sesión. A continuación, se muestra un ejemplo con SoapUI.

   ![](assets/do-not-localize/privacy-api.png)

1. Utilice el token de sesión devuelto como autenticación para todas las llamadas de API posteriores. Caduca a las 24 horas.

A continuación, invoque la API de privacidad:

1. Descargue el WSDL a través de esta URL: **`<server url>`/nl/jsp/schemawsdl.jsp?schema=nms:privacyRequest**.

1. Utilice **[!UICONTROL CreateRequestByName]** para crear una solicitud de privacidad específica.

   A continuación, se muestra un ejemplo con **[!UICONTROL CreateRequestByName]**. Observe cómo se utiliza el token de sesión proporcionado arriba como autenticación. La respuesta es el ID de la solicitud creada.

   ![](assets/do-not-localize/privacy-api-2.png)

   Para que pueda realizar los pasos anteriores, tenga en cuenta lo siguiente:

   * Puede utilizar **queryDef** en el esquema **nms:gdprRequest** para comprobar el estado de la solicitud de acceso.
   * Puede utilizar **queryDef** en el esquema **nms:gdprRequestData** para obtener el resultado de la solicitud de acceso.
   * Para poder descargar el archivo XML desde **&quot;$(serverUrl)&#39;/nms/gdpr.jssp?id=&#39;@id&quot;**, debe iniciar sesión y acceder desde una IP incluida en la lista de permitidos. Para ello, cree una aplicación web que le permita acceder al archivo generado por JSSP.

## Invocación de la API desde un JS {#invoking-api-from-js}

Aquí se muestra un ejemplo de cómo puede invocar la API desde un JS dentro de Campaign Classic.

>[!NOTE]
>
>El campo &quot;Regulación&quot; solo está disponible si utiliza Campaign Classic 20.2 (versión 9178+).
>
>Si migra a 20.2 y ya estaba utilizando la API, debe añadir el campo &quot;Regulación&quot;. Si está utilizando una versión anterior, puede seguir utilizando la API sin el campo &quot;regulación&quot;.

* Si está utilizando **una versión anterior (con el paquete RGPD)**, puede seguir utilizando la API sin el campo Regulación como se muestra a continuación:

   ```
   loadLibrary("nms:gdpr.js");
   /**************************** 
   This code calls an API to create new Privacy request on the DB.
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

* Si **migra a 20.2** y ya estaba utilizando la API, debe añadir el campo Regulación como se muestra a continuación:

   ```
   loadLibrary("nms:gdpr.js");
   /**************************** 
   This code calls an API to create new Privacy request on the DB.
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

* Si **utiliza Campaign Classic 20.2 (versión superior a 9178)**, el campo Regulación es opcional, como se muestra a continuación:

   ```
   loadLibrary("nms:gdpr.js");
   /**************************** 
   This code calls an API to create new Privacy request on the DB.
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
