---
solution: Campaign Classic
product: campaign
title: Configuraciones específicas en la versión 5.11
description: Configuraciones específicas en la versión 5.11
audience: migration
content-type: reference
topic-tags: configuration
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '1041'
ht-degree: 4%

---


# Configuraciones específicas en la versión 5.11{#specific-configurations-in-v5-11}

Esta sección detalla la configuración adicional requerida al migrar desde la versión 5.11. También debe configurar las opciones detalladas en la sección [Configuraciones generales](../../migration/using/general-configurations.md).

## Aplicaciones web {#web-applications}

La siguiente advertencia se mostrará automáticamente durante la migración:

```
The webApp ids have been modified during the migration process. Please make sure to check your scripts/css for broken compatibility (any client side javascript or css dealing directly with another element through its id is impacted). See file 'c:\svn\602\nl\build\ncs\var\upgrade/postupgrade/webAppsMigration_*************.txt' for details about the references that were automatically updated, if any.
```

Algunos componentes de aplicaciones web, por ejemplo los distintos campos de fórmula, tienen atributos @id. Se utilizan en el código XML de las aplicaciones web y ya no se generan de la misma manera. No son visibles en la interfaz y normalmente no se deben usar. Sin embargo, en algunos casos, los atributos @id pueden haberse utilizado para personalizar la representación de las aplicaciones web, por ejemplo mediante una hoja de estilo o utilizando código JavaScript.

Durante la migración, **debe** comprobar la ruta del archivo de registro especificada en la advertencia:

* **El archivo no está vacío**: contiene advertencias que se refieren a incoherencias registradas antes de la migración y que siguen existiendo. Puede ser código JavaScript en una aplicación web que haga referencia a un ID inexistente. Cada error debe comprobarse y corregirse.
* **El archivo está vacío**: esto significa que Adobe Campaign no ha detectado ningún problema.

Tanto si el archivo está vacío como si no, debe comprobar que estos ID no se utilizan para la configuración en otro lugar (y adaptar la configuración si este es el caso).

## Flujos de trabajo {#workflows}

Dado que el nombre del directorio de instalación de Adobe Campaign ha cambiado, es posible que algunos flujos de trabajo no funcionen después de la migración. Si un flujo de trabajo hace referencia al directorio nl5 en una de sus actividades, se producirá un error. Reemplace esta referencia con **build**. Puede ejecutar una consulta SQL para identificar estos flujos de trabajo (ejemplo PostgreSQL):

```
SELECT   iWorkflowId, sInternalName, sLabel 
FROM XtkWorkflow 
WHERE mData LIKE '%nl5%';
```

## Facilidad de uso {#user-friendliness}

La página de inicio Adobe Campaign v5.11 ya no está disponible.

Aunque no se recomienda, existen ciertas soluciones si desea mantener interfaces específicas de Adobe Campaign v5.11. Para más información, por favor contáctenos.

## MySQL {#mysql}

>[!IMPORTANT]
>
>MySQL sólo se admite en v7 como motor de base de datos principal al migrar desde la versión 6.02 o 5.11 con este motor.

MySQL no administra los horarios de forma predeterminada. Para habilitar la administración de husos horarios, ejecute el siguiente comando:

```
mysql_tzinfo_to_sql /usr/share/zoneinfo | mysql -u root mysql
```

