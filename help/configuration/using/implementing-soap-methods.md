---
solution: Campaign Classic
product: campaign
title: Implementación de métodos SOAP
description: Implementación de métodos SOAP
audience: configuration
content-type: reference
topic-tags: api
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '420'
ht-degree: 4%

---


# Implementación de métodos SOAP{#implementing-soap-methods}

## Introducción {#introduction}

Es posible crear métodos SOAP en JavaScript. Esta función simplemente habilita los procesos aplicativos, puede evitar desarrollar JSP y sus llamadas en los formularios.

Estos métodos SOAP se comportan del mismo modo que los definidos de forma nativa en la aplicación. Se admiten los mismos atributos: estático, solo clave y const.

## Definición de una biblioteca de métodos {#defining-a-method-library}

La creación de una biblioteca de métodos implica dos etapas:

* La declaración del método SOAP,
* Definición (o implementación) en JavaScript.

### Declaración {#declaration}

Inicio declarando los métodos en los esquemas (para obtener más información sobre cómo crear y editar esquemas, consulte [esta sección](../../configuration/using/about-schema-edition.md)).

Su declaración es similar a la de los métodos nativos, excepto que debe agregar el atributo &#39;library&#39; especificando el nombre de la biblioteca de métodos donde se encuentra la definición.

Este nombre coincide con el nombre (con la Área de nombres) de la entidad de tipo &#39;Código JavaScript&#39;.

Ejemplo:

El método testLog(msg) se declara en una extensión nms:destinatario

```
<method name="testLog" static="true" library="cus:test">
     <parameters>
       <param name="message" type="string" inout="in"/>
     </parameters>
   </method>
```

>[!NOTE]
>
>La Área de nombres y el nombre utilizados para la biblioteca son independientes del nombre de la Área de nombres y del esquema donde se encuentra la declaración.

### Definición {#definition}

Los métodos SOAP se implementan en forma de función JavaScript agrupada en una secuencia de comandos que representa una biblioteca.

>[!NOTE]
>
>Una biblioteca de métodos puede agrupar funciones para varios esquemas o viceversa, las funciones de un esquema se pueden definir en bibliotecas independientes.

La secuencia de comandos puede contener código que se ejecutará durante la carga inicial de la biblioteca.

**1. Nombre**

El nombre de la función debe cumplir el siguiente formato:

```
 <schema-namespace>_<schema-name>_<method-name>
```

Ejemplo:

La siguiente función de JavaScript es la implementación del método descrito anteriormente. Se definirá en la entidad de tipo &quot;Código JavaScript&quot; utilizando el nombre &#39;cus:test&#39;.

```
function nms_recipient_testLog(message)
 {
   logInfo("*** " + message)
 }
```

**2. Firma**

La firma de la función debe incluir un argumento para cada parámetro &#39;in&#39; o &#39;inout&#39; de la declaración.

Casos específicos:

* **métodos** no estáticos: la función debe incluir primero un argumento adicional, coincidiendo con la entidad XML pasada en forma de objeto de tipo &#39;xml&#39; (E4X).
* **Métodos** de tipo &quot;solo clave&quot;: la función debe incluir primero un argumento adicional, coincidiendo con la clave pasada en forma de cadenas de caracteres.

**3. Valores devueltos**

La función debe devolver un valor para cada parámetro de tipo &#39;out&#39; o &#39;inout&#39;. Caso específico: Si el método se declara sin ninguno de los atributos &#39;static&#39;, &#39;key only&#39; o &#39;const&#39;, el primer valor devuelto debe coincidir con la entidad modificada. Es posible devolver un nuevo objeto o devolver el primer parámetro modificado.

Por ejemplo:

```
function nms_recipient_setLastName(self, name)
 {
   self.@lastName = name
   return self
 }
```

Cuando se devuelven varios valores, deben mostrarse en una tabla.

Ejemplo:

```
function nms_recipient_getKey(self)
 {
   return [self.@firstName, self.@lastName]
 }
```

