---
title: Sincronización de audiencias
seo-title: Sincronización de audiencias
description: Sincronización de audiencias
seo-description: null
page-status-flag: never-activated
uuid: eda67bf7-8a0a-4240-8b31-de364be5d572
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: integrations
content-type: reference
topic-tags: acs-connector
discoiquuid: 749a084e-69ee-46b4-b09b-cb91bb1da3cd
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 0745b9c9d72538b8573ad18ff4054ecf788905f2

---


# Sincronización de audiencias{#synchronizing-audiences}

Puede crear una lista refinada mediante las funciones avanzadas de Campaign v7 y compartir esta lista directamente como una audiencia, en tiempo real y sin fisuras con Campaign Standard (incluidos los datos adicionales). El usuario de Campaign Standard puede consumir la audiencia en Adobe Campaign Standard.

Los objetivos complejos que impliquen datos adicionales no duplicados en Campaign Standard solo se pueden lograr con Campaign v7.

Con Campaign Standard también puede compartir listas de destinatarios o datos procedentes de un conector como Microsoft Dynamics.

Este ejemplo de uso muestra cómo preparar el objetivo de su envío en Campaign v7 y cómo reutilizar este objetivo y sus datos adicionales en un envío creado y realizado con Adobe Campaign Standard.

>[!NOTE]
>
>También puede enriquecer los datos utilizando los acumulados y las colecciones en Adobe Campaign Standard si todos los datos que necesita ya están duplicados.

## Requisitos previos {#prerequisites}

Para lograr esto, es necesario lo siguiente:

* Los destinatarios almacenados en la base de datos de Campaign v7 y sincronizarlos con Campaign Standard. Consulte la sección [Sincronización de perfiles](../../integrations/using/synchronizing-profiles.md) .
* Datos adicionales, como suscripciones o transacciones, almacenados en las tablas relacionadas con nms:recipients en la base de datos de Campaign v7. Estos datos pueden proceder de esquemas OOB o tablas personalizadas de Campaign v7. De forma predeterminada no están disponibles en Campaign Standard, ya que no están sincronizados.
* El derecho para ejecutar los flujos de trabajo en Campaign v7 y Campaign Standard.
* El derecho para crear y ejecutar un envío en Campaign Standard.

## Creación de un flujo de trabajo de objetivos con datos adicionales en Campaign v7 {#create-a-targeting-workflow-with-additional-data-in-campaign-v7}

Los objetivos complejos que impliquen datos adicionales no duplicados en Campaign Standard solo se pueden lograr con Campaign v7.

Una vez definidos el objetivo y los datos adicionales, es posible guardarlo como una lista que pueda compartirse con Campaign Standard.

>[!NOTE]
>
>Este es un ejemplo. Según sus necesidades, puede simplemente crear una consulta con una lista de destinatarios y compartirla con ACS sin más procesamiento. También puede utilizar otras actividades de gestión de datos para preparar el objetivo final.

Para obtener la audiencia final y sus datos adicionales:

1. Cree un nuevo flujo de trabajo desde **[!UICONTROL Profiles and Targets]** > **[!UICONTROL Jobs]** > **[!UICONTROL Targeting workflows]**.
1. Add a **[!UICONTROL Query]** activity and select the recipients that you want to send final email to. Por ejemplo, todos los destinatarios de entre 18 y 30 años que viven en Francia.

   ![](assets/acs_connect_query1.png)

