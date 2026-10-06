---
product: campaign
title: Entregas multicanal
description: Descubra más información sobre las entregas multicanal
feature: Workflows, Channels Activity
hide: true
exl-id: 3bb468e2-7bcf-456f-8d8f-1c4e608e2b25
TQID: 'https://experienceleague.adobe.com/BXn5nJkGD-NL8Rh5kYtltXfGJiWlYQqbyzcdZ1SleJA'
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
    internal-label: Campaign
  - id: fd6e6e36-54e4-4f1a-96fc-1a750e400d50
    internal-label: Campaign Classic v7
feature_v2:
  - id: a658c786-869b-4194-a780-2594d663adda
    internal-label: Data management
subfeature_v2:
  - id: ee25c34b-ea50-427b-9369-ba0a160f7d70
    internal-label: HeatMap
  - id: b5f0aaf4-1e48-400d-95ac-6eb3078cf22f
    internal-label: Execution activities
  - id: d1110311-2ca4-442b-be37-088a6db845ee
    internal-label: Data Management activities
  - id: fcb46c0f-76e1-48bc-9dd0-fcf9d97526cf
    internal-label: Workflows
  - id: bce277d1-7efa-48d8-9a1b-b588bb45ba1c
    internal-label: Channels Activity
source-git-commit: a43e591a565a18d79f583d975e3e812c5435b0c0
workflow-type: tm+mt
source-wordcount: '292'
ht-degree: 100%
---
# Entregas multicanal{#cross-channel-deliveries}



Las entregas multicanal están disponibles en la pestaña **[!UICONTROL Deliveries]** de las actividades de flujo de trabajo de la campaña.

Los varios canales disponibles son los siguientes:

* [Correo electrónico](../../delivery/using/about-email-channel.md)
* [Correo directo](../../delivery/using/about-direct-mail-channel.md)
* [Móvil](../../delivery/using/sms-channel.md)
* [X (anteriormente conocido como Twitter)](../../social/using/about-social-marketing.md)
* [iOS](../../delivery/using/create-notifications-ios.md)
* [Android](../../delivery/using/create-notifications-android.md)

Seleccione la plantilla en la que desea basar la entrega y defina su contenido.

Puede especificar un público objetivo para la entrega ascendente del flujo de trabajo utilizando las distintas actividades de direccionamiento.

En el siguiente ejemplo, crearemos un flujo de trabajo para enviar un correo electrónico o un SMS a los suscriptores de las notificaciones push una semana más tarde. Para ello:

1. Cree una campaña.
1. En la pestaña **[!UICONTROL Targeting and workflows]** de la campaña, añada **[!UICONTROL Query]** al flujo de trabajo.
1. Configure la consulta. Por ejemplo, aquí se seleccionan los destinatarios suscritos a las notificaciones push como la dimensión objetivo.

   >[!NOTE]
   >
   >Para las notificaciones push, recuerde utilizar la dimensión objetivo **aplicaciones del suscriptor**.

   ![](assets/cross_channel_delivery_1.png)

1. Agregue las condiciones de filtro a la consulta. En este caso, se seleccionarán los destinatarios que tengan un número de teléfono móvil o una dirección de correo electrónico.

   ![](assets/cross_channel_delivery_2.png)

1. Añada una actividad **[!UICONTROL Split]** al flujo de trabajo para dividir los destinatarios que tienen número de móvil y aquellos que tienen dirección de correo electrónico.
1. En la pestaña **[!UICONTROL Delivery]**, seleccione una entrega para cada uno de sus destinatarios.

   Cree su envío de la misma manera que con el asistente de envíos clásico, haciendo doble clic en la actividad de envío del flujo de trabajo. Para obtener más información, consulte esta [página](../../delivery/using/about-email-channel.md).

   ![](assets/cross_channel_delivery_3.png)

1. Añada y configure una actividad **[!UICONTROL Wait]** para que los destinatarios no reciban demasiados envíos a la vez.
1. Añada una actividad **[!UICONTROL Split]** para dividir los suscriptores de aplicaciones móviles iOS o Android.

   Seleccione un servicio para cada uno de los sistemas operativos. Para obtener más información sobre creación del servicio, consulte esta [página](../../delivery/using/configuring-the-mobile-application.md).

   ![](assets/cross_channel_delivery_4.png)

1. Seleccione y configure una entrega de aplicaciones para dispositivos móviles para cada uno de los sistemas operativos.

   ![](assets/cross_channel_delivery_5.png)
