---
product: campaign
title: 'Elementos y atributos de esquema: elemento keyfield'
description: elemento keyfield
feature: Schema Extension
exl-id: fb0862f9-5dcc-49f2-b99b-9822aaf3a680
source-git-commit: 254c89490fefa5d405bcecd2f1781df46450a873
workflow-type: tm+mt
source-wordcount: '103'
ht-degree: 4%

---

# elemento keyfield {#keyfield--element}


## Modelo de contenido {#content-model-9}

keyfield:==EMPTY

## Atributos {#attributes-9}

* @xlink (TOKEN MENÚ)
* @xpath (TOKEN MENÚ)

## Padres {#parents-9}

`<key>`, `<dbindex />`

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
