---
solution: Campaign Classic
product: campaign
title: Acerca del procesamiento de eventos
description: Acerca del procesamiento de eventos
audience: message-center
content-type: reference
topic-tags: event-processing
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '332'
ht-degree: 100%

---


# Acerca del procesamiento de eventos{#about-event-processing}

En el contexto de los mensajes de transacciones, un evento se genera mediante un sistema de información y se envía a Adobe Campaign mediante los métodos **[!UICONTROL PushEvent]** y **[!UICONTROL PushEvents]** (consulte [Descripción del evento](../../message-center/using/event-description.md)). Contiene datos vinculados al evento, como su tipo (confirmación de pedido o creación de cuenta en un sitio web por ejemplo), dirección de correo electrónico o número de móvil, así como otra información que permite enriquecer y personalizar el mensaje de transacciones antes de enviarlo. Puede ser la información de contacto del cliente, el idioma del mensaje o el formato de correo electrónico.

Ejemplo de datos de eventos:

![](assets/messagecenter_events_request_001.png)

Para procesar los eventos de mensajes de transacciones, se deben aplicar los siguientes pasos:

1. Recopilación de eventos,
1. Transferencia de eventos a una plantilla de mensajes,
1. Enriquecimiento de eventos con datos de personalización,
1. Ejecución de envío,
1. Reciclaje de eventos cuyo envío vinculado ha fallado (este paso se puede llevar a cabo mediante un flujo de trabajo de Adobe Campaign).

## Estados de eventos {#event-statuses}

**Event history**, en **[!UICONTROL Message Center]** > **[!UICONTROL Event history]**, agrupa todos los eventos procesados en una sola vista. Pueden clasificarse por tipo de evento o por **estado**. Estos estados son:

* **Pending**: indica que el evento puede ser:

   * un evento que acaba de ser recopilado y que aún no se ha procesado. La columna **[!UICONTROL Number of errors]** muestra el valor 0. La plantilla de correo electrónico aún no se ha vinculado.
   * un evento procesado pero cuya confirmación es errónea. La columna **[!UICONTROL Number of errors]** muestra un valor que no es 0. Para saber cuándo se volverá a procesar este evento, consulte la columna **[!UICONTROL Process requested on]**.

* **Pending delivery**: el evento se procesó y la plantilla de envío está vinculada. El correo electrónico está pendiente de envío y se aplica el proceso de envío clásico. Abra la entrega para obtener más información. Consulte [Delivery](../../delivery/using/about-message-tracking.md).
* **Sent**, **Ignored** y **Delivery error**: estos estados de envío se recuperan mediante el flujo de trabajo **updateEventsStatus.** Para obtener más información, se puede abrir la entrega correspondiente.
* **Event not covered**: la fase de enrutamiento del centro de mensajes ha fallado. Por ejemplo, Adobe Campaign no encontró el correo electrónico que actúa como plantilla para el evento.
* **Event expire**: se ha alcanzado el número máximo de intentos de envío. El evento se considera nulo.
