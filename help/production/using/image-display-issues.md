---
product: campaign
title: Problemas de visualización de imágenes
description: Problemas de visualización de imágenes
feature: Monitoring
audience: production
content-type: reference
topic-tags: troubleshooting
exl-id: 62fa491e-3e83-422b-bcde-2bae2c1b676e
TQID: https://experienceleague.adobe.com/aBPQb0Yp8o7goe2CS4h6ydnZV5gjPYINHMxGcc-d140
product_v2: id: dfc56824-e8b9-499e-85d4-21aedb507314
topic_v2: id: c1579802-ddd4-4214-8a91-97b2066abe11
feature_v2: []
subfeature_v2: id: c03a11ff-bdf9-4e5b-b279-f468b4293464id: e519a22f-a06a-42fc-9d09-d78a3ab2c434
source-git-commit: 38eab6b8da73163e4476e91c0ef73f25c3f57546
workflow-type: tm+mt
source-wordcount: 134
ht-degree: 6%

---

# Problemas de visualización de imágenes{#image-display-issues}



Si tiene problemas de visualización de imágenes en un mensaje enviado, los motivos pueden estar vinculados a una ubicación incorrecta:

* Es posible que las ubicaciones no coincidan o que las imágenes no se hayan insertado correctamente en el servidor de seguimiento de duplicados: compruebe la configuración.
* Es posible que las imágenes no residan en la carpeta de recursos públicos de la instancia de marketing: cargue las imágenes en la carpeta de recursos para resolver el problema.
* Si trabaja en una arquitectura intermediaria: compruebe que las imágenes se cargan sin errores cuando se envían las pruebas (la información se muestra en los registros de análisis).

Cómo solucionar problemas:

1. Envíe una prueba que muestre las imágenes.
1. Valide que la configuración de recursos en la configuración de la instancia sea correcta.
1. Compruebe la carpeta de recursos públicos o, si no está en la carpeta de recursos públicos, la carpeta a la que se hace referencia en la entrega.
