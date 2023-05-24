---
product: campaign
title: 'Elementos y atributos de esquema: elemento param'
description: elemento param
exl-id: d8960a2e-6900-4346-9f06-e7dd9d7b5139
source-git-commit: 40da5774c8a6a228992c4aa400e2d9924215611e
workflow-type: tm+mt
source-wordcount: '177'
ht-degree: 6%

---

# elemento param {#param--element}

![](../../../assets/v7-only.svg)

## Modelo de contenido {#content-model-12}

parámetro:==help

## Atributos {#attributes-12}

* @_operation (cadena)
* @desc (cadena)
* @enum (cadena)
* @inout (cadena)
* @label (cadena)
* @localizable (cadena)
* @name (TOKEN MENÚ)
* @namespace (TOKEN MENÚ)
* @type (cadena)

## Padres {#parents-12}

`<parameters>`

## Tareas secundarias {#children-12}

`<help>`

## Descripción {#description-12}

Este elemento permite definir un parámetro para llamar a un método SOAP.

## Descripción de atributo {#attribute-description-12}

* **desc (cadena)**: descripción que hace referencia a `<param>` Elemento.
* **inout (cadena)**: este atributo define si el parámetro se encuentra en la entrada (entrada) o salida (salida) de la llamada SOAP. Si no se especifica este atributo, se introduce el parámetro predeterminado (&quot;@inout=in&quot;).
* **label (cadena)**: `<param>` etiqueta
* **localizable (cadena)**: si está activado, este atributo indica a la herramienta de recopilación que recupere el valor del atributo &quot;@label&quot; para su traducción (uso interno).
* **nombre (MNTOKEN)**: nombre interno del `<param>`
* **type (cadena)**: este atributo define el tipo de `<param>` elemento

   Lista de tipos disponibles:

   * CUALQUIERA
   * cubo
   * mancha
   * booleano
   * byte
   * CDATA
   * datetime
   * datetimetz
   * datetimenotz
   * date
   * DOMocument
   * DOMElement
   * doble
   * enum
   * float
   * html
   * int64
   * vincular
   * largo
   * nota
   * MNTOKEN
   * percent
   * clave principal
   * corto
   * cadena
   * tiempo
   * intervalo de tiempo
   * uuid

## Ejemplos {#examples-9}

Definición de la configuración entrante &quot;serviceName&quot; del tipo de cadena de caracteres:

```
<param desc="Name of the information service(s) (separated with commas)"
               name="serviceName" type="string" inout="in"/>
```
