---
product: campaign
title: Reversión a la versión anterior
description: Obtenga información sobre cómo volver a la versión anterior
audience: migration
content-type: reference
topic-tags: rollback
hide: true
hidefromtoc: true
exl-id: 5120a7c4-3760-48d9-94da-d587d333e8d8
source-git-commit: 80cf56e330731237d5e7b394381b737f30f8b350
workflow-type: tm+mt
source-wordcount: '126'
ht-degree: 0%

---

# Reversión a la versión anterior{#about-rollback}

![](../../assets/v7-only.svg)

Después de una migración, en caso de problemas, es posible que tenga que volver a la versión anterior de Campaign.

El procedimiento de reversión depende de la versión inicial de Campaign.

Este es el procedimiento para restaurar una versión 6.1 desde una versión 7.

1. Recupere el backup de la base de datos y restablézcalo.
1. Recupere el **Adobe Campaign v6.back** carpeta (**nl6.back** en Linux), cambie el nombre a **Adobe Campaign v6** (**nl6** en Linux) y restaurarlo a su ubicación original.
1. Vuelva a configurar IIS reasignando los puertos de escucha para restablecer la integración de Adobe Campaign v6.1 a nivel de sitio web de IIS.
1. Detenga el servicio Adobe Campaign v7.
1. Vuelva a iniciar IIS.
1. Reinicie el servicio Adobe Campaign v6.1.

<!--
	
## Restore to Campaign v6.02

Here is the procedure to restore a v6.02 from a v7.

1. Recover the backup of the database and restore it.
1. Recover the **Neolane v6.back** folder (**nl6.back** in Linux), rename it to **Neolane v6** (**nl6** in Linux) and restore it to its original location.
1. Re-configure IIS by re-assigning the listen ports to re-establish the integration of Adobe Campaign v6.02 at IIS Website level.
1. Stop the Adobe Campaign v6.1 service.
1. Re-start IIS.
1. Restart the Adobe Campaign v6.02 service.

## Restore to Campaign v5.11

Here is the procedure to restore a v5.11 from a v7.

1. Recover the backup of the database and restore it.
1. Recover the **Neolane v5.back** folder (**nl5.back** in Linux), rename it to **Neolane v5** (**nl5** in Linux) and restore it to its original location.
1. Re-configure IIS by re-assigning the listen ports to re-establish the integration of Neolane v5 at IIS Website level.
1. Stop the Adobe Campaign v7 service.
1. Re-start IIS.
1. Re-start the Adobe Campaign v5 service.

-->