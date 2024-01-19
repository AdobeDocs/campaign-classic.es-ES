---
product: campaign
title: Último lanzamiento
description: Notas de la versión más reciente de Campaign Classic v7
feature: Release Notes
badge-v7-only: label="v7" type="Informative" tooltip="Se aplica solo a Campaign Classic v7"
role: User
level: Beginner
exl-id: d65869ca-a785-4327-8e8d-791c28e4696c
source-git-commit: da35a3050d838cd8e57bf802dc066e32f22f8273
workflow-type: ht
source-wordcount: '2295'
ht-degree: 100%

---

# Último lanzamiento{#latest-release}

Esta página lista las nuevas funcionalidades, mejoras y correcciones que se proporcionan con la **última versión de Campaign Classic v7**. Cada nueva compilación viene con un estado que se materializa con un color. Obtenga más información sobre los estados de compilación de Campaign Classic v7 en [esta página](rn-overview.md).

## Versión 7.3.5, compilación 9368 {#release-7-3-5}

[!BADGE Disponibilidad general]{type=Positive url="https://experienceleague.adobe.com/docs/campaign-classic/using/release-notes/rn-overview.html?lang=es#rn-statuses" tooltip="Disponibilidad general"}


_5 de diciembre de 2023_


### Mejoras de seguridad {#release-7-3-5-security}


* Con la versión 7.3.5 de Campaign Classic , se ha mejorado y protegido el proceso de autenticación. Ahora, los operadores técnicos deberán utilizar Adobe Identity Management System (IMS) para conectarse a Campaign. Obtén información sobre cómo migrar tus cuentas técnicas existentes en [esta nota técnica](../../technotes/using/ims-migration.md).

* Además, con el objetivo de reforzar la seguridad y el proceso de autenticación, Adobe Campaign recomienda migrar el modo de autenticación del usuario final de la autenticación nativa de inicio de sesión/contraseña a Adobe Identity Management System (IMS). Aprende a migrar los operadores en [esta nota técnica](../../technotes/using/migrate-users-to-ims.md).

### Parches {#release-7-3-5-patches}

* Se ha corregido un problema que se producía al utilizar datos de una base de datos de Google Big Query y al actualizar datos en una base de datos de Oracle: todas las claves se establecían en `0` en la tabla temporal del flujo de trabajo. (NEO-65091)
* Se ha corregido un problema que ocasionaba que fallara una ejecución de flujo de trabajo cuando se combinaban dos consultas en una base de datos de Google Big Query en una actividad de flujo de trabajo de **Union**. (NEO-63705)
* Se ha corregido un problema que consistía en la solicitud al usuario de volverse a autenticar al hacer clic en el botón `Back` en un informe de campaña. (NEO-65087)
* Se ha corregido un error en el flujo de trabajo para la limpieza de base de datos que se producía cuando se eliminaba un envío antes que las pruebas de envío. (NEO-48114)
* Se ha corregido un problema al conectarse a la consola del cliente: las actualizaciones recientes sobre la verificación TLS provocaban un error de conexión. (NEO-50488)
* Se ha corregido un problema con la autenticación proxy HTTP después de la actualización de Campaign a la versión 7.3.1. Las solicitudes HTTP en los flujos de trabajo de la campaña fallaban con `error 407 – proxy auth required is returned`. (NEO-49624)
* Se ha corregido un error intermitente con el descifrado GPG en actividades de flujo de trabajo de **Script**. El mensaje de error asociado era: `gpg: decryption failed: No secret key`. (NEO-50257)
  <!--* Workflow temporary tables now have a primary index in Teradata with a Federated Data Access (FDA) connection. (NEO-62575)-->

## Versión 7.3.4, compilación 9364 {#release-7-3-4}

[!BADGE Disponibilidad limitada]{type=Neutral url="https://experienceleague.adobe.com/docs/campaign-classic/using/release-notes/rn-overview.html?lang=es#rn-statuses" tooltip="Disponibilidad limitada"}


>[!CAUTION]
>
>La actualización de la consola de cliente es obligatoria. Obtenga información sobre cómo actualizar la consola de cliente en esta [página](../../installation/using/installing-the-client-console.md).
>
>Si está utilizando [Campaign: Conector CRM de Microsoft Dynamics](../../platform/using/crm-connectors.md), debe actualizar los servidores de marketing y de fuentes intermedias con esta nueva versión.

_7 de septiembre de 2023_

