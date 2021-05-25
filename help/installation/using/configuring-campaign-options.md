---
solution: Campaign Classic
product: campaign
title: Configuración de opciones de Campaign
description: Obtenga información sobre cómo configurar las opciones de Campaign
audience: installation
content-type: reference
topic-tags: appendices
exl-id: a979cd99-afa7-4ce6-ba0f-9495089cba08
source-git-commit: 3413a54b1f45d23dcec9bf363bcf714a94642245
workflow-type: tm+mt
source-wordcount: '3941'
ht-degree: 3%

---

# Lista de opciones de Campaign Classic{#configuring-campaign-options}

El nodo **[!UICONTROL Administration / Platform / Options]** permite configurar las opciones de Adobe Campaign. Algunos de ellos están integrados al instalar Campaign, mientras que otros se pueden agregar manualmente cuando sea necesario. Las opciones disponibles varían según los paquetes instalados con la instancia.

>[!CAUTION]
>
>* Las opciones que no aparecen en esta página son solo internas y **no se deben modificar**.
   >
   >
* La modificación o actualización de las opciones de Adobe Campaign solo pueden realizarla usuarios expertos.


## Envío {#delivery}

<table> 
 <thead> 
  <tr> 
   <th> Nombre de la opción </th> 
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
   <td> Fecha del último broadLogMsg enviado a la instancia de envío.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">DmRendering_cuid</span> <br /> </td> 
   <td> Identificador de informes de envío. Póngase en contacto con el servicio de asistencia técnica para obtener su identificador.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">DmRendering_SeedTargets</span> <br /> </td> 
   <td> Lista de esquemas para los que desea utilizar direcciones de prueba para la renderización de la bandeja de entrada. (los nombres de elementos están separados por comas) Por ejemplo: custom_nms_recipient.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NMS_ActivateOwnerConfirmation</span> <br /> </td> 
   <td><p> Permite que el operador a cargo de la entrega confirme la entrega si se designa un operador o grupo de operadores específico para iniciar una entrega en las propiedades de la entrega.</p><p> Para ello, active la opción introduciendo "1" como valor. Para desactivar esta opción, escriba "0".</p><p> El proceso de confirmación de envío funcionará de forma predeterminada: solo el operador o grupo de operadores designados para la entrega en las propiedades de envío (o un administrador) puede confirmar y llevar a cabo la entrega. Consulte <a href="../../campaign/using/marketing-campaign-deliveries.md#starting-an-online-delivery">esta sección</a>.</p> </td> 
   <tr> 
   <td> <span class="uicontrol">Nms_DefaultRcpSchema</span> <br /> </td> 
   <td> Adobe Campaign utiliza una variable global "Nms_DefaultRcpSchema" para dialogar con la base de datos de destinatarios predeterminada (nms:recipient).<br /> El valor de la opción debe corresponder al nombre del esquema que coincida con la tabla de destinatarios externa.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsBilling_MainActionThreshold</span> <br /> </td> 
   <td> Número mínimo de destinatarios para que un envío se considere como el principal en el informe de facturación.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsBroadcast_DefaultProvider</span> <br /> </td> 
   <td> Proveedor de servicio de enrutamiento predeterminado para las nuevas plantillas.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsBroadcast_LogsPerTransac</span> <br /> </td> 
   <td> Número de BroadLogs que se crean para una entrega a la vez.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsBroadcast_MaxDelayPerTransac</span> <br /> </td> 
   <td> Inserción (en la tabla) de registros (broadLogs) por transacciones: número de filas que procesar por lote.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsBroadcast_MidAnalyzeBatchSize</span> <br /> </td> 
   <td> Agrupación del tamaño de las piezas de envío al analizar los envíos intermediarios.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsBroadcast_MsgValidityDuration</span> <br /> </td> 
   <td> Período de entrega predeterminado para una entrega (en segundos).<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsBroadcast_RegexRules</span> <br /> </td> 
   <td> Expresiones regulares para normalizar mensajes de envío.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsBroadcast_RemoveBlackList</span> <br /> </td> 
   <td> La introducción de "1" como valor permite excluir los destinatarios que ya no deseen que se pongan en contacto con ellos.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsBroadcast_RemoveDuplicatesRecipients</span> <br /> </td> 
   <td> La introducción de "1" como valor permite ignorar automáticamente los dobles.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsDelivery_ErrorAddressMask</span> <br /> </td> 
   <td> Permite definir la sintaxis de la dirección de error utilizada al responder a un mensaje.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsDelivery_FromAddressMask</span> <br /> </td> 
   <td> Permite definir la sintaxis de la dirección From utilizada al enviar un mensaje.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsDelivery_ImageServerTimeout</span> <br /> </td> 
   <td> Permite definir un límite de tiempo de espera (en segundos) para obtener una respuesta del servidor al recuperar una imagen descargada de una URL personalizada y adjunta a un correo electrónico. Si se supera este valor, no se puede enviar el mensaje. El valor predeterminado es 60 segundos.<br /> </td> 
  </tr> 
 <tr> 
   <td> <span class="uicontrol">NmsDelivery_MaxDownloadedImageSize</span> <br /> </td> 
   <td> Permite definir el tamaño máximo (en bytes) permitido para una imagen descargada de una URL personalizada y adjunta a un correo electrónico. El valor predeterminado es 100 000 bytes. Al enviar una prueba y descargar las imágenes para procesar el correo electrónico, si el tamaño de una imagen supera este valor o si hay un problema de descarga, se mostrará un error en los registros de envío y el envío de la prueba dará error.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsDelivery_MaxRecomenddedAttachments</span> <br /> </td> 
   <td> Permite establecer un número máximo de archivos adjuntos en una plantilla de correo electrónico o de correo electrónico transaccional. Si se supera este valor, se mostrará una advertencia en los registros de análisis de envío o al publicar la plantilla de correo electrónico transaccional. El valor predeterminado es 1 archivo adjunto.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsDelivery_MaxRetry</span> <br /> </td> 
   <td> Número máximo de reintentos durante el análisis.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsDelivery_PublishingScript</span> <br /> </td> 
   <td> Secuencia de comandos de publicación.<br /> </td> 
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
   <td> Dirección de correo electrónico predeterminada "error" a nivel de instancia utilizada para la entrega de correo electrónico si la deja vacía el usuario.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsEmail_DefaultFromAddr</span> <br /> </td> 
   <td> Dirección de correo electrónico predeterminada "de" a nivel de instancia utilizada para la entrega de correo electrónico si el usuario la deja vacía.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsEmail_DefaultReplyToAddr</span> <br /> </td> 
   <td> Dirección de correo electrónico 'respuesta' predeterminada a nivel de instancia utilizada para la entrega de correo electrónico si el usuario la deja vacía.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsEmail_ExpOrganization</span> <br /> </td> 
   <td> Nombre común del cliente. Se utiliza en algunos mensajes de advertencia mostrados a los destinatarios.<br /> "Recibe este mensaje porque ha estado en contacto con ***** o una empresa afiliada. Para dejar de recibir mensajes de *****".<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsEmail_FromName</span> <br /> </td> 
   <td> Etiqueta de correo electrónico predeterminada "de" a nivel de instancia utilizada para la entrega de correo electrónico si el usuario la deja vacía.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsEmail_ReplyToName</span> <br /> </td> 
   <td> Etiqueta de correo electrónico predeterminada "respuesta" a nivel de instancia utilizada para la entrega de correo electrónico si el usuario lo deja vacío.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsEmail_RetryCount</span> <br /> </td> 
   <td> Período entre dos reintentos de un mensaje de correo electrónico (en segundos).<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsEmail_RetryPeriod</span> <br /> </td> 
   <td> Período de reintentos de los mensajes de correo electrónico.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsForecast_MsgWeightFormula</span> <br /> </td> 
   <td> Fórmula utilizada para calcular la ponderación de un mensaje para una entrega provisional.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsInmail_AllowlistEmails</span> <br /> </td> 
   <td> Lista de direcciones de correo electrónico de reenvío autorizadas (desde el módulo de procesamiento de correo entrante). Las direcciones deben separarse con comas (o * para permitir todo). Por ejemplo, xyz@abc.com,pqr@abc.com.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsLine_AESKey</span> <br /> </td> 
   <td> Clave AES utilizada en el servlet 'lineImage' para codificar las URL (canal LINE).<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsNPAI_EmailMaxError</span> <br /> </td> 
   <td> En el canal "correo electrónico" (usar como predeterminado) : Número máximo de errores aceptados, para errores de SOFT durante el envío antes de poner el destinatario en cuarentena.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsNPAI_EmailSignificantErrorDelay</span> <br /> </td> 
   <td> En el canal "correo electrónico" (usar como predeterminado) : Tiempo mínimo que se ha invertido desde el error SOFT al que se hace referencia anteriormente, antes de tener en cuenta un nuevo error SOFT.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsNPAI_MobileMaxError</span> <br /> </td> 
   <td> En el canal "móvil" : Número máximo de errores aceptados, para errores de SOFT durante el envío antes de poner el destinatario en cuarentena.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsNPAI_MobileSignificantErrorDelay</span> <br /> </td> 
   <td> En el canal "móvil" : Tiempo mínimo que se ha invertido desde el error SOFT al que se hace referencia anteriormente, antes de tener en cuenta un nuevo error SOFT.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsMidSourcing_LogsPeriodHour</span> <br /> </td>
   <td> Permite especificar un periodo máximo (expresado en horas) para limitar el número de registros recuperados cada vez que se ejecuta el flujo de trabajo de sincronización.</a>.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsMidSourcing_PrepareFlow</span> <br /> </td> 
   <td> Número máximo de llamadas en la sesión de midSourcing, que se pueden ejecutar en paralelo (3 de forma predeterminada).<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsMTA_Alert_Delay</span> <br /> </td> 
   <td> Retraso personalizado (en minutos) después del cual un envío se considera "retrasado", el valor predeterminado es de 30 minutos.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsOperation_DeliveryPreparationWindow</span> <br /> </td> 
   <td><p>Esta opción la utiliza el flujo de trabajo técnico <span class="uicontrol"><a href="../../workflow/using/about-technical-workflows.md">operationMgt</a></span> al contar el número de envíos en ejecución.</p>Permite definir el número de días por encima de los cuales los envíos con estado incoherente se excluirán del recuento de envíos en ejecución.</p><p>De forma predeterminada, el valor se establece en "7", lo que significa que se excluirán los envíos incoherentes de más de 7 días.</p></td> 
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
   <td> URL del servidor de páginas espejo (de forma predeterminada, debe ser idéntica a NmsTracking_ServerUrl).<br /> Es el valor predeterminado de los envíos de correo electrónico cuando la dirección URL no se especifica en la definición de enrutamiento.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsSMS_Priority</span> <br /> </td> 
   <td> Parámetros de los mensajes SMS enviados: información transmitida a la puerta de enlace SMS para indicar la prioridad del mensaje.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsSMS_RetryCount</span> <br /> </td> 
   <td> Número de reintentos al enviar mensajes SMS.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsSMS_RetryPeriod</span> <br /> </td> 
   <td> Período durante el cual se realizarán los reintentos de mensajes SMS.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsUserAgentStats_LastConsolidated</span> <br /> </td> 
   <td> Última fecha de consolidación para las estadísticas <span class="uicontrol">NmsUserAgent</span>.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsWebSegments_LastStates</span> <br /> </td> 
   <td> Nombre de la opción que contiene los segmentos web y sus estados.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkBarcode_SpecialChar</span> <br /> </td> 
   <td> Habilite o deshabilite la compatibilidad con caracteres especiales para Code128.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkEmail_Characters</span> <br /> </td> 
   <td> Caracteres válidos para una dirección de correo electrónico.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkSecurity_Restrict_EditXML</span> </td> 
   <td> Añada esta opción con el valor "0" para desactivar la edición del código XML de las entregas (haga clic con el botón derecho en / <span class="uicontrol">Editar código XML</span> o con el método abreviado <span class="uicontrol">CTRL + F4</span>).<br /> </td> 
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
   <th> Nombre de la opción </th> 
   <th> Descripción </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> <span class="uicontrol">NcmRessourcesDir</span> <br /> </td> 
   <td> Ubicación de los recursos para su publicación en la consola del cliente de Adobe Campaign. Consulte <a href="../../delivery/using/formatting.md#image-referencing">esta sección</a>.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NcmRessourcesDirPreview</span> <br /> </td> 
   <td> Ubicación de los recursos para obtener una vista previa en la consola del cliente de Adobe Campaign. Consulte <a href="../../delivery/using/formatting.md#image-referencing">esta sección</a>.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsDelivery_DefaultIgnoredImage</span> <br /> </td> 
   <td> Lista de máscaras de URL para las imágenes omitidas durante la carga.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsDelivery_ImagePublishing</span> </td> 
   <td> Configuración de la carga de imágenes. Los valores pueden ser ninguno / tracking / script / list (puede anularse por la configuración opcional del operador). </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsDelivery_ImageSubDirectory</span> <br /> </td> 
   <td> Carpeta en la que se deben almacenar las imágenes del servidor.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsServer_LogoPath</span> <br /> </td> 
   <td> Espacio para mostrar los logotipos.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NcmPublishingDir</span> <br /> </td> 
   <td> Carpeta raíz para publicaciones.<br /> Para obtener más información sobre la generación de contenido HTML y de texto, consulte  <a href="../../delivery/using/using-a-content-template.md">esta sección</a>.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkImageUrl</span> <br /> </td> 
   <td> Permite definir el servidor en el que se almacenan las imágenes utilizadas en los envíos para permitir que el navegador las obtenga.<br /> Para versiones de compilación  &lt;&gt;<br /> Para versiones de compilación &gt; 5098, utilizamos en su lugar la URL pública de la entrega o la URL de la opción  <span class="uicontrol">XtkFileRes_Public_</span> URL.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsDelivery_MediaInstance</span> <br /> </td> 
   <td> Permite configurar el nombre de instancia para la carga de imágenes.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsDelivery_MediaPassword</span> <br /> </td> 
   <td> Permite configurar la contraseña para la carga de imágenes.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsDelivery_MediaServers</span> <br /> </td> 
   <td> Permite configurar las URL de medios para la carga de imágenes.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsBroadcast_MsgWebValidityDuration</span> <br /> </td> 
   <td> Duración de validez predeterminada para los recursos en línea de un envío (en segundos).<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkFileRes_Public_URL</span> <br /> </td> 
   <td> Nueva URL para archivos de recursos públicos.<br /> </td> 
  </tr> 
 </tbody> 
