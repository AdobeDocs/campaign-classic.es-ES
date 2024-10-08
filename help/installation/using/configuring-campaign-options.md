---
product: campaign
title: Configuración de las opciones de Campaign
description: Obtenga información sobre cómo configurar las opciones de Campaign
feature: Installation, Application Settings
audience: installation
content-type: reference
topic-tags: appendices
exl-id: a979cd99-afa7-4ce6-ba0f-9495089cba08
source-git-commit: 0fba6a2ad4ffa864e2f726f241aa9d7cd39072a6
workflow-type: tm+mt
source-wordcount: '3831'
ht-degree: 1%

---

# Lista de opciones del Campaign Classic{#configuring-campaign-options}

El nodo **[!UICONTROL Administration / Platform / Options]** le permite configurar las opciones de Adobe Campaign. Algunos de ellos están integrados al instalar Campaign y otros se pueden añadir manualmente cuando sea necesario. Las opciones disponibles varían según los paquetes instalados con la instancia.


>[!CAUTION]
>
>* Las opciones que no aparecen en esta página son internas solamente y **no se debe modificar**.
>
>* La modificación o actualización de las opciones de Adobe Campaign solo pueden realizarlas usuarios expertos.

## Envío {#delivery}

<table> 
 <thead> 
  <tr> 
   <th> Nombre de opción </th> 
   <th> Descripción </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> <span class="uicontrol">Deliverability_LastBroadLogMsgDate</span> <br /> </td> 
   <td> Fecha del último broadLogMsg recuperado de la instancia de entrega.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Deliverability_LastBroadLogMsgSent</span> <br /> </td> 
   <td> Fecha del último broadLogMsg enviado a la instancia de entrega.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">DmRendering_cuid</span> <br /> </td> 
   <td> Identificador de informes de envío. Póngase en contacto con el soporte técnico para obtener su identificador.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">DestinosSemillaDeProcesamientoDm</span> <br /> </td> 
   <td> Lista de esquemas para los que desea utilizar direcciones de prueba para el procesamiento de la bandeja de entrada. (los nombres de elementos se separan con comas) P. ej.: custom_nms_recipient.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">DIRECCIÓN_EMTA_BCC</span> </td> 
   <td> Dirección de correo electrónico CCO a la que el MTA mejorado enviará una copia sin procesar de los correos electrónicos enviados. <br /> </td> 
  </tr>
  <tr> 
   <td> <span class="uicontrol">NMS_ActivateOwnerConfirmation</span> <br /> </td> 
   <td><p> Permite al operador a cargo de la entrega confirmar la entrega, si se designa un operador o grupo de operadores específico para iniciar una entrega en las propiedades de la entrega.</p><p> Para ello, active la opción introduciendo "1" como valor. Para desactivar esta opción, escriba "0".</p><p> El proceso de confirmación de envío funcionará de forma predeterminada: solo el operador o grupo de operadores designados para la entrega en las propiedades de envío (o un administrador) puede confirmar y llevar a cabo la entrega. Consulte <a href="../../campaign/using/marketing-campaign-deliveries.md#starting-an-online-delivery">esta sección</a>.</p> </td> 
   <tr> 
   <td> <span class="uicontrol">Nms_DefaultRcpSchema</span> <br /> </td> 
   <td> Adobe Campaign utiliza una variable global "Nms_DefaultRcpSchema" para dialogar con la base de datos de destinatario predeterminada (nms:recipient).<br /> El valor de la opción debe corresponder al nombre del esquema que coincide con la tabla de destinatarios externa.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsBilling_MainActionThreshold</span> <br /> </td> 
   <td> Número mínimo de destinatarios para que una entrega se considere la principal en el informe de facturación.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsBroadcast_DefaultProvider</span> <br /> </td> 
   <td> Proveedor de servicio de enrutamiento predeterminado para las nuevas plantillas.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsBroadcast_LogsPerTransaction</span> <br /> </td> 
   <td> Tamaño mínimo del lote (número de filas) para la inserción de broadLogs durante la preparación de una entrega.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsBroadcast_MaxDelayPerTransaction</span> <br /> </td> 
   <td> Umbral de duración del lote (número de milisegundos) por debajo del cual se duplica el tamaño del lote para la inserción de broadLogs durante una preparación de envío.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsBroadcast_MidAnalyzeBatchSize</span> <br /> </td> 
   <td> Tamaño de agrupación de las partes del envío al analizar los envíos intermediarios.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsBroadcast_MsgValidityDuration</span> <br /> </td> 
   <td> Período de envío predeterminado de un envío (en segundos).<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsBroadcast_RegexRules</span> <br /> </td> 
   <td> Expresiones regulares para normalizar los mensajes de envío.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsBroadcast_RemoveBlackList</span> <br /> </td> 
   <td> Si se introduce "1" como valor, se pueden excluir los destinatarios que ya no desean que se les contacte.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsBroadcast_RemoveDuplicatesRecipients</span> <br /> </td> 
   <td> Si escribe "1" como valor, puede omitir automáticamente las duplicaciones.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsDelivery_ErrorAddressMask</span> <br /> </td> 
   <td> Permite definir la sintaxis de la dirección de error utilizada al responder a un mensaje.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsDelivery_FromAddressMask</span> <br /> </td> 
   <td> Permite definir la sintaxis de la dirección remitente utilizada al enviar un mensaje.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsDelivery_ImageServerTimeout</span> <br /> </td> 
   <td> Permite definir un límite de tiempo de espera (en segundos) para obtener una respuesta del servidor al recuperar una imagen descargada de una dirección URL personalizada y adjunta a un correo electrónico. Si se supera este valor, no se puede enviar el mensaje. El valor predeterminado es 60 segundos.<br /> </td> 
  </tr> 
 <tr> 
   <td> <span class="uicontrol">NmsDelivery_MaxDownloadedImageSize</span> <br /> </td> 
   <td> Permite definir el tamaño máximo (en bytes) permitido para una imagen descargada de una dirección URL personalizada y adjunta a un correo electrónico. El valor predeterminado es 100.000 bytes (100 KB). Al enviar una prueba y descargar las imágenes para procesar el correo electrónico, si el tamaño de una imagen supera este valor o si hay un problema de descarga, se mostrará un error en los registros de entrega y se producirá un error en la entrega de prueba.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsDelivery_MaxRecommendationsAttachments</span> <br /> </td> 
   <td> Permite establecer un número máximo de archivos adjuntos en un correo electrónico o una plantilla de correo electrónico transaccional. Si se supera este valor, se mostrará una advertencia en los registros de análisis de envío o al publicar la plantilla de correo electrónico transaccional. El valor predeterminado es 1 archivo adjunto.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsDelivery_MaxRetry</span> <br /> </td> 
   <td> Número máximo de reintentos durante el análisis.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsDelivery_PublishingScript</span> <br /> </td> 
   <td> Script de publicación.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsDelivery_NoCountBroadLogMsgPush</span> <br /> </td> 
   <td> Deshabilite el recuento broadLogMsg para los mensajes push.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsDeliveryWizard_ShowDeliveryWeight</span> <br /> </td> 
   <td> Mostrar el peso del mensaje en el asistente de envío.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsEmail_DefaultErrorAddr</span> <br /> </td> 
   <td> Dirección de correo electrónico predeterminada con 'error' en el nivel de instancia usado para la entrega de correo electrónico si el usuario la deja vacía.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsEmail_DefaultFromAddr</span> <br /> </td> 
   <td> Dirección de correo electrónico "de" predeterminada en el nivel de instancia utilizado para el envío de correo electrónico si el usuario la deja vacía.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsEmail_DefaultReplyToAddr</span> <br /> </td> 
   <td> Dirección de correo electrónico de "respuesta" predeterminada en el nivel de instancia utilizado para el envío de correo electrónico si el usuario la deja vacía.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsEmail_ExpOrganization</span> <br /> </td> 
   <td> Nombre común del cliente. Se utiliza en algunos mensajes de advertencia mostrados a los destinatarios.<br /> "Está recibiendo este mensaje porque ha estado en contacto con `Organization` o una compañía afiliada. Para dejar de recibir mensajes de `Organization`<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsEmail_FromName</span> <br /> </td> 
   <td> Etiqueta de correo electrónico "de" predeterminada en el nivel de instancia utilizado para el envío de correo electrónico si el usuario la deja vacía.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsEmail_ReplyToName</span> <br /> </td> 
   <td> Etiqueta de correo electrónico predeterminada de "respuesta" en el nivel de instancia utilizado para el envío de correo electrónico si el usuario la deja vacía.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsEmail_RetryCount</span> <br /> </td> 
   <td> Período entre dos reintentos de un mensaje de correo electrónico (en segundos).<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsEmail_RetryPeriod</span> <br /> </td> 
   <td> Período de reintentos para mensajes de correo electrónico.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsForecast_MsgWeightFormula</span> <br /> </td> 
   <td> Fórmula utilizada para calcular la ponderación de un mensaje para una entrega provisional.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsInmail_AllowlistEmails</span> <br /> </td> 
   <td> Lista de direcciones de correo electrónico de reenvío autorizadas (desde el módulo de procesamiento de correo entrante). Las direcciones deben separarse con comas (o * para permitir todo). Por ejemplo: xyz@abc.com,pqr@abc.com.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsLine_AESKey</span> <br /> </td> 
   <td> Clave AES utilizada en el servlet 'lineImage' para codificar las direcciones URL (canal LINE).<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsNPAI_EmailMaxError</span> <br /> </td> 
   <td> En el canal "correo electrónico" (utilizar como predeterminado): número máximo de errores que se aceptan para los errores de mensajes NO ENTREGADOS durante la entrega antes de poner el destinatario en cuarentena.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsNPAI_EmailSignificantErrorDelay</span> <br /> </td> 
   <td> En el canal "correo electrónico" (usar como predeterminado) : Período mínimo transcurrido desde el error SOFT al que se hace referencia anteriormente, antes de tener en cuenta un nuevo error SOFT.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsNPAI_MobileMaxError</span> <br /> </td> 
   <td> En el canal "móvil": Número máximo de errores que se aceptan para los errores SUAVES durante la entrega antes de poner el destinatario en cuarentena.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsNPAI_MobileSignificantErrorDelay</span> <br /> </td> 
   <td> En el canal "móvil": Período mínimo transcurrido desde el error SOFT anterior al que se hace referencia, antes de tener en cuenta un nuevo error SOFT.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsMidSourcing_LogsPeriodHour</span> <br /> </td>
   <td> Permite especificar un periodo máximo (expresado en horas) para limitar el número de registros recuperados cada vez que se ejecuta el flujo de trabajo de sincronización.</a>.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsMidSourcing_PrepareFlow</span> <br /> </td> 
   <td> Número máximo de llamadas en la sesión de MidSourcing, que se pueden ejecutar en paralelo (3 de forma predeterminada).<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsMTA_Alert_Delay</span> <br /> </td> 
   <td> Retraso personalizado (en minutos) tras el cual un envío se considera "retrasado", siendo el valor predeterminado 30 minutos.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsOperation_DeliveryPreparationWindow</span> <br /> </td> 
   <td><p>El flujo de trabajo técnico <span class="uicontrol"><a href="../../workflow/using/about-technical-workflows.md">operationMgt</a></span> utiliza esta opción al contar el número de envíos en ejecución.</p>Permite definir el número de días por encima de los cuales las entregas con estado incoherente se excluirán del recuento de entregas en ejecución.</p><p>De forma predeterminada, el valor se establece en "7", lo que significa que se excluirán las entregas incoherentes de más de 7 días.</p></td> 
  </tr>
  <tr> 
   <td> <span class="uicontrol">NmsPaper_SenderLine1</span> <br /> </td> 
   <td> Línea 1 de la dirección del remitente.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsPaper_SenderLine3</span> <br /> </td> 
   <td> Línea 3 de la dirección del remitente.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsPaper_SenderLine4</span> <br /> </td> 
   <td> Línea 4 de la dirección del remitente.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsPaper_SenderLine6</span> <br /> </td> 
   <td> Línea 6 de la dirección del remitente.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsPaper_SenderLine7</span> <br /> </td> 
   <td> Línea 7 de la dirección del remitente.<br /> </td> 
  </tr>
  <tr> 
   <td> <span class="uicontrol">NmsServer_MirrorPageUrl</span> <br /> </td> 
   <td> La dirección URL del servidor de página espejo (de forma predeterminada, debe ser idéntica a NmsTracking_ServerUrl).<br /> Es el valor predeterminado de los envíos por correo electrónico cuando la dirección URL no se especifica en la definición de enrutamiento.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsSMS_Priority</span> <br /> </td> 
   <td> Parámetros de los mensajes SMS enviados: información transmitida a la puerta de enlace de SMS para indicar la prioridad del mensaje.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsSMS_RetryCount</span> <br /> </td> 
   <td> Número de reintentos al enviar mensajes SMS.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsSMS_RetryPeriod</span> <br /> </td> 
   <td> Período durante el cual se realizarán reintentos de mensajes SMS.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsUserAgentStats_LastConsolidation</span> <br /> </td> 
   <td> Fecha de la última consolidación para <span class="uicontrol">NmsUserAgent</span> estadísticas.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsWebSegments_LastStates</span> <br /> </td> 
   <td> Nombre de la opción que contiene los segmentos web y sus estados.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkBarcode_SpecialChar</span> <br /> </td> 
   <td> Habilitar/deshabilitar la compatibilidad con caracteres especiales para Code128.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Caracteres_Correo_ElectrónicoXtk</span> <br /> </td> 
   <td> Caracteres válidos para una dirección de correo electrónico.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkSecurity_Restrict_EditXML</span> </td> 
   <td> Agregue esta opción con el valor "0" para deshabilitar la edición del código XML de los envíos (haga clic con el botón derecho / <span class="uicontrol">Editar origen XML</span> o acceso directo <span class="uicontrol">CTRL + F4</span>).<br /> </td> 
  </tr>  
 </tbody> 
