---
product: campaign
title: Configuración de la aplicación móvil en Adobe Campaign
description: Obtenga información sobre cómo iniciar la configuración de la aplicación móvil
feature: Push
exl-id: 95bc07cc-8837-4511-81bc-05fad28191c9
source-git-commit: 8d635722b8961b3edac9cc98f00f17b86f4ee523
workflow-type: tm+mt
source-wordcount: '290'
ht-degree: 100%

---

# Introducción a la configuración de la aplicación

![](../../assets/v7-only.svg)

En esta sección puede encontrar debajo un ejemplo de configuración basado en una compañía que vende paquetes para las fiestas en línea. Su aplicación móvil (Neotrips) está disponible para sus clientes en dos versiones: Neotrips para Android y Neotrips para iOS.

Para enviar notificaciones push en Adobe Campaign, debe:

* Cree un servicio de información de tipo **[!UICONTROL Mobile application]** para la aplicación móvil Neotrips. Consulte [esta sección para iOS](configuring-the-mobile-application.md#configuring-ios-service). Y [esta sección para Android](configuring-the-mobile-application-android.md#configuring-android-service).
* Añada a este servicio las versiones de iOS y Android de la aplicación.
* Cree una entrega para [iOS](create-notifications-ios.md) y [Android](create-notifications-android.md).

![](assets/nmac_service_diagram.png)

>[!NOTE]
>
>Vaya a la pestaña **[!UICONTROL Subscriptions]** para ver la lista de suscriptores del servicio, es decir, todas las personas que hayan instalado la aplicación en su móvil y hayan aceptado recibir notificaciones.

## Instalación del paquete {#installing-package-ios}

![](assets/do-not-localize/how-to-video.png) [Obtenga información sobre cómo instalar el paquete de la aplicación móvil con este vídeo](https://experienceleague.adobe.com/docs/campaign-classic-learn/tutorials/sending-messages/push-channel/installing-the-mobile-app-channel.html?lang=es#sending-messages)

Como cliente híbrido/alojado, póngase en contacto con el equipo del [Servicio de atención al cliente de Adobe](https://helpx.adobe.com/es/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html) para acceder al canal de notificaciones push en Campaign.

Como cliente on-premise, debe instalar un paquete integrado.

>[!CAUTION]
>
>Obtenga más información acerca de los paquetes integrados de Campaign, las prácticas recomendadas y las recomendaciones en [esta página](../../installation/using/installing-campaign-standard-packages.md).

Los pasos de instalación son estos:

1.  En la consola de cliente de Adobe Campaign, acceda al asistente de importación del paquete desde **[!UICONTROL Tools > Advanced > Import package]**.

   ![](assets/package_ios.png)

1. Seleccione **[!UICONTROL Install a standard package]**.

1. En la lista que aparece, marque **[!UICONTROL Mobile App Channel]**.

   ![](assets/package_ios_2.png)

1. Haga clic en **[!UICONTROL Next]**, luego en **[!UICONTROL Start]** para iniciar la instalación del paquete.

   Una vez instalados los paquetes, la barra de progreso muestra el **100 %** y puede ver el siguiente mensaje en los registros de instalación: **[!UICONTROL Installation of packages successful]**.

   ![](assets/package_ios_3.png)

1. **[!UICONTROL Close]** la ventana de instalación.

Una vez completado este paso, puede configurar sus aplicaciones de Android e iOS.
Consulte estas secciones:

* [Pasos de configuración para iOS](configuring-the-mobile-application.md)

* [Pasos de configuración para Android](configuring-the-mobile-application-android.md)
