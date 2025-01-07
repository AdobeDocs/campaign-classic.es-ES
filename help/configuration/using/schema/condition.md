---
product: campaign
title: 'Elementos y atributos de esquema: elemento de condición'
description: elemento condición
feature: Schema Extension
exl-id: 71e98d45-3660-4d86-a5ca-8e55ae5896eb
source-git-commit: 254c89490fefa5d405bcecd2f1781df46450a873
workflow-type: tm+mt
source-wordcount: '95'
ht-degree: 5%

---

# elemento condición {#condition--element}


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

Un elemento `<sysfiler>` puede contener varias condiciones de filtrado.

## Descripción de atributo {#attribute-description-2}

* **boolOperator (string)**: si se definen varios `<conditions>` dentro del mismo elemento `<sysfilter>`, este atributo le permite combinarlos. De manera predeterminada, el vínculo lógico está entre `<condition>` elementos y es &quot;AND&quot;. El atributo &quot;@boolOperator&quot; permite combinar vínculos de tipo &quot;OR&quot; y &quot;AND&quot;.
* **enabledIf (string)**: prueba de activación de condición.
* **expr (cadena)**: una expresión XTK.

## Ejemplos {#examples-2}

```
<sysfilter>
  <condition enabledIf="hasNamedRight('admin')=false" expr="@city=[currentOperator/location/@city]" />
</sysfilter>
```
