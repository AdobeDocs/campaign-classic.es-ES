---
product: campaign
title: Implementación de métodos SOAP
description: Implementación de métodos SOAP
feature: Configuration
role: Developer
exl-id: 441a0e5c-fa7f-46c8-a65a-5cca4c846d43
TQID: https://experienceleague.adobe.com/EN-Xu7KjcQ5GXDqnEIySe23eQbhb2JGORf-vmpplNFs
product_v2: id: dfc56824-e8b9-499e-85d4-21aedb507314
feature_v2: id: b12f6872-9271-4369-85e5-86969a0b99a2id: b82389f8-9b5e-4083-8e3b-3cef299fb8b9
subfeature_v2: id: cfc95e9b-b035-4403-a6a9-b27a8a053a37
role_v2: id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
topic_v2: id: b5ce8718-c3af-4fdb-a1a9-fca32f83a87c
source-git-commit: 4c295c0dabae8aba298390a3da2422a3fa1219f9
workflow-type: tm+mt
source-wordcount: 418
ht-degree: 4%

---

# Implementación de métodos SOAP{#implementing-soap-methods}



## Introducción {#introduction}

Es posible crear métodos de SOAP en JavaScript. Esta función simplemente habilita los procesos aplicativos, puede evitar desarrollar JSP y sus llamadas en los formularios.

Estos métodos de SOAP se comportan del mismo modo que los definidos de forma nativa en la aplicación. Se admiten los mismos atributos: static, key only y const.

## Definir una biblioteca de métodos {#defining-a-method-library}

La creación de una biblioteca de métodos consta de dos fases:

* La declaración del método SOAP,
* Definición (o implementación) en JavaScript.

### Declaración {#declaration}

Comience declarando los métodos en los esquemas (para obtener más información sobre cómo crear y editar esquemas, consulte [esta sección](../../configuration/using/about-schema-edition.md)).

Su declaración es similar a la de los métodos nativos, excepto que necesita agregar el atributo &quot;library&quot; (biblioteca) que especifica el nombre de la biblioteca de métodos donde se encuentra la definición.

Este nombre coincide con el nombre (con el área de nombres) de la entidad de tipo &quot;JavaScript Code&quot;.

Ejemplo:

El método testLog(msg) se declara en una extensión nms:recipient

```
<method name="testLog" static="true" library="cus:test">
     <parameters>
       <param name="message" type="string" inout="in"/>
     </parameters>
   </method>
```

>[!NOTE]
>
>El espacio de nombres y el nombre utilizados para la biblioteca son independientes del espacio de nombres y del nombre de esquema donde se encuentra la declaración.

### Definición {#definition}

Los métodos de SOAP se implementan en forma de función de JavaScript agrupada en una secuencia de comandos que representa una biblioteca.

>[!NOTE]
>
>Una biblioteca de métodos puede agrupar funciones para varios esquemas o viceversa, las funciones de un esquema se pueden definir en bibliotecas independientes.

La secuencia de comandos puede contener el código que se va a ejecutar durante la carga inicial de la biblioteca.

**1. Nombre**

El nombre de la función debe cumplir con el siguiente formato:

```
 <schema-namespace>_<schema-name>_<method-name>
```

Ejemplo:

La siguiente función de JavaScript es la implementación del método descrito anteriormente. Se definirá en la entidad de tipo &quot;JavaScript Code&quot; con el nombre &quot;cus:test&quot;.

```
function nms_recipient_testLog(message)
 {
   logInfo("*** " + message)
 }
```

**2. Firma**

La firma de la función debe incluir un argumento para cada parámetro &quot;in&quot; o &quot;inout&quot; de la declaración.

Casos específicos:

* **métodos no estáticos**: la función debe incluir primero un argumento adicional, que coincida con la entidad XML pasada en forma de objeto de tipo &#39;xml&#39; (E4X).
* **métodos de tipo &quot;solo clave&quot;**: la función debe incluir primero un argumento adicional, que coincida con la clave pasada en forma de cadenas de caracteres.

**3. Valores devueltos**

La función debe devolver un valor para cada parámetro de tipo &quot;out&quot; o &quot;inout&quot;. Caso específico: si el método se declara sin ninguno de los atributos &quot;static&quot;, &quot;key only&quot; o &quot;const&quot;, el primer valor devuelto debe coincidir con la entidad modificada. Es posible devolver un objeto nuevo o devolver el primer parámetro modificado.

Por ejemplo:

```
function nms_recipient_setLastName(self, name)
 {
   self.@lastName = name
   return self
 }
```

Cuando se devuelven varios valores, estos deben mostrarse en una tabla.

Ejemplo:

```
function nms_recipient_getKey(self)
 {
   return [self.@firstName, self.@lastName]
 }
```
