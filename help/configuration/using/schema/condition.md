---
product: campaign
title: 'Elementos y atributos de esquema: elemento de condición'
description: elemento condición
exl-id: 71e98d45-3660-4d86-a5ca-8e55ae5896eb
source-git-commit: 40da5774c8a6a228992c4aa400e2d9924215611e
workflow-type: tm+mt
source-wordcount: '95'
ht-degree: 5%

---

# elemento condición {#condition--element}

![](../../../assets/v7-only.svg)

## Modelo de contenido {#content-model-2}

condición:==VACÍO

## Atributos {#attributes-2}

* @boolOperator (cadena)
* @enabledIf (cadena)
* @expr (cadena)

## Padres {#parents-2}

`<sysfilter>`

## Tareas secundarias {#children-2}

Ninguno

## Descripción {#description-2}

Este elemento permite definir una condición de filtrado.

## Uso y contexto de uso {#use-and-context-of-use-2}

Uno `<sysfiler>`  puede contener varias condiciones de filtrado.

## Descripción de atributo {#attribute-description-2}

* **boolOperator (cadena)**: si hay varios `<conditions>` se definen dentro del mismo  `<sysfilter>` , este atributo permite combinarlos. De forma predeterminada, el vínculo lógico es entre `<condition>` elementos es &quot;Y&quot;. El atributo &quot;@boolOperator&quot; permite combinar vínculos de tipo &quot;OR&quot; y &quot;AND&quot;.
* **enabledIf (cadena)**: prueba de activación de condición.
* **expr (cadena)**: una expresión XTK.

## Ejemplos {#examples-2}

```
<sysfilter>
  <condition enabledIf="hasNamedRight('admin')=false" expr="@city=[currentOperator/location/@city]" />
</sysfilter>
```
