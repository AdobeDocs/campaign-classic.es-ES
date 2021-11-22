---
product: campaign
title: Acerca del canal de aplicaciones móviles en Adobe Campaign Classic
description: Esta sección proporciona información general específica del canal de aplicaciones móviles en Adobe Campaign Classic.
audience: delivery
content-type: reference
topic-tags: sending-push-notifications
exl-id: c3b0406f-f652-42f4-ad0d-23fb719cd1b6
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '673'
ht-degree: 100%

---

# Introducción al canal de aplicaciones móviles{#about-mobile-app-channel}

![](../../assets/common.svg)

El **canal de aplicaciones móviles** permite utilizar la plataforma de Adobe Campaign para enviar notificaciones personalizadas a los terminales iOS y Android a través de aplicaciones.

>[!CAUTION]
>
>Este documento detalla el proceso para integrar su aplicación móvil con la plataforma Adobe Campaign. No proporciona información sobre cómo crear la aplicación móvil o cómo configurarla para gestionar notificaciones. Si desea obtener más información, consulte la [documentación](https://developer.apple.com/) oficial de Apple y la [documentación](https://developer.android.com/index.html) de Android.

Hay dos canales de envío disponibles:

* Un canal de iOS que le permite enviar notificaciones a dispositivos móviles de Apple.

   ![](assets/nmac_intro_2.png)

* Un canal de Android que le permite enviar mensajes de datos a dispositivos móviles Android.

   ![](assets/nmac_intro_1.png)

En relación con esos dos canales hay dos actividades de envío en los flujos de trabajo de campaña:

![](assets/nmac_intro_3.png)


>[!NOTE]
>
>Dos plantillas de mensajes transaccionales también están disponibles para la mensajería transaccional.

Puede definir el comportamiento de la aplicación para las situaciones en las que el usuario activa la notificación para mostrar la pantalla correspondiente al contexto de la aplicación. Por ejemplo:

* Se envía una notificación al cliente para informar que el paquete ha salido del almacén. Al activar la notificación, se abre una página con información sobre la entrega.
* El usuario ha añadido elementos al carro de la compra, pero ha salido de la aplicación sin finalizar la compra. Se envía una notificación que informa de que ha abandonado el carro de la compra. Cuando se activa la notificación, el elemento se muestra en la pantalla.

>[!CAUTION]
>
>* Asegúrese de que las notificaciones enviadas a una aplicación móvil cumplan los requisitos previos y las condiciones especificadas por Apple (Servicio de notificaciones push de Apple) y Google (Firebase mensajería en la nube).
>* Advertencia: en algunos países, la ley requiere informar a los usuarios de las aplicaciones del tipo de datos que se recopilan y del propósito de su procesamiento. Debe comprobar la ley.


El flujo de trabajo de **[!UICONTROL NMAC opt-out management]** (mobileAppOptOutMgt) actualiza la notificación de las bajas de suscripción en dispositivos móviles. Para obtener más información sobre este flujo de trabajo, consulte la [lista de flujos de trabajo técnicos](../../workflow/using/about-technical-workflows.md).

Adobe Campaign es compatible con APN HTTP/2. Para obtener más información sobre los pasos de configuración, consulte [esta sección](configuring-the-mobile-application.md).

Para obtener más información sobre la creación de entregas, consulte [esta sección](steps-about-delivery-creation-steps.md).

## Ruta de datos {#data-path}

Los siguientes esquemas detallan los pasos que permiten a una aplicación móvil intercambiar datos con Adobe Campaign. Este proceso consta de tres entidades:

* la aplicación móvil
* El servicio de notificaciones: APNS (servicio de notificaciones push de Apple) para Apple y FCM (Firebase Cloud Messaging) para Android.
* Adobe Campaign

Los tres pasos principales del proceso de notificación son: registro de la aplicación en Adobe Campaign (recopilación de suscripciones), envíos y seguimiento.

### Paso 1: Colección de suscripciones {#step-1--subscription-collection}

El usuario descarga la aplicación móvil desde la App Store o desde Google Play. Esta aplicación contiene la configuración de conexión (certificado de iOS y clave de proyecto para Android) y la clave de integración. La primera vez que se abre la aplicación (según la configuración), se puede pedir al usuario que introduzca la información de registro (@userKey: correo electrónico o número de cuenta). Al mismo tiempo, la aplicación pregunta al servicio de notificaciones para recopilar una ID de notificación (ID de push). Toda esta información (configuración de conexión, clave de integración, identificador de notificación, userKey) se envía a Adobe Campaign.

![](assets/nmac_register_view.png)

### Paso 2: Entrega {#step-2--delivery}

Los especialistas en marketing se dirigen a los suscriptores de la aplicación. El proceso de envío envía la configuración de conexión al servicio de notificaciones (certificado de iOS y clave de proyecto para Android), el ID de notificación (ID de push) y el contenido de la notificación. El servicio de notificaciones envía notificaciones a los terminales de destino.

La siguiente información está disponible en Adobe Campaign:

* Solo Android: número de dispositivos que muestran la notificación (impresiones)
* Android y iOS: número de clics en la notificación

![](assets/nmac_delivery_view.png)

El servidor de Adobe Campaign debe poder ponerse en contacto con el servidor APN en el puerto 443 del conector HTTP/2 de iOS.

Para comprobar si funciona correctamente, utilice los siguientes comandos:

* Para pruebas:

   ```
   api.development.push.apple.com:443
   ```

* En producción:

   ```
   api.push.apple.com:443
   ```

Si se utiliza un conector HTTP/2 de iOS, el servidor de correo y el servidor web deben poder comunicarse con los APN en el puerto 443.

Si necesita utilizar el conector HTTP/2 de iOS a través de un proxy, consulte esta [página](../../installation/using/file-res-management.md#proxy-connection-configuration).
