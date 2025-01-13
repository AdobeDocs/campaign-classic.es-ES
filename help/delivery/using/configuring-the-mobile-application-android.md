---
product: campaign
title: Configuración de la aplicación móvil de Android en Adobe Campaign
description: Descubra cómo configurar su aplicación móvil para Android
feature: Push
role: User, Developer
exl-id: 32c35e61-d0a3-478f-b73b-396e2becf7f9
source-git-commit: 0ed70b3c57714ad6c3926181334f57ed3b409d98
workflow-type: ht
source-wordcount: '837'
ht-degree: 100%

---

# Pasos de configuración para Android

Una vez que el paquete esté instalado, puede definir la configuración de la aplicación de Android en Adobe Campaign Classic.

Los pasos clave son los siguientes:

1. [Configuración de la cuenta externa de Android](#configuring-external-account-android)
1. [Configuración del servicio de Android](#configuring-android-service)
1. [Creación de la aplicación móvil en Campaign](#creating-android-app)
1. [Ampliación del esquema de la aplicación con datos adicionales](#extend-subscription-schema)

Podrá [crear una notificación enriquecida de Android](create-notifications-android.md).

>[!IMPORTANT]
>
>Algunos cambios importantes en el servicio Android Firebase Cloud Messaging (FCM) se lanzarán en 2024 y pueden afectar a la implementación de Adobe Campaign. Es posible que sea necesario actualizar la configuración de los servicios de suscripción para los mensajes push de Android a fin de que admitan este cambio. Ya puede comprobar y realizar acciones. Obtenga más información en esta [nota técnica de Adobe Campaign versión 8](https://experienceleague.adobe.com/docs/campaign/technotes-ac/tn-new/push-technote.html?lang=es){target="_blank"}.


## Configuración de la cuenta externa de Android {#configuring-external-account-android}

Para Android, hay dos conectores disponibles:

* Conector V1, que permite una conexión por elemento secundario de MTA.
* Conector V2, que permite conexiones simultáneas con el servidor FCM para mejorar el rendimiento.

Para elegir el conector que desea utilizar, siga estos pasos:

1. Vaya a **[!UICONTROL Administration > Platform > External accounts]**.
1. Seleccione la cuenta externa **[!UICONTROL Android routing]**.
1. En la pestaña **[!UICONTROL Connector]**, rellene el campo **[!UICONTROL JavaScript used in the connector]**:

   Para Android V2: https://localhost:8080/nms/jsp/androidPushConnectorV2.js

   >[!NOTE]
   >
   > También puede configurarlo de la siguiente manera: https://localhost:8080/nms/jsp/androidPushConnector.js, pero se recomienda utilizar la versión 2 del conector.

   ![](assets/nmac_connectors3.png)

1. Para Android V2, hay un parámetro adicional disponible en el archivo de configuración de Adobe Server (serverConf.xml):

   * **maxGCMConnectPerChild**: Límite máximo de solicitudes HTTP paralelas al FCM iniciado por cada servidor secundario (8 por defecto).

## Configuración del servicio de Android {#configuring-android-service}

![](assets/do-not-localize/how-to-video.png) [Obtenga información sobre cómo configurar un servicio de Android en vídeo](https://experienceleague.adobe.com/docs/campaign-classic-learn/getting-started-with-push-notifications-for-android/configuring-an-android-service-in-campaign.html?lang=es#configuring-an-android-service-and-creating-an-android-mobile-application-in-campaign){target="_blank"}.

1. Vaya al nodo **[!UICONTROL Profiles and Targets > Services and subscriptions]** y seleccione **[!UICONTROL New]**.

   ![](assets/nmac_service_1.png)

1. Defina un **[!UICONTROL Label]** y un **[!UICONTROL Internal name]**.
1. Vaya al campo **[!UICONTROL Type]** y seleccione **[!UICONTROL Mobile application]**.

   >[!NOTE]
   >
   >La asignación de destino predeterminada **[!UICONTROL Subscriber applications (nms:appSubscriptionRcp)]** está relacionada con la tabla de destinatarios. Si desea utilizar una asignación de destinatario diferente, debe crear una nueva asignación de destino e introducirla en el campo **[!UICONTROL Target mapping]** del servicio. Para obtener más información sobre la creación de asignación de destino, consulte [esta sección](../../configuration/using/about-custom-recipient-table.md).

   ![](assets/nmac_ios.png)

1. A continuación, haga clic en el botón **[!UICONTROL Add]** para seleccionar el tipo de aplicación.

   ![](assets/nmac_service_2.png)

1. Cree la aplicación de Android. Para obtener más información, consulte [esta sección](configuring-the-mobile-application-android.md#creating-android-app).

## Creación de la aplicación móvil de Android {#creating-android-app}

Después de crear el servicio, debe crear la aplicación de Android:

1. En el servicio recién creado, haga clic en el botón **[!UICONTROL Add]** para seleccionar el tipo de aplicación.

   ![](assets/nmac_service_2.png)

1. Seleccione **[!UICONTROL Create an Android application]** y escriba un **[!UICONTROL Label]**.

   ![](assets/nmac_android.png)

1. Asegúrese de que se ha definido la misma **[!UICONTROL Integration key]** en Adobe Campaign y en el código de aplicación a través del SDK.<!--For more on this, refer to [this section](integrating-campaign-sdk-into-the-mobile-application.md).-->

   >[!NOTE]
   >
   > **[!UICONTROL Integration key]** es totalmente personalizable con un valor de cadena, pero debe ser exactamente igual al especificado en el SDK.

1. Seleccione la **[!UICONTROL API version]**: HTTP v1 o HTTP (heredada). Estas configuraciones se detallan en [esta sección](#select-api-version)

1. Rellene los campos **[!UICONTROL Firebase Cloud Messaging the Android connection settings]**.

1. Haga clic en **[!UICONTROL Finish]**, luego en **[!UICONTROL Save]**. La aplicación de Android ya está lista para su uso en Campaign Classic.

De forma predeterminada, Adobe Campaign guarda una clave en el campo **[!UICONTROL User identifier]** (@userKey) de la tabla **[!UICONTROL Subscriber applications (nms:appSubscriptionRcp)]**. Esta clave permite vincular una suscripción a un destinatario. Para recopilar datos adicionales (como una clave de reconciliación compleja), es necesario aplicar la siguiente configuración:

### Configure la versión de la API{#select-api-version}

>[!IMPORTANT]
>
>Algunos cambios importantes en el servicio Android Firebase Cloud Messaging (FCM) se lanzarán en 2024 y pueden afectar a la implementación de Adobe Campaign. Como parte del esfuerzo continuo de Google por mejorar sus servicios, las API de FCM existentes dejarán de usarse el **20 de junio de 2024**. Obtenga más información en esta [nota técnica de Adobe Campaign versión 8](https://experienceleague.adobe.com/docs/campaign/technotes-ac/tn-new/push-technote.html?lang=es){target="_blank"}.

Después de crear el servicio y una nueva aplicación móvil, deberá configurar la aplicación móvil. La API de **HTTP (existente)** no debe seleccionarse, ya que ha quedado obsoleta en Google.

Para configurar la versión de la API HTTP v1, siga los pasos a continuación:

1. En la ventana **[!UICONTROL Mobile application creation wizard]**, seleccione **[!UICONTROL HTTPV1]** en la lista desplegable **[!UICONTROL API version]**.

1. Haga clic en **[!UICONTROL Load project json file to extract project details...]** para cargar directamente el archivo con clave JSON. Para obtener más información sobre cómo extraer el archivo JSON, consulte [esta página](https://firebase.google.com/docs/admin/setup#initialize-sdk).

   También puede introducir manualmente los siguientes detalles:
   * **[!UICONTROL Project Id]**
   * **[!UICONTROL Private Key]**
   * **[!UICONTROL Client Email]**

   ![](assets/nmac_android_10.png)

1. Haga clic en **[!UICONTROL Test the connection]** para comprobar que la configuración es correcta y que el servidor de marketing tiene acceso a FCM.

   >[!CAUTION]
   >
   >Para la implementación intermediaria, el botón **[!UICONTROL Test connection]** no comprueba si el servidor MID tiene acceso al servidor FCM.

   ![](assets/nmac_android_11.png)

1. Como opción, puede enriquecer el contenido de un mensaje push con algunos **[!UICONTROL Application variables]** si es necesario. Son totalmente personalizables y una parte de la carga útil de mensajes se envía al dispositivo móvil.

1. Haga clic en **[!UICONTROL Finish]**, luego en **[!UICONTROL Save]**. La aplicación de Android ya está lista para su uso en Campaign Classic.

A continuación se muestran los nombres de carga útil de FCM para personalizar aún más la notificación push:

| Tipo de mensaje | Elemento de mensaje configurable (nombre de carga útil de FCM) | Opciones configurables (nombre de carga útil de FCM) |
|:-:|:-:|:-:|
| mensaje de datos | N/A | validate_only |
| mensaje de notificación | title, body, android_channel_id, icon, sound, tag, color, click_action, image, ticker, sticky, visibility, notification_priority, notification_count <br> | validate_only |

## Ampliación del esquema appsubscriptionRcp {#extend-subscription-schema}

![](assets/do-not-localize/how-to-video.png) [Obtenga información sobre cómo ampliar el esquema appsubscriptionRcp con este vídeo](https://experienceleague.adobe.com/docs/campaign-classic-learn/getting-started-with-push-notifications-for-android/extending-the-app-subscription-schema.html?lang=es#extending-the-app-subscription-schema-to-personalize-push-notifications)

Deberá ampliar **appsubscriptionRcp** para definir nuevos campos adicionales que almacenen parámetros de la aplicación en la base de datos de Campaign. Estos campos se utilizan, por ejemplo, para la personalización. Para ello:

1. Cree una extensión del esquema **[!UICONTROL Subscriber applications (nms:appsubscriptionRcp)]** y defina los campos nuevos. Obtenga más información sobre la extensión de esquema en [esta página](../../configuration/using/about-schema-edition.md).

1. Defina la asignación en la pestaña **[!UICONTROL Subscription parameters]**.

   >[!CAUTION]
   >
   >Asegúrese de que los nombres de configuración en la pestaña **[!UICONTROL Subscription parameters]** sean los mismos que los del código de la aplicación móvil.<!--Refer to [this section](integrating-campaign-sdk-into-the-mobile-application.md).-->
