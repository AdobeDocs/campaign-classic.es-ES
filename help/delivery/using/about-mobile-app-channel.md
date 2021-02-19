---
solution: Campaign Classic
product: campaign
title: Acerca del canal de aplicaciones móviles en Adobe Campaign Classic
description: Esta sección proporciona información general específica del canal de aplicaciones móviles en Adobe Campaign Classic.
audience: delivery
content-type: reference
topic-tags: sending-push-notifications
translation-type: tm+mt
source-git-commit: a9d58e25ab17baaabf4ff8c109b53e83c7d93218
workflow-type: tm+mt
source-wordcount: '755'
ht-degree: 100%

---


# Acerca del canal de aplicaciones móviles{#about-mobile-app-channel}

>[!CAUTION]
>
>Este documento detalla el proceso para integrar su aplicación móvil con la plataforma Adobe Campaign. No proporciona información sobre cómo crear la aplicación móvil o cómo configurarla para gestionar notificaciones. Si desea obtener más información, consulte la [documentación](https://developer.apple.com/) oficial de Apple y la [documentación](https://developer.android.com/index.html) de Android.

Las secciones a continuación proporcionan información específica sobre el canal de aplicaciones móviles.

Para obtener más información sobre la creación de entregas, consulte [esta sección](../../delivery/using/steps-about-delivery-creation-steps.md).

El **Mobile App Channel** permite utilizar la plataforma de Adobe Campaign para enviar notificaciones personalizadas a los terminales iOS y Android a través de aplicaciones. Hay dos canales de envío disponibles:

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

Adobe Campaign es compatible con APNS tanto de tipo binario como HTTP/2. Para obtener más información sobre los pasos de configuración, consulte la sección [Configuración de una aplicación móvil en Adobe Campaign](../../delivery/using/configuring-the-mobile-application.md) .

## Ruta de datos {#data-path}

Los siguientes esquemas detallan los pasos que permiten a una aplicación móvil intercambiar datos con Adobe Campaign. Este proceso consta de tres entidades:

* la aplicación móvil
* El servicio de notificaciones: APNS (servicio de notificaciones push de Apple) para Apple y FCM (Firebase Cloud Messaging) para Android.
* Adobe Campaign

Los tres pasos principales del proceso de notificación son: registro de la aplicación en Adobe Campaign (recopilación de suscripciones), envíos y seguimiento.

### Paso 1: Colección de suscripciones {#step-1--subscription-collection}

El usuario descarga la aplicación móvil desde la App Store o desde Google Play. Esta aplicación contiene la configuración de conexión (certificado de iOS y clave de proyecto para Android) y la clave de integración. La primera vez que se abre la aplicación (según la configuración), se puede pedir al usuario que introduzca la información de registro (@userKey: correo electrónico o número de cuenta). Al mismo tiempo, la aplicación pregunta al servicio de notificaciones para recopilar una ID de notificación (ID de push). Toda esta información (configuración de conexión, clave de integración, identificador de notificación, userKey) se envía a Adobe Campaign.

![](assets/nmac_register_view.png)

### Paso 2: Envío{#step-2--delivery}

Los especialistas en marketing se dirigen a los suscriptores de la aplicación. El proceso de envío envía la configuración de conexión al servicio de notificaciones (certificado de iOS y clave de proyecto para Android), el ID de notificación (ID de push) y el contenido de la notificación. El servicio de notificaciones envía notificaciones a los terminales de destino.

La siguiente información está disponible en Adobe Campaign:

* Solo Android: número de dispositivos que muestran la notificación (impresiones)
* Android y iOS: número de clics en la notificación

![](assets/nmac_delivery_view.png)

El servidor de Adobe Campaign debe poder comunicarse con el servidor APNS en los puertos siguientes:

* 2195 (envío) y 2186 (servicio de comentarios) para el conector binario de iOS
* 443 para el conector HTTP/2 de iOS

   >[!NOTE]
   >
   > A partir de la versión 20.3 de Campaign, el conector binario heredado de iOS está en desuso. Si utiliza este conector, debe adaptar la implementación en consecuencia. [Más información](https://helpx.adobe.com/es/campaign/kb/migrate-to-apns-http2.html)

Para comprobar si funciona correctamente, utilice los siguientes comandos:

* Para pruebas:

   ```
   telnet gateway.sandbox.push.apple.com
   ```

* En producción:

   ```
   telnet gateway.push.apple.com
   ```

Si se utiliza un conector binario de iOS, el MTA y el servidor web deben poder comunicarse con el APNS en el puerto 2195 (envío) y el servidor de flujo de trabajo debe poder comunicarse con el APNS en el puerto 2196 (servicio de comentarios).

Si se utiliza un conector HTTP/2 de iOS, el MTA, el servidor de flujo de trabajo y el servidor web deben poder comunicarse con el APNS en el puerto 443.

