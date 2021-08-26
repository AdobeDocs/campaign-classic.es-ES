---
product: campaign
title: Elementos y atributos
description: Elementos y atributos
audience: configuration
content-type: reference
topic-tags: schema-reference
exl-id: 8207868c-25ff-4ca9-afdd-41b324c7ac0d
source-git-commit: 34404fbe935e68f3cc11d937839209443ad4ca60
workflow-type: tm+mt
source-wordcount: '47'
ht-degree: 21%

---

# elemento de ayuda {#help--element}

![](../../../assets/v7-only.svg)

## Modelo de contenido {#content-model-6}

ayuda:==EMPTY

## Atributos {#attributes-6}

Ninguno

## Principales {#parents-6}

`<srcschema>`  ,   `<element>`   ,    `<attribute>`    ,     `<enumeration>`     ,      `<value>`      ,      `<param />`,       `<method />`

## Niños {#children-6}

Ninguno

## Descripción {#description-6}

Este elemento permite describir una `<element>` o `<attribute>`   elemento. Solo puede contener texto y se almacena en XML en la base de datos.

## Descripción del atributo {#attribute-description-6}

Este elemento no tiene atributos.

## Ejemplos {#examples-5}

```
<method name="CheckOperation" static="true"
      <helpchecks the validity of a campaign</help
...
</method> 
```
