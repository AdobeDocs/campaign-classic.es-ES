---
product: campaign
title: Flujos de trabajo técnicos
description: Obtenga más información sobre los flujos de trabajo técnicos disponibles con los paquetes de Campaign Classic
feature: Workflows
hide: true
hidefromtoc: true
exl-id: 9aed2665-cd4b-419c-b9f2-ea04fc1d8f01
source-git-commit: 776c664a99721063dce5fa003cf40c81d94f8c78
workflow-type: ht
source-wordcount: '1704'
ht-degree: 100%

---

# Flujos de trabajo técnicos{#about-technical-workflows}



## Acerca de los flujos de trabajo técnicos {#overview}

Los flujos de trabajo detallados en esta sección se instalan con los distintos paquetes integrados de Adobe Campaign. Estos paquetes, y los flujos de trabajo técnicos relacionados, dependen del acuerdo de licencia. Los paquetes integrados se detallan en [esta sección](../../installation/using/installing-campaign-standard-packages.md).

De forma predeterminada, los flujos de trabajo técnicos están disponibles en una subcarpeta del siguiente nodo: **[!UICONTROL Administration]** > **[!UICONTROL Production]** > **[!UICONTROL Technical workflows]**.

Tenga en cuenta que solo los operadores con derechos de administración pueden iniciar y modificar los flujos de trabajo técnicos. Para obtener más información sobre los permisos, consulte esta [sección](../../platform/using/access-management-groups.md#default-groups).

>[!NOTE]
>
>Los flujos de trabajo técnicos relacionados con el módulo Centro de mensajes están disponibles de forma predeterminada en el nodo **[!UICONTROL Administration]** > **[!UICONTROL Production]** > **[!UICONTROL Message Center]** > **[!UICONTROL Technical workflows]**.

Para obtener más información sobre la supervisión de flujos de trabajo técnicos, consulte la [sección dedicada](monitoring-technical-workflows.md).

## Lista de flujos de trabajo técnicos {#list-technical-workflows}

| Flujo de trabajo técnico | Paquete | Descripción |
|------|--------|-----------|
| **Limpieza de alias** (aliasCleansing) | Entrega | Este flujo de trabajo estandariza los valores de enumeración. Se activa cada día a las 3 de la mañana de forma predeterminada. |
| **Facturación** (facturación) | Entrega | Este flujo de trabajo envía el informe de actividad del sistema al operador “facturación” por correo electrónico. Se activa el día 25 de cada mes en la instancia de Marketing. |
| **Cálculo de las estadísticas de Twitter** (statsTwitter) | Redes sociales (marketing social): solo Campaign v7 | Este flujo de trabajo calcula las estadísticas vinculadas a los retuits y las visitas en X (anteriormente conocido como Twitter). |
| **Trabajos de Campaign** (operationMgt) | Campañas de marketing (Campaign) | Este flujo de trabajo administra los trabajos de las campañas de marketing (inicia la segmentación, la extracción de archivos, etc.). También crea flujos de trabajo relacionados con campañas recurrentes y periódicas. |
| **Recopilación de datos para el servicio HeatMap** (collectDataHeatMapService) | Instalado de forma predeterminada | Este flujo de trabajo recupera los datos requeridos por el servicio HeatMap. |
| **Recopilar solicitudes de privacidad** (collectPrivacyRequests) | Reglamento de protección de datos de privacidad | Este flujo de trabajo genera los datos del destinatario almacenados en Adobe Campaign y los hace disponibles para su descarga en la pantalla de la solicitud de privacidad. |
| **Cálculo de costes** (budgetMgt) | Campañas de marketing (Campaign) | Este flujo de trabajo inicia el cálculo de las líneas de gastos y de costes sobre presupuestos, planes, programas, campañas, envíos y tareas. |
| **Limpieza de base de datos** (cleanup) | Entrega | Este flujo de trabajo es el de mantenimiento de la base de datos: realiza diferentes cálculos a partir de las estadísticas y procesos, y elimina los datos obsoletos de la base de datos según la configuración definida en el asistente de implementación. Se activa cada día a las 4 a. m. de manera predeterminada. Para obtener más información, consulte [esta página](../../production/using/database-cleanup-workflow.md#monitoring-campaign-classic). |
| **Eliminar usuarios de LINE bloqueados** (deleteBlockedLineUsersV2) | Canal LINE | Este flujo de trabajo garantiza que los datos de los usuarios de LINE V2 se eliminen después de haber bloqueado la cuenta oficial de LINE durante 180 días. |
| **Eliminar datos de solicitudes de privacidad** (deletePrivacyRequestsData) | Reglamento de protección de datos de privacidad | Este flujo de trabajo elimina los datos del destinatario almacenados en Adobe Campaign. |
| **Indicadores de entrega** (deliveryIndicators) | Plataforma intermediaria | Este flujo de trabajo actualiza los indicadores de seguimiento de un envío para un envío. De forma predeterminada, este flujo de trabajo se activa cada hora. |
| **Procesos de los foros de debate** (newsgroupMgt) | Recursos de Marketing (MRM) | Este flujo de trabajo gestiona el envío de notificaciones de los foros de debate. Se activa cuando se recibe una señal de aprobación |
| **Procesos de marketing distribuido** (centralLocalMgt) | Marketing central/local (Marketing distribuido) | Este flujo de trabajo comienza con el proceso vinculado al uso del módulo de marketing distribuido. Inicia la creación de las campañas locales y gestiona las notificaciones vinculadas a los pedidos y a la disponibilidad del paquete de Campaign. |
| **Depuración de eventos** (webAnalyticsPurgeWebEvents) | Conectores de análisis web | Este flujo de trabajo permite eliminar todos los eventos del campo de base de datos según el periodo configurado en el campo Lifespan. |
| **Exportar audiencias a Adobe Experience Cloud** (exportSharedAudience) | Integración con Adobe Experience Cloud | Este flujo de trabajo exporta audiencias como audiencias o segmentos compartidos. Estas audiencias pueden utilizarse con las diferentes soluciones de Adobe Experience Cloud que utiliza. |
| **Previsión**(previsión) | Entrega | Este flujo de trabajo analiza las entregadas guardadas en el calendario provisional (crea registros provisionales). Se activa cada día a la 1 de la mañana de forma predeterminada. |
| **Cálculo acumulado completo (cubo propositionrcp)** (agg_nmspropositionrcp_full) | Motor de ofertas (interacción) | Este flujo de trabajo actualiza el acumulado completo para el cubo Propuesta de oferta. Se activa todos los días a las 6 a. m. de manera predeterminada. Este acumulado captura las siguientes dimensiones: Canal, Envío, Oferta de marketing y Fecha. Luego se utiliza el cubo Propuesta de oferta para generar informes basados en ofertas. Puede obtener más información sobre los cubos en [esta sección](../../reporting/using/ac-cubes.md). |
| **Identificación de contactos convertidos** (webAnalyticsFindConverted) | Conectores de análisis web | Este flujo de trabajo lista a los visitantes del sitio que han finalizado su compra después de la campaña de remarketing. Los datos recopilados por este flujo de trabajo se pueden consultar en el reporte de eficiencia de remarketing (consulte esta página). |
| **Importar audiencias desde Adobe Experience Cloud** (importSharedAudience) | Integración con Adobe Experience Cloud | Este flujo de trabajo permite importar audiencias y segmentos de distintas soluciones de Adobe Experience Cloud en Adobe Campaign. |
| **Trabajos en envíos en campañas** (deliveryMgt) | Campañas de marketing (Campaign) | Este flujo de trabajo activa los envíos aprobados e inicia el posprocesado del proveedor de servicios para un envío externo. También envía notificaciones de aprobación y recordatorios. |
| **Trabajos en proveedores de servicios** (supplierMgt) | Campañas de marketing (Campaign) | Este flujo de trabajo comienza a procesar el proveedor (correo electrónico al enrutador y posprocesado) una vez que se aprueban los envíos. |
| **Actualización de token de acceso de LINE V2** (updateLineV2AccessToken) | Canal LINE: solo Campaign v7 | Este flujo de trabajo actualiza el token de acceso a LINE V2. |
| **Migración MID a LineUserID** (MIDToUserIDMigration) | Canal LINE | Este flujo de trabajo genera las ID de los usuarios de LINE V2 para la migración de LINE V1 a LINE V2. |
| **Notificaciones de recursos de marketing** (assetMgt) | Recursos de Marketing (MRM) | Este flujo de trabajo gestiona las notificaciones vinculadas a la aprobación y publicación de los recursos de marketing. |
| **Centro de mensajes &lt;external_account_name>** (mcSynch_&lt;external_account_name>) | Control de mensajes transaccionales (Centro de mensajes - Control) | Este flujo de trabajo: <ul><li>recupera la lista de eventos procesados por las operaciones.</li><li>se sincroniza con la tabla NmsBroadLogMsg para poder recuperar los atributos del mensaje de la entrega.</li><li>recupera los registros de envío de eventos en cuanto se completa la sincronización con la tabla NmsBroadLogMsg.</li><li>se sincroniza con la tabla NmsTrackingUrl para recuperar el seguimiento de las URL de la entrega.</li><li>recupera las URL de seguimiento de eventos en cuanto se completa la sincronización con la tabla NmsTrackingUrl.</li><li>permite recuperar todas las direcciones de correo electrónico puestas en cuarentena cada tres horas después de realizar una entrega.</li></ul> |
| **Cálculo acumulado completo de MessageCenter** (agg_messageCenter_full) | Control de mensajes transaccionales (Centro de mensajes - Control) | Este flujo de trabajo actualiza el acumulado completo para el cubo Centro de mensajes. Se activa cada día a las 3 de la mañana de forma predeterminada. Este acumulado captura las siguientes dimensiones: canal, fecha, estado y tipo de evento. Luego se utiliza el cubo Centro de mensajes para generar informes basados en eventos. Puede obtener más información sobre los cubos en [esta sección](../../reporting/using/ac-cubes.md) |
| **Intermediario (contadores de envíos)** (defaultMidSourcingDlv) | Transferir a Intermediario | Este flujo de trabajo recopila información de recuento para los envíos en el servidor intermediario. La información de recuento incluye indicadores de entrega generales como el número de envíos realizados, etc. No se incluye la información de seguimiento como las aperturas. De forma predeterminada, se activa cada diez minutos. |
| **Intermediario (registros de envío)** (defaultMidSourcingLog) | Transferir a Intermediario | Este flujo de trabajo recopila los registros de envío en el servidor intermediario. Se activa cada hora de forma predeterminada. |
| **Administración de exclusión de NMAC** (mobileAppOptOutMgt) | Canal de aplicaciones móviles | Este flujo de trabajo actualiza las bajas de las notificaciones en los dispositivos móviles. Se activa cada 6 horas entre la medianoche y la 1 a. m. Para obtener más detalles, consulte [esta sección](../../delivery/using/understanding-quarantine-management.md#push-notification-quarantines). |
| **Notificación de ofertas** (offerMgt) | Entrega | Este flujo de trabajo implementa las ofertas aprobadas en el entorno en línea, así como todas las categorías incluidas en el catálogo de ofertas. |
| **Limpieza de flujos de trabajo en pausa** (cleanupPausedWorkflows) | Entrega | Este flujo de trabajo analiza los flujos de trabajo en pausa con opción de gravedad definida en normal y activa las advertencias y notificaciones cuando dichos flujos llevan demasiado tiempo en pausa. Tras un mes, los flujos de trabajo técnicos en pausa se detienen de manera incondicional. De forma predeterminada, se activa todos los lunes a las 5 a. m. Para obtener más información, consulte [Gestión de flujos de trabajo en pausa](monitoring-workflow-execution.md#handling-of-paused-workflows). |
| **Limpieza de solicitud de privacidad** (cleanupPrivacyRequests) | Reglamento de protección de datos de privacidad | Este flujo de trabajo borra los archivos de solicitud de acceso anteriores a 90 días. |
| **Procesamiento de eventos por lotes** (batchEventsProcessing) | Ejecución de mensaje transaccional (Centro de mensajes - Ejecución) | Este flujo de trabajo permite colocar eventos en lote en cola antes de asociarlos con una plantilla de mensaje. |
| **Procesamiento de eventos en tiempo real** (rtEventsProcessing) | Ejecución de mensaje transaccional (Centro de mensajes - Ejecución) | Este flujo de trabajo permite colocar eventos en tiempo real en cola antes de asociarlos con una plantilla de mensaje. |
| **Sincronización de propuestas** (propositionSynch) | Control del motor de oferta con instancia de ejecución | Este flujo de trabajo sincroniza las propuestas entre la instancia de marketing y la instancia de ejecución utilizada para las interacciones. |
| **Recuperación de eventos en la web** (webAnalyticsGetWebEvents) | Conectores de análisis web | Cada hora, este flujo de trabajo descarga segmentos sobre el comportamiento de los usuarios de Internet en un sitio determinado, los integra en la base de datos de Adobe Campaign e inicia el flujo de trabajo de remarketing. |
| **Sistema de informes de acumulados** (reportingAggregates) | Entrega | Este flujo de trabajo actualiza los agregados que se utilizan en los informes. Se activa cada día a la 2 de la mañana de forma predeterminada. |
| **Envío de indicadores y atributos de campañas** (webAnalyticsSendMetrics) | Conectores de análisis web | Este flujo de trabajo permite enviar indicadores de campaña de correo electrónico desde Adobe Campaign a Adobe Experience Cloud Suite a través del conector de Adobe® Analytics. Los indicadores correspondientes son los siguientes: Enviado (iSent), Número total de aperturas (iTotalRecipientOpen), Número total de destinatarios que hicieron clic (iTotalRecipientClick), Errores (iError), Exclusión (opt-out) (iOptOut). |
| **Stock: pedidos y alertas** (stockMgt) | Campañas de marketing (Campaign) | Este flujo de trabajo inicia el cálculo de stock en las líneas de pedido y administra los umbrales de alertas de advertencia. |
| **Sincronización de seguidores de Facebook** (syncFacebookFans) | Redes sociales (marketing social): solo Campaign v7 | Este flujo de trabajo importa los seguidores de Facebook en Adobe Campaign todos los días a las 7 a. m. |
| **Sincronización de páginas de Facebook** (syncFacebook) | Redes sociales (marketing social): solo Campaign v7 | Este flujo de trabajo sincroniza las páginas de Facebook con Adobe Campaign todos los días a las 7 a. m. |
| **Sincronización de páginas de Twitter** (syncTwitter) | Redes sociales (marketing social): solo Campaign v7 | Este flujo de trabajo importa los seguidores de X a Adobe Campaign todos los días a las 07:00. |
| **Notificación de tareas** (taskMgt) | Recursos de marketing (MRM): solo Campaign v7 | Este flujo de trabajo le permite enviar mensajes de notificación sobre las tareas de las campañas de marketing. |
| **Seguimiento** (seguimiento) | Entrega | Este flujo de trabajo realiza la recuperación y la consolidación de la información de seguimiento. También garantiza que se recalculen las estadísticas de seguimiento y envío, especialmente las utilizadas por los flujos de trabajo de archivado del Centro de mensajes. De forma predeterminada, se activa una vez cada hora. |
| **Actualizar estado del evento** (updateEventsStatus) | Ejecución de mensaje transaccional (Centro de mensajes - Ejecución) | Este flujo de trabajo permite asignar un estado a un evento. Los estados de eventos son los siguientes:<ul><li>Pendiente: el evento está en cola. Aún no se le ha asociado ninguna plantilla de mensaje.</li><li>Envío pendiente: el evento está en cola, se le ha asociado una plantilla de mensaje y el envío lo está procesando en ese momento.</li><li>Enviado: este estado se copia desde los registros de envío. Significa que el envío se realizó.</li><li>Envío ignorado: este estado se copia desde los registros de envío. Significa que el envío se ha ignorado.</li><li>Error de envío: este estado se copia desde los registros de envío. Significa que el envío ha fallado.</li><li>Evento no cubierto: el evento no se ha podido asociar con una plantilla de mensaje. El evento no se vuelve a procesar.</li></ul> |
| **Actualización para la entrega** (deliverabilityUpdate) | Entrega | Este flujo de trabajo se ejecuta todas las noches y gestiona las reglas de cualificación de los correos electrónicos rechazados, así como la lista de dominios y los MX. Esto requiere que el puerto HTTPS se abra en la plataforma. |