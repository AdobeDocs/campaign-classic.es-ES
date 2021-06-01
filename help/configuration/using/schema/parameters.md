---
product: campaign
title: Elementos y atributos
description: Elementos y atributos
audience: configuration
content-type: reference
topic-tags: schema-reference
exl-id: 54538c3e-3232-4bf7-a09c-dacf0f072be5
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: tm+mt
source-wordcount: '46'
ht-degree: 21%

---

# elemento de parámetros {#parameters--element}

## Modelo de contenido {#content-model-13}

parámetros:==param

## Atributos {#attributes-13}

Ninguno

## Padres {#parents-13}

`<method>`

## Niños {#children-13}

`<param>`

## Descripción {#description-13}

Este elemento define un grupo de `<parameter>` elementos.

## Uso y contexto de uso {#use-and-context-of-use-8}

Este elemento es obligatorio, incluso para un solo elemento `<param>` secundario del elemento `<method>` .

## Descripción de atributo {#attribute-description-13}

Ninguno

## Ejemplos {#examples-10}

```
<parameters
... //definition of one or more <param
</parameters>
```
