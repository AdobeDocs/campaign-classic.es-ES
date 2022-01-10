---
product: campaign
title: Adaptar la configuración
description: Aprenda a adaptar la configuración antes y después de una migración a Campaign v7
audience: migration
content-type: reference
topic-tags: migration-procedure
exl-id: ad71dead-c0ca-42d5-baa8-0f340979231a
source-git-commit: 327f220d6700242308ef3738a38cc95b970e3f46
workflow-type: tm+mt
source-wordcount: '1980'
ht-degree: 4%

---

# Adaptar la configuración{#configuring-your-platform}

![](../../assets/v7-only.svg)

Algunos cambios importantes en Adobe Campaign v7 requieren una configuración específica. Estas configuraciones pueden ser necesarias antes o después de la migración.

La configuración detallada que se debe llevar a cabo en Adobe Campaign v7 al migrar desde Campaign v5 o v6 está disponible en [esta página](general-configurations.md).


Durante la migración, la variable **NmsRecipient** se regenera a partir de la definición de esquemas. Se perderá cualquier cambio realizado en la estructura SQL de esta tabla fuera de Adobe Campaign.

Ejemplo de elementos para comprobar:

* Si ha añadido una columna (o un índice) al **NmsRecipient** pero no la ha detallado en el esquema, esto no se guardará.
* La variable **tablespace** recupera sus valores de forma predeterminada, es decir, los definidos en el asistente de implementación.
* Si ha añadido una vista de referencia a la variable **NmsRecipient** , debe eliminarla antes de migrar.


## Antes de la migración {#before-the-migration}

Al migrar a Adobe Campaign v7, deben configurarse los siguientes elementos. Estos elementos deben abordarse antes de iniciar el **postupgrade**.

