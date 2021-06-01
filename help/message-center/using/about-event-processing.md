---
product: campaign
title: Procesamiento de eventos
description: Descubra cómo se procesan los eventos de mensajería transaccional en Adobe Campaign Classic.
audience: message-center
content-type: reference
topic-tags: event-processing
exl-id: 3d85866a-6339-458c-807a-b267cce772b8
source-git-commit: e86350cf12db37e3f2c227563057b97922601729
workflow-type: tm+mt
source-wordcount: '691'
ht-degree: 46%

---

# Procesamiento de eventos {#about-event-processing}

En el contexto de los mensajes transaccionales, un evento se genera mediante un sistema de información externo y se envía a Adobe Campaign mediante los métodos **[!UICONTROL PushEvent]** y **[!UICONTROL PushEvents]** (consulte [Descripción del evento](../../message-center/using/event-description.md)).

Este evento contiene datos vinculados al evento, como su [tipo](../../message-center/using/creating-event-types.md) (confirmación de pedido, creación de cuenta en un sitio web, etc.), dirección de correo electrónico o número de móvil, así como otra información que permite enriquecer y personalizar el mensaje transaccional antes del envío (información de contacto del cliente, idioma del mensaje, formato de correo electrónico, etc.).

Ejemplo de datos de eventos:

![](assets/messagecenter_events_request_001.png)

## Pasos del procesamiento de eventos {#event-processing}

Para procesar los eventos de mensajería transaccional, se aplican los siguientes pasos a las instancias de ejecución:

1. [Colección de eventos](#event-collection)
1. [Transferencia de eventos a una plantilla de mensajes](#routing-towards-a-template)
1. Enriquecimiento de eventos con datos de personalización
1. [Ejecución de entrega](../../message-center/using/delivery-execution.md)
1. [Reciclaje de ](#event-recycling) eventos cuyo envío vinculado ha fallado (a través de un flujo de trabajo de Adobe Campaign)

Una vez que todos los pasos anteriores se llevan a cabo mediante la instancia de ejecución, cada destinatario objetivo recibe un mensaje personalizado.

>[!NOTE]
>
>Para obtener más información sobre las instancias de mensajería transaccional, consulte [Arquitectura de mensajería transaccional](../../message-center/using/transactional-messaging-architecture.md).


## Recopilación de eventos {#event-collection}

Los eventos que genera el sistema de información se pueden recopilar mediante dos modos:

* Las llamadas a métodos SOAP permiten insertar eventos en Adobe Campaign: el método PushEvent permite enviar un evento a la vez, el método PushEvents permite enviar varios eventos a la vez. Para obtener más información, consulte [Descripción del evento](../../message-center/using/event-description.md).

* La creación de un flujo de trabajo permite recuperar eventos mediante la importación de archivos o mediante una puerta de vínculo SQL (con la opción [Acceso de datos federado](../../installation/using/about-fda.md)).

Una vez recopilados, los eventos se desglosan por flujos de trabajo técnicos entre colas en tiempo real y por lotes de las instancias de ejecución, mientras esperan vincularse a una plantilla de mensaje.

![](assets/messagecenter_events_queues_001.png)

>[!NOTE]
>
>En las instancias de ejecución, las carpetas **[!UICONTROL Real time events]** o **[!UICONTROL Batch events]** no deben configurarse como vistas, ya que esto podría provocar problemas con el derecho de acceso. Para obtener más información sobre la configuración de una carpeta como vista, consulte [esta sección](../../platform/using/access-management-folders.md).

## Enrutamiento hacia una plantilla {#routing-towards-a-template}

Una vez que la plantilla de mensaje se publica en las instancias de ejecución, se generan dos plantillas automáticamente: uno que se vinculará a un evento en tiempo real y otro que se vinculará a un evento por lotes.

El paso de enrutamiento consiste en vincular un evento a la plantilla de mensaje adecuada, en función de:

* El tipo de evento especificado en las propiedades del propio evento:

   ![](assets/messagecenter_event_type_001.png)

* El tipo de evento especificado en las propiedades de la plantilla de mensaje:

   ![](assets/messagecenter_event_type_002.png)

De forma predeterminada, el enrutamiento depende de la siguiente información:

* El tipo de evento
* El canal que se va a utilizar (predeterminado: correo electrónico)
* La plantilla de envío más reciente, en función de la fecha de publicación

## Estados de eventos {#event-statuses}

**Event history**, en **[!UICONTROL Message Center]** > **[!UICONTROL Event history]**, agrupa todos los eventos procesados en una sola vista. Pueden clasificarse por tipo de evento o por **estado**. Estos estados son:

* **Pendiente**: El evento puede ser:

   * Un evento que acaba de recopilarse y que aún no se ha procesado. La columna **[!UICONTROL Number of errors]** muestra el valor 0. La plantilla de correo electrónico aún no se ha vinculado.
   * Un evento procesado pero cuya confirmación es errónea. La columna **[!UICONTROL Number of errors]** muestra un valor que no es 0. Para saber cuándo se volverá a procesar este evento, consulte la columna **[!UICONTROL Process requested on]**.

* **Entrega** pendiente: El evento se procesó y la plantilla de envío está vinculada. El correo electrónico está pendiente de envío y se aplica el proceso de envío clásico. Abra la entrega para obtener más información.
* **Enviado**,  **** Ignorado y  **Error** de envío: Estos estados de entrega se recuperan mediante el flujo de trabajo  **** updateEventsStatus . Para obtener más información, se puede abrir la entrega correspondiente.
* **Evento no cubierto**: Error en la fase de enrutamiento de mensajería transaccional. Por ejemplo, Adobe Campaign no encontró el correo electrónico que actúa como plantilla para el evento.
* **Evento caducado**: Se ha alcanzado el número máximo de intentos de envío. El evento se considera nulo.

## Reciclaje de eventos {#event-recycling}

Si falla el envío de un mensaje en un canal específico, Adobe Campaign puede reenviar el mensaje con un canal diferente. Por ejemplo, si un envío del canal SMS falla, el mensaje se reenvía mediante el canal de correo electrónico.

Para ello, es necesario configurar un flujo de trabajo que vuelva a crear todos los eventos con el estado **Error de entrega** y les asigne un canal diferente.

>[!CAUTION]
>
>Este paso solo se puede llevar a cabo con un flujo de trabajo y, por lo tanto, se reserva para usuarios expertos. Para obtener más información, póngase en contacto con su administrador de cuentas de Adobe.