>[!NOTE]
>
>Para obtener más información, consulte la página [https://dev.mysql.com/doc/refman/8.0/en/time-zone-support.html](https://dev.mysql.com/doc/refman/8.0/en/time-zone-support.html).

Si se han realizado modificaciones en la estructura de la base de datos, durante la configuración, por ejemplo (creación de índices específicos, creación de vistas SQL, etc.), se deben tomar ciertas precauciones al migrar. De hecho, algunas modificaciones pueden generarse a partir de incompatibilidades con el procedimiento de migración. Por ejemplo, la creación de vistas SQL que contengan campos **Timestamp** no es compatible con la opción **usetimestamptz**. Por lo tanto, le aconsejamos que siga las siguientes recomendaciones:

1. Antes de iniciar la migración, realice una copia de seguridad de la base de datos.
1. Eliminar cambios SQL.
1. Realice la postactualización según el procedimiento detallado en la sección [Requisitos previos para la migración a Adobe Campaign 7](../../migration/using/prerequisites-for-migration-to-adobe-campaign-7.md).
   >[!NOTE]
   >
   >Es imperativo que siga los pasos de migración que se indican en la sección [Requisitos previos para la migración a Adobe Campaign 7](../../migration/using/prerequisites-for-migration-to-adobe-campaign-7.md).
1. Reintegrar cambios SQL.

En este ejemplo, se ha creado una vista **NmcTrackingLogMessages** que tiene un campo **Timestamp** denominado **tslog**. En este caso, el procedimiento de migración falla y aparece el siguiente mensaje de error:

```
2011-10-04 11:57:51.804Z B67B28C0 1 info log Updating table 'NmcTrackingLogMessages'
2011-10-04 11:57:51.804Z B67B28C0 1 error log PostgreSQL error: ERROR: cannot alter type of a column used by a view or rule\nDETAIL: rule _RETURN on view nmctrackinglogmessagesview depends on column "tslog"\n (iRc=-2006)
2011-10-04 11:57:51.804Z B67B28C0 1 error log SQL order 'ALTER TABLE NmcTrackingLogMessages ALTER COLUMN tsLog TYPE TIMESTAMPTZ' was not executed. (iRc=-2006)
```

Para asegurarse de que la postactualización funciona, debe eliminar la vista antes de la migración y volver a crearla después de la migración, mientras la adapta al modo TIMESTAMP WITH TIMEZONE.

## Seguimiento {#tracking}

Se modificó la fórmula de seguimiento. Al migrar, la fórmula antigua (v5) se sustituye por la nueva (v7). Si utiliza una fórmula personalizada en Adobe Campaign v5, esta configuración debe adaptarse en Adobe Campaign v7 (**NmsTracking_ClickFormula** y **NmsTracking_OpenFormula** opciones).

También se ha modificado la administración de seguimientos web. Una vez que se ha realizado la migración a v7, debe inicio del asistente de implementación para finalizar la configuración del seguimiento web.

![](assets/migration_web_tracking.png)

Hay tres modos disponibles:

* **Seguimiento** web de sesión: Si el  **[!UICONTROL Leads]** paquete no se ha instalado, esta opción está seleccionada de forma predeterminada. Esta opción es la más ideal en términos de rendimiento y le permite limitar el tamaño de los registros de seguimiento.
* **Seguimiento web Permanente**
* **Seguimiento web** anónimo: Si el  **[!UICONTROL Leads]** paquete está instalado, esta opción está seleccionada de forma predeterminada. Es la opción que más consume recursos. Como se ha indicado anteriormente, la columna **sSourceId** debe indizarse (en la tabla de seguimiento y en la tabla **CrmInomingLead**).

>[!NOTE]
>
>Para obtener más información sobre estos tres modos, consulte [esta sección](../../configuration/using/about-web-tracking.md).

## Estructura de árbol de Adobe Campaign v7 {#campaign-vseven-tree-structure}

Durante la migración, la estructura de árbol se reorganiza automáticamente según los estándares de la versión 7. Se añaden las nuevas carpetas, se eliminan las carpetas obsoletas y su contenido se coloca en la carpeta &quot;Para mover&quot;. Todos los elementos de esta carpeta deben comprobarse después de la migración y el consultor debe decidir mantenerla o eliminarla. Los elementos que se van a conservar deben trasladarse al lugar adecuado.

Se ha agregado una opción para desactivar la migración automática del árbol de navegación. Esta operación ahora es manual. Las carpetas obsoletas no se eliminan y no se agregan nuevas carpetas. Esta opción solo debe utilizarse si el árbol de navegación v5 predeterminado ha sufrido demasiados cambios. Añada la opción en la consola, antes de migrar, en el nodo **[!UICONTROL Administration > Options]**:

* Nombre interno: NlMigration_KeepFolderStructure
* Tipo de datos: Entero
* Valor (texto): 1

Si utiliza esta opción, después de la migración tendrá que eliminar las carpetas obsoletas, agregar las nuevas carpetas y ejecutar todas las comprobaciones necesarias.

**Lista de nuevas carpetas**:

Después de la migración, es necesario agregar las siguientes carpetas:

| Nombre interno | Etiqueta | Condición |
|---|---|---|
| nmsAutoObjects | Objetos creados automáticamente | - |
| nmsCampaignAdmin | Gestión de la campaña | - |
| nmsCampaignMgt | Gestión de la campaña | - |
| nmsCampaignRes | Gestión de la campaña | - |
| nmsModels | Plantillas | - |
| nmsOnlineRes | En línea | - |
| nmsProduction | Producción | - |
| nmsProfilProcess | Procesos | - |
| xtkDashboard | Paneles | - |
| xtkPlatformAdmin | Plataforma | - |
| nmsLocalOrgUnit | Unidades organizativas | - |
| nmsMRM | MRM | MRM instalado |
| nmsOperations | Campañas | Campaña instalada |

**Lista de carpetas** obsoletas:

Las carpetas obsoletas que se eliminarán después de la migración son las siguientes:

>[!NOTE]
>
>Se debe comprobar todo el contenido de las carpetas obsoletas y, para cada elemento, el consultor decide si desea conservarlo o eliminarlo. Los elementos que se van a conservar deben trasladarse al lugar adecuado.

| Nombre interno | Etiqueta | Condición |
|---|---|---|
| nmsAdministration | Administración | - |
| nmsDeliveryMgt | Ejecución de campañas | - |
| ncmContent | Gestión de contenido | Content Manager instalado |
| ncmForm | Formulario de entrada | Content Manager instalado |
| ncmImage | Imágenes | Content Manager instalado |
| ncmJavascript | Códigos JavaScript | Content Manager instalado |
| ncmJst | Plantillas JavaScript | Content Manager instalado |
| ncmParameters | Configuración | Content Manager instalado |
| ncmSrcSchema | Esquemas de datos | Content Manager instalado |
| ncmStylesheet | Archivos de estilo XSL | Content Manager instalado |
| nmsAdminPlan | Administración | Campaña instalada |
| nmsResourcePlan | Recursos | Campaña instalada |
| nmsResourcesModels | Plantillas | Campaña instalada |
| nmsRootPlan | Gestión de la campaña | Campaña instalada |
| nmsOperator | Operadores de marketing | MRM instalado |

