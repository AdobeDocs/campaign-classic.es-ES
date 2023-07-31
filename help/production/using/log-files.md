---
product: campaign
title: Archivos de registro
description: Archivos de registro
feature: Monitoring
badge-v7-only: label="v7" type="Informative" tooltip="Solo se aplica a Campaign Classic v7"
badge-v7-prem: label="on-premise e híbrido" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=es" tooltip="Se aplica solo a implementaciones On-premise e híbridas"
audience: production
content-type: reference
topic-tags: production-procedures
exl-id: c9d427da-6965-4945-90f0-d0770701d55e
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: tm+mt
source-wordcount: '456'
ht-degree: 6%

---

# Archivos de registro{#log-files}



Los archivos de registro se organizan de la siguiente manera:

![](assets/d_ncs_directory.png)

Cada **nlserver** Este módulo genera un archivo de registro guardado en el siguiente directorio: **`<installation directory>`/var/`<instance>`/log/`<module>`.log**.

El **nlserver syslogd** El módulo guarda los registros en el disco. Este módulo es similar al de Unix **daemon syslog**, pero se ha adaptado para la compatibilidad entre Unix y Windows. Los demás módulos de Adobe Campaign no guardan sus registros en el disco; delegan esta tarea al **syslogd** mediante el envío de paquetes UDP.

De forma predeterminada, la plataforma de Adobe Campaign tiene el **syslogd** módulo instalado en él, pero es posible utilizar otro **daemon syslog**. Este módulo crea los archivos de registro en **registro** directorio.

Los registros de los módulos de varias instancias se almacenan en el siguiente directorio: **`<installation directory>`/var/default/log/**. El mismo archivo de registro se comparte en todas las instancias (por ejemplo, **web.log**).

Los registros de los demás módulos se almacenan en una subcarpeta denominada como consecuencia de la instancia. Cada instancia tiene sus propios archivos de registro.

Los archivos de registro de varias instancias se enumeran en la siguiente tabla:

| Archivo | Descripción |
|---|---|
| web.log | Registros del módulo web (consola de cliente, informes, API de SOAP, etc.) |
| webmdl.log | Registros del módulo de redirección |
| watchdog.log | Registros del módulo de monitorización de procesos de Adobe Campaign |
| trackinglogd.log | Registros de seguimiento |

Los archivos de registro de instancia mono se enumeran en la siguiente tabla:

| Archivo | Descripción |
|---|---|
| mta.log | registros del módulo mta |
| mtachild.log | Registros de procesamiento de entrega de mensajes |
| wfserver.log | Registros del módulo del servidor de flujo de trabajo |
| runwf.log | Registros de ejecución de flujo de trabajo |
| inMail.log | Registro del módulo de correo rechazado |
| logins.log | Registra todos los intentos de inicio de sesión en Adobe Campaign (tenga éxito o no) |

>[!IMPORTANT]
>
>El **redir** solo existe en servidores de redirección. El **url** subdirectorio contiene las coincidencias de las direcciones URL que se van a redirigir y el subdirectorio **registro** contiene los registros de seguimiento. Para generar registros de seguimiento, la variable **trackinglogd** El módulo debe estar en ejecución.

Para optimizar el rendimiento y el almacenamiento, el archivo logins.log se divide en varios archivos, uno cada día (logins.aa-mm-dd.log) con un máximo de 365 archivos retenidos. El número de días se puede cambiar en serverConf.xml, en syslogd (**maxNumberOfLoginsFiles** opción). Consulte la documentación de la [archivo de configuración del servidor](../../installation/using/the-server-configuration-file.md#syslogd).

De forma predeterminada, los registros están limitados a dos archivos de 10 MB por módulo y por instancia. El segundo archivo se llama: **`<modulename>`_2.log**. Por lo tanto, el tamaño de los registros está limitado a 2&#42;10 MB por módulo y por instancia.

Sin embargo, puede conservar archivos de mayor tamaño. Para habilitar esto, cambie el valor del **maxFileSizeMb=10** configuración en la **syslogd** nodo del **conf/serverConf.xml** archivo. Este valor representa el tamaño máximo en MB de un archivo de registro.

Si desea mantener niveles de detalle adicionales en los registros, puede iniciar los módulos de Adobe Campaign con la variable **-verboso** parámetro:

**nlserver start `<MODULE>`@`<INSTANCE>` -verboso**
