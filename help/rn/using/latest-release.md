---
product: campaign
title: Último lanzamiento
description: Notas de la versión más reciente de Campaign Classic v7
feature: Release Notes
role: User
level: Beginner
exl-id: d65869ca-a785-4327-8e8d-791c28e4696c
source-git-commit: 8fec4d038eddaa3c5a2aade1b619f2543453d4de
workflow-type: tm+mt
source-wordcount: '352'
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

* Ahora, cuando un formulario web tiene el estado **Publicación pendiente**, no se activa automáticamente. Para evitar problemas de seguridad, debe publicarse antes de que esté **En línea** y sea accesible a través de la URL del formulario web en un explorador web. [Más información](../../web/using/publishing-a-web-form.md#life-cycle-of-a-form)

### Parches {#release-7-3-5-patches}

* Se ha corregido un problema que se producía al utilizar datos de una base de datos de Google Big Query y al actualizar datos en una base de datos de Oracle: todas las claves se establecían en `0` en la tabla temporal del flujo de trabajo. (NEO-65091)
* Se ha corregido un problema que ocasionaba que fallara una ejecución de flujo de trabajo cuando se combinaban dos consultas en una base de datos de Google Big Query en una actividad de flujo de trabajo de **Union**. (NEO-63705)
* Se ha corregido un problema que consistía en la solicitud al usuario de volverse a autenticar al hacer clic en el botón `Back` en un informe de campaña. (NEO-65087)
* Se ha corregido un error en el flujo de trabajo para la limpieza de base de datos que se producía cuando se eliminaba un envío antes que las pruebas de envío. (NEO-48114)
* Se ha corregido un problema al conectarse a la consola del cliente: las actualizaciones recientes sobre la verificación TLS provocaban un error de conexión. (NEO-50488)
* Se ha corregido un problema con la autenticación proxy HTTP después de la actualización de Campaign a la versión 7.3.1. Las solicitudes HTTP en los flujos de trabajo de la campaña fallaban con `error 407 – proxy auth required is returned`. (NEO-49624)
* Se ha corregido un error intermitente con el descifrado GPG en actividades de flujo de trabajo de **Script**. El mensaje de error asociado era: `gpg: decryption failed: No secret key`. (NEO-50257)
  <!--* Workflow temporary tables now have a primary index in Teradata with a Federated Data Access (FDA) connection. (NEO-62575)-->

