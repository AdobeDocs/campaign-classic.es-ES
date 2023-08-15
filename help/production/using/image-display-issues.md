---
product: campaign
title: Problemas de visualización de imágenes
description: Problemas de visualización de imágenes
feature: Monitoring
badge-v7-only: label="v7" type="Informative" tooltip="Se aplica solo a Campaign Classic v7"
audience: production
content-type: reference
topic-tags: troubleshooting
exl-id: 62fa491e-3e83-422b-bcde-2bae2c1b676e
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: tm+mt
source-wordcount: '140'
ht-degree: 11%

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
