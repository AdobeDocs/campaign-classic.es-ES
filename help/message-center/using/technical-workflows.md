---
title: Flujos de trabajo técnicos
seo-title: Flujos de trabajo técnicos
description: Flujos de trabajo técnicos
seo-description: null
page-status-flag: never-activated
uuid: dfd1b180-86b5-4740-9bad-a0e210f433c5
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: message-center
content-type: reference
topic-tags: instance-configuration
discoiquuid: 2e648e63-06d2-4e8f-9934-066a41d18eac
translation-type: tm+mt
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: tm+mt
source-wordcount: '358'
ht-degree: 82%

---


# Flujos de trabajo técnicos{#technical-workflows}

Debe asegurarse de que los flujos de trabajo técnicos de la instancia de control y de las diferentes instancias de ejecución se hayan creado e iniciado antes de implementar cualquier plantilla de mensaje transaccional.

Los distintos flujos de trabajo técnicos relacionados con los mensajes transaccionales (centro de mensajes) se desglosan entre la instancia de control y la instancia de ejecución.

## Flujos de trabajo de instancias de control {#control-instance-workflows}

En la instancia de control, se debe crear un flujo de trabajo de archivado por instancia de ejecución. A continuación, se puede acceder a los flujos de trabajo de archivado desde la carpeta **Administration > Production > Message Center.** Una vez creados, los flujos de trabajo de archivado se inician automáticamente.

**Arquitectura distribuida**

Si se tiene una o varias instancias de ejecución registradas, en la instancia de control se debe crear un flujo de trabajo de archivado para cada cuenta externa **[!UICONTROL Message Center execution instance]**. Click the **[!UICONTROL Create the archiving workflow]** button to create and start the workflow.

![](assets/messagecenter_archiving_002.png)

**Arquitectura mínima**

Una vez instalados los módulos de control y ejecución en la misma instancia, se debe crear el flujo de trabajo de archivado mediante el asistente de implementación. Click the **[!UICONTROL Create the archiving workflow]** button to create and start the workflow.

![](assets/messagecenter_archiving_001.png)

## Flujos de trabajo de instancias de ejecución {#execution-instance-workflows}

En la instancia de ejecución, se puede acceder a los flujos de trabajo técnicos para la mensajería transaccional desde la carpeta **Administration > Production > Message Center.** Solo tiene que iniciarlos. Los flujos de trabajo de la lista son:

* **[!UICONTROL Processing batch events]** (internal name: **[!UICONTROL batchEventsProcessing]**): este flujo de trabajo permite desglosar eventos por lote en cola antes de relacionarlos con una plantilla de mensaje.
* **[!UICONTROL Processing real time events]** (internal name: **[!UICONTROL rtEventsProcessing]**): este flujo de trabajo permite desglosar eventos en tiempo real en cola antes de relacionarlos con una plantilla de mensaje.
* **[!UICONTROL Update event status]** (nombre interno: **[!UICONTROL updateEventStatus]** ): este flujo de trabajo le permite atribuir un estado al evento.

   Los siguientes estados de eventos están disponibles:

   * **[!UICONTROL Pending]**: el evento está en cola. Aún no se le ha asignado ninguna plantilla de mensaje.
   * **[!UICONTROL Pending delivery]**: el evento está en cola, se le ha asignado una plantilla de mensaje y la entrega lo está procesando.
   * **[!UICONTROL Sent]** :: este estado se copia de los registros de envío. Significa que la entrega se realizó.
   * **[!UICONTROL Ignored by the delivery]** :: este estado se copia de los registros de envío. Significa que la entrega se ha omitido.
   * **[!UICONTROL Delivery failed]** :: este estado se copia de los registros de envío. Significa que la entrega ha fallado.
   * **[!UICONTROL Event not taken into account]** :: el evento no se pudo vincular a una plantilla de mensaje. El evento no se va a procesar.

