---
product: campaign
title: Falta de imágenes
description: Falta de imágenes
feature: Monitoring
badge-v7-only: label="v7" type="Informative" tooltip="Se aplica solo a Campaign Classic v7"
audience: production
content-type: reference
topic-tags: troubleshooting
exl-id: 6ccda57d-f7a3-4501-b2f4-59fcb05f9013
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: tm+mt
source-wordcount: '116'
ht-degree: 11%

---

# Falta de imágenes{#images-missing}



En la versión 17.9, se han movido varios archivos (iconos en particular).

Para los clientes alojados, no hay ningún impacto. Para instalaciones on-premise, lea lo siguiente.

**Usuarios de Apache:**

Los usuarios de Apache no sufren ningún impacto si utilizan el proporcionado **apache_neolane.conf**.

**Usuarios de IIS:**

Para los usuarios de IIS (en Windows), después de la actualización de la compilación, aparecerán varios iconos que faltan en la consola. Se requieren pasos de actualización de IIS adicionales:

1. Después de la actualización de la compilación, haga doble clic en **iis_neolane_setup.vbs** ubicado en el directorio de instalación de Campaign. La ruta predeterminada es C:\Program Files (x86)\Adobe\Adobe Campaign v7\conf
1. Reinicie el sitio de IIS que se haya actualizado en el paso anterior.
