---
product: campaign
title: 'Elementos y atributos: elemento sysfilter'
description: Elementos y atributos
audience: configuration
content-type: reference
topic-tags: schema-reference
exl-id: a0069688-fd05-42e9-91dd-adc10bea3461
source-git-commit: 40da5774c8a6a228992c4aa400e2d9924215611e
workflow-type: tm+mt
source-wordcount: '45'
ht-degree: 13%

---

# elemento sysfilter {#sysfilter--element}

![](../../../assets/v7-only.svg)

## Modelo de contenido {#content-model-15}

sysFilter:==condition

## Atributos {#attributes-15}

Ninguno

## Principales {#parents-15}

`<element>`

## Niños {#children-15}

`<condition>`

## Descripción {#description-15}

Este elemento permite definir un filtro.

## Descripción del atributo {#attribute-description-15}

Este elemento no tiene atributos.

## Ejemplos {#examples-12}

Definición de un filtro con una condición en el atributo @name:

```
<sysFilter>
      <condition expr="@name ='Doe'"/>
  <sysFilter>
```
