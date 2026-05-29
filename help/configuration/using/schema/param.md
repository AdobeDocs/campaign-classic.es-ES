---
product: campaign
title: 'Elementos y atributos de esquema: elemento param'
description: elemento param
feature: Schema Extension
exl-id: d8960a2e-6900-4346-9f06-e7dd9d7b5139
TQID: https://experienceleague.adobe.com/fiMkJtGU90FP-G6BJhTnIrgBJ39uIJaakqKD49EhXS0
product_v2: id: dfc56824-e8b9-499e-85d4-21aedb507314
feature_v2: []
subfeature_v2: []
source-git-commit: bb41e9407ab5853b0194bb325bbf3f17bc3ea232
workflow-type: tm+mt
source-wordcount: 177
ht-degree: 12%

---

# elemento param {#param--element}


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

* **desc (cadena)**: descripción que hace referencia al elemento `<param>`.
* **inout (cadena)**: este atributo define si el parámetro se encuentra o no en la entrada (entrada) o salida (salida) de la llamada de SOAP. Si no se especifica este atributo, se introduce el parámetro predeterminado (&quot;@inout=in&quot;).
* **etiqueta (cadena)**: `<param>` etiqueta
* **localizable (cadena)**: si está activado, este atributo indica a la herramienta de recopilación que recupere el valor del atributo &quot;@label&quot; para su traducción (uso interno).
* **nombre (MNTOKEN)**: nombre interno de `<param>`
* **type (string)**: este atributo define el tipo de elemento `<param>`

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
   * fecha
   * DOMocument
   * DOMElement
   * doble
   * enum
   * flotante
   * html
   * int64
   * vínculo
   * largo
   * nota
   * MNTOKEN
   * porcentaje
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
