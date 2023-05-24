---
product: campaign
title: 'Elementos y atributos de esquema: elemento de ayuda '
description: elemento de ayuda
exl-id: 8207868c-25ff-4ca9-afdd-41b324c7ac0d
source-git-commit: 40da5774c8a6a228992c4aa400e2d9924215611e
workflow-type: tm+mt
source-wordcount: '49'
ht-degree: 12%

---

# elemento de ayuda {#help--element}

![](../../../assets/v7-only.svg)

## Modelo de contenido {#content-model-6}

ayuda:==VACÍO

## Atributos {#attributes-6}

Ninguno

## Padres {#parents-6}

`<srcschema>`  ,  `<element>`   ,   `<attribute>`    ,    `<enumeration>`     ,     `<value>`      ,     `<param />`,      `<method />`

## Tareas secundarias {#children-6}

Ninguno

## Descripción {#description-6}

Este elemento permite describir una `<element>`  o  `<attribute>`   Elemento. Solo puede contener texto y se almacena en XML en la base de datos.

## Descripción de atributo {#attribute-description-6}

Este elemento no tiene atributos.

## Ejemplos {#examples-5}

```
<method name="CheckOperation" static="true"
      <helpchecks the validity of a campaign</help
...
</method> 
```
