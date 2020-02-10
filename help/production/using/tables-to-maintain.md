---
title: Tablas para mantener
seo-title: Tablas para mantener
description: Tablas para mantener
seo-description: null
page-status-flag: never-activated
uuid: 1085e929-65cc-48fa-9c31-0508a14b4704
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: production
content-type: reference
topic-tags: database-maintenance
discoiquuid: 6ec4e566-7116-4d7f-835d-cb0f3c3a6a7a
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 579329d9194115065dff2c192deb0376c75e67bd

---


# Tablas para mantener{#tables-to-maintain}

La lista de tablas que se deben mantener depende de la versión de Adobe Campaign, de cómo se utilice y de la configuración del modelo de datos.

La siguiente lista contiene sólo las tablas más sujetas a fragmentación. Los efectos son los siguientes:

* consumo excesivo de espacio en disco, lo que afecta al acceso a la base de datos,
* índices que no se han actualizado regularmente, lo que ralentiza el rendimiento de la consulta.

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
   <td> Hay un registro por acción de envío. Un único registro se puede actualizar varias veces para reflejar el progreso de la entrega, por lo que los índices de esta tabla tienden a fragmentarse rápidamente. <br /> </td> 
  </tr> 
  <tr> 
   <td> NmsDeliveryPart<br /> </td> 
   <td> Medio<br /> </td> 
   <td> Inserciones, actualizaciones, eliminaciones<br /> </td> 
   <td> Tabla de trabajo en la que se insertan los registros durante la preparación de la entrega. Después se actualizan durante la entrega y se eliminan una vez finalizada la entrega.<br /> Esta tabla tiende a fragmentarse rápidamente aunque su tamaño promedio sea bastante limitado.<br /> </td> 
  </tr> 
  <tr> 
   <td> NmsMirrorPageInfo<br /> </td> 
   <td> Grande<br /> </td> 
   <td> Inserciones, eliminaciones<br /> </td> 
   <td> Esta tabla contiene la información necesaria para generar páginas reflejadas personalizadas. Contiene un campo memo (CLOB), y como tal tenderá a ser muy grande. El volumen es directamente proporcional al historial de las páginas reflejadas conservadas. <br /> </td> 
  </tr> 
  <tr> 
   <td> NmsDeliveryStat<br /> </td> 
   <td> Medio<br /> </td> 
   <td> Inserciones, actualizaciones, eliminaciones<br /> </td> 
   <td> Esta tabla contiene estadísticas sobre el proceso de entrega. Sus registros se actualizan periódicamente. <br /> </td> 
  </tr> 
  <tr> 
   <td> NmsAddress<br /> </td> 
   <td> Medio<br /> </td> 
   <td> Actualizaciones, inserciones<br /> </td> 
   <td> Esta tabla contiene información sobre las direcciones de correo electrónico. Se actualiza con frecuencia como parte del proceso de cuarentena (los registros se crean en el primer error de entrega, se actualizan cuando los contadores cambian y se eliminan una vez que la entrega se realiza correctamente). <br /> </td> 
  </tr> 
  <tr> 
   <td> XtkWorkflow<br /> </td> 
   <td> Pequeño<br /> </td> 
   <td> Actualizaciones<br /> </td> 
   <td> Hay un registro por instancia de flujo de trabajo, por lo que hay muy pocos registros. Sin embargo, la tabla se actualiza periódicamente para reflejar el estado y el progreso.<br /> </td> 
  </tr> 
  <tr> 
   <td> XtkWorkflowTask<br /> </td> 
   <td> Pequeño<br /> </td> 
   <td> Inserciones, actualizaciones, eliminaciones<br /> </td> 
   <td> Cada ejecución de una actividad de flujo de trabajo lleva a la creación de un registro en esta tabla. El mecanismo de purga los elimina una vez caducados.<br /> </td> 
  </tr> 
  <tr> 
   <td> XtkWorkflowEvent<br /> </td> 
   <td> Pequeño<br /> </td> 
   <td> Inserciones, actualizaciones, eliminaciones<br /> </td> 
   <td> Cada transición activada entre tareas de un flujo de trabajo lleva a la creación de un registro en esta tabla. El mecanismo de purga los elimina una vez caducados. <br /> </td> 
  </tr> 
  <tr> 
   <td> XtkWorkflowJob<br /> </td> 
   <td> Muy pequeño <br /> </td> 
   <td> Inserciones, actualizaciones, eliminaciones<br /> </td> 
   <td> Esta tabla es específica del motor de flujo de trabajo. Permite el envío de comandos a flujos de trabajo (por ejemplo, Inicio, Detener, Pausa). Aunque es pequeña, esta tabla se tiene en cuenta durante la purga de tablas transaccionales vinculadas a flujos de trabajo.<br /> </td> 
  </tr> 
  <tr> 
   <td> NmsBroadLog<br /> </td> 
   <td> Más grande<br /> </td> 
   <td> Inserciones, actualizaciones, eliminaciones<br /> </td> 
   <td> Ésta es la tabla más grande del sistema. Hay un registro por mensaje enviado y estos registros se insertan, actualizan para realizar un seguimiento del estado de entrega y se eliminan al depurar el historial. <br /> </td> 
  </tr> 
  <tr> 
   <td> NmsTrackingLog<br /> </td> 
   <td> Grande<br /> </td> 
   <td> Inserciones, eliminaciones<br /> </td> 
   <td> Los registros de seguimiento se insertan y eliminan cuando se depura el historial, pero no se actualizan. <br /> </td> 
  </tr> 
  <tr> 
   <td> NmsBroadlogMsg <br /> </td> 
   <td> Pequeño<br /> </td> 
   <td> Actualizaciones<br /> </td> 
   <td> Esta tabla contiene información utilizada para calificar los errores SMTP. Es bastante pequeño, pero se actualizará masivamente, por lo que los índices de esta tabla tienden a fragmentarse rápidamente. <br /> </td> 
  </tr> 
  <tr> 
   <td> NmsEmailErrorStat<br /> </td> 
   <td> Medio<br /> </td> 
   <td> Inserciones, actualizaciones, eliminaciones<br /> </td> 
   <td> Esta tabla contiene los agregados de los errores SMTP ordenados por dominio. En un principio contiene información detallada que se agrega mediante la tarea de limpieza una vez que se ha desactualizado. <br /> </td> 
  </tr> 
  <tr> 
   <td> NmsBroadLogMid (en una instancia de abastecimiento intermedio)<br /> </td> 
   <td> Grande<br /> </td> 
   <td> Inserciones, actualizaciones, eliminaciones<br /> </td> 
   <td> Solo cuando se utiliza la instancia 5.10 (o posterior) como instancia de abastecimiento intermedio. Ésta es una de las tablas más grandes de la base de datos. Hay un registro por mensaje enviado y estos registros se insertan, actualizan para realizar un seguimiento del estado de entrega y se eliminan al depurar el historial. Cuando se utiliza la contratación intermedia, la recomendación es limitar el historial (generalmente menos de dos meses), por lo que esta tabla sigue siendo razonable en términos de tamaño (menos de 30 Go por 60 millones de filas, datos+índice), pero es muy importante reconstruirla de vez en cuando. <br /> </td> 
  </tr> 
  <tr> 
   <td> NmsBroadLogRcp (cuando se utiliza la tabla NmsRecipient) <br /> </td> 
   <td> Grande<br /> </td> 
   <td> Inserciones, actualizaciones, eliminaciones<br /> </td> 
   <td> Ésta es la tabla más grande del sistema. Hay un registro por mensaje enviado y estos registros se insertan, actualizan para realizar un seguimiento del estado de entrega y se eliminan al depurar el historial. Tenga en cuenta que en 5.10, esta tabla es más pequeña que el equivalente en 4.05 (NmsBroadLog), ya que el texto del mensaje SMTP se factoriza en la tabla NmsBroadLogMsg de la versión 5.10. Sin embargo, sigue siendo esencial volver a indexar esta tabla con regularidad (para empezar, cada dos semanas) y reconstruirla completamente de vez en cuando (una vez al mes o cuando el rendimiento se ve afectado). <br /> </td> 
  </tr> 
  <tr> 
   <td> AAAABroadLogXxx (cuando se utiliza una tabla de destinatarios externa)<br /> </td> 
   <td> Grande<br /> </td> 
   <td> Inserciones, actualizaciones, eliminaciones<br /> </td> 
   <td> Igual que NmsBroadLogRcp pero con una tabla de destinatarios externa. Adapte AAAA y Xxx con los valores de la asignación de entrega. <br /> </td> 
  </tr> 
  <tr> 
   <td> NmsTrackingLogRcp (cuando se utiliza la tabla NmsRecipient) <br /> </td> 
   <td> Grande<br /> </td> 
   <td> Inserciones, eliminaciones<br /> </td> 
   <td> Los registros de seguimiento se insertan y eliminan cuando se depura el historial, pero no se actualizan. El volumen depende de la duración de la retención de datos. <br /> </td> 
  </tr> 
  <tr> 
   <td> AAAATrackingLogXxx (cuando se utiliza la tabla de destinatarios externos)<br /> </td> 
   <td> Grande<br /> </td> 
   <td> Inserciones, eliminaciones<br /> </td> 
   <td> Igual que NmsTrackingLogRcp pero con una tabla de destinatarios externa. Adapte AAAA y Xxx con los valores utilizados en la asignación de entregas. <br /> </td> 
  </tr> 
  <tr> 
   <td> NmsBroadLogRtEvent (instancia de ejecución de Message Center)<br /> </td> 
   <td> Grande<br /> </td> 
   <td> Inserciones, actualizaciones, eliminaciones<br /> </td> 
   <td> Es similar a las otras tablas de registro extensivo, pero con NmsRtEvent en lugar de NmsRecipient.<br /> </td> 
  </tr> 
  <tr> 
   <td> NmsTrackingLogRtEvent( instancia de ejecución de Message Center)<br /> </td> 
   <td> Grande<br /> </td> 
   <td> Inserciones, eliminaciones<br /> </td> 
   <td> Similar a las otras tablas trackingLog, pero con la tabla NmsRtEvent en lugar de NmsRecipient.<br /> </td> 
  </tr> 
  <tr> 
   <td> NmsRtEvent (instancia de ejecución de Message Center)<br /> </td> 
   <td> Grande<br /> </td> 
   <td> Inserciones, actualizaciones, eliminaciones<br /> </td> 
   <td> Tabla que contiene la cola de eventos del centro de mensajes. El centro de mensajes actualiza el estado de estos eventos a medida que se procesan. Las eliminaciones se realizan durante la purga. Le recomendamos que vuelva a crear regularmente el índice de esta tabla y vuelva a crearlo.<br /> </td> 
  </tr> 
  <tr> 
   <td> NmsEventHisto (instancia de control del centro de mensajes)<br /> </td> 
   <td> Grande<br /> </td> 
   <td> Inserciones, actualizaciones, eliminaciones<br /> </td> 
   <td> Similar a NmsRtEvent. Esta tabla archiva todos los eventos de todas las instancias de ejecución. No se utiliza en ningún proceso en tiempo real, solo en los informes.<br /> </td> 
  </tr> 
  <tr> 
   <td> NmsMobileApp<br /> </td> 
   <td> Muy pequeño<br /> </td> 
   <td> Inserciones, actualizaciones, eliminaciones<br /> </td> 
   <td> Tablas que incluyen aplicaciones móviles y su configuración.<br /> </td> 
  </tr> 
  <tr> 
   <td> NmsAppSubscriptionRcp<br /> </td> 
   <td> Grande<br /> </td> 
   <td> Inserciones, actualizaciones<br /> </td> 
   <td> Tabla que incluye los identificadores de dispositivos móviles (direcciones) utilizados para enviar la notificación (similar a una tabla de destinatarios).<br /> </td> 
  </tr> 
  <tr> 
   <td> NmsBroadLogAppSubRcp<br /> </td> 
   <td> Grande<br /> </td> 
   <td> Inserciones, actualizaciones, eliminaciones<br /> </td> 
   <td> Similar a las otras tablas de registro masivo, pero con NmsappSubscriptionRcp en lugar de NmsRecipient.<br /> </td> 
  </tr> 
  <tr> 
   <td> NmsTrackingLogAppSubRcp<br /> </td> 
   <td> Grande<br /> </td> 
   <td> Inserciones, eliminaciones<br /> </td> 
   <td> Similar a las otras tablas trackingLog, pero con la tabla NmsappSubscriptionRcp en lugar de NmsRecipient.<br /> </td> 
  </tr> 
  <tr> 
   <td> XtkSessionInfo<br /> </td> 
   <td> Pequeño<br /> </td> 
   <td> Inserciones, eliminaciones<br /> </td> 
   <td> Tabla que incluye sesiones de usuario. El número de inserciones y eliminaciones es muy importante.<br /> </td> 
  </tr> 
 </tbody> 
</table>

## Tablas del cliente {#customer-tables}

Además de la lista anterior, las tablas que contienen datos creados por clientes (que no existen en el modelo de datos de Adobe Campaign) durante la configuración de la plataforma también pueden estar sujetas a fragmentación, especialmente si se actualizan con frecuencia durante los procedimientos de sincronización o carga de datos. Estas tablas pueden formar parte del modelo de datos predeterminado de Adobe Campaign (por ejemplo, **NmsRecipient**). En este caso, corresponde al administrador de la plataforma Adobe Campaign realizar una auditoría de su modelo de base de datos específico para encontrar estas tablas personalizadas. Estas tablas no necesariamente se mencionan explícitamente en nuestros procedimientos de mantenimiento.
