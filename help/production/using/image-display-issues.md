---
product: campaign
title: Problemas de visualización de imágenes
description: Problemas de visualización de imágenes
audience: production
content-type: reference
topic-tags: troubleshooting
exl-id: 62fa491e-3e83-422b-bcde-2bae2c1b676e
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: tm+mt
source-wordcount: '133'
ht-degree: 6%

---

# Problemas de visualización de imágenes{#image-display-issues}

Si tiene problemas de visualización de imágenes en un mensaje enviado, las razones pueden estar vinculadas a una ubicación incorrecta:

* Es posible que las ubicaciones no coincidan o que las imágenes no se hayan insertado correctamente en el servidor de seguimiento duplicado: compruebe su configuración.
* Es posible que las imágenes no residan en la carpeta de recursos públicos de la instancia de marketing: cargue las imágenes en la carpeta de recursos para resolver el problema.
* Si trabaja en una arquitectura intermediaria: compruebe que las imágenes se carguen sin errores cuando se envían pruebas (la información se muestra en los registros de análisis).

Solución de problemas:

1. Envíe una prueba que muestre las imágenes.
1. Valide que la configuración de recursos en la configuración de instancias es correcta.
1. Compruebe la carpeta de recursos públicos o, si no está en la carpeta de recursos públicos, la carpeta a la que se hace referencia en la entrega.
