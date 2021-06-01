---
product: campaign
title: Configuraciones específicas en la versión 5.11
description: Configuraciones específicas en la versión 5.11
audience: migration
content-type: reference
topic-tags: configuration
exl-id: 978e1249-f79b-4f5f-9a94-3bb2510785de
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: tm+mt
source-wordcount: '1041'
ht-degree: 4%

---

# Configuraciones específicas en la versión 5.11{#specific-configurations-in-v5-11}

Esta sección detalla la configuración adicional necesaria al migrar desde la versión 5.11. También debe configurar los ajustes detallados en la sección [Configuraciones generales](../../migration/using/general-configurations.md).

## Aplicaciones web {#web-applications}

La siguiente advertencia se mostrará automáticamente durante la migración:

```
The webApp ids have been modified during the migration process. Please make sure to check your scripts/css for broken compatibility (any client side javascript or css dealing directly with another element through its id is impacted). See file 'c:\svn\602\nl\build\ncs\var\upgrade/postupgrade/webAppsMigration_*************.txt' for details about the references that were automatically updated, if any.
```

Algunos componentes de aplicaciones web, por ejemplo los distintos campos de fórmula, tienen atributos @id. Se utilizan en el código XML de las aplicaciones web y ya no se generan de la misma manera. No están visibles en la interfaz y normalmente no se deben utilizar. Sin embargo, en algunos casos, los atributos @id pueden haberse utilizado para personalizar la renderización de aplicaciones web, por ejemplo a través de una hoja de estilo o utilizando código JavaScript.

Durante la migración, **debe** comprobar la ruta del archivo de registro especificada en la advertencia:

* **El archivo no está vacío**: contiene advertencias que se refieren a incoherencias registradas antes de la migración y que siguen existiendo. Puede ser código JavaScript en una aplicación web que haga referencia a un ID inexistente. Cada error debe comprobarse y corregirse.
* **El archivo está vacío**: esto significa que Adobe Campaign no ha detectado ningún problema.

Tanto si el archivo está vacío como si no, debe comprobar que estos ID no se utilizan para la configuración en otra parte (y adaptar la configuración si este es el caso).

## Flujos de trabajo {#workflows}

Dado que el nombre del directorio de instalación de Adobe Campaign ha cambiado, es posible que algunos flujos de trabajo no funcionen después de la migración. Si un flujo de trabajo hace referencia al directorio nl5 en una de sus actividades, esto generará un error. Reemplace esta referencia por **build**. Puede ejecutar una consulta SQL para identificar estos flujos de trabajo (ejemplo PostgreSQL):

```
SELECT   iWorkflowId, sInternalName, sLabel 
FROM XtkWorkflow 
WHERE mData LIKE '%nl5%';
```

## Facilidad de uso {#user-friendliness}

La página de inicio de Adobe Campaign v5.11 ya no está disponible.

Aunque no se recomienda, existen ciertas soluciones si desea mantener interfaces específicas de Adobe Campaign v5.11. Para obtener más información, póngase en contacto con nosotros.

## MySQL {#mysql}

>[!IMPORTANT]
>
>MySQL sólo se admite en v7 como motor de base de datos principal cuando se migra de la versión 6.02 o 5.11 con este motor.

MySQL no administra zonas horarias de forma predeterminada. Para habilitar la administración de zona horaria, ejecute el siguiente comando:

```
mysql_tzinfo_to_sql /usr/share/zoneinfo | mysql -u root mysql
```

