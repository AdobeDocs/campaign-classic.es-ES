---
title: Recopilación de eventos
seo-title: Recopilación de eventos
description: Recopilación de eventos
seo-description: null
page-status-flag: never-activated
uuid: 8c373962-40d4-4982-9bd1-ce1cf8261dd5
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: message-center
content-type: reference
topic-tags: event-processing
discoiquuid: cfff302a-6ac0-461a-a1e4-8e4b617fe134
translation-type: tm+mt
source-git-commit: 95dff2f3704e316e9ec9e454a8f3fb9835508ccd
workflow-type: tm+mt
source-wordcount: '106'
ht-degree: 50%

---


# Recopilación de eventos{#event-collection}

Los eventos que genera el sistema de información se pueden recopilar mediante dos modos:

* Las llamadas a los métodos SOAP le permiten insertar eventos en Adobe Campaign: el método PushEvent permite enviar un evento a la vez, mientras que el método PushEvents permite enviar varios a la vez. Consulte la [Descripción del evento](../../message-center/using/event-description.md).
* Creating a workflow lets you recover events by importing files or via an SQL gateway (with the **Federated Data Access** option).

Una vez recopilados, los eventos se desglosan, por flujos de trabajo técnicos, entre colas en tiempo real y por lotes de las instancias de ejecución, mientras esperan vincularse a una plantilla de mensaje.

![](assets/messagecenter_events_queues_001.png)