</table>

## Administración de campañas y flujos de trabajo {#campaign-e-workflow-management}

<table> 
 <thead> 
  <tr> 
   <th> Nombre de la opción </th> 
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
   <td> Número máximo de trabajos de entrega/flujo de trabajo/hipótesis/simulación que se pueden procesar a la vez, iniciados por el flujo de trabajo de operationMgt.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsOperation_OperationMgtDebug</span> <br /> </td> 
   <td> Permite monitorizar la ejecución del flujo de trabajo técnico <a href="../../workflow/using/about-technical-workflows.md">operationMgt</a>. Cuando se activa (valor "1"), la información de ejecución se registra en los registros de auditoría del flujo de trabajo.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsOperation_TimeRange</span> <br /> </td> 
   <td> Período de tiempo para condiciones de objetivo y extracción en modo programado.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Workflow_AnalysisThreshold</span> <br /> </td> 
   <td> Número de registros afectados después de los cuales se recomiendan automáticamente las estadísticas de tabla.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkReport_Logo</span> <br /> </td> 
   <td> Logotipo que se mostrará en la esquina superior derecha de los informes exportados.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsServer_PausedWorkflowPeriod</span> <br /> </td> 
   <td> Número de días de espera entre comprobaciones para flujos de trabajo en pausa.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsCampaign_Activate_OwnerConfirmation</span> <br /> </td> 
   <td> Active la validación de envíos por parte del propietario de la operación introduciendo "1" como valor. Para desactivar esta opción, escriba "0".<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsAsset_JavascriptExt</span> <br /> </td> 
   <td> Biblioteca JS adicional para cargar en la actividad de flujo de trabajo "Notificaciones de recursos de marketing".<br /> </td> 
  </tr> 
 </tbody> 
