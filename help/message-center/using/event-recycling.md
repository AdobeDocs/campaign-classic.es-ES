---
title: Reciclaje de eventos
seo-title: Reciclaje de eventos
description: Reciclaje de eventos
seo-description: null
page-status-flag: never-activated
uuid: 55624a41-65a1-4759-8087-6e5d2c5c5b62
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: message-center
content-type: reference
topic-tags: event-processing
discoiquuid: 568a9dec-5818-4666-b858-aa41fe827b92
index: y
internal: n
snippet: y
translation-type: ht
source-git-commit: 579329d9194115065dff2c192deb0376c75e67bd

---


# Reciclaje de eventos{#event-recycling}

Si falla el envío de un mensaje en un canal específico, Adobe Campaign puede reenviar el mensaje con un canal diferente. Por ejemplo, si un envío del canal SMS falla, el mensaje se reenvía mediante el canal de correo electrónico.

Para ello, es necesario configurar un flujo de trabajo que vuelva a crear todos los eventos con el estado **Error de entrega** y les asigne un canal diferente.

>[!CAUTION]
>
>Este paso solo se puede llevar a cabo con un flujo de trabajo y, por lo tanto, se reserva para usuarios expertos. Para obtener más información, póngase en contacto con su administrador de cuenta de Adobe.

