---
title: Archivos de registro
seo-title: Archivos de registro
description: Archivos de registro
seo-description: null
page-status-flag: never-activated
uuid: 266bc067-0218-4b3e-941c-dc5cd0b6a10d
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: production
content-type: reference
topic-tags: production-procedures
discoiquuid: fac3e3ec-82a7-4087-ba88-2b28b0f69d1c
translation-type: tm+mt
source-git-commit: 849e1ebf14f707d9e86c5a152de978acb6f1cb35
workflow-type: tm+mt
source-wordcount: '433'
ht-degree: 3%

---


# Archivos de registro{#log-files}

Los archivos de registro están organizados de la siguiente manera:

![](assets/d_ncs_directory.png)

Cada **módulo nlserver** genera un archivo de registro guardado en el siguiente directorio: **`<installation directory>`/var/`<instance>`/log/`<module>`.log**.

El **módulo syslogd** de nlserver guarda los registros en el disco. Este módulo es similar al demonio **** syslog Unix, pero se ha adaptado para la compatibilidad entre Unix y Windows. Los demás módulos de Adobe Campaign no guardan sus registros en el disco; delegan esta tarea al módulo **syslogd** enviándole paquetes UDP.

De forma predeterminada, la plataforma Adobe Campaign tiene instalado el módulo **syslogd** , pero es posible utilizar otro demonio **syslog**. Este módulo crea los archivos de registro en el directorio de **registro** .

Los registros de módulos de varias instancias se almacenan en el siguiente directorio: **`<installation directory>`/var/default/log/**. Todas las instancias comparten el mismo archivo de registro (por ejemplo, **web.log**).

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
>El directorio **redir** solo existe en los servidores de redirección. El subdirectorio **url** contiene las coincidencias de las direcciones URL que se van a redirigir y el **registro** de subdirectorio contiene las registros de seguimiento. Para generar registros de seguimiento, el módulo **trackinglogd** debe estar en ejecución.

Para optimizar el rendimiento y el almacenamiento, el archivo inicios de sesión.log se divide en varios archivos, uno cada día (inicios de sesión.yy-mm-dd.log) con un máximo de 365 archivos retenidos. El número de días se puede cambiar en serverConf.xml, en syslogd (opción **maxNumberOfLoginsFiles** ). Consulte la documentación del archivo [de configuración del](../../installation/using/the-server-configuration-file.md#syslogd)servidor.

De forma predeterminada, los registros están limitados a dos archivos de 10 MB por módulo y por instancia. El segundo archivo se denomina: **`<modulename>`_2.log**. Por lo tanto, el tamaño de los registros está limitado a 2*10 MB por módulo y por instancia.

Sin embargo, puede guardar archivos más grandes. Para habilitarlo, cambie el valor de la configuración **maxFileSizeMb=&quot;10&quot;** en el nodo **syslogd** del archivo **conf/serverConf.xml** . Este valor representa el tamaño máximo en MB de un archivo de registro.

Si desea mantener más niveles de detalle en los registros, puede inicio de los módulos de Adobe Campaign con el parámetro **-verbose** :

**nlserver inicio `<MODULE>`@`<INSTANCE>` -verbose**