</table>

## Seguridad {#security}

<table> 
 <thead> 
  <tr> 
   <th> Nombre de la opción </th> 
   <th> Descripción </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> <span class="uicontrol">XtkAcceptOldPasswords</span> <br /> </td> 
   <td> (Instalar modo de compatibilidad: build&gt;6000) Cuando se activa (valor "1"), esta opción permite el uso de contraseñas antiguas almacenadas en la base de datos para la conexión a cuentas externas o a la instancia.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkKey</span> <br /> </td> 
   <td> Esta clave se utiliza para cifrar la mayoría de las contraseñas de la base de datos. (cuentas externas, contraseña LDAP...).<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkSecurity_Allow_PrivilegeEscalation</span> <br /> </td> 
   <td> Si se selecciona 1, esta opción permite el privilegioEscalation en javascript.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkSecurity_Disable_ControlsOnFileDownload</span> <br /> </td> 
   <td> Si se selecciona 1, esta opción deshabilita los controles ACL durante una descarga de archivo (a través de fileDownload.jsp).<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkSecurity_Disable_JSFileSandboxing</span> <br /> </td> 
   <td> Si se selecciona 1, esta opción deshabilitará el entorno limitado del archivo en Javascript.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkSecurity_SaveOptions_AllowNonAdmin</span> <br /> </td> 
   <td> Si se establece en 'true', el operador no administrador autorizado actualizará los valores de xtkOption a través del asistente de implementación.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkSecurity_Unsafe_DecryptString</span> <br /> </td> 
   <td> Si se selecciona 1, esta opción permite utilizar decryptString para descifrar algunas contraseñas.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkTraceDeleteLogin</span> <br /> </td> 
   <td> Introduzca el valor "1" para rastrear la eliminación de elementos con información de pista de auditoría en mData, mediante la modificación de su campo "modificado por" antes de la eliminación del registro.<br /> </td> 
  </tr> 
 </tbody> 
