---
product: campaign
title: Último lanzamiento
description: Notas de la versión más reciente de Campaign Classic v7
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
feature: Overview
role: User
level: Beginner
exl-id: d65869ca-a785-4327-8e8d-791c28e4696c
source-git-commit: 88ee8d1575f6397a35fb6f7412cd08119a75c131
workflow-type: ht
source-wordcount: '962'
ht-degree: 100%

---

# Último lanzamiento{#latest-release}



Esta página lista las nuevas funcionalidades, mejoras y correcciones que se proporcionan con la **última versión de Campaign Classic v7**. Cada nueva compilación viene con un estado que se materializa con un color. Obtenga más información sobre los estados de compilación de Campaign Classic v7 en [esta página](rn-overview.md).

## ![](assets/do-not-localize/green_2.png) Versión 7.3.3, compilación 9359 {#release-7-3-3}

>[!CAUTION]
>
>La actualización de la consola de cliente es obligatoria. Obtenga información sobre cómo actualizar la consola de cliente en esta [página](../../installation/using/installing-the-client-console.md).

_20 de marzo de 2023_

**Mejora de la seguridad**

* Para mejorar la seguridad, Tomcat se ha actualizado de la versión 8.5.81 a la 8.5.85. (NEO-56936)

**Mejoras**

* El flujo de trabajo Facturación se ha mejorado para optimizar el rendimiento. (NEO-47658)
* El flujo de trabajo de seguimiento se ha mejorado para optimizar el rendimiento en caso de que el tamaño del envío sea elevado. (NEO-45064)
* Se ha mejorado la administración del seguimiento para corregir posibles problemas con los parámetros dinámicos en las direcciones URL. La administración de seguimiento v3 ahora gestiona las URL de tipo ajax (con parámetros después de &#39;#&#39;) e impide que las herramientas de terceros modifiquen las URL de seguimiento. Para aplicar este cambio, debe ponerse en contacto con Adobe. (NEO-46535)

<!--To apply this change, the marketing, tracking and mid servers need to be updated to 7.3.3. To enable the new tracking management mode, set the `emailLinksVersion` parameter to '3' in the configuration file of the marketing server. (NEO-46535)-->

**Parches**

* Se ha corregido un problema que podía impedir que las notificaciones push de prueba de iOS se enviaran desde la instancia de control (contexto de mensajería transaccional). (NEO-54713)
* Se ha corregido un problema que podía impedir que se desplazara en la pestaña **Editar** del Editor de contenido digital (DCE). (NEO-54474)
* Se ha corregido un problema que se producía cuando dos actividades de enriquecimiento utilizaban el mismo identificador de nombre en sus vínculos, lo que hacía que la segunda actividad de enriquecimiento utilizara los vínculos de la primera. (NEO-48851)

## ![](assets/do-not-localize/orange_2.png) Versión 7.3.2, compilación 9356 {#release-7-3-2}

_21 de noviembre de 2022_

>[!CAUTION]
>
>La actualización de la consola de cliente es obligatoria. Obtenga información sobre cómo actualizar la consola de cliente en esta [página](../../installation/using/installing-the-client-console.md).

**Actualizaciones de compatibilidad**

* Adobe Campaign ahora es compatible con PostgreSQL 14. Para obtener más información, consulte esta [nota técnica](../../technotes/using/tech-stack-upgrade.md).

* Tras el fin de la vida útil de Microsoft Internet Explorer 11, el motor de renderización de HTML para los paneles de la consola del cliente utiliza ahora Microsoft Edge Chromium. (NEO-20741)

Obtenga más información en la [Matriz de compatibilidad de Campaign](../../rn/using/compatibility-matrix.md#RDBMSservers).

**Mejoras**

* El conector Google BigQuery ahora admite totalmente los campos booleanos. (NEO-49181)
* Ahora puede configurar la duración de vigencia de las cookies de IMS en la sección `Configuration for the redirection service` del archivo serverConf.xml. Esto se aplica a las siguientes cookies: `uuid230`, `nllastdelid` y `AMCV_` (NEO-42541)
* Ahora la IP se puede ocultar en la solicitud &quot;/r/test&quot; estableciendo `showSourceIP` como falso en el nodo de redirección del archivo serverConf.xml. [Más información](../../installation/using/the-server-configuration-file.md#redirection-redirection)(NEO-46656)

**Funciones obsoletas**

* El marketing social con Facebook ya no se utiliza. Puede usar la integración de Twitter para publicar en medios sociales o trabajar con Adobe para crear un canal personalizado.
* El conector ACS (oferta Prime) ya no se utiliza. Puede utilizar las funcionalidades de exportación e importación de Campaign para extraer e insertar datos en ambos productos.

Obtenga más información en la página [Funciones obsoletas y eliminadas](deprecated-features.md).

**Otros cambios**

* Se han mejorado los registros web: ahora las advertencias `logonEscalation` solo se muestran a usuarios con privilegios de administrador. (NEO-47167)
* Para evitar errores, el flujo de trabajo **Recopilación de datos para el servicio HeatMap** (collectDataHeatMapService) ahora se detiene de forma predeterminada. (NEO-33959)
* Se han implementado varias mejoras para optimizar el uso de la CPU para el panel de campañas. (NEO-46417)
* Para evitar bloqueos, se ha eliminado el método loadLibraryDebug JS. (NEO-46968)
* Las referencias restantes a la biblioteca log4j se han eliminado de la instalación de Campaign en Windows. (NEO-44851)

**Parches**

* Se ha corregido un problema que impedía usar la opción de flujo de trabajo **Combinar líneas seleccionadas**. (NEO-48488)
* Se ha corregido un problema que impedía que el indicador de entrega **Correcto** se actualizara correctamente al usar el MTA mejorado de Adobe Campaign. (NEO-50462)
* Se ha corregido un problema al restablecer la aprobación de contenido en un ENVÍO de correo electrónico, que impedía la nueva aprobación. (NEO-44259)
* Se ha corregido un problema que podía impedir que se mostrara el botón **Aprobación de envío**. (NEO-47547)
* Se ha corregido un problema de rendimiento en la pestaña HTML de un envío que se podía producir en código HTML extenso. (NEO-47440)
* Se ha corregido un problema que afectaba a las actualizaciones de estado del registro de entregas en la instancia MID, cuando la opción `FeatureFlag_GZIP_Compression` estaba activada. (NEO-49183)
* Se ha corregido un problema que impedía enviar notificaciones de aplicaciones móviles de iOS desde una instancia de ejecución al usar la autenticación basada en token. (NEO-45961)
* Se ha corregido un problema con el flujo de trabajo **Actualizar la entrega** (deliverabilityUpdate) que se bloqueaba cuando tenía que sincronizar demasiados broadlogs. (NEO-48287)
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
