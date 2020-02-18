---
title: API orientadas al negocio
seo-title: API orientadas al negocio
description: API orientadas al negocio
seo-description: null
page-status-flag: never-activated
uuid: ddb6e5cf-dfe0-4dc9-ac5b-fab21827b874
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: configuration
content-type: reference
topic-tags: api
discoiquuid: e7b3ffca-c85f-498d-89b4-23fcff59de49
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: dbff132e3bf88c408838f91e50e4b047947ee32a

---


# API orientadas al negocio{#business-oriented-apis}

La API comercial es específica para cada tipo de objeto. Tienen un efecto en:

* Entregas:

   * Creación de una acción de entrega, consulte [SubmitDelivery (nms:delivery)](#submitdelivery--nms-delivery-),
   * envío de una campaña (iniciar, pausar, detener, enviar prueba),
   * recuperación de registros de entrega.

* Flujos de trabajo:

   * inicio de un flujo de trabajo,
   * verificación de procesos, etc.

      Consulte Métodos [SOAP en JavaScript](../../configuration/using/soap-methods-in-javascript.md).

* Gestión de contenido
* Gestión de suscripciones, consulte [Suscribirse (nms:subscription)](#subscribe--nms-subscription-) y [Cancelar suscripción (nms:subscription)](#unsubscribe--nms-subscription-).
* Procesos de datos: importaciones, exportaciones.

Esta sección detalla el uso de los servicios &quot;Suscribirse&quot;, &quot;Cancelar suscripción&quot; y &quot;Enviar entrega&quot;.

>[!IMPORTANT]
>
>[La documentación](http://docs.campaign.adobe.com/doc/AC/en/jsapi/index.html) de JSAPI de campaña contiene información adicional sobre las llamadas SOAP y el uso de Javascript en Adobe Campaign, así como una referencia completa a todos los métodos y funciones utilizados en la aplicación.

## Suscribirse (nms:subscription) {#subscribe--nms-subscription-}

Este servicio le permite suscribirse a un destinatario en un servicio de información y actualizar el perfil del destinatario.

Se requieren los siguientes parámetros para llamar al servicio:

* una autenticación,
* nombre interno del servicio de suscripción,
* un documento XML que contiene la información del destinatario (del esquema &quot;nms:destination&quot;),
* un valor booleano para la creación de destinatarios si no hay ninguno.

Descripción del método &quot;subscription&quot; en el esquema &quot;nms:subscription&quot;:

```
<method name="Subscribe" static="true">
  <parameters>
     <param name="serviceName" type="string"  desc="List of information service names (comma separated)"/>
     <param name="recipient" type="DOMElement" desc="Recipient"/>
     <param name="create" type="Boolean" desc="Create recipient if it does not exist"/>
   </parameters>
</method>
```

La definición de la clave de reconciliación debe introducirse mediante el atributo _**key** en el `<recipient>` elemento del documento XML. El contenido de este atributo es una lista XPath separada por comas.

Esta llamada no devuelve datos, excepto errores.

### Ejemplos {#examples}

Suscripción con clave de reconciliación del destinatario en la dirección de correo electrónico: el documento XML de entrada debe hacer referencia a la dirección de correo electrónico y a la definición de la clave en este campo.

```
<recipient _key="email" email= "john.doe@adobe.com"/>
```

Actualizando el destinatario y la suscripción.

```
<recipient _key="email, [folder-id]" email= "john.doe@adobe.com" folder-id="1305" firstName="John" lastName="Doe"/>
```

### Ejemplo de mensajes SOAP {#example-of-soap-messages}

* Consulta:

   ```
   <?xml version='1.0' encoding='ISO-8859-1'?>
   <SOAP-ENV:Envelope xmlns:xsd='http://www.w3.org/2001/XMLSchema' xmlns:xsi='http://www.w3.org/2001/XMLSchema-instance' xmlns:SOAP-ENV='http://schemas.xmlsoap.org/soap/envelope/'>
     <SOAP-ENV:Body>
       <m:Subscribe xmlns:m='urn:nms:subscription' SOAP-ENV:encodingStyle='http://schemas.xmlsoap.org/soap/encoding/'>
         <sessiontoken xsi:type='xsd:string'/>
         <service xsi:type='xsd:string'>SVC1</service>
         <content xsi:type='' SOAP-ENV:encodingStyle='http://xml.apache.org/xml-soap/literalxml'>
           <recipient _key="@email" email= "john.doe@adobe.com/>
         </content>
         <create xsi:type='xsd:boolean'>true</create>
       </m:Subscribe>
     </SOAP-ENV:Body>
   </SOAP-ENV:Envelope>
   ```

* Respuesta:

   ```
   <?xml version='1.0' encoding='ISO-8859-1'?>
   <SOAP-ENV:Envelope xmlns:xsd='http://www.w3.org/2001/XMLSchema' xmlns:xsi='http://www.w3.org/2001/XMLSchema-instance' xmlns:ns='http://xml.apache.org/xml-soap' xmlns:SOAP-ENV='http://schemas.xmlsoap.org/soap/envelope/'>
     <SOAP-ENV:Body>
       <m:SubscribeResponse xmlns:m='urn:nms:subscription' SOAP-ENV:encodingStyle='http://schemas.xmlsoap.org/soap/encoding/'>
       </m:SubscribeResponse>
     </SOAP-ENV:Body>
   </SOAP-ENV:Envelope>
   ```

## Cancelar suscripción (nms:subscription) {#unsubscribe--nms-subscription-}

Este servicio le permite cancelar la suscripción de un destinatario de un servicio de información y actualizar el perfil del destinatario.

Se requieren los siguientes parámetros para llamar al servicio:

* una autenticación,
* Nombre interno del servicio del que se va a cancelar la suscripción,
* un documento XML que contiene la información del destinatario (del esquema &quot;nms:destination&quot;),

Descripción del método &quot;Cancelar suscripción&quot; en el esquema &quot;nms:subscription&quot;:

```
<method name="Unsubscribe" static="true">
  <parameters>
    <param name="serviceName" type="string" desc="List of information service names (comma separated)"/>
    <param name="recipient" type="DOMElement"  desc="Recipient"/>
  </parameters>
</method>
```

La definición de la clave de reconciliación debe introducirse mediante el atributo _key en el `<recipient>` elemento del documento XML. El contenido de este atributo es una lista XPath separada por comas.

Si el destinatario no está presente en la base de datos o no está suscrito al servicio de información correspondiente, el servicio no realiza ninguna acción ni genera un error.

>[!NOTE]
>
>Si el nombre del servicio no se especifica como parámetro, el destinatario se bloquea automáticamente (@blackList=&quot;1&quot;).

Esta llamada no devuelve datos, excepto errores.

### Ejemplo de mensajes SOAP {#example-of-soap-messages-1}

Consulta:

```
<?xml version='1.0' encoding='ISO-8859-1'?>
<SOAP-ENV:Envelope xmlns:xsd='http://www.w3.org/2001/XMLSchema' xmlns:xsi='http://www.w3.org/2001/XMLSchema-instance' xmlns:SOAP-ENV='http://schemas.xmlsoap.org/soap/envelope/'>
  <SOAP-ENV:Body>
    <m:Unsubscribe xmlns:m='urn:nms:subscription' SOAP-ENV:encodingStyle='http://schemas.xmlsoap.org/soap/encoding/'>
    <sessiontoken xsi:type='xsd:string'/>
    <service xsi:type='xsd:string'>SVC1</service>
    <content xsi:type='' SOAP-ENV:encodingStyle='http://xml.apache.org/xml-soap/literalxml'>
      <recipient _key="@email" email= "john.doe@adobe.com/>
    </content>
  </m:Unsubscribe>
</SOAP-ENV:Body>
```

Respuesta:

```
<?xml version='1.0' encoding='ISO-8859-1'?>
<SOAP-ENV:Envelope xmlns:xsd='http://www.w3.org/2001/XMLSchema' xmlns:xsi='http://www.w3.org/2001/XMLSchema-instance' xmlns:ns='http://xml.apache.org/xml-soap' xmlns:SOAP-ENV='http://schemas.xmlsoap.org/soap/envelope/'>
  <SOAP-ENV:Body>
    <m:UnsubscribeResponse xmlns:m='urn:nms:subscription' SOAP-ENV:encodingStyle='http://schemas.xmlsoap.org/soap/encoding/'>
    </m:UnsubscribeResponse>
  </SOAP-ENV:Body>
</SOAP-ENV:Envelope>
```

## SubmitDelivery (nms:delivery) {#submitdelivery--nms-delivery-}

Este servicio le permite crear y enviar una acción de entrega.

Se requieren los siguientes parámetros para llamar al servicio:

* una autenticación,
* nombre interno de la plantilla de entrega,
* un documento XML opcional que contiene datos de envío adicionales.

No se debe llamar a esta API por volumen, ya que puede encontrar problemas de rendimiento.

Descripción del método en su esquema:

```
<method name="SubmitDelivery" static="true">
  <parameters>
    <param name="scenarioName" type="string" inout="in" desc="Internal name of the delivery template"/>
    <param name="content" type="DOMElement"  inout="in" desc="XML content of the delivery template" />
  </parameters>
</method>
```

Se debe crear una plantilla de entrega desde la consola de cliente de Adobe Campaign. Contiene los parámetros comunes a todas las entregas (dirección del remitente o duración de validez del mensaje).

El documento XML de entrada es un fragmento de plantilla de entrega que obedece a la estructura del esquema &quot;nms:delivery&quot;. Contiene todos los datos adicionales que no se pudieron definir de forma estática en la plantilla de envío (por ejemplo, la lista de destinatarios a los que se va a dirigir).

Esta llamada no devuelve datos, excepto errores.

### Ejemplo de documento XML {#xml-document-example}

Este ejemplo se basa en una plantilla de entrega personalizada de un origen de datos externo (un archivo en este caso). La configuración se describe completamente en la plantilla de envío, de modo que todo lo que queda por enviar cuando se produce la llamada es el contenido del archivo del `<externalsource>` elemento.

```
<delivery>
  <targets fromExternalSource="true">
    <externalSource>
      MsgId|ClientId|Title|Name|FirstName| Mobile|Email| Market_segment|Product_affinity1 |Product_affinity2|Product_affinity3| Product_affinity4| Support_Number|Amount|Threshold1|000001234|M.| Doe|John|0650201020| john.doe@adobe.com
|1| A1|A2|A3|A4|E12|120000|100000
    </externalSource>
  </target>
</delivery>
```

Si no tiene una plantilla de entrega, puede utilizar el siguiente ejemplo:

```
<delivery>
<targets fromExternalSource="true" targetMode="1" noReconciliation="true" addressField="Email" >  
    <fileFormat active="true">  
      <source format="text" type="text">  
        <dataSourceConfig >  
          <dataSourceColumn label="Email" name="Email" type="string"/>  
        </dataSourceConfig>  
      </source>  
      <destination type="xtkDataStore"/>  
    </fileFormat>  
    <externalSource><![CDATA[not-a-repicipient@domain.com]]></externalSource>  
  </targets> 
</delivery> 
```

