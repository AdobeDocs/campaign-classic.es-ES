---
product: campaign
title: Monitorización de entregas en la IU de Campaign
description: Obtenga información sobre cómo acceder a la lista de entregas y utilizar el panel de entregas para monitorizar las entregas
feature: Monitoring
role: User, Developer
exl-id: 44ecc8c6-6584-43eb-96b4-7d8463053123
source-git-commit: eac670cd4e7371ca386cee5f1735dc201bf5410a
workflow-type: tm+mt
source-wordcount: '533'
ht-degree: 57%

---

# Monitorización de entregas en la IU de Campaign {#delivery-dashboard}

>[!NOTE]
>
>Encontrará instrucciones detalladas sobre el acceso a la lista de envíos y el uso del panel de entregas en la [documentación de Campaign v8](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/send/monitor/delivery-dashboard). Este contenido se aplica tanto a los usuarios de Campaign Classic v7 como a los de Campaign v8.
>
>Esta página documenta **personalizaciones específicas de Campaign Classic v7** para implementaciones híbridas y locales.

La monitorización de las entregas es esencial para garantizar que las campañas sean eficientes y lleguen a los clientes.

Para obtener información completa sobre el acceso a la lista de entregas, el uso de las pestañas del panel de entregas y la monitorización de las entregas, consulte [Monitorización de entregas de Campaign v8 en la documentación de la IU de Campaign](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/send/monitor/delivery-dashboard){target="_blank"}.

## Personalizar registros de envío {#use-case}

Para **implementaciones híbridas/locales de Campaign Classic v7**, puede personalizar los registros de envío ampliando los esquemas. Esta sección muestra cómo agregar las direcciones IP de los remitentes a los registros de envío.

>[!NOTE]
>
>Esta personalización requiere funcionalidades de extensión de esquema disponibles en implementaciones locales. Los usuarios de Cloud Services administrados de Campaign v8 deben ponerse en contacto con el Servicio de atención al cliente de Adobe para ver los campos de registro de envío personalizados.
>
>Esta modificación es diferente si utiliza una instancia única o una instancia de intermediario. Antes de realizar la modificación, asegúrese de que está conectado a la instancia de entregas de correo electrónico.

### Paso 1: Ampliación del esquema

Para agregar **publicID** a sus registros de entregas, primero debe extender el esquema. Puede continuar como se indica a continuación.

1. Cree una extensión de esquema en **[!UICONTROL Administration]** > **[!UICONTROL Configuration]** > **[!UICONTROL Data Schemas]** > **[!UICONTROL New]**.

   Para obtener más información sobre las extensiones de esquema, consulte [esta página](../../configuration/using/extending-a-schema.md).

1. Seleccione **[!UICONTROL broadLogRcp]** para ampliar los registros de entregas de destinatario (nms) y definir un espacio de nombres personalizado. En este caso será &quot;cus&quot;:

   ![](assets/schema-parameters.png)

   >[!NOTE]
   >
   >Si la instancia está en Intermediario, debe usar el esquema broadLogMid.

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

### Paso 2: Actualización de la estructura de la base de datos

Una vez realizadas las modificaciones, debe actualizar la estructura de la base de datos para que esté alineada con su descripción lógica.

Para realizar esto, siga los pasos a continuación:

1. Haga clic en el menú **[!UICONTROL Tools]** > **[!UICONTROL Advanced]** > **[!UICONTROL Update database structure...]**.

   ![](assets/update-database-structure.png)

1. En la ventana **[!UICONTROL Edit tables]**, se comprueba la tabla **[!UICONTROL NmsBroadLogRcp]** (o la tabla **[!UICONTROL broadLogMid]** si está en un entorno de intermediario), como se muestra a continuación:

   ![](assets/edit-tables.png)

   >[!IMPORTANT]
   >
   >Asegúrese siempre de que no haya ninguna otra modificación, excepto la tabla **[!UICONTROL NmsBroadLoGRcp]** (o la tabla **[!UICONTROL broadLogMid]** si está en un entorno de intermediario). Si es así, desmarque otras tablas.

1. Haga clic en **[!UICONTROL Next]** para validar. Se muestra la siguiente pantalla:

   ![](assets/update-script.png)

1. Haga clic en **[!UICONTROL Next]**, luego **[!UICONTROL Start]**, para actualizar la estructura de la base de datos de inicio. Se inicia la creación de índices. Este paso puede ser largo, dependiendo del número de filas de la tabla **[!UICONTROL NmsBroadLogRcp]**.

   ![](assets/start-database-update.png)

>[!NOTE]
>
>Una vez que la actualización de la estructura física de la base de datos se haya completado correctamente, debe desconectarse y volver a conectarse para que se tengan en cuenta las modificaciones.

### Paso 3: Validación de la modificación

Para confirmar que todo funcionó correctamente, debe actualizar la pantalla de registros de entregas.

Para ello, acceda a los registros de entregas y agregue la columna Identificador de IP.

![](assets/list-config.png)

>[!NOTE]
>
>Para obtener información sobre cómo configurar listas en la interfaz de Campaign Classic, consulte [esta página](../../platform/using/adobe-campaign-workspace.md).

A continuación, se muestra lo que debería ver en la pestaña **[!UICONTROL Delivery]** después de realizar las modificaciones:

![](assets/logs-with-ip.png)

## Temas relacionados

* [Supervisar los envíos en la interfaz de usuario de Campaign](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/send/monitor/delivery-dashboard){target="_blank"} (documentación de Campaign v8)
* [Estados de entrega](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/send/monitor/delivery-statuses){target="_blank"} (documentación de Campaign v8)
* [Explicación de los errores de entrega](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/send/monitor/delivery-failures){target="_blank"} (Documentación de Campaign v8: guía completa para v7 y v8)
* [Administración de cuarentena](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/send/monitor/quarantines){target="_blank"} (documentación de Campaign v8: guía completa para v7 y v8)
* [Configuración de correo rechazado](understanding-delivery-failures.md) (v7 híbrido/local)
* [Configuración de cuarentena](understanding-quarantine-management.md) (v7 híbrido/local)
