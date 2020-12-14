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
source-wordcount: '46'
ht-degree: 21%

---


# elemento de parámetros {#parameters--element}

## Modelo de contenido {#content-model-13}

parameters:==param

## Atributos {#attributes-13}

Ninguno

## Padres {#parents-13}

`<method>`

## Niños {#children-13}

`<param>`

## Descripción {#description-13}

Este elemento define un grupo de `<parameter>` elementos.

## Uso y contexto de uso {#use-and-context-of-use-8}

Este elemento es obligatorio, incluso para un solo elemento secundario `<param>` del elemento `<method>`.

## Descripción del atributo {#attribute-description-13}

Ninguno

## Ejemplos {#examples-10}

```
<parameters
... //definition of one or more <param
</parameters>
```
