---
product: campaign
title: Flujo de trabajo para limpieza de bases de datos
description: Descubra cómo se limpian automáticamente los datos obsoletos
feature: Monitoring, Workflows
badge-v7-only: label="v7" type="Informative" tooltip="Solo se aplica a Campaign Classic v7"
audience: production
content-type: reference
topic-tags: data-processing
exl-id: 75d3a0af-9a14-4083-b1da-2c1b22f57cbe
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: tm+mt
source-wordcount: '2830'
ht-degree: 1%

---

# Flujo de trabajo para limpieza de bases de datos{#database-cleanup-workflow}



## Introducción {#introduction}

El **[!UICONTROL Database cleanup]** flujo de trabajo accesible a través de **[!UICONTROL Administration > Production > Technical workflows]** , permite eliminar datos obsoletos para evitar el crecimiento exponencial de la base de datos. El flujo de trabajo se activa automáticamente sin intervención del usuario.

![cleanup](assets/ncs_cleanup_workflow.png)

## Configuración {#configuration}

La limpieza de la base de datos se configura en dos niveles: en el programador de flujo de trabajo y en el asistente de implementación.

### Planificador de flujo de trabajo {#the-scheduler}

>[!NOTE]
>
>Para obtener más información sobre el planificador, consulte [esta sección](../../workflow/using/scheduler.md).

De forma predeterminada, la variable **[!UICONTROL Database cleanup]** El flujo de trabajo de está configurado para iniciarse diariamente a las 4 de la mañana. El planificador permite cambiar la frecuencia de activación del flujo de trabajo. Las frecuencias disponibles son las siguientes:

* **[!UICONTROL Several times a day]**
* **[!UICONTROL Daily]**
* **[!UICONTROL Weekly]**
* **[!UICONTROL Once]**

![planificador](assets/ncs_cleanup_scheduler.png)

>[!IMPORTANT]
>
>Para que la **[!UICONTROL Database cleanup]** flujo de trabajo para comenzar en la fecha y hora definidas en el planificador, se debe iniciar el motor de flujo de trabajo (wfserver).

### Asistente de implementación {#deployment-wizard}

El **[!UICONTROL Deployment wizard]**, a través de **[!UICONTROL Tools > Advanced]** , permite configurar durante cuánto tiempo se guardan los datos. Los valores se expresan en días. Si estos valores no se modifican, el flujo de trabajo utilizará los valores predeterminados.

![](assets/ncs_cleanup_deployment-wizard.png)

Los campos del **[!UICONTROL Purge of data]** coincide con las siguientes opciones. Las utilizan algunas de las tareas ejecutadas por **[!UICONTROL Database cleanup]** flujo de trabajo:

* Seguimiento consolidado: **NmsCleanup_TrackingStatPurgeDelay** (consulte [Limpieza de registros de seguimiento](#cleanup-of-tracking-logs))
* Registros de envío: **NmsCleanup_BroadLogPurgeDelay** (consulte [Limpieza de registros de envío](#cleanup-of-delivery-logs))
* Registros de seguimiento: **NmsCleanup_TrackingLogPurgeDelay** (consulte [Limpieza de registros de seguimiento](#cleanup-of-tracking-logs))
* Envíos eliminados: **NmsCleanup_RecycledDeliveryPurgeDelay** (consulte [Limpieza de los envíos que se van a eliminar o reciclar](#cleanup-of-deliveries-to-be-deleted-or-recycled))
* Importar rechazos: **NmsCleanup_RejectsPurgeDelay** (consulte [Limpieza de rechazos generados por importaciones](#cleanup-of-rejects-generated-by-imports-))
* Perfiles de visitantes: **NmsCleanup_VisitorPurgeDelay** (consulte [Limpieza de visitantes](#cleanup-of-visitors))
* Propuestas de oferta: **NmsCleanup_PropositionPurgeDelay** (consulte [Limpieza de propuestas](#cleanup-of-propositions))

  >[!NOTE]
  >
  >El **[!UICONTROL Offer propositions]** El campo solo está disponible cuando la variable **Interacción** El módulo de está instalado.

* Eventos: **NmsCleanup_EventPurgeDelay** (consulte [Limpieza de eventos caducados](#cleansing-expired-events))
* Eventos archivados: **NmsCleanup_EventHistoPurgeDelay** (consulte [Limpieza de eventos caducados](#cleansing-expired-events))

  >[!NOTE]
  >
  >El **[!UICONTROL Events]** y **[!UICONTROL Archived events]** Los campos de solo están disponibles si **Centro de mensajes** El módulo de está instalado.

* Pista de auditoría: **XtkCleanup_AuditTrailPurgeDelay** (consulte [Limpieza de la pista de auditoría](#cleanup-of-audit-trail))

Todas las tareas ejecutadas por **[!UICONTROL Database cleanup]** flujo de trabajo se describen en la siguiente sección.

## Tareas realizadas por el flujo de trabajo Database cleanup {#tasks-carried-out-by-the-database-cleanup-workflow}

En la fecha y hora definidas en el planificador del flujo de trabajo (consulte [El planificador](#the-scheduler)), el motor de flujo de trabajo inicia el proceso de limpieza de la base de datos. Database cleanup se conecta a la base de datos y ejecuta las tareas en la secuencia que se muestra a continuación.

>[!IMPORTANT]
>
>Si falla una de estas tareas, no se ejecutan las siguientes.
>
>Consultas SQL con un **LIMITAR** se ejecutan repetidamente hasta que se procesa toda la información.


### Listas para eliminar la limpieza {#lists-to-delete-cleanup}

La primera tarea ejecutada por **[!UICONTROL Database cleanup]** el flujo de trabajo elimina todos los grupos con **deleteStatus!= 0** atributo del **NmsGroup**. También se eliminan los registros vinculados a estos grupos y que existen en otras tablas.

1. Las listas que se van a eliminar se recuperan mediante la siguiente consulta SQL:

   ```sql
   SELECT iGroupId, sLabel, iType FROM NmsGroup WHERE iDeleteStatus <> 0 OR tsExpirationDate <= GetDate() 
   ```

1. Cada lista tiene varios vínculos a otras tablas. Todos estos vínculos se eliminan por lotes mediante la siguiente consulta:

   ```sql
   DELETE FROM $(relatedTable) WHERE iGroupId=$(l) IN (SELECT iGroupId FROM $(relatedTable) WHERE iGroupId=$(l) LIMIT 5000) 
   ```

   donde `$(relatedTable)` es una tabla relacionada con **NmsGroup** y `$(l)` es el identificador de la lista.

1. Cuando la lista es de tipo &quot;Lista&quot;, la tabla asociada se elimina mediante la siguiente consulta:

   ```sql
   DROP TABLE grp$(l)
   ```

1. Cada **Seleccionar** La lista de tipos recuperada por la operación se elimina mediante la siguiente consulta:

   ```sql
   DELETE FROM NmsGroup WHERE iGroupId=$(l) 
   ```

   donde `$(l)` es el identificador de lista

### Limpieza de los envíos que se van a eliminar o reciclar {#cleanup-of-deliveries-to-be-deleted-or-recycled}

Esta tarea purga todas las entregas para eliminarlos o reciclarlos.

1. El **[!UICONTROL Database cleanup]** flujo de trabajo selecciona todas las entregas para los que **deleteStatus** tiene el valor **[!UICONTROL Yes]** o **[!UICONTROL Recycled]** y cuya fecha de eliminación sea anterior al periodo definido en la variable **[!UICONTROL Deleted deliveries]** (**NmsCleanup_RecycledDeliveryPurgeDelay**) del asistente de implementación. Para obtener más información, consulte [Asistente de implementación](#deployment-wizard). Este periodo se calcula en relación con la fecha actual del servidor.
1. Para cada servidor intermediario, la tarea selecciona la lista de envíos que desea eliminar.
1. El **[!UICONTROL Database cleanup]** el flujo de trabajo elimina los registros de envío, los archivos adjuntos, la información de página espejo y todos los demás datos relacionados.
1. Antes de eliminar la entrega de forma definitiva, el flujo de trabajo depura la información vinculada de las siguientes tablas:

   * En la tabla de exclusión de envíos (**NmsDlvExclusion**), se utiliza la siguiente consulta:

     ```sql
     DELETE FROM NmsDlvExclusion WHERE iDeliveryId=$(l)
     ```

     donde **$(l)** es el identificador de la entrega.

   * En la tabla de cupones (**NmsCouponValue**), se utiliza la siguiente consulta (con eliminaciones masivas):

     ```sql
     DELETE FROM NmsCouponValue WHERE iMessageId IN (SELECT iMessageId FROM NmsCouponValue WHERE EXISTS (SELECT B.iBroadLogId FROM $(BroadLogTableName) B WHERE B.iDeliveryId = $(l) AND B.iBroadLogId = iMessageId ) LIMIT 5000)
     ```

     donde `$(l)` es el identificador de la entrega.

   * En las tablas del registro de envío (**NmsBroadlogXxx**), las eliminaciones masivas se ejecutan en lotes de 20 000 registros.
   * En las tablas de propuesta de ofertas (**NmsPropositionXxx**), las eliminaciones masivas se ejecutan en lotes de 20 000 registros.
   * En las tablas del registro de seguimiento (**NmsTrackinglogXxx**), las eliminaciones masivas se ejecutan en lotes de 20 000 registros.
   * En la tabla de fragmentos de envío (**NmsDeliveryPart**), las eliminaciones masivas se ejecutan en lotes de 500 000 registros. Esta tabla contiene información de personalización sobre los mensajes restantes que se van a enviar.
   * En la tabla de fragmentos de datos de la página espejo (**NmsMirrorPageInfo**), las eliminaciones masivas se ejecutan en lotes de 20 000 registros para las partes de envío caducadas y para las finalizadas o canceladas. Esta tabla contiene información de personalización sobre todos los mensajes utilizados para generar páginas espejo.
   * En la tabla de búsqueda de la página espejo (**NmsMirrorPageSearch**), las eliminaciones masivas se ejecutan en lotes de 20 000 registros. Esta tabla es un índice de búsqueda que proporciona acceso a la información de personalización almacenada en **NmsMirrorPageInfo** tabla.
   * En la tabla de registro de procesos por lotes (**XtkJobLog**), las eliminaciones masivas se ejecutan en lotes de 20 000 registros. Esta tabla contiene el registro de envíos que se van a eliminar.
   * En la tabla de seguimiento de URL de entrega (**NmsTrackingUrl**), se utiliza la siguiente consulta:

     ```sql
     DELETE FROM NmsTrackingUrl WHERE iDeliveryId=$(l)
     ```

     donde `$(l)` es el identificador de la entrega.

     Esta tabla contiene las direcciones URL encontradas en los envíos que se van a eliminar para habilitar su seguimiento.

1. La entrega se elimina de la tabla de entregas (**NmsDelivery**):

   ```sql
   DELETE FROM NmsDelivery WHERE iDeliveryId = $(l)
   ```

   donde `$(l)` es el identificador de la entrega.

#### Envíos mediante intermediario {#deliveries-using-mid-sourcing}

El **[!UICONTROL Database cleanup]** El flujo de trabajo de también elimina los envíos en los servidores de mid-sourcing.

1. Para ello, el flujo de trabajo comprueba que cada entrega está inactivo (según su estado). Si una entrega está activo, se detendrá antes de eliminarse. La comprobación se realiza ejecutando la siguiente consulta:

   ```sql
   SELECT iState FROM NmsDelivery WHERE iDeliveryId = $(l) AND iState <> 100;
   ```

   donde **$(l)** es el identificador de la entrega.

1. Si el valor del estado es **[!UICONTROL Start pending]** , **[!UICONTROL In progress]** , **[!UICONTROL Recovery pending]** , **[!UICONTROL Recovery in progress]** , **[!UICONTROL Pause requested]** , **[!UICONTROL Pause in progress]** , o **[!UICONTROL Paused]** (valores 51, 55, 61, 62, 71, 72, 75), la entrega se detiene y la tarea depura la información vinculada.

### Limpieza de envíos caducados {#cleanup-of-expired-deliveries}

Esta tarea detiene los envíos cuyo periodo de validez ha caducado.

1. El **[!UICONTROL Database cleanup]** workflow crea la lista de envíos que han caducado. Esta lista incluye todas las entregas caducados con un estado distinto a **[!UICONTROL Finished]** , así como los envíos detenidos recientemente con más de 10 000 mensajes sin procesar. Se utiliza la siguiente consulta:

   ```sql
   SELECT iDeliveryId, iState FROM NmsDelivery WHERE iDeleteStatus=0 AND iIsModel=0 AND iDeliveryMode=1 AND ( (iState >= 51 AND iState < 85 AND tsValidity IS NOT NULL AND tsValidity < $(currentDate) ) OR (iState = 85 AND DateMinusDays(15) < tsLastModified AND iToDeliver - iProcessed >= 10000 ))
   ```

   donde `delivery mode 1` coincide con el **[!UICONTROL Mass delivery]** modo, `state 51` coincide con el **[!UICONTROL Start pending]** estado, `state 85` coincide con el **[!UICONTROL Stopped]** y el número más alto de registros de envío actualizados de forma masiva en el servidor de envío es igual a 10 000.

1. A continuación, el flujo de trabajo incluye la lista de envíos caducados recientemente que utilizan intermediarios. Se excluyen los envíos para los que aún no se han recuperado registros de envío a través del servidor intermediario.

   Se utiliza la siguiente consulta:

   ```sql
   SELECT iDeliveryId, tsValidity, iMidRemoteId, mData FROM NmsDelivery WHERE (iDeliveryMode = 4 AND (iState = 85 OR iState = 95) AND tsValidity IS NOT NULL AND (tsValidity < SubDays(GetDate() , 15) OR tsValidity < $(DateOfLastLogPullUp)) AND tsLastModified > SubDays(GetDate() , 15))
   ```

1. La siguiente consulta se utiliza para detectar si la cuenta externa sigue activa o no, para filtrar los envíos por fecha:

   ```sql
   SELECT iExtAccountId FROM NmsExtAccount WHERE iActive<>0 AND sName=$(providerName)
   ```

1. En la lista de envíos caducados, registros de envío cuyo estado es **[!UICONTROL Pending]** , cambie a **[!UICONTROL Delivery cancelled]** y todas las entregas de esta lista cambian a **[!UICONTROL Finished]** .

   Se utilizan las siguientes consultas:

   ```sql
   UPDATE $(BroadLogTableName) SET tsLastModified=$(curdate), iStatus=7, iMsgId=$(bl) WHERE iDeliveryId=$(dl) AND iStatus=6
   ```

   donde `$(curdate)`es la fecha actual del servidor de la base de datos, `$(bl)` es el identificador del mensaje de &quot;logs&quot; de envío, `$(dl)` es el identificador de la entrega, `delivery status 6` coincide con el **[!UICONTROL Pending]** estado y `delivery status 7` coincide con el **[!UICONTROL Delivery cancelled]** estado.

   ```sql
   UPDATE NmsDelivery SET iState = 95, tsLastModified = $(curdate), tsBroadEnd = tsValidity WHERE iDeliveryId = $(dl)
   ```

   donde `delivery state 95` coincide con el **[!UICONTROL Finished]** estado, y `$(dl)` es el identificador de la entrega.

1. Todos los fragmentos (**deliveryParts**) de entregas obsoletas se eliminan y todos los fragmentos obsoletos de entregas de notificación en curso se eliminan. La eliminación masiva se utiliza para ambas tareas.

   Se utilizan las siguientes consultas:

   ```sql
   DELETE FROM NmsDeliveryPart WHERE iDeliveryPartId IN (SELECT iDeliveryPartId FROM NmsDeliveryPart WHERE iDeliveryId IN (SELECT iDeliveryId FROM NmsDelivery WHERE iState=95 OR iState=85) LIMIT 5000)
   ```

   ```sql
   DELETE FROM NmsDeliveryPart WHERE iDeliveryPartId IN (SELECT iDeliveryPartId FROM NmsDeliveryPart WHERE tsValidity < $(curDate) LIMIT 500000)
   ```

   donde `delivery state 95` coincide con el **[!UICONTROL Finished]** estado, `delivery state 85` coincide con el **[!UICONTROL Stopped]** estado, y `$(curDate)` es la fecha actual del servidor.

### Limpieza de páginas espejo {#cleanup-of-mirror-pages}

Esta tarea elimina los recursos web (páginas espejo) utilizados por las entregas.

1. En primer lugar, la lista de envíos que se van a purgar se recupera mediante la siguiente consulta:

   ```sql
   SELECT iDeliveryId, iNeedMirrorPage FROM NmsDelivery WHERE iWebResPurged = 0 AND tsWebValidity IS NOT NULL AND tsWebValidity < $(curdate)
   ```

   donde `$(curDate)` es la fecha actual del servidor.

1. El **NmsMirrorPageInfo** A continuación, se purga la tabla de, si es necesario, utilizando el identificador de la entrega recuperado anteriormente. La eliminación masiva se utiliza para generar las siguientes consultas:

   ```sql
   DELETE FROM NmsMirrorPageInfo WHERE iMirrorPageInfoId IN (SELECT iMirrorPageInfoId FROM NmsMirrorPageInfo WHERE iDeliveryId = $(dl)) LIMIT 5000
   ```

   ```sql
   DELETE FROM NmsMirrorPageSearch WHERE iMessageId IN (SELECT iMessageId FROM NmsMirrorPageSearch WHERE iDeliveryId = $(dl)) LIMIT 5000
   ```

   donde `$(dl)` es el identificador de la entrega.

1. A continuación, se agrega una entrada al registro de envíos.
1. Las entregas depuradas se identifican entonces para evitar tener que volver a procesarlas más adelante. Se ejecuta la siguiente consulta:

   ```sql
   UPDATE NmsDelivery SET iWebResPurged = 1 WHERE iDeliveryId IN ($(strIn))
   ```

   donde `$(strIn)` es la lista de identificadores de envío.

### Limpieza de tablas de trabajo {#cleanup-of-work-tables}

Esta tarea elimina de la base de datos todas las tablas de trabajo que coincidan con las entregas cuyo estado sea **[!UICONTROL Being edited]** , **[!UICONTROL Stopped]** o **[!UICONTROL Deleted]** .

1. La lista de tablas con nombres que comienzan por **wkDlv_** se recupera primero con la siguiente consulta (postgresql):

   ```sql
   SELECT relname FROM pg_class WHERE relname LIKE Lower('wkDlv_') ESCAPE E'\\' AND relkind IN ('r','v') AND pg_get_userbyid(relowner)<>'postgres'
   ```

1. A continuación, se excluyen las tablas utilizadas por los flujos de trabajo en curso. Para ello, la lista de envíos en curso se recupera mediante la siguiente consulta:

   ```sql
   SELECT iDeliveryId FROM NmsDelivery WHERE iDeliveryId<>0 AND iDeleteStatus=0 AND iState NOT IN (0,85,100);
   ```

   donde `0` es el valor que coincide con el **[!UICONTROL Being edited]** estado del envío, `85` coincide con el **[!UICONTROL Stopped]** estado y `100` coincide con el **[!UICONTROL Deleted]** estado.

1. Las tablas que ya no se utilizan se eliminarán con la siguiente consulta:

   ```sql
   DROP TABLE wkDlv_15487_1;
   ```

### Limpieza de rechazos generados por importaciones {#cleanup-of-rejects-generated-by-imports-}

Este paso le permite eliminar registros para los que no se han procesado todos los datos durante la importación.

1. La eliminación masiva se realiza en el **XtkReject** con la siguiente consulta:

   ```sql
   DELETE FROM XtkReject WHERE iRejectId IN (SELECT iRejectId FROM XtkReject WHERE tsLog < $(curDate)) LIMIT $(l)
   ```

   donde `$(curDate)` es la fecha actual del servidor de la que restamos el periodo definido para la **NmsCleanup_RejectsPurgeDelay** (consulte) [Asistente de implementación](#deployment-wizard)) y `$(l)` es el número máximo de registros que se van a eliminar de forma masiva.

1. A continuación, se eliminan todos los rechazos huérfanos mediante la siguiente consulta:

   ```sql
   DELETE FROM XtkReject WHERE iJobId NOT IN (SELECT iJobId FROM XtkJob)
   ```

### Limpieza de instancias de flujo de trabajo {#cleanup-of-workflow-instances}

Esta tarea depura cada instancia de flujo de trabajo con su identificador (**lWorkflowId**) e historial (**lHistory**). Elimina las tablas inactivas ejecutando de nuevo la tarea de limpieza de la tabla de trabajo. La limpieza también elimina todas las tablas de trabajo huérfanas (wkf% y wkfisto%) de los flujos de trabajo eliminados.

>[!NOTE]
>
>La frecuencia de depuración del historial se especifica para cada flujo de trabajo en la **Historial en días** campo (valor predeterminado 30 días). Este campo se puede encontrar en la **Ejecución** de las propiedades del flujo de trabajo. Para obtener más información, consulte [esta sección](../../workflow/using/workflow-properties.md#execution).

1. Para recuperar la lista de flujos de trabajo que desea eliminar, se utiliza la siguiente consulta:

   ```sql
   SELECT iWorkflowId, iHistory FROM XtkWorkflow WHERE iWorkflowId<>0
   ```

1. Esta consulta genera la lista de flujos de trabajo que se utilizarán para eliminar todos los registros vinculados, las tareas finalizadas y los eventos finalizados, mediante las siguientes consultas:

   ```sql
   DELETE FROM XtkWorkflowLog WHERE iWorkflowId=$(lworkflow) AND tsLog < DateMinusDays($(lhistory))
   ```

   ```sql
   DELETE FROM XtkWorkflowTask WHERE iWorkflowId=$(lworkflow) AND iStatus<>0 AND tsCompletion < DateMinusDays($(lhistory)) 
   ```

   ```sql
   DELETE FROM XtkWorkflowEvent WHERE iWorkflowId=$(l) AND iStatus>2 AND tsProcessing < DateMinusDays($(lHistory))
   ```

   donde `$(lworkflow)` es el identificador del flujo de trabajo y `$(lhistory)` es el identificador del historial.

1. Se eliminan todas las tablas no utilizadas. Para ello, todas las tablas se recopilan gracias a un **wkf%** escriba la máscara utilizando la siguiente consulta (postgresql):

   ```sql
   SELECT relname FROM pg_class WHERE relname LIKE Lower('wkf%') ESCAPE E'\\' AND relkind IN ('r','v') AND pg_get_userbyid(relowner)<>'postgres'
   ```

1. Luego se excluyen todas las tablas utilizadas por una instancia de flujo de trabajo pendiente. La lista de flujos de trabajo activos se recupera mediante la siguiente consulta:

   ```sql
   SELECT iWorkflowId FROM XtkWorkflow WHERE iWorkflowId<>0 AND iState<>20
   ```

1. Cada identificador de flujo de trabajo se recupera a continuación para encontrar el nombre de las tablas utilizadas por los flujos de trabajo en curso. Estos nombres se excluyen de la lista de tablas recuperadas anteriormente.
1. las tablas del historial de actividades de tipo &quot;consulta incremental&quot; se excluyen mediante las siguientes consultas:

   ```sql
   SELECT relname FROM pg_class WHERE relname LIKE Lower('wkfhisto%') ESCAPE E'\\' AND relkind IN ('r','v') AND pg_get_userbyid(relowner)<>'postgres'
   ```

   ```sql
   SELECT iWorkflowId FROM XtkWorkflow WHERE iWorkflowId IN ($(strCondition))
   ```

   donde `$(strcondition)` es la lista de tablas que coinciden con el **wkfhisto%** máscara.

1. Las tablas restantes se eliminan mediante la siguiente consulta:

   ```sql
   DROP TABLE wkf15487_12;
   ```

### Limpieza de inicios de sesión del flujo de trabajo {#cleanup-of-workflow-logins}

Esta tarea elimina los inicios de sesión del flujo de trabajo mediante la siguiente consulta:

```sql
DELETE FROM XtkWorkflowLogin WHERE iWorkflowId NOT IN (SELECT iWorkflowId FROM XtkWorkflow)
```

### Limpieza de tablas de trabajo huérfanas {#cleanup-of-orphan-work-tables}

Esta tarea elimina las tablas de trabajo huérfanas vinculadas a grupos. El **NmsGroup** almacena los grupos que se van a limpiar (con un tipo diferente de 0). El prefijo de los nombres de tabla es **grp**. Para identificar los grupos que se van a limpiar, se utiliza la siguiente consulta:

```sql
SELECT iGroupId FROM NmsGroup WHERE iType>0"
```

### Limpieza de visitantes {#cleanup-of-visitors}

Esta tarea elimina los registros obsoletos de la tabla del visitante mediante la eliminación masiva. Los registros obsoletos son aquellos para los que la última modificación es anterior al periodo de conservación definido en el asistente de implementación (consulte [Asistente de implementación](#deployment-wizard)). Se utiliza la siguiente consulta:

```sql
DELETE FROM NmsVisitor WHERE iVisitorId IN (SELECT iVisitorId FROM NmsVisitor WHERE iRecipientId = 0 AND tsLastModified < AddDays(GetDate(), -30) AND iOrigin = 0 LIMIT 20000)
```

donde `$(tsDate)` es la fecha actual del servidor, a partir de la cual se resta el periodo definido para **NmsCleanup_VisitorPurgeDelay** opción.

### Limpieza de NPAI {#cleanup-of-npai}

Esta tarea permite eliminar registros que coincidan con direcciones válidas de **NmsAddress** tabla. La siguiente consulta se utiliza para realizar la eliminación masiva:

```sql
DELETE FROM NmsAddress WHERE iAddressId IN (SELECT iAddressId FROM NmsAddress WHERE iStatus=2 AND tsLastModified < $(tsDate1) AND tsLastModified >= $(tsDate2) LIMIT 5000)
```

donde `status 2` coincide con el **[!UICONTROL Valid]** estado, `$(tsDate1)` es la fecha actual del servidor, y `$(tsDate2)` coincide con el **NmsCleanup_LastCleanup** opción.

### Limpieza de suscripciones {#cleanup-of-subscriptions-}

Esta tarea purga todas las suscripciones eliminadas por el usuario del **NmsSubscription** tabla, con eliminación masiva. Se utiliza la siguiente consulta:

```sql
DELETE FROM NmsSubscription WHERE iDeleteStatus <>0
```

### Limpieza de registros de seguimiento {#cleanup-of-tracking-logs}

Esta tarea elimina los registros obsoletos de las tablas de registro de seguimiento y seguimiento web. Los registros obsoletos son aquellos que son anteriores al periodo de conservación definido en el asistente de implementación (consulte [Asistente de implementación](#deployment-wizard)).

1. En primer lugar, la lista de tablas de registro de seguimiento se recupera mediante la siguiente consulta:

   ```sql
   SELECT distinct(sTrackingLogSchema) FROM NmsDeliveryMapping WHERE sTrackingLogSchema IS NOT NULL;
   ```

1. La eliminación masiva se utiliza para purgar todas las tablas de la lista de tablas recuperadas anteriormente. Se utiliza la siguiente consulta:

   ```sql
   DELETE FROM NmsTrackingLogRcp WHERE iTrackingLogId IN (SELECT iTrackingLogId FROM NmsTrackingLogRcp WHERE tsLog < $(tsDate) LIMIT 5000) 
   ```

   donde `$(tsDate)` es la fecha actual del servidor de la que restamos el periodo definido para la **NmsCleanup_TrackingLogPurgeDelay** opción.

1. La tabla de estadísticas de seguimiento se purga mediante la eliminación masiva. Se utiliza la siguiente consulta:

   ```sql
   DELETE FROM NmsTrackingStats WHERE iTrackingStatsId IN (SELECT iTrackingStatsId FROM NmsTrackingStats WHERE tsStart < $(tsDate) LIMIT 5000) 
   ```

   donde `$(tsDate)` es la fecha actual del servidor de la que restamos el periodo definido para la **NmsCleanup_TrackingStatPurgeDelay** opción.

### Limpieza de registros de envío {#cleanup-of-delivery-logs}

Esta tarea permite depurar los &quot;logs&quot; de envío almacenados en varias tablas.

1. Para ello, la lista de esquemas de registro de envío se recupera mediante la siguiente consulta:

   ```sql
   SELECT distinct(sBroadLogSchema) FROM NmsDeliveryMapping WHERE sBroadLogSchema IS NOT NULL UNION SELECT distinct(sBroadLogExclSchema) FROM NmsDeliveryMapping WHERE sBroadLogExclSchema IS NOT NULL
   ```

1. Al utilizar intermediarios, la variable **NmsBroadLogMid** no se hace referencia a la tabla en las asignaciones de envío. El **nms:broadLogMid** Este esquema se añade a la lista recuperada por la consulta anterior.
1. El **Database cleanup** A continuación, el flujo de trabajo depura los datos obsoletos de tablas previamente recuperadas. Se utiliza la siguiente consulta:

   ```sql
   DELETE FROM $(tableName) WHERE iBroadLogId IN (SELECT iBroadLogId FROM $(tableName) WHERE tsLastModified < $(option) LIMIT 5000) 
   ```

   donde `$(tableName)` es el nombre de cada tabla en la lista de esquemas y `$(option)` es la fecha definida para la **NmsCleanup_BroadLogPurgeDelay** (consulte) [Asistente de implementación](#deployment-wizard)).

1. Finalmente, el flujo de trabajo comprueba si las variables **NmsProviderMsgId** La tabla existe. Si es así, todos los datos obsoletos se eliminan mediante la siguiente consulta:

   ```sql
   DELETE FROM NmsProviderMsgId WHERE iBroadLogId IN (SELECT iBroadLogId FROM NmsProviderMsgId WHERE tsCreated < $(option) LIMIT 5000)
   ```

   donde `$(option)` coincide con la fecha definida para **NmsCleanup_BroadLogPurgeDelay** (consulte) [Asistente de implementación](#deployment-wizard)).

### Limpieza de la tabla NmsEmailErrorStat {#cleanup-of-the-nmsemailerrorstat-table-}

Esta tarea limpia el **NmsEmailErrorStat** tabla. El programa principal (**coalesceErrors**) define dos fechas:

* **Fecha de inicio**: fecha del siguiente proceso que coincide con el **NmsLastErrorStatCoalesce** o la fecha más reciente de la tabla.
* **Fecha de finalización**: fecha actual del servidor.

Si la fecha de inicio es buena o igual a la fecha de finalización, no se producirá ningún proceso. En este caso, la variable **coalesceUpToDate** aparece un mensaje.

Si la fecha de inicio es anterior a la fecha de finalización, la variable **NmsEmailErrorStat** se ha limpiado la tabla.

El número total de errores en la **NmsEmailErrorStat** , entre las fechas de inicio y finalización, se recupera mediante la siguiente consulta:

```sql
SELECT COUNT(*) FROM NmsEmailErrorStat WHERE tsDate>= $(start) AND tsDate< $(end)
```

donde `$end` y `$start` son las fechas de inicio y finalización definidas anteriormente.

Si el total es bueno que 0:

1. La siguiente consulta se ejecuta para mantener solo los errores que superan un determinado umbral (igual a 20):

   ```sql
   SELECT iMXIP, iPublicId, SUM(iTotalConnections), SUM(iTotalErrors), SUM(iMessageErrors), SUM(iAbortedConnections), SUM(iFailedConnections), SUM(iRefusedConnections), SUM(iTimeoutConnections) FROM NmsEmailErrorStat WHERE tsDate>=$(start ) AND tsDate<$(end ) GROUP BY iMXIP, iPublicId HAVING SUM(iTotalErrors) >= 20
   ```

1. El **coalescingErrors** se muestra el mensaje.
1. Se crea una nueva conexión para eliminar todos los errores que se produjeron entre las fechas de inicio y finalización. Se utiliza la siguiente consulta:

   ```sql
   DELETE FROM NmsEmailErrorStat WHERE tsDate>=$(start) AND tsDate<$(end)
   ```

1. Cada error se guarda en la **NmsEmailErrorStat** mediante la siguiente consulta:

   ```sql
   INSERT INTO NmsEmailErrorStat(iMXIP, iPublicId, tsDate, iTotalConnections, iTotalErrors, iTimeoutConnections, iRefusedConnections, iAbortedConnections, iFailedConnections, iMessageErrors) VALUES($(lmxip ), $(lpublicId ), $(tsstart ), $(lconnections ), $(lconnectionErrors ),$(ltimeoutConnections ), $(lrefusedConnections ), $(labortedConnections ), $(lfailedConnections ), $(lmessageErrors))
   ```

   donde cada variable coincide con un valor recuperado por la consulta anterior.

1. El **start** se actualiza con los valores del proceso anterior para finalizar el bucle.

El bucle y la tarea se detienen.

Las limpiezas se ejecutan en **NmsEmailError** y **cleanupNmsMxDomain** tablas.

### Limpieza de la tabla NmsEmailError {#cleanup-of-the-nmsemailerror-table-}

Se utiliza la siguiente consulta:

```sql
DELETE FROM NmsEmailError WHERE iMXIP NOT IN (SELECT DISTINCT iMXIP FROM NmsEmailErrorStat)
```

Esta consulta elimina todas las líneas sin registros vinculados en el **NmsEmailErrorStat** desde el **NmsEmailError** tabla.

### Limpieza de la tabla NmsMxDomain {#cleanup-of-the-nmsmxdomain-table-}

Se utiliza la siguiente consulta:

```sql
DELETE FROM NmsMxDomain WHERE iMXIP NOT IN (SELECT DISTINCT iMXIP FROM NmsEmailErrorStat)
```

Esta consulta elimina todas las líneas sin un registro vinculado en la **NmsEmailErrorStat** de la tabla de **NmsMxDomain** tabla.

### Limpieza de propuestas {#cleanup-of-propositions}

Si la variable **Interacción** está instalado, esta tarea se ejecuta para purgar el **NmsPropositionXxx** tablas.

La lista de tablas de propuestas se recupera y se realiza una eliminación masiva en cada una de ellas, utilizando la siguiente consulta:

```sql
DELETE FROM NmsPropositionXxx WHERE iPropositionId IN (SELECT iPropositionId FROM NmsPropositionXxx WHERE tsLastModified < $(option) LIMIT 5000) 
```

donde `$(option)` es la fecha definida para la **NmsCleanup_PropositionPurgeDelay** (consulte) [Asistente de implementación](#deployment-wizard)).

### Limpieza de tablas de simulación {#cleanup-of-simulation-tables}

Esta tarea limpia las tablas de simulación huérfanas (que ya no están vinculadas a una simulación de oferta o de envío).

1. Para recuperar la lista de simulaciones que requieren limpieza, se utiliza la siguiente consulta:

   ```sql
   SELECT iSimulationId FROM NmsSimulation WHERE iSimulationId<>0
   ```

1. El nombre de las tablas que se van a eliminar está formado por el **wkSimu_** seguido del identificador de la simulación (por ejemplo: **wkSimu_456831_aggr**):

   ```sql
   DROP TABLE wkSimu_456831_aggr
   ```

### Limpieza de la pista de auditoría {#cleanup-of-audit-trail}

Se utiliza la siguiente consulta:

```sql
DELETE FROM XtkAudit WHERE tsChanged < $(tsDate)
```

donde **$(tsDate)** es la fecha actual del servidor desde la que se define el periodo para **XtkCleanup_AuditTrailPurgeDelay** opción se resta.

### Limpieza de Nmsaddress {#cleanup-of-nmsaddress}

Se utiliza la siguiente consulta:

```sql
DELETE FROM NmsAddress WHERE iAddressId IN (SELECT iAddressId FROM NmsAddress WHERE iStatus=STATUS_QUARANTINE AND tsLastModified < $(NmsCleanup_AppSubscriptionRcpPurgeDelay + 5d) AND iType IN (MESSAGETYPE_IOS, MESSAGETYPE_ANDROID ) LIMIT 5000)
```

Esta consulta elimina todas las entradas relacionadas con iOS y Android.

### Actualización de estadísticas y optimización del almacenamiento {#statistics-update}

El **XtkCleanup_NoStats** permite controlar el comportamiento del paso de optimización del almacenamiento del flujo de trabajo de limpieza.

Si la variable **XtkCleanup_NoStats** La opción no existe o si su valor es 0, se ejecutará la optimización del almacenamiento en modo detallado (VACUUM VERBOSE ANALYZE) en PostgreSQL y se actualizarán las estadísticas de todas las demás bases de datos. Para asegurarse de que este comando se ejecuta, compruebe los registros de PostgreSQL. VACUUM mostrará las líneas en el formato: `INFO: vacuuming "public.nmsactivecontact"` y ANALYZE generará líneas con el formato: `INFO: analyzing "public.nmsactivecontact"`.

Si el valor de la opción es 1, la actualización de estadísticas no se ejecuta en ninguna base de datos. La siguiente línea de registro aparecerá en los registros del flujo de trabajo: `Option 'XtkCleanup_NoStats' is set to '1'`.

Si el valor de la opción es 2, se ejecutará el análisis de almacenamiento en modo detallado (ANALYZE VERBOSE) en PostgreSQL y se actualizarán las estadísticas de todas las demás bases de datos. Para asegurarse de que este comando se ejecuta, compruebe los registros de PostgreSQL. ANALYZE generará líneas con el formato: `INFO: analyzing "public.nmsactivecontact"`.

### Limpieza de suscripciones (NMAC) {#subscription-cleanup--nmac-}

Esta tarea elimina cualquier suscripción relacionada con los servicios eliminados o las aplicaciones móviles.

Para recuperar la lista de esquemas de &quot;broadlog&quot;, se utiliza la siguiente consulta:

```sql
SELECT distinct(sBroadLogSchema) FROM NmsDeliveryMapping WHERE sBroadLogSchema IS NOT NULL
```

A continuación, la tarea recupera los nombres de las tablas vinculadas a **appSubscription** vincular y elimina estas tablas.

Este flujo de trabajo de limpieza también elimina todas las entradas donde deshabilitado = 1 que no se han actualizado desde la hora establecida en el **NmsCleanup_AppSubscriptionRcpPurgeDelay** opción.

### Limpiando información de sesión {#cleansing-session-information}

Esta tarea limpia la información del **sessionInfo** , se utiliza la siguiente consulta:

```sql
DELETE FROM XtkSessionInfo WHERE tsexpiration < $(curdate) 
```

### Limpieza de eventos caducados {#cleansing-expired-events}

Esta tarea limpia los eventos recibidos y almacenados en las instancias de ejecución y los eventos archivados en una instancia de control.

### Reacciones de limpieza {#cleansing-reactions}

Esta tarea limpia las reacciones (tabla) **NmsRemaMatchRcp**) en el que se han eliminado las propias hipótesis.
