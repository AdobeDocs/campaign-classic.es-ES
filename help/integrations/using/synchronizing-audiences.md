---
product: campaign
title: Sincronización de públicos
description: Obtenga información sobre cómo sincronizar públicos con el conector ACS
feature: ACS Connector
hide: true
exl-id: 88e581cf-43cd-4c43-9347-d016c62fdf42
TQID: https://experienceleague.adobe.com/9gc7VAt25SZk-QEFwAKpmRJCtRQu1HpMXQYzaRZAJ2I
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
feature_v2:
  - id: a658c786-869b-4194-a780-2594d663adda
  - id: b82389f8-9b5e-4083-8e3b-3cef299fb8b9
  - id: d5ef99fa-df0c-4153-bf94-105ad0724167
subfeature_v2:
  - id: cbcf4d90-26be-46e2-b16a-aebc529dc41e
  - id: df0d6518-6f49-46e2-b46e-3bcc513f553f
  - id: eb007b6d-6e57-46ab-9485-3f24d6102304
  - id: b1fd1501-3105-4d6b-b4d4-9af53126df75
topic_v2:
  - id: aa2f3246-cb95-4b30-8899-fdf7d73550cc
  - id: b5ce8718-c3af-4fdb-a1a9-fca32f83a87c
  - id: c1579802-ddd4-4214-8a91-97b2066abe11
  - id: e0eb8757-182f-49f3-94a4-1587d16f5094
  - id: ebde5b41-29c9-4f5e-9ef6-1197e85409e3
  - id: eddd9b14-83bd-4ff4-9072-54a4a484abb7
source-git-commit: 38eab6b8da73163e4476e91c0ef73f25c3f57546
workflow-type: ht
source-wordcount: 1161
ht-degree: 100%

---

# Sincronización de públicos{#synchronizing-audiences}



Puede crear una lista refinada mediante las funciones avanzadas de Campaign v7 y compartir esta lista directamente como un público, en tiempo real y sin fisuras con Campaign Standard (incluidos los datos adicionales). El usuario de Campaign Standard puede consumir el público en Adobe Campaign Standard.

Los objetivos complejos que impliquen datos adicionales no duplicados en Campaign Standard solo se pueden lograr con Campaign v7.

Con Campaign Standard también puede compartir listas de destinatarios o datos procedentes de un conector como Microsoft Dynamics.

Este ejemplo de uso muestra cómo preparar el objetivo de su entrega en Campaign v7 y cómo reutilizar este objetivo y sus datos adicionales en una entrega creada y realizada con Adobe Campaign Standard.

>[!NOTE]
>
>También puede enriquecer los datos utilizando los acumulados y las colecciones en Adobe Campaign Standard si todos los datos que necesita ya están duplicados.

## Requisitos previos {#prerequisites}

Para lograr esto, es necesario lo siguiente:

* Los destinatarios almacenados en la base de datos de Campaign v7 y sincronizarlos con Campaign Standard. Consulte la sección [Sincronización de perfiles](../../integrations/using/synchronizing-profiles.md).
* Datos adicionales, como suscripciones o transacciones, almacenados en tablas relacionadas con nms:recipients en la base de datos de Campaign versión 7.Estos datos pueden proceder de esquemas OOB o tablas personalizadas de Campaign v7. De forma predeterminada no están disponibles en Campaign Standard, ya que no están sincronizados.
* El derecho para ejecutar los flujos de trabajo en Campaign v7 y Campaign Standard.
* El derecho para crear y ejecutar una entrega en Campaign Standard.

## Creación de un flujo de trabajo de direccionamiento con datos adicionales en Campaign v7 {#create-a-targeting-workflow-with-additional-data-in-campaign-v7}

Los objetivos complejos que impliquen datos adicionales no duplicados en Campaign Standard solo se pueden lograr con Campaign v7.

Una vez definidos el objetivo y los datos adicionales, es posible guardarlo como una lista que pueda compartirse con Campaign Standard.

>[!NOTE]
>
>Este es un ejemplo. Según sus necesidades, puede simplemente crear una consulta con una lista de destinatarios y compartirla con ACS sin más procesamiento. También puede utilizar otras actividades de gestión de datos para preparar el objetivo final.

