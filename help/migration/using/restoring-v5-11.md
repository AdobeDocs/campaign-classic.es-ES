---
title: Restauración de la versión 5.11
seo-title: Restauración de la versión 5.11
description: Restauración de la versión 5.11
seo-description: null
page-status-flag: never-activated
uuid: 4480c97c-5845-483c-a17b-644f05783b4e
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: migration
content-type: reference
topic-tags: rollback
discoiquuid: ef778333-8e50-402b-9a69-78ac94497c67
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 9482a99c3be164651b3428179388cb0a8a75783f

---


# Restauración de la versión 5.11{#restoring-v}

Este es el procedimiento para restaurar una versión 5.11 desde una versión 7.

1. Recupere el backup de la base de datos y restauítela.
1. Recupere la carpeta **Neolane v5.back** (**nl5.back** en Linux), cámbiele el nombre a **Neolane v5** (**nl5** en Linux) y restaure su ubicación original.
1. Vuelva a configurar IIS asignando los puertos de escucha para restablecer la integración de Neolane v5 en el nivel de sitio web de IIS.
1. Detenga el servicio Adobe Campaign v7.
1. Reinicie IIS.
1. Vuelva a iniciar el servicio Adobe Campaign v5.

