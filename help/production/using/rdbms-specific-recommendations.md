---
product: campaign
title: Recomendaciones específicas de RDBMS
description: Recomendaciones específicas de RDBMS
feature: Monitoring
badge-v7-prem: label="Solo local/híbrido" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=es" tooltip="Se aplica solo a implementaciones On-premise e híbridas"
audience: production
content-type: reference
topic-tags: database-maintenance
exl-id: a586d70b-1b7f-47c2-a821-635098a70e45
source-git-commit: 14ba450ebff9bba6a36c0df07d715b7279604222
workflow-type: tm+mt
source-wordcount: '1243'
ht-degree: 4%

---

# Recomendaciones específicas de RDBMS{#rdbms-specific-recommendations}



Para ayudarle a configurar planes de mantenimiento, en esta sección se enumeran algunas recomendaciones y prácticas recomendadas adaptadas a los distintos motores RDBMS compatibles con Adobe Campaign. Sin embargo, solo son recomendaciones. Depende de usted adaptarlos a sus necesidades, en consonancia con sus procedimientos internos y restricciones. El administrador de la base de datos tiene la responsabilidad de crear y ejecutar estos planes.

## PostgreSQL {#postgresql}

### Detección de tablas grandes {#detecting-large-tables}

1. Puede agregar la siguiente vista a la base de datos:

   ```
   create or replace view uvSpace
    as
    SELECT c1.relname AS tablename, c2.relname AS indexname, c2.relpages * 8 / 1024 AS size_mbytes, c2.relfilenode AS filename, 0 AS row_count
    FROM pg_class c1, pg_class c2, pg_index i
    WHERE c1.oid = i.indrelid AND i.indexrelid = c2.oid
    UNION 
    SELECT pg_class.relname AS tablename, NULL::"unknown" AS indexname, pg_class.relpages * 8 / 1024 AS size_mbytes, pg_class.relfilenode AS filename, cast(pg_class.reltuples as integer) AS row_count
    FROM pg_class
    WHERE pg_class.relkind = 'r'::"char"
    ORDER BY 3 DESC, 1, 2 DESC;
   ```

1. Puede ejecutar esta consulta para detectar tablas e índices grandes:

   ```
   SELECT * FROM uvSpace;
   ```

   Como alternativa, puede ejecutar esta consulta, por ejemplo, para ver todos los tamaños de índice de forma colectiva:

   ```
   SELECT
      tablename,
      sum(size_mbytes) AS "sizeMB_all",
      (
         SELECT sum(size_mbytes)
         FROM uvspace
         AS uv2
         WHERE
            INDEXNAME IS NULL
            AND uv1.tablename = uv2.tablename
      ) AS "sizeMB_data",
      (
         SELECT sum(size_mbytes)
         FROM uvspace 
         AS uv2 
         WHERE
            INDEXNAME IS NOT NULL
            AND uv1.tablename = uv2.tablename
      ) AS "sizeMB_index",
      (
         SELECT ROW_COUNT
         FROM uvspace
         AS uv2
         WHERE
            INDEXNAME IS NULL
            AND uv1.tablename = uv2.tablename
      ) AS ROWS FROM uvspace AS uv1
      GROUP BY tablename
      ORDER BY 2 DESC
   ```

### Mantenimiento sencillo {#simple-maintenance}

>[!IMPORTANT]
>
>Adobe recomienda no ejecutar VACUUM FULL en las configuraciones de base de datos alojadas en Campaign Adobe. El mantenimiento sugerido es una guía solo para instalaciones ON-PREMISE. Para implementaciones y esquemas de tablas personalizadas, utilice VACUUM FULL bajo su propia responsabilidad, ya que VACUUM, sin supervisión, puede bloquear exclusivamente las tablas causando consultas estancadas y, en algunos casos, bloquear toda la base de datos.

En PostgreSQL, puede utilizar estas palabras clave típicas:

* VACÍO (COMPLETO, ANALIZAR, DETALLADO)

Para ejecutar la operación VACUUM, analizarla y cronometrarla, puede utilizar esta sintaxis:

```
\timing on
VACUUM (FULL, ANALYZE, VERBOSE) <table>;
```

Se recomienda encarecidamente no omitir la instrucción ANALYZE. De lo contrario, la tabla vaciada se queda sin estadísticas. El motivo es que se crea una nueva tabla y, a continuación, se elimina la anterior. Como resultado, el ID de objeto (OID) de la tabla cambia, pero no se calculan estadísticas. Por lo tanto, experimentará inmediatamente problemas de rendimiento.

Este es un ejemplo típico de un plan de mantenimiento SQL que se va a ejecutar de forma regular:

