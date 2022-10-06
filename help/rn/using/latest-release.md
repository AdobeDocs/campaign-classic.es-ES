---
product: campaign
title: Último lanzamiento
description: Notas de la versión más reciente de Campaign Classic v7
feature: Overview
role: User
level: Beginner
exl-id: d65869ca-a785-4327-8e8d-791c28e4696c
source-git-commit: 52e9925932e9b802a92f317b0950a1e933499b56
workflow-type: ht
source-wordcount: '2008'
ht-degree: 100%

---

# Último lanzamiento{#latest-release}

![](../../assets/v7-only.svg)

Esta página lista las nuevas funcionalidades, mejoras y correcciones que se proporcionan con la **última versión de Campaign Classic v7**. Cada nueva compilación viene con un estado que se materializa con un color. Obtenga más información sobre los estados de compilación de Campaign Classic v7 en [esta página](rn-overview.md).

## ![](assets/do-not-localize/limited_2.png) Versión 7.3.1, compilación 9352 {#release-7-3-1}

_1 de julio de 2022_

**Novedades**

<table> 
<thead>
<tr> 
<th> <strong>Notificaciones con distinción de tiempo</strong><br /> </th> 
</tr> 
</thead> 
<tbody> 
<tr> 
<td> <p>Con iOS 15, Apple ha agregado una noción de notificaciones importantes que permite al desarrollador de la aplicación controlar el modo de evitar el enfoque cuando una notificación se considera importante y necesita llegar al usuario en tiempo real.</p>
<p>Obtenga información sobre cómo crear una notificación confidencial en la <a href="../../delivery/using/create-notifications-ios.md">documentación detallada</a>.</p>
</td> 
</tr> 
</tbody> 
</table>

**Actualizaciones de compatibilidad**

* El SDK de Adobe Campaign ahora es compatible con Android 12 y iOS 15 para las notificaciones push.
* Adobe Campaign ahora es compatible con MySQL 8.
* Adobe Campaign ahora es compatible con Windows 11.
* Adobe Campaign ahora es compatible con Debian 11.

