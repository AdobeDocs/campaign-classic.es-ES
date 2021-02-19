---
solution: Campaign Classic
product: campaign
title: Acerca de los servicios Web
description: Acerca de los servicios Web
audience: configuration
content-type: reference
topic-tags: api
translation-type: tm+mt
source-git-commit: c625b4109e2cb47446331cd009ff9827c8267c93
workflow-type: tm+mt
source-wordcount: '658'
ht-degree: 5%

---


# Acerca de los servicios Web{#about-web-services}

## Definición de las API de Adobe Campaign {#definition-of-adobe-campaign-apis}

El servidor de aplicaciones de Adobe Campaign fue diseñado para la apertura y la fácil integración con sistemas de información de compañía cada vez más diversos y complejos.

Las API de Adobe Campaign se utilizan en JavaScript dentro de la aplicación y en SOAP fuera de ella. Constituyen una biblioteca de funciones genéricas que se pueden enriquecer. Para obtener más información, consulte [Implementación de métodos SOAP](../../configuration/using/implementing-soap-methods.md).

>[!IMPORTANT]
>
>El número de llamadas al motor autorizadas por día varía según el contrato de licencia. Para obtener más información, consulte [esta página](https://helpx.adobe.com/legal/product-descriptions/adobe-campaign-classic---product-description.html).\
>En [esta documentación dedicada](https://docs.adobe.com/content/help/en/campaign-classic/technicalresources/api/index.html) encontrará una lista de todas las API, incluida su descripción completa.

## Requisitos previos {#prerequisites}

Antes de usar las API de Adobe Campaign, debe conocer los siguientes temas:

* Javascript
* Protocolo SOAP
* Modelo de datos de Adobe Campaign

## Uso de las API de Adobe Campaign {#using-adobe-campaign-apis}

Adobe Campaign utiliza dos tipos de API:

* API de acceso a datos genéricos para consultar los datos del modelo de datos. Consulte [API orientadas a datos](../../configuration/using/data-oriented-apis.md).
* API empresariales específicas que le permiten actuar en cada objeto: envíos, flujos de trabajo, suscripciones, etc. Consulte [API orientadas al negocio](../../configuration/using/business-oriented-apis.md).

Para desarrollar API e interactuar con Adobe Campaign, debe estar familiarizado con su modelo de datos. Adobe Campaign permite generar una descripción completa de la base. Consulte [Descripción del modelo](../../configuration/using/data-oriented-apis.md#description-of-the-model).

## Llamadas SOAP {#soap-calls}

El protocolo SOAP permite invocar métodos de API mediante el cliente enriquecido, aplicaciones de terceros que utilizan servicios Web o JSP que utilizan estos métodos de forma nativa.

![](assets/s_ncs_configuration_architecture.png)

La estructura de un mensaje SOAP es la siguiente:

* un sobre que defina la estructura del mensaje,
* un encabezado opcional,
* un organismo que contenga la información sobre la llamada y la respuesta,
* administración de errores que define la condición de error.

## Recursos e intercambios {#resources-and-exchanges}

El siguiente esquema muestra los distintos recursos involucrados en el uso de las API de Adobe Campaign:

![](assets/s_ncs_integration_webservices_schema_pres.png)

## Ejemplo de un mensaje SOAP en el método &#39;ExecuteQuery&#39; {#example-of-a-soap-message-on-the--executequery--method--}

En este ejemplo, una consulta SOAP invoca el método &quot;ExecuteQuery&quot;, que toma una cadena de caracteres como parámetro para la autenticación (token de sesión) y un contenido XML para la descripción de la consulta que se va a ejecutar.

Para obtener más información, consulte [ExecuteQuery (xtk:queryDef)](../../configuration/using/data-oriented-apis.md#executequery--xtk-querydef-).

>[!NOTE]
>
>La descripción WSDL de este servicio se completa en el ejemplo que se muestra a continuación: [Descripción del servicio Web: WSDL](../../configuration/using/web-service-calls.md#web-service-description--wsdl).

### CONSULTA SOAP {#soap-query}

```
<?xml version='1.0' encoding='ISO-8859-1'?>
  <SOAP-ENV:Envelope xmlns:xsd='http://www.w3.org/2001/XMLSchema' xmlns:xsi='http://www.w3.org/2001/XMLSchema-instance' xmlns:ns='http://xml.apache.org/xml-soap' xmlns:SOAP-ENV='http://schemas.xmlsoap.org/soap/envelope/'>
    <SOAP-ENV:Body>
      <ExecuteQuery xmlns='urn:xtk:queryDef' SOAP-ENV:encodingStyle='http://schemas.xmlsoap.org/soap/encoding/'>
        <__sessiontoken xsi:type='xsd:string'/>
        <entity xsi:type='ns:Element' SOAP-ENV:encodingStyle='http://xml.apache.org/xml-soap/literalxml'>
          <queryDef firstRows="true" lineCount="200" operation="select" schema="nms:rcpGrpRel" startLine="0" startPath="/" xtkschema="xtk:queryDef">
          ...
          </queryDef>
        </entity>
      </ExecuteQuery>
  </SOAP-ENV:Body>
</SOAP-ENV:Envelope>
```

El elemento `<soap-env:envelope>` es el primer elemento del mensaje que representa el sobre SOAP.

El elemento `<soap-env:body>` es el primer elemento secundario del sobre. Contiene la descripción del mensaje, es decir, el contenido de la consulta o la respuesta.

El método que se va a invocar se introduce en el elemento `<executequery>` del cuerpo del mensaje SOAP.

En SOAP, los parámetros se reconocen por orden de aspecto. El primer parámetro, `<__sessiontoken>`, toma la cadena de autenticación, el segundo parámetro es la descripción XML de la consulta del elemento `<querydef>`.

### Respuesta SOAP {#soap-response}

```
<?xml version='1.0' encoding='ISO-8859-1'?>
  <SOAP-ENV:Envelope xmlns:xsd='http://www.w3.org/2001/XMLSchema' xmlns:xsi='http://www.w3.org/2001/XMLSchema-instance' xmlns:ns='http://xml.apache.org/xml-soap' xmlns:SOAP-ENV='http://schemas.xmlsoap.org/soap/envelope/'>
    <SOAP-ENV:Body>
      <ExecuteQueryResponse xmlns='urn:xtk:queryDef' SOAP-ENV:encodingStyle='http://schemas.xmlsoap.org/soap/encoding/'>
        <pdomOutput xsi:type='ns:Element' SOAP-ENV:encodingStyle='http://xml.apache.org/xml-soap/literalxml'>
          <rcpGrpRel-collection><rcpGrpRel group-id="1872" recipient-id="1362"></rcpGrpRel></rcpGrpRel-collection>
        </pdomOutput>
      </ExecuteQueryResponse>
    </SOAP-ENV:Body>
</SOAP-ENV:Envelope>
```

El resultado de la consulta se introduce desde el elemento `<pdomoutput>`.

## Gestión de errores {#error-management}

Ejemplo de respuesta de error SOAP:

```
<?xml version='1.0' encoding='ISO-8859-1'?>
<SOAP-ENV:Envelope xmlns:SOAP-ENV='http://schemas.xmlsoap.org/soap/envelope/'>
  <SOAP-ENV:Body>
    <SOAP-ENV:Fault>
      <faultcode>SOAP-ENV:Server</faultcode>
      <faultstring>Error while executing 'Write' of the 'xtk:persist'.</faultstring> service
      <detail>ODBC error: [Microsoft][ODBC SQL Server Driver][SQL Server]Cannot insert duplicate key row in object 'XtkOption' with unique index 'XtkOption_name'. SQLSTate: 23000
ODBC error: [Microsoft][ODBC SQL Server Driver][SQL Server]The statement has been terminated. SQLSTate: 01000 Cannot save the 'Options (xtk:option)' document </detail>
    </SOAP-ENV:Fault>
  </SOAP-ENV:Body>
</SOAP-ENV:Envelope>
```

El elemento `<soap-env:fault>` del cuerpo del mensaje SOAP se utiliza para transmitir las señales de error que surgen durante el procesamiento del servicio Web. Se compone de los siguientes subelementos:

* `<faultcode>` :: indica el tipo de error. Los tipos de error son:

   * &quot;VersionMismatch&quot; en el evento de incompatibilidad con la versión de SOAP utilizada,
   * &quot;MustUnderstanding&quot; en el evento de un problema en el encabezado del mensaje,
   * &quot;Cliente&quot; en el evento de que el cliente carece de información,
   * &quot;Servidor&quot; en el evento de que el servidor tiene un problema al ejecutar el procesamiento.

* `<faultstring>` :: mensaje que describe el error
* `<detail>` :: mensaje de error largo

El éxito o error de la invocación del servicio se identifica cuando se verifica el elemento `<faultcode>`.

>[!IMPORTANT]
>
>Todos los servicios Web de Adobe Campaign gestionan errores. Por lo tanto, se recomienda encarecidamente probar cada llamada para controlar los errores devueltos.

Ejemplo de gestión de errores en C#:

```
try 
{
  // Invocation of method
  ...
}
catch (SoapException e)
{
  System.Console.WriteLine("Soap exception: " + e.Message);        
  if (e.Detail != null)
    System.Console.WriteLine(e.Detail.InnerText);
}
```

## Dirección URL del servidor de servicios Web (o EndPoint) {#url-of-web-service-server--or-endpoint-}

Para enviar el servicio Web, debe ponerse en contacto con el servidor de Adobe Campaign que implementa el método de servicio correspondiente.

La dirección URL del servidor es la siguiente:

https://serverName/nl/jsp/soaprouter.jsp

Con **`<server>`** el servidor de aplicaciones de Adobe Campaign (**nlserver web**).
