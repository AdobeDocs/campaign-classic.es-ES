---
product: campaign
title: Introducción a los esquemas en Adobe Campaign
description: Aprenda a trabajar con esquemas y a ampliar el modelo de datos conceptuales de la base de datos de Adobe Campaign
feature: Schema Extension
role: Developer
level: Intermediate, Experienced
exl-id: f36a1b01-a002-4a21-9255-ea78b5f173fe
TQID: 'https://experienceleague.adobe.com/ikQVjdkvhTM-361S7mcpRYsuhpqjHxX-Y-9wdRCYldg'
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
  - id: cfc95e9b-b035-4403-a6a9-b27a8a053a37
    internal-label: PI
role_v2:
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
level_v2:
  - id: b5a62a22-46f7-4f0d-b151-3fc640bef588
    internal-label: Intermediate
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: a97306b73a2b577841e6f24536c62b2526e9fda9
workflow-type: tm+mt
source-wordcount: '264'
ht-degree: 16%
---
# Introducción a los esquemas {#about-schema-reference}

## Qué es un esquema {#what-is-a-schema}

En este capítulo se describe cómo configurar esquemas de extensión para ampliar el modelo de datos conceptuales de la base de datos de Adobe Campaign.

Para comprender mejor las tablas integradas de Campaign y su interacción, consulte [Modelo de datos de Campaign Classic](https://experienceleague.adobe.com/es/docs/campaign/campaign-v8/developer/datamodel){target="_blank"} (documentación de Campaign v8).

En Adobe Campaign, la estructura física y lógica de los datos que se llevan en la aplicación se describe en XML. Un **esquema** es un documento XML asociado a una tabla de base de datos. Define la estructura de datos y describe la definición SQL de la tabla:

* Nombre de la tabla
* Campos
* Índices
* Vínculos con otras tablas

También describe la estructura XML utilizada para almacenar datos:

* Elementos y atributos
* Jerarquía de elementos
* Tipos de elementos y atributos
* Valores predeterminados
* Etiquetas, descripciones y otras propiedades.

Los esquemas permiten definir una entidad en la base de datos. Hay un esquema para cada entidad.

La siguiente ilustración muestra la ubicación de los esquemas en el sistema de datos de Adobe Campaign:

![](assets/reference_schema_intro.png)

Como parte de la transición de Campaign v7 a v8, el conjunto de documentación de Campaign Classic se ha optimizado y reorganizado. Ahora, las funciones comunes solo están disponibles en el conjunto de documentación de Campaign v8. Para obtener más información sobre la sintaxis y la identificación de esquemas, consulte la [documentación de Campaign v8](https://experienceleague.adobe.com/es/docs/campaign/campaign-v8/developer/schemas-forms/schemas){target=_blank}.

[![imagen](../../assets/do-not-localize/learn-more-button.svg)](https://experienceleague.adobe.com/es/docs/campaign/campaign-v8/developer/schemas-forms/schemas){target=_blank}
