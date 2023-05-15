---
product: campaign
title: Archivos de registro
description: Archivos de registro
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
badge-v7-prem: label="on-premise & hybrid" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=en" tooltip="Applies to on-premise and hybrid deployments only"
audience: production
content-type: reference
topic-tags: production-procedures
exl-id: c9d427da-6965-4945-90f0-d0770701d55e
source-git-commit: a5762cd21a1a6d5a5f3a10f53a5d1f43542d99d4
workflow-type: tm+mt
source-wordcount: '431'
ht-degree: 2%

---

# Archivos de registro{#log-files}



Los archivos de registro están organizados de la siguiente manera:

![](assets/d_ncs_directory.png)

Cada **nlserver** genera un archivo de registro guardado en el siguiente directorio: **`<installation directory>`/var/`<instance>`/log/`<module>`.log**.

La variable **nlserver syslogd** guarda los registros en el disco. Este módulo es similar a Unix **syslog daemon**, pero se ha adaptado para la compatibilidad entre Unix y Windows. Los demás módulos Adobe Campaign no guardan sus registros en el disco; delegan esta tarea a la **syslogd** enviando paquetes UDP.

De forma predeterminada, la plataforma Adobe Campaign tiene la variable **syslogd** módulo instalado en él, pero es posible utilizar otro **syslog daemon**. Este módulo crea los archivos de registro en la variable **log** directorio.

Los registros de módulos de varias instancias se almacenan en el siguiente directorio: **`<installation directory>`/var/default/log/**. Todas las instancias comparten el mismo archivo de registro (p. ej. **web.log**).

Los registros de los demás módulos se almacenan en una subcarpeta denominada como la instancia de . Cada instancia tiene sus propios archivos de registro.

Los archivos de registro de varias instancias se enumeran en la siguiente tabla:

| Archivo | Descripción |
|---|---|
| web.log | Registros de módulos web (consola de cliente, informes, API SOAP, etc.) |
| webmdl.log | Registros del módulo de redirección |
| watchdog.log | Registros del módulo de monitorización de procesos de Adobe Campaign |
| trackinglogd.log | Registros de seguimiento |

Los archivos de registro de instancia única se enumeran en la siguiente tabla:

| Archivo | Descripción |
|---|---|
| mta.log | registros de módulo mta |
| mtachild.log | Registros de procesamiento de entrega de mensajes |
| wfserver.log | Registros del módulo del servidor de flujo de trabajo |
| runwf.log | Registros de ejecución del flujo de trabajo |
| inMail.log | Registro del módulo de correo rechazado |
| logins.log | Registra todos los intentos de inicio de sesión en Adobe Campaign (éxito o no) |

>[!IMPORTANT]
>
>La variable **redir** solo existe en los servidores de redirección. La variable **url** El subdirectorio contiene las coincidencias de las direcciones URL que se van a redirigir y el subdirectorio **log** contiene los registros de seguimiento. Para generar registros de seguimiento, la variable **trackinglogd** debe estar ejecutándose.

Para optimizar el rendimiento y el almacenamiento, el archivo logins.log se divide en varios archivos, uno cada día (logins.yy-mm-dd.log) con un máximo de 365 archivos retenidos. El número de días se puede cambiar en serverConf.xml, en syslogd (**maxNumberOfLoginsFiles** ). Consulte la documentación de [archivo de configuración del servidor](../../installation/using/the-server-configuration-file.md#syslogd).

De forma predeterminada, los registros están limitados a dos archivos de 10 MB por módulo y por instancia. El segundo archivo se llama: **`<modulename>`_2.log**. Por lo tanto, el tamaño de los registros está limitado a 2&#42;10 MB por módulo y por instancia.

Sin embargo, puede mantener archivos más grandes. Para habilitar esto, cambie el valor de la variable **maxFileSizeMb=&quot;10&quot;** en la **syslogd** nodo de la variable **conf/serverConf.xml** archivo. Este valor representa el tamaño máximo en MB de un archivo de registro.

Si desea mantener más niveles de detalle en los registros, puede iniciar los módulos de Adobe Campaign con la variable **-verbose** parámetro:

**inicio de nlserver `<MODULE>`@`<INSTANCE>` -verbose**