```
\timing on
VACUUM (FULL, ANALYZE, VERBOSE) nmsdelivery;

\timing on
VACUUM (FULL, ANALYZE, VERBOSE) nmsdeliverystat;

\timing on
VACUUM (FULL, ANALYZE, VERBOSE) xtkworkflow;

\timing on
VACUUM (FULL, ANALYZE, VERBOSE) xtkworkflowevent;

\timing on
VACUUM (FULL, ANALYZE, VERBOSE) xtkworkflowjob;

\timing on
VACUUM (FULL, ANALYZE, VERBOSE) xtkworkflowlog;

\timing on
VACUUM (FULL, ANALYZE, VERBOSE) xtkworkflowtask;

\timing on
VACUUM (FULL, ANALYZE, VERBOSE) xtkjoblog;

\timing on
VACUUM (FULL, ANALYZE, VERBOSE) xtkjob;

\timing on
VACUUM (FULL, ANALYZE, VERBOSE) nmsaddress;

\timing on
VACUUM (FULL, ANALYZE, VERBOSE) nmsdeliverypart;

\timing on
VACUUM (FULL, ANALYZE, VERBOSE) nmsmirrorpageinfo;
```

>[!NOTE]
>
>* Adobe recomienda comenzar con tablas más pequeñas: de esta manera, si el proceso falla en tablas grandes (donde el riesgo de fallo es mayor), al menos parte del mantenimiento se ha completado.
>* El Adobe recomienda agregar las tablas específicas al modelo de datos, que pueden estar sujetas a actualizaciones significativas. Este puede ser el caso de **NmsRecipient** si tiene flujos de replicación de datos diarios grandes.
>* La instrucción VACUUM bloqueará la tabla, lo que pone en pausa algunos procesos mientras se realiza el mantenimiento.
>* Para tablas muy grandes (normalmente superiores a 5 Gb), la instrucción VACUUM FULL puede volverse bastante ineficiente y tardar mucho tiempo. El Adobe no recomienda utilizarlo para **YyyNmsBroadLogXxx** tabla.
>* Esta operación de mantenimiento se puede implementar mediante un flujo de trabajo de Adobe Campaign, utilizando un **[!UICONTROL SQL]** actividad. Para obtener más información, consulte [esta sección](../../workflow/using/architecture.md). Asegúrese de programar el mantenimiento para un tiempo de actividad bajo que no entre en conflicto con la ventana de copia de seguridad.
>

### Reconstrucción de una base de datos {#rebuilding-a-database}

PostgreSQL no proporciona una manera fácil de realizar una regeneración de tabla en línea, ya que la instrucción VACUUM FULL bloquea la tabla, lo que impide la producción regular. Esto significa que el mantenimiento debe realizarse cuando no se utiliza la tabla. Puede:

* realizar tareas de mantenimiento cuando la plataforma Adobe Campaign esté detenida,
* detenga los distintos subservicios de Adobe Campaign que tienen probabilidad de escribir en la tabla que se está reconstruyendo (**nlserver stop wfserver nombre_instancia** para detener el proceso de flujo de trabajo).

A continuación, se muestra un ejemplo de desfragmentación de tabla mediante funciones específicas para generar el DDL necesario. El siguiente SQL permite crear dos nuevas funciones: **GenRebuildTablePart1** y **GenRebuildTablePart2**, que se puede utilizar para generar el DDL necesario para volver a crear una tabla.

* La primera función permite crear una tabla de trabajo (** _tmp** aquí) que es una copia de la tabla original.
* A continuación, la segunda función elimina la tabla original y cambia el nombre de la tabla de trabajo y sus índices.
* El uso de dos funciones en lugar de una significa que si la primera falla, no se corre el riesgo de eliminar la tabla original.

