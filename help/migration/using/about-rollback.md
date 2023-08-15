---
product: campaign
title: Volver a la versión anterior
description: Obtenga información sobre cómo revertir a la versión anterior
feature: Upgrade
badge-v7-only: label="v7" type="Informative" tooltip="Se aplica solo a Campaign Classic v7"
audience: migration
content-type: reference
topic-tags: rollback
hide: true
hidefromtoc: true
exl-id: 5120a7c4-3760-48d9-94da-d587d333e8d8
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: tm+mt
source-wordcount: '133'
ht-degree: 5%

---

# Volver a la versión anterior{#about-rollback}



Después de una migración, en caso de problemas, es posible que tenga que volver a la versión anterior de Campaign.

El procedimiento de reversión depende de la versión inicial de Campaign.

Este es el procedimiento para restaurar una versión 6.1 desde una versión 7.

1. Recupere la copia de seguridad de la base de datos y restáurela.
1. Recupere el **Adobe Campaign v6.back** carpeta (**nl6.back** en Linux), cambie el nombre a **Adobe Campaign v6** (**nl6** en Linux) y restáurelo a su ubicación original.
1. Vuelva a configurar IIS reasignando los puertos de escucha para restablecer la integración de Adobe Campaign v6.1 en el nivel de sitio web de IIS.
1. Detenga el servicio de Adobe Campaign v7.
1. Vuelva a iniciar IIS.
1. Reinicie el servicio de Adobe Campaign v6.1.

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