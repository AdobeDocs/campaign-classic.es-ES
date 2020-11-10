---
title: Entregas multicanal
description: Más información sobre los envíos entre canales
page-status-flag: never-activated
uuid: 191ff39e-f739-48b3-8865-ad1b641b7499
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: workflow
content-type: reference
topic-tags: action-activities
discoiquuid: 8dda45b4-4b5d-4b4e-a8b4-45d9bc49aaf3
translation-type: tm+mt
source-git-commit: 6be6c353c3464839a74ba857d8d93d0f68bc8865
workflow-type: tm+mt
source-wordcount: '312'
ht-degree: 98%

---


# Entregas multicanal{#cross-channel-deliveries}

Los envíos multicanal están disponibles en la pestaña **[!UICONTROL Deliveries]** de las actividades de flujo de trabajo de la campaña.

Permiten crear una entrega específica a un canal concreto. Puede especificar la plantilla en la que desea basar su envío, así como su contenido, del mismo modo que con un asistente de envíos clásico.

Los varios canales disponibles son:

* [Correo electrónico](../../delivery/using/about-email-channel.md)
* [Correo postal](../../delivery/using/about-direct-mail-channel.md)
* [Móvil](../../delivery/using/sms-channel.md)
* [Twitter](../../social/using/publishing-on-twitter.md)
* [Facebook](../../social/using/publishing-on-facebook.md)
* [iOS](../../delivery/using/creating-notifications.md#sending-notifications-on-ios)
* [Android](../../delivery/using/creating-notifications.md#sending-notifications-on-android)

Puede especificar un público objetivo para la entrega ascendente del flujo de trabajo utilizando las distintas actividades de objetivos.

Por ejemplo, aquí podemos crear un flujo de trabajo para enviar un correo electrónico o un SMS a los suscriptores de las notificaciones push una semana más tarde. Para ello:

1. Cree una campaña.
1. En la pestaña **[!UICONTROL Targeting and workflows]** de la campaña, añada **[!UICONTROL Query]** al flujo de trabajo.
1. Configure la consulta. Por ejemplo, aquí se seleccionan los destinatarios suscritos a las notificaciones push como la dimensión objetivo.

   >[!NOTE]
   >
   >Para las notificaciones push, recuerde utilizar la dimensión objetivo **suscriber applications**.

   ![](assets/cross_channel_delivery_1.png)

1. Agregue las condiciones de filtro a la consulta. En este caso, se seleccionarán los destinatarios que tengan un número de teléfono móvil o una dirección de correo electrónico.

   ![](assets/cross_channel_delivery_2.png)

1. Añada una actividad **[!UICONTROL Split]** al flujo de trabajo para dividir los destinatarios que tienen número de móvil y aquellos que tienen dirección de correo electrónico.
1. En la pestaña **[!UICONTROL Delivery]**, seleccione una entrega para cada uno de sus destinatarios.

   Cree su envío de la misma manera que con el asistente de envíos clásico haciendo doble clic en la actividad de envío del flujo de trabajo. Para obtener más información, consulte [esta página](../../delivery/using/about-email-channel.md).

   ![](assets/cross_channel_delivery_3.png)

1. Añada y configure una actividad **[!UICONTROL Wait]** para que los destinatarios no reciban demasiados envíos a la vez.
1. Añada una actividad **[!UICONTROL Split]** para dividir los suscriptores de aplicaciones móviles iOS o Android.

   Seleccione un servicio para cada uno de los sistemas operativos. Para obtener más información sobre creación del servicio, consulte esta [página](../../delivery/using/configuring-the-mobile-application.md).

   ![](assets/cross_channel_delivery_4.png)

1. Seleccione y configure una entrega de aplicaciones para dispositivos móviles para cada uno de los sistemas operativos.

   ![](assets/cross_channel_delivery_5.png)
