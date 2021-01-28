---
solution: Campaign Classic
product: campaign
title: Depuración de eventos
description: Depuración de eventos
audience: message-center
content-type: reference
topic-tags: instance-configuration
translation-type: ht
source-git-commit: 5bc6c8a824929c6a61cf562fc961e5bdd1867837
workflow-type: ht
source-wordcount: '90'
ht-degree: 100%

---


# Depuración de eventos{#purging-events}

Se puede utilizar el [asistente de implementación](../../production/using/database-cleanup-workflow.md#deployment-wizard) para configurar cuánto tiempo se guardan los datos en la base de datos.

El [flujo de trabajo de limpieza de la base de datos](../../production/using/database-cleanup-workflow.md) lleva a cabo la depuración de eventos automáticamente. Este flujo de trabajo depura los eventos recibidos y almacenados en las instancias de ejecución y los eventos archivados en una instancia de control.

Utilice las flechas según corresponda para modificar la configuración de depuración.

Configuración de depuración de eventos en una instancia de control:

![](assets/messagecenter_delete_events_001.png)

Configuración de depuración de eventos en una instancia de ejecución:

![](assets/messagecenter_delete_events_002.png)

Para obtener más información sobre el flujo de trabajo de limpieza, consulte [esta sección](../../production/using/database-cleanup-workflow.md).
