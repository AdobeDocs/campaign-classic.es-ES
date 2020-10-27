---
title: Falta de imágenes
seo-title: Falta de imágenes
description: Falta de imágenes
seo-description: null
page-status-flag: never-activated
uuid: 0dc73ea0-70bc-476d-bdff-2e62d6929f21
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: production
content-type: reference
topic-tags: troubleshooting
discoiquuid: e001db7a-7c53-477e-a534-ce4d83d68559
translation-type: tm+mt
source-git-commit: d509dc584cd4ae17c6dda85c09fceee8c6162dba
workflow-type: tm+mt
source-wordcount: '114'
ht-degree: 7%

---


# Falta de imágenes{#images-missing}

En la versión 17.9, se han movido varios archivos (iconos en particular).

Para los clientes alojados, no hay ningún impacto. Para las instalaciones in situ, lea lo siguiente.

**Usuarios de Apache:**

No hay ningún impacto para los usuarios de Apache si utilizan el **apache_neolane.conf proporcionado**

**Usuarios de IIS:**

Para los usuarios de IIS (en Windows), aparecerán varios iconos en la consola después de la actualización de compilación. Se requieren pasos adicionales de actualización de IIS:

1. Después de la actualización de la compilación, haga clic con el doble en **iis_neolane_setup.vbs** , que se encuentra en el directorio de instalación de la Campaña. La ruta predeterminada es C:\Program Files (x86)\Adobe\Adobe Campaign v7\conf
1. Reinicie el sitio de IIS que se ha actualizado en el paso anterior.

