---
product: campaign
title: Reversión a la versión anterior
description: Obtenga información sobre cómo volver a la versión anterior
audience: migration
content-type: reference
topic-tags: rollback
exl-id: 5120a7c4-3760-48d9-94da-d587d333e8d8
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '291'
ht-degree: 0%

---

# Reversión a la versión anterior{#about-rollback}

![](../../assets/v7-only.svg)

Después de una migración, en caso de problemas, es posible que tenga que volver a la versión anterior de Campaign.

El procedimiento de reversión depende de la versión inicial de Campaign.

## Restauración de la versión 6.1

Este es el procedimiento para restaurar una versión 6.1 desde una versión 7.

1. Recupere el backup de la base de datos y restablézcalo.
1. Recupere el **Adobe Campaign v6.back** carpeta (**nl6.back** en Linux), cambie el nombre a **Adobe Campaign v6** (**nl6** en Linux) y restaurarlo a su ubicación original.
1. Vuelva a configurar IIS reasignando los puertos de escucha para restablecer la integración de Adobe Campaign v6.1 a nivel de sitio web de IIS.
1. Detenga el servicio Adobe Campaign v7.
1. Vuelva a iniciar IIS.
1. Reinicie el servicio Adobe Campaign v6.1.

## Restauración a Campaign v6.02

Este es el procedimiento para restaurar una versión 6.02 desde una versión 7.

1. Recupere el backup de la base de datos y restablézcalo.
1. Recupere el **Neolane v6.back** carpeta (**nl6.back** en Linux), cambie el nombre a **Neolane v6** (**nl6** en Linux) y restaurarlo a su ubicación original.
1. Vuelva a configurar IIS reasignando los puertos de escucha para restablecer la integración de Adobe Campaign v6.02 a nivel de sitio web de IIS.
1. Detenga el servicio Adobe Campaign v6.1.
1. Vuelva a iniciar IIS.
1. Reinicie el servicio Adobe Campaign v6.02.

## Restauración a Campaign v5.11

Este es el procedimiento para restaurar una versión 5.11 desde una versión 7.

1. Recupere el backup de la base de datos y restablézcalo.
1. Recupere el **Neolane v5.back** carpeta (**nl5.back** en Linux), cambie el nombre a **Neolane v5** (**nl5** en Linux) y restaurarlo a su ubicación original.
1. Vuelva a configurar IIS reasignando los puertos de escucha para restablecer la integración de Neolane v5 a nivel de sitio web de IIS.
1. Detenga el servicio Adobe Campaign v7.
1. Vuelva a iniciar IIS.
1. Vuelva a iniciar el servicio Adobe Campaign v5.
