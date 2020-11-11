---
title: 'Configuración de la aplicación móvil en Adobe Campaign '
description: Obtenga información sobre cómo iniciar la configuración de la aplicación móvil
page-status-flag: never-activated
uuid: aff1a4a0-34e7-4ce0-9eb3-30a8de1380f2
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: delivery
content-type: reference
topic-tags: sending-push-notifications
discoiquuid: 7b5a1ad6-da5a-4cbd-be51-984c07c8d0b3
translation-type: ht
source-git-commit: fd75f7f75e8e77d7228233ea311dd922d100417c
workflow-type: ht
source-wordcount: '252'
ht-degree: 100%

---


# Introducción a la configuración de la aplicación

En esta sección puede encontrar debajo un ejemplo de configuración basado en una compañía que vende paquetes para las fiestas en línea. Su aplicación móvil (Neotrips) está disponible para sus clientes en dos versiones: Neotrips para Android y Neotrips para iOS.

Para enviar notificaciones push en Adobe Campaign, debe:

* Cree un servicio de información de tipo **[!UICONTROL Mobile application]** para la aplicación móvil Neotrips. Consulte [esta sección para iOS](../../delivery/using/configuring-the-mobile-application.md#configuring-ios-service). Y [esta sección para Android](../../delivery/using/configuring-the-mobile-application-android.md#configuring-android-service).
* Añada a este servicio las versiones de iOS y Android de la aplicación.
* Cree un envío tanto para iOS como para Android. [Consulte esta página](../../delivery/using/creating-notifications.md).

![](assets/nmac_service_diagram.png)

>[!NOTE]
>
>Vaya a la pestaña **[!UICONTROL Subscriptions]** para ver la lista de suscriptores del servicio, es decir, todas las personas que hayan instalado la aplicación en su móvil y hayan aceptado recibir notificaciones.

## Instalación del paquete {#installing-package-ios}

Como cliente híbrido/alojado, póngase en contacto con el equipo de atención al cliente de Adobe para acceder al canal de notificaciones push en Campaign.

Como cliente On-Premise, debe realizar los siguientes pasos de instalación:

1.  En la consola de cliente de Adobe Campaign, acceda al asistente de importación del paquete desde **[!UICONTROL Tools > Advanced > Package import...]**.

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

* [Pasos de configuración para iOS](../../delivery/using/configuring-the-mobile-application.md)

* [Pasos de configuración para Android](../../delivery/using/configuring-the-mobile-application-android.md)
