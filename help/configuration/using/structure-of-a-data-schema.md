---
product: campaign
title: Estructura de un esquema de datos
description: Estructura de un esquema de datos
feature: Custom Resources
role: Developer
exl-id: 86036f2f-ec7c-413e-b1e1-10a71a06cd6d
TQID: https://experienceleague.adobe.com/bp-x2YrBY5WzNVTXJjpzdZgG45vNPPG9-z339I9U5Lw
product_v2: id: dfc56824-e8b9-499e-85d4-21aedb507314
role_v2: id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
feature_v2: []
subfeature_v2: []
source-git-commit: bb41e9407ab5853b0194bb325bbf3f17bc3ea232
workflow-type: tm+mt
source-wordcount: 142
ht-degree: 10%

---

# Estructura de un esquema de datos{#structure-of-a-data-schema}

La estructura de un esquema de datos se muestra en forma de estructura de árbol. Para verlo gráficamente en la consola del cliente de Adobe Campaign, seleccione el esquema de destino y haga clic en la subpestaña **[!UICONTROL Structure]**.

![](assets/d_ncs_integration_schema_arbo.png)

Como estándar, los campos se muestran primero (Activo, Activado, etc.) y en orden alfabético. Los elementos de estructuración vienen después (dirección postal, ubicación) y, por último, los vínculos (información de correo electrónico, carpeta, etc.).

Las claves principales se identifican con una clave roja y las claves externas con una clave amarilla.

Los vínculos se distinguen gráficamente en función de si pertenecen a la tabla. Las que comienzan desde la tabla, es decir, que tienen la clave externa en la tabla, se muestran primero (Información de correo electrónico, Carpeta, País). Vínculos de recopilación &quot;Invertir&quot; (suscripción, pedidos, etc.) se muestran al final.
