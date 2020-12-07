---
solution: Campaign Classic
product: campaign
title: Reciclaje de eventos
description: Reciclaje de eventos
audience: message-center
content-type: reference
topic-tags: event-processing
translation-type: ht
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: ht
source-wordcount: '95'
ht-degree: 100%

---


# Reciclaje de eventos{#event-recycling}

Si falla el envío de un mensaje en un canal específico, Adobe Campaign puede reenviar el mensaje con un canal diferente. Por ejemplo, si un envío del canal SMS falla, el mensaje se reenvía mediante el canal de correo electrónico.

Para ello, es necesario configurar un flujo de trabajo que vuelva a crear todos los eventos con el estado **Error de entrega** y les asigne un canal diferente.

>[!CAUTION]
>
>Este paso solo se puede llevar a cabo con un flujo de trabajo y, por lo tanto, se reserva para usuarios expertos. Para obtener más información, póngase en contacto con su administrador de cuenta de Adobe.