```
 -- --------------------------------------------------------------------------
 -- Generate the CREATE TABLE DDL for a table
 -- --------------------------------------------------------------------------
 create or replace function GenTableDDL(text) returns text as $$
 declare
 vstrTable text;
 vrecFld RECORD;
 vstrDDL text;
 vstrFields text;
 vstrNsTable text;
 vstrTableSpace text;
 begin
 vstrTable = lower($1);
 
 vstrDDL = ;
 
 SELECT
 pg_catalog.quote_ident(n.nspname) || '.' || pg_catalog.quote_ident(c.relname),
 pg_catalog.quote_ident(t.spcname)
 INTO
 vstrNsTable, vstrTableSpace
 FROM
 pg_namespace n, pg_class c left outer join pg_tablespace t on c.reltablespace = t.oid
 WHERE
 n.oid = c.relnamespace AND
 c.relname = vstrTable;
 
 vstrDDL = 'CREATE TABLE ' || vstrNsTable || '_tmp(';
 
 vstrFields = ;
 FOR vrecFld IN
 SELECT
 pg_catalog.quote_ident(a.attname) ||
 ' ' || t.typname ||
 case when t.typname='varchar' then '(' || cast(a.atttypmod-4 as text) || ')'
 when t.typname='numeric' then '(' || cast((a.atttypmod-4)/65536 as text) || ',' || cast((a.atttypmod-4)%65536 as text) || ')'
 else end ||
 case when a.attnotnull then ' not null' else end ||
 case when a.atthasdef then ' default '|| d.adsrc else end as DDL
 FROM
 pg_type t, pg_class c, pg_attribute a LEFT OUTER JOIN pg_attrdef d ON d.adrelid=a.attrelid and d.adnum=a.attnum
 WHERE 
 a.attnum > 0 AND
 a.attrelid = c.oid AND
 t.oid = a.atttypid AND
 c.relname = vstrTable
 ORDER BY
 a.attnum
 LOOP
 IF vstrFields <> THEN
 vstrFields = vstrFields || ',' || chr(10) || ' ';
 ELSE
 vstrFields = vstrFields || chr(10) || ' ';
 END IF;
 vstrFields = vstrFields || vrecFld.DDL;
 END LOOP;
 
 vstrDDL = vstrDDL || vstrFields || chr(10) || ')';
 if vstrTableSpace <> then
 vstrDDL = vstrDDL || ' TABLESPACE ' || vstrTableSpace;
 end if;
 vstrDDL = vstrDDL || ';' || chr(10);
 
 return vstrDDL;
 END;
 $$ LANGUAGE plpgsql;

 -- --------------------------------------------------------------------------
 -- Generate the CREATE INDEX DDL for a table
 -- --------------------------------------------------------------------------
 create or replace function GenIndexDDL(text) returns text as $$
 declare
 vstrTable text;
 vrecIndex RECORD;
 vstrDDL text;
 viFld integer;
 vstrFld text;
 begin
 vstrTable = lower($1);
 
 vstrDDL = ;
 
 FOR vrecIndex IN
 SELECT
 i.indkey, i.indisunique,
 pg_catalog.quote_ident(c.relname) as tablename,
 pg_catalog.quote_ident(ic.relname) as indexname,
 pg_catalog.quote_ident(t.spcname) as tablespace
 FROM
 pg_class c, pg_index i, pg_class ic left outer join pg_tablespace t on ic.reltablespace = t.oid
 WHERE
 i.indexrelid = ic.oid AND
 i.indrelid = c.oid AND
 c.relname = vstrTable
 LOOP
 
  vstrDDL = vstrDDL || 'CREATE ';
  if vrecIndex.indisunique then
  vstrDDL = vstrDDL || 'UNIQUE ';
  end if;
  vstrDDL = vstrDDL ||
   'INDEX ' ||vrecIndex.indexname || '_tmp ON ' ||
   vrecIndex.tablename || '_tmp(';
 
  FOR viFld IN array_lower(vrecIndex.indkey, 1) .. array_upper(vrecIndex.indkey, 1) LOOP
  SELECT pg_catalog.quote_ident(a.attname) INTO vstrFld 
  FROM 
   pg_attribute a, pg_class c
  WHERE 
   a.attnum = vrecIndex.indkey[viFld] AND
   a.attrelid = c.oid AND c.relname=vstrTable;
  
  vstrDDL = vstrDDL || vstrFld;
  if viFld <> array_upper(vrecIndex.indkey, 1) then
   vstrDDL = vstrDDL || ', ';
  end if;
  END LOOP;
  vstrDDL = vstrDDL || ')';
 
  if vrecIndex.tablespace <> then
  vstrDDL = vstrDDL || 'TABLESPACE ' || vrecIndex.tablespace;
  end if;
  vstrDDL = vstrDDL || ';' || chr(10);
 
 END LOOP;
 
 return vstrDDL;
 END;
 $$ LANGUAGE plpgsql;

 -- --------------------------------------------------------------------------
 -- Generate the ALTER INDEX RENAME for a table
 -- --------------------------------------------------------------------------
 create or replace function GenRenameIndexDDL(text) returns text as $$
 declare
 vstrTable text;
 vrecIndex RECORD;
 vstrDDL text;
 begin
 vstrTable = lower($1);
 
 vstrDDL = ;
 
 FOR vrecIndex IN
  SELECT
  pg_catalog.quote_ident(n.nspname) as namespace,
  pg_catalog.quote_ident(ic.relname) as indexname
  FROM
  pg_namespace n, pg_class c, pg_index i, pg_class ic
  WHERE
  i.indexrelid = ic.oid AND
  n.oid = ic.relnamespace AND
  i.indrelid = c.oid AND
  c.relname = vstrTable
 LOOP
 
  vstrDDL = vstrDDL || 'ALTER INDEX ' || vrecIndex.namespace || '.' || vrecIndex.indexname ||
    '_tmp RENAME TO ' || vrecIndex.indexname ||
    ';' || chr(10);
 END LOOP;
 
 return vstrDDL;
 END;
 $$ LANGUAGE plpgsql;

 -- --------------------------------------------------------------------------
 -- Build a copy of a table, with index
 -- --------------------------------------------------------------------------
 create or replace function GenRebuildTablePart1(text) returns text as $$
 declare
 vstrTable text;
 vstrTmp text;
 vstrDDL text;
 begin
 vstrTable = lower($1);
  
 vstrDDL = ;
 
 SELECT GenTableDDL(vstrTable) INTO vstrTmp;
 vstrDDL = vstrDDL|| vstrTmp || chr(10);
 
 vstrDDL = vstrDDL|| 'INSERT INTO ' || vstrTable || '_tmp SELECT * FROM ' || vstrTable || ';'||chr(10);
 SELECT GenIndexDDL(vstrTable) INTO vstrTmp;
 
 vstrDDL = vstrDDL|| vstrTmp || chr(10);
 vstrDDL = vstrDDL|| 'VACUUM ANALYSE '|| vstrTable || '_tmp;' ||chr(10);
 
 return vstrDDL;
 end;
 $$ LANGUAGE plpgsql;
 
 -- --------------------------------------------------------------------------
 -- Drop the original table and rename the copy
 -- --------------------------------------------------------------------------
 create or replace function GenRebuildTablePart2(text) returns text as $$
 declare
 vstrTable text;
 vstrTmp text;
 vstrDDL text;
 begin
 vstrTable = lower($1);
  
 vstrDDL = 'DROP TABLE ' || vstrTable||';'|| chr(10);
 vstrDDL = vstrDDL|| 'ALTER TABLE ' || vstrTable || '_tmp RENAME TO ' || vstrTable ||';'|| chr(10);
 
 SELECT GenRenameIndexDDL(vstrTable) INTO vstrTmp;
 vstrDDL = vstrDDL|| vstrTmp || chr(10);
 
 return vstrDDL;
 end;
 $$ LANGUAGE plpgsql;
```

