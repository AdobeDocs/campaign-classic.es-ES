---
product: campaign
title: Creación de una notificación push para dispositivos Android
description: Aprenda a crear notificaciones push para Android
badge-v7-only: label="v7" type="Informative" tooltip="Se aplica solo a Campaign Classic v7"
feature: Push
exl-id: 13ccc5d6-4355-42ba-80dc-30a45d3b69a4
source-git-commit: 4661688a22bd1a82eaf9c72a739b5a5ecee168b1
workflow-type: tm+mt
source-wordcount: '720'
ht-degree: 100%

---

# Creación de notificaciones para Android{#create-notificaations-android}



Utilice Adobe Campaign para enviar notificaciones push a los dispositivos Android. En [esta sección](steps-about-delivery-creation-steps.md) se exponen conceptos globales sobre la creación de envíos.

Comience creando una nueva entrega.

![](assets/nmac_delivery_1.png)

Con Firebase Cloud Messaging, puede elegir entre dos tipos de mensajes:

* **[!UICONTROL Data message]**, gestionado por la aplicación del cliente.
  <br>Los mensajes se envían directamente a la aplicación móvil, que generará y mostrará la notificación de Android al dispositivo. Los mensajes de datos solo contienen las variables de aplicación personalizadas.

* **[!UICONTROL Notification message]**, gestionado automáticamente por el SDK de FCM.
  <br> FCM muestra automáticamente el mensaje en los dispositivos de los usuarios en nombre de la aplicación del cliente. Los mensajes de notificación contienen un conjunto predefinido de parámetros y opciones, pero pueden personalizarse aún más con las variables de aplicación personalizadas.