### Mejoras de seguridad {#release-7-3-4-security}

* Se ha mejorado la seguridad en las API de IMS. La información confidencial del cliente (es decir, los tokens de acceso) se ha eliminado de los parámetros de URL. Estas credenciales ahora se envían en el encabezado de datos de publicación o autorización, lo que garantiza un proceso de comunicación más seguro. (NEO-63045)
* Se ha mejorado la seguridad de las aplicaciones web para evitar ataques de DDOS. (NEO-50757)
* Se ha mejorado la seguridad para evitar que los datos PII se expongan en los errores de registros web. (NEO-46827)
* Se ha optimizado la seguridad para evitar que el token de seguridad se incluya en la dirección URL de la página de inicio de Campaign. (NEO-38519)

### Actualizaciones de compatibilidad  {#release-7-3-4-compat}

* Tomcat se ha actualizado a la versión 8.5.91
* La biblioteca libexpat se ha actualizado a la versión 2.5.0 para mejorar la seguridad. (NEO-51023)

### Mejoras {#release-7-3-4-improvements}

* El parámetro MaxWorkingSetMb del archivo de configuración del servidor (serverConf.xml) se ha modificado para optimizar la asignación de memoria para los envíos. (NEO-49204)
* La cuenta externa de BigQuery se ha mejorado con las nuevas opciones utilizadas para configurar el SDK de GCloud. (NEO-63879) [Más información](../../installation/using/configure-fda-google-big-query.md#google-external)
* Una nueva sección de `cusHeader` se ha añadido en el archivo de configuración del servidor (serverConf.xml). Permite añadir encabezados personalizados al cargar un archivo desde un servidor externo. (NEO-58339) [Más información](../../installation/using/the-server-configuration-file.md#cusheaders).
* Se ha mejorado la administración del registro de seguimiento para evitar ID negativos para lastMsgId. Se ha cambiado de int32 a int64. (NEO-52290)
* El flujo de trabajo Intermediario (estadísticas de envío) se ha añadido de forma predeterminada. Este nuevo flujo de trabajo sincroniza los datos estadísticos de envío (nms:deliveryStat) desde el mid a la instancia de marketing. (NEO-36802)

### Parches {#release-7-3-4-patches}

* Se ha corregido un problema que se podía producir cuando se realizaba una solicitud de servicio antes del inicio de sesión de IMS, si la autenticación de llamada de solicitud de servicio utilizaba un token de servicio. (NEO-64903)
* Se ha corregido un problema de regresión que podía provocar problemas de desplazamiento al utilizar el Editor de contenido digital. (NEO-64671, NEO-59256)
* Se ha corregido un problema de regresión al pegar contenido desde Excel al Editor de contenido digital. (NEO-63287)
* Se ha corregido un problema que podía impedir que las aplicaciones web se mostraran correctamente en el modo de compatibilidad v5. (NEO-63174)
* Se ha corregido un problema que impedía que los operadores que no eran administradores hicieran envíos de webAnalytics. (NEO-62750)
* Se ha corregido un problema para evitar que los exploradores agregaran espacios adicionales al utilizar contenido condicional en un envío. (NEO-62132)
* Se ha corregido un problema de regresión que impedía que el cálculo del contacto activo funcionara correctamente en el flujo de trabajo Facturación al utilizar esquemas de destino asociados con varios esquemas de registro. (NEO-61468)
* Se ha corregido un problema que podría provocar un error e impedir que usted se desplace al editar el contenido de un envío. (NEO-61364)
* Se ha corregido un problema que provocaba que se abriera una ventana emergente al hacer clic en una imagen en el editor de contenido de correo electrónico. (NEO-60752)
* Se ha corregido un problema que podía provocar que los caracteres especiales del contenido del HTML de un envío se codificaran incorrectamente en varios exploradores. (NEO-60081)
* Se corrigió un problema con la sincronización que se podría producir al utilizar la actividad de flujo de trabajo inSMS. (NEO-59544)
* Se ha corregido un problema que se producía al usar el conector de Big Query con campos de fecha y hora o marca de tiempo. (NEO-59502, NEO-49768)
* Se ha corregido un problema que impedía usar informes de envío acumulativos. (NEO-59211)
* Se ha corregido un problema que podría provocar errores al compartir públicos con el servicio principal Personas. (NEO-58637)
* Se corrigió un problema que se producía al mostrar la página espejo de un envío. (NEO-58325)
* Se ha corregido un problema que impedía que funcionara la expresión xtk XtkLibrary.Right(). (NEO-57870)
* Se ha corregido un problema que provocaba que el atributo de estilo de la etiqueta de cuerpo cambiara al cargar una imagen en el editor de contenido digital. (NEO-57697)
* Se ha corregido un problema con los caracteres especiales al realizar exportaciones por lotes con la actividad del conector de CRM. (NEO-54300)
* Se ha corregido un problema que impedía que la carga masiva funcionara con tipos de datos de &quot;cadena&quot; al utilizar una actividad de carga de datos y el conector de Big Query. (NEO-53748)
* Se ha corregido un problema con la clave de caché que podría provocar problemas de procesamiento de ofertas. (NEO-51516, NEO-49995)
* Se ha corregido un problema que podría provocar un error de validación al enviar un envío de correo directo mediante targetMapping con aprobaciones. (NEO-50758)
* Se corrigió un problema con la administración de consultas que podría afectar al rendimiento del envío. (NEO-49991)
* Se ha corregido un problema que se producía al usar cuentas externas en actividades de envío de flujo de trabajo de Campaign, lo que podía provocar problemas de configuración de cuentas externas. (NEO-49959)
* Se ha corregido un problema de rendimiento al enviar notificaciones push. (NEO-49953)
Se ha corregido un problema que podía hacer que los caracteres japoneses se mostraran incorrectamente al exportar informes (NEO-49308).
* Se ha corregido un problema que hacía que el informe de errores de Tomcat mostrara demasiados detalles de error. (NEO-49029)
* Se ha corregido un problema que podría provocar un error de envío al utilizar un gran número de ofertas. (NEO-48807)
* Se ha corregido un problema que podía impedir que la actividad de flujos de trabajo **Actualizar datos** funcionara correctamente. (NEO-48140)
* Se ha corregido un problema que podía impedir que los datos de rastreo de clics se sincronizaran para envíos con una cuenta externa diferente al correo electrónico.(NEO-47277)
* Se ha corregido un problema que podía impedir que los registros de seguimiento en tiempo real se sincronizaran en la instancia de marketing del Centro de mensajes. (NEO-42540)
* Se ha corregido un problema que impedía que el prefijo del espacio de trabajo se mostrara en la ventana de detección de un esquema para las tablas de la base de datos Snowflake. (NEO-40297)
* Se ha corregido un problema que impedía que las etiquetas `<img-amp>` funcionaran en el contenido del correo electrónico. (NEO-38685)
* Se ha corregido un problema que podría provocar que el flujo de trabajo de archivado del Centro de mensajes falle al utilizar una retransmisión HTTP. (NEO-33783)
* Se ha corregido un problema que podría provocar errores de nombre y tamaño de fuente en el editor de contenido de correo electrónico. (NEO-61342)

## Versión 7.3.3, compilación 9359 {#release-7-3-3}

[!BADGE Disponibilidad limitada]{type=Neutral url="https://experienceleague.adobe.com/docs/campaign-classic/using/release-notes/rn-overview.html?lang=es#rn-statuses" tooltip="Disponibilidad limitada"}

>[!AVAILABILITY]
>
>Hay disponible una actualización de parche específica de Campaign v7.3.3.IMS para esta versión, si no se ha aplicado ningún otro parche a su entorno. Realiza [actualizaciones de seguridad de Adobe Identity Management System (IMS) incluidas en la versión 7.3.5](#release-7-3-5-security) en los entornos existentes de la versión 7.3.3.


_20 de marzo de 2023_


### Mejora de la seguridad {#release-7-3-3-security}

* Para mejorar la seguridad, Tomcat se ha actualizado de la versión 8.5.81 a la 8.5.85. (NEO-56936)



### Mejoras {#release-7-3-3-improvements}

* El flujo de trabajo Facturación se ha mejorado para optimizar el rendimiento. (NEO-47658)
* El flujo de trabajo de seguimiento se ha mejorado para optimizar el rendimiento en caso de que el tamaño del envío sea elevado. (NEO-45064)
* Se ha mejorado la administración del seguimiento para corregir posibles problemas con los parámetros dinámicos en las direcciones URL. La administración de seguimiento v3 ahora gestiona las URL de tipo ajax (con parámetros después de &#39;#&#39;) e impide que las herramientas de terceros modifiquen las URL de seguimiento. Para aplicar este cambio, debe ponerse en contacto con Adobe. (NEO-46535)

<!--To apply this change, the marketing, tracking and mid servers need to be updated to 7.3.3. To enable the new tracking management mode, set the `emailLinksVersion` parameter to '3' in the configuration file of the marketing server. (NEO-46535)-->

>[!CAUTION]
>
>La actualización de la consola de cliente es obligatoria. Obtenga información sobre cómo actualizar la consola de cliente en esta [página](../../installation/using/installing-the-client-console.md).

### Parches {#release-7-3-3-patches}

* Se ha corregido un problema que podía impedir que las notificaciones push de prueba de iOS se enviaran desde la instancia de control (contexto de mensajería transaccional). (NEO-54713)
* Se ha corregido un problema que podía impedir que se desplazara en la pestaña **Editar** del Editor de contenido digital (DCE). (NEO-54474)
* Se ha corregido un problema que se producía cuando dos actividades de enriquecimiento utilizaban el mismo identificador de nombre en sus vínculos, lo que hacía que la segunda actividad de enriquecimiento utilizara los vínculos de la primera. (NEO-48851)

## Versión 7.3.2, compilación 9356 {#release-7-3-2}

[!BADGE Disponibilidad limitada]{type=Neutral url="https://experienceleague.adobe.com/docs/campaign-classic/using/release-notes/rn-overview.html?lang=es#rn-statuses" tooltip="Disponibilidad limitada"}


>[!AVAILABILITY]
>
>Hay disponible una actualización de parche específica de Campaign v7.3.2.IMS para esta versión, si no se ha aplicado ningún otro parche a su entorno. Realiza [actualizaciones de seguridad de Adobe Identity Management System (IMS) incluidas en la versión 7.3.5](#release-7-3-5-security) en los entornos existentes de la versión 7.3.3.

_21 de noviembre de 2022_

### Actualizaciones de compatibilidad {#release-7-3-2-compat}

* Adobe Campaign ahora es compatible con PostgreSQL 14. Para obtener más información, consulte esta [nota técnica](../../technotes/using/tech-stack-upgrade.md).

* Tras el fin de la vida útil de Microsoft Internet Explorer 11, el motor de renderización de HTML para los paneles de la consola del cliente utiliza ahora Microsoft Edge Chromium. (NEO-20741)

Obtenga más información en la [Matriz de compatibilidad de Campaign](../../rn/using/compatibility-matrix.md#RDBMSservers).

>[!CAUTION]
>
>La actualización de la consola de cliente es obligatoria. Obtenga información sobre cómo actualizar la consola de cliente en esta [página](../../installation/using/installing-the-client-console.md).

### Mejoras {#release-7-3-2-improvements}

* El conector Google BigQuery ahora admite totalmente los campos booleanos. (NEO-49181)
* Ahora puede configurar la duración de vigencia de las cookies de IMS en la sección `Configuration for the redirection service` del archivo serverConf.xml. Esto se aplica a las siguientes cookies: `uuid230`, `nllastdelid` y `AMCV_` (NEO-42541)
* Ahora la IP se puede ocultar en la solicitud &quot;/r/test&quot; estableciendo `showSourceIP` como falso en el nodo de redirección del archivo serverConf.xml. [Más información](../../installation/using/the-server-configuration-file.md#redirection-redirection)(NEO-46656)

### Funciones obsoletas  {#release-7-3-2-deprecated}

* El marketing social con Facebook ya no se utiliza. Puede usar la integración de X (anteriormente conocido como Twitter) para publicar en medios sociales o trabajar con Adobe para crear un canal personalizado.
* El conector ACS (oferta Prime) ya no se utiliza. Puede utilizar las funcionalidades de exportación e importación de Campaign para extraer e insertar datos en ambos productos.

Obtenga más información en la página [Funciones obsoletas y eliminadas](deprecated-features.md).

### Otros cambios  {#release-7-3-2-other}

* Se han mejorado los registros web: ahora las advertencias `logonEscalation` solo se muestran a usuarios con privilegios de administrador. (NEO-47167)
* Para evitar errores, el flujo de trabajo **Recopilación de datos para el servicio HeatMap** (collectDataHeatMapService) ahora se detiene de forma predeterminada. (NEO-33959)
* Se han implementado varias mejoras para optimizar el uso de la CPU para el panel de campañas. (NEO-46417)
* Para evitar bloqueos, se ha eliminado el método loadLibraryDebug JS. (NEO-46968)
* Las referencias restantes a la biblioteca log4j se han eliminado de la instalación de Campaign en Windows. (NEO-44851)

### Parches {#release-7-3-2-patches}

* Se ha corregido un problema que impedía usar la opción de flujo de trabajo **Combinar líneas seleccionadas**. (NEO-48488)
* Se ha corregido un problema que impedía que el indicador de entrega **Correcto** se actualizara correctamente al usar el MTA mejorado de Adobe Campaign. (NEO-50462)
* Se ha corregido un problema al restablecer la aprobación de contenido en un ENVÍO de correo electrónico, que impedía la nueva aprobación. (NEO-44259)
* Se ha corregido un problema que podía impedir que se mostrara el botón **Aprobación de envío**. (NEO-47547)
* Se ha corregido un problema de rendimiento en la pestaña HTML de un envío que se podía producir en código HTML extenso. (NEO-47440)
* Se ha corregido un problema que afectaba a las actualizaciones de estado del registro de entregas en la instancia MID, cuando la opción `FeatureFlag_GZIP_Compression` estaba activada. (NEO-49183)
* Se ha corregido un problema que impedía enviar notificaciones de aplicaciones móviles de iOS desde una instancia de ejecución al usar la autenticación basada en token. (NEO-45961)
* Se ha corregido un problema con el flujo de trabajo **Actualizar la entregabilidad** (deliverabilityUpdate) que se bloqueaba cuando tenía que sincronizar demasiados broadlogs. (NEO-48287)
* Se ha corregido un problema con el tipo de eventos que bloqueaba el flujo de trabajo **Sincronización del centro de mensajes** (mcSynch).
* Se ha corregido un problema que podría provocar un error al añadir el indicador **Destinatarios que han abierto** (estimatedRecipientOpen) en los datos adicionales de una actividad del flujo de trabajo **Consulta**. (NEO-46665)
* Se ha corregido un problema con el flujo de trabajo **Facturación** que fallaba cuando los paquetes de control y ejecución del centro de mensajes se habían instalado en la misma instancia. (NEO-47674)
* Se ha corregido un problema con el flujo de trabajo **Facturación** que fallaba cuando tenía tablas con la clave principal definida como una cadena en lugar de como un número entero. (NEO-46254)
* Se ha corregido un problema con los filtros de mapa de calor cuando el nombre del flujo de trabajo era demasiado largo. (NEO-46301)
* Se ha corregido un problema introducido en la versión 7.3.1 del conector de FDA de Snowflake que provocaba la eliminación de registros al utilizar la &quot;combinación simple de cardinalidad 0 o 1&quot; durante el enriquecimiento. (NEO-48737)
* Se ha corregido un problema con el FDAC de Snowflake al utilizar el parámetro de ordenación en una actividad **División** del flujo de trabajo. (NEO-45899)
* Se ha corregido un problema que podía impedir que guardara la configuración de la cuenta externa. La cuenta externa ahora se guarda automáticamente después de la prueba de conexión, para conectores con capacidad de analizador (Snowflake y Google BigQuery). (NEO-47636)
* Se ha corregido un problema que impedía insertar un tipo de datos de hora en una actividad **Actualización de datos** del flujo de trabajo en MSSQL. (NEO-47763)
* Se ha corregido un problema que provocaba que el proceso de MTA se bloqueara cuando no se había establecido la zona horaria del motor (específico para MSSQL). (NEO-46619)
* Se ha corregido un problema con la importación de archivos HTML cuando los nodos de imagen (img) contenían direcciones URL con campos de personalización. (NEO-48396)
* Se ha corregido un error HTTP 500 al intentar conectarse a una instancia en la que el nodo `limit` no estaba configurado en el archivo serverConf.xml.
* Se ha corregido un problema que podría provocar el error &quot;El conjunto de caracteres no coincide&quot; al utilizar determinadas funciones como `to_nclob` con una base de datos Unicode de Oracle en la que NChar no estuviera habilitado. (NEO-49361)
* Se ha corregido un problema que provocaba un error cuando un usuario con derechos de acceso de lectura en la carpeta nmsDeliveryMapping intentaba ejecutar una campaña o un flujo de trabajo. (NEO-48230)
* Se ha corregido un problema que impedía el funcionamiento de la función `JSPContext.sqlExecWithOneParam`. (NEO-50066)
* Se han corregido varios errores de redirección. (NEO-50030)
