---
title: Envíos multicanal
seo-title: Envíos multicanal
description: Envíos multicanal
seo-description: null
page-status-flag: never-activated
uuid: 191ff39e-f739-48b3-8865-ad1b641b7499
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: workflow
content-type: reference
topic-tags: action-activities
discoiquuid: 8dda45b4-4b5d-4b4e-a8b4-45d9bc49aaf3
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: fa2b6890d3c9eaf7b4b6521b2edfb494faa4798c

---


# Envíos multicanal{#cross-channel-deliveries}

Cross-channel deliveries are available in the **[!UICONTROL Deliveries]** tab of campaign workflow activities.

Permiten crear un envío específico a un canal concreto. Puede especificar la plantilla en la que desea basar su envío, así como su contenido, del mismo modo que con un asistente de envíos clásico.

Los varios canales disponibles son:

* [Correo electrónico](../../delivery/using/about-email-channel.md)
* [Correo postal](../../delivery/using/about-direct-mail-channel.md)
* [Móvil](../../delivery/using/sms-channel.md)
* [Twitter](../../social/using/publishing-on-twitter.md)
* [Facebook](../../social/using/publishing-on-facebook.md)
* [iOS](../../delivery/using/creating-notifications.md#sending-notifications-on-ios)
* [Android](../../delivery/using/creating-notifications.md#sending-notifications-on-android)

Puede especificar un público objetivo para el envío ascendente del flujo de trabajo utilizando las distintas actividades de objetivos.

Por ejemplo, aquí podemos crear un flujo de trabajo para enviar un correo electrónico o un SMS a los suscriptores de las notificaciones push una semana más tarde. Para ello:

1. Cree una campaña.
1. In the **[!UICONTROL Targeting and workflows]** tab of your campaign, add a **[!UICONTROL Query]** to your workflow.
1. Configure la consulta. Por ejemplo, aquí se seleccionan los destinatarios suscritos a las notificaciones push como la dimensión objetivo.

   >[!NOTE]
   >
   >Para las notificaciones push, recuerde utilizar la dimensión objetivo **suscriber applications**.

   ![](assets/cross_channel_delivery_1.png)

1. Agregue las condiciones de filtro a la consulta. En este caso, se seleccionarán los destinatarios que tengan un número de teléfono móvil o una dirección de correo electrónico.

   ![](assets/cross_channel_delivery_2.png)

1. Add a **[!UICONTROL Split]** activity to your workflow to divide recipients who have a mobile number and those who have an email address.
1. In the **[!UICONTROL Delivery]** tab, select a delivery for each of your targets.

   Cree su envío de la misma manera que con el asistente de envíos clásico haciendo doble clic en la actividad de envío del flujo de trabajo. Para obtener más información, consulte [esta página](../../delivery/using/about-email-channel.md).

   ![](assets/cross_channel_delivery_3.png)

1. Add and configure a **[!UICONTROL Wait]** activity in order for the recipients not to receive too many deliveries at once.
1. Add a **[!UICONTROL Split]** activity to divide subscribers of an iOS or Android mobile applications.

   Seleccione un servicio para cada uno de los sistemas operativos. Para obtener más información sobre creación del servicio, consulte esta [página](../../delivery/using/configuring-the-mobile-application.md).

   ![](assets/cross_channel_delivery_4.png)

1. Seleccione y configure un envío de aplicaciones para dispositivos móviles para cada uno de los sistemas operativos.

   ![](assets/cross_channel_delivery_5.png)
