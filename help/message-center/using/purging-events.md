---
title: Depuración de eventos
seo-title: Depuración de eventos
description: Depuración de eventos
seo-description: null
page-status-flag: never-activated
uuid: bbce6813-dfa8-418c-9b52-06e814c15265
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: message-center
content-type: reference
topic-tags: instance-configuration
discoiquuid: 2f643080-93b4-4c9f-80cf-b1770b149e6c
index: y
internal: n
snippet: y
translation-type: ht
source-git-commit: 20f835c357d016643ea1f3209ee4dfb6d3239f90

---


# Depuración de eventos{#purging-events}

Se puede utilizar el asistente de implementación para configurar cuánto tiempo se guardan los datos en la base de datos.

El flujo de trabajo **[!UICONTROL Database cleanup]** lleva a cabo la depuración de eventos automáticamente. Este flujo de trabajo depura los eventos recibidos y almacenados en las instancias de ejecución y los eventos archivados en una instancia de control.

Utilice las flechas según corresponda para modificar la configuración de depuración.

Configuración de depuración de eventos en una instancia de control:

![](assets/messagecenter_delete_events_001.png)

Configuración de depuración de eventos en una instancia de ejecución:

![](assets/messagecenter_delete_events_002.png)

Para obtener más información sobre el flujo de trabajo de limpieza, consulte [esta sección](../../production/using/database-cleanup-workflow.md).
