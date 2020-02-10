---
title: Faltan imágenes
seo-title: Faltan imágenes
description: Faltan imágenes
seo-description: null
page-status-flag: never-activated
uuid: 0dc73ea0-70bc-476d-bdff-2e62d6929f21
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: production
content-type: reference
topic-tags: troubleshooting
discoiquuid: e001db7a-7c53-477e-a534-ce4d83d68559
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 579329d9194115065dff2c192deb0376c75e67bd

---


# Faltan imágenes{#images-missing}

En la versión 17.9, se han movido varios archivos (iconos en particular).

Para los clientes alojados, no hay ningún impacto. Para las instalaciones in situ, lea lo siguiente.

**Usuarios de Apache:**

No hay ningún impacto para los usuarios de Apache si utilizan el **apache_neolane.conf proporcionado**

**Usuarios de IIS:**

Para los usuarios de IIS (en Windows), aparecerán varios iconos en la consola después de la actualización de compilación. Se requieren pasos adicionales de actualización de IIS:

1. Después de la actualización de la compilación, haga doble clic en **iis_neolane_setup.vbs** , que se encuentra en el directorio de instalación de Campaign. La ruta predeterminada es C:Archivos de programa (x86)Adobe Campaign v7tomcat-7conf
1. Reinicie el sitio de IIS que se ha actualizado en el paso anterior.

