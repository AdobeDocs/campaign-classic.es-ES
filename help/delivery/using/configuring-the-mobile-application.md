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
translation-type: ht
source-git-commit: a358da7c499b5ee780563b4aef0eb2f4463186cf

---


# Configuración de la aplicación móvil en Adobe Campaign {#configuring-the-mobile-application-in-adobe-campaign}

Puede encontrar debajo un ejemplo de configuración basado en una empresa que vende paquetes festivos en línea. Su aplicación móvil (Neotrips) está disponible para sus clientes en dos versiones: Neotrips para Android y Neotrips para iOS. Para configurar la aplicación móvil en Adobe Campaign, siga los siguientes pasos:

* Cree un servicio de información de tipo **[!UICONTROL Mobile application]** para la aplicación móvil Neotrips.
* Añada a este servicio las versiones de iOS y Android de la aplicación.
* Cree un envío tanto para iOS como para Android.

![](assets/nmac_service_diagram.png)

>[!NOTE]
>
>Vaya a la pestaña **[!UICONTROL Subscriptions]** para ver la lista de suscriptores del servicio, es decir, todas las personas que hayan instalado la aplicación en su móvil y hayan aceptado recibir notificaciones.

## Configuración de la aplicación móvil con iOS {#configuring-the-mobile-application-ios}

