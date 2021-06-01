---
product: campaign
title: Elementos y atributos
description: Elementos y atributos
audience: configuration
content-type: reference
topic-tags: schema-reference
exl-id: 0fb74318-fe09-473c-8e33-1f3afd66b4cc
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: tm+mt
source-wordcount: '205'
ht-degree: 3%

---

# elemento de método {#method--element}

## Modelo de contenido {#content-model-10}

método:==( help | parámetros)

## Atributos {#attributes-10}

* @_operation (cadena)
* @access (cadena)
* @const (booleano)
* @hidden (booleano)
* @label (cadena)
* @library (cadena)
* @name (MNTOKEN)
* @pkonly (booleano)
* @static (booleano)

## Padres {#parents-10}

`<methods>`  ,  `<interface />`

## Niños {#children-10}

* `<help>`
* `<parameters>`

## Descripción {#description-10}

Este elemento permite definir un método SOAP.

## Uso y contexto de uso {#use-and-context-of-use-7}

Los métodos SOAP permiten procesos de aplicación.

La &quot;@library&quot; es necesaria para declarar un nuevo método (no nativo): el espacio de nombres y el nombre utilizado para la biblioteca son independientes del espacio de nombres y el nombre del esquema donde está la declaración.

## Descripción de atributo {#attribute-description-10}

* **acceso (cadena)**: este atributo define el control de acceso para el uso del método . Si falta este atributo, la identificación es obligatoria. Los valores disponibles son: &#39;anonymous&#39;, &#39;admin&#39; y &#39;sql&#39;.
* **const (booleano)**: si está activado, este atributo significa que el método declarado alterará la entidad
* **label (cadena)**: etiqueta del método .
* **biblioteca (cadena)**: este método no es nativo de la aplicación. Este atributo toma el valor de la biblioteca de métodos donde se encuentra la definición del método (nms:mylibrary.js).
* **nombre (MNTOKEN)**: nombre de método único.
* **estático (booleano)**: si este atributo está activado, el método se considera autónomo, se deben especificar todos los parámetros del método cuando se llame a él.

## Ejemplos {#examples-7}

Definición del método &quot;Suscribirse&quot; fuera de la caja:

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
