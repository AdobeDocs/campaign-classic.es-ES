---
product: campaign
title: 'Elementos y atributos de esquema: elemento keyfield'
description: elemento keyfield
feature: Schema Extension
exl-id: fb0862f9-5dcc-49f2-b99b-9822aaf3a680
TQID: 'https://experienceleague.adobe.com/tVWLlgg97dREZZHvUW81FhDVhS-uNvUHlbhH0YBrAdY'
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
    internal-label: Campaign
  - id: fd6e6e36-54e4-4f1a-96fc-1a750e400d50
    internal-label: Campaign Classic v7
feature_v2:
  - id: b82389f8-9b5e-4083-8e3b-3cef299fb8b9
    internal-label: Schemas
subfeature_v2:
  - id: a72a22e0-8c8d-4019-ba42-3f2644aa91a3
    internal-label: Schema extension
source-git-commit: a43e591a565a18d79f583d975e3e812c5435b0c0
workflow-type: tm+mt
source-wordcount: '106'
ht-degree: 6%
---
# elemento keyfield {#keyfield--element}


## Modelo de contenido {#content-model-9}

keyfield:==EMPTY

## Atributos {#attributes-9}

* @xlink (TOKEN MENÚ)
* @xpath (TOKEN MENÚ)

## Padres {#parents-9}

`<key>`  ,  `<dbindex />`

## Tareas secundarias {#children-9}

Ninguno

## Descripción {#description-9}

Este elemento define los campos que se van a integrar en un índice o una clave.

## Descripción de atributo {#attribute-description-9}

* **xlink (MNTOKEN)**: permite hacer referencia automáticamente a las claves externas definidas en la unión para una tabla de relación (vínculo N-N).
* **xpath (MNTOKEN)**: definición de un índice o clave en un elemento `<attribute>`. Este atributo recibe un Xpath que define la ruta al atributo de esquema que define la clave o el índice.

## Ejemplos {#examples-}

Selección del campo &quot;sName&quot; en un índice con un Xpath en &quot;@name&quot;:

```
<keyfield xpath="@name"/>
```
