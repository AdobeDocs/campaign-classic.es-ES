---
product: campaign
title: Configuraciones adicionales
description: Obtenga información sobre cómo configurar configuraciones adicionales para la mensajería transaccional en Adobe Campaign Classic.
audience: message-center
content-type: reference
topic-tags: instance-configuration
exl-id: 4d25d740-db57-4d18-8cae-2dd49c4a786e
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: tm+mt
source-wordcount: '749'
ht-degree: 85%

---

# Configuraciones adicionales {#mc-additional-configurations}

## Umbrales de monitor {#monitoring-thresholds}

Puede configurar los umbrales de advertencia (naranja) y los umbrales de alerta (rojo) de los indicadores que aparecen en los informes **Nivel de servicio del Centro de mensajes** y **Tiempo de procesamiento del Centro de mensajes** (consulte).[](../../message-center/using/about-transactional-messaging-reports.md)

Para realizar esto, siga los pasos a continuación:

1. Abra el asistente de implementación en la **instancia de ejecución**.

1. Vaya a la página **[!UICONTROL Message Center]**.

1. Utilice las flechas para cambiar los umbrales.

   ![](assets/messagecenter_monitor_events_001.png)

>[!NOTE]
>
>El número de eventos pendientes en la cola se muestra en la sección [System indicators](../../production/using/monitoring-processes.md#system-indicators) de la página de monitorización del proceso de Adobe Campaign. Para obtener más información sobre el asistente de implementación, consulte [esta sección](../../installation/using/deploying-an-instance.md#deployment-wizard).

## Purga de eventos {#purging-events}

Se puede utilizar el [asistente de implementación](../../production/using/database-cleanup-workflow.md#deployment-wizard) para configurar cuánto tiempo se guardan los datos en la base de datos.

El [flujo de trabajo de limpieza de la base de datos](../../production/using/database-cleanup-workflow.md) lleva a cabo la depuración de eventos automáticamente. Este flujo de trabajo depura los eventos recibidos y almacenados en las instancias de ejecución y los eventos archivados en una instancia de control.

Utilice las flechas según corresponda para modificar la configuración de depuración.

Configuración de depuración de eventos en una instancia de control:

![](assets/messagecenter_delete_events_001.png)

Configuración de depuración de eventos en una instancia de ejecución:

![](assets/messagecenter_delete_events_002.png)

Para obtener más información sobre el flujo de trabajo de limpieza de la base de datos, consulte [esta sección](../../production/using/database-cleanup-workflow.md).


## Flujos de trabajo técnicos {#technical-workflows}

Debe asegurarse de que los flujos de trabajo técnicos de la instancia de control y de las diferentes instancias de ejecución se hayan creado e iniciado antes de implementar cualquier plantilla de mensaje transaccional.

Los distintos flujos de trabajo técnicos relacionados con los mensajes transaccionales (centro de mensajes) se desglosan entre la instancia de control y la instancia de ejecución.

### Flujos de trabajo de instancias de control {#control-instance-workflows}

En la instancia de control, tanto si tiene una o varias instancias de ejecución registradas, debe crear un flujo de trabajo de archivado para cada cuenta externa de la **[!UICONTROL Message Center execution instance]**. Haga clic en el botón **[!UICONTROL Create the archiving workflow]** para crear e iniciar el flujo de trabajo.

![](assets/messagecenter_archiving_002.png)

A continuación, se puede acceder a estos flujos de trabajo de archivado desde la carpeta **Administration > Production > Message Center**. Una vez creados, los flujos de trabajo de archivado se inician automáticamente.

<!--**Minimal architecture**

Once the control and execution modules are installed on the same instance, you must create the archiving workflow using the deployment wizard. Click the **[!UICONTROL Create the archiving workflow]** button to create and start the workflow.

![](assets/messagecenter_archiving_001.png)-->

### Flujos de trabajo de instancias de ejecución {#execution-instance-workflows}

En la instancia de ejecución, se puede acceder a los flujos de trabajo técnicos para la mensajería transaccional desde la carpeta **Administration > Production > Message Center.** Solo tiene que iniciarlos. Los flujos de trabajo de la lista son:

* **[!UICONTROL Processing batch events]** (internal name: **[!UICONTROL batchEventsProcessing]**): este flujo de trabajo permite desglosar eventos por lote en cola antes de relacionarlos con una plantilla de mensaje.
* **[!UICONTROL Processing real time events]** (internal name: **[!UICONTROL rtEventsProcessing]**): este flujo de trabajo permite desglosar eventos en tiempo real en cola antes de relacionarlos con una plantilla de mensaje.
* **[!UICONTROL Update event status]** (internal name: **[!UICONTROL updateEventStatus]**): este flujo de trabajo le permite atribuir un estado al evento.

   Los siguientes estados de eventos están disponibles:

   * **[!UICONTROL Pending]**: el evento está en cola. Aún no se le ha asignado ninguna plantilla de mensaje.
   * **[!UICONTROL Pending delivery]**: el evento está en cola, se le ha asignado una plantilla de mensaje y la entrega lo está procesando.
   * **[!UICONTROL Sent]** : este estado se copia desde los registros de envío. Significa que la entrega se realizó.
   * **[!UICONTROL Ignored by the delivery]** : este estado se copia desde los registros de envío. Significa que la entrega se ha omitido.
   * **[!UICONTROL Delivery failed]** : este estado se copia desde los registros de envío. Significa que la entrega ha fallado.
   * **[!UICONTROL Event not taken into account]**: el evento no se ha podido relacionar con una plantilla de mensaje. El evento no se va a procesar.

## Configuración de marcas múltiples {#configuring-multibranding}

Esta sección describe una solución para configurar el seguimiento y las direcciones URL de las páginas espejo por marca para los mensajes transacciones en Adobe Campaign.

### Requisitos previos {#prerequisites}

* Todos los anfitriones deben añadirse al archivo de configuración de la instancia (`config-<instance>.xml`).
* A cada marca se le debe asignar un subdominio.
* Se debe tener un certificado HTTPS para todas las marcas si el seguimiento web se realiza en páginas HTTPS.

Para configurar marcas múltiples, es necesario configurar las instancias de ejecución y la instancia de control.

### Instancia de ejecución {#execution-instance}

En las instancias de ejecución, siga los pasos a continuación:

1. Cree una cuenta externa por marca.

   >[!NOTE]
   >
   >Obtenga información sobre cómo crear una cuenta externa de tipo instancia de ejecución en la sección [Control instance](../../message-center/using/configuring-instances.md#control-instance).

1. Amplíe el esquema nms:extAccount para añadir la URL de seguimiento:

   ```
   <attribute advanced="true" desc="URL of the tracking servers" label="Tracking server URL"
   length="100" name="trackingURL" type="string"/>
   ```

   >[!NOTE]
   >
   >Obtenga información sobre cómo ampliar un esquema existente en la sección [Ampliación de un esquema](../../configuration/using/extending-a-schema.md).

1. Modifique el formulario nms:extAccount:

   ```
   <container label="Message domain branding" type="frame">
        <static type="help"> These parameters are used to override the DNS alias and addresses used during message delivery. When not populated, the values of the 'NmsServer_MirrorPageUrl' and 'NmsEmail_DefaultErrorAddr' options are used.</static>
        <input xpath="@mirrorURL"/>
        <input xpath="@trackingURL"/>
        <input img="nms:sendemail.png" menuId="deliveryMenuBuilder" type="scriptEdit">
               xpath="errorAddress"/>
      </container>
   ```

1. Modifique las opciones NmsTracking_OpenFormula y NmsTracking_ClickFormula para utilizar la cuenta externa en lugar de una opción global.

   Para ello, sustituya:

   ```
   <%@ include option='NmsTracking_ServerUrl' %>
   ```

   con:

   ```
   <%@ value object="provider" xpath="@trackingURL" %>
   ```

   >[!IMPORTANT]
   >
   >Estos cambios podrían provocar conflictos al realizar la actualización. Es posible que deba combinar manualmente estas fórmulas con su nueva versión.

### Instancia de control {#control-instance}

En la instancia de control, se deben vincular las plantillas de envío y las cuentas externas.

Para realizar esto, siga los pasos a continuación:

1. Cree una cuenta externa por marca con el mismo nombre interno que se define en la [instancia de ejecución](#execution-instance) (paso 1).

1. Crear una plantilla de envío predeterminada por cada marca.

   >[!NOTE]
   >
   >    Aprenda a crear una plantilla de envío en [esta sección](../../delivery/using/creating-a-delivery-template.md#creating-a-new-template).

1. En **[!UICONTROL Properties]** de la plantilla de envío, configure el enrutamiento en la cuenta externa de la marca.
