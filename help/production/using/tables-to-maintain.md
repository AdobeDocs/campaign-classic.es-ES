---
product: campaign
title: Tablas que mantener
description: Tablas que mantener
feature: Monitoring
badge-v7-prem: label="Solo local/híbrido" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=es" tooltip="Se aplica solo a implementaciones On-premise e híbridas"
audience: production
content-type: reference
topic-tags: database-maintenance
exl-id: 194f12de-4671-4a56-8cdc-cd5e3dac147b
source-git-commit: 14ba450ebff9bba6a36c0df07d715b7279604222
workflow-type: tm+mt
source-wordcount: '1140'
ht-degree: 1%

---

# Tablas que mantener{#tables-to-maintain}



La lista de tablas que mantener depende de la versión de Adobe Campaign, de cómo se utilice y de la configuración del modelo de datos.

La siguiente lista contiene únicamente las tablas que están más sujetas a fragmentación. Los impactos son los siguientes:

* consumo excesivo de espacio en disco, lo que afecta al acceso a la base de datos,
* índices que no se han actualizado regularmente, lo que ralentiza el rendimiento de las consultas.

## Tablas de Adobe Campaign {#adobe-campaign-tables}

<table> 
 <thead> 
  <tr> 
   <th> <strong>Nombre de tabla </strong><br /> </th> 
   <th> <strong>Tamaño</strong><br /> </th> 
   <th> <strong>Tipo principal de actividad</strong><br /> </th> 
   <th> <strong>Comentarios</strong><br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> NmsDelivery<br /> </td> 
   <td> Pequeño<br /> </td> 
   <td> Actualizaciones<br /> </td> 
   <td> Hay un registro por acción de envío. Un solo registro se puede actualizar varias veces para reflejar el progreso de la entrega, por lo que los índices de esta tabla tienden a fragmentarse rápidamente. <br /> </td> 
  </tr> 
  <tr> 
   <td> NmsDeliveryPart<br /> </td> 
   <td> Mediana<br /> </td> 
   <td> Inserciones, actualizaciones y eliminaciones<br /> </td> 
   <td> Tabla de trabajo en la que se insertan los registros durante la preparación de la entrega. A continuación, se actualizan durante la entrega y, finalmente, se eliminan una vez finalizada la entrega.<br /> Esta tabla tiende a fragmentarse rápidamente aunque su tamaño medio sea bastante limitado.<br /> </td> 
  </tr> 
  <tr> 
   <td> NmsMirrorPageInfo<br /> </td> 
   <td> Grande<br /> </td> 
   <td> Inserciones y eliminaciones<br /> </td> 
   <td> Esta tabla contiene la información necesaria para generar páginas espejo personalizadas. Contiene un campo memo (CLOB) y, como tal, tiende a ser muy grande. El volumen es directamente proporcional al historial de páginas espejo conservadas. <br /> </td> 
  </tr> 
  <tr> 
   <td> NmsDeliveryStat<br /> </td> 
   <td> Mediana<br /> </td> 
   <td> Inserciones, actualizaciones y eliminaciones<br /> </td> 
   <td> Esta tabla contiene estadísticas sobre el proceso de envío. Sus registros se actualizan periódicamente. <br /> </td> 
  </tr> 
  <tr> 
   <td> NmsAddress<br /> </td> 
   <td> Mediana<br /> </td> 
   <td> Actualizaciones e inserciones<br /> </td> 
   <td> Esta tabla contiene información sobre las direcciones de correo electrónico. Se actualiza con frecuencia como parte del proceso de cuarentena (los registros se crean en el primer error de entrega, se actualizan cuando los contadores cambian y se eliminan una vez que la entrega se realiza correctamente). <br /> </td> 
  </tr> 
  <tr> 
   <td> XtkWorkflow<br /> </td> 
   <td> Pequeño<br /> </td> 
   <td> Actualizaciones<br /> </td> 
   <td> Hay un registro por instancia de flujo de trabajo, por lo que hay muy pocos registros. Sin embargo, la tabla se actualiza regularmente para reflejar el estado y el progreso.<br /> </td> 
  </tr> 
  <tr> 
   <td> XtkWorkflowTask<br /> </td> 
   <td> Pequeño<br /> </td> 
   <td> Inserciones, actualizaciones y eliminaciones<br /> </td> 
   <td> Cada ejecución de una actividad de flujo de trabajo lleva a la creación de un registro en esta tabla. El mecanismo de depuración los elimina una vez que han caducado.<br /> </td> 
  </tr> 
  <tr> 
   <td> XtkWorkflowEvent<br /> </td> 
   <td> Pequeño<br /> </td> 
   <td> Inserciones, actualizaciones y eliminaciones<br /> </td> 
   <td> Cada transición activada entre las tareas de un flujo de trabajo lleva a la creación de un registro en esta tabla. El mecanismo de depuración los elimina una vez que han caducado. <br /> </td> 
  </tr> 
  <tr> 
   <td> XtkWorkflowJob<br /> </td> 
   <td> Muy pequeño <br /> </td> 
   <td> Inserciones, actualizaciones y eliminaciones<br /> </td> 
   <td> Esta tabla es específica del motor de flujo de trabajo. Permite enviar comandos a flujos de trabajo (por ejemplo, Start, Stop, Pause). Aunque es pequeña, esta tabla se tiene en cuenta durante la depuración de tablas transaccionales vinculadas a flujos de trabajo.<br /> </td> 
  </tr> 
  <tr> 
   <td> NmsBroadLog<br /> </td> 
   <td> Mayor<br /> </td> 
   <td> Inserciones, actualizaciones y eliminaciones<br /> </td> 
   <td> Esta es la tabla más grande del sistema. Hay un registro por mensaje enviado y estos registros se insertan, actualizan para rastrear el estado de envío y se eliminan cuando se purga el historial. <br /> </td> 
  </tr> 
  <tr> 
   <td> NmsTrackingLog<br /> </td> 
   <td> Grande<br /> </td> 
   <td> Inserciones y eliminaciones<br /> </td> 
   <td> Los registros de seguimiento se insertan y eliminan cuando se purga el historial, pero no se actualizan. <br /> </td> 
  </tr> 
  <tr> 
   <td> NmsBroadlogMsg <br /> </td> 
   <td> Pequeño<br /> </td> 
   <td> Actualizaciones<br /> </td> 
   <td> Esta tabla contiene información utilizada para calificar errores de SMTP. Es bastante pequeño, pero se actualizará masivamente, por lo que los índices de esta tabla tienden a fragmentarse rápidamente. <br /> </td> 
  </tr> 
  <tr> 
   <td> NmsEmailErrorStat<br /> </td> 
   <td> Mediana<br /> </td> 
   <td> Inserciones, actualizaciones y eliminaciones<br /> </td> 
   <td> Esta tabla contiene los agregados de los errores SMTP ordenados por dominio. Inicialmente contiene información detallada que añade la tarea de limpieza una vez que queda obsoleta. <br /> </td> 
  </tr> 
  <tr> 
   <td> NmsBroadLogMid (en una instancia intermediaria)<br /> </td> 
   <td> Grande<br /> </td> 
   <td> Inserciones, actualizaciones y eliminaciones<br /> </td> 
   <td> Solo cuando la instancia 5.10 (o posterior) se utiliza como instancia intermediaria. Esta es una de las tablas más grandes de la base de datos. Hay un registro por mensaje enviado y estos registros se insertan, actualizan para rastrear el estado de envío y se eliminan cuando se purga el historial. Al utilizar intermediarios, la recomendación es limitar el historial (normalmente menos de dos meses), por lo que esta tabla sigue siendo razonable en términos de tamaño (menos de 30 Go para 60 millones de filas, data+index), pero es muy importante reconstruirla de vez en cuando. <br /> </td> 
  </tr> 
  <tr> 
   <td> NmsBroadLogRcp (cuando se utiliza la tabla NmsRecipient) <br /> </td> 
   <td> Grande<br /> </td> 
   <td> Inserciones, actualizaciones y eliminaciones<br /> </td> 
   <td> Esta es la tabla más grande del sistema. Hay un registro por mensaje enviado y estos registros se insertan, actualizan para rastrear el estado de envío y se eliminan cuando se purga el historial. Tenga en cuenta que en 5.10, esta tabla es más pequeña que el equivalente en 4.05 (NmsBroadLog), ya que el texto del mensaje SMTP se factoriza en la tabla NmsBroadLogMsg en la versión 5.10. Sin embargo, sigue siendo esencial reindexar esta tabla regularmente (cada dos semanas para empezar) y reconstruirla completamente de vez en cuando (una vez al mes o cuando el rendimiento se vea afectado). <br /> </td> 
  </tr> 
  <tr> 
   <td> YyyBroadLogXxx (cuando se utiliza una tabla de destinatarios externa)<br /> </td> 
   <td> Grande<br /> </td> 
   <td> Inserciones, actualizaciones y eliminaciones<br /> </td> 
   <td> Igual que NmsBroadLogRcp, pero con una tabla de destinatarios externa. Adapte Yyy y Xxx con los valores de la asignación de envíos. <br /> </td> 
  </tr> 
  <tr> 
   <td> NmsTrackingLogRcp (cuando se utiliza la tabla NmsRecipient) <br /> </td> 
   <td> Grande<br /> </td> 
   <td> Inserciones y eliminaciones<br /> </td> 
   <td> Los registros de seguimiento se insertan y eliminan cuando se purga el historial, pero no se actualizan. El volumen depende de la duración de la retención de datos. <br /> </td> 
  </tr> 
  <tr> 
   <td> YyyTrackingLogXxx (cuando se utiliza la tabla de destinatarios externa)<br /> </td> 
   <td> Grande<br /> </td> 
   <td> Inserciones y eliminaciones<br /> </td> 
   <td> Igual que NmsTrackingLogRcp, pero con una tabla de destinatarios externa. Adapte Yyy y Xxx con los valores utilizados en la asignación de envíos. <br /> </td> 
  </tr> 
  <tr> 
   <td> NmsBroadLogRtEvent (instancia de ejecución del centro de mensajes)<br /> </td> 
   <td> Grande<br /> </td> 
   <td> Inserciones, actualizaciones y eliminaciones<br /> </td> 
   <td> Similar a las otras tablas de broadlog, pero con NmsRtEvent en lugar de NmsRecipient.<br /> </td> 
  </tr> 
  <tr> 
   <td> NmsTrackingLogRtEvent( instancia de ejecución del centro de mensajes)<br /> </td> 
   <td> Grande<br /> </td> 
   <td> Inserciones y eliminaciones<br /> </td> 
   <td> Similar a las otras tablas trackingLog, pero con la tabla NmsRtEvent en lugar de NmsRecipient.<br /> </td> 
  </tr> 
  <tr> 
   <td> NmsRtEvent (instancia de ejecución del centro de mensajes)<br /> </td> 
   <td> Grande<br /> </td> 
   <td> Inserciones, actualizaciones y eliminaciones<br /> </td> 
   <td> Tabla que contiene la cola de eventos del Centro de mensajes. El centro de mensajes actualiza el estado de estos eventos a medida que se procesan. Las eliminaciones se realizan durante la depuración. Le recomendamos que vuelva a crear con regularidad el índice de esta tabla y que la reconstruya.<br /> </td> 
  </tr> 
  <tr> 
   <td> NmsEventHisto (instancia de control del centro de mensajes)<br /> </td> 
   <td> Grande<br /> </td> 
   <td> Inserciones, actualizaciones y eliminaciones<br /> </td> 
   <td> Similar a NmsRtEvent. Esta tabla archiva todos los eventos de todas las instancias de ejecución. No se utiliza en procesos en tiempo real, solo en informes.<br /> </td> 
  </tr> 
  <tr> 
   <td> NmsMobileApp<br /> </td> 
   <td> Muy pequeño<br /> </td> 
   <td> Inserciones, actualizaciones y eliminaciones<br /> </td> 
   <td> Tablas que incluyen aplicaciones móviles y su configuración.<br /> </td> 
  </tr> 
  <tr> 
   <td> NmsAppSubscriptionRcp<br /> </td> 
   <td> Grande<br /> </td> 
   <td> Inserciones y actualizaciones<br /> </td> 
   <td> Tabla que incluye los identificadores de dispositivos móviles (direcciones) utilizados para enviar la notificación (similar a una tabla de destinatarios).<br /> </td> 
  </tr> 
  <tr> 
   <td> NmsBroadLogAppSubRcp<br /> </td> 
   <td> Grande<br /> </td> 
   <td> Inserciones, actualizaciones y eliminaciones<br /> </td> 
   <td> Similar a las otras tablas de broadlog, pero con NmsappSubscriptionRcp en lugar de NmsRecipient.<br /> </td> 
  </tr> 
  <tr> 
   <td> NmsTrackingLogAppSubRcp<br /> </td> 
   <td> Grande<br /> </td> 
   <td> Inserciones y eliminaciones<br /> </td> 
   <td> Similar a las otras tablas trackingLog, pero con la tabla NmsappSubscriptionRcp en lugar de NmsRecipient.<br /> </td> 
  </tr> 
  <tr> 
   <td> XtkSessionInfo<br /> </td> 
   <td> Pequeño<br /> </td> 
   <td> Inserciones y eliminaciones<br /> </td> 
   <td> Tabla que incluye sesiones de usuario. El número de inserciones y eliminaciones es muy importante.<br /> </td> 
  </tr> 
 </tbody> 
</table>

## Tablas de clientes {#customer-tables}

Además de la lista anterior, las tablas que contienen creadas por clientes (que no existen en el modelo de datos de Adobe Campaign) durante la configuración de la plataforma también pueden estar sujetas a fragmentación, especialmente si se actualizan con frecuencia durante los procedimientos de carga o sincronización de datos. Estas tablas pueden formar parte del modelo de datos predeterminado de Adobe Campaign (por ejemplo, **NmsRecipient**). En este caso, es responsabilidad del administrador de la plataforma de Adobe Campaign realizar una auditoría de su modelo de base de datos específico para encontrar estas tablas personalizadas. Estas tablas no se mencionan necesariamente explícitamente en nuestros procedimientos de mantenimiento.
