---
solution: Campaign Classic
product: campaign
title: Enrutamiento hacia una plantilla
description: Enrutamiento hacia una plantilla
audience: message-center
content-type: reference
topic-tags: event-processing
exl-id: 2c18c557-f49b-4af8-8795-3d59bd78e63f
translation-type: ht
source-git-commit: 6854d06f8dc445b56ddfde7777f02916a60f2b63
workflow-type: ht
source-wordcount: '121'
ht-degree: 100%

---

# Enrutamiento hacia una plantilla{#routing-towards-a-template}

Una vez que la plantilla de mensaje se publique en las instancias de ejecución, se generan automáticamente dos plantillas que se van a vincular a un evento en tiempo real o por lotes. El paso de enrutamiento consiste en vincular un evento a la plantilla de mensaje correspondiente. La vinculación se basa en el tipo de evento especificado en las propiedades del propio evento y de las de la plantilla.

Definición del tipo de evento en las propiedades de evento:

![](assets/messagecenter_event_type_001.png)

Definición del tipo de evento en las propiedades de la plantilla de mensaje:

![](assets/messagecenter_event_type_002.png)

De forma predeterminada, el enrutamiento se basa en la siguiente información:

* El tipo de evento
* El canal que se va a utilizar (predeterminado: correo electrónico)
* La plantilla de envío más reciente, en función de la fecha de publicación