>[!CAUTION]
>
>La aplicación debe estar configurada para acciones push ANTES de cualquier integración con el SDK de Adobe Campaign.
>
>Si no es así, consulte [esta página](https://developer.apple.com/library/archive/documentation/NetworkingInternet/Conceptual/RemoteNotificationsPG/).

### Paso 1: Instalación del paquete {#installing-package-ios}

1.  En la consola de cliente de Adobe Campaign, acceda al asistente de importación del paquete desde **[!UICONTROL Tools > Advanced > Package import...]**.

   ![](assets/package_ios.png)

1. Seleccione **[!UICONTROL Install a standard package]**.

1. En la lista que aparece, marque **[!UICONTROL Mobile App Channel]**.

   ![](assets/package_ios_2.png)

1. Haga clic en **[!UICONTROL Next]**, luego en **[!UICONTROL Start]** para iniciar la instalación del paquete.

   Una vez instalados los paquetes, la barra de progreso muestra el **100 %** y puede ver el siguiente mensaje en los registros de instalación: **[!UICONTROL Installation of packages successful]**.

   ![](assets/package_ios_3.png)

1. **[!UICONTROL Close]** la ventana de instalación.

### Paso 2: Configuración de la cuenta externa de iOS {#configuring-external-account-ios}

Para iOS, hay dos conectores disponibles:

* El conector binario de iOS envía notificaciones en el servidor binario APNS heredado.
* El conector HTTP/2 de iOS envía notificaciones a la APNS HTTP/2.

Para elegir el conector que desea utilizar, siga estos pasos:

1. Vaya a **[!UICONTROL Administration > Platform > External accounts]**.
1. Seleccione la cuenta externa **[!UICONTROL iOS routing]**.
1. En la pestaña **[!UICONTROL Connector]**, rellene el campo **[!UICONTROL Access URL of the connector]**:

   Para el conector HTTP2 de iOS: http://localhost:8080/nms/jsp/iosHTTP2.jsp

   ![](assets/nmac_connectors.png)

   >[!NOTE]
   >
   > También puede configurarlo de la siguiente manera: https://localhost:8080/nms/jsp/ios.jsp, pero le recomendamos que utilice la versión 2 del conector.

1. Haga clic **[!UICONTROL Save]**.

Ya está configurado el conector de iOS. Puede crear su servicio.

### Paso 3: Configuración del servicio iOS {#configuring-ios-service}

1. Vaya al nodo **[!UICONTROL Profiles and Targets > Services and subscriptions]** y seleccione **[!UICONTROL New]**.

   ![](assets/nmac_service_1.png)

1. Defina un **[!UICONTROL Label]** y un **[!UICONTROL Internal name]**.
1. Vaya al campo **[!UICONTROL Type]** y seleccione **[!UICONTROL Mobile application]**.

   >[!NOTE]
   >
   >La asignación de destino predeterminada **[!UICONTROL Subscriber applications (nms:appSubscriptionRcp)]** está relacionada con la tabla de destinatarios. Si desea utilizar una asignación de destino diferente, debe crear una nueva asignación de destino e introducirla en el campo **[!UICONTROL Target mapping]** del servicio. Para obtener más información sobre la creación de destino de mapeo, consulte la [guía de configuración](../../configuration/using/about-custom-recipient-table.md).

   ![](assets/nmac_ios.png)

1. A continuación, haga clic en el botón **[!UICONTROL Add]** para seleccionar el tipo de aplicación.

   ![](assets/nmac_service_2.png)

1. Aparece la siguiente ventana. Seleccione **[!UICONTROL Create an iOS application]** y comience introduciendo el **[!UICONTROL Label]**.

   ![](assets/nmac_ios_2.png)

1. Como opción, puede enriquecer el contenido de un mensaje push con algunos **[!UICONTROL Application variables]** si es necesario. Son totalmente personalizables y una parte de la carga útil de mensajes se envía al dispositivo móvil.
En el siguiente ejemplo, se añaden **mediaURl** y **mediaExt** para crear notificaciones push enriquecidas y, a continuación, se proporciona a la aplicación la imagen que se muestra en la notificación.

   ![](assets/nmac_ios_3.png)

1. La pestaña **[!UICONTROL Subscription parameters]** permite definir la asignación con una extensión del esquema **[!UICONTROL Subscriber applications (nms:appsubscriptionRcp)]**.

   >[!NOTE]
   >
   >Asegúrese de no utilizar el mismo certificado para la versión de desarrollo (entorno limitado) y la versión de producción de la aplicación.

1. La pestaña **[!UICONTROL Sounds]** permite especificar un sonido para reproducir. Haga clic en **[!UICONTROL Add]** y rellene el campo **[!UICONTROL Internal name]** que debe contener el nombre del archivo incrustado en la aplicación o el nombre del sonido del sistema.

1. Haga clic en **[!UICONTROL Next]** para comenzar a configurar la aplicación de desarrollo.

1. Asegúrese de que se ha definido la misma **[!UICONTROL Integration key]** en Adobe Campaign y en el código de la aplicación a través del SDK. Para obtener más información, consulte: [Integración del SDK de Campaign en la aplicación móvil](../../delivery/using/integrating-campaign-sdk-into-the-mobile-application.md). Esta clave de integración, específica de cada aplicación, permite vincular la aplicación móvil con la plataforma de Adobe Campaign.

   >[!NOTE]
   >
   > **[!UICONTROL Integration key]** es totalmente personalizable con un valor de cadena, pero debe ser exactamente igual al especificado en el SDK.

1. Seleccione uno de los iconos predeterminados en el campo **[!UICONTROL Application icon]** para personalizar la aplicación móvil en el servicio.

1. Haga clic en el enlace **[!UICONTROL Enter the certificate...]**, seleccione el certificado de autenticación e introduzca la contraseña que proporcionó el desarrollador de aplicaciones móviles. Puede hacer clic en **[!UICONTROL Test the connection]** para asegurarse de que se ha realizado correctamente.

   >[!NOTE]
   >
   >Apple requiere certificados diferentes para las versiones de desarrollo y producción de una misma aplicación móvil. Debe configurar las dos aplicaciones independientes en Adobe Campaign.

   ![](assets/nmac_ios_4.png)

1. Haga clic en **[!UICONTROL Next]** para configurar la aplicación de producción y siga los mismos pasos detallados anteriormente.

   ![](assets/nmac_ios_5.png)

1. Haga clic **[!UICONTROL Finish]**. La aplicación de iOS ya está lista para su uso en Campaign Classic.

### Paso 4: Creación de una notificación enriquecida de iOS {#creating-ios-delivery}

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

## Configuración de la aplicación móvil con Android {#configuring-the-mobile-application-android}

### Paso 1: Instalación del paquete {#installing-package-android}

1.  En la consola de cliente de Adobe Campaign, acceda al asistente de importación del paquete desde **[!UICONTROL Tools > Advanced > Package import...]**.

   ![](assets/package_ios.png)

1. Seleccione **[!UICONTROL Install a standard package]**.

1. En la lista que aparece, marque **[!UICONTROL Mobile App Channel]**.

   ![](assets/package_ios_2.png)

1. Haga clic en **[!UICONTROL Next]**, luego en **[!UICONTROL Start]** para iniciar la instalación del paquete.

   Una vez instalados los paquetes, la barra de progreso muestra el **100 %** y puede ver el siguiente mensaje en los registros de instalación: **[!UICONTROL Installation of packages successful]**.

   ![](assets/package_ios_3.png)

1. **[!UICONTROL Close]** la ventana de instalación.

### Paso 2: Configuración de la cuenta externa de Android {#configuring-external-account-android}

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

### Paso 3: Configuración del servicio Android {#configuring-android-service}

1. Vaya al nodo **[!UICONTROL Profiles and Targets > Services and subscriptions]** y seleccione **[!UICONTROL New]**.

   ![](assets/nmac_service_1.png)

1. Defina un **[!UICONTROL Label]** y un **[!UICONTROL Internal name]**.
1. Vaya al campo **[!UICONTROL Type]** y seleccione **[!UICONTROL Mobile application]**.

   >[!NOTE]
   >
   >La asignación de destino predeterminada **[!UICONTROL Subscriber applications (nms:appSubscriptionRcp)]** está relacionada con la tabla de destinatarios. Si desea utilizar una asignación de destino diferente, debe crear una nueva asignación de destino e introducirla en el campo **[!UICONTROL Target mapping]** del servicio. Para obtener más información sobre la creación de destino de mapeo, consulte la [guía de configuración](../../configuration/using/about-custom-recipient-table.md).

   ![](assets/nmac_ios.png)

1. A continuación, haga clic en el botón **[!UICONTROL Add]** para seleccionar el tipo de aplicación.

   ![](assets/nmac_service_2.png)

1. Seleccione **[!UICONTROL Create an Android application]**.

   ![](assets/nmac_android.png)

1. Introduzca un **[!UICONTROL Label]**.

1. Asegúrese de que se ha definido la misma **[!UICONTROL Integration key]** en Adobe Campaign y en el código de la aplicación a través del SDK. Para obtener más información, consulte: [Integración del SDK de Campaign en la aplicación móvil](../../delivery/using/integrating-campaign-sdk-into-the-mobile-application.md).

   >[!NOTE]
   >
   > **[!UICONTROL Integration key]** es totalmente personalizable con un valor de cadena, pero debe ser exactamente igual al especificado en el SDK.

1. Seleccione uno de los iconos predeterminados en el campo **[!UICONTROL Application icon]** para personalizar la aplicación móvil en el servicio.

1. Introduzca la configuración de conexión de la aplicación: escriba la clave de proyecto que proporcionó el desarrollador de la aplicación móvil.

1. Como opción, puede enriquecer el contenido de un mensaje push con algunos **[!UICONTROL Application variables]** si es necesario. Son totalmente personalizables y una parte de la carga útil de mensajes se envía al dispositivo móvil.

   En el ejemplo siguiente, se añade **title**, **imageURL** e **iconURL** para crear notificaciones push enriquecidas y, a continuación, se proporciona a la aplicación la imagen, el título y el icono que se muestran en la notificación.

   ![](assets/nmac_android_2.png)

1. Haga clic en **[!UICONTROL Finish]**, luego en **[!UICONTROL Save]**. La aplicación de Android ya está lista para su uso en Campaign Classic.

De forma predeterminada, Adobe Campaign guarda una clave en el campo **[!UICONTROL User identifier]** (@userKey) de la tabla **[!UICONTROL Subscriber applications (nms:appSubscriptionRcp)]**. Esta clave permite vincular una suscripción a un destinatario. Para recopilar datos adicionales (como una clave de acceso compleja), es necesario aplicar la siguiente configuración:

1. Cree una extensión del esquema **[!UICONTROL Subscriber applications (nms:appsubscriptionRcp)]** y defina los campos nuevos.
1. Defina la asignación en la pestaña **[!UICONTROL Subscription parameters]**.
   >[!CAUTION]
   >
   >Asegúrese de que los nombres de configuración en la pestaña **[!UICONTROL Subscription parameters]** sean los mismos que los del código de la aplicación móvil. Consulte la sección [Integración del SDK de campaña en la aplicación móvil](../../delivery/using/integrating-campaign-sdk-into-the-mobile-application.md).

### Paso 4: Creación de una notificación enriquecida de Android {#creating-android-delivery}

Debe crear un nuevo envío y vincularlo a la aplicación móvil creada.

1. Vaya a **[!UICONTROL Campaign management]** > **[!UICONTROL Deliveries]**.

1. Haga clic **[!UICONTROL New]**.

   ![](assets/nmac_android_3.png)

1. Seleccione **[!UICONTROL Deliver on Android (android)]** en la lista desplegable **[!UICONTROL Delivery template]**. Añada un **[!UICONTROL Label]** al envío.

1. Haga clic en **[!UICONTROL To]** para definir la población en destinatario. De forma predeterminada, se aplica la asignación de destino **[!UICONTROL Subscriber application]**. Haga clic en **[!UICONTROL Add]** para seleccionar el servicio creado anteriormente.

   ![](assets/nmac_android_7.png)

1. En la ventana **[!UICONTROL Target type]**, seleccione Suscriptores de una aplicación móvil de Android y haga clic en **[!UICONTROL Next]**.

1. En la lista desplegable **[!UICONTROL Service]**, seleccione el servicio creado anteriormente y, a continuación, la aplicación, y haga clic en **[!UICONTROL Finish]**.
Las **[!UICONTROL Application variables]** se añaden automáticamente en función de lo que se añadió durante los pasos de configuración.

   ![](assets/nmac_android_6.png)

1. Edite la notificación enriquecida.

   ![](assets/nmac_android_5.png)

1. Haga clic en **[!UICONTROL Save]** y realice la entrega.

La imagen y la página web deberían aparecer en la notificación push cuando se reciban en los dispositivos móviles Android de los suscriptores.

![](assets/nmac_android_4.png)