</table>

## Centro de mensajes {#message-center}

<table> 
 <thead> 
  <tr> 
   <th> Nombre de la opción </th> 
   <th> Descripción </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> <span class="uicontrol">MC_EnrichmentCustomJs</span> <br /> </td> 
   <td> Biblioteca JavaScript que se personalizará para enriquecer eventos. Debe contener la implementación de estas dos funciones:<br /> 
    <ul> 
     <li> <p> <span class="uicontrol">enrichRtEvents(aiEventId);</span> : enriquece y guarda eventos en la base de datos (donde  <span class="uicontrol"></span> aiEventId corresponde a la tabla de eventos en tiempo real procesados).</p> </li> 
     <li> <p> <span class="uicontrol">enrichBatchEvents(aiEventId);</span> : enriquece y guarda eventos en la base de datos (donde  <span class="uicontrol"></span> aiEventId corresponde a la tabla de ID de eventos por lotes procesados).</p> </li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">MC_LastUpdateFromBL</span> <br /> </td> 
   <td> Fecha de la última actualización de estado del evento mediante registros de envío.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">MC_RoutingCustomJs</span> <br /> </td> 
   <td> Biblioteca JavaScript que se personalizará para los eventos de enrutamiento. Debe contener la implementación de estas dos funciones:<br /> 
    <ul> 
     <li> <p> <span class="uicontrol">patchRtEvent(iEventId);</span> : devuelve el nombre interno del mensaje transaccional seleccionado para procesar el evento en tiempo real (donde  <span class="uicontrol"></span> iEventId corresponde al ID del evento en tiempo real procesado).</p> </li> 
     <li> <p> <span class="uicontrol">shiftBatchEvent(iEventId);</span> : devuelve el nombre interno del mensaje transaccional seleccionado para procesar el evento por lotes (donde  <span class="uicontrol"></span> iEventId corresponde al ID del evento por lotes procesado).</p> </li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">MC_RtEventAvgDeliveryTimeAlert</span> <br /> </td> 
   <td> Umbral de alerta del tiempo de envío promedio de los eventos en tiempo real.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">MC_RtEventAvgDeliveryTimeWarning</span> <br /> </td> 
   <td> Umbral de advertencia para el tiempo de envío promedio de los eventos en tiempo real.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">MC_RtEventAvgProcessTimeAlert</span> <br /> </td> 
   <td> Umbral de alerta para el tiempo de procesamiento promedio de los eventos en tiempo real.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">MC_RtEventAvgProcessTimeWarning</span> <br /> </td> 
   <td> Umbral de advertencia para el tiempo de procesamiento promedio de los eventos en tiempo real.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">MC_RtEventAvgQueueAlert</span> <br /> </td> 
   <td> Umbral de alerta para el número promedio de eventos en tiempo real en cola.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">MC_RtEventAvgQueueTimeAlert</span> <br /> </td> 
   <td> Umbral de alerta para el tiempo de cola promedio de los eventos en tiempo real.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">MC_RtEventAvgQueueTimeWarning</span> <br /> </td> 
   <td> Umbral de advertencia para el tiempo de cola promedio de los eventos en tiempo real.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">MC_RtEventAvgQueueWarning</span> <br /> </td> 
   <td> Umbral de advertencia para el número promedio de eventos en tiempo real en cola.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">MC_RtEventErrorAlert</span> <br /> </td> 
   <td> Umbral de alerta para procesar errores de eventos en tiempo real.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">MC_RtEventErrorWarning</span> <br /> </td> 
   <td> Umbral de advertencia para procesar errores de eventos en tiempo real.<br /> </td> 
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
   <td> Umbral antes de la condición crítica para la cola de eventos en tiempo real pendientes.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">MC_RtEventQueueWarning</span> <br /> </td> 
   <td> Umbral antes de la advertencia para la cola de eventos en tiempo real pendientes.<br /> </td> 
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
   <td> Tamaño de la reagrupación para el enrutamiento del evento.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">MC_LastRtEventStat</span> <br /> </td> 
   <td> Actualice el puntero del estado de RtEvent (última fecha hasta el momento en que se recuperaron los datos).<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsLine_MessageCenterURL</span> <br /> </td> 
   <td> URL del servidor del centro de mensajes utilizada para enviar mensajes de bienvenida (canal LINE).<br /> </td> 
  </tr> 
 </tbody> 
