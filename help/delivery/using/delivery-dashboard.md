---
solution: Campaign Classic
product: campaign
title: Panel de entregas
description: Obtenga más información sobre cómo utilizar el panel de envío para supervisar sus envíos.
audience: delivery
content-type: reference
topic-tags: monitoring-deliveries
translation-type: tm+mt
source-git-commit: 3c82e30cdc1057be6357d48170b959fb89c79528
workflow-type: tm+mt
source-wordcount: '1173'
ht-degree: 50%

---


# Panel de entregas {#delivery-dashboard}

El **panel de entrega** es fundamental para controlar las entregas y los problemas que puedan ser detectados durante la entrega de mensajes.

Permite recuperar información de un envío y editarla si es necesario. Tenga en cuenta que el contenido de la ficha ya no se puede cambiar una vez que se haya enviado el envío.

A continuación se muestra la información que puede supervisar mediante las distintas fichas disponibles en el panel:

* [Resumen de envíos](#delivery-summary)
* [Informes de entrega](#delivery-reports)
* [Registros de envío, páginas espejo, exclusiones](#delivery-logs-and-history)
* [Registros de seguimiento e historia del envío](#tracking-logs)
* [Representación de envíos](#delivery-rendering)
* [Auditoría de entrega](#delivery-audit-)

![](assets/s_ncs_user_del_details.png)

**Temas relacionados:**

* [Comprensión de los errores de entrega](../../delivery/using/understanding-delivery-failures.md)
* [Comprensión de la gestión de la cuarentena](../../delivery/using/understanding-quarantine-management.md)
* [Prácticas recomendadas relacionadas con las entregas](../../delivery/using/delivery-best-practices.md)
* [Administración de envíos](../../delivery/using/about-deliverability.md)

## Resumen de entregas {#delivery-summary}

La pestaña **[!UICONTROL Summary]** contiene las características de la entrega: estado de entrega, canal utilizado, información sobre el remitente, asunto, información sobre la ejecución.

## Informes de entrega {#delivery-reports}

El vínculo **[!UICONTROL Reports]**, al que se puede acceder desde la ficha **[!UICONTROL Summary]**, permite ver un conjunto de informes relacionados con la acción de envío: informe general de envíos, informe detallado, informe de envíos, distribución de mensajes fallidos, tasa de apertura, clics y transacciones, etc.

El contenido de esta pestaña se puede configurar según sus necesidades. Para obtener más información sobre informes de envío, consulte [esta sección](../../reporting/using/delivery-reports.md).

![](assets/delivery-report.png)

## Registros de envío, historial y exclusiones {#delivery-logs-and-history}

La pestaña **[!UICONTROL Delivery]** ofrece un historial de los sucesos en esta entrega. Contiene los registros de entregas, es decir, la lista de mensajes enviados y su estado y los mensajes asociados.

Para una entrega, puede mostrar, por ejemplo, solo los destinatarios con una entrega fallido o una dirección en cuarentena. Para ello, haga clic en el botón **[!UICONTROL Filters]** y seleccione **[!UICONTROL By state]**. Seleccione el estado en la lista desplegable. En [esta página](../../delivery/using/delivery-statuses.md) se enumeran varios estados.

>[!NOTE]
>
>La lista que muestra los registros de envío se puede personalizar, como cualquier lista en Campaign Classic. Por ejemplo, puede agregar una columna para saber qué dirección IP envió cada correo electrónico en un envío. Para obtener más información sobre esto, consulte el caso de uso detallado en [esta sección](#use-case).

![](assets/s_ncs_user_delivery_delivery_tab.png)

El enlace **[!UICONTROL Display the mirror page for this message...]** permite ver la página espejo del contenido del envío seleccionado en la lista en una nueva ventana.

La página espejo solo está disponible para las entregas para los que se ha definido contenido HTML. Para obtener más información, consulte [Generación de la página espejo](../../delivery/using/sending-messages.md#generating-the-mirror-page).

![](assets/s_ncs_user_wizard_miror_page_link.png)

## Registros de seguimiento e historial de envíos {#tracking-logs}

La pestaña **[!UICONTROL Tracking]** enumera el historial de seguimiento de esta entrega. Esta pestaña muestra los datos de seguimiento de los mensajes enviados, es decir, todas las direcciones URL sobre las que Adobe Campaign realiza un seguimiento. Los datos de seguimiento se actualizan cada hora.

>[!NOTE]
>
>Si el seguimiento no está habilitado para un envío, esta ficha no se muestra.

La configuración de seguimiento se realiza en el escenario adecuado del asistente de envíos. Consulte [Configuración de los vínculos rastreados](../../delivery/using/how-to-configure-tracked-links.md).

Los datos de **[!UICONTROL Tracking]** se interpretan en los informes de envío. Consulte [esta sección](../../reporting/using/delivery-reports.md).

![](assets/s_ncs_user_delivery_tracking_tab.png)

## Renderización de la bandeja de entrada {#delivery-rendering}

La ficha **[!UICONTROL Inbox rendering]** le permite previsualización del mensaje en los diferentes contextos en los que se puede recibir y comprobar la compatibilidad en las principales aplicaciones y escritorios.

De este modo, puede asegurarse de que su mensaje se mostrará a los destinatarios de una manera óptima en una variedad de clientes web, correos electrónicos y dispositivos.

Para obtener más información sobre la representación de bandeja de entrada, consulte [esta página](../../delivery/using/inbox-rendering.md)

![](assets/s_tn_inbox_rendering_tokens.png)

## Auditoría de entrega {#delivery-audit-}

La pestaña **[!UICONTROL Audit]** contiene el registro de entrega y todos los mensajes correspondientes a las pruebas.

El botón **[!UICONTROL Refresh]** permite actualizar los datos. Utilice el botón **[!UICONTROL Filters]** para definir un filtro en los datos.

Los iconos especiales permiten identificar errores o advertencias. Consulte [Análisis de la entrega](../../delivery/using/steps-validating-the-delivery.md#analyzing-the-delivery).

La subpestaña **[!UICONTROL Proofs]** permite ver la lista de pruebas que se han enviado.

![](assets/s_ncs_user_delivery_log_tab.png)

Puede modificar la información mostrada en esta ventana (y la de las pestañas **[!UICONTROL Delivery]** y **[!UICONTROL Tracking]**) seleccionando las columnas que desea mostrar. Para ello, haga clic en el icono **[!UICONTROL Configure list]** situado en la esquina inferior derecha. Para obtener más información sobre la configuración de listas, consulte [esta sección](../../platform/using/adobe-campaign-workspace.md#configuring-lists).

## Sincronización del panel de entregas {#delivery-dashboard-synchronization}

En el panel de entregas, se recomienda comprobar los mensajes procesados y los registros de entregas para asegurarse de que su entrega se haya realizado correctamente.

Algunos indicadores o estados pueden ser incorrectos o no estar actualizados; esto puede resolverse con las soluciones siguientes:

* Si su estado de entrega es incorrecto, compruebe que se hayan realizado todas las aprobaciones necesarias para esta entrega o que los flujos de trabajo de **[!UICONTROL operationMgt]** y **[!UICONTROL deliveryMgt]** se estén ejecutando sin errores. Esto también se puede deber a que la entrega mediante una afinidad no está configurado en la instancia del emisor.

* Si los indicadores de envío aún se encuentran en 0 y si se encuentra en una configuración intermediaria, consulte el flujo de trabajo técnico **[!UICONTROL Mid-sourcing (delivery counters)]**. Inícielo si su estado no es **[!UICONTROL Started]**. A continuación, puede intentar volver a calcular los indicadores haciendo clic con el botón derecho en la entrega correspondiente en el explorador de Adobe Campaign y seleccionando **[!UICONTROL Actions]** > **[!UICONTROL Recompute delivery and tracking indicators]**. Para obtener más información sobre los indicadores de seguimiento, consulte [esta sección](../../reporting/using/delivery-reports.md#tracking-indicators).

* Si el contador de envío no coincide con su envío, intente volver a calcular los indicadores haciendo clic con el botón derecho en el envío correspondiente del explorador de Adobe Campaign y seleccionando **[!UICONTROL Actions]** > **[!UICONTROL Recompute delivery and tracking indicators]** para volver a sincronizar. Para obtener más información sobre los indicadores de seguimiento, consulte [esta sección](../../reporting/using/delivery-reports.md#tracking-indicators).

* Si el contador de envío no está actualizado para las implementaciones intermediarias, compruebe que se esté ejecutando el flujo de trabajo técnico **[!UICONTROL Mid-Sourcing (Delivery counters)]**. Para obtener más información, consulte [esta página](../../installation/using/mid-sourcing-deployment.md).

También puede rastrear las entregas con diferentes informes a través del panel de entrega. Para obtener más información, consulte [esta sección](../../reporting/using/delivery-reports.md).

## Caso de uso: Añadir las direcciones IP de los remitentes a los registros {#use-case}

En esta sección, aprenderá a agregar a los registros de envío información sobre la dirección IP que envió cada correo electrónico en un envío.

>[!NOTE]
>
>Esta modificación es diferente si utiliza una instancia única o una instancia de intermediaria. Antes de realizar la modificación, asegúrese de que está conectado a la instancia de envío de correo electrónico.

### Paso 1: Ampliar el esquema

Para agregar **publicID** a sus registros de envío, primero debe extender el esquema. Puede continuar como se indica a continuación.

1. Cree una extensión de esquema en **[!UICONTROL Administration]** > **[!UICONTROL Configuration]** > **[!UICONTROL Data Schemas]** > **[!UICONTROL New]**.

   Para obtener más información acerca de las extensiones de esquema, consulte [esta página](../../configuration/using/extending-a-schema.md).

1. Seleccione **[!UICONTROL broadLogRcp]** para ampliar los registros de envío de Destinatario (nms) y definir una Área de nombres personalizada. En este caso será &quot;cus&quot;:

   ![](assets/schema-parameters.png)

   >[!NOTE]
   >
   >Si la instancia está en Intermediaria, debe trabajar con el esquema wideLogMid.

1. Añada el nuevo campo en la extensión. En este ejemplo, debe reemplazar:

   ```
   <element img="nms:broadLog.png" label="Recipient delivery logs" labelSingular="Recipient delivery log" name="broadLogRcp"/>
   ```

   por:

   ```
   <element img="nms:broadLog.png" label="Recipient delivery logs" labelSingular="Recipient delivery log" name="broadLogRcp">
   <attribute desc="Outbound IP identifier" label="IP identifier"
   name="publicId" type="long"/>
   </element>
   ```

   ![](assets/edit-schema.png)

### Paso 2: Actualizar estructura de base de datos

Una vez realizadas las modificaciones, debe actualizar la estructura de la base de datos para que esté alineada con su descripción lógica.

Para realizar esto, siga los pasos a continuación:

1. Haga clic en el menú **[!UICONTROL Tools]** > **[!UICONTROL Advanced]** > **[!UICONTROL Update database structure...]**.

   ![](assets/update-database-structure.png)

1. En la ventana **[!UICONTROL Edit tables]**, se comprueba la tabla **[!UICONTROL NmsBroadLogRcp]** (o la tabla **[!UICONTROL broadLogMid]** si está en un entorno de Intermediaria), como se muestra a continuación:

   ![](assets/edit-tables.png)

   >[!IMPORTANT]
   >
   >Asegúrese siempre de que no haya ninguna otra modificación, excepto la tabla **[!UICONTROL NmsBroadLoGRcp]** (o la tabla **[!UICONTROL broadLogMid]** si está en un entorno de Intermediaria). Si es así, desmarque otras tablas.

1. Haga clic en **[!UICONTROL Next]** para validar. Se muestra la siguiente pantalla:

   ![](assets/update-script.png)

1. Haga clic en **[!UICONTROL Next]**, luego **[!UICONTROL Start]** para actualizar la estructura de la base de datos de inicio. Se está iniciando la creación de índices. Este paso puede ser largo, dependiendo del número de filas en la tabla **[!UICONTROL NmsBroadLogRcp]**.

   ![](assets/start-database-update.png)

>[!NOTE]
>
>Una vez que la actualización de la estructura física de la base de datos se haya completado correctamente, debe desconectarse y volver a conectarse para que se tengan en cuenta las modificaciones.

### Paso 3: Validar la modificación

Para confirmar que todo funcionó correctamente, debe actualizar la pantalla registros de envío.

Para ello, acceda a los registros de envío y agregue la columna &quot;Identificador de IP&quot;.

![](assets/list-config.png)

>[!NOTE]
>
>Para obtener información sobre cómo configurar listas en la interfaz de Campaign Classic, consulte [esta página](../../platform/using/adobe-campaign-workspace.md).

A continuación se muestra lo que debería ver en la ficha **[!UICONTROL Delivery]** después de realizar las modificaciones:

![](assets/logs-with-ip.png)
