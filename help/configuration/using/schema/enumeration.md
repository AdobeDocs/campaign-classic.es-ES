---
product: campaign
title: 'Elementos y atributos de esquema: elemento de enumeración'
description: elemento de enumeración
feature: Schema Extension
exl-id: 4cd67278-2623-4508-9a9f-9007c6a5f8ac
source-git-commit: fd5e4bbc87a48f029a09b14ab1d927b9afe4ac52
workflow-type: tm+mt
source-wordcount: '198'
ht-degree: 8%

---

# elemento de enumeración {#enumeration--element}

![](../../../assets/v7-only.svg)

## Modelo de contenido {#content-model-5}

enumeración:==(ayuda| value)

## Atributos {#attributes-5}

* @basetype (cadena)
* @default (cadena)
* @desc (cadena)
* @label (cadena)
* @name (cadena)
* @template (cadena)

## Padres {#parents-5}

`<srcschema>`

## Tareas secundarias {#children-5}

* `<help>`
* `<value>`

## Descripción {#description-5}

Este elemento permite definir una enumeración de valores. Una enumeración pertenece al esquema en el que se define, pero es accesible a través de otro esquema.

## Uso y contexto de uso {#use-and-context-of-use-4}

Las enumeraciones se definen al principio de un esquema (antes de definir el elemento principal).

## Descripción de atributo {#attribute-description-5}

* **basetype (string)**: tipo de los valores almacenados en la enumeración.

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

* **default (cadena)**: Valor predeterminado. El valor predeterminado también puede ser uno de los valores definidos en la enumeración.
* **desc (cadena)**: descripción de la enumeración.
* **label (string)**: etiqueta de enumeración.
* **nombre (cadena)**: nombre interno de la enumeración.
* **template (string)**: este atributo define una referencia a un elemento `<enumeration>` compartido por varios esquemas. La definición se copia automáticamente en el esquema actual.

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