</table>

<!--<tr> 
   <td> <span class="uicontrol">EMTA_BCC_ADDRESS</span> </td> 
   <td> BCC email address for Momentum to send a raw copy of the sent emails. <br /> </td> 
  </tr>
-->

## Recursos {#resources}

<table> 
 <thead> 
  <tr> 
   <th> Nombre de opción </th> 
   <th> Descripción </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> <span class="uicontrol">NcmRessourcesDir</span> <br /> </td> 
   <td> Ubicación de los recursos para su publicación en la consola del cliente de Adobe Campaign. Consulte <a href="../../delivery/using/formatting.md#image-referencing">esta sección</a>.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NcmRessourcesDirPreview</span> <br /> </td> 
   <td> Ubicación de los recursos para la vista previa en la consola del cliente de Adobe Campaign. Consulte <a href="../../delivery/using/formatting.md#image-referencing">esta sección</a>.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsDelivery_DefaultIgnoredImage</span> <br /> </td> 
   <td> Lista de máscaras de URL para las imágenes omitidas durante la carga.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsDelivery_ImagePublishing</span> </td> 
   <td> Configuración de la carga de imágenes. Los valores pueden ser none / tracking / script / list (puede anularse mediante la configuración opcional del operador). </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsDelivery_ImageSubDirectory</span> <br /> </td> 
   <td> Carpeta en la que se almacenarán las imágenes del servidor.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsServer_LogoPath</span> <br /> </td> 
   <td> Espacio para mostrar logotipos.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NcmPublishingDir</span> <br /> </td> 
   <td> Carpeta raíz para publicaciones.<br /> Para obtener más información sobre la generación de contenido de texto y HTML, consulte <a href="../../delivery/using/using-a-content-template.md">esta sección</a>.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkImageUrl</span> <br /> </td> 
   <td> Permite definir el servidor en el que se almacenan las imágenes utilizadas en los envíos para permitir que el explorador las obtenga.<br /> Para las versiones de compilación &lt;= 5098, usamos la dirección URL de las imágenes que se cargaron en la instancia.<br /> Para versiones de compilación &gt; 5098, usamos en su lugar la URL pública de la entrega o la URL de la opción <span class="uicontrol">XtkFileRes_Public_URL</span>.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsDelivery_MediaInstance</span> <br /> </td> 
   <td> Permite configurar el nombre de instancia para la carga de imágenes.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsDelivery_MediaPassword</span> <br /> </td> 
   <td> Le permite configurar la contraseña para la carga de imágenes.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsDelivery_MediaServers</span> <br /> </td> 
   <td> Permite configurar las direcciones URL de medios para la carga de imágenes.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsBroadcast_MsgWebValidityDuration</span> <br /> </td> 
   <td> Duración de validez predeterminada para los recursos en línea de un envío (en segundos).<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkFileRes_Public_URL</span> <br /> </td> 
   <td> Nueva dirección URL para archivos de recursos públicos.<br /> </td> 
  </tr> 
 </tbody> 
