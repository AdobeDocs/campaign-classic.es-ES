---
product: campaign
title: Introducción al canal de aplicaciones móviles
description: Introducción al canal de aplicaciones móviles en Adobe Campaign
feature: Push
role: User
exl-id: c3b0406f-f652-42f4-ad0d-23fb719cd1b6
source-git-commit: ad6f3f2cf242d28de9e6da5cec100e096c5cbec2
workflow-type: tm+mt
source-wordcount: '572'
ht-degree: 37%

---

# Introducción al canal de aplicaciones móviles{#about-mobile-app-channel}

Con Adobe Campaign, puede crear envíos de notificaciones push para enviar mensajes personalizados a los usuarios de su aplicación móvil.

Las notificaciones push le permiten atraer a usuarios en iOS y Android en tiempo real. Ya sea que envíe actualizaciones, anuncios o promociones, puede controlar el contenido, el tiempo y el objetivo. Aprenda a configurar y utilizar el canal push, administrar suscripciones, integrar con APNS y FCM y personalizar mensajes en [documentación de Adobe Campaign v8](https://experienceleague.adobe.com/es/docs/campaign/campaign-v8/send/emails/email){target=_blank}.

Como parte de la transición de Campaign v7 a v8, el conjunto de documentación de Campaign Classic se ha optimizado y reorganizado. Las funciones comunes ahora están disponibles exclusivamente en el conjunto de documentación de Campaign v8.

>[!BEGINTABS]

>[!TAB Documentación del canal push]

Para obtener más información sobre el canal de notificaciones push, consulte la [documentación de Campaign v8](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/push/push.html){target=_blank}.

[![imagen](../../assets/do-not-localize/learn-more-button.svg)](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/push/push.html){target=_blank}


>[!TAB Creación de envíos push]

Conozca los pasos clave relacionados con la creación de envíos push **en la documentación de Campaign v8**:

* [Crear una notificación push](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/push/push.html#push-create){target="_blank"}: Obtenga información acerca de los diferentes pasos necesarios para crear una entrega push.
* [Envíe y supervise la notificación push](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/push/push.html#push-test){target="_blank"}: Obtenga información sobre cómo validar, enviar y rastrear sus envíos.
* [Diseñe una entrega de notificaciones push enriquecidas de Android](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/push/rich-push/rich-push-android.html){target="_blank"}: Aprenda a crear y configurar notificaciones push enriquecidas para dispositivos Android.
* [Diseñe una entrega push enriquecida de iOS](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/push/rich-push/rich-push-ios.html){target="_blank"}: Aprenda a diseñar y configurar notificaciones push enriquecidas para dispositivos iOS en Adobe Campaign v8.


>[!TAB Parámetros push]

Consulte estas páginas para obtener más información sobre los parámetros push **en la documentación de Campaign v8**:

* [Requisitos previos de configuración](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/push/push-settings.html#before-starting){target="_blank"}: Aprenda a configurar permisos y a configurar su aplicación.
* [Configurar la propiedad de Launch](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/push/push-settings.html#launch-property){target="_blank"}: Obtenga información sobre cómo configurar una propiedad de etiquetas móviles en la recopilación de datos de Adobe Experience Platform para habilitar las notificaciones push.
* [Configurar servicios push en Mobile Services](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/push/push-settings.html#push-service){target="_blank"}: configure los servicios push de iOS y Android en Adobe para habilitar las notificaciones push dirigidas a los usuarios de su aplicación móvil.
* [Configure la extensión en su propiedad móvil](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/push/push-settings.html#configure-extension){target="_blank"}: Integre la extensión de Campaign en su propiedad móvil para habilitar las notificaciones push y administrar las interacciones del usuario de forma eficaz.

>[!ENDTABS]


La siguiente información es específica de Campaign Classic.

+++ **Instalación de paquetes**

![](assets/do-not-localize/how-to-video.png) [Obtenga información sobre cómo instalar el paquete de la aplicación móvil con este vídeo](https://experienceleague.adobe.com/docs/campaign-classic-learn/tutorials/sending-messages/push-channel/installing-the-mobile-app-channel.html?lang=es#sending-messages)

Como cliente híbrido/alojado, póngase en contacto con el equipo del [Servicio de atención al cliente de Adobe](https://helpx.adobe.com/es/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html) para acceder al canal de notificaciones push en Campaign.

Como cliente on-premise, debe instalar un paquete integrado.

>[!CAUTION]
>
>Obtenga más información acerca de los paquetes integrados de Campaign, las prácticas recomendadas y las recomendaciones en [esta página](../../installation/using/installing-campaign-standard-packages.md).

Los pasos de instalación son estos:

1. En la consola del cliente de Adobe Campaign, acceda al asistente de importación de paquetes desde **[!UICONTROL Tools > Advanced > Import package]**.

   ![](assets/package_ios.png)

1. Seleccione **[!UICONTROL Install a standard package]**.

1. En la lista que aparece, marque **[!UICONTROL Mobile App Channel]**.

   ![](assets/package_ios_2.png)

1. Haga clic en **[!UICONTROL Next]**, luego en **[!UICONTROL Start]** para iniciar la instalación del paquete.

   Una vez instalados los paquetes, la barra de progreso muestra el **100 %** y puede ver el siguiente mensaje en los registros de instalación: **[!UICONTROL Installation of packages successful]**.

   ![](assets/package_ios_3.png)

1. **[!UICONTROL Close]** la ventana de instalación.

Una vez completado este paso, puede configurar las aplicaciones de Android y iOS. Consulte la [documentación](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/push/push.html){target="_blank"} de Campaign v8.

+++

+++ **Resolución de problemas**

Si su dispositivo móvil está conectado a una red wifi y no recibe las notificaciones, compruebe que el firewall no haya bloqueado los puertos FCM/APN.

**Android**: El dispositivo móvil se conecta a los servidores FCM en los puertos 5228 a 5230. Por lo tanto, se debe configurar el cortafuegos para que autorice la conexión con FCM. Los puertos que se van a abrir son: 5228 (el más utilizado), 5229 y 5230.

**iOS**:

Conector HTTP/2: se debe permitir la comunicación con los siguientes servidores:

* api.push.apple.com: puerto 443
* api.development.push.apple.com: puerto 443

>[!NOTE]
>
>Para obtener más información sobre los dos conectores, consulte la [documentación](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/push/push-settings.html){target="_blank"} de Campaign v8.

+++
