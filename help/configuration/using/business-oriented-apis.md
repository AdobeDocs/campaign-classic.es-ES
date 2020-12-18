---
solution: Campaign Classic
product: campaign
title: API orientadas al negocio
description: API orientadas al negocio
audience: configuration
content-type: reference
topic-tags: api
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '635'
ht-degree: 3%

---


# API orientadas al negocio{#business-oriented-apis}

La API comercial es específica para cada tipo de objeto. Tienen un efecto en:

* Entregas:

   * Creación de una acción de envío, consulte [SubmitDelivery (nms:envío)](#submitdelivery--nms-delivery-),
   * enviar una campaña (inicio, pausa, parada, enviar prueba),
   * recuperar registros de envío.

* Flujos de trabajo:

   * inicio de un flujo de trabajo,
   * verificación de procesos, etc.

      Consulte [Métodos SOAP en JavaScript](../../configuration/using/soap-methods-in-javascript.md).

* Gestión de contenido
* Administración de suscripciones, consulte [Suscribirse (nms:suscripción)](#subscribe--nms-subscription-) y [Cancelar suscripción (nms:suscripción)](#unsubscribe--nms-subscription-).
* Procesos de datos: importaciones, exportaciones.

Esta sección detalla el uso de los servicios &quot;Suscribirse&quot;, &quot;Cancelar suscripción&quot; y &quot;Enviar entrega&quot;.

>[!IMPORTANT]
>
>[La ](https://docs.adobe.com/content/help/en/campaign-classic/technicalresources/api/index.html) documentación de JSAPI de campaña contiene información adicional sobre las llamadas SOAP y el uso de Javascript en Adobe Campaign, así como una referencia completa a todos los métodos y funciones utilizados en la aplicación.

## Suscripción (nms:suscripción) {#subscribe--nms-subscription-}

Este servicio le permite suscribirse a un destinatario en un servicio informativo y actualizar el perfil de destinatario.

Se requieren los siguientes parámetros para llamar al servicio:

* una autenticación,
* nombre interno del servicio de suscripción,
* un documento XML que contiene la información de destinatario (del esquema &quot;nms:destinatario&quot;),
* un booleano para la creación de destinatarios si no hay uno.

Descripción del método &quot;subscription&quot; en el esquema &quot;nms:suscripción&quot;:

```
<method name="Subscribe" static="true">
  <parameters>
     <param name="serviceName" type="string"  desc="List of information service names (comma separated)"/>
     <param name="recipient" type="DOMElement" desc="Recipient"/>
     <param name="create" type="Boolean" desc="Create recipient if it does not exist"/>
   </parameters>
</method>
```

La definición de la clave de reconciliación debe introducirse mediante el atributo _**key** en el elemento `<recipient>` del documento XML. El contenido de este atributo es una lista XPath separada por comas.

Esta llamada no devuelve datos, excepto errores.

### Ejemplos {#examples}

Suscripción con clave de reconciliación de destinatario en la dirección de correo electrónico: el documento XML de entrada debe hacer referencia a la dirección de correo electrónico y a la definición de la clave en este campo.

```
<recipient _key="email" email= "john.doe@adobe.com"/>
```

Actualización del destinatario y de la suscripción.

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

## Cancelar suscripción (nms:suscripción) {#unsubscribe--nms-subscription-}

Este servicio le permite cancelar la suscripción de un destinatario de un servicio informativo y actualizar el perfil de destinatario.

Se requieren los siguientes parámetros para llamar al servicio:

* una autenticación,
* Nombre interno del servicio del que se va a cancelar la suscripción,
* un documento XML que contiene la información de destinatario (del esquema &quot;nms:destinatario&quot;),

Descripción del método &quot;Cancelar suscripción&quot; en el esquema &quot;nms:suscripción&quot;:

```
<method name="Unsubscribe" static="true">
  <parameters>
    <param name="serviceName" type="string" desc="List of information service names (comma separated)"/>
    <param name="recipient" type="DOMElement"  desc="Recipient"/>
  </parameters>
</method>
```

La definición de la clave de reconciliación debe introducirse mediante el atributo _key en el elemento `<recipient>` del documento XML. El contenido de este atributo es una lista XPath separada por comas.

Si el destinatario no está presente en la base de datos o no está suscrito al servicio informativo correspondiente, el servicio no realiza ninguna acción y no genera un error.

>[!NOTE]
>
>Si el nombre del servicio no se especifica como parámetro, el destinatario se mostrará automáticamente en lista de bloqueados (@blackList=&quot;1&quot;).

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

## SubmitDelivery (nms:envío) {#submitdelivery--nms-delivery-}

Este servicio le permite crear y enviar una acción de envío.

Se requieren los siguientes parámetros para llamar al servicio:

* una autenticación,
* nombre interno de la Plantilla de envíos,
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

Se debe crear una Plantilla de envíos desde la consola cliente de Adobe Campaign. Contiene los parámetros comunes a todos los envíos (dirección del remitente o duración de validez del mensaje).

El documento XML de entrada es un fragmento de Plantilla de envíos que obedece a la estructura del esquema &quot;nms:envío&quot;. Contendrá todos los datos adicionales que no pudieron definirse estáticamente en la Plantilla de envíos (por ejemplo, la lista de destinatarios al destinatario).

Esta llamada no devuelve datos, excepto errores.

### Ejemplo de documento XML {#xml-document-example}

Este ejemplo se basa en una Plantilla de envíos personalizada de un origen de datos externo (un archivo en este caso). La configuración se describe completamente en la Plantilla de envíos, de modo que todo lo que queda por enviar cuando se produce la llamada es el contenido del archivo del elemento `<externalsource>`.

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

Si no tiene una Plantilla de envíos, puede utilizar el siguiente ejemplo:

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