Para obtener más información sobre los tipos de mensajes de Firebase Cloud Messaging, consulte la documentación [de FCM](https://firebase.google.com/docs/cloud-messaging/concept-options#notifications_and_data_messages).

## Creación de un mensaje de datos {#creating-data-message}

1. Vaya a **[!UICONTROL Campaign management]** > **[!UICONTROL Deliveries]**.

1. Haga clic **[!UICONTROL New]**.

   ![](assets/nmac_android_3.png)

1. Seleccione **[!UICONTROL Deliver on Android (android)]** en la lista desplegable **[!UICONTROL Delivery template]**. Añada un **[!UICONTROL Label]** al envío.

1. Haga clic en **[!UICONTROL To]** para definir la población en destinatario. De forma predeterminada, se aplica la asignación de destino **[!UICONTROL Subscriber application]**. Haga clic en **[!UICONTROL Add]** para seleccionar el servicio.

   ![](assets/nmac_android_7.png)

1. En la ventana **[!UICONTROL Target type]**, seleccione **[!UICONTROL Subscribers of an Android mobile application]** y haga clic en **[!UICONTROL Next]**.

1. En la lista desplegable **[!UICONTROL Service]**, seleccione el servicio creado anteriormente y, a continuación, la aplicación, y haga clic en **[!UICONTROL Finish]**.
Las **[!UICONTROL Application variables]** se añaden automáticamente en función de lo que se añadió durante los pasos de configuración.

   ![](assets/nmac_android_6.png)

1. Seleccione **[!UICONTROL data message]** como **[!UICONTROL Message Type]**.

1. Edite la notificación enriquecida.

   ![](assets/nmac_android_5.png)

1. Puede agregar información en la configuración **[!UICONTROL Application variables]** si es necesario. **[!UICONTROL Application variables]** debe configurarse en el servicio Android y formar parte de la carga de mensajes que se envía al dispositivo móvil.

1. Haga clic en **[!UICONTROL Save]** y realice la entrega.

La imagen y la página web deberían aparecer en la notificación push cuando se reciban en los dispositivos móviles Android de los suscriptores.

![](assets/nmac_android_4.png)

## Creación de un mensaje de notificación {#creating-notification-message}

>[!NOTE]
>
>Las opciones adicionales para los mensajes de notificación solo están disponibles con la configuración de la API HTTP v1. Para obtener más información, consulte [esta sección](configuring-the-mobile-application-android.md#android-service-httpv1).

![](assets/do-not-localize/how-to-video.png) [Obtenga información sobre cómo crear una notificación push de Android con este vídeo](https://experienceleague.adobe.com/docs/campaign-classic-learn/getting-started-with-push-notifications-for-android/configuring-and-sending-push-notifications.html?lang=es#additional-resources)

1. Vaya a **[!UICONTROL Campaign management]** > **[!UICONTROL Deliveries]**.

1. Haga clic **[!UICONTROL New]**.

   ![](assets/nmac_android_3.png)

1. Seleccione **[!UICONTROL Deliver on Android (android)]** en la lista desplegable **[!UICONTROL Delivery template]**. Añada un **[!UICONTROL Label]** al envío.

1. Haga clic en **[!UICONTROL To]** para definir la población en destinatario. De forma predeterminada, se aplica la asignación de destino **[!UICONTROL Subscriber application]**. Haga clic en **[!UICONTROL Add]** para seleccionar el servicio.

   ![](assets/nmac_android_7.png)

1. En la ventana **[!UICONTROL Target type]**, seleccione **[!UICONTROL Subscribers of an Android mobile application]** y haga clic en **[!UICONTROL Next]**.

1. En la lista desplegable **[!UICONTROL Service]**, seleccione el servicio creado anteriormente y, a continuación, la aplicación, y haga clic en **[!UICONTROL Finish]**.

   ![](assets/nmac_android_6.png)

1. Seleccione **[!UICONTROL notification message]** como **[!UICONTROL Message Type]**.

1. Añada un título y edite el mensaje. Personalice la notificación push con **[!UICONTROL Notification options]**:

   * **[!UICONTROL Channel ID]**: configure el ID de canal de la notificación. La aplicación debe crear un canal con este ID de canal antes de recibir cualquier notificación.
   * **[!UICONTROL Sound]**: configure el sonido para que se reproduzca cuando el dispositivo reciba la notificación.
   * **[!UICONTROL Color]**: configure el color del icono de la notificación.
   * **[!UICONTROL Icon]**: configure el icono de la notificación para que se muestre en los dispositivos de sus perfiles.
   * **[!UICONTROL Tag]**: establezca el identificador utilizado para reemplazar las notificaciones existentes en el cajón de notificaciones.
   * **[!UICONTROL Click action]**: configure en la notificación la acción asociada con el clic del usuario.

   Para obtener más información sobre **[!UICONTROL Notification options]** y cómo rellenar estos campos, consulte la [documentación de FCM](https://firebase.google.com/docs/reference/fcm/rest/v1/projects.messages#androidnotification).

   ![](assets/nmac_android_8.png)

1. Si la aplicación está configurada con el protocolo de API HTTP v1, puede personalizar aún más la notificación push con el siguiente **[!UICONTROL HTTPV1 additional options]**:

   * **[!UICONTROL Ticker]**: configure el texto del valor de la notificación. Solo está disponible para dispositivos configurados con Android 5.0 Lollipop.
   * **[!UICONTROL Image]**: configure la dirección URL de la imagen para que se muestre en la notificación.
   * **[!UICONTROL Notification Count]**: configure el número de información nueva sin leer para que se muestre directamente en el icono de la aplicación.
   * **[!UICONTROL Sticky]**: establezca en true o false. Si se establece en false, la notificación se descarta automáticamente cuando el usuario hace clic en ella. Si se establece en true, la notificación se seguirá mostrando incluso cuando el usuario haga clic en ella.
   * **[!UICONTROL Notification Priority]**: establezca los niveles de prioridad de la notificación en predeterminados, mínimos, bajos o altos. Para más información, consulte la [documentación de FCM](https://firebase.google.com/docs/reference/fcm/rest/v1/projects.messages#NotificationPriority).
   * **[!UICONTROL Visibility]**: establezca los niveles de visibilidad de la notificación en pública, privada o secreta. Para más información, consulte la [documentación de FCM](https://firebase.google.com/docs/reference/fcm/rest/v1/projects.messages#visibility).

   Para obtener más información sobre **[!UICONTROL HTTP v1 additional options]** y cómo rellenar estos campos, consulte la [documentación de FCM](https://firebase.google.com/docs/reference/fcm/rest/v1/projects.messages#androidnotification).

   ![](assets/nmac_android_9.png)

1. Puede agregar información en la configuración **[!UICONTROL Application variables]** si es necesario. **[!UICONTROL Application variables]** debe configurarse en el servicio Android y formar parte de la carga de mensajes que se envía al dispositivo móvil.

1. Haga clic en **[!UICONTROL Save]** y realice la entrega.

La imagen y la página web deberían aparecer en la notificación push cuando se reciban en los dispositivos móviles Android de los suscriptores.
