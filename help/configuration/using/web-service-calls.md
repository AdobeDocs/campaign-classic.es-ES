---
product: campaign
title: Llamadas al servicio web
description: Llamadas al servicio web
feature: API
role: Data Engineer, Developer
exl-id: ce94e7e7-b8f8-4c82-937f-e87d15e50c34
source-git-commit: b666535f7f82d1b8c2da4fbce1bc25cf8d39d187
workflow-type: tm+mt
source-wordcount: '923'
ht-degree: 1%

---

# Llamadas al servicio web{#web-service-calls}

## Información general {#general-information}

Todos los métodos API se presentan en forma de servicios web. Esto permite administrar todas las funciones de Adobe Campaign mediante llamadas SOAP, que son el punto de entrada nativo del servidor de aplicaciones de Adobe Campaign. La propia consola de Adobe Campaign solo utiliza llamadas SOAP.

Los servicios web permiten crear muchas aplicaciones a partir de un sistema de terceros:

* Alertas sincrónicas, notificaciones y ejecución de plantillas de envío en tiempo real desde un sistema de back office o de transacción.
* Desarrollo de interfaces especiales con funcionalidad simplificada (interfaces web, etc.),
* La alimentación y búsqueda de datos en la base de datos, al tiempo que se observan las reglas comerciales y se mantiene aislado del modelo físico subyacente.

## Definición de servicios web {#definition-of-web-services}

La definición de los servicios web implementados en el servidor de aplicaciones de Adobe Campaign está disponible en los esquemas de datos.

Un servicio web se describe en la gramática de los esquemas de datos y está disponible en el **`<methods>`** Elemento.

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

Aquí tiene un ejemplo de la definición del método llamado **GenerateForm**.

La descripción del servicio comienza con `<method>` Elemento. La lista de parámetros del método se completa desde el  `<parameters>` Elemento. Cada parámetro se especifica mediante un nombre, un tipo (Boolean, string, DOMElement, etc.) y una descripción. El atributo &quot;inout&quot; con el valor &quot;out&quot; permite especificar que el parámetro &quot;result&quot; se encuentra en la salida de la llamada SOAP.

La presencia del atributo &quot;static&quot; (con el valor &quot;true&quot;) describe este método como static, lo que significa que se deben declarar todos los parámetros del método.

Un método &quot;const&quot; tiene implícitamente un documento XML en formato de su esquema asociado como entrada.

Una descripción completa de la `<method>` de un esquema de Adobe Campaign está disponible en el capítulo &quot;Referencias de esquema&quot; en [Método](../../configuration/using/schema/method.md)

Ejemplo del método &quot;ExecuteQuery&quot; de tipo &quot;const&quot; del esquema &quot;xtk:queryDef&quot;:

```
<method name="ExecuteQuery" const="true">
  <help>Retrieve data from a query</help>
  <parameters>
    <param desc="Output xml document" name="output" type="DOMDocument" inout="out"/>
  </parameters>
</method>
```

El parámetro de entrada de este método es un documento XML con formato del esquema &quot;xtk:queryDef&quot;.

## Descripción del servicio web: WSDL {#web-service-description--wsdl}

Hay disponible un archivo WSDL (Biblioteca de descripción de servicios web) para cada servicio. Este archivo XML utiliza un metalenguaje para describir el servicio y especificar los métodos, parámetros y el servidor de contacto disponibles para ejecutarlo.

### Generación de archivos WSDL {#wsdl-file-generation}

Para generar un archivo WSDL, debe introducir la siguiente URL desde un explorador web:

https://`<server>`/nl/jsp/schemawsdl.jsp?schema=`<schema>`

Con:

* **`<server>`**: el servidor de aplicaciones de Adobe Campaign (nlserver web)
* **`<schema>`**: clave de identificación de esquema (área de nombres:schema_name)

### Ejemplo del método &quot;ExecuteQuery&quot; del esquema &quot;xtk:queryDef&quot; {#example-on-the--executequery--method-of-schema--xtk-querydef-}

El archivo WSDL se genera a partir de la dirección URL:

`https://localhost/nl/jsp/schemawsdl.jsp?schema=xtk:queryDef`

