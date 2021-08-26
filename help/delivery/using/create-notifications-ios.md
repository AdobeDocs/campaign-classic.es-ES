---
product: campaign
title: Creación de una notificación push para dispositivos iOS
description: Aprenda a crear notificaciones push para iOS
audience: delivery
content-type: reference
topic-tags: sending-push-notifications
exl-id: 13ccc5d6-4355-42ba-80dc-30a45d3b69a4
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '783'
ht-degree: 100%

---

# Creación de notificaciones para iOS{#create-notifications-ios}

![](../../assets/common.svg)

En esta sección se detallan los elementos específicos para la entrega de notificaciones en iOS. En [esta sección](steps-about-delivery-creation-steps.md) se exponen conceptos globales sobre la creación de envíos.

Comience creando una nueva entrega.

![](assets/nmac_delivery_1.png)

Para crear una notificación push para dispositivos iOS, siga los pasos a continuación:

1. Seleccione la plantilla de envíos **[!UICONTROL Deliver on iOS]**.

   ![](assets/nmac_delivery_ios_1.png)

1. Para definir el objetivo de la notificación, haga clic en el enlace **[!UICONTROL To]** y, luego, en **[!UICONTROL Add]**.

   ![](assets/nmac_delivery_ios_2.png)

   >[!NOTE]
   >
   >En [esta sección](steps-defining-the-target-population.md) se describe el proceso detallado al seleccionar la población objetivo de una entrega.
   >
   >Para obtener más información sobre el uso de los campos de personalización, consulte [esta sección](about-personalization.md).
   >
   >Para obtener más información sobre la integración de una lista de reasignación, consulte [Acerca de las direcciones semilla](about-seed-addresses.md)

1. Seleccione **[!UICONTROL Subscribers of an iOS mobile application (iPhone, iPad)]**, seleccione el servicio correspondiente a su aplicación móvil (Neotrips, en este caso) y luego seleccione la versión de iOS de la aplicación.

   ![](assets/nmac_delivery_ios_3.png)

1. Seleccione el tipo de notificación: **[!UICONTROL Alert]**, **[!UICONTROL Badge]**, **[!UICONTROL Alert and badge]** o **[!UICONTROL Silent Push]**.

   ![](assets/nmac_delivery_ios_4.png)

   >[!NOTE]
   >
   >El modo **Push silenciosa** permite enviar una notificación “silenciosa” a una aplicación móvil. No se avisa al usuario de la llegada de la notificación. Esta se transfiere directamente a la aplicación.

1. En el campo **[!UICONTROL Title]**, introduzca la etiqueta del título que desea que aparezca en la notificación. Solo aparece en la lista de notificaciones disponibles en el centro de notificaciones. Este campo permite definir el valor del parámetro **title** de la carga útil de notificación de iOS.

1. Si utiliza el conector HTTP/2, puede añadir un subtítulo (valor del parámetro **subtitle** de la carga útil de notificación de iOS). Consulte [esta sección](configuring-the-mobile-application.md).

1. A continuación, introduzca el **[!UICONTROL Message]** y el **[!UICONTROL Value of the badge]** en función del tipo de notificación elegido.

   ![](assets/nmac_delivery_ios_5.png)

   >[!NOTE]
   >
   >Las notificaciones de tipo **[!UICONTROL Badge]** y **[!UICONTROL Alert and badge]** permiten modificar el valor del distintivo (el número situado encima del logotipo de la aplicación móvil). Para actualizar el distintivo, sencillamente debe introducir 0 como valor. Si el campo está vacío, el valor de la insignia no cambia.

1. Haga clic en el icono **[!UICONTROL Insert emoticon]** para insertar emoticonos en la notificación push. Para personalizar la lista de emoticonos, consulte [esta sección](customizing-emoticon-list.md)

