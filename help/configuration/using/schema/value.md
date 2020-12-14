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

Este elemento permite definir los valores almacenados en una lista desglosada.

## Descripción del atributo {#attribute-description-16}

* **applyIf (string)**: este atributo le permite convertir un valor de lista desglosada en opcional. Recibe una expresión XTK.
* **desc (cadena)**: descripción del valor de lista desglosada.
* **enabledIf (string)**: condición para activar el valor de lista desglosada.
* **img (cadena)**: imagen vinculada a la lista desglosada en el formulario &quot;Área de nombres:nombre_imagen&quot;. La imagen debe importarse en el servidor de aplicaciones.
* **label (string)**: del valor de lista desglosada.
* **name (string)**: nombre interno del valor de lista desglosada.
* **value (string)**: valor del valor de lista desglosada. El tipo de valor se define en función del tipo de lista desglosada. Si la lista desglosada es del tipo de cadena de caracteres, sólo puede contener valores de tipo de cadena de caracteres.

## Ejemplos {#examples-13}

```
<enumeration name="myEnum">
       <value name="One" value="1"/>
       <value name="Two" value="2"/>
    </enumeration>
```