1. Añada los datos adicionales desde la consulta. Para obtener más información, consulte la sección [Adición de información](../../workflow/using/query.md#adding-data).

   Este ejemplo muestra cómo añadir un acumulado para contar cuántos envíos recibió un destinatario en un año.

   En el **[!UICONTROL Query]**, seleccione **[!UICONTROL Add data...]**.

   ![](assets/acs_connect_query2.png)

1. Seleccione **[!UICONTROL Data linked to the filtering dimension]** y haga clic en **[!UICONTROL Next]**.

   ![](assets/acs_connect_query3.png)

1. Elija **[!UICONTROL Data linked to the filtering dimension]** y, a continuación, seleccione el **[!UICONTROL Recipient delivery logs]** nodo y haga clic en **[!UICONTROL Next]**.

   ![](assets/acs_connect_query4.png)

1. Seleccione **[!UICONTROL Aggregates]** en el **[!UICONTROL Data collected]** campo y haga clic en **[!UICONTROL Next]**.

   ![](assets/acs_connect_query5.png)

1. Añada una condición de filtrado para tener en cuenta solo los “logs” de cuentas creados durante los últimos 365 días y haga clic en **[!UICONTROL Next]**.

   ![](assets/acs_connect_query6.png)

1. Defina las columnas de salida. En este caso, la única columna necesaria es la del número de envíos. Para ello:

   * Select **[!UICONTROL Add]** on the right of the window.
   * En la **[!UICONTROL Select field]** ventana, haga clic en **[!UICONTROL Advanced selection]**.
   * Seleccione **[!UICONTROL Aggregate]** y luego **[!UICONTROL Count]**. Marque la **[!UICONTROL Distinct]** opción y haga clic en **[!UICONTROL Next]**.
   * En la lista de campos, seleccione el campo utilizado para la función **Recuento.** Choose a field that will always be populated, for example the **[!UICONTROL Primary key]** field, and click **[!UICONTROL Finish]**.
   * Change the expression in the **[!UICONTROL Alias]** column. Este alias le permite recuperar fácilmente la columna añadida en el envío final. Por ejemplo, **NBdeliveries**.
   * Haga clic en **[!UICONTROL Finish]** y guarde la configuración de la **[!UICONTROL Query]** actividad.
   ![](assets/acs_connect_query7.png)

1. Guarde el flujo de trabajo. En la siguiente sección se muestra cómo compartir la población con ACS.

## Uso compartido del objetivo con Campaign Standard {#share-the-target-with-campaign-standard}

Once the target population is defined, you can share it with ACS through a **[!UICONTROL List update]** activity.

1. In the workflow created previously, add a **[!UICONTROL List update]** activity and specify the list you want to update or create.

   Especifique la carpeta en la que desea guardar la lista en Campaign v7. Las listas están sujetas a la asignación de carpetas definida durante la implementación, lo cual puede afectar a su visibilidad una vez compartidas en Campaign Standard. Consulte la sección Conversión [de](../../integrations/using/acs-connector-principles-and-data-cycle.md#rights-conversion) derechos.

1. Make sure the **[!UICONTROL Share with ACS]** option is checked. Está activada de forma predeterminada.

   ![](assets/acs_connect_listupdate1.png)

1. Guarde y ejecute el flujo de trabajo.

   El objetivo y sus datos adicionales se guardan en una lista de Campaign v7 y se comparten inmediatamente como una audiencia de lista en Campaign Standard. Solo los perfiles que se hayan duplicado se comparten con ACS.

If an error occurs on the **[!UICONTROL List update]** activity, it means that the synchronization with Campaign Standard may have failed. To be able to see more details about what went wrong, go to **[!UICONTROL Administration]** > **[!UICONTROL ACS Connector]** > **[!UICONTROL Process]** > **[!UICONTROL Diagnosis]**. This folder contains synchronization workflows triggered by the **[!UICONTROL List update]** activity execution. Consulte la sección [Localización de averías del conector](../../integrations/using/troubleshooting-the-acs-connector.md) ACS.

## Recuperación de los datos en Campaign Standard y uso en un envío {#retrieve-the-data-in-campaign-standard-and-use-it-in-a-delivery}

Once the targeting workflow is executed in Campaign v7, you are able to find the list audience in read-only mode from the **[!UICONTROL Audiences]** menu of Campaign Standard.

![](assets/acs_connect_deliveryworkflow_audience.png)

Mediante la creación de un flujo de trabajo de envío en Campaign Standard, es posible utilizar esta audiencia, así como los datos adicionales que contiene, en un envío.

1. Create a new workflow from the **[!UICONTROL Marketing activities]** menu.
1. Add a **[!UICONTROL Read audience]** activity and select the audience you previously shared from Campaign v7.

   Esta actividad se utiliza para recuperar los datos de la audiencia seleccionada. You can also apply an additional **[!UICONTROL Source Filtering]** if needed by using the according tab of this activity.

1. Add an **[!UICONTROL Email delivery]** activity and configure it as any other [email delivery activity](https://docs.adobe.com/content/help/en/campaign-standard/using/managing-processes-and-data/channel-activities/email-delivery.html).
1. Abra el contenido del envío.
1. Añada un campo personalizado. From the popup, locate the **[!UICONTROL Additional data (targetData)]** node. Este nodo contiene los datos adicionales de la audiencia que se calcularon en el flujo de trabajo inicial de objetivo. Puede utilizarlos como cualquier otro campo personalizado.

   Para este ejemplo, el dato adicional proveniente del flujo de trabajo de objetivo original es el número de envíos a cada destinatario en los últimos 365 días. El alias de NBdeliveries especificado en el flujo de trabajo de objetivo se puede ver aquí.

   ![](assets/acs_connect_deliveryworkflow_targetdata.png)

1. Guarde el envío y el flujo de trabajo.

   El flujo de trabajo está listo para ejecutarse. El envío se analiza y está listo para su envío.

   ![](assets/acs_connect_deliveryworkflow_ready.png)

## Realización y monitorización de su envío {#send-and-monitor-your-delivery}

Una vez que el envío y el contenido estén listos, realice el envío tal y como se describe más detalladamente en [esta sección](https://docs.adobe.com/content/help/en/campaign-standard/using/managing-processes-and-data/channel-activities/email-delivery.html):

1. Ejecute el flujo de trabajo de envío. Este paso prepara el envío del correo electrónico.
1. En el panel de envío, confirme manualmente que el envío se puede realizar.
1. Monitorice los informes y “logs” de envío

   * **En Campaign Standard**: Acceda a [informes](https://docs.adobe.com/content/help/en/campaign-standard/using/reporting/about-reporting/about-dynamic-reports.html) y [registros](https://docs.adobe.com/content/help/en/campaign-standard/using/testing-and-sending/monitoring-messages/monitoring-a-delivery.html) relacionados con la entrega como en cualquier entrega.
   * **en Campaign v7 y Campaign Standard**: Las ID de envío, los registros generales de correo electrónico y los registros de seguimiento de correo electrónico se sincronizan con Campaign v7. A continuación, puede obtener una visualización a 360 grados de sus campañas de marketing desde Campaign v7.

      Las cuarentenas se sincronizan automáticamente con Campaign v7. Esto permite tener en cuenta la información que no se debe enviar de cara a la siguiente actividad de objetivos realizada en Campaign v7.

      Puede encontrar más información sobre la administración de la cuarentena en Campaign Standard en [esta sección](https://docs.adobe.com/content/help/en/campaign-standard/using/testing-and-sending/monitoring-messages/understanding-quarantine-management.html).

