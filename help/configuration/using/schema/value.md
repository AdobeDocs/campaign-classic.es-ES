---
product: campaign
title: 'Elementos y atributos: elemento de valor'
description: Elementos y atributos
audience: configuration
content-type: reference
topic-tags: schema-reference
exl-id: bad7fb4b-43d9-4033-ae0d-cf191d89114b
source-git-commit: 40da5774c8a6a228992c4aa400e2d9924215611e
workflow-type: tm+mt
source-wordcount: '149'
ht-degree: 4%

---

# elemento de valor {#value--element}

![](../../../assets/v7-only.svg)

## Modelo de contenido {#content-model-16}

value:==help

## Atributos {#attributes-16}

* @applyIf (cadena)
* @desc (cadena)
* @enabledIf (cadena)
* @img (cadena)
* @label (cadena)
* @name (cadena)
* @value (cadena)

## Principales {#parents-16}

`<enumeration>`

## Tareas secundarias {#children-16}

`<help>`

## Descripción {#description-16}

Este elemento permite definir los valores almacenados en una enumeración.

## Descripción del atributo {#attribute-description-16}

* **applyIf (cadena)**: este atributo permite hacer que un valor de enumeración sea opcional. Recibe una expresión XTK.
* **desc (cadena)**: descripción del valor de enumeración.
* **enabledIf (cadena)**: condición para activar el valor de enumeración.
* **img (cadena)**: imagen vinculada a la enumeración en el formulario &quot;namespace:image_name&quot;. La imagen debe importarse en el servidor de aplicaciones.
* **label (cadena)**: etiqueta del valor de enumeración.
* **name (cadena)**: nombre interno del valor de enumeración.
* **value (string)**: del valor de enumeración. El tipo de valor se define en función del tipo de enumeración. Si la enumeración es de tipo cadena de caracteres, solo puede contener valores de tipo cadena de caracteres.

## Ejemplos {#examples-13}

```
<enumeration name="myEnum">
       <value name="One" value="1"/>
       <value name="Two" value="2"/>
    </enumeration>
```
