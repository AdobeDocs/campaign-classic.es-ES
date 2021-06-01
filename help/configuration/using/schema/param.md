---
product: campaign
title: Elementos y atributos
description: Elementos y atributos
audience: configuration
content-type: reference
topic-tags: schema-reference
exl-id: d8960a2e-6900-4346-9f06-e7dd9d7b5139
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: tm+mt
source-wordcount: '175'
ht-degree: 6%

---

# elemento param {#param--element}

## Modelo de contenido {#content-model-12}

param:==help

## Atributos {#attributes-12}

* @_operation (cadena)
* @desc (cadena)
* @enum (cadena)
* @inout (cadena)
* @label (cadena)
* @localizable (cadena)
* @name (MNTOKEN)
* @namespace (MNTOKEN)
* @type (cadena)

## Padres {#parents-12}

`<parameters>`

## Niños {#children-12}

`<help>`

## Descripción {#description-12}

Este elemento permite definir un parámetro para llamar a un método SOAP.

## Descripción de atributo {#attribute-description-12}

* **desc (cadena)**: descripción que afecta al  `<param>` elemento.
* **inout (cadena)**: este atributo define si el parámetro se encuentra o no en la entrada (in) o salida (out) de la llamada SOAP. Si no se especifica este atributo, el parámetro predeterminado es input (&quot;@inout=in&quot;).
* **label (cadena)**:  `<param>` label
* **localizable (cadena)**: si está activado, este atributo indica a la herramienta de recopilación que recupere el valor del atributo &quot;@label&quot; para la traducción (uso interno).
* **nombre (MNTOKEN)**: nombre interno del  `<param>`
* **tipo (cadena)**: este atributo define el tipo de  `<param>` elemento

   Lista de tipos disponibles:

   * CUALQUIER
   * bin
   * blob
   * booleano
   * byte
   * CDATA
   * datetime
   * datetimetz
   * datetimenotz
   * date
   * DOMDocument
   * DOMElement
   * double
   * enum
   * float
   * html
   * int64
   * vínculo
   * long
   * memo
   * MNTOKEN
   * percent
   * primarykey
   * short
   * string
   * tiempo
   * timespan
   * uuid

## Ejemplos {#examples-9}

Definición de la configuración entrante &quot;serviceName&quot; del tipo de cadena de caracteres:

```
<param desc="Name of the information service(s) (separated with commas)"
               name="serviceName" type="string" inout="in"/>
```