</table>

## Administración de campañas y flujos de trabajo {#campaign-e-workflow-management}

<table> 
 <thead> 
  <tr> 
   <th> Nombre de opción </th> 
   <th> Descripción </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> <span class="uicontrol">CrmMarketingActivityWindow</span> <br /> </td> 
   <td> Historial de marketing mostrado para este número de meses.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsOperation_Duration</span> <br /> </td> 
   <td> Período de validez predeterminado de una campaña (en segundos).<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsOperation_LimitConcurrency</span> <br /> </td> 
   <td> Número máximo de trabajos de entrega, flujo de trabajo, hipótesis o simulación que se pueden procesar a la vez, iniciados por el flujo de trabajo de operationMgt.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsOperation_OperationMgtDebug</span> <br /> </td> 
   <td> Permite supervisar la ejecución del flujo de trabajo técnico <a href="../../workflow/using/about-technical-workflows.md">operationMgt</a>. Cuando se activa (valor "1"), la información de ejecución se registra en los registros de auditoría del flujo de trabajo.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsOperation_TimeRange</span> <br /> </td> 
   <td> Período de tiempo para condiciones de segmentación y extracción en modo programado.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Workflow_AnalysisThreshold</span> <br /> </td> 
   <td> Número de registros afectados tras los cuales las estadísticas de tabla se vuelven a calcular automáticamente.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkReport_Logo</span> <br /> </td> 
   <td> El logotipo se mostrará en la esquina superior derecha de los informes exportados.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsServer_PausedWorkflowPeriod</span> <br /> </td> 
   <td> Número de días de espera entre comprobaciones de flujos de trabajo en pausa.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsCampaign_Activate_OwnerConfirmation</span> <br /> </td> 
   <td> Active la validación de envíos por el propietario de la operación introduciendo "1" como valor. Para desactivar esta opción, escriba "0".<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsAsset_JavascriptExt</span> <br /> </td> 
   <td> Biblioteca JS adicional para cargar en la actividad del flujo de trabajo "Notificaciones de recursos de marketing".<br /> </td> 
  </tr> 
 </tbody> 
