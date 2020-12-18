---
solution: Campaign Classic
product: campaign
title: Estructura de un esquema de datos
description: Estructura de un esquema de datos
audience: configuration
content-type: reference
topic-tags: editing-schemas
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '141'
ht-degree: 10%

---


# Estructura de un esquema de datos{#structure-of-a-data-schema}

La estructura de un esquema de datos se muestra en forma de estructura de árbol. Para vista gráfica en la consola de cliente de Adobe Campaign, seleccione el esquema de destino y haga clic en la subficha **[!UICONTROL Structure]**.

![](assets/d_ncs_integration_schema_arbo.png)

Como estándar, los campos se muestran primero (Activo, Activado, etc.) y en orden alfabético. Los elementos de estructuración vienen a continuación (dirección postal, ubicación) y finalmente los vínculos (información de correo electrónico, carpeta, etc.).

Las claves principales se identifican con una clave roja y las claves externas con una clave amarilla.

Los vínculos se distinguen gráficamente en función de si pertenecen a la tabla. Los inicios de la tabla, es decir, que tienen la clave externa en la tabla, se muestran primero (Información de correo electrónico, Carpeta, País). Vínculos de recopilación &quot;inversos&quot; (Suscripción, Pedidos, etc.) se muestran al final.
