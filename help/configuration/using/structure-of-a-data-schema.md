---
product: campaign
title: Estructura de un esquema de datos
description: Estructura de un esquema de datos
audience: configuration
content-type: reference
topic-tags: editing-schemas
exl-id: 86036f2f-ec7c-413e-b1e1-10a71a06cd6d
source-git-commit: f000cb8bae164c22d1ede15db4e763cf50530674
workflow-type: tm+mt
source-wordcount: '141'
ht-degree: 10%

---

# Estructura de un esquema de datos{#structure-of-a-data-schema}

![](../../assets/v7-only.svg)

La estructura de un esquema de datos se muestra en forma de estructura de árbol. Para verla gráficamente en la consola del cliente de Adobe Campaign, seleccione el esquema de destino y haga clic en el botón **[!UICONTROL Structure]** subpestaña .

![](assets/d_ncs_integration_schema_arbo.png)

Como estándar, los campos se muestran primero (Activo, Activado, etc.) y en orden alfabético. Los elementos de estructuración vienen a continuación (dirección postal, ubicación) y finalmente los vínculos (información de correo electrónico, carpeta, etc.).

Las claves principales se identifican con una clave roja, mientras que las claves externas se identifican con una clave amarilla.

Los vínculos se distinguen gráficamente en función de si pertenecen a la tabla. Los que comienzan desde la tabla, es decir, que tienen la clave externa en la tabla, se muestran primero (Información de correo electrónico, Carpeta, País). Vínculos de colección &quot;Invertir&quot; (suscripción, pedidos, etc.) se muestran al final.
