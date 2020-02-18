---
title: Acerca del canal de aplicaciones móviles en Adobe Campaign Classic
description: Esta sección proporciona información general específica del canal de aplicaciones móviles en Adobe Campaign Classic.
page-status-flag: never-activated
uuid: e8d26b33-dc7c-4abd-956a-92f419a117e1
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: delivery
content-type: reference
topic-tags: sending-push-notifications
discoiquuid: 6b3fe8b9-dae6-4f8e-83e1-3376c0fe72a5
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 4ac96bf0e54268832b84b17c3cc577af038cc712

---


# Acerca del canal de aplicaciones móviles{#about-mobile-app-channel}

>[!CAUTION]
>
>Este documento detalla el proceso para integrar su aplicación móvil con la plataforma Adobe Campaign. No proporciona información sobre cómo crear la aplicación móvil o cómo configurarla para gestionar notificaciones. If you would like further information on this, refer to the official Apple [documentation](https://developer.apple.com/) and Android [documentation](https://developer.android.com/index.html).

Las secciones a continuación proporcionan información específica sobre el canal de aplicaciones móviles.

For global information on how to create a delivery, refer to [this section](../../delivery/using/steps-about-delivery-creation-steps.md).

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

* Se envía una notificación al cliente para informar que el paquete ha salido del almacén. Al activar la notificación, se abre una página con información sobre el envío.
* El usuario ha añadido elementos al carro de la compra, pero ha salido de la aplicación sin finalizar la compra. Se envía una notificación que informa de que ha abandonado el carro de la compra. Cuando se activa la notificación, el elemento se muestra en la pantalla.

>[!CAUTION]
>
>* Debe asegurarse de que las notificaciones enviadas a una aplicación móvil cumplen los requisitos y condiciones especificados por Apple (servicio de notificaciones push de Apple) y Google (mensajería en la nube de Firebase).
>* Advertencia: en algunos países, la ley requiere informar a los usuarios de las aplicaciones del tipo de datos que se recopilan y del propósito de su procesamiento. Debe comprobar la ley.


The **[!UICONTROL NMAC opt-out management]** (mobileAppOptOutMgt) workflow updates notification unsubscriptions on mobile devices. Para obtener más información sobre este flujo de trabajo, consulte la [guía sobre flujos de trabajo](../../workflow/using/mobile-app-channel.md).

Adobe Campaign es compatible con APNS tanto de tipo binario como HTTP/2. Para obtener más información sobre los pasos de configuración, consulte la sección [Configuración de una aplicación móvil en Adobe Campaign](../../delivery/using/configuring-the-mobile-application.md) .

## Ruta de datos {#data-path}

Los siguientes esquemas detallan los pasos que permiten a una aplicación móvil intercambiar datos con Adobe Campaign. Este proceso consta de tres entidades:

* la aplicación móvil
* el servicio de notificación: APNS (Servicio de notificaciones push de Apple) para Apple y FCM (Firebase Cloud Messaging) para Android
* Espacio de trabajo de Adobe Campaign

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

El servidor de Adobe Campaign debe poder comunicarse con el servidor APNS en los puertos siguientes:

* 2195 (envío) y 2186 (servicio de comentarios) para el conector binario de iOS
* 443 para el conector HTTP/2 de iOS

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

