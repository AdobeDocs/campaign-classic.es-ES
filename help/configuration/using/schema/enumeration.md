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
source-wordcount: '196'
ht-degree: 6%

---


# Elemento de lista desglosada {#enumeration--element}

## Modelo de contenido {#content-model-5}

lista desglosada:==(ayuda| valor)

## Atributos {#attributes-5}

* @basetype (string)
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

Este elemento nos permite definir una lista desglosada de valor. Una lista desglosada pertenece al esquema en el que está definida, pero se puede acceder a ella a través de otro esquema.

## Uso y contexto de uso {#use-and-context-of-use-4}

Las listas desglosadas se definen en el inicio de un esquema (antes de definir el elemento principal).

## Descripción del atributo {#attribute-description-5}

* **basetype (string)**: tipo de los valores almacenados en la lista desglosada.

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

* **default (string)**: Valor predeterminado. El valor predeterminado también puede ser uno de los valores definidos en la lista desglosada.
* **desc (cadena)**: Descripción de la lista desglosada.
* **label (string)**: Etiqueta de lista desglosada.
* **name (string)**: nombre interno de la lista desglosada.
* **template (string)**: este atributo define una referencia a un  `<enumeration>` elemento compartido por varios esquemas. La definición se copia automáticamente en el esquema actual.

## Ejemplos {#examples-4}

Ejemplo de valores de lista desglosada cuyos valores se almacenan en la base de datos:

```
    <enumeration name="myEnum">
       <value name="One" value="1"/>
       <value name="Two" value="2"/>
    </enumeration>

    <element label="Sample" name="Sample">
       <attribute dbEnum="myEnum" length="100" name="Number" required="true" type="string"/>
    </element>
```

Definición de una lista desglosada con un valor predeterminado:

```
 <enumeration basetype="byte" default="email" name="canal">
    <value label="Email" name="email" value="0"/> 
    <value label="Téléphone" name="phone" value="1"/>
    <value label="Call Center" name="callcenter" value="2"/>
 </enumeration>
```
