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
source-wordcount: '92'
ht-degree: 10%

---


# `<condition>` Elemento {#condition--element}

## Modelo de contenido {#content-model-2}

condición:==EMPTY

## Atributos {#attributes-2}

* @boolOperator (cadena)
* @enabledIf (cadena)
* @expr (cadena)

## Padres {#parents-2}

`<sysfilter>`

## Niños {#children-2}

Ninguno

## Descripción {#description-2}

Este elemento permite definir una condición de filtrado.

## Uso y contexto de uso {#use-and-context-of-use-2}

Un elemento `<sysfiler>` puede contener varias condiciones de filtrado.

## Descripción del atributo {#attribute-description-2}

* **boolOperator (cadena)**: si  `<conditions>` se definen varios dentro del mismo   `<sysfilter>` elemento, este atributo permite combinarlos. De forma predeterminada, el vínculo lógico está entre `<condition>` elementos es &quot;AND&quot;. El atributo &quot;@boolOperator&quot; permite combinar vínculos de tipo &quot;O&quot; y &quot;Y&quot;.
* **enabledIf (string)**: prueba de activación de condición.
* **expr (cadena)**: una expresión XTK.

## Ejemplos {#examples-2}

```
<sysfilter>
  <condition enabledIf="hasNamedRight('admin')=false" expr="@city=[currentOperator/location/@city]" />
</sysfilter>
```