Consulte la [Matriz de compatibilidades de Campaign](../../rn/using/compatibility-matrix.md#OperatingSystems).

**Mejoras**

* Tras el fin de vida útil de Microsoft Internet Explorer 11, el motor de renderización del HTML para Adobe Services (página de inicio de sesión) en la consola de cliente ahora utiliza Edge Chromium. Tenga en cuenta que Microsoft Internet Explorer 11 sigue siendo el motor de renderización del HTML para los paneles de la consola del cliente.  Además, ahora se requiere la instalación del tiempo de ejecución de Microsoft Edge Webview 2 para cualquier instalación de la consola del cliente (desde la versión de Campaign Classic 7.3). [Más información](../../installation/using/installing-the-client-console.md)
* Se ha mejorado la administración de conexiones de base de datos en Adobe Campaign para optimizar la estabilidad.
* La autenticación OAuth 2.0 de Microsoft Exchange Online para POP3 ahora es compatible con Campaign. [Más información](../../installation/using/external-accounts.md#bounce-mails-external-account)
* Se han corregido varios problemas al utilizar una actividad de flujo de trabajo de enriquecimiento con datos externos. (NEO-38069)
* El conector FDA de SAP Hana se ha actualizado para funcionar con la última versión de la base de datos SAP Hana (2.x).
* El conector FDA del Teradata se ha actualizado para funcionar con la última versión del Teradata (17).
* En la versión 20.2, la compatibilidad de la autenticación basada en tokens para las entregas de iOS se introdujo para las nuevas entregas y las plantillas de entrega. En la versión 7.2, se añadió un parche a la categoría para aplicar el soporte de autenticación basado en tokens a un máximo de 10 000 entregas y plantillas de entregas creadas anteriormente. En la versión 7.3, se ha mejorado el parche y se ha eliminado el límite.

**Parches**

* Se ha corregido un error de la versión anterior que impedía a los usuarios cambiar el tamaño de la página de inicio de sesión de IMS. (NEO-30085)
* Se ha corregido un error que se producía al instalar el paquete del gestor de contenido en una instancia existente. (NEO-32349)
* Se ha corregido un problema en el menú **Campañas** en el que se mostraba continuamente un mensaje “operación en curso”. (NEO-44904)
* Con Adobe Analytics habilitado, se ha corregido un problema que eliminaba BID (ID de Broadlog) y CID (ID de campaña) de la URL al enviar un correo electrónico con una URL sin guardar la entrega. (NEO-38678)
* Se ha corregido un problema que se producía al cargar una imagen en la carpeta de recursos públicos de una instancia con una configuración específica del Centro de mensajes. Aparecerá el siguiente mensaje de error: “No se pueden cargar las imágenes en los servidores de seguimiento”. (NEO-38546, NEO-45572)
* Se ha corregido un problema que hacía que el sistema se bloqueara al regenerar la configuración en caso de archivos de configuración incorrectos. (NEO-38752)
* Se ha corregido un problema que podría provocar que los indicadores de entrega no se actualicen correctamente. (NEO-44827)
* Se ha corregido un problema que podría provocar un error posterior a la actualización al utilizar consultas complejas. (NEO-43648)
* Se ha corregido un problema que podía impedir que funcionara la previsualización de webApps. (NEO-43242)
* Se ha corregido un problema que podría provocar que la preparación de la entrega falle al utilizar un archivo de asignación de destinatario externo en un flujo de trabajo con una actividad de carga de datos (archivo). (NEO-43691)
* Se ha corregido un problema que podía provocar bloqueos y requerir un reinicio completo de la instancia. (NEO-44645)
* Se ha corregido un problema que podía impedir que el mapa de calor del flujo de trabajo cargara ningún resultado. (NEO-43360)
* Se ha corregido un problema que podría provocar problemas de conexión al utilizar el conector externo de FDA. (NEO-42722)
* Se ha corregido un problema con las pruebas al usar la sustitución de direcciones y la exclusión de grupos de control. (NEO-39695)
* Se ha corregido un problema que podría provocar errores en el flujo de trabajo debido a un problema con el conector del Snowflake. (NEO-46299)
* Se ha corregido un problema que podía bloquear la consola del cliente debido a un carácter no válido en un bloque personalizado. (NEO-45761)
* Se ha corregido un problema que podría provocar problemas de conexión al crear una cuenta externa para Snowflake como base de datos externa. (NEO-45744)
* Se ha corregido un problema que podría provocar la visualización de información de tabla protegida por un atributo visibleIf. (NEO-37865)
* Se ha corregido un problema que podía mostrar el mensaje de error &quot;$ is not defined&quot; durante la fase de análisis de entrega. (NEO-32940)
* Se ha corregido un problema que provocaba que las entregas se asociaran con un eventType incorrecto. (NEO-45743)
* Se ha corregido un problema que podría provocar bloqueos debido a volcados de núcleo intermitentes (NEO-30549)
* Se ha corregido un problema que podía provocar bloqueos al utilizar código de HTML erróneo en una entrega. (NEO-40385)
* Se ha corregido un problema que podía impedir que los usuarios no administradores accedieran a la pestaña **Análisis** en las propiedades de entrega. (NEO-34025)
* Se ha corregido un problema que podía impedir que una imagen se cargara en modo de fragmento desde un servidor externo durante la preparación del mensaje. (NEO-40307)

## ![](assets/do-not-localize/green_2.png) Versión 7.2.2, compilación 9349 {#release-7-2-2}

_1 de marzo de 2022_

>[!NOTE]
>
> Esta compilación es compatible con la consola de cliente versión 7.2.1.

**Parches**

* Se ha corregido un problema que se producía al configurar la cuenta externa de **Web Analytics**, lo que provocaba que el estado de la integración siempre mostrase “Integración correcta” incluso cuando se producían errores. (NEO-36672)
* Se han corregido varios errores posteriores a la actualización relacionados con el mecanismo de ID de secuencia al tener ID negativos. (NEO-43205, NEO-42846, NEO-42845)
* Se ha corregido un problema que se producía al usar la cuenta externa de **Web Analytics** con entregas recurrentes y continuas, lo que provocaba que se perdieran parcialmente los datos de la cuenta externa. (NEO-38548)
* Se ha corregido un problema que ralentizaba la actualización posterior a la actualización de la tabla NmsActiveContact. (NEO-43206)
* Se ha corregido un problema de error posterior a la actualización que se producía si las carpetas integradas se habían movido del nodo **Administración** a cualquier otra ubicación. (NEO-42875)
* Se ha corregido un problema que se producía al usar una actividad de flujo de trabajo de **Actualización de datos** que podría evitar que el esquema del destinatario se actualice con los datos del destinatario de una base de datos externa de Google Cloud. (NEO-42343)
* Se ha corregido un problema durante la posactualización relacionado con el conector de Adobe Analytics. (NEO-43318, NEO-38136)
* Se ha corregido un problema de CUID sobrescrito por VALUE_TO_CHANGE durante la posactualización. (NEO-43267)
* Se ha corregido un problema que provocaba errores al sincronizar las instancias de intermediario y marketing en una configuración con varios intermediarios. (NEO-10432)
* Se ha corregido un problema que provocaba un error al actualizar el flujo de trabajo de la capacidad de entrega cuando se tenían más de 1000 broadlogs al mismo tiempo. (NEO-40276)
* Se ha corregido un problema que impedía que los indicadores de entrega de proporción de clics y proporción de aperturas se actualizaran automáticamente. (NEO-43253)

## ![](assets/do-not-localize/limited_2.png) Versión 7.2.1, compilación 9346 {#release-7-2-1}

_10 de enero de 2022_

**Mejora de la seguridad**

Se han realizado varias mejoras de seguridad en las cuentas de FDA:

* Al configurar la cuenta externa de FDA, ahora puede iniciar sesión en la cuenta de Snowflake mediante la autenticación de par de claves para mejorar la seguridad de la autenticación. [Más información](../../installation/using/configure-fda-snowflake.md)
* Al configurar la cuenta externa de FDA, ahora puede iniciar sesión en la cuenta de Azure Synapse Analytics con la identidad administrada asignada al sistema. [Más información](../../installation/using/configure-fda-synapse.md#azure-external)
* Todas las referencias a la biblioteca log4j se han eliminado de Campaign para garantizar una seguridad óptima.

**Actualizaciones de compatibilidad**

Adobe Campaign ahora es compatible con Windows Server 2019. Consulte la [Matriz de compatibilidades de Campaign](../../rn/using/compatibility-matrix.md#OperatingSystems).

**Mejoras**

* Conector CRM 365 de Microsoft Dynamics

   Se han aplicado correcciones críticas con respecto a la API web del conector de Microsoft Dynamics:

   * Se ha corregido un problema durante una importación desencadenada por un flujo de trabajo que provocaba que los valores nulos de los campos de tipo cadena se guardaran como Null en lugar de valores vacíos.
   * Se ha corregido un problema que provocaba el siguiente error en la importación o exportación de datos mediante llamadas a la API web: “URI no válido: El esquema de URI es demasiado largo”.
   * Se han corregido varios problemas al importar, desde Microsoft Dynamics 365, datos que contenían campos de búsqueda.

* Conector de FDA de Google BigQuery

   * El conector FDA de Google, BigQuery, ya está disponible para implementaciones alojadas. [Más información](../../installation/using/configure-fda-google-big-query.md)
   * Se ha agregado compatibilidad para habilitar conexiones a un servidor proxy para el conector FDA de Google, BigQuery. Las opciones de proxy requeridas se pueden configurar mediante el campo Opciones de la configuración de cuenta externa. [Más información](../../installation/using/configure-fda-google-big-query.md#google-external)

**Otros cambios**

* Tras su desuso, las actividades de acción Microsoft CRM, Salesforce, Oracle CRM bajo demanda se han eliminado de la interfaz. Para configurar la sincronización de datos entre Adobe Campaign y un sistema CRM, puede utilizar la actividad del conector de CRM. [Más información](../../workflow/using/crm-connector.md)
* El campo **[!UICONTROL Encrypted identifier]** se ha añadido al esquema del visitante (nms:visitante). Este campo se calcula y se utiliza para aplicaciones web. Esto se aplica cuando el canal de línea está configurado en la instancia intermediaria.
* Ahora, las fuentes de datos CRM se pueden usar con la actividad **Cambiar fuente de datos**.
* Se ha añadido una nueva opción en las propiedades de la **Gestión de errores** de las actividades de flujo de trabajo: la opción **Anular por error** detendrá automáticamente el flujo de trabajo. No podrá reiniciarlo posteriormente (NEO-29661). [Más información](../../workflow/using/advanced-parameters.md#in-case-of-errors)
* Ahora se utiliza una secuencia dedicada para generar las claves principales de la tabla nmsGroup, que se utiliza para crear grupos estadísticos de destinatarios. Anteriormente, se utilizaba la secuencia xtknewId. (NEO-30832)
* Se ha agregado compatibilidad con operaciones de actualización por lotes mediante la actividad conector de CRM.
* Rendimiento mejorado para el tiempo de procesamiento de la mensajería transaccional. (NEO-40370)

**Parches**

* Se ha corregido un problema al crear una entrega que provocaba un error en la pestaña **Imágenes** de la ventana **Seguimiento e imágenes**. Esto ocurría al usar una configuración de proxy automática. (NEO-33260)
* Se ha corregido un problema que podía impedir que se cargara un archivo en un servidor Debian 10 (HTTPS) en modo sincrónico.
* Se ha corregido un problema que podía impedir los registros de la tabla de estadísticas de envíos (`nmsDeliveryLogStats`) para que no se purgue de la instancia de intermediario durante la limpieza de la base de datos después de que se hayan eliminado los envíos relacionados. (NEO-31034)
* Se ha corregido un problema que impedía enviar notificaciones de aplicaciones móviles en iOS al usar autenticación basada en token (NEO-38640).
* Se ha corregido un problema que podía mostrar mensajes de error de scripts al intentar crear y configurar informes (NEO-38393).
* Se ha corregido un problema que podría provocar que el flujo de trabajo de seguimiento falle en Oracle debido a que los altos volúmenes de indicadores de entrega se actualizan simultáneamente (NEO-39653).
* Se ha corregido un problema que podía impedir que se enviara una entrega debido a un error que se producía al ejecutar una tipología de control (NEO-39833).
* Se ha corregido un problema en las páginas de aterrizaje que podía impedir que los caracteres especiales se mostraran correctamente en las páginas HTML de las respuestas de encuestas en línea (NEO-39438).
* Se ha corregido un problema que podía impedir que la consola de Campaign Classic funcionara al hacer clic con el botón derecho en cualquiera de las carpetas desde la pestaña Explorer (NEO-38884).
* Se ha corregido un error al usar una plantilla de envíos creada anteriormente y vinculada a una cuenta de Web Analytics en una nueva entrega en la que faltaba la configuración de Web Analytics. (NEO-28666)
* Se ha corregido un problema que podía impedir que previsualizara los envíos móviles adjuntos a un flujo de trabajo.
* Se ha corregido un error que impedía que se redirigieran las direcciones URL de seguimiento personalizadas cuando el mecanismo de firma de URL para el seguimiento de vínculos estaba habilitado.
* Se ha corregido un problema que podría provocar errores después de la actualización debido a un problema con la administración de índices.
* Se ha corregido un error que se producía al usar tipos de datos de campo de búsqueda con Microsoft Dynamics CRM en **Importar** o **Exportar** actividades de flujo de trabajo.
* Se ha corregido un problema que podía impedir que los usuarios iniciaran sesión en la consola debido a un problema de configuración de proxy. (NEO-38388)
* Se ha corregido un problema de regresión que impedía que la funcionalidad **Purgar carpeta** funcionara correctamente. (NEO-37459)
* Se ha corregido un problema que provocaba un error de solicitud incorrecto al usar campos de datos xml con la cuenta de Microsoft Dynamics CRM si el xml al que se hace referencia contenía comillas dobles.
* Se ha corregido un problema que provocaba que los problemas de tiempo de espera de red se registraran incorrectamente como problemas de interrupción de scripts en lugar de errores de red. Este problema ocurría en el caso de solicitudes HTTP incluidas en actividades JavaScript. (NEO-38079)
* Se ha corregido un problema que devolvía resultados incorrectos al ejecutar las funciones Amazon Redshift HoursDiff y MinutesDiff al intentar extraer el componente de tiempo.(NEO-31673)
* Se ha corregido un problema que impedía que el informe de **Clics activos** cargara para entregas desde la versión 9182. (NEO-28900)
* Se ha corregido un error que reemplazaba el símbolo &amp; en una dirección URL con la referencia de entidad de carácter (`&amp;`) que impedía a los usuarios acceder a la URL vinculada a un código QR. (NEO-28621)
* Se ha corregido un problema que creaba una nueva cuenta externa cada vez que un usuario creaba un nuevo flujo de trabajo de campaña y una actividad de entrega vinculada a una cuenta de Web Analytics. Esto se debía a la falta de un ID en el objeto de entrega webAnalyticsAccount. (NEO-39691)
* Se ha corregido un problema que podía impedir que la actividad de flujo de trabajo **Leer lista** funcionara cuando la lista se identificaba en la base de datos con un ID negativo. (NEO-39607)
* Se ha corregido un problema que podría provocar que el flujo de trabajo **Intermediario (registros de envío)** falle. (NEO-39662)
* Se ha corregido un problema que podía impedir que previsualizara los envíos de correo electrónico adjuntos a un flujo de trabajo. (NEO-37840)
* Se ha corregido un problema que podía hacer que el flujo de trabajo de limpieza de la base de datos eliminara tablas válidas que contenían valores de lista. (NEO-34911)
* Se ha corregido un problema que podía provocar que el flujo de trabajo de facturación se bloqueara en las instancias de marketing.
