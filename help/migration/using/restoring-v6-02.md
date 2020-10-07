---
title: Restauración de la versión 6.02
seo-title: Restauración de la versión 6.02
description: Restauración de la versión 6.02
seo-description: null
page-status-flag: never-activated
uuid: df21209b-4825-42fa-a303-f383f872abb5
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: migration
content-type: reference
topic-tags: rollback
discoiquuid: 4f65ba19-e9f0-4425-b640-f27c61394859
translation-type: tm+mt
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: tm+mt
source-wordcount: '86'
ht-degree: 9%

---


# Restauración de la versión 6.02{#restoring-v}

Este es el procedimiento para restaurar una versión v6.02 desde una v7.

1. Recupere el backup de la base de datos y restauítela.
1. Recupere la carpeta **Neolane v6.back** (**nl6.back** en Linux), cámbiele el nombre a **Neolane v6** (**nl6** en Linux) y restaure su ubicación original.
1. Vuelva a configurar IIS asignando los puertos de escucha para restablecer la integración de Adobe Campaign v6.02 en el nivel de sitio web de IIS.
1. Detenga el servicio Adobe Campaign v6.1.
1. Volver a inicio de IIS.
1. Reinicie el servicio Adobe Campaign v6.02.

