---
product: campaign
title: 'Elementos y atributos: elemento sysfilter'
description: Elementos y atributos
feature: Schema Extension
audience: configuration
content-type: reference
topic-tags: schema-reference
exl-id: a0069688-fd05-42e9-91dd-adc10bea3461
TQID: https://experienceleague.adobe.com/hjsD-JSGBPnwyj1IsLDo-tUy-63apy0-6kT9vngaaQk
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
feature_v2: []
subfeature_v2: []
source-git-commit: bb41e9407ab5853b0194bb325bbf3f17bc3ea232
workflow-type: tm+mt
source-wordcount: 45
ht-degree: 17%

---

# elemento sysfilter {#sysfilter--element}


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
