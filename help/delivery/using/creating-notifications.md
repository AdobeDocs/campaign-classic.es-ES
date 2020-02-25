---
title: Creación de notificaciones
seo-title: Creación de notificaciones
description: Creación de notificaciones
seo-description: null
page-status-flag: never-activated
uuid: fb1862df-e616-4147-a642-dc867bc983b5
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: delivery
content-type: reference
topic-tags: sending-push-notifications
discoiquuid: 345af5c2-c852-4086-8ed0-ff3e7e402e04
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: b78db689958c9b240da9a0315060fe63bcb48e0a

---


# Creación de notificaciones{#creating-notifications}

En esta sección se detallan los elementos específicos para el envío de notificaciones en iOS y Android. En [esta sección](../../delivery/using/steps-about-delivery-creation-steps.md) se exponen conceptos globales sobre la creación de envíos.

Comience creando un nuevo envío.

![](assets/nmac_delivery_1.png)

## Envío de notificaciones en iOS {#sending-notifications-on-ios}

1. Seleccione la plantilla de envío **[!UICONTROL Deliver on iOS]** .

   ![](assets/nmac_delivery_ios_1.png)

1. To define the target of the notification, click the **[!UICONTROL To]** link, then click **[!UICONTROL Add]**.

   ![](assets/nmac_delivery_ios_2.png)

   >[!NOTE]
   >
   >En [esta sección](../../delivery/using/steps-defining-the-target-population.md) se describe el proceso detallado al seleccionar la población objetivo de un envío.
   >
   >For more on the use of personalization fields, refer to [About personalization](../../delivery/using/about-personalization.md).
   >
   >For more on the inclusion of a seed list, refer to [About seed addresses](../../delivery/using/about-seed-addresses.md).

1. Select **[!UICONTROL Subscribers of an iOS mobile application (iPhone, iPad)]**, select the service relevant to your mobile application (Neotrips, in this case), then select the iOS version of the application.

   ![](assets/nmac_delivery_ios_3.png)

1. Seleccione el tipo de notificación: **[!UICONTROL Alert]**, **[!UICONTROL Badge]**, **[!UICONTROL Alert and badge]** o **[!UICONTROL Silent Push]**.

   ![](assets/nmac_delivery_ios_4.png)

   >[!NOTE]
   >
   >El modo **Silent Push** está disponible en iOS 7. Esto permite enviar una notificación “silenciosa” a una aplicación móvil. No se avisa al usuario de la llegada de la notificación. Esta se transfiere directamente a la aplicación.

