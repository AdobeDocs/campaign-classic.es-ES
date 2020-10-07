---
title: Enrutamiento hacia una plantilla
seo-title: Enrutamiento hacia una plantilla
description: Enrutamiento hacia una plantilla
seo-description: null
page-status-flag: never-activated
uuid: 1f8252c4-7f96-4759-9544-39b8f854961f
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: message-center
content-type: reference
topic-tags: event-processing
discoiquuid: 8fa464e6-3c88-441c-8179-0c54960469a7
translation-type: tm+mt
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: tm+mt
source-wordcount: '125'
ht-degree: 100%

---


# Enrutamiento hacia una plantilla{#routing-towards-a-template}

Una vez que la plantilla de mensaje se publique en las instancias de ejecución, se generan automáticamente dos plantillas que se van a vincular a un evento en tiempo real o por lotes. El paso de enrutamiento consiste en vincular un evento a la plantilla de mensaje correspondiente. La vinculación se basa en el tipo de evento especificado en las propiedades del propio evento y de las de la plantilla.

Definición del tipo de evento en las propiedades de evento:

![](assets/messagecenter_event_type_001.png)

Definición del tipo de evento en las propiedades de la plantilla de mensaje:

![](assets/messagecenter_event_type_002.png)

De forma predeterminada, el enrutamiento se basa en la siguiente información:

* el tipo de evento,
* el canal que se va a utilizar (predeterminado: correo electrónico),
* la plantilla de envío más reciente, en función de la fecha de publicación.

