---
product: campaign
title: Archivos de registro
description: Archivos de registro
audience: production
content-type: reference
topic-tags: production-procedures
exl-id: c9d427da-6965-4945-90f0-d0770701d55e
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: tm+mt
source-wordcount: '431'
ht-degree: 2%

---

# Archivos de registro{#log-files}

Los archivos de registro están organizados de la siguiente manera:

![](assets/d_ncs_directory.png)

Cada módulo **nlserver** genera un archivo de registro guardado en el siguiente directorio: **`<installation directory>`/var/`<instance>`/log/`<module>`.log**.

El módulo **nlserver syslogd** guarda los registros en el disco. Este módulo es similar al demonio **syslog** de Unix, pero se ha adaptado para la compatibilidad entre Unix y Windows. Los demás módulos Adobe Campaign no guardan sus registros en el disco; delegan esta tarea al módulo **syslogd** enviándole paquetes UDP.

De forma predeterminada, la plataforma Adobe Campaign tiene instalado el módulo **syslogd**, pero es posible utilizar otro **syslog daemon**. Este módulo crea los archivos de registro en el directorio **log**.

Los registros de módulos de varias instancias se almacenan en el siguiente directorio: **`<installation directory>`/var/default/log/**. Todas las instancias comparten el mismo archivo de registro (p. ej. **web.log**).

Los registros de los demás módulos se almacenan en una subcarpeta denominada como la instancia de . Cada instancia tiene sus propios archivos de registro.

Los archivos de registro de varias instancias se enumeran en la siguiente tabla:

| Archivo | Descripción |
|---|---|
| web.log | Registros de módulos web (consola de cliente, informes, API SOAP, etc.) |
| webmdl.log | Registros del módulo de redirección |
| watchdog.log | Registros del módulo de monitorización del proceso de Adobe Campaign |
| trackinglogd.log | Registros de seguimiento |

Los archivos de registro de instancia única se enumeran en la siguiente tabla:

| Archivo | Descripción |
|---|---|
| mta.log | registros de módulo mta |
| mtachild.log | Registros de procesamiento de entrega de mensajes |
| wfserver.log | Registros del módulo del servidor de flujo de trabajo |
| runwf.log | Registros de ejecución del flujo de trabajo |
| inMail.log | Registro del módulo de correo rechazado |
| logins.log | Registra todos los intentos de inicio de sesión en Adobe Campaign (exitosos o no) |

>[!IMPORTANT]
>
>El directorio **redir** solo existe en los servidores de redirección. El subdirectorio **url** contiene las coincidencias de las direcciones URL que se van a redirigir y el subdirectorio **log** contiene los registros de seguimiento. Para generar registros de seguimiento, el módulo **trackinglogd** debe estar ejecutándose.

Para optimizar el rendimiento y el almacenamiento, el archivo logins.log se divide en varios archivos, uno cada día (logins.yy-mm-dd.log) con un máximo de 365 archivos retenidos. El número de días se puede cambiar en serverConf.xml, en syslogd (**maxNumberOfLoginsFiles** opción). Consulte la documentación del [archivo de configuración del servidor](../../installation/using/the-server-configuration-file.md#syslogd).

De forma predeterminada, los registros están limitados a dos archivos de 10 MB por módulo y por instancia. El segundo archivo se llama: **`<modulename>`_2.log**. Por lo tanto, el tamaño de los registros está limitado a 2*10 MB por módulo y por instancia.

Sin embargo, puede mantener archivos más grandes. Para habilitarlo, cambie el valor de la configuración **maxFileSizeMb=&quot;10&quot;** en el nodo **syslogd** del archivo **conf/serverConf.xml**. Este valor representa el tamaño máximo en MB de un archivo de registro.

Si desea mantener más niveles de detalle en los registros, puede iniciar los módulos de Adobe Campaign con el parámetro **-verbose**:

**nlserver start  `<MODULE>`@`<INSTANCE>` -verbose**
