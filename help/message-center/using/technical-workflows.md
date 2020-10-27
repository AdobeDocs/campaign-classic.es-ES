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
source-git-commit: f7527a2d9b76e34fbaa2c9471c44a7a1e7e074d7
workflow-type: tm+mt
source-wordcount: '309'
ht-degree: 70%

---


# Flujos de trabajo técnicos{#technical-workflows}

Debe asegurarse de que los flujos de trabajo técnicos de la instancia de control y de las diferentes instancias de ejecución se hayan creado e iniciado antes de implementar cualquier plantilla de mensaje transaccional.

Los distintos flujos de trabajo técnicos relacionados con los mensajes transaccionales (centro de mensajes) se desglosan entre la instancia de control y la instancia de ejecución.

## Flujos de trabajo de instancias de control {#control-instance-workflows}

En la instancia de control, tanto si tiene una o varias instancias de ejecución registradas, debe crear un flujo de trabajo de archivado para cada **[!UICONTROL Message Center execution instance]** cuenta externa. Click the **[!UICONTROL Create the archiving workflow]** button to create and start the workflow.

![](assets/messagecenter_archiving_002.png)

These workflows can then be accessed from the **Administration > Production > Message Center** folder. Una vez creados, los flujos de trabajo de archivado se inician automáticamente.

<!--**Minimal architecture**

Once the control and execution modules are installed on the same instance, you must create the archiving workflow using the deployment wizard. Click the **[!UICONTROL Create the archiving workflow]** button to create and start the workflow.

![](assets/messagecenter_archiving_001.png)-->

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