El siguiente ejemplo se puede utilizar en un flujo de trabajo para reconstruir las tablas necesarias en lugar de utilizar el **aspirar/reconstruir** comando:

```
function sqlGetMemo(strSql)
 {
 var res = sqlSelect("s, m:memo", strSql);
 return res.s.m.toString();
 }

 function RebuildTable(strTable)
 {
 // Rebuild a table_tmp
 var strSql = sqlGetMemo("select GenRebuildTablePart1('"+strTable+"')");
 logInfo("Rebuilding table '"+strTable+"'...");
 // logInfo(strSql);
 sqlExec(strSql);
 
 // If fails, there is an exception thrown and so we do not delete the original table
 strSql = sqlGetMemo("select GenRebuildTablePart2('"+strTable+"')");
 logInfo("Swapping table '"+strTable+"'...");
 //logInfo(strSql);
 sqlExec(strSql);
 }
 
 RebuildTable('nmsrecipient');
 RebuildTable('nmsrcpgrlrel');
 // ... other tables here
```

## Oracle {#oracle}

Póngase en contacto con el administrador de la base de datos para conocer los procedimientos más adecuados para su versión de Oracle.

## Microsoft SQL Server {#microsoft-sql-server}

>[!NOTE]
>
>Para Microsoft SQL Server, puede utilizar el plan de mantenimiento detallado en [esta página](https://ola.hallengren.com/sql-server-index-and-statistics-maintenance.html).

El ejemplo siguiente se refiere a Microsoft SQL Server 2005. Si utiliza otra versión, póngase en contacto con el administrador de la base de datos para conocer los procedimientos de mantenimiento.

1. En primer lugar, conéctese a Microsoft SQL Server Management Studio con un inicio de sesión con derechos de administrador.
1. Vaya a la **[!UICONTROL Management > Maintenance Plans]** carpeta, haga clic con el botón derecho en ella y elija **[!UICONTROL Maintenance Plan Wizard]**.
1. Clic **[!UICONTROL Next]** cuando aparezca la primera página.
1. Seleccione el tipo de plan de mantenimiento que desea crear (programas independientes para cada tarea o un solo programa para todo el plan) y, a continuación, haga clic en **[!UICONTROL Change...]** botón.
1. En el **[!UICONTROL Job schedule properties]** , seleccione la configuración de ejecución que desee y haga clic en **[!UICONTROL OK]**, luego haga clic en **[!UICONTROL Next]**.
1. Seleccione las tareas de mantenimiento que desee realizar y haga clic en **[!UICONTROL Next]**.

   >[!NOTE]
   >
   >Se recomienda realizar al menos las tareas de mantenimiento que se muestran a continuación. También puede seleccionar la tarea de actualización de estadísticas, aunque ya la esté realizando el flujo de trabajo de limpieza de la base de datos.

1. En la lista desplegable, seleccione la base de datos en la que desea ejecutar el **[!UICONTROL Database Check Integrity]** tarea.
1. Seleccione la base de datos y haga clic en **[!UICONTROL OK]**, luego haga clic en **[!UICONTROL Next]**.
1. Configure el tamaño máximo asignado a la base de datos y haga clic en **[!UICONTROL Next]**.

   >[!NOTE]
   >
   >Si el tamaño de la base de datos supera este umbral, el plan de mantenimiento intentará eliminar los datos no utilizados para liberar espacio.

1. Reorganice o vuelva a generar el índice:

   * Si la tasa de fragmentación del índice está entre el 10 % y el 40 %, se recomienda una reorganización.

     Elija las bases de datos y los objetos (tablas o vistas) que desea reorganizar y haga clic en **[!UICONTROL Next]**.

     >[!NOTE]
     >
     >Según la configuración, puede elegir las tablas seleccionadas anteriormente o todas las tablas de la base de datos.

   * Si la tasa de fragmentación del índice es superior al 40 %, se recomienda volver a generar.

     Seleccione las opciones que desee aplicar a la tarea de regeneración de índices y haga clic en **[!UICONTROL Next]**.

     >[!NOTE]
     >
     >El proceso de regeneración de índices es más restrictivo en términos de uso del procesador y bloquea los recursos de la base de datos. Seleccione el **[!UICONTROL Keep index online while reindexing]** si desea que el índice esté disponible durante la regeneración.

1. Seleccione las opciones que desee mostrar en el informe de actividad y haga clic en **[!UICONTROL Next]**.
1. Compruebe la lista de tareas configuradas para el plan de mantenimiento y haga clic en **[!UICONTROL Finish]**.

   Se muestra un resumen del plan de mantenimiento y los estados de sus distintos pasos.

1. Una vez completado el plan de mantenimiento, haga clic en **[!UICONTROL Close]**.
1. En el explorador de Microsoft SQL Server, haga doble clic en **[!UICONTROL Management > Maintenance Plans]** carpeta.
1. Seleccione el plan de mantenimiento de Adobe Campaign: los distintos pasos se detallan en un flujo de trabajo.

   Tenga en cuenta que se ha creado un objeto en **[!UICONTROL SQL Server Agent > Jobs]** carpeta. Este objeto le permite iniciar el plan de mantenimiento. En nuestro ejemplo, solo hay un objeto, ya que todas las tareas de mantenimiento forman parte del mismo plan.

   >[!IMPORTANT]
   >
   >Para que este objeto se ejecute, el agente de Microsoft SQL Server debe estar habilitado.

**Configuración de una base de datos independiente para tablas de trabajo**

>[!NOTE]
>
>Esta configuración es opcional.

La opción **WdbcOptions_TempDbName** permite configurar una base de datos independiente para las tablas de trabajo en Microsoft SQL Server. Esto optimiza los backups y la replicación.

Esta opción se puede utilizar si desea que las tablas de trabajo (por ejemplo, las tablas creadas durante la ejecución de un flujo de trabajo) se creen en otra base de datos.

Cuando establece la opción en &quot;tempdb.dbo.&quot;, las tablas de trabajo se crean en la base de datos temporal predeterminada de Microsoft SQL Server. El administrador de la base de datos debe permitir el acceso de escritura a la base de datos tempdb.

Si la opción está establecida, se utiliza en todas las bases de datos de Microsoft SQL Server configuradas en Adobe Campaign (base de datos principal y cuentas externas). Tenga en cuenta que si dos cuentas externas comparten el mismo servidor, pueden producirse conflictos (ya que tempdb es única). Del mismo modo, si dos instancias de Campaign utilizan el mismo servidor MSSQL, puede haber conflictos si utilizan la misma tempdb.
