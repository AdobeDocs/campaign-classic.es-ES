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
source-wordcount: '43'
ht-degree: 20%

---


# sysfilter elemento {#sysfilter--element}

## Modelo de contenido {#content-model-15}

sysFilter:==condition

## Atributos {#attributes-15}

Ninguno

## Padres {#parents-15}

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
