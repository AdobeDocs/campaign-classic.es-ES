---
product: campaign
title: Falta de imágenes
description: Falta de imágenes
feature: Monitoring
audience: production
content-type: reference
topic-tags: troubleshooting
exl-id: 6ccda57d-f7a3-4501-b2f4-59fcb05f9013
TQID: https://experienceleague.adobe.com/GDlcjvzSGP70FlVGHmnhJHsqC3SFG5Y-kQOohR00j8c
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
topic_v2:
  - id: c1579802-ddd4-4214-8a91-97b2066abe11
feature_v2: []
subfeature_v2:
  - id: c03a11ff-bdf9-4e5b-b279-f468b4293464
  - id: e519a22f-a06a-42fc-9d09-d78a3ab2c434
source-git-commit: 38eab6b8da73163e4476e91c0ef73f25c3f57546
workflow-type: tm+mt
source-wordcount: 111
ht-degree: 5%

---

# Falta de imágenes{#images-missing}



En la versión 17.9, se han movido varios archivos (iconos en particular).

Para los clientes alojados, no hay ningún impacto. Para instalaciones on-premise, lea lo siguiente.

**Usuarios de Apache:**

Los usuarios de Apache no se verán afectados si usan el **apache_neolane.conf** proporcionado.

**usuarios de IIS:**

Para los usuarios de IIS (en Windows), después de la actualización de la compilación, aparecerán varios iconos que faltan en la consola. Se requieren pasos de actualización de IIS adicionales:

1. Después de la actualización de la compilación, haga doble clic en **iis_neolane_setup.vbs**, que se encuentra en el directorio de instalación de Campaign. La ruta predeterminada es C:\Program Files (x86)\Adobe\Adobe Campaign v7\conf
1. Reinicie el sitio de IIS que se haya actualizado en el paso anterior.
