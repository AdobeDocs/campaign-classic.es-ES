---
title: Estructura de un esquema de datos
seo-title: Estructura de un esquema de datos
description: Estructura de un esquema de datos
seo-description: null
page-status-flag: never-activated
uuid: 83e3995d-fa31-4cb5-acf2-83f17329c99c
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: configuration
content-type: reference
topic-tags: editing-schemas
discoiquuid: a1a39eaa-6d6f-42c5-a36b-bd1cb3a77dcb
translation-type: tm+mt
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: tm+mt
source-wordcount: '146'
ht-degree: 13%

---


# Estructura de un esquema de datos{#structure-of-a-data-schema}

La estructura de un esquema de datos se muestra en forma de estructura de árbol. Para vista gráfica en la consola de cliente de Adobe Campaign, seleccione el esquema de destino y haga clic en la **[!UICONTROL Structure]** subficha.

![](assets/d_ncs_integration_schema_arbo.png)

Como estándar, los campos se muestran primero (Activo, Activado, etc.) y en orden alfabético. Los elementos de estructuración vienen a continuación (dirección postal, ubicación) y finalmente los vínculos (información de correo electrónico, carpeta, etc.).

Las claves principales se identifican con una clave roja y las claves externas con una clave amarilla.

Los vínculos se distinguen gráficamente en función de si pertenecen a la tabla. Los inicios de la tabla, es decir, que tienen la clave externa en la tabla, se muestran primero (Información de correo electrónico, Carpeta, País). Vínculos de recopilación &quot;inversos&quot; (Suscripción, Pedidos, etc.) se muestran al final.