Una descripción de WSDL comienza por definir los tipos utilizados para formar mensajes, asociados en &quot;puertos&quot;, conectados a un protocolo mediante &quot;enlaces&quot; que forman servicios web.

#### Tipos {#types}

Las definiciones de tipo se basan en esquemas XML. En este ejemplo, el método &quot;ExecuteQuery&quot; toma una cadena &quot;s:string&quot; y un documento XML (`<s:complextype>`) como parámetros. El valor devuelto del método (&quot;ExecuteQueryResponse&quot;) es un documento XML (  `<s:complextype>`).

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

El `<binding>` especifica el protocolo de comunicación SOAP ( `<soap:binding>` ), transporte de datos en HTTP (valor del atributo &quot;transport&quot;) y formato de datos para la operación &quot;ExecuteQuery&quot;. El cuerpo del sobre SOAP contiene los segmentos de mensaje directamente sin transformación.

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

El `<service>` Este artículo describe el servicio &quot;XtkQueryDef&quot; con su URI en la URL del servidor de aplicaciones de Adobe Campaign.

```
<service name="XtkQueryDef">
  <port binding="tns:queryDefMethodsSoap" name="queryDefMethodsSoap">
    <soap:address location="https://localhost/nl/jsp/soaprouter.jsp"/>
  </port>
</service>
```

## Conectividad {#connectivity}

Adobe Campaign ha aumentado la seguridad de los mecanismos de autenticación al introducir [zonas de seguridad](../../installation/using/security-zones.md) y la configuración de administración de sesiones.

Hay dos modos de autenticación disponibles:

* **mediante una llamada a los métodos de inicio de sesión**. Este modo genera un token de sesión y un token de seguridad. Es el modo más seguro y, por lo tanto, el más recomendado.

o

* **mediante el inicio de sesión y la contraseña de Adobe Campaign** que crea un token de sesión. El token de sesión caduca automáticamente después de un periodo establecido. No se recomienda este modo y es necesario reducir la configuración de seguridad de la aplicación para algunas zonas (allowUserPassword=&quot;true&quot; y sessionTokenOnly=&quot;true&quot;).

### Características del token de sesión {#session-token-characteristics}

El token de sesión tiene las siguientes características:

* un ciclo de vida de X horas (el ciclo de vida se puede configurar en el archivo &quot;serverConf.xml&quot;, el periodo predeterminado es de 24 horas)
* una construcción aleatoria (ya no contiene el nombre de usuario y la contraseña)
* cuando se accede a través de la web:

   * el token de sesión se convierte en un token permanente y no se destruye una vez que se cierra el explorador
   * se coloca en una cookie HTTP-ONLY (las cookies deben activarse para los operadores)

### Características del token de seguridad {#security-token-characteristics}

El token de seguridad tiene las siguientes características:

* se genera a partir del token de sesión
* tiene un ciclo de vida de 24 horas (configurable en el archivo &quot;serverConf.xml&quot;, el periodo predeterminado es de 24 horas)
* se almacena en la consola de Adobe Campaign
* cuando se accede a través de la web:

   * se almacena en un documento.__securityToken, propiedad
   * las direcciones URL de la página se actualizan para actualizar el token de seguridad
   * los formularios también se actualizan mediante un campo oculto que contiene el token

#### Movimiento del token de seguridad {#security-token-movement}

Cuando se accede a través de la consola, es:

* transmitido en la respuesta de inicio de sesión (en el encabezado HTTP)
* se utiliza en cada consulta (en el encabezado HTTP)

Desde un POST y un GET HTTP:

* el servidor completa los vínculos con el token
* el servidor agrega un campo oculto a los formularios

Desde una llamada SOAP:

* se añade a los encabezados de llamada

### Ejemplos de llamadas {#call-examples}

* Uso de **HttpSoapConnection/SoapService**:

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

* Uso de **HttpServletRequest**:

>[!NOTE]
>
>Las direcciones URL utilizadas en lo siguiente **HttpServletRequest** las llamadas de deben estar en lista de permitidos en la sección permisos de url de **serverConf.xml** archivo. Esto también se aplica a la dirección URL del propio servidor.

Ejecución de inicio de sesión:

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
