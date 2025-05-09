---
product: campaign
title: Último lanzamiento
description: Notas de la versión más reciente de Campaign Classic v7
feature: Release Notes
role: User
level: Beginner
exl-id: d65869ca-a785-4327-8e8d-791c28e4696c
source-git-commit: 458821770c6233ec1893d4efe60169516b311bdd
workflow-type: tm+mt
source-wordcount: '865'
ht-degree: 26%

---

# Último lanzamiento {#latest-release}

Esta página lista las nuevas funcionalidades, mejoras y correcciones que se proporcionan con la **última versión de Campaign Classic v7**. Cada nueva compilación viene con un estado que se materializa con un color. Obtenga más información sobre los estados de compilación de Campaign Classic v7 en [esta página](rn-overview.md).

## Versión 7.4.2, compilación 9390 {#release-7-4-2}

[!BADGE Disponibilidad general]{type=Positive url="https://experienceleague.adobe.com/docs/campaign-classic/using/release-notes/rn-overview.html?lang=es#rn-statuses" tooltip="Disponibilidad general"}

_2 de abril de 2025_

<!--
### Compatibility updates {#comp-7-4-2}

This release comes with the following compatibility updates:

* JQuery library update: fixes multiple UI issues (reports, web apps)
* PostgreSQL 15 and 16

-->

### Mejoras de seguridad {#security-7-4-2}

Esta versión incluye varias correcciones de seguridad.

La conexión con las soluciones y aplicaciones de Adobe a través de la cuenta externa de **[!UICONTROL Adobe Experience Cloud]** se ha actualizado para reforzar la seguridad.

### Correcciones principales {#release-7-4-2-fixes}

Esta versión incluye las siguientes correcciones principales:

* Conexión TLS/SMPP: se han corregido problemas de estabilidad de SMPP

* Correcciones de Google BigQuery:

   * Se han corregido regresiones en tipos de datos BOOLEAN
   * Se han corregido problemas de configuración de proxy
   * Se han corregido regresiones en tipos de datos DATETIME
   * Se ha corregido la estabilidad de carga masiva
   * Se han mejorado las pruebas internas en versiones de ODBC
   * Se ha corregido un problema con los caracteres especiales en la cadena de conexión
   * Se ha quitado el tiempo de espera predeterminado (5 minutos) en las consultas de Google BigQuery

* Agente de transferencia de correo (MTA): se ha corregido que un elemento secundario de MTA huérfano quede bloqueado en estado **[!UICONTROL Start pending]**.


### Otras correcciones {#release-7-4-2-other-fixes}

En esta versión se han corregido también los siguientes problemas:

* Se ha corregido un problema en el cual la actividad **Carga de datos (archivo)** no podía cargar archivos en el servidor<!--after an upgrade to version 8.3.8-->. Los usuarios ahora pueden cargar archivos correctamente sin encontrar errores de consola o progreso atascado. (NEO-47269)

* Se han resuelto errores de segmentación en Apache <!--following an upgrade to Adobe Campaign Classic 7.2.2 build 9349-->. Esta corrección evita la generación de archivos principales y garantiza un funcionamiento estable del servidor. (NEO-59059)

* Se corrigió un problema de conectividad con la base de datos de Google BigQuery <!--after upgrading to version 7.3.3 build 9359-->. Los usuarios ahora pueden probar las conexiones correctamente con la cuenta externa de GCP. (NEO-62455)

* Compatibilidad mejorada para actualizaciones de columnas booleanas y datetime en tablas de Google BigQuery mediante el acceso de datos federado (FDA). Esta corrección garantiza la administración adecuada de los tipos de datos durante las operaciones de inserción y actualización. (NEO-65774)

* Se ha corregido una vulnerabilidad de inyección de recursos que permitía a los atacantes insertar elementos de HTML en puntos finales de correo electrónico. Esta mejora de seguridad evita el acceso no autorizado y los intentos de phishing. (NEO-66462)

* Se han resuelto errores intermitentes al insertar datos en tablas de Google BigQuery debido a problemas de codificación de contenido HTTP o de transferencia. Esta corrección garantiza flujos de trabajo de carga de datos estables. (NEO-66989)

* Se corrigió una vulnerabilidad de recorrido de ruta en el método `File.list()` dentro de los flujos de trabajo. Esta mejora de seguridad evita el acceso no autorizado a directorios y protege los archivos confidenciales. (NEO-77898)

* Se ha corregido un problema por el cual los registros de envío de SMS no se actualizaban correctamente al estado &quot;recibido en el móvil&quot;. Esta mejora garantiza unos informes de envío precisos. (NEO-78843)

