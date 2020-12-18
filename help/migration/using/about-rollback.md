---
solution: Campaign Classic
product: campaign
title: Revertir a la versión anterior
description: Aprenda a revertir a la versión anterior
audience: migration
content-type: reference
topic-tags: rollback
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '291'
ht-degree: 0%

---


# Revertir a la versión anterior{#about-rollback}

Después de una migración, en caso de problemas, es posible que tenga que volver a la versión anterior de Campaña.

El procedimiento de reversión depende de la versión inicial de la Campaña.

## Restauración de la versión 6.1

Este es el procedimiento para restaurar una v6.1 desde una v7.

1. Recupere el backup de la base de datos y restauítela.
1. Recupere la carpeta **Adobe Campaign v6.back** (**nl6.back** en Linux), cámbiele el nombre a **Adobe Campaign v6** (**nl6** en Linux) y restálela a su ubicación original.
1. Vuelva a configurar IIS asignando los puertos de escucha para restablecer la integración de Adobe Campaign v6.1 en el nivel de sitio web de IIS.
1. Detenga el servicio Adobe Campaign v7.
1. Volver a inicio de IIS.
1. Reinicie el servicio Adobe Campaign v6.1.

## Restauración a Campaña v6.02

Este es el procedimiento para restaurar una versión v6.02 desde una v7.

1. Recupere el backup de la base de datos y restauítela.
1. Recupere la carpeta **Neolane v6.back** (**nl6.back** en Linux), cámbiele el nombre a **Neolane v6** (**nl6** en Linux) y restálela a su ubicación original.
1. Vuelva a configurar IIS asignando los puertos de escucha para restablecer la integración de Adobe Campaign v6.02 en el nivel de sitio web de IIS.
1. Detenga el servicio Adobe Campaign v6.1.
1. Volver a inicio de IIS.
1. Reinicie el servicio Adobe Campaign v6.02.

## Restauración a Campaña v5.11

Este es el procedimiento para restaurar una versión 5.11 desde una versión 7.

1. Recupere el backup de la base de datos y restauítela.
1. Recupere la carpeta **Neolane v5.back** (**nl5.back** en Linux), cámbiele el nombre a **Neolane v5** (**nl5** en Linux) y restálela a su ubicación original.
1. Vuelva a configurar IIS asignando los puertos de escucha para restablecer la integración de Neolane v5 en el nivel de sitio web de IIS.
1. Detenga el servicio Adobe Campaign v7.
1. Volver a inicio de IIS.
1. Vuelva a realizar el inicio del servicio Adobe Campaign v5.