</table>

## Database {#database}

<table> 
 <thead> 
  <tr> 
   <th> Nombre de la opción </th> 
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
   <td> <p>Permite definir el retraso tras el cual se borra el broadlog de la base de datos.</p><p>Esta opción se crea automáticamente una vez que se modifica el retraso dentro de la interfaz. Si modifica el valor de la lista de opciones, debe expresarse en segundos.</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsCleanup_EventHistoPurgeDelay</span> <br /> </td> 
   <td><p> Permite definir el retraso tras el cual se borra el historial de eventos de la base de datos.</p><p>
   Esta opción se crea automáticamente una vez que se modifica el retraso dentro de la interfaz. Si modifica el valor de la lista de opciones, debe expresarse en segundos.</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsCleanup_EventPurgeDelay</span> <br /> </td> 
   <td><p> Permite definir el retraso tras el cual se borran los eventos de la base de datos.</p><p>Esta opción se crea automáticamente una vez que se modifica el retraso dentro de la interfaz. Si modifica el valor de la lista de opciones, debe expresarse en segundos.</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsCleanup_EventStatPurgeDelay</span> <br /> </td> 
   <td><p> Permite definir el retraso tras el cual se borran las estadísticas de evento de la base de datos.</p><p>Esta opción se crea automáticamente una vez que se modifica el retraso dentro de la interfaz. Si modifica el valor de la lista de opciones, debe expresarse en segundos.</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsCleanup_PropositionPurgeDelay</span> <br /> </td> 
   <td><p> Permite definir el retraso tras el cual se borran las propuestas de la base de datos.</p><p> Esta opción se crea automáticamente una vez que se modifica el retraso dentro de la interfaz. Si modifica el valor de la lista de opciones, debe expresarse en segundos.</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsCleanup_QuarantineMailboxFull</span> <br /> </td> 
   <td> <p>Permite definir el retraso tras el cual se borran las cuarentenas de la base de datos.</p><p> Esta opción se crea automáticamente una vez que se modifica el retraso dentro de la interfaz. Si modifica el valor de la lista de opciones, debe expresarse en segundos.</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsCleanup_RecycledDeliveryPurgeDelay</span> <br /> </td> 
   <td> <p>Permite definir el retraso tras el cual se borran de la base de datos los envíos reciclados.</p><p> Esta opción se crea automáticamente una vez que se modifica el retraso dentro de la interfaz. Si modifica el valor de la lista de opciones, debe expresarse en segundos.</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsCleanup_RejectsPurgeDelay</span> <br /> </td> 
   <td> <p>Permite definir el retraso tras el cual se borran los rechazos de la base de datos.</p><p>Esta opción se crea automáticamente una vez que se modifica el retraso dentro de la interfaz. Si modifica el valor de la lista de opciones, debe expresarse en segundos.</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsCleanup_TrackingLogPurgeDelay</span> <br /> </td> 
   <td> <p>Permite definir el retraso tras el cual se borran los registros de seguimiento de la base de datos.</p><p>Esta opción se crea automáticamente una vez que se modifica el retraso dentro de la interfaz. Si modifica el valor de la lista de opciones, debe expresarse en segundos.</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsCleanup_TrackingStatPurgeDelay</span> <br /> </td> 
   <td><p> Permite definir el retraso tras el cual se borran las estadísticas de seguimiento de la base de datos.</p><p> Esta opción se crea automáticamente una vez que se modifica el retraso dentro de la interfaz. Si modifica el valor de la lista de opciones, debe expresarse en segundos.</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsCleanup_VisitorPurgeDelay</span> <br /> </td> 
   <td> <p>Permite definir el retraso tras el cual se borran los visitantes de la base de datos.</p><p> Esta opción se crea automáticamente una vez que se modifica el retraso dentro de la interfaz. Si modifica el valor de la lista de opciones, debe expresarse en segundos.</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsCleanup_WorkflowResultPurgeDelay</span> <br /> </td> 
   <td> <p>Permite definir el retraso tras el cual se borran los resultados del flujo de trabajo de la base de datos.</p><p> Esta opción se crea automáticamente una vez que se modifica el retraso dentro de la interfaz. Si modifica el valor de la lista de opciones, debe expresarse en segundos.</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">WdbcCapabilities_AzureDw</span> <br /> </td> 
   <td> Opciones del conector del almacén de datos SQL de Azure.<br /> </td> 
  </tr>
   <tr> 
   <td> <span class="uicontrol">WdbcKillSessionPolicy</span> <br /> </td> 
   <td>Permite afectar al comportamiento de detención incondicional en todos los flujos de trabajo y consultas de base de datos PostgreSQL según los siguientes valores posibles:<ul>
    <li><p>0: predeterminado: detiene el proceso del flujo de trabajo, sin afectar a la base de datos<p></li>
    <li><p>1 - pg_cancel_backend: detiene el proceso del flujo de trabajo y cancela la consulta en la base de datos<p></li>
    <li><p>2 - pg_terminate_backend: detiene el proceso de flujo de trabajo y finaliza la consulta en la base de datos<p></li></ul></td> 
  </tr>  
    <tr> 
   <td> <span class="uicontrol">WdbcOptions_TableSpaceUser</span> <br /> </td> 
   <td> Nombre del tablespace que va a contener los datos de las tablas ootb de Adobe Campaign.<br />Consulte  <a href="../../installation/using/creating-and-configuring-the-database.md">Creación y configuración de la base de datos</a>.</td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">WdbcOptions_TableSpaceIndex</span> <br /> </td> 
   <td> Nombre del tablespace destinado a contener los índices de las tablas ootb de Adobe Campaign.<br />Consulte  <a href="../../installation/using/creating-and-configuring-the-database.md">Creación y configuración de la base de datos</a>.</td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">WdbcOptions_TableSpaceWork</span> <br /> </td> 
   <td> Nombre del tablespace que va a contener los datos de las tablas de trabajo de Adobe Campaign.<br />Consulte  <a href="../../installation/using/creating-and-configuring-the-database.md">Creación y configuración de la base de datos</a>.</td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">WdbcOptions_TableSpaceWorkIndex</span> <br /> </td> 
   <td> Nombre del tablespace destinado a contener los índices de las tablas de trabajo de Adobe Campaign.<br />Consulte  <a href="../../installation/using/creating-and-configuring-the-database.md">Creación y configuración de la base de datos</a>.</td> 
  </tr> 
    <tr> 
   <td> <span class="uicontrol">WdbcOptions_TempDbName</span> <br /> </td> 
   <td> Permite configurar una base de datos independiente para tablas de trabajo en Microsoft SQL Server, a fin de optimizar las copias de seguridad y la replicación. La opción corresponde al nombre de la base de datos temporal: Si se especifica, las tablas de trabajo se escribirán en esta base de datos. Ejemplo: 'tempdb.dbo'. (tenga en cuenta que el nombre debe terminar con un punto). <a href="../../production/using/rdbms-specific-recommendations.md#microsoft-sql-server">Más información</a> <br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">WdbcTimeZone</span> <br /> </td> 
   <td> Zona horaria de la instancia de Adobe Campaign. Consulte <a href="../../installation/using/time-zone-management.md#configuration" target="_blank">Configuración</a>.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">WdbcUseNChar</span> <br /> </td> 
   <td> ¿Los campos de cadena de la base de datos están definidos con NChar?<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">WdbcUseTimeStampWithTZ</span> <br /> </td> 
   <td> ¿Los campos "datetime" de la base de datos almacenan información de zona horaria?<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkDatabaseId</span> <br /> </td> 
   <td> ID de la base de datos. Comienza por "u" para Base de datos Unicode.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkInstancePrefix</span> <br /> </td> 
   <td> Prefijo añadido a los nombres internos generado automáticamente.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkQuery_Schema_LineCount</span> <br /> </td> 
   <td> Número máximo de resultados devueltos por una consulta en xtk:schema y xtk:srcSchema.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkSequence_AutoGeneration</span> <br /> </td> 
   <td> Todos los esquemas personalizados, creados después de este tiempo, con autopk="true" y sin el atributo "pkSequence" obtendrán una secuencia autogenerada "auto_ 
    &lt;schemanamespace&gt; 
     &lt;schemaname&gt;
       _seq. 
   </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NlMigration_KeepFolderStructure</span> <br /> </td> 
   <td> Durante la migración, la estructura de árbol se reorganiza automáticamente según los nuevos estándares de versión.<br /> Esta opción le permite desactivar la migración automática del árbol de navegación. Si lo utiliza, después de la migración deberá eliminar las carpetas obsoletas, agregar las nuevas carpetas y ejecutar todas las comprobaciones necesarias.<br /> 
    <ul> 
     <li> <p> <span class="uicontrol">Tipo de datos: </span> entero</p> </li> 
     <li> <p> <span class="uicontrol">Valor (texto)</span> : 1 </p> </li> 
    </ul> Esta opción solo debe utilizarse si el árbol de navegación integrado ha sufrido demasiados cambios.<br /> Para obtener más información, consulte <a href="../../migration/using/specific-configurations-in-v5-11.md#campaign-vseven-tree-structure">esta sección</a>.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsLastErrorStatCoalesce</span> <br /> </td> 
   <td> Última fecha de procesamiento de la limpieza de tabla <span class="uicontrol">NmsEmailErrorStat</span>.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">PostUpgradeLastError</span> <br /> </td> 
   <td> Información sobre el error que se produjo en la actualización posterior, siguiendo la sintaxis siguiente:<br /> <strong>{Número de compilación}:{mode: pre/post/...}:{El 'lessThan'/'greaterOrEquelThan' donde se produjo el error + sub-step}</strong> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkCleanup_NoStats</span> <br /> </td> 
   <td> Introduzca el valor "1" para que la actualización de las estadísticas no se realice a través del flujo de trabajo de limpieza.<br /> </td> 
  </tr> 
 </tbody> 
