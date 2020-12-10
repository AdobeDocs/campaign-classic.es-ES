---
solution: Campaign Classic
product: campaign
title: Elementos y atributos
description: Elementos y atributos
audience: configuration
content-type: reference
topic-tags: schema-reference
translation-type: tm+mt
source-git-commit: 1818bd2aeb60689b2ce0e59cb0bd157f000de513
workflow-type: tm+mt
source-wordcount: '204'
ht-degree: 4%

---


# `<method>` Elemento {#method--element}

## Modelo de contenido {#content-model-10}

método:==( help | parámetros)

## Atributos {#attributes-10}

* @_operation (string)
* @access (cadena)
* @const (booleano)
* @hidden (booleano)
* @label (cadena)
* @library (cadena)
* @name (MNTOKEN)
* @pkonly (booleano)
* @static (boolean)

## Padres {#parents-10}

`<methods>`  ,  `<interface />`

## Niños {#children-10}

* `<help>`
* `<parameters>`

## Descripción {#description-10}

Este elemento permite definir un método SOAP.

## Uso y contexto de uso {#use-and-context-of-use-7}

Los métodos SOAP habilitan procesos de aplicación.

&quot;@library&quot; es necesario para declarar un nuevo método (no nativo): la Área de nombres y el nombre utilizados para la biblioteca son independientes de la Área de nombres y el nombre del esquema en el que se encuentra la declaración.

## Descripción del atributo {#attribute-description-10}

* **access (cadena)**: este atributo define el control de acceso para utilizar el método. Si falta este atributo, la identificación es obligatoria. Los valores disponibles son: &#39;anónimo&#39;, &#39;admin&#39; y &#39;sql&#39;.
* **const (booleano)**: si se activa, este atributo significa que el método declarado alterará la entidad
* **label (string)**: del método.
* **library (string)**: este método no es nativo de la aplicación. Este atributo toma el valor de la biblioteca de métodos en la que se encuentra la definición de método (nms:mylibrary.js).
* **name (MNTOKEN)**: nombre de método único.
* **static (boolean)**: si este atributo está activado, el método se considera autónomo, se deben especificar todos los parámetros del método cuando se llame a él.

## Ejemplos {#examples-7}

Definición del método &quot;Subscribe&quot; out of box:

```
 
<method name="Subscribe" static="true">
      <help>Creation of update of a recipient's subscription to an information service</help>
      <parameters>
        <param desc="Name of the information service(s) (separated with commas)"
               name="serviceName" type="string"/>
        <param desc="Recipient to subscribe and possibly create" name="recipient"
               type="DOMElement"/>
        <param desc="Create the recipient if they don't exist" name="create" type="boolean"/>
      </parameters>     
    </method>
```
