---
title: Acerca del canal de aplicaciones móviles en Adobe Campaign Classic
description: Esta sección proporciona información general específica del canal de aplicaciones móviles en Adobe Campaign Classic.
page-status-flag: never-activated
uuid: e8d26b33-dc7c-4abd-956a-92f419a117e1
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: delivery
content-type: reference
topic-tags: sending-push-notifications
discoiquuid: 6b3fe8b9-dae6-4f8e-83e1-3376c0fe72a5
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: c581f22261af7e083f6bd47e603d17d2d71e7ce6

---


# Acerca del canal de aplicaciones móviles{#about-mobile-app-channel}

>[!CAUTION]
>
>Este documento detalla el proceso para integrar su aplicación móvil con la plataforma Adobe Campaign. No proporciona información sobre cómo crear la aplicación móvil o cómo configurarla para gestionar notificaciones. Si desea obtener más información sobre este tema, consulte la documentación oficial de Apple ([https://developer.apple.com/](https://developer.apple.com/)) y Android ([https://developer.android.com/index.html](https://developer.android.com/index.html)).

Las secciones a continuación proporcionan información específica sobre el canal de aplicaciones móviles. For global information on how to create a delivery, refer to [this section](../../delivery/using/steps-about-delivery-creation-steps.md).

El **Mobile App Channel** permite utilizar la plataforma de Adobe Campaign para enviar notificaciones personalizadas a los terminales iOS y Android a través de aplicaciones. Hay dos canales de envío disponibles:

* Un canal de iOS que le permite enviar notificaciones a dispositivos móviles de Apple.

   ![](assets/nmac_intro_2.png)

* Un canal de Android que le permite enviar mensajes de datos a dispositivos móviles Android.

   ![](assets/nmac_intro_1.png)

En relación con esos dos canales hay dos actividades de envío en los flujos de trabajo de campaña:

![](assets/nmac_intro_3.png)

>[!NOTE]
>
>Dos plantillas de mensajes transaccionales también están disponibles para la mensajería transaccional.

Puede definir el comportamiento de la aplicación para las situaciones en las que el usuario activa la notificación para mostrar la pantalla correspondiente al contexto de la aplicación. Por ejemplo:

* Se envía una notificación al cliente para informar que el paquete ha salido del almacén. Al activar la notificación, se abre una página con información sobre el envío.
* El usuario ha añadido elementos al carro de la compra, pero ha salido de la aplicación sin finalizar la compra. Se envía una notificación que informa de que ha abandonado el carro de la compra. Cuando se activa la notificación, el elemento se muestra en la pantalla.

>[!CAUTION]
>
>* Asegúrese de que las notificaciones enviadas a una aplicación móvil cumplen los requisitos previos y las condiciones especificadas por Apple (Servicio de notificaciones inmediatas de Apple) y Google (Google Cloud Messaging).
>* Advertencia: en algunos países, la ley requiere informar a los usuarios de las aplicaciones del tipo de datos que se recopilan y del propósito de su procesamiento. Debe comprobar la ley.


The **[!UICONTROL NMAC opt-out management]** (mobileAppOptOutMgt) workflow updates notification unsubscriptions on mobile devices. Para obtener más información sobre este flujo de trabajo, consulte la [guía sobre flujos de trabajo](../../workflow/using/mobile-app-channel.md).

Adobe Campaign es compatible con APNS tanto de tipo binario como HTTP/2. For more details on the configuration steps, refer to the [Connectors](../../delivery/using/setting-up-mobile-app-channel.md#connectors) section.
