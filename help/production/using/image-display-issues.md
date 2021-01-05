---
solution: Campaign Classic
product: campaign
title: Problemas de visualización de imágenes
description: Problemas de visualización de imágenes
audience: production
content-type: reference
topic-tags: troubleshooting
translation-type: tm+mt
source-git-commit: 50f95d7156e7104d90fa7a31eea30711b9c11bbf
workflow-type: tm+mt
source-wordcount: '133'
ht-degree: 6%

---


# Problemas de visualización de imágenes{#image-display-issues}

Si tiene problemas con la visualización de imágenes en un mensaje enviado, es posible que las razones estén vinculadas a una ubicación incorrecta:

* Es posible que las ubicaciones no coincidan o que las imágenes no se hayan insertado correctamente en el servidor de seguimiento de duplicado: compruebe su configuración.
* Es posible que las imágenes no residan en la carpeta recurso público de la instancia de marketing: cargue las imágenes en la carpeta de recursos para resolver el problema.
* Si trabaja en una arquitectura intermediaria: comprobar que las imágenes se cargan sin errores cuando se envían pruebas (la información se muestra en los registros de análisis).

Cómo solucionar problemas:

1. Envíe una prueba que muestre las imágenes.
1. Valide la configuración de los recursos en la configuración de la instancia es correcta.
1. Compruebe la carpeta recursos públicos o, si no se encuentra en la carpeta recursos públicos, la carpeta a la que se hace referencia en el envío.
