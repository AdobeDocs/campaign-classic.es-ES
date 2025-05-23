---
product: campaign
title: Configuración de la aplicación móvil de iOS en Adobe Campaign
description: Descubra cómo configurar su aplicación móvil para iOS
feature: Push
role: User, Developer
level: Intermediate, Experienced
exl-id: 67eee1c5-a918-46b9-875d-7c3c71c00635
source-git-commit: 2bfcec5eaa1145cfb88adfa9c8b2f72ee3cd9469
workflow-type: ht
source-wordcount: '588'
ht-degree: 100%

---

# Pasos de configuración para iOS {#configuring-the-mobile-application-in-adobe-campaign-ios}

Una vez que el paquete esté instalado, puede definir la configuración de la aplicación de iOS en Adobe Campaign Classic.

Los pasos clave son los siguientes:

1. [Configuración de la cuenta externa de iOS](#configuring-external-account-ios)
1. [Configuración del servicio de iOS](#configuring-ios-service)
1. [Integración de la aplicación móvil de iOS en Campaign](#creating-ios-app)

A continuación, podrá [crear una notificación push para los dispositivos iOS](create-notifications-ios.md).

## Configuración de la cuenta externa de iOS {#configuring-external-account-ios}

Para iOS, el conector HTTP/2 de iOS envía notificaciones a la APNS HTTP/2.

Para configurar este conector, siga estos pasos:

1. Vaya a **[!UICONTROL Administration > Platform > External accounts]**.
1. Seleccione la cuenta externa **[!UICONTROL iOS routing]**.
1. En la pestaña **[!UICONTROL Connector]**, rellene el campo **[!UICONTROL Access URL of the connector]** con la siguiente dirección URL: ```http://localhost:8080/nms/jsp/iosHTTP2.jsp```

   ![](assets/nmac_connectors.png)

1. Haga clic **[!UICONTROL Save]**.

Ya está configurado el conector de iOS. Puede crear su servicio.

## Configuración del servicio iOS {#configuring-ios-service}

>[!CAUTION]
>
>La aplicación debe estar configurada para acciones push ANTES de cualquier integración con el SDK de Adobe 
>
>Si no es así, consulte [esta página](https://developer.apple.com/documentation/usernotifications).

1. Vaya al nodo **[!UICONTROL Profiles and Targets > Services and subscriptions]** y seleccione **[!UICONTROL New]**.

   ![](assets/nmac_service_1.png)

1. Defina un **[!UICONTROL Label]** y un **[!UICONTROL Internal name]**.
1. Vaya al campo **[!UICONTROL Type]** y seleccione **[!UICONTROL Mobile application]**.

   >[!NOTE]
   >
   >La asignación de destino predeterminada **[!UICONTROL Subscriber applications (nms:appSubscriptionRcp)]** está relacionada con la tabla de destinatarios. Si desea utilizar una asignación de destinatario diferente, debe crear una nueva asignación de destino e introducirla en el campo **[!UICONTROL Target mapping]** del servicio. Para obtener más información sobre la creación de asignación de destinatario, consulte la [guía de configuración](../../configuration/using/about-custom-recipient-table.md).

   ![](assets/nmac_ios.png)

1. A continuación, haga clic en el botón **[!UICONTROL Add]** para seleccionar el tipo de aplicación.

   ![](assets/nmac_service_2.png)

1. Cree sus aplicaciones de desarrollo y producción de iOS. Para obtener más información, consulte [esta sección](configuring-the-mobile-application.md#creating-ios-app).

## Creación de una aplicación móvil de iOS {#creating-ios-app}

Después de crear el servicio, cree la aplicación de iOS en Campaign. Siga estos pasos:

1. En el servicio recién creado, haga clic en el botón **[!UICONTROL Add]** para seleccionar el tipo de aplicación.

   ![](assets/nmac_service_2.png)

1. Aparece la siguiente ventana. Seleccione **[!UICONTROL Create an iOS application]** y comience introduciendo el **[!UICONTROL Label]**.

   ![](assets/nmac_ios_2.png)

1. Como opción, puede enriquecer el contenido de un mensaje push con algunos **[!UICONTROL Application variables]** si es necesario. Son totalmente personalizables y una parte de la carga útil de mensajes se envía al dispositivo móvil.
En el siguiente ejemplo, se añaden **mediaURl** y **mediaExt** para crear notificaciones push enriquecidas y, a continuación, se proporciona a la aplicación la imagen que se muestra en la notificación.

   ![](assets/nmac_ios_3.png)

1. La pestaña **[!UICONTROL Subscription parameters]** permite definir la asignación con una extensión del esquema **[!UICONTROL Subscriber applications (nms:appsubscriptionRcp)]**.

   >[!NOTE]
   >
   >Asegúrese de no utilizar el mismo certificado para la versión de desarrollo (zona protegida) y la versión de producción de la aplicación.

1. La pestaña **[!UICONTROL Sounds]** permite especificar un sonido para reproducir. Haga clic en **[!UICONTROL Add]** y rellene el campo **[!UICONTROL Internal name]** que debe contener el nombre del archivo incrustado en la aplicación o el nombre del sonido del sistema.

1. Haga clic en **[!UICONTROL Next]** para comenzar a configurar la aplicación de desarrollo.

1. Asegúrese de que se ha definido la misma **[!UICONTROL Integration key]** en Adobe Campaign y en el código de la aplicación a través del SDK. <!--For more on this, refer to [this page](integrating-campaign-sdk-into-the-mobile-application.md).-->Esta clave de integración, que es específica de cada aplicación, permite vincular la aplicación móvil con la plataforma de Adobe Campaign.

   >[!NOTE]
   >
   > **[!UICONTROL Integration key]** es totalmente personalizable con un valor de cadena, pero debe ser exactamente igual al especificado en el SDK.

1. Seleccione uno de los iconos predeterminados en el campo **[!UICONTROL Application icon]** para personalizar la aplicación móvil en el servicio.

1. Seleccione el **[!UICONTROL Authentication mode]**.

   ![](assets/nmac_ios_5.png)

   Hay dos modos disponibles:

   * (Recomendado) **[!UICONTROL Token-based authentication]**: complete la configuración las conexiones APNS **[!UICONTROL Key Id]**, **[!UICONTROL Team Id]** y **[!UICONTROL Bundle Id]** y luego seleccione el certificado p8 haciendo clic en **[!UICONTROL Enter the private key...]**. Para más información sobre **[!UICONTROL Token-based authentication]**, consulte la [documentación de Apple](https://developer.apple.com/documentation/usernotifications/setting_up_a_remote_notification_server/establishing_a_token-based_connection_to_apns){target="_blank"}.

   * **[!UICONTROL Certificate-based authentication]**: haga clic en **[!UICONTROL Enter the certificate...]**, seleccione la clave p12 e introduzca la contraseña proporcionada por el desarrollador de aplicaciones móviles.

   >[!NOTE]
   >
   > Adobe recomienda utilizar **[!UICONTROL Token-based authentication]** para la configuración de iOS, ya que las claves de autenticación P8 son más nuevas y seguras.

1. Utilice el botón **[!UICONTROL Test the connection]** para validar la configuración.

1. Haga clic en **[!UICONTROL Next]** para configurar la aplicación de producción y siga los mismos pasos detallados anteriormente.


1. Haga clic en **[!UICONTROL Finish]**.

La aplicación de iOS ya está lista para su uso en Campaign Classic.
