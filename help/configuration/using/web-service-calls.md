---
solution: Campaign Classic
product: campaign
title: Llamadas al servicio Web
description: Llamadas al servicio Web
audience: configuration
content-type: reference
topic-tags: api
translation-type: tm+mt
source-git-commit: c366326f6a439dabaa42fdd799ec2e55c180a929
workflow-type: tm+mt
source-wordcount: '951'
ht-degree: 1%

---


# Llamadas al servicio Web{#web-service-calls}

## Información general {#general-information}

Todos los métodos de API se presentan en forma de servicios Web. Esto le permite administrar todas las funciones de Adobe Campaign mediante llamadas SOAP, que son el punto de entrada nativo del servidor de aplicaciones de Adobe Campaign. La consola de Adobe Campaign solo utiliza llamadas SOAP.

Los servicios Web permiten crear muchas aplicaciones a partir de un sistema de terceros:

* Alertas sincrónicas, notificaciones y ejecución de Plantillas de envíos en tiempo real desde un back-office o sistema de transacciones,
* Desarrollo de interfaces especiales con funcionalidad simplificada (interfaces Web, etc.),
* Alimentación y búsqueda de datos en la base de datos mientras se observan las reglas comerciales y se mantienen aisladas del modelo físico subyacente.

## Definición de servicios Web {#definition-of-web-services}

La definición de los servicios Web implementados en el servidor de aplicaciones de Adobe Campaign está disponible en los esquemas de datos.

Un servicio Web se describe en la gramática de los esquemas de datos y está disponible en el elemento **`<methods>`**.

```
<methods>
  <method name="GenerateForm" static="true">
    <help>Generates the form in Mail or Web mode</help>
    <parameters>
      <param name="formName" type="string" desc="Name of form"/>
      <param name="mailMode" type="boolean" desc="Generate a form of type Mail"/>
      <param name="result" type="string" inout="out" desc="Result "/>
    </parameters>
  </method>
</methods>
```

Aquí tenemos un ejemplo de la definición del método llamado **GenerateForm**.

Descripción de los inicios de servicio con el elemento `<method>`. La lista de los parámetros del método se completa desde el elemento `<parameters>`. Cada parámetro se especifica con un nombre, un tipo (booleano, cadena, DOMElement, etc.) y una descripción. El atributo &quot;inout&quot; con el valor &quot;out&quot; permite especificar que el parámetro &quot;result&quot; se encuentra en la salida de llamada SOAP.

La presencia del atributo &quot;static&quot; (con el valor &quot;true&quot;) describe este método como estático, lo que significa que se deben declarar todos los parámetros del método.

Un método &quot;const&quot; tiene implícitamente un documento XML en el formato de su esquema asociado como entrada.

Hay una descripción completa del elemento `<method>` de un esquema de Adobe Campaign disponible en el capítulo &quot;Referencias de Esquema&quot; en [Método](../../configuration/using/schema/method.md)

Ejemplo del método &quot;const&quot;-type &quot;ExecuteQuery&quot; desde el esquema &quot;xtk:queryDef&quot;:

```
<method name="ExecuteQuery" const="true">
  <help>Retrieve data from a query</help>
  <parameters>
    <param desc="Output xml document" name="output" type="DOMDocument" inout="out"/>
  </parameters>
</method>
```

El parámetro de entrada de este método es un documento XML con el formato del esquema &quot;xtk:queryDef&quot;.

## Descripción del servicio Web: WSDL {#web-service-description--wsdl}

Hay disponible un archivo WSDL (biblioteca de descripción de servicios Web) para cada servicio. Este archivo XML utiliza un idioma para describir el servicio y especificar los métodos, parámetros y el servidor con el que se va a establecer contacto para ejecutar el servicio.

### Generación de archivos WSDL {#wsdl-file-generation}

Para generar un archivo WSDL, debe introducir la siguiente URL desde un explorador Web:

https://`<server>`/nl/jsp/schemawsdl.jsp?esquema=`<schema>`

Con:

* **`<server>`**:: el servidor de aplicaciones de Adobe Campaign (nlserver web)
* **`<schema>`**:: Clave de identificación de esquema (Área de nombres:nombre_esquema)

### Ejemplo del método &#39;ExecuteQuery&#39; del esquema &#39;xtk:queryDef&#39; {#example-on-the--executequery--method-of-schema--xtk-querydef-}

El archivo WSDL se genera a partir de la dirección URL:

