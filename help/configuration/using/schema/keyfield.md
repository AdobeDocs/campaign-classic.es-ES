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
source-wordcount: '100'
ht-degree: 10%

---


# `<keyfield>` Elemento {#keyfield--element}

## Modelo de contenido {#content-model-9}

keyfield:==EMPTY

## Atributos {#attributes-9}

* @xlink (MNTOKEN)
* @xpath (MNTOKEN)

## Padres {#parents-9}

`<key>`  ,  `<dbindex />`

## Niños {#children-9}

Ninguno

## Descripción {#description-9}

Este elemento define los campos que se integrarán en un índice o una clave.

## Descripción del atributo {#attribute-description-9}

* **xlink (MNTOKEN)**: permite hacer referencia automáticamente a claves externas definidas en la unión para una tabla de relación (vínculo N-N).
* **xpath (MNTOKEN)**: definición de un índice o una clave en un  `<attribute>`  elemento. Este atributo recibe un Xpath que define la ruta al atributo esquema que define la clave o el índice.

## Ejemplos {#examples-}

Selección del campo &quot;sName&quot; en un índice con una Xpath en &quot;@name&quot;:

```
<keyfield xpath="@name"/>
```
