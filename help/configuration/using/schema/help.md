---
solution: Campaign Classic
product: campaign
title: Elementos y atributos
description: Elementos y atributos
audience: configuration
content-type: reference
topic-tags: schema-reference
translation-type: tm+mt
source-git-commit: 1818bd2aeb60689b2ce0e59cb0bd157f000de513
workflow-type: tm+mt
source-wordcount: '46'
ht-degree: 23%

---


# `<help>` Elemento {#help--element}

## Modelo de contenido {#content-model-6}

help:==EMPTY

## Atributos {#attributes-6}

Ninguno

## Padres {#parents-6}

`<srcschema>`  ,   `<element>`   ,    `<attribute>`    ,     `<enumeration>`     ,      `<value>`      ,      `<param />`,       `<method />`

## Niños {#children-6}

Ninguno

## Descripción {#description-6}

Este elemento permite describir un `<element>` o `<attribute>`   elemento. Sólo puede contener texto y se almacena en XML en la base de datos.

## Descripción del atributo {#attribute-description-6}

Este elemento no tiene atributos.

## Ejemplos {#examples-5}

```
<method name="CheckOperation" static="true"
      <helpchecks the validity of a campaign</help
...
</method> 
```
