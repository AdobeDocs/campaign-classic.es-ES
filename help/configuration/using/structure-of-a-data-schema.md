---
product: campaign
title: Estructura de un esquema de datos
description: Estructura de un esquema de datos
feature: Custom Resources
role: Developer
exl-id: 86036f2f-ec7c-413e-b1e1-10a71a06cd6d
source-git-commit: 9f5205ced6b8d81639d4d0cb6a76905a753cddac
workflow-type: tm+mt
source-wordcount: '141'
ht-degree: 10%

---

# Estructura de un esquema de datos{#structure-of-a-data-schema}

La estructura de un esquema de datos se muestra en forma de estructura de árbol. Para verlo gráficamente en la consola del cliente de Adobe Campaign, seleccione el esquema de destino y haga clic en la subpestaña **[!UICONTROL Structure]**.

![](assets/d_ncs_integration_schema_arbo.png)

Como estándar, los campos se muestran primero (Activo, Activado, etc.) y en orden alfabético. Los elementos de estructuración vienen después (dirección postal, ubicación) y, por último, los vínculos (información de correo electrónico, carpeta, etc.).

Las claves principales se identifican con una clave roja y las claves externas con una clave amarilla.

Los vínculos se distinguen gráficamente en función de si pertenecen a la tabla. Las que comienzan desde la tabla, es decir, que tienen la clave externa en la tabla, se muestran primero (Información de correo electrónico, Carpeta, País). Los vínculos de recopilación &quot;Invertir&quot; (Suscripción, Pedidos, etc.) se muestran al final.
