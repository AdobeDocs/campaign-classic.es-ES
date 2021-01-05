---
solution: Campaign Classic
product: campaign
title: Falta de imágenes
description: Falta de imágenes
audience: production
content-type: reference
topic-tags: troubleshooting
translation-type: tm+mt
source-git-commit: 50f95d7156e7104d90fa7a31eea30711b9c11bbf
workflow-type: tm+mt
source-wordcount: '111'
ht-degree: 5%

---


# Falta de imágenes{#images-missing}

En la versión 17.9, se han movido varios archivos (iconos en particular).

Para los clientes alojados, no hay ningún impacto. Para las instalaciones in situ, lea lo siguiente.

**Usuarios de Apache:**

No hay impacto para los usuarios de Apache si utilizan el **apache_neolane.conf** proporcionado.

**Usuarios de IIS:**

Para los usuarios de IIS (en Windows), aparecerán varios iconos en la consola después de la actualización de compilación. Se requieren pasos adicionales de actualización de IIS:

1. Después de la actualización de la compilación, haga clic con el doble **iis_neolane_setup.vbs** ubicado en el directorio de instalación de la Campaña. La ruta predeterminada es C:\Program Files (x86)\Adobe\Adobe Campaign v7\conf
1. Reinicie el sitio de IIS que se ha actualizado en el paso anterior.
