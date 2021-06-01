---
product: campaign
title: Elementos y atributos
description: Elementos y atributos
audience: configuration
content-type: reference
topic-tags: schema-reference
exl-id: fb0862f9-5dcc-49f2-b99b-9822aaf3a680
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: tm+mt
source-wordcount: '101'
ht-degree: 8%

---

# elemento de campo clave {#keyfield--element}

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

Este elemento define los campos que se van a integrar en un índice o una clave.

## Descripción de atributo {#attribute-description-9}

* **xlink (MNTOKEN)**: permite hacer referencia automáticamente a claves externas definidas en la unión para una tabla de relación (vínculo N-N).
* **xpath (MNTOKEN)**: definición de un índice o una clave en un  `<attribute>`  elemento. Este atributo recibe una Xpath que define la ruta al atributo schema que define la clave o el índice.

## Ejemplos {#examples-}

Selección del campo &quot;sName&quot; en un índice con una Xpath en &quot;@name&quot;:

```
<keyfield xpath="@name"/>
```
