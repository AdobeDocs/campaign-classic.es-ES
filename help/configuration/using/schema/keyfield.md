---
product: campaign
title: 'Elementos y atributos de esquema: elemento de campo clave'
description: elemento keyfield
exl-id: fb0862f9-5dcc-49f2-b99b-9822aaf3a680
source-git-commit: 40da5774c8a6a228992c4aa400e2d9924215611e
workflow-type: tm+mt
source-wordcount: '103'
ht-degree: 2%

---

# elemento keyfield {#keyfield--element}

![](../../../assets/v7-only.svg)

## Modelo de contenido {#content-model-9}

keyfield:==EMPTY

## Atributos {#attributes-9}

* @xlink (MNTOKEN)
* @xpath (MNTOKEN)

## Principales {#parents-9}

`<key>`  ,  `<dbindex />`

## Niños {#children-9}

Ninguno

## Descripción {#description-9}

Este elemento define los campos que se van a integrar en un índice o una clave.

## Descripción del atributo {#attribute-description-9}

* **xlink (MNTOKEN)**: permite hacer referencia automáticamente a claves externas definidas en la unión para una tabla de relación (vínculo N-N).
* **xpath (MNTOKEN)**: definición de un índice o una clave en una `<attribute>`  elemento. Este atributo recibe una Xpath que define la ruta al atributo schema que define la clave o el índice.

## Ejemplos {#examples-}

Selección del campo &quot;sName&quot; en un índice con una Xpath en &quot;@name&quot;:

```
<keyfield xpath="@name"/>
```
