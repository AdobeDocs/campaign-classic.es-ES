---
solution: Campaign Classic
product: campaign
title: Elementos y atributos
description: Elementos y atributos
audience: configuration
content-type: reference
topic-tags: schema-reference
translation-type: tm+mt
source-git-commit: 922257b157f8d76d6e703b0510ff689d1aa4d067
workflow-type: tm+mt
source-wordcount: '175'
ht-degree: 6%

---


# elemento param {#param--element}

## Modelo de contenido {#content-model-12}

param:==help

## Atributos {#attributes-12}

* @_operation (string)
* @desc (cadena)
* @enum (cadena)
* @inout (cadena)
* @label (cadena)
* @localizable (cadena)
* @name (MNTOKEN)
* @Área de nombres (MNTOKEN)
* @type (cadena)

## Padres {#parents-12}

`<parameters>`

## Niños {#children-12}

`<help>`

## Descripción {#description-12}

Este elemento permite definir un parámetro para llamar a un método SOAP.

## Descripción del atributo {#attribute-description-12}

* **desc (cadena)**: descripción que afecta al  `<param>` elemento.
* **inout (cadena)**: este atributo define si el parámetro se encuentra o no en la entrada (entrada) o salida (salida) de la llamada SOAP. Si no se especifica este atributo, el parámetro predeterminado es input (&quot;@inout=in&quot;).
* **label (string)**:  `<param>` label
* **localizable (cadena)**: si se activa, este atributo indica a la herramienta de recopilación que recupere el valor del atributo &quot;@label&quot; para traducción (uso interno).
* **name (MNTOKEN)**: nombre interno del  `<param>`
* **type (string)**: este atributo define el tipo de  `<param>` elemento

   Lista de los tipos disponibles:

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
   * doble
   * enum
   * float
   * html
   * int64
   * link
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

Definición de la configuración de entrada &quot;serviceName&quot; del tipo de cadena de caracteres:

```
<param desc="Name of the information service(s) (separated with commas)"
               name="serviceName" type="string" inout="in"/>
```
