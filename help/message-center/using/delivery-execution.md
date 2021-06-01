---
solution: Campaign Classic
product: campaign
title: Ejecución de entrega
description: Obtenga más información sobre la ejecución y supervisión del envío de mensajes transaccionales.
audience: message-center
content-type: reference
topic-tags: event-processing
exl-id: 930c6395-0c00-40ee-a925-3e0cae67c55f
source-git-commit: d39b15b0efc6cbd6ab24e074713be6f8fc90e5fc
workflow-type: tm+mt
source-wordcount: '233'
ht-degree: 85%

---

# Ejecución de entrega {#delivery-execution}

## Mensaje transaccional que envía {#transactional-message-send}

En la instancia de ejecución, una vez que se haya completado la fase de enriquecimiento y se haya vinculado una plantilla de envíos al evento, se realiza el envío.

>[!NOTE]
>
>El MTA prioriza el procesamiento de los mensajes transaccionales sobre cualquier otro envío.

Todos los envíos se agrupan en la carpeta **[!UICONTROL Administration > Production > Message Center > Default > Deliveries]**.

![](assets/messagecenter_deliveries_execinstances_001.png)

De forma predeterminada, se clasifican en subcarpetas por mes de envío. Este orden se puede cambiar en las propiedades de la plantilla de mensaje como se muestra a continuación.

![](assets/messagecenter_deliveries_properties_001.png)

>[!NOTE]
>
>En el caso de instalaciones alojadas o híbridas, si se ha actualizado al [servidor de correo mejorado](../../delivery/using/sending-with-enhanced-mta.md), todos los mensajes transaccionales también se pueden enviar con el servidor de correo mejorado de Adobe Campaign para mejorar la capacidad de envío, el rendimiento y la gestión de rechazos. Todos los impactos son los mismos que con los mensajes de marketing estándar.

## Supervisión de mensajes transaccionales {#transactional-message-monitoring}

Para monitorizar los mensajes transaccionales, compruebe los [registros de envío](../../delivery/using/delivery-dashboard.md#delivery-logs-and-history).

Los envíos transaccionales enviados desde la instancia de ejecución se sincronizan con la instancia de control a través de un flujo de trabajo técnico (**[!UICONTROL Message Center execution instance]**) que se ejecuta cada hora.

>[!NOTE]
>
>Los envíos acumulan semanalmente los eventos en función de la actualización de eventos más reciente y no en la fecha de creación del evento. Por lo tanto, al extraer registros de envío de mensajería transaccional de la instancia de control, el ID de envío asociado con cada ID de registro de envío puede cambiar con el tiempo a medida que se actualiza el registro (por ejemplo, cuando se recibe una devolución de entrada para el evento).

<!--The transactional deliveries sent from the execution instance are synchronized back to the control instance as follows.

Let's take a [delivery template](../../message-center/using/introduction.md) labelled *Template_1*.

1. An event corresponding to *Template_1* is received on the execution instance.
1. The **Processing real time events** (rtEventsProcessing) workflow processes the event and searches for an existing delivery for the current month.

    >[!NOTE]
    >
    >If not found, a new delivery is created and the event is assigned to the new delivery.

1. The transactional email is sent and the delivery status changes to **[!UICONTROL Sent]**.
1. The **Message Center execution instance** (mcSync_mcExec) workflow retrieves the delivery logs from the execution instance and updates the delivery logs on the control instance.
1. The control instance searches for an existing delivery for week 40 (2020-09-28_Template_1).

    >[!NOTE]
    >
    >If not found, a new delivery is created.

1. The week after, an inbound bounce is received for the event.
1. The status of the event changes to **[!UICONTROL Delivery failed]**.
1. The **Message Center execution instance** (mcSync_mcExec) workflow retrieves the delivery logs from the execution instance and searches for a delivery for week 41 (2020-10-05_Template_1) to update the delivery logs. The delivery logs are then linked to a new delivery for the current week.

To summarize, the deliveries weekly accumulate the events based on the latest event update, and not on the event creation date.

Therefore, when extracting transactional messaging delivery logs from the control instance, the delivery ID associated with each delivery log ID changes every week.-->

Para monitorizar la actividad y ejecución de las instancias de ejecución, consulte [Informes de mensajería transaccional](../../message-center/using/about-transactional-messaging-reports.md).
