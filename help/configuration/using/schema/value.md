---
product: campaign
title: 'Elementos y atributos: elemento de valor'
description: Elementos y atributos
feature: Schema Extension
audience: configuration
content-type: reference
topic-tags: schema-reference
exl-id: bad7fb4b-43d9-4033-ae0d-cf191d89114b
source-git-commit: fd5e4bbc87a48f029a09b14ab1d927b9afe4ac52
workflow-type: tm+mt
source-wordcount: '148'
ht-degree: 2%

---

# elemento de valor {#value--element}

![](../../../assets/v7-only.svg)

## Modelo de contenido {#content-model-16}

valor:==ayuda

## Atributos {#attributes-16}

* @applicableIf (cadena)
* @desc (cadena)
* @enabledIf (cadena)
* @img (cadena)
* @label (cadena)
* @name (cadena)
* @value (cadena)

## Padres {#parents-16}

`<enumeration>`

## Tareas secundarias {#children-16}

`<help>`

## Descripción {#description-16}

Este elemento permite definir los valores almacenados en una enumeración.

## Descripción de atributo {#attribute-description-16}

* **applyIf (cadena)**: este atributo permite hacer opcional un valor de enumeración. Recibe una expresión XTK.
* **desc (cadena)**: descripción del valor de enumeración.
* **enabledIf (cadena)**: condición para activar el valor de enumeración.
* **img (cadena)**: imagen vinculada a la enumeración en el formulario &quot;namespace:image_name&quot;. La imagen debe importarse en el servidor de aplicaciones.
* **label (cadena)**: etiqueta del valor de enumeración.
* **nombre (cadena)**: nombre interno del valor de enumeración.
* **value (string)**: valor del valor de enumeración. El tipo de valor se define en función del tipo de enumeración. Si la enumeración es del tipo cadena de caracteres, sólo puede contener valores de tipo cadena de caracteres.

## Ejemplos {#examples-13}

```
<enumeration name="myEnum">
       <value name="One" value="1"/>
       <value name="Two" value="2"/>
    </enumeration>
```
