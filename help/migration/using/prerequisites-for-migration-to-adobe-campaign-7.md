---
title: Requisitos previos para la migración a Adobe Campaign 7
seo-title: Requisitos previos para la migración a Adobe Campaign 7
description: Requisitos previos para la migración a Adobe Campaign 7
seo-description: null
page-status-flag: never-activated
uuid: 9f4e4cdf-5338-4597-9d9d-5a3bd13033c7
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: migration
content-type: reference
topic-tags: migrating-to-adobe-campaign-7
discoiquuid: a3bbd8cc-97c6-4b08-adbf-76ab77b97262
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: f460c79a763c6a207656c54351a4c685f2a78a03

---


# Requisitos previos para la migración a Adobe Campaign 7{#prerequisites-for-migration-to-adobe-campaign}

Antes de ejecutar cualquier migración, consulte las secciones [Antes de iniciar la migración](../../migration/using/before-starting-migration.md) y [Configuración de la plataforma](../../migration/using/configuring-your-platform.md) .

Al migrar de v6.02 a Adobe Campaign v7, algunos archivos entregados de antemano no se entregan.

Si aparece un error de cliente, debe actualizar los tableros con el nuevo código de Adobe Campaign v7 o copiar manualmente los siguientes archivos de la instancia v6.02 a la instancia v7:

```
v6.02 files and spaces:
/usr/local/neolane/nl6/datakit/xtk/eng/css/dropDownMenu.css
/usr/local/neolane/nl6/datakit/xtk/eng/js/client/dropDownMenu.js
v6.1 files and spaces:
/usr/local/neolane/nl6/deprecated/xtk/css/dropDownMenu.css
/usr/local/neolane/nl6/deprecated/xtk/js/client/dropDownMenu.js  
```
