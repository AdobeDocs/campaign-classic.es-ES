---
product: campaign
title: 'Elementos y atributos: elemento de valor'
description: Elementos y atributos
feature: Schema Extension
audience: configuration
content-type: reference
topic-tags: schema-reference
exl-id: bad7fb4b-43d9-4033-ae0d-cf191d89114b
TQID: 'https://experienceleague.adobe.com/rGaA--VHVGxCBHX5SgZUQQ9AwMgOTYWqMYGpYWU4-WY'
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
    internal-label: Campaign
  - id: fd6e6e36-54e4-4f1a-96fc-1a750e400d50
    internal-label: Campaign Classic v7
feature_v2:
  - id: b82389f8-9b5e-4083-8e3b-3cef299fb8b9
    internal-label: Schemas
subfeature_v2:
  - id: a72a22e0-8c8d-4019-ba42-3f2644aa91a3
    internal-label: Schema extension
source-git-commit: a43e591a565a18d79f583d975e3e812c5435b0c0
workflow-type: tm+mt
source-wordcount: '147'
ht-degree: 4%
---
# elemento de valor {#value--element}


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

* **applyIf (string)**: este atributo permite hacer opcional un valor de enumeración. Recibe una expresión XTK.
* **desc (cadena)**: descripción del valor de enumeración.
* **enabledIf (string)**: condición para activar el valor de enumeración.
* **img (string)**: imagen vinculada a la enumeración en el formulario &quot;namespace:image_name&quot;. La imagen debe importarse en el servidor de aplicaciones.
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
