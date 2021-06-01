---
product: campaign
title: Falta de imágenes
description: Falta de imágenes
audience: production
content-type: reference
topic-tags: troubleshooting
exl-id: 6ccda57d-f7a3-4501-b2f4-59fcb05f9013
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: tm+mt
source-wordcount: '111'
ht-degree: 5%

---

# Falta de imágenes{#images-missing}

En la versión 17.9, se han movido varios archivos (iconos en particular).

Para los clientes alojados, no hay ningún impacto. Para las instalaciones in situ, lea lo siguiente.

**Usuarios de Apache:**

Los usuarios de Apache no se verán afectados si utilizan el **apache_neolane.conf** proporcionado.

**Usuarios de IIS:**

Para los usuarios de IIS (en Windows), aparecerán varios iconos en la consola tras la actualización de la compilación. Se requieren pasos adicionales de actualización de IIS:

1. Después de la actualización de la compilación, haga doble clic en **iis_neolane_setup.vbs**, ubicado en el directorio de instalación de Campaign. La ruta predeterminada es C:\Program Files (x86)\Adobe\Adobe Campaign v7\conf
1. Reinicie el sitio IIS que se actualizó en el paso anterior.