>[!NOTE]
>
>Para obtener más información, consulte la página [https://dev.mysql.com/doc/refman/8.0/en/time-zone-support.html](https://dev.mysql.com/doc/refman/8.0/en/time-zone-support.html).

Si se han realizado modificaciones en la estructura de la base de datos, durante la configuración, por ejemplo (creación de índices específicos, creación de vistas SQL, etc.), se deben tomar ciertas precauciones al migrar. De hecho, algunas modificaciones pueden generarse a partir de incompatibilidades con el procedimiento de migración. Por ejemplo, la creación de vistas SQL que contengan campos **Timestamp** no es compatible con la opción **usetimestamptz**. Por lo tanto, le recomendamos que siga las recomendaciones que se indican a continuación:

1. Antes de iniciar la migración, realice una copia de seguridad de la base de datos.
1. Eliminar cambios SQL.
1. Realice la actualización posterior según el procedimiento detallado en la sección [Requisitos previos para la migración a Adobe Campaign 7](../../migration/using/prerequisites-for-migration-to-adobe-campaign-7.md).
   >[!NOTE]
   >
   >Es imperativo que siga los pasos de migración presentados en la sección [Requisitos previos para la migración a Adobe Campaign 7](../../migration/using/prerequisites-for-migration-to-adobe-campaign-7.md).
1. Reintegrar cambios SQL.

En este ejemplo, se ha creado una vista **NmcTrackingLogMessages** que tiene un campo **Timestamp** denominado **tslog**. En este caso, el procedimiento de migración falla y aparece el siguiente mensaje de error:

```
2011-10-04 11:57:51.804Z B67B28C0 1 info log Updating table 'NmcTrackingLogMessages'
2011-10-04 11:57:51.804Z B67B28C0 1 error log PostgreSQL error: ERROR: cannot alter type of a column used by a view or rule\nDETAIL: rule _RETURN on view nmctrackinglogmessagesview depends on column "tslog"\n (iRc=-2006)
2011-10-04 11:57:51.804Z B67B28C0 1 error log SQL order 'ALTER TABLE NmcTrackingLogMessages ALTER COLUMN tsLog TYPE TIMESTAMPTZ' was not executed. (iRc=-2006)
```

Para asegurarse de que la actualización posterior funciona, debe eliminar la vista antes de la migración y volver a crearla después de la migración, adaptándola al modo MARCA DE TIEMPO CON ZONA HORARIA .

## Seguimiento {#tracking}

Se ha modificado la fórmula de seguimiento. Al migrar, la fórmula antigua (v5) se sustituye por la nueva (v7). Si utiliza una fórmula personalizada en Adobe Campaign v5, esta configuración debe adaptarse en Adobe Campaign v7 (**NmsTracking_ClickFormula** y **NmsTracking_OpenFormula** opciones).

También se ha modificado la administración del seguimiento web. Una vez realizada la migración a v7, debe iniciar el asistente de implementación para finalizar la configuración del seguimiento web.

![](assets/migration_web_tracking.png)

Hay tres modos disponibles:

* **Seguimiento web de la sesión**: Si el  **[!UICONTROL Leads]** paquete no se ha instalado, esta opción está seleccionada de forma predeterminada. Esta opción es la más ideal en términos de rendimiento y le permite limitar el tamaño de los registros de seguimiento.
* **Seguimiento web permanente**
* **Seguimiento web anónimo**: Si el  **[!UICONTROL Leads]** paquete está instalado, esta opción está seleccionada de forma predeterminada. Es la opción que más consume recursos. Como se ha indicado anteriormente, la columna **sSourceId** debe indexarse (en la tabla de seguimiento y en la tabla **CrmIncomingLead** ).

>[!NOTE]
>
>Para obtener más información sobre estos tres modos, consulte [esta sección](../../configuration/using/about-web-tracking.md).

## Estructura de árbol de Adobe Campaign v7 {#campaign-vseven-tree-structure}

Durante la migración, la estructura de árbol se reorganiza automáticamente según los estándares de la versión 7. Se añaden las nuevas carpetas, se eliminan las carpetas obsoletas y su contenido se coloca en la carpeta &quot;To move&quot;. Todos los elementos de esta carpeta deben comprobarse después de la migración y el consultor debe decidir si los mantiene o los elimina. Los elementos que se van a conservar deben moverse al lugar correcto.

Se ha añadido una opción para deshabilitar la migración automática del árbol de navegación. Esta operación es ahora manual. Las carpetas obsoletas no se eliminan y no se agregan nuevas carpetas. Esta opción solo debe utilizarse si el árbol de navegación v5 listo para usar ha sufrido demasiados cambios. Agregue la opción a la consola, antes de migrar, en el nodo **[!UICONTROL Administration > Options]**:

* Nombre interno: NlMigration_KeepFolderStructure
* Tipo de datos: Número entero
* Valor (texto): 1

Si utiliza esta opción, después de la migración deberá eliminar las carpetas obsoletas, agregar las nuevas carpetas y ejecutar todas las comprobaciones necesarias.

**Lista de nuevas carpetas**:

Después de la migración es necesario agregar las siguientes carpetas:

| Nombre interno | Etiqueta | Condición |
|---|---|---|
| nmsAutoObjects | Objetos creados automáticamente | - |
| nmsCampaignAdmin | Administración de campañas | - |
| nmsCampaignMgt | Administración de campañas | - |
| nmsCampaignRes | Administración de campañas | - |
| nmsModels | Plantillas | - |
| nmsOnlineRes | En línea | - |
| nmsProduction | Producción | - |
| nmsProfilProcess | Procesos | - |
| xtkDashboard | Tableros | - |
| xtkPlatformAdmin | Plataforma | - |
| nmsLocalOrgUnit | Unidades organizativas | - |
| nmsMRM | MRM | MRM instalado |
| nmsOperations | Campañas | Campaign instalado |

**Lista de carpetas** obsoletas:

Las carpetas obsoletas que se eliminarán después de la migración son las siguientes:

>[!NOTE]
>
>Se debe comprobar todo el contenido de las carpetas obsoletas y, para cada elemento, el consultor decide si conservarlo o eliminarlo. Los elementos que se vayan a conservar deben trasladarse al lugar apropiado.

| Nombre interno | Etiqueta | Condición |
|---|---|---|
| nmsAdministration | Administración | - |
| nmsDeliveryMgt | Ejecución de campañas | - |
| ncmContent | Gestión de contenido | Administrador de contenido instalado |
| ncmForm | Formulario de entrada | Administrador de contenido instalado |
| ncmImage | Imágenes | Administrador de contenido instalado |
| ncmJavascript | Códigos JavaScript | Administrador de contenido instalado |
| ncmJst | Plantillas JavaScript | Administrador de contenido instalado |
| ncmParameters | Configuración | Administrador de contenido instalado |
| ncmSrcSchema | Esquemas de datos | Administrador de contenido instalado |
| ncmStylesheet | Archivos de estilo XSL | Administrador de contenido instalado |
| nmsAdminPlan | Administración | Campaign instalado |
| nmsResourcePlan | Recursos | Campaign instalado |
| nmsResourcesModels | Plantillas | Campaign instalado |
| nmsRootPlan | Administración de campañas | Campaign instalado |
| nmsOperator | Operadores de marketing | MRM instalado |
