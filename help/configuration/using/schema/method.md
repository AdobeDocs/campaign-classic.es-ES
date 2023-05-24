---
product: campaign
title: 'Elementos y atributos de esquema: elemento de método'
description: elemento de método
exl-id: 0fb74318-fe09-473c-8e33-1f3afd66b4cc
source-git-commit: 40da5774c8a6a228992c4aa400e2d9924215611e
workflow-type: tm+mt
source-wordcount: '207'
ht-degree: 1%

---

# elemento de método {#method--element}

![](../../../assets/v7-only.svg)

## Modelo de contenido {#content-model-10}

método:==( ayuda | parámetros)

## Atributos {#attributes-10}

* @_operation (cadena)
* @access (cadena)
* @const (booleano)
* @hidden (booleano)
* @label (cadena)
* @library (cadena)
* @name (TOKEN MENÚ)
* @pkonly (booleano)
* @static (booleano)

## Padres {#parents-10}

`<methods>`  ,  `<interface />`

## Tareas secundarias {#children-10}

* `<help>`
* `<parameters>`

## Descripción {#description-10}

Este elemento permite definir un método SOAP.

## Uso y contexto de uso {#use-and-context-of-use-7}

Los métodos SOAP habilitan procesos de aplicación.

La &quot;@library&quot; es necesaria para declarar un nuevo método (no nativo): el área de nombres y el nombre utilizados para la biblioteca son independientes del área de nombres y el nombre del esquema donde se encuentra la declaración.

## Descripción de atributo {#attribute-description-10}

* **acceso (cadena)**: este atributo define el control de acceso para el uso del método. Si falta este atributo, la identificación es obligatoria. Los valores disponibles son: &quot;anonymous&quot;, &quot;admin&quot; y &quot;sql&quot;.
* **const (booleano)**: si está activado, este atributo significa que el método declarado alterará la entidad
* **label (cadena)**: etiqueta del método.
* **library (string)**: este método no es nativo de la aplicación. Este atributo toma el valor de la biblioteca de métodos donde se encuentra la definición del método (nms:mylibrary.js).
* **nombre (MNTOKEN)**: nombre de método único.
* **static (booleano)**: si este atributo está activado, el método se considera autónomo; todos los parámetros deben especificarse en el método cuando se solicite.

## Ejemplos {#examples-7}

Definición del método predeterminado &quot;Subscribe&quot;:

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
