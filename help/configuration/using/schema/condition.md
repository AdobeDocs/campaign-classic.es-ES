---
product: campaign
title: Elementos y atributos
description: Elementos y atributos
audience: configuration
content-type: reference
topic-tags: schema-reference
exl-id: 71e98d45-3660-4d86-a5ca-8e55ae5896eb
source-git-commit: 34404fbe935e68f3cc11d937839209443ad4ca60
workflow-type: tm+mt
source-wordcount: '93'
ht-degree: 9%

---

# elemento de condición {#condition--element}

![](../../../assets/v7-only.svg)

## Modelo de contenido {#content-model-2}

condición:==EMPTY

## Atributos {#attributes-2}

* @boolOperator (cadena)
* @enabledIf (cadena)
* @expr (cadena)

## Principales {#parents-2}

`<sysfilter>`

## Niños {#children-2}

Ninguno

## Descripción {#description-2}

Este elemento permite definir una condición de filtrado.

## Uso y contexto de uso {#use-and-context-of-use-2}

Un elemento `<sysfiler>` puede contener varias condiciones de filtrado.

## Descripción del atributo {#attribute-description-2}

* **boolOperator (cadena)**: si  `<conditions>` se definen varios dentro del mismo   `<sysfilter>` elemento, este atributo permite combinarlos. De forma predeterminada, el vínculo lógico está entre `<condition>` elementos es &quot;AND&quot;. El atributo &quot;@boolOperator&quot; permite combinar vínculos de tipo &quot;O&quot; y &quot;Y&quot;.
* **enabledIf (cadena)**: prueba de activación de condición.
* **expr (cadena)**: una expresión XTK.

## Ejemplos {#examples-2}

```
<sysfilter>
  <condition enabledIf="hasNamedRight('admin')=false" expr="@city=[currentOperator/location/@city]" />
</sysfilter>
```