</table>

## Seguridad {#security}

<table> 
 <thead> 
  <tr> 
   <th> Nombre de opción </th> 
   <th> Descripción </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> <span class="uicontrol">RestringirEdiciónOOTBSchema</span> <br /> </td> 
   <td> (a partir de la versión 21.1.3) Si se selecciona 1 (valor predeterminado), esta opción deshabilita la edición de esquemas integrados.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">RestrictEditingOOTBJavascript</span> <br /> </td> 
   <td> (a partir de la versión 21.1.3) Si se selecciona 1 (valor predeterminado), esta opción deshabilita la edición de los códigos JavaScript integrados.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkAcceptOldPasswords</span> <br /> </td> 
   <td> (Modo de compatibilidad de instalación: compilación&gt;6000) Cuando se activa (valor "1"), esta opción permite el uso de contraseñas antiguas almacenadas en la base de datos para la conexión a cuentas externas o a la instancia.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkKey</span> <br /> </td> 
   <td> Esta clave se utiliza para cifrar la mayoría de las contraseñas de la base de datos. (cuentas externas, contraseña de LDAP...).<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkSecurity_Allow_PrivilegeEscalation</span> <br /> </td> 
   <td> Si se selecciona 1, esta opción permite la Escalación de privilegios en JavaScript.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkSecurity_Disable_ControlsOnFileDownload</span> <br /> </td> 
   <td> Si se selecciona 1, esta opción deshabilita los controles ACL durante la descarga de un archivo (mediante fileDownload.jsp).<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkSecurity_Disable_JSFileSandboxing</span> <br /> </td> 
   <td> Si se selecciona 1, esta opción deshabilita la zona protegida de archivos en JavaScript.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkSecurity_SaveOptions_AllowNonAdmin</span> <br /> </td> 
   <td> Si se establece como 'true', se autoriza al operador no administrador a actualizar los valores de xtkOption mediante el asistente de implementación.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkSecurity_Unsafe_DecryptString</span> <br /> </td> 
   <td> Si se selecciona 1, esta opción permite utilizar decryptString para descifrar algunas contraseñas.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkTraceDeleteLogin</span> <br /> </td> 
   <td> Introduzca el valor "1" para realizar un seguimiento de la eliminación de elementos con información de pista de auditoría en mData, mediante la modificación de su campo "modificado por" antes de la eliminación del registro.<br /> </td> 
  </tr> 
 </tbody> 
</table>

## Centro de mensajes {#message-center}

<table> 
 <thead> 
  <tr> 
   <th> Nombre de opción </th> 
   <th> Descripción </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> <span class="uicontrol">MC_EnrichmentCustomJs</span> <br /> </td> 
   <td> La biblioteca JavaScript se personalizará para enriquecer eventos. Debe contener la implementación de estas dos funciones: <br /> 
    <ul> 
     <li> <p> <span class="uicontrol">enrichRtEvents(aiEventId);</span> : enriquece y guarda eventos en la base de datos (donde <span class="uicontrol">aiEventId</span> corresponde a la tabla de eventos en tiempo real procesados).</p> </li> 
     <li> <p> <span class="uicontrol">enrichBatchEvents(aiEventId);</span> : enriquece y guarda eventos en la base de datos (donde <span class="uicontrol">aiEventId</span> corresponde a la tabla de ID de eventos por lotes procesados).</p> </li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">MC_LastUpdateFromBL</span> <br /> </td> 
   <td> Fecha de la última actualización del estado del evento mediante registros de envío.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">MC_RoutingCustomJs</span> <br /> </td> 
   <td> La biblioteca JavaScript se personalizará para los eventos de enrutamiento. Debe contener la implementación de estas dos funciones: <br /> 
    <ul> 
     <li> <p> <span class="uicontrol">patchRtEvent(iEventId);</span> : devuelve el nombre interno del mensaje transaccional seleccionado para procesar el evento en tiempo real (donde <span class="uicontrol">iEventId</span> corresponde al ID del evento en tiempo real procesado).</p> </li> 
     <li> <p> <span class="uicontrol">patchBatchEvent(iEventId);</span> : devuelve el nombre interno del mensaje transaccional seleccionado para procesar el evento por lotes (donde <span class="uicontrol">iEventId</span> corresponde al ID del evento por lotes procesado).</p> </li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">MC_RtEventAvgDeliveryTimeAlert</span> <br /> </td> 
   <td> Umbral de alerta de tiempo medio de envío de eventos en tiempo real.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">MC_RtEventAvgDeliveryTimeWarning</span> <br /> </td> 
   <td> Umbral de advertencia para el tiempo medio de envío de eventos en tiempo real.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">MC_RtEventAvgProcessTimeAlert</span> <br /> </td> 
   <td> Umbral de alerta para el tiempo medio de procesamiento de eventos en tiempo real.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">MC_RtEventAvgProcessTimeWarning</span> <br /> </td> 
   <td> Umbral de advertencia para el tiempo medio de procesamiento de eventos en tiempo real.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">MC_RtEventAvgQueueAlert</span> <br /> </td> 
   <td> Umbral de alerta para el promedio de eventos en tiempo real en cola.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">MC_RtEventAvgQueueTimeAlert</span> <br /> </td> 
   <td> Umbral de alerta para el tiempo medio de cola de eventos en tiempo real.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">MC_RtEventAvgQueueTimeWarning</span> <br /> </td> 
   <td> Umbral de advertencia para el tiempo medio de cola de los eventos en tiempo real.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">MC_RtEventAvgQueueWarning</span> <br /> </td> 
   <td> Umbral de advertencia para el promedio de eventos en tiempo real en cola.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">MC_RtEventErrorAlert</span> <br /> </td> 
   <td> Umbral de alerta para procesar errores de eventos en tiempo real.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">MC_RtEventErrorWarning</span> <br /> </td> 
   <td> Umbral de advertencia para el procesamiento de errores de eventos en tiempo real.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">MC_RtEventMaxQueueAlert</span> <br /> </td> 
   <td> Umbral de alerta para el número máximo de eventos en tiempo real en cola.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">MC_RtEventMaxQueueWarning</span> <br /> </td> 
   <td> Umbral de advertencia para el número máximo de eventos en tiempo real en cola.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">MC_RtEventMinQueueAlert</span> <br /> </td> 
   <td> Umbral de alerta para el número mínimo de eventos en tiempo real en cola.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">MC_RtEventMinQueueWarning</span> <br /> </td> 
   <td> Umbral de advertencia para el número mínimo de eventos en tiempo real en cola.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">MC_RtEventQueueAlert</span> <br /> </td> 
   <td> Umbral antes de condición crítica para la cola de eventos pendientes en tiempo real.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">MC_RtEventQueueWarning</span> <br /> </td> 
   <td> Umbral antes de la advertencia para la cola de eventos pendientes en tiempo real.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">MC_RtEventThroughputAlert</span> <br /> </td> 
   <td> Umbral de alerta para el rendimiento de eventos en tiempo real.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">MC_RtEventThroughputWarning</span> <br /> </td> 
   <td> Umbral de advertencia para el rendimiento de eventos en tiempo real.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsMessageCenter_RoutingBatchSize</span> <br /> </td> 
   <td> Tamaño del reagrupamiento para el enrutamiento de eventos.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">MC_LastRtEventStat</span> <br /> </td> 
   <td> Actualizar el puntero del estado de RtEvent (última fecha hasta que se recuperaron los datos).<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsLine_MessageCenterURL</span> <br /> </td> 
   <td> URL del servidor del Centro de mensajes utilizada para enviar mensajes de bienvenida (canal LINE).<br /> </td> 
  </tr> 
 </tbody> 