</table>

## Integración {#integration}

<table> 
 <thead> 
  <tr> 
   <th> Nombre de la opción </th> 
   <th> Descripción </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> <span class="uicontrol">AEMResourceTypeFilter</span> <br /> </td> 
   <td> Tipos de recursos AEM que se pueden utilizar en Adobe Campaign. Los valores deben separarse con comas.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">nmsPipeline_config</span> <br /> </td> 
   <td> Permite configurar Déclencheur de Experience Cloud. El tipo de datos es "texto largo" y debe tener el formato JSON. Consulte <a class="anchorLink" href="https://helpx.adobe.com/campaign/kb/triggers-and-campaign.html#PipelineoptionNmsPipelineConfig" target="_blank">Uso de Déclencheur de Experience Cloud con Adobe Campaign Classic</a>.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">LASTIMPORT_&lt;%=instance.internalName%&gt;_&lt;%=activityName%&gt;</span> <br /> </td> 
   <td> Esta opción se utiliza al importar datos de un sistema de terceros a través de un conector CRM. La activación de la opción  solo permite recopilar objetos modificados desde la última importación. Esta opción debe crearse manualmente y rellenarse de la siguiente manera: 
    <ul> 
     <li> <p> <span class="uicontrol">Nombre</span>  interno: LASTIMPORT_&lt;&gt;_&lt;&gt;</p> </li> 
     <li> <p> <span class="uicontrol">Valor (campo)</span> : fecha de la última importación, con el formato aaaa/MM/dd hh:mm:ss . </p> </li> 
    </ul><br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">TNT_EdgeServer</span> <br /> </td> 
   <td> Servidor de Adobe Target utilizado para la integración. Esta opción está seleccionada de forma predeterminada. Este valor corresponde al Domain Server de Adobe Target, seguido del valor /m2. Por ejemplo: tt.omtrdc.net/m2.<br /> Consulte <a href="../../integrations/using/configuring-the-integration-with-adobe-target.md">esta sección</a>.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">TNT_TenantName</span> <br /> </td> 
   <td> Nombre de la organización de Adobe Target. Este valor corresponde al nombre de Client de Adobe Target.<br /> Consulte <a href="../../integrations/using/configuring-the-integration-with-adobe-target.md">esta sección</a>.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">AAM_DataSourceId</span> <br /> </td> 
   <td> Opción utilizada para la integración con Adobe Audience Manager.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">AAM_DestinationId</span> <br /> </td> 
   <td> Opción utilizada para la integración con Adobe Audience Manager.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">WdbcCapabilities_Teradata</span> <br /> </td> 
   <td> Opciones del conector de teradata.<br /> </td> 
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
   <th> Nombre de la opción </th> 
   <th> Descripción </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> <span class="uicontrol">NmsCoupons_MaxPerTransac</span> <br /> </td> 
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
   <td> Habilite/deshabilite la escritura asíncrona de propuestas ("0" para deshabilitar, "1" para habilitar).<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsModule_CouponsEnabled</span> <br /> </td> 
   <td> Permite habilitar los cupones.<br /> </td> 
  </tr> 
 </tbody> 