* Zonas horarias

   Durante la migración desde una plataforma v5.11, debe especificar la zona horaria que se utilizará después de la actualización.

   Si desea utilizar el modo &quot;multizona horaria&quot;, consulte [esta sección](../../migration/using/general-configurations.md#time-zones).

   Si utiliza Oracle como base de datos, compruebe que los archivos de zona horaria de Oracle se hayan sincronizado correctamente entre el servidor de aplicaciones y el servidor de base de datos. [Más información](../../migration/using/general-configurations.md#oracle)

* Zonas de seguridad

   Por motivos de seguridad, ya no se puede acceder a la plataforma Adobe Campaign de forma predeterminada: debe configurar las zonas de seguridad, lo que requiere la recopilación de las direcciones IP del usuario antes de la migración. [Más información](../../migration/using/general-configurations.md#security)

* Sintaxis

   Es posible que parte del código Javascript ya no se acepte en la versión v7 debido al uso de un nuevo intérprete. [Más información](../../migration/using/general-configurations.md#javascript).

   Del mismo modo, se introduce una nueva sintaxis en Adobe Campaign v7 para reemplazar la sintaxis basada en SQLData. Si utiliza elementos de código con esta sintaxis, debe adaptarlos. [Más información](../../migration/using/general-configurations.md#sqldata)

* Contraseñas

   Debe configurar la variable **Administrador** y **Internas** contraseñas. [Más información](../../migration/using/before-starting-migration.md#user-passwords)

* Estructura de árbol

   Si migra desde una plataforma v5.11, debe reorganizar las carpetas de estructura de árbol según las normas de Adobe Campaign v6. [Más información](../../migration/using/configuring-your-platform.md#specific-configurations-in-v5-11).

* Interacción

   Si va a migrar desde Campaign v6.02 y usa la variable  **Interacción** , debe eliminar todas las referencias de esquema 6.02 que ya no existan en v7. [Más información](../../migration/using/general-configurations.md#interaction)

## Después de la migración {#after-the-migration}

Después de ejecutar **postupgrade**, compruebe y configure los siguientes elementos:

* Páginas espejo

   El bloque de personalización de páginas espejo ha cambiado con la versión 6.x. Esta nueva versión mejora la seguridad al acceder a estas páginas.

   Si ha utilizado el bloque personalizado v5 en los mensajes, la visualización de la página espejo fallará. Adobe recomienda encarecidamente utilizar el nuevo bloque personalizado al insertar una página espejo en los mensajes.

   Sin embargo, como solución temporal (y como las páginas espejo aún están activas), puede volver al antiguo bloque personalizado para evitar este problema cambiando la opción **[!UICONTROL XtkAcceptOldPasswords]** y configúrelo en **[!UICONTROL 1]**. Esto no afecta al uso del nuevo bloque personalizado v6.x.

* Sintaxis

   Si se producen errores relacionados con la sintaxis, durante la actualización posterior debe activar temporalmente la variable **allowSQLInjection** en la **serverConf.xml** , ya que esto le da tiempo de reescribir el código. Una vez adaptado el código, asegúrese de reactivar la seguridad. [Más información](../../migration/using/general-configurations.md#sqldata)

* Conflictos

   La migración se realiza a través de una actualización posterior y es posible que los conflictos aparezcan en informes, formularios o aplicaciones web. Estos conflictos se pueden resolver desde la consola. [Más información](../../migration/using/general-configurations.md#conflicts)

* Tomcat

   Si ha personalizado la carpeta de instalación, asegúrese de que está correctamente actualizada después de la migración. [Más información](../../migration/using/general-configurations.md#tomcat)

* Informes

   Todos los informes listos para usar actualmente utilizan el motor de renderización v6.x. Si ha añadido código JavaScript a los informes, es posible que algunos elementos se vean afectados. [Más información](../../migration/using/general-configurations.md#reports)

* Aplicaciones web

   Después de la actualización, si tiene algún problema para conectarse a las aplicaciones web identificadas, debe activar la variable **allowUserPassword** y **sessionTokenOnly** en el **serverConf.xml** archivo. Para evitar cualquier problema de seguridad, estas dos opciones deben reactivarse una vez resuelto el problema. [Más información](../../migration/using/general-configurations.md#identified-web-applications)

   Según el tipo de aplicaciones web y su configuración, debe realizar manipulaciones adicionales para asegurarse de que funcionan correctamente. [Más información](../../migration/using/general-configurations.md#web-applications)

   Si se migra desde una plataforma v5.11, se deben realizar configuraciones adicionales. [Más información](../../migration/using/general-configurations.md#specific-configurations-in-v5-11.md)

* Zonas de seguridad

   Antes de iniciar el servidor, debe configurar las zonas de seguridad. [Más información](../../installation/using/security-zones.md) y [vea aquí](../../migration/using/general-configurations.md#security)

* Flujos de trabajo

   Si migra desde una plataforma v5.11, debe comprobar la carpeta de flujos de trabajo. [Más información](../../migration/using/configuring-your-platform.md#specific-configurations-in-v5-11)

* Seguimiento

   Si migra desde una plataforma v5.11, debe configurar el modo de seguimiento. [Más información](../../migration/using/configuring-your-platform.md#specific-configurations-in-v5-11)

* Interacción

   Si usa **Interacción**, debe ajustar los parámetros después de la migración. [Más información](../../migration/using/general-configurations.md#interaction)

* Tableros

   Si aparece un error de cliente, debe actualizar los tableros con el nuevo código de Adobe Campaign v7 o copiar manualmente los siguientes archivos de la instancia v6.02 a la instancia v7:

   ```
   v6.02 files and spaces:
   /usr/local/neolane/nl6/datakit/xtk/eng/css/dropDownMenu.css
   /usr/local/neolane/nl6/datakit/xtk/eng/js/client/dropDownMenu.js
   v6.1 files and spaces:
   /usr/local/neolane/nl6/deprecated/xtk/css/dropDownMenu.css
   /usr/local/neolane/nl6/deprecated/xtk/js/client/dropDownMenu.js  
   ```


## Configuraciones específicas de a v5.11 a v7{#specific-configurations-in-v5-11}

![](../../assets/v7-only.svg)

Esta sección detalla la configuración adicional necesaria para migrar desde la versión 5.11. También debe configurar los ajustes detallados en la [Configuraciones generales](../../migration/using/general-configurations.md) para obtener más información.

### Aplicaciones web {#web-applications-v5}

La siguiente advertencia se mostrará automáticamente durante la migración:

```
The webApp ids have been modified during the migration process. Please make sure to check your scripts/css for broken compatibility (any client side JavaScript or css dealing directly with another element through its id is impacted). See file 'c:\svn\602\nl\build\ncs\var\upgrade/postupgrade/webAppsMigration_*************.txt' for details about the references that were automatically updated, if any.
```

Algunos componentes de aplicaciones web, por ejemplo los distintos campos de fórmula, tienen atributos @id. Se utilizan en el código XML de las aplicaciones web y ya no se generan de la misma manera. No están visibles en la interfaz y normalmente no se deben utilizar. Sin embargo, en algunos casos, los atributos @id pueden haberse utilizado para personalizar la renderización de aplicaciones web, por ejemplo a través de una hoja de estilo o utilizando código JavaScript.

Durante la migración, **must** compruebe la ruta del archivo de registro especificada en la advertencia:

* **El archivo no está vacío**: contiene advertencias que se refieren a incoherencias registradas antes de la migración y que siguen existiendo. Puede ser código JavaScript en una aplicación web que haga referencia a un ID inexistente. Cada error debe comprobarse y corregirse.
* **El archivo está vacío**: esto significa que Adobe Campaign no ha detectado ningún problema.

Tanto si el archivo está vacío como si no, debe comprobar que estos ID no se utilizan para la configuración en otra parte (y adaptar la configuración si este es el caso).

### Flujos de trabajo {#workflows}

Dado que el nombre del directorio de instalación de Adobe Campaign ha cambiado, es posible que algunos flujos de trabajo no funcionen después de la migración. Si un flujo de trabajo hace referencia al directorio nl5 en una de sus actividades, esto generará un error. Sustituya esta referencia por **versión**. Puede ejecutar una consulta SQL para identificar estos flujos de trabajo (ejemplo PostgreSQL):

```
SELECT   iWorkflowId, sInternalName, sLabel 
FROM XtkWorkflow 
WHERE mData LIKE '%nl5%';
```

### MySQL {#mysql}

>[!CAUTION]
>
>MySQL sólo se admite en v7 como motor de base de datos principal cuando se migra de la versión 6.02 o 5.11 con este motor.

MySQL no administra zonas horarias de forma predeterminada. Para habilitar la administración de zona horaria, ejecute el siguiente comando:

```
mysql_tzinfo_to_sql /usr/share/zoneinfo | mysql -u root mysql
```

>[!NOTE]
>
>Para obtener más información, consulte [https://dev.mysql.com/doc/refman/8.0/en/time-zone-support.html](https://dev.mysql.com/doc/refman/8.0/en/time-zone-support.html) página.

Si se han realizado modificaciones en la estructura de la base de datos, durante la configuración, por ejemplo (creación de índices específicos, creación de vistas SQL, etc.), se deben tomar ciertas precauciones al migrar. De hecho, algunas modificaciones pueden generarse a partir de incompatibilidades con el procedimiento de migración. Por ejemplo, la creación de vistas SQL que contengan **Marca de tiempo** los campos no son compatibles con la variable **usetimestamptz** . Por lo tanto, le recomendamos que siga las recomendaciones que se indican a continuación:

1. Antes de iniciar la migración, realice una copia de seguridad de la base de datos.
1. Eliminar cambios SQL.
1. Realizar la postactualización
   >[!NOTE]
   >
   >Debe seguir los pasos de migración presentados en [esta sección](../../migration/using/migrating-in-windows-for-adobe-campaign-7.md).
1. Reintegrar cambios SQL.

En este ejemplo, una **NmcTrackingLogMessages** se ha creado la vista y esto tiene un **Marca de tiempo** campo denominado **tslog**. En este caso, el procedimiento de migración falla y aparece el siguiente mensaje de error:

```
2011-10-04 11:57:51.804Z B67B28C0 1 info log Updating table 'NmcTrackingLogMessages'
2011-10-04 11:57:51.804Z B67B28C0 1 error log PostgreSQL error: ERROR: cannot alter type of a column used by a view or rule\nDETAIL: rule _RETURN on view nmctrackinglogmessagesview depends on column "tslog"\n (iRc=-2006)
2011-10-04 11:57:51.804Z B67B28C0 1 error log SQL order 'ALTER TABLE NmcTrackingLogMessages ALTER COLUMN tsLog TYPE TIMESTAMPTZ' was not executed. (iRc=-2006)
```

Para asegurarse de que la actualización posterior funciona, debe eliminar la vista antes de la migración y volver a crearla después de la migración, adaptándola al modo MARCA DE TIEMPO CON ZONA HORARIA .

### Seguimiento {#tracking}

Se ha modificado la fórmula de seguimiento. Al migrar, la fórmula antigua (v5) se sustituye por la nueva (v7). Si utiliza una fórmula personalizada en Adobe Campaign v5, esta configuración debe adaptarse en Adobe Campaign v7 (**NmsTracking_ClickFormula** y **NmsTracking_OpenFormula** ).

También se ha modificado la administración del seguimiento web. Una vez realizada la migración a v7, debe iniciar el asistente de implementación para finalizar la configuración del seguimiento web.

![](assets/migration_web_tracking.png)

Hay tres modos disponibles:

* **Seguimiento web de sesión**: Si la variable **[!UICONTROL Leads]** paquete no se ha instalado, esta opción está seleccionada de forma predeterminada. Esta opción es la más ideal en términos de rendimiento y le permite limitar el tamaño de los registros de seguimiento.
* **Seguimiento web permanente**
* **Seguimiento web anónimo**: Si la variable **[!UICONTROL Leads]** está instalado, esta opción está seleccionada de forma predeterminada. Es la opción que más consume recursos. Como se ha indicado anteriormente, la variable **sSourceId** debe estar indexada (en la tabla de seguimiento y en la **CrmIncomingLead** ).

>[!NOTE]
>
>Para obtener más información sobre estos tres modos, consulte [esta sección](../../configuration/using/about-web-tracking.md).

### Estructura de árbol de Adobe Campaign v7 {#campaign-vseven-tree-structure}

Durante la migración, la estructura de árbol se reorganiza automáticamente según los estándares de la versión 7. Se añaden las nuevas carpetas, se eliminan las carpetas obsoletas y su contenido se coloca en la carpeta &quot;To move&quot;. Todos los elementos de esta carpeta deben comprobarse después de la migración y el consultor debe decidir si los mantiene o los elimina. Los elementos que se van a conservar deben moverse al lugar correcto.

Se ha añadido una opción para deshabilitar la migración automática del árbol de navegación. Esta operación es ahora manual. Las carpetas obsoletas no se eliminan y no se agregan nuevas carpetas. Esta opción solo debe utilizarse si el árbol de navegación v5 listo para usar ha sufrido demasiados cambios. Agregue la opción a la consola, antes de migrar, en la **[!UICONTROL Administration > Options]** nodo:

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

**Lista de carpetas obsoletas**:

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


## Configuraciones específicas de la versión 6.02 a la versión 7{#specific-configurations-in-v6-02}

![](../../assets/v7-only.svg)

La siguiente sección detalla la configuración adicional necesaria para migrar desde la versión 6.02. También debe configurar los ajustes detallados en [esta página](../../migration/using/general-configurations.md).

### Aplicaciones web {#web-applications-v6}

Si va a migrar desde la versión 6.02, es posible que aparezcan registros de errores relacionados con las aplicaciones web de tipo &quot;descripción general&quot;. Ejemplos de mensajes de error:

```
[PU-0006] Entity of type : 'xtk:entityBackupNew' and Id 'nms:webApp|taskOverview', expression '[SQLDATA[' was found : '...)) or (@id IN ([SQLDATA[select 
[PU-0006] Entity of type : 'xtk:formDictionary' and Id 'nms:webApp|lastTasks', expression '[SQLDATA[' was found : '...)) or (@id IN ([SQLDATA[select 
[PU-0006] Entity of type : 'nms:webApp' and Id 'taskOverview', expression '[SQLDATA[' was found : '...@owner-id] IN ([SQLDATA[select iGroupid...'. (iRc=-1)
```

Estas aplicaciones web usaban SQLData y no son compatibles con v7, debido a la mayor seguridad. Estos errores llevarán a un error de migración.

Si no ha utilizado estas aplicaciones web, ejecute el siguiente script de limpieza y vuelva a ejecutar la postactualización:

```
Nlserver javascript -instance:[instance_name] -file [installation_path]/datakit/xtk/fra/js/removeOldWebApp.js
```

Si ha modificado estas aplicaciones web y desea seguir usándolas en la versión 7, debe activar la variable **allowSQLInjection** en las diferentes zonas de seguridad y vuelva a iniciar la posactualización. Consulte la [SQLData](../../migration/using/general-configurations.md#sqldata) para obtener más información.

### Centro de mensajes {#message-center}

Después de una migración de instancias de control del centro de mensajes, debe volver a publicar las plantillas de mensajes transaccionales para que funcionen.

En la versión 7, los nombres de las plantillas de mensajes transaccionales en las instancias de ejecución han cambiado. Actualmente tienen el prefijo del nombre del operador que corresponde a la instancia de control en la que se crean, por ejemplo **control1_template1_rt** (donde **control1** es el nombre del operador). Si tiene un volumen significativo de plantillas, le recomendamos que elimine las plantillas antiguas en las instancias de control.