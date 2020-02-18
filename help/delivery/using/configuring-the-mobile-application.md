---
title: Configuración de la aplicación móvil en Adobe Campaign
seo-title: Configuración de la aplicación móvil en Adobe Campaign
description: Configuración de la aplicación móvil en Adobe Campaign
seo-description: null
page-status-flag: never-activated
uuid: aff1a4a0-34e7-4ce0-9eb3-30a8de1380f2
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: delivery
content-type: reference
topic-tags: sending-push-notifications
discoiquuid: 7b5a1ad6-da5a-4cbd-be51-984c07c8d0b3
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 4ac96bf0e54268832b84b17c3cc577af038cc712

---


# Configuración de la aplicación móvil en Adobe Campaign {#configuring-the-mobile-application-in-adobe-campaign}

Puede encontrar debajo un ejemplo de configuración basado en una empresa que vende paquetes festivos en línea. Su aplicación móvil (Neotrips) está disponible para sus clientes en dos versiones: Neotrips para Android y Neotrips para iOS. Para configurar la aplicación móvil en Adobe Campaign, siga los siguientes pasos:

* Create a **[!UICONTROL Mobile application]** type information service for the Neotrips mobile application.
* Añada a este servicio las versiones de iOS y Android de la aplicación.
* Cree una entrega para iOS y Android.

![](assets/nmac_service_diagram.png)

>[!NOTE]
>
>Go to the **[!UICONTROL Subscriptions]** tab of the service to view the list of subscribers to the service, i.e. all people who have installed the application on their mobile and agreed to receive notifications.

## Configuración de la aplicación móvil con iOS {#configuring-the-mobile-application-ios}