</table>

## Servidor {#server}

<table> 
 <thead> 
  <tr> 
   <th> Nombre de la opción </th> 
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
   <td> URL base interna para acceder al servidor de aplicaciones.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsServer_LastPostUpgrade</span> <br /> </td> 
   <td> Número de compilación de la instancia de AC antes de la última actualización.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsServer_URL</span> <br /> </td> 
   <td> URL base del servidor de aplicaciones web público.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkPassUnknownSQLFunctionsToRDBMS</span> <br /> </td> 
   <td> Permite seguir utilizando funciones SQL antiguas no declaradas después de migrar. Recomendamos encarecidamente no utilizar esta opción debido a los riesgos de seguridad que introduce.<br /> </td> 
  </tr> 
 </tbody> 
</table>

## Seguimiento {#tracking}

<table> 
 <thead> 
  <tr> 
   <th> Nombre de la opción </th> 
   <th> Descripción </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> <span class="uicontrol">NmsTracking_Available</span> <br /> </td> 
   <td> Opción que le permite activar el seguimiento.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsTracking_ClickFormula</span> <br /> </td> 
   <td> Secuencia de comandos de cálculo de URL rastreada.<br /> </td> 
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
   <td> <span class="uicontrol">NmsTracking_LastConsolidated</span> <br /> </td> 
   <td> La última vez que se consolidó la información de seguimiento con nuevos datos.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsTracking_OpenFormula</span> <br /> </td> 
   <td> Abra el script de cálculo de URL.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsTracking_Password</span> <br /> </td> 
   <td> Contraseña del servidor de seguimiento<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsTracking_Pointer</span> <br /> </td> 
   <td> El puntero realiza un seguimiento de los últimos eventos de mensaje que se procesaron a través de sus ID y fecha.<br /> </td> 
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
   <td> Lista de las direcciones URL utilizadas para comunicarse con los servidores de seguimiento.<br /> </td> 
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
   <td> Nombre del envío virtual diseñado para la administración del seguimiento web.<br /> </td> 
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
   <th> Nombre de la opción </th> 
   <th> Descripción </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> <span class="uicontrol">Privacy_Request_ConfirmDeletePending</span> <br /> </td> 
   <td> Si la opción 1 está seleccionada, debe confirmar manualmente la eliminación en la interfaz en un segundo paso. De lo contrario, los datos se eliminarán sin confirmación.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Privacy_Request_ConfirmDeletePendingDelay</span> <br /> </td> 
   <td> El retraso entre la solicitud espera para eliminar la confirmación y la solicitud se cancela.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Privacy_Request_MaxErrorAllowed</span> <br /> </td> 
   <td> Número máximo de errores permitidos al procesar o eliminar una solicitud de privacidad.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Privacy_Request_PurgeDelay</span> <br /> </td> 
   <td> El retraso entre la solicitud se crea en la cola y los datos de la solicitud se eliminan.<br /> </td> 
  </tr> 
 </tbody> 