</table>

## Base de datos {#database}

<table> 
 <thead> 
  <tr> 
   <th> Nombre de opción </th> 
   <th> Descripción </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> <span class="uicontrol">NmsCleanup_LastCleanup</span> <br /> </td> 
   <td> Define la última vez que se ejecutó el proceso de limpieza.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsCleanup_BroadLogPurgeDelay</span> <br /> </td> 
   <td> <p>Permite definir el retraso tras el cual se borran los broadlogs de la base de datos.</p><p>Esta opción se crea automáticamente una vez que el retraso se modifica en la interfaz. Si modifica el valor de la lista de opciones, debe expresarse en segundos.</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsCleanup_EventHistoPurgeDelay</span> <br /> </td> 
   <td><p> Permite definir el retraso tras el cual se borra el historial de eventos de la base de datos.</p><p>
   Esta opción se crea automáticamente una vez que el retraso se modifica en la interfaz. Si modifica el valor de la lista de opciones, debe expresarse en segundos.</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsCleanup_EventPurgeDelay</span> <br /> </td> 
   <td><p> Permite definir el retardo tras el cual se borran los eventos de la base de datos.</p><p>Esta opción se crea automáticamente una vez que el retraso se modifica en la interfaz. Si modifica el valor de la lista de opciones, debe expresarse en segundos.</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsCleanup_EventStatPurgeDelay</span> <br /> </td> 
   <td><p> Permite definir el retraso tras el cual se borran las estadísticas de evento de la base de datos.</p><p>Esta opción se crea automáticamente una vez que el retraso se modifica en la interfaz. Si modifica el valor de la lista de opciones, debe expresarse en segundos.</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsCleanup_PropositionPurgeDelay</span> <br /> </td> 
   <td><p> Permite definir el retraso tras el cual se borran las propuestas de la base de datos.</p><p> Esta opción se crea automáticamente una vez que el retraso se modifica en la interfaz. Si modifica el valor de la lista de opciones, debe expresarse en segundos.</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsCleanup_QuarantineMailboxFull</span> <br /> </td> 
   <td> <p>Permite definir el retraso tras el cual se borran las cuarentenas de la base de datos.</p><p> Esta opción se crea automáticamente una vez que el retraso se modifica en la interfaz. Si modifica el valor de la lista de opciones, debe expresarse en segundos.</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsCleanup_RecycledDeliveryPurgeDelay</span> <br /> </td> 
   <td> <p>Permite definir el retraso tras el cual se borran los envíos reciclados de la base de datos.</p><p> Esta opción se crea automáticamente una vez que el retraso se modifica en la interfaz. Si modifica el valor de la lista de opciones, debe expresarse en segundos.</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsCleanup_RejectsPurgeDelay</span> <br /> </td> 
   <td> <p>Permite definir el retraso tras el cual se borran los rechazos de la base de datos.</p><p>Esta opción se crea automáticamente una vez que el retraso se modifica en la interfaz. Si modifica el valor de la lista de opciones, debe expresarse en segundos.</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsCleanup_TrackingLogPurgeDelay</span> <br /> </td> 
   <td> <p>Permite definir el retraso tras el cual se borran los registros de seguimiento de la base de datos.</p><p>Esta opción se crea automáticamente una vez que el retraso se modifica en la interfaz. Si modifica el valor de la lista de opciones, debe expresarse en segundos.</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsCleanup_TrackingStatPurgeDelay</span> <br /> </td> 
   <td><p> Permite definir el retraso tras el cual se borran las estadísticas de seguimiento de la base de datos.</p><p> Esta opción se crea automáticamente una vez que el retraso se modifica en la interfaz. Si modifica el valor de la lista de opciones, debe expresarse en segundos.</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsCleanup_VisitorPurgeDelay</span> <br /> </td> 
   <td> <p>Permite definir el retraso tras el cual se borran los visitantes de la base de datos.</p><p> Esta opción se crea automáticamente una vez que el retraso se modifica en la interfaz. Si modifica el valor de la lista de opciones, debe expresarse en segundos.</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsCleanup_WorkflowResultPurgeDelay</span> <br /> </td> 
   <td> <p>Permite definir el retraso tras el cual se borran de la base de datos los resultados del flujo de trabajo.</p><p> Esta opción se crea automáticamente una vez que el retraso se modifica en la interfaz. Si modifica el valor de la lista de opciones, debe expresarse en segundos.</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">WdbcCapabilities_AzureDw</span> <br /> </td> 
   <td> Opciones del conector SQL Datawarehouse de Azure.<br /> </td> 
  </tr>
   <tr> 
   <td> <span class="uicontrol">WdbcKillSessionPolicy</span> <br /> </td> 
   <td>Permite afectar al comportamiento Unconditional Stop en todos los flujos de trabajo y consultas de base de datos PostgreSQL según los siguientes valores potenciales:<ul>
    <li><p>0 - predeterminado: detiene el proceso de flujo de trabajo, sin impacto en la base de datos<p></li>
    <li><p>1 - pg_cancel_backend: detiene el proceso de flujo de trabajo y cancela la consulta en la base de datos<p></li>
    <li><p>2 - pg_terminate_backend: detiene el proceso de flujo de trabajo y finaliza la consulta en la base de datos<p></li></ul></td> 
  </tr>  
    <tr> 
   <td> <span class="uicontrol">WdbcOptions_TableSpaceUser</span> <br /> </td> 
   <td> Nombre del tablespace que va a contener los datos de las tablas ootb de Adobe Campaign.<br />Consulte <a href="../../installation/using/creating-and-configuring-the-database.md">Creación y configuración de la base de datos</a>.</td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">WdbcOptions_TableSpaceIndex</span> <br /> </td> 
   <td> Nombre del tablespace que va a contener los índices de las tablas ootb de Adobe Campaign.<br />Consulte <a href="../../installation/using/creating-and-configuring-the-database.md">Creación y configuración de la base de datos</a>.</td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">WdbcOptions_TableSpaceWork</span> <br /> </td> 
   <td> Nombre del tablespace que va a contener los datos de las tablas de trabajo de Adobe Campaign.<br />Consulte <a href="../../installation/using/creating-and-configuring-the-database.md">Creación y configuración de la base de datos</a>.</td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">WdbcOptions_TableSpaceWorkIndex</span> <br /> </td> 
   <td> Nombre del tablespace que va a contener los índices de las tablas de trabajo de Adobe Campaign.<br />Consulte <a href="../../installation/using/creating-and-configuring-the-database.md">Creación y configuración de la base de datos</a>.</td> 
  </tr> 
    <tr> 
   <td> <span class="uicontrol">WdbcOptions_TempDbName</span> <br /> </td> 
   <td> Permite configurar una base de datos independiente para las tablas de trabajo en Microsoft SQL Server, con el fin de optimizar las copias de seguridad y la replicación. La opción corresponde al nombre de la base de datos temporal: si se especifica, las tablas de trabajo se escriben en esta base de datos. Ejemplo: 'tempdb.dbo.' (tenga en cuenta que el nombre debe terminar con un punto). <a href="../../production/using/rdbms-specific-recommendations.md#microsoft-sql-server">Más información</a> <br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">WdbcTimeZone</span> <br /> </td> 
   <td> Zona horaria de la instancia de Adobe Campaign. Ver <a href="../../installation/using/time-zone-management.md#configuration" target="_blank">Configuración</a>.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">WdbcUseNChar</span> <br /> </td> 
   <td> ¿Se han definido los campos de cadena de la base de datos con NChar?<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">WdbcUseTimeStampWithTZ</span> <br /> </td> 
   <td> ¿Los campos "datetime" de la base de datos almacenan información de zona horaria?<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkDatabaseId</span> <br /> </td> 
   <td> ID de la base de datos. Comienza por 'u' para la base de datos Unicode.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkInstancePrefix</span> <br /> </td> 
   <td> Prefijo agregado a nombres internos generado automáticamente.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkQuery_Schema_LineCount</span> <br /> </td> 
   <td> Número máximo de resultados devueltos por una consulta en xtk:schema y xtk:srcSchema.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkSequence_AutoGeneration</span> <br /> </td> 
   <td> Todos los esquemas personalizados, creados después de este tiempo, con autopk="true" y sin el atributo "pkSequence", obtienen una secuencia generada automáticamente "auto_ 
    &lt;schemanamespace&gt; 
     &lt;schemaname&gt;
       _seq. 
   </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NlMigration_KeepFolderStructure</span> <br /> </td> 
   <td> Durante la migración, la estructura de árbol se reorganiza automáticamente en función de los estándares de la nueva versión.<br /> Esta opción le permite deshabilitar la migración automática del árbol de navegación. Si lo utiliza, después de la migración tendrá que eliminar las carpetas obsoletas, agregar las nuevas carpetas y ejecutar todas las comprobaciones necesarias.<br /> 
    <ul> 
     <li> <p> <span class="uicontrol">Tipo de datos:</span> Entero</p> </li> 
     <li> <p> <span class="uicontrol">Valor (texto)</span> : 1 </p> </li> 
    </ul> Esta opción solo debe usarse si el árbol de navegación predeterminado ha sufrido demasiados cambios.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsLastErrorStatCoalesce</span> <br /> </td> 
   <td> Última fecha de procesamiento de la limpieza de la tabla <span class="uicontrol">NmsEmailErrorStat</span>.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">PostUpgradeLastError</span> <br /> </td> 
   <td> Información acerca del error que se produjo en la posactualización, según la sintaxis siguiente:<br /> <strong>{Build number}:{mode: pre/post/...}:{The 'lessThan'/'greaterOrEquelThan' where error occur + sub-step}</strong> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkCleanup_NoStats</span> <br /> </td> 
   <td> Escriba el valor "1" para que la actualización de estadísticas no se realice a través del flujo de trabajo de limpieza.<br /> </td> 
  </tr> 
 </tbody> 
