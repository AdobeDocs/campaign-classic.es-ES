---
product: campaign
title: Elementos y atributos
description: Elementos y atributos
audience: configuration
content-type: reference
topic-tags: schema-reference
exl-id: 4cd67278-2623-4508-9a9f-9007c6a5f8ac
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: tm+mt
source-wordcount: '196'
ht-degree: 6%

---

# elemento de enumeración {#enumeration--element}

## Modelo de contenido {#content-model-5}

enumeration:==(help| value)

## Atributos {#attributes-5}

* @basetype (cadena)
* @default (cadena)
* @desc (cadena)
* @label (cadena)
* @name (cadena)
* @template (cadena)

## Padres {#parents-5}

`<srcschema>`

## Niños {#children-5}

* `<help>`
* `<value>`

## Descripción {#description-5}

Este elemento permite definir una enumeración de valores. Una enumeración pertenece al esquema en el que está definida, pero se puede acceder a ella a través de otro esquema.

## Uso y contexto de uso {#use-and-context-of-use-4}

Las enumeraciones se definen al principio de un esquema (antes de que se defina el elemento principal).

## Descripción de atributo {#attribute-description-5}

* **basetype (cadena)**: tipo de los valores almacenados en la enumeración .

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

* **predeterminado (cadena)**: Valor predeterminado. El valor predeterminado también puede ser uno de los valores definidos en la enumeración.
* **desc (cadena)**: descripción de la enumeración.
* **label (cadena)**: etiqueta de enumeración.
* **nombre (cadena)**: nombre interno de la enumeración.
* **plantilla (cadena)**: este atributo define una referencia a un  `<enumeration>` elemento compartido por varios esquemas. La definición se copia automáticamente en el esquema actual.

## Ejemplos {#examples-4}

Ejemplo de valores de enumeración cuyos valores se almacenan en la base de datos:

```
    <enumeration name="myEnum">
       <value name="One" value="1"/>
       <value name="Two" value="2"/>
    </enumeration>

    <element label="Sample" name="Sample">
       <attribute dbEnum="myEnum" length="100" name="Number" required="true" type="string"/>
    </element>
```

Definición de una enumeración con un valor predeterminado:

```
 <enumeration basetype="byte" default="email" name="canal">
    <value label="Email" name="email" value="0"/> 
    <value label="Téléphone" name="phone" value="1"/>
    <value label="Call Center" name="callcenter" value="2"/>
 </enumeration>
```
