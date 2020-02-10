---
title: Restauración de v6.1
seo-title: Restauración de v6.1
description: Restauración de v6.1
seo-description: null
page-status-flag: never-activated
uuid: 3fb71b6f-4d70-4814-a885-4d414a542eca
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: migration
content-type: reference
topic-tags: rollback
discoiquuid: e510482c-a56d-4254-90f8-19bd5c545e30
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 9482a99c3be164651b3428179388cb0a8a75783f

---


# Restauración de v6.1{#restoring-v}

Este es el procedimiento para restaurar una v6.1 desde una v7.

1. Recupere el backup de la base de datos y restauítela.
1. Recupere la carpeta **Adobe Campaign v6.back** (**nl6.back** en Linux), cámbiele el nombre a **Adobe Campaign v6** (**nl6** en Linux) y restaure su ubicación original.
1. Vuelva a configurar IIS asignando los puertos de escucha para restablecer la integración de Adobe Campaign v6.1 en el nivel de sitio web de IIS.
1. Detenga el servicio Adobe Campaign v7.
1. Reinicie IIS.
1. Reinicie el servicio Adobe Campaign v6.1.

