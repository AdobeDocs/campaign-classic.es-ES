---
product: campaign
title: Introducción a la mensajería transaccional
description: Obtenga más información sobre el principio operativo y los pasos clave de la mensajería transaccional de Adobe Campaign Classic
feature: Transactional Messaging, Message Center
exl-id: dc52e789-d0bf-4e8f-b448-9d69a2762cc1
TQID: 'https://experienceleague.adobe.com/n4w2hZkuzHlD3Axc1tUCGfBQ13D28j3Xpmdh07tVr4g'
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
    internal-label: Campaign
  - id: fd6e6e36-54e4-4f1a-96fc-1a750e400d50
    internal-label: Campaign Classic v7
feature_v2:
  - id: a4671286-a59f-47e3-b97b-90627a1977d5
    internal-label: Communication channels
  - id: 6d358f27-4f3c-5ddf-9159-05192e672ba7
    internal-label: Message Center
subfeature_v2:
  - id: d3b34fea-a110-482f-adb2-aae8d686bac8
    internal-label: Transactional messaging
source-git-commit: 617db6f51887118c965b8938b2b9f14335293875
workflow-type: tm+mt
source-wordcount: '606'
ht-degree: 67%
---
# Introducción a la mensajería transaccional {#about-transactional-messaging}



## Información general {#overview}

La **mensajería transaccional** (Centro de mensajería) es un módulo de Campaign diseñado para administrar las notificaciones de activador personalizadas generadas a partir de eventos enviados por un sistema de información externo.

Como parte de la transición de Campaign v7 a v8, el conjunto de documentación de Campaign Classic se ha optimizado y reorganizado. Ahora, las funciones comunes solo están disponibles en el conjunto de documentación de Campaign v8. Para obtener más información sobre la mensajería transaccional, consulte la [documentación de Campaign v8](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/send/real-time/transactional){target=_blank}.

[![imagen](../../assets/do-not-localize/learn-more-button.svg)](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/send/real-time/transactional){target=_blank}

Esta sección cubre la arquitectura de mensajería transaccional y la configuración de las instancias de control y ejecución, específicas para implementaciones locales e híbridas.

>[!IMPORTANT]
>
>La mensajería transaccional requiere una licencia específica. Compruebe el acuerdo de licencia.

<!--Before starting with transactional messaging, make sure you read the corresponding [best practices and limitations]().-->

## Principio operativo de mensajería transaccional {#transactional-messaging-operating-principle}

El módulo de Mensajería transaccional de Adobe Campaign está integrado en un sistema de información que devuelve eventos que se deben modificar en mensajes transaccionales personalizados. Estos mensajes se pueden enviar por separado o en serie por correo electrónico, SMS o notificaciones push.

Esta funcionalidad se basa en una arquitectura específica, donde la **instancia de ejecución** está separada de la **instancia de control**. Esta distribución garantiza una mayor disponibilidad y una mejor administración de la carga. Para obtener más información, consulte [Arquitectura de mensajería transaccional](../../message-center/using/transactional-messaging-architecture.md).

>[!NOTE]
>
>Para crear nuevos usuarios para las instancias de ejecución del Centro de mensajería alojadas en Adobe Cloud, debe ponerse en contacto con el [Servicio de atención al cliente de Adobe](https://helpx.adobe.com/es/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html). Los usuarios del Centro de mensajería son operadores específicos que requieren permisos especiales para acceder a las carpetas **[!UICONTROL Real time events (nmsRtEvent)]**.

>[!NOTE]
>
>Adobe Campaign prioriza el procesamiento de los mensajes transaccionales sobre cualquier otra entrega.

## Pasos clave {#key-steps}

A continuación se resumen los pasos principales para crear y administrar mensajes transaccionales personalizados en Adobe Campaign.

### Pasos que se deben seguir en la instancia de control

En la **instancia de control**, debe realizar las siguientes acciones:

1. [Crear un tipo de evento](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/send/real-time/transactional){target="_blank"} (documentación de Campaign v8).
1. [Cree y diseñe la plantilla de mensaje](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/send/real-time/transactional-template){target="_blank"} (documentación de Campaign v8). Debe vincular un evento al mensaje durante este paso.
1. [Pruebe el mensaje](../../message-center/using/testing-message-templates.md).
1. [Publicar la plantilla de mensaje](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/send/real-time/transactional-template){target="_blank"} (documentación de Campaign v8).

>[!NOTE]
>
>Todos los pasos anteriores se realizan en la **instancia de control**. La publicación de la plantilla en la instancia de control también la publicará en todas las **instancias de ejecución**. Para obtener más información sobre las instancias de mensajería transaccional, consulte [Arquitectura de mensajería transaccional](../../message-center/using/transactional-messaging-architecture.md).

### Procesamiento de eventos en la instancia de ejecución

Una vez que haya diseñado y publicado la plantilla de mensaje transaccional, si se activa un evento correspondiente, los pasos principales a continuación se realizan en la **instancia de ejecución**:

1. Cuando el sistema de información externa genera el evento, los datos relevantes se envían a Campaign mediante los métodos **PushEvent** y **PushEvents**. Consulte [Recopilación de eventos](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/send/real-time/event/event-processing#event-collection){target="_blank"} (documentación de Campaign v8).
1. El evento está vinculado a la plantilla de mensaje adecuada. Ver [Enrutamiento hacia una plantilla](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/send/real-time/event/event-processing#event-to-template){target="_blank"} (documentación de Campaign v8).
1. Una vez finalizada la fase de enriquecimiento, se realiza la entrega. Consulte [Ejecución de entrega](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/send/real-time/event/delivery-execution){target="_blank"} (documentación de Campaign v8). Cada destinatario objetivo recibe un mensaje personalizado.

## Temas relacionados {#related-topics}

* [Introducción a los canales de comunicación](../../delivery/using/communication-channels.md)
* [Pasos clave para la creación de envíos](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/create-message.html?lang=es){target="_blank"}
* [Arquitectura de la mensajería transaccional](../../message-center/using/transactional-messaging-architecture.md)
* [Informes de mensajería transaccional de acceso](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/send/real-time/event/delivery-execution){target="_blank"} (documentación de Campaign v8)
