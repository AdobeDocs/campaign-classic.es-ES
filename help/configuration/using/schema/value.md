---
product: campaign
title: Elementos y atributos
description: Elementos y atributos
audience: configuration
content-type: reference
topic-tags: schema-reference
exl-id: bad7fb4b-43d9-4033-ae0d-cf191d89114b
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: tm+mt
source-wordcount: '147'
ht-degree: 5%

---

# elemento de valor {#value--element}

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

## Padres {#parents-16}

`<enumeration>`

## Niños {#children-16}

`<help>`

## Descripción {#description-16}

Este elemento permite definir los valores almacenados en una enumeración.

## Descripción de atributo {#attribute-description-16}

* **applyIf (cadena)**: este atributo permite hacer que un valor de enumeración sea opcional. Recibe una expresión XTK.
* **desc (cadena)**: descripción del valor de enumeración.
* **enabledIf (cadena)**: condición para activar el valor de enumeración.
* **img (cadena)**: imagen vinculada a la enumeración en el formulario &quot;namespace:image_name&quot;. La imagen debe importarse en el servidor de aplicaciones.
* **label (cadena)**: etiqueta del valor de enumeración.
* **nombre (cadena)**: nombre interno del valor de enumeración.
* **valor (cadena)**: del valor de enumeración. El tipo de valor se define en función del tipo de enumeración. Si la enumeración es de tipo cadena de caracteres, solo puede contener valores de tipo cadena de caracteres.

## Ejemplos {#examples-13}

```
<enumeration name="myEnum">
       <value name="One" value="1"/>
       <value name="Two" value="2"/>
    </enumeration>
```