>[!CAUTION]
>
>La aplicación debe estar configurada para acciones push ANTES de cualquier integración con el SDK de Adobe Campaign.
>
>If this is not the case, please refer to [this page](https://developer.apple.com/library/archive/documentation/NetworkingInternet/Conceptual/RemoteNotificationsPG/).

### Paso 1: Instalación del paquete {#installing-package-ios}

1. Acceda al asistente de importación de paquetes desde **[!UICONTROL Tools > Advanced > Package import...]** la consola de cliente de Adobe Campaign.

   ![](assets/package_ios.png)

1. Select **[!UICONTROL Install a standard package]**.

1. En la lista que aparece, marque **[!UICONTROL Mobile App Channel]**.

   ![](assets/package_ios_2.png)

1. Haga clic en **[!UICONTROL Next]**, luego **[!UICONTROL Start]** para iniciar la instalación del paquete.

   Una vez instalados los paquetes, la barra de progreso muestra el **100%** y puede ver el siguiente mensaje en los registros de instalación: **[!UICONTROL Installation of packages successful]**.

   ![](assets/package_ios_3.png)

1. **[!UICONTROL Close]** la ventana de instalación.

### Paso 2: Configuración de la cuenta externa de iOS {#configuring-external-account-ios}

Para iOS, hay dos conectores disponibles:

* El conector binario de iOS envía notificaciones en el servidor binario APNS heredado.
* El conector HTTP/2 de iOS envía notificaciones a la APNS HTTP/2.

Para elegir el conector que desea utilizar, siga estos pasos:

1. Vaya a **[!UICONTROL Administration > Platform > External accounts]**.
1. Seleccione la cuenta **[!UICONTROL iOS routing]** externa.
1. En la **[!UICONTROL Connector]** ficha, rellene el **[!UICONTROL Access URL of the connector]** campo:

   Para el conector HTTP2 de iOS: http://localhost:8080/nms/jsp/iosHTTP2.jsp

   ![](assets/nmac_connectors.png)

   >[!NOTE]
   >
   > También puede configurarlo de la siguiente manera: https://localhost:8080/nms/jsp/ios.jsp, pero le recomendamos que utilice la versión 2 del conector.

1. Haga clic **[!UICONTROL Save]**.

El conector de iOS ya está configurado. Puede empezar a crear el servicio.

### Paso 3: Configuración del servicio iOS {#configuring-ios-service}

1. Vaya al **[!UICONTROL Profiles and Targets > Services and subscriptions]** nodo y haga clic en **[!UICONTROL New]**.

   ![](assets/nmac_service_1.png)

1. Defina un **[!UICONTROL Label]** y un **[!UICONTROL Internal name]**.
1. Vaya al **[!UICONTROL Type]** campo y seleccione **[!UICONTROL Mobile application]**.

   >[!NOTE]
   >
   >The default **[!UICONTROL Subscriber applications (nms:appSubscriptionRcp)]** target mapping is linked to the recipients table. If you want to use a different target mapping, you need to create a new target mapping and enter it in the **[!UICONTROL Target mapping]** field of the service. Para obtener más información sobre la creación de destino de mapeo, consulte la [guía de configuración](../../configuration/using/about-custom-recipient-table.md).

   ![](assets/nmac_ios.png)

1. A continuación, haga clic en el **[!UICONTROL Add]** botón para seleccionar el tipo de aplicación.

   ![](assets/nmac_service_2.png)

1. Aparece la siguiente ventana. Seleccione **[!UICONTROL Create an iOS application]** y comience por introducir el **[!UICONTROL Label]**.

   ![](assets/nmac_ios_2.png)

1. Como opción, puede enriquecer el contenido de un mensaje push con algunos **[!UICONTROL Application variables]** si es necesario. Son totalmente personalizables y una parte de la carga útil de mensajes se envía al dispositivo móvil.
En el siguiente ejemplo, se agregan **mediaURl** y **mediaExt** para crear notificaciones push enriquecidas y, a continuación, se proporciona a la aplicación la imagen que se mostrará en la notificación.

   ![](assets/nmac_ios_3.png)

1. La **[!UICONTROL Subscription parameters]** ficha permite definir la asignación con una extensión del **[!UICONTROL Subscriber applications (nms:appsubscriptionRcp)]** esquema.

   >[!NOTE]
   >
   >Asegúrese de no utilizar el mismo certificado para la versión de desarrollo (entorno limitado) y la versión de producción de la aplicación.

1. La **[!UICONTROL Sounds]** ficha permite especificar un sonido para reproducir. Haga clic **[!UICONTROL Add]** y rellene el **[!UICONTROL Internal name]** campo que debe contener el nombre del archivo incrustado en la aplicación o el nombre del sonido del sistema.

1. Haga clic en **[!UICONTROL Next]** para comenzar a configurar la aplicación de desarrollo.

1. Make sure the same **[!UICONTROL Integration key]** is defined in Adobe Campaign and in the application code via the SDK. Para obtener más información sobre esto, consulte: [Integración del SDK de Campaign en la aplicación](#integrating-campaign-sdk-into-the-mobile-application)móvil. Esta clave de integración, específica de cada aplicación, permite vincular la aplicación móvil con la plataforma de Adobe Campaign.

   >[!NOTE]
   >
   > El **[!UICONTROL Integration key]** es totalmente personalizable con un valor de cadena, pero debe ser exactamente igual al especificado en el SDK.

1. Seleccione uno de los iconos listos para usar en el **[!UICONTROL Application icon]** campo para personalizar la aplicación móvil en el servicio.

1. Click the **[!UICONTROL Enter the certificate...]** link then select the authentication certificate and enter the password that was provided by the mobile application developer. Puede hacer clic en **[!UICONTROL Test the connection]** para asegurarse de que se ha realizado correctamente.

   >[!NOTE]
   >
   >Apple requiere certificados diferentes para las versiones de desarrollo y producción de una misma aplicación móvil. Deberá configurar las dos aplicaciones independientes en Adobe Campaign.

   ![](assets/nmac_ios_4.png)

1. Haga clic en **[!UICONTROL Next]** para comenzar a configurar la aplicación de producción y siga los mismos pasos que se detallan arriba.

   ![](assets/nmac_ios_5.png)

1. Haga clic **[!UICONTROL Finish]**. La aplicación de iOS ya está lista para utilizarse en Campaign Classic.

### Paso 4: Creación de una notificación enriquecida de iOS {#creating-ios-delivery}

Con iOS 10 o posterior, es posible generar notificaciones rich. Adobe Campaign puede enviar notificaciones mediante variables que permiten al dispositivo mostrar una notificación rich.

Ahora debe crear una nueva entrega y vincularla a la aplicación móvil que ha creado.

1. Vaya a **[!UICONTROL Campaign management]** > **[!UICONTROL Deliveries]**.

1. Haga clic **[!UICONTROL New]**.

   ![](assets/nmac_android_3.png)

1. Seleccione **[!UICONTROL Deliver on iOS (ios)]** en la **[!UICONTROL Delivery template]** lista desplegable. Agregue un **[!UICONTROL Label]** a la entrega.

1. Haga clic **[!UICONTROL To]** para definir la población objetivo. De forma predeterminada, se aplica la asignación de **[!UICONTROL Subscriber application]** objetivos. Haga clic **[!UICONTROL Add]** para seleccionar nuestro servicio creado anteriormente.

   ![](assets/nmac_ios_9.png)

1. En la **[!UICONTROL Target type]** ventana, seleccione **[!UICONTROL Subscribers of an iOS mobile application (iPhone, iPad)]** y haga clic en **[!UICONTROL Next]**.

1. En la **[!UICONTROL Service]** lista desplegable, seleccione el servicio creado anteriormente y, a continuación, la aplicación que desee dirigir y haga clic en **[!UICONTROL Finish]**.
Los **[!UICONTROL Application variables]** se agregan automáticamente en función de lo que se agregó durante los pasos de configuración.

   ![](assets/nmac_ios_6.png)

1. Edite la notificación enriquecida.

   ![](assets/nmac_ios_7.png)

1. Marque la **[!UICONTROL Mutable content]** casilla en la ventana de notificación de edición para permitir que la aplicación móvil descargue contenido multimedia.

1. Click **[!UICONTROL Save]** and send your delivery.

La imagen y la página web deben mostrarse en la notificación push cuando se reciben en los dispositivos iOS móviles de los suscriptores.

![](assets/nmac_ios_8.png)

## Configuración de la aplicación móvil con Android {#configuring-the-mobile-application-android}

### Paso 1: Instalación del paquete {#installing-package-android}

1. Acceda al asistente de importación de paquetes desde **[!UICONTROL Tools > Advanced > Package import...]** la consola de cliente de Adobe Campaign.

   ![](assets/package_ios.png)

1. Select **[!UICONTROL Install a standard package]**.

1. En la lista que aparece, marque **[!UICONTROL Mobile App Channel]**.

   ![](assets/package_ios_2.png)

1. Haga clic en **[!UICONTROL Next]**, luego **[!UICONTROL Start]** para iniciar la instalación del paquete.

   Una vez instalados los paquetes, la barra de progreso muestra el **100%** y puede ver el siguiente mensaje en los registros de instalación: **[!UICONTROL Installation of packages successful]**.

   ![](assets/package_ios_3.png)

1. **[!UICONTROL Close]** la ventana de instalación.

### Paso 2: Configuración de la cuenta externa de Android {#configuring-external-account-android}

Para Android, hay dos conectores disponibles:

* Conector V1, que permite una conexión por elemento secundario de MTA.
* Conector V2, que permite conexiones simultáneas con el servidor FCM para mejorar el rendimiento.

Para elegir el conector que desea utilizar, siga estos pasos:

1. Vaya a **[!UICONTROL Administration > Platform > External accounts]**.
1. Seleccione la cuenta **[!UICONTROL Android routing]** externa.
1. En la **[!UICONTROL Connector]** ficha, rellene el **[!UICONTROL JavaScript used in the connector]** campo:

   Para Android V2: https://localhost:8080/nms/jsp/androidPushConnectorV2.js

   >[!NOTE]
   >
   > También puede configurarlo de la siguiente manera: https://localhost:8080/nms/jsp/androidPushConnector.js, pero le recomendamos que utilice la versión 2 del conector.

   ![](assets/nmac_connectors3.png)

1. Para Android V2, hay un parámetro adicional disponible en el archivo de configuración de Adobe Server (serverConf.xml):

   * **maxGCMConnectPerChild**: Límite máximo de solicitudes HTTP paralelas al FCM iniciadas por cada servidor secundario (8 de forma predeterminada).

### Paso 3: Configuración del servicio Android {#configuring-android-service}

1. Vaya al **[!UICONTROL Profiles and Targets > Services and subscriptions]** nodo y haga clic en **[!UICONTROL New]**.

   ![](assets/nmac_service_1.png)

1. Defina un **[!UICONTROL Label]** y un **[!UICONTROL Internal name]**.
1. Vaya al **[!UICONTROL Type]** campo y seleccione **[!UICONTROL Mobile application]**.

   >[!NOTE]
   >
   >The default **[!UICONTROL Subscriber applications (nms:appSubscriptionRcp)]** target mapping is linked to the recipients table. If you want to use a different target mapping, you need to create a new target mapping and enter it in the **[!UICONTROL Target mapping]** field of the service. Para obtener más información sobre la creación de destino de mapeo, consulte la [guía de configuración](../../configuration/using/about-custom-recipient-table.md).

   ![](assets/nmac_ios.png)

1. A continuación, haga clic en el **[!UICONTROL Add]** botón para seleccionar el tipo de aplicación.

   ![](assets/nmac_service_2.png)

1. Select **[!UICONTROL Create an Android application]**.

   ![](assets/nmac_android.png)

1. Introduzca un **[!UICONTROL Label]**.

1. Make sure the same **[!UICONTROL Integration key]** is defined in Adobe Campaign and in the application code via the SDK. Para obtener más información sobre esto, consulte: [Integración del SDK de Campaign en la aplicación](#integrating-campaign-sdk-into-the-mobile-application)móvil.

   >[!NOTE]
   >
   > El **[!UICONTROL Integration key]** es totalmente personalizable con un valor de cadena, pero debe ser exactamente igual al especificado en el SDK.

1. Seleccione uno de los iconos listos para usar en el **[!UICONTROL Application icon]** campo para personalizar la aplicación móvil en el servicio.

1. Introduzca la configuración de conexión de la aplicación: introduzca la clave de proyecto proporcionada por el desarrollador de la aplicación móvil.

1. Como opción, puede enriquecer el contenido de un mensaje push con algunos **[!UICONTROL Application variables]** si es necesario. Son totalmente personalizables y una parte de la carga útil de mensajes se envía al dispositivo móvil.

   En el ejemplo siguiente, se agrega **title**, **imageURL** e **iconURL** para crear notificaciones push enriquecidas y, a continuación, se proporciona a la aplicación la imagen, el título y el icono que se mostrarán en la notificación.

   ![](assets/nmac_android_2.png)

1. Haga clic en **[!UICONTROL Finish]** luego **[!UICONTROL Save]**. La aplicación de Android ya está lista para utilizarse en Campaign Classic.

De forma predeterminada, Adobe Campaign guarda una clave en el campo **[!UICONTROL User identifier]** (@userKey) de la **[!UICONTROL Subscriber applications (nms:appSubscriptionRcp)]** tabla. Esta clave permite vincular una suscripción a un destinatario. Para recopilar datos adicionales (como una clave de acceso compleja), es necesario aplicar la siguiente configuración:

1. Create an extension of the **[!UICONTROL Subscriber applications (nms:appsubscriptionRcp)]** schema and define the new fields.
1. Defina la asignación en la **[!UICONTROL Subscription parameters]** ficha.
   >[!CAUTION]
   >
   >Make sure the configuration names in the **[!UICONTROL Subscription parameters]** tab are the same as those in the mobile application code. Consulte la sección [Integración del SDK de campaña en la aplicación](#integrating-campaign-sdk-into-the-mobile-application) móvil.

### Paso 4: Creación de una notificación enriquecida de Android {#creating-android-delivery}

Ahora debe crear una nueva entrega y vincularla a la aplicación móvil que ha creado.

1. Vaya a **[!UICONTROL Campaign management]** > **[!UICONTROL Deliveries]**.

1. Haga clic **[!UICONTROL New]**.

   ![](assets/nmac_android_3.png)

1. Seleccione **[!UICONTROL Deliver on Android (android)]** en la **[!UICONTROL Delivery template]** lista desplegable. Agregue un **[!UICONTROL Label]** a la entrega.

1. Haga clic **[!UICONTROL To]** para definir la población objetivo. De forma predeterminada, se aplica la asignación de **[!UICONTROL Subscriber application]** objetivos. Haga clic **[!UICONTROL Add]** para seleccionar nuestro servicio creado anteriormente.

   ![](assets/nmac_android_7.png)

1. En la **[!UICONTROL Target type]** ventana, seleccione Suscriptores de una aplicación móvil de Android y haga clic en **[!UICONTROL Next]**.

1. En la **[!UICONTROL Service]** lista desplegable, seleccione el servicio creado anteriormente y, a continuación, la aplicación, y haga clic en **[!UICONTROL Finish]**.
Los **[!UICONTROL Application variables]** se agregan automáticamente en función de lo que se agregó durante los pasos de configuración.

   ![](assets/nmac_android_6.png)

1. Edite la notificación enriquecida.

   ![](assets/nmac_android_5.png)

1. Click **[!UICONTROL Save]** and send your delivery.

La imagen y la página web deberían aparecer en la notificación push cuando se reciban en los dispositivos móviles Android de los suscriptores.

![](assets/nmac_android_4.png)
