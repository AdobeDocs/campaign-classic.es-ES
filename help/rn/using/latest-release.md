---
product: campaign
title: Último lanzamiento
description: Notas de la versión más reciente de Campaign Classic v7
feature: Release Notes
role: User
level: Beginner
exl-id: d65869ca-a785-4327-8e8d-791c28e4696c
source-git-commit: 86bc3bdfe628cc694e47a4670e99225e05b3df1b
workflow-type: ht
source-wordcount: '224'
ht-degree: 100%

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

### Correcciones {#release-7-4-2-fixes}

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

En esta versión se han corregido también los siguientes problemas:

NEO-47269, NEO-59059, NEO-62455, NEO-65774, NEO-66462, NEO-66989, NEO-77898, NEO-78843, NEO-79373, NEO-79598, NEO-80145, NEO-80245, NEO-80434, NEO-80683, NEO-81222, NEO-81433, NEO-81864, NEO-82351, NEO-82781, NEO-82838, NEO-82923, NEO-83252, NEO-83809, NEO-83826, NEO-84024, NEO-84553, NEO-85150