</table>

## LDAP {#ldap}

<table> 
 <thead> 
  <tr> 
   <th> Nombre de la opción </th> 
   <th> Descripción </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> <span class="uicontrol">XtkLdap_Active</span> <br /> </td> 
   <td> Habilite el servidor LDAP para que se utilice para autenticar a los usuarios y proporcionar autorizaciones a los usuarios.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkLdap_AppLogin</span> <br /> </td> 
   <td> Inicio de sesión en la aplicación para ponerse en contacto con el servidor para realizar varias búsquedas.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkLdap_AppPassword</span> <br /> </td> 
   <td> Contraseña cifrada para el inicio de sesión de la aplicación.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkLdap_AutoOperator</span> <br /> </td> 
   <td> Habilite la creación automática de operadores y derechos en Adobe Campaign.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkLdap_DN</span> <br /> </td> 
   <td> Fórmula de cálculo para LDAP DN basada en el inicio de sesión.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkLdap_DNSearch</span> <br /> </td> 
   <td> Habilitar la búsqueda DN en el directorio.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkLdap_DNSearchBase</span> <br /> </td> 
   <td> Base de búsqueda.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkLdap_DNSearchFilter</span> <br /> </td> 
   <td> Filtro de búsqueda DN.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkLdap_DNSearchScope</span> <br /> </td> 
   <td> Ámbito de búsqueda.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkLdap_Facility</span> <br /> </td> 
   <td> Tipo de autenticación utilizado para ponerse en contacto con el servidor LDAP (plain, md5, lds, ntlm, dpa).<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkLdap_Rights</span> <br /> </td> 
   <td> Habilite la sincronización de autorizaciones y grupos desde el directorio LDAP a derechos asignados en Adobe Campaign.<br /> </td> 
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
   <td> Busque el filtro de autorizaciones de usuario.<br /> </td> 
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
   <td> <span class="uicontrol">XtkLdap_Server</span> <br /> </td> 
   <td> Dirección del servidor LDAP (es posible especificar un puerto especificando ':' como separador).<br /> </td> 
  </tr> 
 </tbody> 
</table>

## Formularios web {#web-forms}

<table> 
 <thead> 
  <tr> 
   <th> Nombre de la opción </th> 
   <th> Descripción </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> <span class="uicontrol">XtkUseScrollBar</span> <br /> </td> 
   <td> El valor establecido en 1 permitirá la adición de la barra de desplazamiento a los formularios detallados.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkWebForm_Instance</span> <br /> </td> 
   <td> Instancia que se utilizará para la invalidación de formularios web en el modo "otros servidores".<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkWebForm_Password</span> <br /> </td> 
   <td> Contraseña de la instancia que se utilizará para la invalidación de formularios web en el modo "otros servidores".<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkWebForm_ServersMode</span> <br /> </td> 
   <td> Opción que permite especificar el modo de invalidación de los formularios web: local de forma predeterminada, utiliza servidores de seguimiento si la opción es 'tracking' y utiliza una lista personalizada con la opción 'other server(s)'.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkWebForm_ServersURLs</span> <br /> </td> 
   <td> Lista de direcciones personalizadas con los servidores a los que se debe contactar para la invalidación de formularios web (modo "otros servidores").<br /> </td> 
  </tr> 
 </tbody> 
</table>