Para obtener el público final y sus datos adicionales:

1. Cree un nuevo de flujo de trabajo desde **[!UICONTROL Profiles and Targets]** > **[!UICONTROL Jobs]** > **[!UICONTROL Targeting workflows]**.
1. Añada una actividad de **[!UICONTROL Query]** y seleccione los destinatarios a los que desea enviar el correo electrónico final. Por ejemplo, todos los destinatarios de entre 18 y 30 años que viven en Francia.

   ![](assets/acs_connect_query1.png)

1. Añada los datos adicionales desde la consulta. Para obtener más información, consulte la sección [Adición de información](../../workflow/using/query.md#adding-data).

   Este ejemplo muestra cómo añadir un acumulado para contar cuántos envíos recibió un destinatario en un año.

   En **[!UICONTROL Query]**, seleccione **[!UICONTROL Add data...]**

   ![](assets/acs_connect_query2.png)

1. Seleccione **[!UICONTROL Data linked to the filtering dimension]** y haga clic en **[!UICONTROL Next]**.

   ![](assets/acs_connect_query3.png)

1. Elija **[!UICONTROL Data linked to the filtering dimension]** y luego seleccione el nodo **[!UICONTROL Recipient delivery logs]** y haga clic en **[!UICONTROL Next]**.

   ![](assets/acs_connect_query4.png)

1. Seleccione **[!UICONTROL Aggregates]** en el campo **[!UICONTROL Data collected]** y haga clic en **[!UICONTROL Next]**.

   ![](assets/acs_connect_query5.png)

1. Añada una condición de filtrado para tener en cuenta solo los registros creados durante los últimos 365 días y haga clic en **[!UICONTROL Next]**.

   ![](assets/acs_connect_query6.png)

1. Defina las columnas de salida. En este caso, la única columna necesaria es la del número de envíos. Para ello:

   * En la parte derecha de la ventana, seleccione **[!UICONTROL Add]**.
   * En la ventana **[!UICONTROL Select field]**, haga clic en **[!UICONTROL Advanced selection]**.
   * Seleccione **[!UICONTROL Aggregate]**, luego **[!UICONTROL Count]**. Marque la opción **[!UICONTROL Distinct]** y haga clic en **[!UICONTROL Next]**.
   * En la lista de campos, seleccione el campo utilizado para la función **Recuento**. Seleccione un campo que se rellene siempre, por ejemplo, el campo **[!UICONTROL Primary key]**, y haga clic en **[!UICONTROL Finish]**.
   * Cambie la expresión en la columna **[!UICONTROL Alias]**. Este alias le permite recuperar fácilmente la columna añadida en la entrega final. Por ejemplo, **NBdeliveries**.
   * Haga clic en **[!UICONTROL Finish]** y guarde la configuración de la actividad **[!UICONTROL Query]**.

   ![](assets/acs_connect_query7.png)

1. Guarde el flujo de trabajo. En la siguiente sección se muestra cómo compartir la población con ACS.

## Uso compartido del destinatario con Campaign Standard {#share-the-target-with-campaign-standard}

Una vez definida la población destinataria, puede compartirla con ACS a través de una actividad de **[!UICONTROL List update]**.

1. En el flujo de trabajo creado anteriormente, añada una actividad **[!UICONTROL List update]** y especifique la lista que desea actualizar o crear.

   Especifique la carpeta en la que desea guardar la lista en Campaign v7. Las listas están sujetas a la asignación de carpetas definida durante la implementación, lo cual puede afectar a su visibilidad una vez compartidas en Campaign Standard. Consulte la sección [Conversión de derechos](../../integrations/using/acs-connector-principles-and-data-cycle.md#rights-conversion).

1. Asegúrese de que la opción **[!UICONTROL Share with ACS]** esté seleccionada. Está activada de forma predeterminada.

   ![](assets/acs_connect_listupdate1.png)

1. Guarde y ejecute el flujo de trabajo.

   El objetivo y sus datos adicionales se guardan en una lista de Campaign v7 y se comparten inmediatamente como un público de lista en Campaign Standard. Solo los perfiles que se hayan duplicado se comparten con ACS.

Si se produce un error en la actividad **[!UICONTROL List update]**, significa que la sincronización con Campaign Standard puede haber fallado. Para poder ver más detalles sobre qué ha fallado, vaya a **[!UICONTROL Administration]** > **[!UICONTROL ACS Connector]** > **[!UICONTROL Process]** > **[!UICONTROL Diagnosis]**. Esta carpeta contiene los flujos de trabajo de sincronización activados por la ejecución de la actividad **[!UICONTROL List update]**. Consulte la sección [Solución de problemas del conector ACS](../../integrations/using/troubleshooting-the-acs-connector.md).

## Recuperación de los datos en Campaign Standard y uso en una entrega {#retrieve-the-data-in-campaign-standard-and-use-it-in-a-delivery}

Una vez que el flujo de trabajo de segmentación se ejecuta en Campaign v7, puede encontrar el público de lista en modo de solo lectura desde el menú **[!UICONTROL Audiences]** de Campaign Standard.

![](assets/acs_connect_deliveryworkflow_audience.png)

Mediante la creación de un flujo de trabajo de entrega en Campaign Standard, es posible utilizar este público, así como los datos adicionales que contiene, en una entrega.

1. Cree un nuevo flujo de trabajo a través del menú **[!UICONTROL Marketing activities]**.
1. Añada una actividad **[!UICONTROL Read audience]** y seleccione el público que ha compartido previamente desde Campaign v7.

   Esta actividad se utiliza para recuperar los datos del público seleccionado. También puede aplicar un **[!UICONTROL Source Filtering]** adicional si lo necesita utilizando la pestaña correspondiente de esta actividad.

1. Añada una actividad **[!UICONTROL Email delivery]** y configúrela como cualquier otra [actividad de entrega de correo electrónico](https://experienceleague.adobe.com/docs/campaign-standard/using/managing-processes-and-data/channel-activities/email-delivery.html?lang=es).
1. Abra el contenido de la entrega.
1. Añada un campo personalizado. En la ventana emergente, busque el nodo **[!UICONTROL Additional data (targetData)]**. Este nodo contiene los datos adicionales del público que se calcularon en el flujo de trabajo inicial de segmentación. Puede utilizarlos como cualquier otro campo personalizado.

   Para este ejemplo, el dato adicional proveniente del flujo de trabajo de objetivo original es el número de envíos a cada destinatario en los últimos 365 días. El alias de NBdeliveries especificado en el flujo de trabajo de objetivo se puede ver aquí.

   ![](assets/acs_connect_deliveryworkflow_targetdata.png)

1. Guarde la entrega y el flujo de trabajo.

   El flujo de trabajo está listo para ejecutarse. La entrega se analiza y está listo para su entrega.

   ![](assets/acs_connect_deliveryworkflow_ready.png)

## Realización y monitorización de su entrega {#send-and-monitor-your-delivery}

Una vez que la entrega y el contenido estén listos, realice la entrega:

1. Ejecute el flujo de trabajo de entrega. Este paso prepara la entrega del correo electrónico.
1. En el panel de control de entrega, confirme manualmente que la entrega se puede realizar.
1. Monitorice los informes y “logs” de entrega

   * **En Campaign Standard**: Aceda a [informes](https://experienceleague.adobe.com/docs/campaign-standard/using/reporting/about-reporting/about-dynamic-reports.html?lang=es) y [registros](https://experienceleague.adobe.com/docs/campaign-standard/using/testing-and-sending/monitoring-messages/monitoring-a-delivery.html?lang=es) relacionados a la entrega como para cualquier entrega.
   * **en Campaign v7 y Campaign Standard**: Las ID de entrega, los registros generales de correo electrónico y los registros de seguimiento de correo electrónico se sincronizan con Campaign v7. A continuación, puede obtener una visualización a 360 grados de sus campañas de marketing desde Campaign v7.

     Las cuarentenas se sincronizan automáticamente con Campaign v7. Esto permite tener en cuenta la información que no se debe enviar de cara a la siguiente actividad de objetivos realizada en Campaign v7.

     Puede encontrar más información sobre la administración de la cuarentena en Campaign Standard en [esta sección](https://experienceleague.adobe.com/docs/campaign-standard/using/testing-and-sending/monitoring-messages/understanding-quarantine-management.html?lang=es).
