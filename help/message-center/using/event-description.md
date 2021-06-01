---
product: campaign
title: Descripción del evento
description: Descubra cómo se administran los eventos de mensajería transaccional en Adobe Campaign Classic mediante los métodos SOAP.
audience: message-center
content-type: reference
topic-tags: introduction
exl-id: 9f7f4b6c-2ee8-4091-847d-f616d6abeb6b
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: tm+mt
source-wordcount: '751'
ht-degree: 94%

---

# Descripción del evento {#event-description}

## Modelo de datos de mensajería transaccional {#about-transactional-messaging-datamodel}

La mensajería transaccional se basa en el modelo de datos de Adobe Campaign y utiliza dos tablas independientes adicionales. Estas [tablas](../../configuration/using/data-model-description.md#message-center-module), **NmsRtEvent** y **NmsBatchEvent** contienen los mismos campos y permiten administrar eventos en tiempo real por un lado y eventos por lotes por otro.

## Métodos SOAP {#soap-methods}

Esta sección detalla los métodos SOAP asociados a los esquemas de módulos de mensajes transaccionales.

Dos métodos SOAP **PushEvent** o **PushEvents** están vinculados a los dos esquemas de datos **nms:rtEvent** y **nms:BatchEvent**. Es el sistema de información el que determina si un evento es de tipo “por lotes” o en “tiempo real”.

* **PushEvent** le permite insertar un solo evento en el mensaje,
* **PushEvents** le permite insertar una serie de eventos en el mensaje.

La ruta WSDL para acceder a ambos métodos es:

* **http://hostname/nl/jsp/schemawsdl.jsp?schema=nms:rtEvent** para acceder al esquema de tipo en tiempo real.
* **http://hostname/nl/jsp/schemawsdl.jsp?schema=nms:batchEvent** para acceder al esquema de tipo por lote.

Ambos métodos contienen un elemento **`<urn:sessiontoken>`** para iniciar sesión en el módulo de mensajes transaccionales. Se recomienda utilizar un método de identificación a través de direcciones IP de confianza. Para recuperar el símbolo de sesión, realice una llamada SOAP de inicio de sesión y obtenga el autentificador seguido de un cierre de sesión. Utilice el mismo símbolo para varias llamadas de RT. Los ejemplos incluidos en esta sección utilizan el método de símbolo de sesión, que es el recomendado.

Si utiliza un servidor balanceador de carga, puede utilizar la autenticación Usuario/Contraseña (en el nivel del mensaje RT). Ejemplo:

```
<PushEvent xmlns="urn:nms:rtEvent">
<sessiontoken>mc/PASSWORD</sessiontoken>
<domEvent>
<rtEvent wishedChannel="41" type="rt_MobileJourney_iOS_Push" registrationToken="c3ddc8aaecc24822df25d0f49865cca61ea3f86c61bfa53ae4d37294e37f4a1c" hashlpId="27EE7571EC14DBA23B9B5CC0EF79BB782DAECF4C03C88E5D92CC9B9DAC4E5DDA" correlationId="415b7593-4f6f-e911-811f-00505691247c" xmlns="">
<mobileApp uuid="236B24DC-C073-412F-8BCB-AC7207096258" _operation="none"/>
<ctx>...</ctx>
</rtEvent>
</domEvent>
</PushEvent>
```

El método **PushEvent** está formado por un parámetro **`<urn:domevent>`** que contiene el evento.

El método **PushEvents** está formado por un parámetro **`<urn:domeventcollection>`** que contiene eventos.

Ejemplo con PushEvent:

```
<urn:PushEvent>

 <sessiontoken>___921f9b38-72ac-49ad-b481-ab32973efc50</sessiontoken>
 
 <urn:domEvent>
 
   <rtEvent>
   
   ...
   
   </rtEvent>
 
 </urn:domEvent>

</urn:PushEvent>
```

>[!NOTE]
>
>En caso de una llamada al método **PushEvents**, se debe añadir un elemento XML principal para cumplir con el XML estándar. Este elemento XML crea los diversos elementos **`<rtevent>`** contenidos en el evento.

Ejemplo con PushEvents:

```
<urn:PushEvents>

 <sessiontoken>___921f9b38-72ac-49ad-b481-ab32973efc50</sessiontoken>
 
 <urn:domEventCollection>
 
   <Events>
   
     <rtEvent>... </rtEvent>
     
     <rtEvent>... </rtEvent>
     
     ...
   
   </Events>
 
 </urn:domEventCollection>

</urn:PushEvents>
```

Los elementos **`<rtevent>`** y **`<batchevent>`** tienen un conjunto de atributos así como un elemento secundario obligatorio: **`<ctx>`** para integrar datos de mensajes.

>[!NOTE]
>
>El elemento **`<batchevent>`** permite añadir el evento a la cola “por lotes”. El elemento **`<rtevent>`** añade el evento a la cola “en tiempo real”.

Los atributos obligatorios de los elementos **`<rtevent>`** y **`<batchevent>`** son @type y @email. El valor de @type debe ser el mismo que el valor de la lista desglosada definido al configurar la instancia de ejecución. Este valor permite definir la plantilla que se va a vincular al contenido del evento durante la entrega.

`<rtevent> configuration example:`

```
<rtEvent type="order_confirmation" email="john.doe@domain.com" origin="eCommerce" wishedChannel="0" externalId="1242" mobilePhone="+33620202020"> 
```

En este ejemplo se ofrecen dos canales: la dirección de correo electrónico y el número de teléfono móvil. **wishedChannel** permite seleccionar el canal que se desea utilizar al transformar el evento en un mensaje. El valor “0” corresponde al canal de correo electrónico, el valor “1” al canal móvil, etc.

Si desea posponer una entrega de eventos, añada el campo **[!UICONTROL scheduled]** seguido de la fecha preferida. El evento se transforma en un mensaje en esta fecha.

Se recomienda rellenar los atributos @wishedChannel y @emailFormat con valores numéricos. La tabla de funciones que vincula los valores numéricos y las etiquetas se encuentra en la descripción del esquema de datos.

>[!NOTE]
>
>Una descripción detallada de todos los atributos autorizados, así como sus valores, están disponibles en la descripción del esquema de datos **nms:rtEvent** y **nms:BatchEvent**.

El elemento **`<ctx>`** contiene los datos del mensaje. Su contenido XML está abierto, lo que significa que se puede configurar según el contenido que se va a enviar.

>[!NOTE]
>
>Es importante optimizar el número y el tamaño de los nodos XML contenidos en el mensaje para evitar sobrecargar los servidores durante la entrega.

Ejemplo de datos:

```
   <ctx>
               <client>
                        <firstname>John</firstname>
                        <lastname>Doe</lastname>
               </client>
               <action>
                         <type>Order confirmation</type>
                          <number>CN23453</number>
               </action>
               <orderdetails>
                          <article num="1">
                                   <name>Generic USB key</name>
                                   <price>20</price>
                           </article>
               </orderdetails>
    </ctx>
```

## Información devuelta por la llamada SOAP {#information-returned-by-the-soap-call}

Cuando recibe un evento, Adobe Campaign genera un ID de retorno único. Este es el ID de la versión archivada del evento.

>[!IMPORTANT]
>
>Al recibir llamadas SOAP, Adobe Campaign verifica el formato de dirección de correo electrónico. Si una dirección de correo electrónico tiene formato incorrecto, se devuelve un error.

* Ejemplo de un identificador devuelto por el método cuando el procesamiento de eventos es exitoso:

   ```
   <SOAP-ENV:Envelope xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:ns="http://xml.apache.org/xml-soap" xmlns:SOAP-ENV="http://schemas.xmlsoap.org/soap/envelope/">
      <SOAP-ENV:Body>
         <urn:PushEventResponse SOAP-ENV:encodingStyle="http://schemas.xmlsoap.org/soap/encoding/" xmlns:urn="urn:nms:rtEvent">
            <plId xsi:type="xsd:long">72057594037935966</plId>
         </urn:PushEventResponse>
      </SOAP-ENV:Body>
   </SOAP-ENV:Envelope>
   ```

Si el valor del identificador devuelto es estrictamente mayor que cero, significa que el evento se ha archivado correctamente en Adobe Campaign.

Sin embargo, si no se puede procesar el evento, el método devuelve un mensaje de error o un valor igual a cero.

* Ejemplo de proceso de un evento que falla cuando la consulta no contiene un inicio de sesión o el operador especificado no tiene los derechos requeridos:

   ```
   <SOAP-ENV:Envelope xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:SOAP-ENV="http://schemas.xmlsoap.org/soap/envelope/">
      <SOAP-ENV:Body>
         <SOAP-ENV:Fault>
            <faultcode>SOAP-ENV:Client</faultcode>
            <faultstring xsi:type="xsd:string">Error while reading parameters of method 'PushEvent' of service 'nms:rtEvent'.</faultstring>
            <detail xsi:type="xsd:string">Invalid login or password. Connection denied.</detail>
         </SOAP-ENV:Fault>
      </SOAP-ENV:Body>
   </SOAP-ENV:Envelope>
   ```

* Ejemplo de un evento que ha fallado debido a un error en la consulta (la clasificación XML no se cumple):

   ```
   <SOAP-ENV:Envelope xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:SOAP-ENV="http://schemas.xmlsoap.org/soap/envelope/">
      <SOAP-ENV:Body>
         <SOAP-ENV:Fault>
            <faultcode>SOAP-ENV:Client</faultcode>
            <faultstring xsi:type="xsd:string">The XML SOAP message is invalid (service 'PushEvent', method 'nms:rtEvent').</faultstring>
            <detail xsi:type="xsd:string"><![CDATA[(16:8) : Expected end of tag 'rtevent'
   Error while parsing XML string '<soapenv:Envelope xmlns:soapenv="http://schemas.xmlsoap.org/soap/envelope/" xmlns:urn="urn:nms:rtEvent">
      <soapenv:Header/>
      <soapenv:Body>
         <urn:PushEvent>
            <urn:sessiontoken>mc/</urn:sessiontoken>
            <urn:domEvent>
   <rtevent type="create_account" email="esther.hall@adobe.com" origin="eCommerce" wishedChannel="email" 
         externalId="1596" language="english" country="EN" emailFormat="2"
         mobilePhone="+447700123123">
     <ctx>
      <website name="eCommerce" url="http://www.eCo']]></detail>
         </SOAP-ENV:Fault>
      </SOAP-ENV:Body>
   </SOAP-ENV:Envelope>
   ```

* Ejemplo de un evento que ha fallado y devuelto un identificador cero (nombre de método incorrecto):

   ```
   <SOAP-ENV:Envelope xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:ns="http://xml.apache.org/xml-soap" xmlns:SOAP-ENV="http://schemas.xmlsoap.org/soap/envelope/">
      <SOAP-ENV:Body>
         <urn:PushEventResponse SOAP-ENV:encodingStyle="http://schemas.xmlsoap.org/soap/encoding/" xmlns:urn="urn:nms:rtEvent">
            <plId xsi:type="xsd:long">0</plId>
         </urn:PushEventResponse>
      </SOAP-ENV:Body>
   </SOAP-ENV:Envelope>
   ```
