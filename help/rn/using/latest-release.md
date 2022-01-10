---
product: campaign
title: Última versión
description: Últimas notas de la versión 7.0 de Campaign Classic
feature: Overview
role: User
level: Beginner
exl-id: d65869ca-a785-4327-8e8d-791c28e4696c
source-git-commit: e4dfdd32c07753ee9e202ab4e4bf815485e47d8b
workflow-type: tm+mt
source-wordcount: '1032'
ht-degree: 17%

---

# Último lanzamiento{#latest-release}

![](../../assets/v7-only.svg)

Esta página enumera las nuevas funcionalidades, mejoras y correcciones que se incluyen con la **última versión de Campaign Classic v7**. Cada nueva compilación viene con un estado que se materializa con un color. Obtenga más información sobre los estados de compilación de Campaign Classic v7 en [esta página](rn-overview.md).

## ![](assets/do-not-localize/green_2.png) Versión 7.2.1, compilación 9346 {#release-7-2-1}

_10 de enero de 2022_

**Mejora de la seguridad**

Se han realizado varias mejoras de seguridad en las cuentas de FDA:

* Los controladores ODBC ahora se instalan directamente con terceros de Adobe Campaign. Ya no es necesario realizar pasos manuales para instalar estos controladores.
* Al configurar la cuenta externa de FDA, ahora puede iniciar sesión en la cuenta de Snowflake mediante la autenticación de par de claves para mejorar la seguridad de la autenticación. [Más información](../../installation/using/configure-fda-snowflake.md)
* Al configurar la cuenta externa de FDA, ahora puede iniciar sesión en la cuenta de Azure synapse Analytics con la identidad administrada asignada al sistema. [Más información](../../installation/using/configure-fda-synapse.md#azure-external)


**Mejoras**

* Conector de Microsoft Dynamics CRM 365

   Se han aplicado correcciones críticas con respecto a la API web del conector de Microsoft Dynamics:

   * Se ha corregido un problema durante una importación desencadenada por un flujo de trabajo que provocaba que los valores nulos de los campos de tipo cadena se guardaran como Null en lugar de valores vacíos.
   * Se ha corregido un problema que provocaba el siguiente error en la importación o exportación de datos mediante llamadas a la API web: &quot;URI no válido: El esquema de URI es demasiado largo&quot;.
   * Se han corregido varios problemas al importar, desde Microsoft Dynamics 365, datos que contenían campos de búsqueda.

* Conector de FDA de Google BigQuery

   * El conector FDA BigQuery de Google ya está disponible para implementaciones alojadas. [Más información](../../installation/using/configure-fda-google-big-query.md)
   * Se ha agregado compatibilidad para habilitar conexiones a un servidor proxy para el conector FDA Google BigQuery. Las opciones de proxy requeridas se pueden configurar mediante el campo Opciones de la configuración de cuenta externa. [Más información](../../installation/using/configure-fda-google-big-query.md#google-external)

**Otros cambios**

* Tras su desaprobación, las actividades de acción Microsoft CRM, Salesforce, Oracle CRM On Demand se han eliminado de la interfaz. Para configurar la sincronización de datos entre Adobe Campaign y un sistema CRM, puede utilizar la actividad Conector de CRM . [Más información](../../workflow/using/crm-connector.md)
* La variable **[!UICONTROL Encrypted identifier]** se ha añadido al esquema del visitante (nms:visitor). Este campo se calcula y se utiliza para aplicaciones web. Esto se aplica cuando el canal de línea está configurado en la instancia de mid-sourcing.
* Ahora, las fuentes de datos CRM se pueden usar con la variable **Cambiar fuente de datos** actividad.
* Se ha añadido una nueva opción en el **Gestión de errores** propiedades de las actividades de flujo de trabajo: La variable **Anular por error** detendrá automáticamente el flujo de trabajo. No podrá reiniciarlo posteriormente (NEO-29661). [Más información](../../workflow/using/advanced-parameters.md#in-case-of-errors)
* Ahora se utiliza una secuencia dedicada para generar las claves principales de la tabla nmsGroup , que se utiliza para crear grupos estadísticos de destinatarios. Anteriormente, se utilizaba la secuencia xtknownId. (NEO-30832)
* Se ha agregado compatibilidad con operaciones de actualización por lotes mediante la actividad Conector de CRM .

**Parches**

* Se ha corregido un problema al crear una entrega que provocaba un error en la variable **Imágenes** de la pestaña **Seguimiento e imágenes** ventana. Esto ocurría al usar una configuración de proxy automática. (NEO-33260)
* Se ha corregido un problema que podía impedir que se cargara un archivo en un servidor Debian 10 (HTTPS) en modo sincrónico.
* Se ha corregido un problema que podía impedir los registros de la tabla de estadísticas de envíos (`nmsDeliveryLogStats`) para que no se purgue de la instancia de intermediario durante la limpieza de la base de datos después de que se hayan eliminado los envíos relacionados. (NEO-31034)
* Se ha corregido un problema que impedía enviar notificaciones de aplicaciones móviles en iOS al usar autenticación basada en token (NEO-38640).
* Se ha corregido un problema que podía mostrar mensajes de error de secuencia de comandos al intentar crear y configurar informes (NEO-38393).
* Se ha corregido un problema que podría provocar que el flujo de trabajo de seguimiento falle en el Oracle debido a que los altos volúmenes de indicadores de envío se actualizan simultáneamente (NEO-39653).
* Se ha corregido un problema que podía impedir que se enviara un envío debido a un error que se producía al ejecutar una tipología de control (NEO-39833).
* Se ha corregido un problema en las páginas de aterrizaje que podía impedir que los caracteres especiales se mostraran correctamente en las páginas HTML de las respuestas de encuestas en línea (NEO-39438).
* Se ha corregido un problema que podía impedir que la consola del Campaign Classic funcionara al hacer clic con el botón derecho en cualquiera de las carpetas desde la pestaña Explorer (NEO-38884).
* Se ha corregido un error al usar una plantilla de envío creada anteriormente y vinculada a una cuenta de Web Analytics en un nuevo envío en el que faltaba la configuración de Web Analytics. (NEO-28666)
* Se ha corregido un problema que podía impedir que previsualizara los envíos móviles adjuntos a un flujo de trabajo.
* Se ha corregido un error que impedía que se redirigieran las direcciones URL de seguimiento personalizadas cuando el mecanismo de firma de URL para el seguimiento de vínculos estaba habilitado.
* Se ha corregido un problema que podría provocar errores después de la actualización debido a un problema con la administración de índices.
* Se ha corregido un error que se producía al usar tipos de datos de campo de búsqueda con Microsoft Dynamics CRM en **Importar** o **Exportar** actividades de flujo de trabajo.
* Se ha corregido un problema que podía impedir que iniciara sesión en la consola debido a un problema de configuración de proxy. (NEO-38388)
* Se ha corregido un problema de regresión que impedía que la funcionalidad **Purgar carpeta** funcionara correctamente. (NEO-37459)
* Se ha corregido un problema que provocaba un error de solicitud incorrecto al usar campos de datos xml con la cuenta de Microsoft Dynamics CRM si el xml al que se hace referencia contenía comillas dobles.
* Se ha corregido un problema que provocaba que los problemas de tiempo de espera de red se registraran incorrectamente como problemas de interrupción de secuencia de comandos en lugar de errores de red. Este problema ocurría en el caso de solicitudes HTTP incluidas en actividades JavaScript. (NEO-38079)
* Se ha corregido un problema que devolvía resultados incorrectos al ejecutar las funciones Amazon Redshift HoursDiff y MinutesDiff al intentar extraer el componente de tiempo.(NEO-31673)
* Se ha corregido un problema que impedía que la variable **Clics activos** informe de carga para entregas desde la compilación 9182. (NEO-28900)
* Se ha corregido un error que reemplazaba el símbolo &amp; en una dirección URL con la referencia de entidad de carácter (`&amp;`) que impiden a los usuarios acceder a la URL vinculada a un código QR. (NEO-28621)
* Se ha corregido un problema que creaba una nueva cuenta externa cada vez que un usuario creaba un nuevo flujo de trabajo de campaña y una actividad de entrega vinculada a una cuenta de Web Analytics. Esto se debía a la falta de un ID en el objeto de entrega webAnalyticsAccount. (NEO-39691)
* Se ha corregido un problema que podía impedir que la actividad de flujo de trabajo **Leer lista** funcionara cuando la lista se identificaba en la base de datos con un ID negativo. (NEO-39607)
* Se ha corregido un problema con que podría provocar que la variable **Mid-sourcing (delivery logs)** para que el flujo de trabajo falle. (NEO-39662)
* Se ha corregido un problema que podía impedir que previsualizara los envíos de correo electrónico adjuntos a un flujo de trabajo. (NEO-37840)
* Se ha corregido un problema que podía hacer que el flujo de trabajo de limpieza de la base de datos eliminara tablas válidas que contenían valores de lista. (NEO-34911)
* Se ha corregido un problema que podía provocar que el flujo de trabajo de facturación se bloqueara en las instancias de marketing.