* Se han resuelto errores de inicio de sesión en Adobe Campaign Classic al utilizar el acceso de datos federado de Azure (FDA). Los usuarios ahora pueden iniciar sesión correctamente a través de la consola del cliente. (NEO-79373)

* Se corrigió un bloqueo en los flujos de trabajo causado por el método `CCurlAzureBlobStorage::UploadStream()`. Esta mejora garantiza una ejecución estable del flujo de trabajo. (NEO-79598)

* Se activaron dos indicadores de compilación esenciales (`ControlFlowGuard` y `StackProtection`) en Windows para mejorar la seguridad del producto y mitigar los riesgos de explotación. (NEO-80145)

* Se ha corregido un problema por el cual los estados de eventos se enviaban incorrectamente mientras el &quot;broadlog&quot; estaba en estado fallido. Esta mejora garantiza unos informes de eventos precisos. (NEO-80245)

* La actualización POP3 de OAuth y el token de acceso ahora se guardan en la base de datos y el error `Authentication failure: unknown user name or bad password` ya no aparece después de que caduque el token de actualización. (NEO-80683)

* Ahora se usa una opción `XApiKey` como valor para que el ID de cliente se conecte a Adobe Analytics en lugar de usar el ID de cliente de la cuenta externa de Marketing Cloud (MAC). (NEO-80434)

* Se ha resuelto un problema en el cual los usuarios de inMail encontraban errores de autenticación debido a la caducidad del token. Los usuarios ahora pueden probar la conexión y reiniciar el servidor para resolver problemas similares. (NEO-80683)

* Se ha mejorado la funcionalidad de la API de Analytics al garantizar que todas las llamadas de Analytics utilicen una clave de API coherente (Campaign1) para la autenticación, incluso al cambiar a un ID de cliente aleatorio. Esto garantiza un seguimiento de análisis sin problemas. (NEO-80434)

* Se ha mejorado el conector de acceso de datos federado (FDA) de BigQuery, lo que permite a los usuarios ajustar el periodo de espera para las consultas. Esta mejora evita errores de tiempo de espera durante las consultas de larga ejecución. (NEO-81222)

* Se ha actualizado el proceso de actualización de la versión de Campaign <!--7.4.1--> para incluir las dependencias necesarias. Esta mejora simplifica el proceso de actualización para los usuarios. (NEO-81433)

* Se corrigió un problema con el bloqueo de la consola al utilizar un subflujo de trabajo en combinación con un campo `enum`. Esta mejora garantiza una ejecución estable del flujo de trabajo. (NEO-81864)

* Se ha resuelto un problema en el que los procesos secundarios de MTA se quedaban atascados, lo que bloqueaba las ranuras de entrega. Esta corrección garantiza operaciones de entrega sin problemas para las comunicaciones push y WhatsApp. (NEO-82351)

* Se ha corregido un problema por el cual los envíos se quedaban atascados en la personalización pendiente debido a actividades de envío pausadas. Esta mejora garantiza la ejecución correcta de la entrega. (NEO-82781)

* Se ha mejorado la funcionalidad de inicio de sesión de IMS al aprovechar el extremo CampaignIO para la autenticación. Esta mejora optimiza el proceso de inicio de sesión. (NEO-82838)

* Se han vuelto a abordar los errores de tiempo de espera de acceso de datos federado (FDA) de Google BigQuery para garantizar una ejecución de consulta estable tras la implementación de correcciones. (NEO-82923)

* Se ha resuelto un problema de espacio al cargar volúmenes de datos grandes en tablas de Teradata. Esta mejora garantiza operaciones de carga de datos estables. (NEO-83252)

* Se corrigió un problema en el cual las consultas GCP fallaban debido a que las comparaciones de fecha y marca de tiempo <!--after upgrading to version 9383--> no coincidían. Esta mejora garantiza la compatibilidad de las consultas. (NEO-83826)

* Se corrigieron errores de entrega causados por la reanudación de actividades de entrega en pausa. Esta corrección garantiza la ejecución correcta de la entrega. (NEO-83809)

* Se han corregido errores de autenticación con el conector de acceso de datos federado (FDA) de Snowflake al utilizar la autenticación de clave privada. Esta mejora garantiza conexiones de base de datos correctas. (NEO-84024)

* Se han implementado cambios de vigilante para abordar el bloqueo de ranuras secundarias MTA causado por procesos atascados. Esta mejora garantiza unas operaciones de envío sin problemas. (NEO-84553)

* Comprobaciones de espera de Javascript aumentadas para solucionar el bloqueo de ranura secundaria de MTA causado por procesos en estado operativo. Esta corrección garantiza operaciones de envío estables. (NEO-85150)