</table>

## Integración {#integration}

<table> 
 <thead> 
  <tr> 
   <th> Nombre de opción </th> 
   <th> Descripción </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> <span class="uicontrol">AEMResourceTypeFilter</span> <br /> </td> 
   <td> AEM Tipos de recursos que se pueden utilizar en Adobe Campaign. Los valores deben estar separados por comas.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">nmsPipeline_config</span> <br /> </td> 
   <td> Permite configurar las Déclencheur del Experience Cloud. El tipo de datos es "texto largo" y debe estar en formato JSON. Ver <a class="anchorLink" href="https://helpx.adobe.com/campaign/kb/triggers-and-campaign.html#PipelineoptionNmsPipelineConfig" target="_blank">Cómo usar Déclencheur de Experience Cloud con Adobe Campaign Classic</a>.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">LASTIMPORT_&lt;%=instance.internalName%&gt;_&lt;%=activityName%&gt;</span> <br /> </td> 
   <td> Esta opción se utiliza al importar datos de un sistema de terceros a través de un conector CRM. La activación de la opción solo permite recopilar objetos modificados desde la última importación. Esta opción debe crearse manualmente y rellenarse de la siguiente manera: 
    <ul> 
     <li> <p> <span class="uicontrol">Nombre interno</span> : LASTIMPORT_&lt;%=instance.internalName%&gt;_&lt;%=activityName%&gt;</p> </li> 
     <li> <p> <span class="uicontrol">Valor (campo)</span> : fecha de la última importación, con el formato aaaa/MM/dd hh:mm:ss. </p> </li> 
    </ul><br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">TNT_EdgeServer</span> <br /> </td> 
   <td> Servidor de Adobe Target utilizado para la integración. Esta opción está seleccionada de forma predeterminada. Este valor corresponde al Domain Server de Adobe Target, seguido del valor /m2. Por ejemplo: tt.omtrdc.net/m2.<br /> Ver <a href="../../integrations/using/configuring-the-integration-with-adobe-target.md">esta sección</a>.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">TNT_TenantName</span> <br /> </td> 
   <td> Nombre de la organización Adobe Target. Este valor corresponde al nombre de Adobe Target Client.<br /> Ver <a href="../../integrations/using/configuring-the-integration-with-adobe-target.md">esta sección</a>.<br /> </td> 
  </tr> 
  <tr> 
   <td> AAM <span class="uicontrol">ID_origenDeDatosDeDatos</span> <br /> </td> 
   <td> Opción utilizada para la integración con Adobe Audience Manager.<br /> </td> 
  </tr> 
  <tr> 
   <td> AAM <span class="uicontrol">ID_destino_de_destino</span> <br /> </td> 
   <td> Opción utilizada para la integración con Adobe Audience Manager.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">WdbcCapabilities_Teradata</span> <br /> </td> 
   <td> opciones del conector de teradata.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">WdbcCapabilities_Hive</span> <br /> </td> 
   <td> Opciones de conector de Hive.<br /> </td> 
  </tr> 
 </tbody> 
