---
solution: Campaign Classic
product: campaign
title: Archivos de registro
description: Archivos de registro
audience: production
content-type: reference
topic-tags: production-procedures
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '431'
ht-degree: 2%

---


# Archivos de registro{#log-files}

Los archivos de registro están organizados de la siguiente manera:

![](assets/d_ncs_directory.png)

Cada módulo **nlserver** genera un archivo de registro guardado en el siguiente directorio: **`<installation directory>`/var/`<instance>`/log/`<module>`.log**.

El módulo **nlserver syslogd** guarda los registros en el disco. Este módulo es similar al daemon Unix **syslog**, pero se ha adaptado para la compatibilidad entre Unix y Windows. Los demás módulos de Adobe Campaign no guardan sus registros en el disco; delegan esta tarea al módulo **syslogd** enviándole paquetes UDP.

De forma predeterminada, la plataforma Adobe Campaign tiene instalado el módulo **syslogd**, pero es posible utilizar otro **daemon syslog**. Este módulo crea los archivos de registro en el directorio **log**.

Los registros de módulos de varias instancias se almacenan en el siguiente directorio: **`<installation directory>`/var/default/log/**. Todas las instancias comparten el mismo archivo de registro (p. ej. **web.log**).

Los registros de los demás módulos se almacenan en una subcarpeta con el nombre de la instancia. Cada instancia tiene sus propios archivos de registro.

Los archivos de registro de varias instancias se enumeran en la siguiente tabla:

| Archivo | Descripción |
|---|---|
| web.log | Registros de módulos Web (consola de cliente, informes, API de SOAP, etc.) |
| webmdl.log | Registros del módulo de redirección |
| watchdog.log | Registros del módulo de supervisión de procesos de Adobe Campaign |
| trackinglogd.log | Registros de seguimiento |

Los archivos de registro de instancia única se enumeran en la tabla siguiente:

| Archivo | Descripción |
|---|---|
| mta.log | registros de módulos mta |
| mtachild.log | Registros de procesamiento del envío de mensajes |
| wfserver.log | Registros del módulo del servidor de flujo de trabajo |
| runwf.log | Registros de ejecución de flujo de trabajo |
| inMail.log | Registro del módulo de correo de devolución |
| logins.log | Registra todos los intentos de inicio de sesión en Adobe Campaign (exitosos o no) |

>[!IMPORTANT]
>
>El directorio **redir** sólo existe en los servidores de redirección. El subdirectorio **url** contiene las coincidencias de las direcciones URL que se van a redirigir y el subdirectorio **log** contiene las registros de seguimiento. Para generar registros de seguimiento, el módulo **trackinglogd** debe estar en ejecución.

Para optimizar el rendimiento y el almacenamiento, el archivo inicios de sesión.log se divide en varios archivos, uno cada día (inicios de sesión.yy-mm-dd.log) con un máximo de 365 archivos retenidos. El número de días se puede cambiar en serverConf.xml, en syslogd (**maxNumberOfLoginsFiles** opción). Consulte la documentación del [archivo de configuración del servidor](../../installation/using/the-server-configuration-file.md#syslogd).

De forma predeterminada, los registros están limitados a dos archivos de 10 MB por módulo y por instancia. El segundo archivo se denomina: **`<modulename>`_2.log**. Por lo tanto, el tamaño de los registros está limitado a 2*10 MB por módulo y por instancia.

Sin embargo, puede guardar archivos más grandes. Para habilitarlo, cambie el valor de la configuración **maxFileSizeMb=&quot;10&quot;** en el nodo **syslogd** del archivo **conf/serverConf.xml**. Este valor representa el tamaño máximo en MB de un archivo de registro.

Si desea mantener más niveles de detalle en los registros, puede inicio de los módulos de Adobe Campaign con el parámetro **-verbose**:

**nlserver inicio  `<MODULE>`@`<INSTANCE>` -verbose**
