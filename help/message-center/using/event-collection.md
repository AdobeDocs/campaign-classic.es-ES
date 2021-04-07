---
solution: Campaign Classic
product: campaign
title: Recopilación de eventos
description: Recopilación de eventos
audience: message-center
content-type: reference
topic-tags: event-processing
translation-type: ht
source-git-commit: 693e38477b318ee44e0373a04d8524ddf128fe36
workflow-type: ht
source-wordcount: '138'
ht-degree: 100%

---


# Recopilación de eventos{#event-collection}

Los eventos que genera el sistema de información se pueden recopilar mediante dos modos:

* Las llamadas a métodos SOAP permiten insertar eventos en Adobe Campaign: el método PushEvent permite enviar un evento a la vez, el método PushEvents permite enviar varios a la vez. Consulte la [Descripción del evento](../../message-center/using/event-description.md).
* La creación de un flujo de trabajo permite recuperar eventos mediante la importación de archivos o mediante una puerta de vínculo SQL (con la opción **Acceso de datos federado**).

Una vez recopilados, los eventos se desglosan, por flujos de trabajo técnicos, entre colas en tiempo real y por lotes de las instancias de ejecución, mientras esperan vincularse a una plantilla de mensaje.

![](assets/messagecenter_events_queues_001.png)

>[!NOTE]
>
>En las instancias de ejecución, las carpetas **[!UICONTROL Real time events]** o **[!UICONTROL Batch events]** no deben configurarse como vistas, ya que esto podría provocar problemas con el derecho de acceso. Para obtener más información sobre la configuración de una carpeta como vista, consulte [esta sección](../../platform/using/access-management-folders.md).