1. In the **[!UICONTROL Title]** field, enter the label of the title that you want to appear on the notification. Solo aparece en la lista de notificaciones disponibles en el centro de notificaciones. Este campo permite definir el valor del parámetro **title** de la carga útil de notificación de iOS.
1. Si utiliza el conector HTTP/2, puede añadir un subtítulo (valor del parámetro **subtitle** de la carga útil de notificación de iOS). Consulte la sección [Configuración de la aplicación móvil en Adobe Campaign](../../delivery/using/configuring-the-mobile-application.md) .
1. A continuación, introduzca el **[!UICONTROL Message]** y el **[!UICONTROL Value of the badge]** en función del tipo de notificación elegido.

   ![](assets/nmac_delivery_ios_5.png)

   >[!NOTE]
   >
   >Puede añadir emojis al contenido de su notificación. Para ello, vaya a un sitio web de listado de emojis ([ejemplo](https://www.utf8-chartable.de/unicode-utf8-table.pl?start=9728)), copie un emoji y péguelo directamente en el editor de contenido. En Windows 7, es posible que algunos emojis no se muestren correctamente en el editor (símbolo cuadrado), pero deberían aparecer correctamente en la notificación final. La posibilidad de mostrar emojis depende del sistema operativo instalado en el dispositivo. Le recomendamos que envíe pruebas para verificar que el envío se muestra correctamente antes de enviarla.

   >[!NOTE]
   >
   >**[!UICONTROL Badge]** y **[!UICONTROL Alert and badge]** las notificaciones de tipo le permiten modificar el valor del distintivo (el número encima del logotipo de la aplicación móvil). Para actualizar el distintivo, sencillamente debe introducir 0 como valor. Si el campo está vacío, el valor de la insignia no cambia.

1. The **[!UICONTROL Action button]** allows you to define a label for the action button appearing on the alert notifications (**action_loc_key** field of the payload). Si la aplicación de iOS administra cadenas localizables (**Localizable.strings**), introduzca la clave correspondiente en este campo. Si la aplicación no administra texto localizable, introduzca la etiqueta que desea ver en el botón de acción. Para obtener más información sobre cadenas localizables, consulte la [documentación de Apple](https://developer.apple.com/library/archive/documentation/NetworkingInternet/Conceptual/RemoteNotificationsPG/CreatingtheNotificationPayload.html#//apple_ref/doc/uid/TP40008194-CH10-SW1) .
1. In the **[!UICONTROL Play a sound]** field, select the sound to be played by the mobile terminal when the notification is received.

   >[!NOTE]
   >
   >Los sonidos deben incluirse en la aplicación y definirse cuando se cree el servicio. Consulte [Configuración de la cuenta](../../delivery/using/configuring-the-mobile-application.md#configuring-external-account-ios)externa de iOS.

1. In the **[!UICONTROL Application variables]** field, enter the value of each variable. Las variables de aplicación permiten definir el comportamiento de las notificaciones: por ejemplo, se puede configurar una pantalla específica de la aplicación que aparece cuando el usuario activa la notificación.

   >[!NOTE]
   >
   >Las variables de aplicación se deben definir en el código de la aplicación móvil e introducirse durante la creación del servicio. Para obtener más información sobre esto, consulte: [Configuración de una aplicación móvil en Adobe Campaign](../../delivery/using/configuring-the-mobile-application.md).

1. Once the notification is configured, click the **[!UICONTROL Preview]** tab to preview the notification.

   ![](assets/nmac_intro_2.png)

   >[!NOTE]
   >
   >El estilo de la notificación (banner o alerta) no se define en Adobe Campaign. Depende de la configuración seleccionada por el usuario en los ajustes de iOS. Sin embargo, Adobe Campaign permite previsualizar cada tipo de estilo de notificación. Haga clic en la flecha situada en la parte inferior derecha para cambiar de un estilo a otro.
   >
   >La previsualización utiliza el aspecto y la presentación de iOS 10.

Para enviar una prueba y realizar el envío final, utilice el mismo proceso que en los envíos por correo electrónico.

Después de enviar mensajes, puede monitorizar y realizar un seguimiento de los envíos. Para obtener más información, consulte estas secciones:

* [Cuarentena de notificaciones push](../../delivery/using/understanding-quarantine-management.md#push-notification-quarantines)
* [Seguimiento de un envío](../../delivery/using/monitoring-a-delivery.md)
* [Comprensión de los errores de envío](../../delivery/using/understanding-delivery-failures.md)

## Envío de notificaciones en Android {#sending-notifications-on-android}

1. Comience seleccionando la plantilla de envío **[!UICONTROL Deliver on Android (android)]** .

   ![](assets/nmac_delivery_android_1.png)

1. To define the target of the notification, click the **[!UICONTROL To]** link, then click **[!UICONTROL Add]**.

   ![](assets/nmac_delivery_android_2.png)

1. Select **[!UICONTROL Subscribers of an Android mobile application]**, choose the service relevant to your mobile application (Neotrips, in this case), then select the Android version of the application.

   ![](assets/nmac_delivery_android_3.png)

1. A continuación, introduzca el contenido de la notificación.

   ![](assets/nmac_delivery_android_4.png)

   >[!NOTE]
   >
   >Puede añadir emojis al contenido de su notificación. Para ello, vaya a un sitio web de listado de emojis ([ejemplo](https://www.utf8-chartable.de/unicode-utf8-table.pl?start=9728)), copie un emoji y péguelo directamente en el editor de contenido. En Windows 7, es posible que algunos emojis no se muestren correctamente en el editor (símbolo cuadrado); sin embargo, deberían enviarse correctamente en el correo electrónico final. La posibilidad de mostrar emojis depende del sistema operativo instalado en el dispositivo. Le recomendamos que envíe pruebas para verificar que el envío se muestra correctamente antes de enviarla.

1. In the **[!UICONTROL Application variables]** field, enter the value of each variable. Las variables de aplicación permiten definir el comportamiento de las notificaciones: por ejemplo, se puede configurar una pantalla específica de la aplicación que aparece cuando el usuario activa la notificación.

   >[!NOTE]
   >
   >Las variables de aplicación se deben definir en el código de la aplicación móvil e introducirse durante la creación del servicio. Para obtener más información sobre esto, consulte: [Configuración de una aplicación móvil en Adobe Campaign](../../delivery/using/configuring-the-mobile-application.md).

1. Once the notification is configured, click the **[!UICONTROL Preview]** tab to preview the notification.

   ![](assets/nmac_intro_1.png)

Para enviar una prueba y realizar el envío final, utilice el mismo proceso que en los envíos por correo electrónico.

El proceso detallado para validar y realizar un envío se presenta en las siguientes secciones:

* [Validación del envío](../../delivery/using/steps-validating-the-delivery.md)
* [Realización del envío](../../delivery/using/steps-sending-the-delivery.md)

Después de enviar mensajes, puede monitorizar y realizar un seguimiento de los envíos. Para obtener más información, consulte estas secciones:

* [Cuarentena de notificaciones push](../../delivery/using/understanding-quarantine-management.md#push-notification-quarantines)
* [Seguimiento de un envío](../../delivery/using/monitoring-a-delivery.md)
* [Comprensión de los errores de envío](../../delivery/using/understanding-delivery-failures.md)
