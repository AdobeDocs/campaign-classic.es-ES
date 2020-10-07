---
title: Restauración de la versión 6.1
seo-title: Restauración de la versión 6.1
description: Restauración de la versión 6.1
seo-description: null
page-status-flag: never-activated
uuid: 3fb71b6f-4d70-4814-a885-4d414a542eca
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: migration
content-type: reference
topic-tags: rollback
discoiquuid: e510482c-a56d-4254-90f8-19bd5c545e30
translation-type: tm+mt
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: tm+mt
source-wordcount: '88'
ht-degree: 9%

---


# Restauración de la versión 6.1{#restoring-v}

Este es el procedimiento para restaurar una v6.1 desde una v7.

1. Recupere el backup de la base de datos y restauítela.
1. Recupere la carpeta **Adobe Campaign v6.back** (**nl6.back** en Linux), cámbiele el nombre a **Adobe Campaign v6** (**nl6** en Linux) y restaure su ubicación original.
1. Vuelva a configurar IIS asignando los puertos de escucha para restablecer la integración de Adobe Campaign v6.1 en el nivel de sitio web de IIS.
1. Detenga el servicio Adobe Campaign v7.
1. Volver a inicio de IIS.
1. Reinicie el servicio Adobe Campaign v6.1.

