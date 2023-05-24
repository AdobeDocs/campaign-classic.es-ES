---
product: campaign
title: API orientadas a empresa
description: API orientadas a empresa
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
feature: API
exl-id: e6638870-3141-4f12-b904-db436127c0d1
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: tm+mt
source-wordcount: '632'
ht-degree: 3%

---

# API orientadas a empresa{#business-oriented-apis}

Las API empresariales son específicas para cada tipo de objeto. Tienen un efecto en:

* Envíos:

   * Creación de una acción de entrega, consulte [SubmitDelivery (nms:delivery)](#submitdelivery--nms-delivery-),
   * envío de una campaña (inicio, pausa, parada, envío de prueba),
   * recuperando registros de envío.

* Flujos de trabajo:

   * inicio de un flujo de trabajo,
   * verificación de procesos, etc.

      Consulte [Métodos SOAP en JavaScript](../../configuration/using/soap-methods-in-javascript.md).

* Gestión de contenido
* Administración de suscripciones, consulte [Suscribirse (nms:subscription)](#subscribe--nms-subscription-) y [Cancelar suscripción (nms:subscription)](#unsubscribe--nms-subscription-).
* Procesos de datos: importaciones y exportaciones.

Esta sección detalla el uso de los servicios &quot;Suscribirse&quot;, &quot;Cancelar suscripción&quot; y &quot;SubmitDelivery&quot;.

>[!IMPORTANT]
>
>[Documentación de JSAPI de Campaign](https://experienceleague.adobe.com/developer/campaign-api/api/index.html?lang=es) contiene información adicional sobre las llamadas SOAP y el uso de Javascript en Adobe Campaign, así como una referencia completa a todos los métodos y funciones utilizados en la aplicación.

## Suscribirse (nms:subscription) {#subscribe--nms-subscription-}

Este servicio permite suscribir a un destinatario a un servicio informativo y actualizar el perfil del destinatario.

Se requieren los siguientes parámetros para llamar al servicio:

* una autenticación,
* nombre interno del servicio de suscripción,
* un documento XML que contiene la información del destinatario (del esquema &quot;nms:recipient&quot;),
* un booleano para la creación de destinatarios si aún no lo hay.

Descripción del método &quot;subscribe&quot; en el esquema &quot;nms:subscription&quot;:

```
<method name="Subscribe" static="true">
  <parameters>
     <param name="serviceName" type="string"  desc="List of information service names (comma separated)"/>
     <param name="recipient" type="DOMElement" desc="Recipient"/>
     <param name="create" type="Boolean" desc="Create recipient if it does not exist"/>
   </parameters>
</method>
```

La definición de la clave de reconciliación debe introducirse mediante _**key** en el `<recipient>` del documento XML. El contenido de este atributo es una lista XPath separada por comas.

Esta llamada no devuelve ningún dato, excepto errores.

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

## Cancelar suscripción (nms:subscription) {#unsubscribe--nms-subscription-}

Este servicio permite cancelar la suscripción de un destinatario a un servicio informativo y actualizar el perfil del destinatario.

Se requieren los siguientes parámetros para llamar al servicio:

* una autenticación,
* Nombre interno del servicio desde el que cancelar la suscripción,
* un documento XML que contiene la información del destinatario (del esquema &quot;nms:recipient&quot;),

Descripción del método &quot;Unsubscribe&quot; en el esquema &quot;nms:subscription&quot;:

```
<method name="Unsubscribe" static="true">
  <parameters>
    <param name="serviceName" type="string" desc="List of information service names (comma separated)"/>
    <param name="recipient" type="DOMElement"  desc="Recipient"/>
  </parameters>
</method>
```

La definición de la clave de reconciliación debe introducirse mediante el atributo _key en `<recipient>` del documento XML. El contenido de este atributo es una lista XPath separada por comas.

Si el destinatario no está presente en la base de datos o no está suscrito al servicio informativo en cuestión, el servicio no realiza ninguna acción y no genera un error.

>[!NOTE]
>
>Si el nombre del servicio no se especifica como parámetro, el destinatario se envía automáticamente a la lista de bloqueados (@blackList=&quot;1&quot;). El destinatario se encuentra automáticamente a la hora de la .

Esta llamada no devuelve ningún dato, excepto errores.

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

Este servicio permite crear y enviar una acción de envío.

Se requieren los siguientes parámetros para llamar al servicio:

* una autenticación,
* nombre interno de la plantilla de envíos,
* un documento XML opcional que contiene datos de envío adicionales.

No se debe llamar a esta API en el volumen, ya que puede encontrar problemas de rendimiento.

Descripción del método en su esquema:

```
<method name="SubmitDelivery" static="true">
  <parameters>
    <param name="scenarioName" type="string" inout="in" desc="Internal name of the delivery template"/>
    <param name="content" type="DOMElement"  inout="in" desc="XML content of the delivery template" />
  </parameters>
</method>
```

Se debe crear una plantilla de envíos desde la consola del cliente de Adobe Campaign. Contiene los parámetros comunes a todas las entregas (dirección del remitente o duración de validez del mensaje).

El documento XML de entrada es un fragmento de plantilla de envíos que obedece a la estructura del esquema &quot;nms:delivery&quot;. Contiene todos los datos adicionales que no se hayan podido definir estáticamente en la plantilla de envíos (por ejemplo, lista de destinatarios objetivo).

Esta llamada no devuelve ningún dato, excepto errores.

### Ejemplo de documento XML {#xml-document-example}

Este ejemplo se basa en una plantilla de envío personalizada de una fuente de datos externa (un archivo en este caso). La configuración se describe completamente en la plantilla de envíos, por lo que lo único que queda por enviar cuando se produce la llamada es el contenido del archivo desde el `<externalsource>` Elemento.

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

Si no tiene una plantilla de envíos, puede utilizar el siguiente ejemplo:

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
