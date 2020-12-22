---
solution: Campaign Classic
product: campaign
title: Depuración de eventos
description: Depuración de eventos
audience: message-center
content-type: reference
topic-tags: instance-configuration
translation-type: tm+mt
source-git-commit: 5bc6c8a824929c6a61cf562fc961e5bdd1867837
workflow-type: tm+mt
source-wordcount: '90'
ht-degree: 66%

---


# Depuración de eventos{#purging-events}

Puede utilizar el [asistente de implementación](../../production/using/database-cleanup-workflow.md#deployment-wizard) para configurar cuánto tiempo se almacenarán los datos en la base de datos.

La depuración de eventos se realiza automáticamente mediante el [flujo de trabajo de limpieza de bases de datos](../../production/using/database-cleanup-workflow.md). Este flujo de trabajo depura los eventos recibidos y almacenados en las instancias de ejecución y los eventos archivados en una instancia de control.

Utilice las flechas según corresponda para modificar la configuración de depuración.

Configuración de depuración de eventos en una instancia de control:

![](assets/messagecenter_delete_events_001.png)

Configuración de depuración de eventos en una instancia de ejecución:

![](assets/messagecenter_delete_events_002.png)

Para obtener más información sobre el flujo de trabajo de limpieza, consulte [esta sección](../../production/using/database-cleanup-workflow.md).
