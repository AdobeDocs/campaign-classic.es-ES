---
product: campaign
title: Requisitos previos para la migración a Adobe Campaign 7
description: Requisitos previos para la migración a Adobe Campaign 7
audience: migration
content-type: reference
topic-tags: migrating-to-adobe-campaign-7
exl-id: 747d8a2c-b13a-4852-a9b5-0d37b236a36f
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '80'
ht-degree: 22%

---

# Requisitos previos para la migración a Adobe Campaign 7{#prerequisites-for-migration-to-adobe-campaign}

![](../../assets/v7-only.svg)

Antes de ejecutar cualquier migración, consulte la [Antes de iniciar la migración](../../migration/using/before-starting-migration.md) y [Configuración de la plataforma](../../migration/using/configuring-your-platform.md) secciones.

Al migrar de la versión 6.02 a Adobe Campaign v7, algunos archivos entregados previamente no se entregan.

Si aparece un error de cliente, debe actualizar los tableros con el nuevo código de Adobe Campaign v7 o copiar manualmente los siguientes archivos de la instancia v6.02 a la instancia v7:

```
v6.02 files and spaces:
/usr/local/neolane/nl6/datakit/xtk/eng/css/dropDownMenu.css
/usr/local/neolane/nl6/datakit/xtk/eng/js/client/dropDownMenu.js
v6.1 files and spaces:
/usr/local/neolane/nl6/deprecated/xtk/css/dropDownMenu.css
/usr/local/neolane/nl6/deprecated/xtk/js/client/dropDownMenu.js  
```
