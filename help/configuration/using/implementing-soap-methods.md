---
product: campaign
title: Implementación de métodos SOAP
description: Implementación de métodos SOAP
feature: Configuration
role: Data Engineer, Developer
exl-id: 441a0e5c-fa7f-46c8-a65a-5cca4c846d43
source-git-commit: 0ed70b3c57714ad6c3926181334f57ed3b409d98
workflow-type: tm+mt
source-wordcount: '419'
ht-degree: 4%

---

# SOAP Implementación de métodos de{#implementing-soap-methods}



## Introducción {#introduction}

SOAP Es posible crear métodos de en JavaScript. Esta función simplemente habilita los procesos aplicativos, puede evitar desarrollar JSP y sus llamadas en los formularios.

SOAP Estos métodos de se comportan del mismo modo que los definidos de forma nativa en la aplicación. Se admiten los mismos atributos: static, key only y const.

## Definir una biblioteca de métodos {#defining-a-method-library}

La creación de una biblioteca de métodos consta de dos fases:

* SOAP La declaración de método de la,
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

SOAP Se implementan métodos en forma de función de JavaScript agrupada en una secuencia de comandos que representa una biblioteca.

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

La siguiente función de JavaScript es la implementación del método descrito anteriormente. Se definirá en la entidad de tipo &quot;JavaScript Code&quot; utilizando el nombre &quot;cus:test&quot;.

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
