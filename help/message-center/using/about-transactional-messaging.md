---
solution: Campaign Classic
product: campaign
title: Introducción a la mensajería transaccional
description: 'Obtenga más información sobre el principio operativo y los pasos clave de la mensajería transaccional de Adobe Campaign Classic. '
audience: message-center
content-type: reference
topic-tags: introduction
exl-id: dc52e789-d0bf-4e8f-b448-9d69a2762cc1
source-git-commit: d39b15b0efc6cbd6ab24e074713be6f8fc90e5fc
workflow-type: tm+mt
source-wordcount: '644'
ht-degree: 13%

---


# Introducción a la mensajería transaccional {#about-transactional-messaging}

## Información general {#overview}

**La mensajería transaccional**  (Centro de mensajes) es un módulo de Campaign diseñado para administrar las notificaciones de déclencheur personalizadas generadas a partir de eventos enviados por un sistema de información externo.

Un mensaje transaccional es una comunicación individual y única que un proveedor, como un sitio web, envía en tiempo real. Se espera especialmente, ya que contiene información importante que el destinatario desea comprobar o confirmar.

Las capacidades de mensajería transaccional están diseñadas para admitir la escalabilidad y proporcionar un servicio las 24 horas del día, los 7 días de la semana.

* **¿Cuándo es debido?** Dado que este mensaje contiene información importante, el usuario espera que se envíe en tiempo real. Por lo tanto, el retraso entre el evento que se está activando y el mensaje que llega tiene que ser muy corto.

* **¿Por qué es importante?** Generalmente, un mensaje transaccional tiene altas tasas de apertura. Por lo tanto, debe diseñarse cuidadosamente, ya que puede tener un fuerte impacto en el comportamiento de los clientes, ya que define la relación con ellos.

* **Por ejemplo?** Podría ser un mensaje de bienvenida después de crear una cuenta, una confirmación de envío de un pedido, una factura, un mensaje que confirme un cambio de contraseña, una notificación después de que un cliente navegue por su sitio web, una comunicación de no disponibilidad del producto, un extracto de cuenta, etc.

>[!IMPORTANT]
>
>La mensajería transaccional requiere una licencia específica. Compruebe el acuerdo de licencia.

<!--Before starting with transactional messaging, make sure you read the corresponding [best practices and limitations]().-->

## Principio operativo de mensajería transaccional {#transactional-messaging-operating-principle}

El módulo de mensajería transaccional de Adobe Campaign se integra en un sistema de información que devuelve eventos que se deben cambiar a mensajes transaccionales personalizados. Estos mensajes se pueden enviar por separado o en serie por correo electrónico, SMS o notificaciones push.

Esta función se basa en una arquitectura específica, donde la **instancia de ejecución** está separada de la **instancia de control**. Esta distribución garantiza una mayor disponibilidad y una mejor administración de la carga. Para obtener más información, consulte [Instancias de mensajería transaccional](../../message-center/using/transactional-messaging-architecture.md).

>[!NOTE]
>
>Para crear nuevos usuarios para las instancias de ejecución del Centro de mensajes alojadas en Adobe Cloud, debe ponerse en contacto con el [Servicio de atención al cliente de Adobe](https://helpx.adobe.com/es/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html). Los usuarios del Centro de mensajes son operadores específicos que requieren permisos específicos para acceder a las carpetas **[!UICONTROL Real time events (nmsRtEvent)]**.

El proceso general de mensajería transaccional se puede describir de la siguiente manera:

![](assets/transactional-msg-overview.png)

Por ejemplo, imaginemos que es una empresa con un sitio web en el que los clientes pueden comprar productos.

Adobe Campaign le permite enviar un correo electrónico de notificación a los clientes que han añadido productos al carro de compras. Cuando uno de ellos abandona el sitio web sin pasar por sus compras (evento externo que déclencheur un evento de Campaign), se les envía automáticamente un correo electrónico de abandono del carro de compras (envío de mensaje transaccional).

Los pasos principales para ponerlo en práctica se detallan a continuación en [esta sección](#key-steps).

>[!NOTE]
>
>Adobe Campaign prioriza el procesamiento de mensajes transaccionales sobre cualquier otro envío.

## Pasos clave {#key-steps}

A continuación se resumen los pasos principales para crear y administrar mensajes transaccionales personalizados en Adobe Campaign.

### Pasos que se deben seguir en la instancia de control

En la **instancia de control**, debe realizar las siguientes acciones:

1. [Cree un tipo de evento](../../message-center/using/creating-event-types.md).
1. [Cree y diseñe la plantilla](../../message-center/using/creating-the-message-template.md) de mensaje. Debe vincular un evento al mensaje durante este paso.
1. [Pruebe el mensaje](../../message-center/using/testing-message-templates.md).
1. [Publique la plantilla de mensaje](../../message-center/using/publishing-message-templates.md).

>[!NOTE]
>
>Todos los pasos anteriores se realizan en la **instancia de control**. La publicación de la plantilla en la instancia de control también la publicará en todas las **instancias de ejecución**. Para obtener más información sobre las instancias de mensajería transaccional, consulte [Arquitectura de mensajería transaccional](../../message-center/using/transactional-messaging-architecture.md).

### Procesamiento de eventos en la instancia de ejecución

Una vez que haya diseñado y publicado la plantilla de mensaje transaccional, si se activa un evento correspondiente, los pasos principales a continuación se realizan en la **instancia de ejecución**:

1. Cuando el sistema de información externa genera el evento, los datos relevantes se envían a Campaign mediante los métodos **PushEvent** y **PushEvents**. Consulte [Recopilación de eventos](#event-collection).
1. El evento está vinculado a la plantilla de mensaje adecuada. Consulte [Enrutamiento hacia una plantilla](#routing-towards-a-template).
1. Una vez finalizada la fase de enriquecimiento, se realiza la entrega. Consulte [Ejecución de envío](../../message-center/using/delivery-execution.md). Cada destinatario objetivo recibe un mensaje personalizado.

## Temas relacionados {#related-topics}

* [Introducción a los canales de comunicación](../../delivery/using/communication-channels.md)
* [Pasos clave de creación de entregas](../../delivery/using/steps-about-delivery-creation-steps.md)
* [Arquitectura de la mensajería transaccional](../../message-center/using/transactional-messaging-architecture.md)
* [Acerca de los informes de mensajería transaccional](../../message-center/using/about-transactional-messaging-reports.md)