[https://localhost/nl/jsp/schemawsdl.jsp?schema=xtk:queryDef](https://my_serveur/nl/jsp/schemawsdl.jsp?schema=xtk:queryDef)

Una descripción WSDL inicio definiendo los tipos utilizados para los mensajes de formulario, asociados en &quot;puertos&quot;, conectados a un protocolo mediante &quot;enlaces&quot; que forman servicios Web.

#### Tipos {#types}

Las definiciones de tipo se basan en esquemas XML. En nuestro ejemplo, el método &quot;ExecuteQuery&quot; toma una cadena &quot;s:string&quot; y un documento XML (`<s:complextype>`) como parámetros. El valor devuelto por el método (&quot;ExecuteQueryResponse&quot;) es un documento XML ( `<s:complextype>`).

```
<types>
<s:schema elementFormDefault="qualified" targetNamespace="urn:xtk:queryDef">
  <s:element name="ExecuteQuery">
    <s:complexType>
      <s:sequence>
        <s:element maxOccurs="1" minOccurs="1" name="sessiontoken" type="s:string"/>
        <s:element maxOccurs="1" minOccurs="1" name="entity">
          <s:complexType>
            <s:sequence>
              <s:any/>
            </s:sequence>
          </s:complexType>
        </s:element>
      </s:sequence>
    </s:complexType>
  </s:element>
  <s:element name="ExecuteQueryResponse">
    <s:complexType>
      <s:sequence>
        <s:element maxOccurs="1" minOccurs="1" name="pdomOutput">
          <s:complexType mixed="true">
            <s:sequence>
              <s:any/>
            </s:sequence>
          </s:complexType>
        </s:element>
      </s:sequence>
    </s:complexType>
  </s:element>
```

#### Mensajes {#messages}

El `<message>` describe los nombres y tipos de un conjunto de campos que se van a enviar. El método utiliza dos mensajes para pasar como parámetro (&quot;ExecuteQueryIn&quot;) y el valor devuelto (&quot;ExecuteQueryOut&quot;).

```
<message name="ExecuteQueryIn">
  <part element="tns:ExecuteQuery" name="parameters"/>
</message>

<message name="ExecuteQueryOut">
  <part element="tns:ExecuteQueryResponse" name="parameters"/>
</message> 
```

#### PortType {#porttype}

El `<porttype>` asocia los mensajes en la operación &quot;ExecuteQuery&quot; desencadenada por la consulta (&quot;input&quot;) que genera una respuesta (&quot;output&quot;).

```
<portType name="queryDefMethodsSoap">
  <operation name="ExecuteQuery">
    <input message="tns:ExecuteQueryIn"/>
    <output message="tns:ExecuteQueryOut"/>
  </operation>
</portType>
```

#### Enlace {#binding}

La parte `<binding>` especifica el protocolo de comunicación SOAP ( `<soap:binding>` ), el transporte de datos en HTTP (valor del atributo &quot;Transport&quot;) y el formato de datos para la operación &quot;ExecuteQuery&quot;. El cuerpo del sobre SOAP contiene los segmentos de mensaje directamente sin transformación.

```
<binding name="queryDefMethodsSoap" type="tns:queryDefMethodsSoap">
  <soap:binding style="document" transport="http://schemas.xmlsoap.org/soap/http"/>
  <operation name="ExecuteQuery">
    <soap:operation soapAction="xtk:queryDef#ExecuteQuery" style="document"/>
    <input>
      <soap:body encodingStyle="http://schemas.xmlsoap.org/soap/encoding/" namespace="urn:xtk:queryDef" use="literal"/>
    </input>
    <output>
      <soap:body encodingStyle="http://schemas.xmlsoap.org/soap/encoding/" namespace="urn:xtk:queryDef" use="literal"/>
    </output>
  </operation>
</binding>
```

#### Servicio {#service}

La parte `<service>` describe el servicio &quot;XtkQueryDef&quot; con su URI en la dirección URL del servidor de aplicaciones de Adobe Campaign.

```
<service name="XtkQueryDef">
  <port binding="tns:queryDefMethodsSoap" name="queryDefMethodsSoap">
    <soap:address location="https://localhost/nl/jsp/soaprouter.jsp"/>
  </port>
</service>
```

## Conectividad {#connectivity}

Adobe Campaign ha aumentado la seguridad de los mecanismos de autenticación mediante la introducción de zonas de seguridad (consulte el capítulo **Definición de zonas de seguridad** de [esta sección](../../installation/using/configuring-campaign-server.md#defining-security-zones)), así como la configuración de administración de sesiones.

Existen dos modos de autenticación disponibles:

* **mediante una llamada al método()** de inicio de sesión. Este modo genera un token de sesión y un distintivo de seguridad. Es el modo más seguro y, por lo tanto, el más recomendado.

o

* **mediante el inicio de sesión de Adobe Campaign +** contraseña que crea un token de sesión. El token de sesión caduca automáticamente después de un período establecido. Este modo no se recomienda y requiere reducir la configuración de seguridad de la aplicación para algunos ajustes de zona (allowUserPassword=&quot;true&quot; y sessionTokenOnly=&quot;true&quot;).

### Características del token de sesión {#session-token-characteristics}

El token de sesión tiene las características siguientes:

* un ciclo de vida de X horas (el ciclo de vida se puede configurar en el archivo &#39;serverConf.xml&#39;, el período predeterminado es de 24 horas)
* una construcción aleatoria (ya no contiene el nombre de usuario y la contraseña)
* cuando se accede a través de la Web:

   * el token de sesión se convierte en un token permanente, no se destruye una vez que se cierra el explorador
   * se coloca en una cookie HTTP-ONLY (las cookies deben activarse para los operadores)

### Características del token de seguridad {#security-token-characteristics}

El token de seguridad tiene las características siguientes:

* se genera a partir del token de sesión
* tiene un ciclo de vida de 24 horas (configurable en el archivo &#39;serverConf.xml&#39;, el período predeterminado es de 24 horas)
* se almacena en la consola de Adobe Campaign
* cuando se accede a través de la Web:

   * se almacena en un documento.__securityToken, propiedad
   * las direcciones URL de la página se actualizan para actualizar el token de seguridad
   * los formularios también se actualizan mediante un campo oculto que contiene el token

#### Movimiento del token de seguridad {#security-token-movement}

Cuando se accede a través de la consola, es:

* transmitido en la respuesta de inicio de sesión (en el encabezado HTTP)
* se utiliza en cada consulta (en el encabezado HTTP)

Desde un POST y HTTP de GET:

* el servidor completa los vínculos con el token
* el servidor agrega un campo oculto a los formularios

Desde una llamada SOAP:

* se agrega a los encabezados de llamada

### Ejemplos de llamadas {#call-examples}

* Usando **HttpSoapConnection/SoapService**:

```
  
    var cnx = new HttpSoapConnection("https://serverURL/nl/jsp/soaprouter.jsp");
  var session = new SoapService(cnx, 'urn:xtk:session');
  session.addMethod("Logon", "xtk:session#Logon",
                      ["sessiontoken", "string", "Login", "string", "Password", "string", "Parameters", "NLElement"],
                      ["sessionToken", "string", "sessionInfo", "NLElement", "securityToken", "string"]);
  
  var res = session.Logon("", "admin", "pwd", <param/>);
  var sessionToken = res[0];
  var securityToken = res[2];
  
  cnx.addTokens(sessionToken, securityToken);
  var query = new SoapService(cnx, 'urn:xtk:queryDef');
  query.addMethod("ExecuteQuery", "xtk:queryDef#ExecuteQuery",
                      ["sessiontoken", "string", "entity", "NLElement"],
                      ["res", "NLElement"]);
  
  var queryRes = query.ExecuteQuery("", <queryDef operation="select" schema="nms:recipient">
            <select>
              <node expr="@email"/>
              <node expr="@lastName"/>
              <node expr="@firstName"/>
            </select>
            <where>
              <condition expr="@email = 'joe.doe@aol.com'"/>
            </where>
          </queryDef>);
  logInfo(queryRes[0].toXMLString())
```

* Usando **HttpServletRequest**:

>[!NOTE]
>
>Las direcciones URL utilizadas en las siguientes llamadas **HttpServletRequest** deben estar en lista de permitidos en la sección de permisos de URL del archivo **serverConf.xml**. Esto también se aplica a la dirección URL del propio servidor.

Inicio de sesión, ejecución():

```
var req = new HttpClientRequest("https://serverURL/nl/jsp/soaprouter.jsp");
req.header["Content-Type"] = "text/xml; charset=utf-8";
req.header["SOAPAction"] =   "xtk:session#Logon";
req.method = "POST";
req.body = '<soapenv:Envelope xmlns:soapenv="http://schemas.xmlsoap.org/soap/envelope/" xmlns:urn="urn:xtk:session">' +
    '<soapenv:Header/>' +
    '<soapenv:Body>' +
        '<urn:Logon>' +
            '<urn:sessiontoken></urn:sessiontoken>' +
            '<urn:strLogin>LOGIN_HERE</urn:strLogin>' +
            '<urn:strPassword>PASSWORD_HERE</urn:strPassword>' +
            '<urn:elemParameters></urn:elemParameters>' +
        '</urn:Logon>' +
    '</soapenv:Body>' +
'</soapenv:Envelope>';
req.execute();
           
var resp = req.response;
var xmlRes = new XML(String(resp.body).replace("<?xml version='1.0'?>",""));
var sessionToken = String(xmlRes..*::pstrSessionToken);;
var securityToken = String(xmlRes..*::pstrSecurityToken);
```

Ejecución de consulta:

```
var req2 = new HttpClientRequest("https://serverURL/nl/jsp/soaprouter.jsp");
req2.header["Content-Type"] = "text/xml; charset=utf-8";
req2.header["SOAPAction"] =   "xtk:queryDef#ExecuteQuery";req2.header["X-Security-Token"] = securityToken;
req2.header["cookie"]           = "__sessiontoken="+sessionToken;
req2.method = "POST";
req2.body = '<soapenv:Envelope xmlns:soapenv="http://schemas.xmlsoap.org/soap/envelope/" xmlns:urn="urn:xtk:queryDef">' +
             '<soapenv:Header/><soapenv:Body><urn:ExecuteQuery><urn:sessiontoken/><urn:entity>' +
                '<queryDef operation="select" schema="nms:recipient">' +
                  '<select><node expr="@email"/><node expr="@lastName"/><node expr="@firstName"/></select>' +
                  '<where><condition expr="@email = \'john.doe@aol.com\'"/></where>' +
                '</queryDef>' +
           '</urn:entity></urn:ExecuteQuery></soapenv:Body></soapenv:Envelope>';
req2.execute();
var resp2 = req2.response;
logInfo(resp2.body)
```