</table>

## Ofertas {#offers}

<table> 
 <thead> 
  <tr> 
   <th> Nombre de opción </th> 
   <th> Descripción </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> <span class="uicontrol">NmsCoupons_MaxPerTransaction</span> <br /> </td> 
   <td> Número de cupones que se actualizan por transacción SQL.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsInteraction_LastPropositionSynchControl_</span> <br /> </td> 
   <td> '+ [esquema de la propuesta] + "_" + extAccountSource.@executionInstanceId + [esquema de la propuesta] + "_" + vars.executionInstanceIdFilter<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsInteraction_LastPropositionSynchExec_</span> <br /> </td> 
   <td> '+ [ esquema de la propuesta] + "_" + extAccountSource.@executionInstanceId + "_" + extAccountTarget.@executionInstanceId<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsInteraction_SynchWorkflowIds</span> <br /> </td> 
   <td> Seguimiento del flujo de trabajo de sincronización.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsInteraction_UseDaemon</span> <br /> </td> 
   <td> Habilitar/deshabilitar la escritura asincrónica de propuestas ("0" para deshabilitar, "1" para habilitar).<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsModule_CouponsEnabled</span> <br /> </td> 
   <td> Permite habilitar cupones.<br /> </td> 
  </tr> 
 </tbody> 
</table>

## Servidor {#server}

<table> 
 <thead> 
  <tr> 
   <th> Nombre de opción </th> 
   <th> Descripción </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> <span class="uicontrol">NmsExecutionInstanceId</span> <br /> </td> 
   <td> Identificador de instancia de ejecución.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsServer_CustomerId</span> <br /> </td> 
   <td> Identificador de cliente utilizado al enviar el informe de facturación.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsServer_IntranetURL</span> <br /> </td> 
   <td> URL base interna para obtener acceso al servidor de aplicaciones.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsServer_LastPostUpgrade</span> <br /> </td> 
   <td> Número de compilación de la instancia de AC antes de la última actualización.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsServer_URL</span> <br /> </td> 
   <td> URL básica del servidor de aplicaciones web públicas.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkPassUnknownSQLFunctionsToRDBMS</span> <br /> </td> 
   <td> Permite seguir utilizando funciones SQL antiguas no declaradas después de migrar. Se recomienda encarecidamente no utilizar esta opción debido a los riesgos de seguridad que presenta.<br /> </td> 
  </tr> 
 </tbody> 
</table>

## Seguimiento {#tracking}