1. **[!UICONTROL Action button]** le permite definir una etiqueta para el botón de acción que aparece en las notificaciones de alerta (campo **action_loc_key** de la carga útil). Si la aplicación de iOS administra cadenas localizables (**Localizable.strings**), introduzca la clave correspondiente en este campo. Si la aplicación no administra texto localizable, introduzca la etiqueta que desea ver en el botón de acción. Para obtener más información sobre cadenas localizables, consulte la [documentación de Apple](https://developer.apple.com/library/archive/documentation/NetworkingInternet/Conceptual/RemoteNotificationsPG/CreatingtheNotificationPayload.html#//apple_ref/doc/uid/TP40008194-CH10-SW1).
1. En el campo **[!UICONTROL Play a sound]**, seleccione el sonido que el terminal móvil debe reproducir cuando reciba la notificación.

   >[!NOTE]
   >
   >Los sonidos deben incluirse en la aplicación y definirse cuando se cree el servicio. Consulte [esta sección](configuring-the-mobile-application.md#configuring-external-account-ios).

1. En el campo **[!UICONTROL Application variables]**, introduzca el valor de cada variable. Las variables de aplicación permiten definir el comportamiento de las notificaciones: por ejemplo, se puede configurar una pantalla específica de la aplicación que aparece cuando el usuario activa la notificación.

   >[!NOTE]
   >
   >Las variables de aplicación se deben definir en el código de la aplicación móvil e introducirse durante la creación del servicio. Para obtener más información, consulte [esta sección](configuring-the-mobile-application.md).

1. Una vez configurada la notificación, haga clic en la pestaña **[!UICONTROL Preview]** para previsualizar la notificación.

   ![](assets/nmac_intro_2.png)

   >[!NOTE]
   >
   >El estilo de la notificación (banner o alerta) no se define en Adobe Campaign. Depende de la configuración seleccionada por el usuario en los ajustes de iOS. Sin embargo, Adobe Campaign permite previsualizar cada tipo de estilo de notificación. Haga clic en la flecha situada en la parte inferior derecha para cambiar de un estilo a otro.
   >
   >La previsualización utiliza el aspecto y la presentación de iOS 10.

Para enviar una prueba y realizar la entrega final, utilice el mismo proceso que en las entregas por correo electrónico.

Después de enviar mensajes, puede monitorizar y realizar un seguimiento de las entregas. Para obtener más información, consulte estas secciones:

* [Cuarentenas de notificaciones push](understanding-quarantine-management.md#push-notification-quarantines)
* [Seguimiento de una entrega](about-delivery-monitoring.md)
* [Comprensión de los errores de entrega](understanding-delivery-failures.md)


## Creación de una notificación enriquecida de iOS {#creating-ios-delivery}

Con iOS 10 o posterior, es posible generar notificaciones rich. Adobe Campaign puede enviar notificaciones mediante variables que permiten al dispositivo mostrar una notificación rich.

Debe crear un nuevo envío y vincularlo a la aplicación móvil creada.

1. Vaya a **[!UICONTROL Campaign management]** > **[!UICONTROL Deliveries]**.

1. Haga clic **[!UICONTROL New]**.

   ![](assets/nmac_android_3.png)

1. Seleccione **[!UICONTROL Deliver on iOS (ios)]** en la lista desplegable **[!UICONTROL Delivery template]**. Añada un **[!UICONTROL Label]** al envío.

1. Haga clic en **[!UICONTROL To]** para definir la población en destinatario. De forma predeterminada, se aplica la asignación de destino **[!UICONTROL Subscriber application]**. Haga clic en **[!UICONTROL Add]** para seleccionar el servicio creado anteriormente.

   ![](assets/nmac_ios_9.png)

1. En la ventana **[!UICONTROL Target type]**, seleccione **[!UICONTROL Subscribers of an iOS mobile application (iPhone, iPad)]** y haga clic en **[!UICONTROL Next]**.

1. En la lista desplegable **[!UICONTROL Service]**, seleccione el servicio creado anteriormente, luego la aplicación a la que desee dirigirse y haga clic en **[!UICONTROL Finish]**.
Las **[!UICONTROL Application variables]** se añaden automáticamente en función de lo que se añadió durante los pasos de configuración.

   ![](assets/nmac_ios_6.png)

1. Edite la notificación enriquecida.

   ![](assets/nmac_ios_7.png)

1. Marque la casilla **[!UICONTROL Mutable content]** en la ventana de notificación de edición para permitir que la aplicación móvil descargue contenido de medios.

1. Haga clic en **[!UICONTROL Save]** y realice la entrega.

La imagen y la página web deben aparecer en la notificación push cuando se reciban en los dispositivos móviles iOS de los suscriptores.

![](assets/nmac_ios_8.png)
