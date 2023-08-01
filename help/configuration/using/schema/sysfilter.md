---
product: campaign
title: 'Elementos y atributos: elemento sysfilter'
description: Elementos y atributos
feature: Schema Extension
audience: configuration
content-type: reference
topic-tags: schema-reference
exl-id: a0069688-fd05-42e9-91dd-adc10bea3461
source-git-commit: fd5e4bbc87a48f029a09b14ab1d927b9afe4ac52
workflow-type: tm+mt
source-wordcount: '45'
ht-degree: 17%

---

# elemento sysfilter {#sysfilter--element}

![](../../../assets/v7-only.svg)

## Modelo de contenido {#content-model-15}

sysFilter:==condición

## Atributos {#attributes-15}

Ninguno

## Padres {#parents-15}

`<element>`

## Tareas secundarias {#children-15}

`<condition>`

## Descripción {#description-15}

Este elemento permite definir un filtro.

## Descripción de atributo {#attribute-description-15}

Este elemento no tiene atributos.

## Ejemplos {#examples-12}

Definición de un filtro con una condición en el atributo @name:

```
<sysFilter>
      <condition expr="@name ='Doe'"/>
  <sysFilter>
```
