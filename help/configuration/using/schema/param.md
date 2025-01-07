---
product: campaign
title: 'Elementos y atributos de esquema: elemento param'
description: elemento param
feature: Schema Extension
exl-id: d8960a2e-6900-4346-9f06-e7dd9d7b5139
source-git-commit: 254c89490fefa5d405bcecd2f1781df46450a873
workflow-type: tm+mt
source-wordcount: '177'
ht-degree: 9%

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

SOAP Este elemento permite definir un parámetro para llamar a un método de.

## Descripción de atributo {#attribute-description-12}

* **desc (cadena)**: descripción que hace referencia al elemento `<param>`.
* SOAP **inout (cadena)**: este atributo define si el parámetro se encuentra o no en la entrada (entrada) o salida (salida) de la llamada a la. Si no se especifica este atributo, se introduce el parámetro predeterminado (&quot;@inout=in&quot;).
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
   * vincular
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