<table> 
 <thead> 
  <tr> 
   <th> Nombre de opción </th> 
   <th> Descripción </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> <span class="uicontrol">NmsTracking_Available</span> <br /> </td> 
   <td> Opción que permite activar el seguimiento.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsTracking_ClickFormula</span> <br /> </td> 
   <td> Script de cálculo de URL rastreada.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsTracking_ExtAccount</span> <br /> </td> 
   <td> Permite definir la cuenta externa del servidor de seguimiento.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsTracking_Instance</span> <br /> </td> 
   <td> Permite definir el nombre de instancia en el servidor de seguimiento.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsTracking_LastConsolidation</span> <br /> </td> 
   <td> Última vez que la información de seguimiento se consolidó con nuevos datos.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsTracking_OpenFormula</span> <br /> </td> 
   <td> Abrir script de cálculo de URL.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsTracking_Password</span> <br /> </td> 
   <td> Contraseña para el servidor de seguimiento <br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsTracking_Pointer</span> <br /> </td> 
   <td> El puntero realiza un seguimiento de los últimos eventos de mensaje que se procesaron mediante sus identificadores y fecha.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsTracking_SecureServerUrl</span> <br /> </td> 
   <td> URL segura del servidor de seguimiento frontal.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsTracking_ServerUrl</span> <br /> </td> 
   <td> URL del servidor de seguimiento frontal.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsTracking_ServerUrlList</span> <br /> </td> 
   <td> Lista de direcciones URL utilizadas para ponerse en contacto con los servidores de seguimiento.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsTracking_UserAgentRules</span> <br /> </td> 
   <td> Conjunto de reglas de identificación del explorador.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsTracking_WebFormula</span> <br /> </td> 
   <td> Script utilizado para calcular las etiquetas de seguimiento web.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsTracking_WebTrackingDelivery</span> <br /> </td> 
   <td> Nombre de la entrega virtual diseñada para la administración del seguimiento web.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsTracking_WebTrackingMode</span> <br /> </td> 
   <td> Permite definir el modo de seguimiento web.<br /> </td> 
  </tr> 
 </tbody> 
</table>

## Privacidad {#privacy}

<table> 
 <thead> 
  <tr> 
   <th> Nombre de opción </th> 
   <th> Descripción </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> <span class="uicontrol">Solicitud de privacidad_ConfirmaciónEliminaciónPendiente</span> <br /> </td> 
   <td> Si se selecciona la opción 1, debe confirmar manualmente la eliminación en la interfaz en un segundo paso. De lo contrario, los datos se eliminarán sin confirmación.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Solicitud de privacidad_Confirmar eliminaciónPendienteDemora</span> <br /> </td> 
   <td> Retraso entre las esperas de solicitud para eliminar la confirmación y la solicitud se ha cancelado.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Solicitud de privacidad_MaxErrorAllowed</span> <br /> </td> 
   <td> Número máximo de errores permitidos al procesar o eliminar una solicitud de privacidad.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Demora_Purga_Solicitud_Privacidad</span> <br /> </td> 
   <td> Se crea un retraso entre la solicitud en la cola y los datos de la solicitud se eliminan.<br /> </td> 
  </tr> 
 </tbody> 
</table>

## LDAP {#ldap}

<table> 
 <thead> 
  <tr> 
   <th> Nombre de opción </th> 
   <th> Descripción </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> <span class="uicontrol">XtkLdap_Active</span> <br /> </td> 
   <td> Habilite el servidor LDAP para que se use para autenticar usuarios y proporcionar autorizaciones a los usuarios.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkLdap_AppLogin</span> <br /> </td> 
   <td> Inicio de sesión de la aplicación para ponerse en contacto con el servidor para realizar varias búsquedas.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkLdap_AppPassword</span> <br /> </td> 
   <td> Contraseña cifrada para el inicio de sesión de la aplicación.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkLdap_AutoOperator</span> <br /> </td> 
   <td> Habilitar la creación automática de operadores y derechos en Adobe Campaign.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkLdap_DN</span> <br /> </td> 
   <td> Fórmula de cálculo para DN de LDAP basada en el inicio de sesión.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkLdap_DNSsearch</span> <br /> </td> 
   <td> Habilitar la búsqueda de DN en el directorio.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkLdap_DNSsearchBase</span> <br /> </td> 
   <td> Base de búsqueda.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkLdap_DNSsearchFilter</span> <br /> </td> 
   <td> Filtro de búsqueda DN.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkLdap_DNSsearchScope</span> <br /> </td> 
   <td> Ámbito de búsqueda.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Mecanismo_XtkLdap</span> <br /> </td> 
   <td> Tipo de autenticación usado para ponerse en contacto con el servidor LDAP (sin formato, md5, lds, ntlm, dpa).<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkLdap_Rights</span> <br /> </td> 
   <td> Habilite la sincronización de autorizaciones y grupos desde el directorio LDAP a los derechos asignados en Adobe Campaign.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkLdap_RightsAttr</span> <br /> </td> 
   <td> Atributo LDAP que contiene el nombre de autorización.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkLdap_RightsBase</span> <br /> </td> 
   <td> Base de búsqueda.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkLdap_RightsFilter</span> <br /> </td> 
   <td> Filtro de búsqueda para autorizaciones de usuario.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkLdap_RightsMask</span> <br /> </td> 
   <td> Expresión para extraer los nombres de los derechos de Adobe Campaign de las autorizaciones LDAP.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkLdap_RightsScope</span> <br /> </td> 
   <td> Ámbito de búsqueda.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">ServidorXtkLdap</span> <br /> </td> 
   <td> Dirección del servidor LDAP (es posible especificar un puerto especificando ':' como separador).<br /> </td> 
  </tr> 
 </tbody> 
</table>

## Formularios web {#web-forms}

<table> 
 <thead> 
  <tr> 
   <th> Nombre de opción </th> 
   <th> Descripción </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> <span class="uicontrol">XtkUseScrollBar</span> <br /> </td> 
   <td> El valor establecido en 1 permitirá agregar la barra de desplazamiento a los formularios de detalles.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">InstanciaDeFormularioWebDeXtk</span> <br /> </td> 
   <td> Instancia que se utilizará para invalidar formularios web en el modo "otros servidores".<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkWebForm_Password</span> <br /> </td> 
   <td> Contraseña de la instancia que se va a usar para invalidar formularios web en el modo "otros servidores".<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkWebForm_ServersMode</span> <br /> </td> 
   <td> Opción que permite especificar el modo de invalidación de los formularios web: local de forma predeterminada, utiliza servidores de seguimiento si la opción es "seguimiento" y utiliza una lista personalizada con la opción "otros servidores".<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkWebForm_ServersURL</span> <br /> </td> 
   <td> Lista de direcciones personalizadas de servidores con los que se debe contactar para invalidar formularios web (modo "otros servidores").<br /> </td> 
  </tr> 
 </tbody> 
</table>
