---
product: campaign
title: Configuraciones adicionales
description: Obtenga información sobre cómo ajustar configuraciones adicionales para la mensajería transaccional en Adobe Campaign Classic
feature: Transactional Messaging, Message Center
audience: message-center
content-type: reference
topic-tags: instance-configuration
exl-id: 4d25d740-db57-4d18-8cae-2dd49c4a786e
TQID: 'https://experienceleague.adobe.com/TJ5R6T1pu5JQU5SaGoWRgZLG2m29TWWPVB8nniorRUg'
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
    internal-label: Campaign
  - id: fd6e6e36-54e4-4f1a-96fc-1a750e400d50
    internal-label: Campaign Classic v7
feature_v2:
  - id: c5474392-5419-4296-9e41-f6f4ce4f6e9b
    internal-label: Administration
  - id: 6d358f27-4f3c-5ddf-9159-05192e672ba7
    internal-label: Message Center
  - id: a4671286-a59f-47e3-b97b-90627a1977d5
    internal-label: Communication channels
subfeature_v2:
  - id: d3b34fea-a110-482f-adb2-aae8d686bac8
    internal-label: Transactional messaging
topic_v2:
  - id: b5ce8718-c3af-4fdb-a1a9-fca32f83a87c
    internal-label: Implementation
  - id: eddd9b14-83bd-4ff4-9072-54a4a484abb7
    internal-label: Administration
source-git-commit: 758d5159759b19f7ef32e8cc8f6237547599e727
workflow-type: tm+mt
source-wordcount: '612'
ht-degree: 91%
---
# Configuraciones adicionales {#mc-additional-configurations}

Esta página cubre configuraciones adicionales para la mensajería transaccional en Campaign Classic v7.

>[!NOTE]
>
>Como parte del proceso de transición de la versión 7 a 8 de Campaign, toda la documentación de Campaign Classic se ha optimizado y reorganizado. Ahora, las funciones comunes solo están disponibles en el conjunto de documentación de Campaign v8. Para obtener más información sobre la depuración de eventos de mensajería transaccional y los flujos de trabajo técnicos, consulte la [documentación de Campaign v8](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/config/settings/transactional-msg-settings){target=_blank}.
>
>[![imagen](../../assets/do-not-localize/learn-more-button.svg)](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/config/settings/transactional-msg-settings){target=_blank}

## Umbrales de monitorización {#monitoring-thresholds}

Puede configurar los umbrales de advertencia (naranja) y los umbrales de alerta (rojo) de los indicadores que aparecen en los informes de **nivel de servicio del Centro de mensajes** y de **tiempo de procesamiento del Centro de mensajes** (consulte [Acceso a los informes de mensajería transaccional](https://experienceleague.adobe.com/es/docs/campaign/campaign-v8/send/real-time/event/delivery-execution){target="_blank"} [documentación de Campaign v8]).

Para realizar esto, siga los pasos a continuación:

1. Abra el asistente de implementación en la **instancia de ejecución**.

1. Vaya a la página **[!UICONTROL Message Center]**.

1. Utilice las flechas para modificar los umbrales.

   ![](assets/messagecenter_monitor_events_001.png)

>[!NOTE]
>
>El número de eventos pendientes en la cola se muestra en la sección [System indicators](../../production/using/monitoring-processes.md#system-indicators) de la página de monitorización del proceso de Adobe Campaign. Para obtener más información sobre el asistente de implementación, consulte [esta sección](../../installation/using/deploying-an-instance.md#deployment-assistant).

## Flujos de trabajo técnicos {#technical-workflows}

Debe asegurarse de que los flujos de trabajo técnicos de la instancia de control y de las diferentes instancias de ejecución se hayan creado e iniciado antes de implementar cualquier plantilla de mensaje transaccional.

### Archivado de la programación del flujo de trabajo

Evite modificar la programación del **flujo de trabajo de archivado** que se ejecuta en la instancia de control. De lo contrario, es posible que se pierdan algunos datos de seguimiento que se están extrayendo de la instancia de ejecución.

Si modifica la programación del flujo de trabajo de archivado, también debe cambiar la programación del **flujo de trabajo de seguimiento** en la instancia de ejecución para que coincida con la programación del flujo de trabajo de archivado en la instancia de control.

## Configuración de marcas múltiples {#configuring-multibranding}

Esta sección describe una solución para configurar el seguimiento y las direcciones URL de las páginas espejo por marca para los mensajes transaccionales en Adobe Campaign.

### Nota sobre la compatibilidad {#compatibility-note}

Esta configuración de promoción de la marca heredada no es compatible con el nuevo modelo de [promoción de la marca centralizada](https://experienceleague.adobe.com/docs/campaign-web/v8/conf/branding/branding-gs.html?lang=es){target="_blank"} introducido en Campaign v8.

Si el entorno existente utiliza esta configuración heredada, no se podrá migrar directamente al nuevo modelo de promoción de la marca centralizado. Se requiere una reimplementación completa de la configuración de la personalización de la marca para adoptar el nuevo sistema.

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
   >Obtenga información sobre cómo crear una cuenta externa de tipo instancia de ejecución en [esta sección](../../message-center/using/configuring-instances.md#control-instance).

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

En la instancia de control, se deben vincular las plantillas de entrega y las cuentas externas.

Para realizar esto, siga los pasos a continuación:

1. Cree una cuenta externa por marca con el mismo nombre interno que se define en la [instancia de ejecución](#execution-instance) (paso 1).

1. Cree una plantilla de envíos para cada marca. Consulte la [documentación de Campaign v8](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/create-templates.html?lang=es){target="_blank"}.

1. En las **[!UICONTROL Properties]** de la plantilla de envíos, configure el enrutamiento en la cuenta externa de la marca.
