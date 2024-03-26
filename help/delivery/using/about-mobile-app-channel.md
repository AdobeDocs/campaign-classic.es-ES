---
product: campaign
title: Introducción al canal de aplicaciones móviles
description: Introducción al canal de aplicaciones móviles en Adobe Campaign
badge-v7: label="v7" type="Informative" tooltip="Se aplica a Campaign Classic v7"
badge-v8: label="v8" type="Positive" tooltip="También se aplica a Campaign v8"
feature: Push
role: User
exl-id: c3b0406f-f652-42f4-ad0d-23fb719cd1b6
source-git-commit: 92c79e7050124bc707f4d6b87c7952016586002c
workflow-type: tm+mt
source-wordcount: '684'
ht-degree: 100%

---

# Introducción al canal de aplicaciones móviles{#about-mobile-app-channel}

El **canal de aplicaciones móviles** permite utilizar la plataforma de Adobe Campaign para enviar notificaciones personalizadas a los terminales iOS y Android a través de aplicaciones.

Hay dos canales de envío disponibles:

* Un canal de iOS que le permite enviar notificaciones a dispositivos móviles de Apple.

  ![](assets/nmac_intro_2.png)

* Un canal de Android que le permite enviar mensajes de datos a dispositivos móviles Android.

  ![](assets/nmac_intro_1.png)

  >[!IMPORTANT]
  >
  >Algunos cambios importantes en el servicio Android Firebase Cloud Messaging (FCM) se lanzarán en 2024 y pueden afectar a la implementación de Adobe Campaign. Es posible que sea necesario actualizar la configuración de los servicios de suscripción para los mensajes push de Android a fin de que admitan este cambio. Ya puede comprobar y realizar acciones. Obtenga más información en esta [nota técnica de Adobe Campaign versión 8](https://experienceleague.adobe.com/docs/campaign/technotes-ac/tn-new/push-technote.html?lang=es){target="_blank"}.

En relación con esos dos canales hay dos actividades de envío en los flujos de trabajo de la campaña. Dos plantillas de mensajes transaccionales también están disponibles para la mensajería transaccional.

![](assets/nmac_intro_3.png)


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
