---
product: campaign
title: Principio de funcionamiento
description: Principio de funcionamiento
audience: production
content-type: reference
topic-tags: production-procedures
exl-id: 1c032ef9-af11-4947-90c6-76cb9434ae85
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: tm+mt
source-wordcount: '500'
ht-degree: 1%

---

# Principio de funcionamiento{#operating-principle}

Técnicamente, la plataforma Adobe Campaign se basa en varios módulos.

Hay muchos módulos de Adobe Campaign. Algunos funcionan de forma continua, mientras que otros se inician ocasionalmente para realizar tareas administrativas (por ejemplo, configurar la conexión de base de datos) o para ejecutar una tarea recurrente (por ejemplo, consolidar la información de seguimiento).

Existen tres tipos de módulos de Adobe Campaign:

* Módulos de varias instancias: se ejecuta un solo proceso para todas las instancias. Esto se aplica a los siguientes módulos: **web**, **syslogd**, **trackinglogd** y **watchdog** (actividades del archivo **config-default.xml**).
* Módulos de instancia única: se ejecuta un proceso por instancia. Esto se aplica a los siguientes módulos: **mta**, **wfserver**, **inMail**, **sms** y **stat** (actividades del archivo **config-`<instance>`.xml**).
* Módulos de utilidad: son módulos que se ejecutan ocasionalmente para realizar operaciones ocasionales o recurrentes (**cleanup**, **config**, descargar registros de seguimiento, etc.).

La administración del módulo se realiza utilizando la herramienta de línea de comandos **nlserver** instalada en el directorio **bin** de la carpeta de instalación.

La sintaxis general de la herramienta **nlserver** es la siguiente:

**nlserver  `<command>``<command arguments>`**

Para la lista de módulos disponibles, utilice el comando **nlserver**.

Los módulos disponibles se detallan en la siguiente tabla:

| Comando | Descripción |
|---|---|
| aliasCleansing | Estandarización de los valores de enumeración |
| facturación | Envío del informe de actividad del sistema a billing@neolane.net |
| cleanup | Limpieza de la base de datos: elimina los datos obsoletos de la base de datos y ejecuta una actualización de las estadísticas utilizadas por el optimizador del motor de base de datos. |
| config | Modificación de la configuración del servidor |
| copybase | Copia de una base de datos |
| exportar | Exportación a la línea de comandos: permite enviar a la línea de comandos un modelo de exportación creado en la consola del cliente de Adobe Campaign |
| fileconvert | Conversión de un archivo de tamaño definido |
| importar | Importación a la línea de comandos: permite enviar a la línea de comandos un modelo de importación creado en la consola del cliente de Adobe Campaign. |
| inMail | Analizador de correo entrante |
| installsetup | Disponibilidad del archivo de instalación del cliente |
| javascript | Ejecución de secuencias de comandos de JavaScript con acceso a las API de SOAP. |
| trabajo | Procesamiento de la línea de comandos |
| combinar | Combinación de formularios |
| midSourcing | Recuperación de la información de entrega en modo intermediario |
| monitor | XML Visualización del estado de los procesos del servidor y las tareas programadas, por ejemplo. |
| mta | Mensaje de transferencia del agente principal |
| paquete | Importación o exportación de archivos de paquetes de entidades |
| pdump | Visualización de los estados de proceso del servidor |
| prepareda | Preparación de una acción de entrega |
| restart | Reinicio parcial del servidor |
| runwf | Ejecución de una instancia de flujo de trabajo |
| shutdown | Cierre completo del sistema |
| sms | Procesamiento de notificaciones SMS |
| sql | Ejecución de secuencia de comandos SQL |
| start | Comienzos adicionales |
| stat | Mantiene las estadísticas de conexión de MTA |
| stop | Apagado parcial del sistema |
| submitda | Envío de una acción de entrega |
| syslogd | Servidor de escritura de registro y seguimiento |
| seguimiento | Consolidación y recuperación de registros de seguimiento |
| trackinglogd | Seguimiento de la escritura y depuración de registros en el servidor |
| watchdog | Instancia de inicio y monitorización |
| web | Servidor de aplicaciones (HTTP y SOAP) |
| wfserver | Servidor de flujo de trabajo |

>[!IMPORTANT]
>
>Hay un último módulo: el módulo de seguimiento y retransmisión vinculado al servidor de aplicaciones que, por motivos de rendimiento, se integra mediante mecanismos nativos en un servidor web Apache o IIS a través de una biblioteca dinámica. No hay ningún comando de Adobe Campaign que le permita iniciar o administrar este módulo. Por lo tanto, debe utilizar los comandos del propio servidor web.

El uso del módulo y la sintaxis de sus parámetros se muestran mediante el siguiente comando: **nlserver `[module]` -?**

Ejemplo:

**nlserver config -?**

```
Usage: nlserver [-verbose:<verbose mode>] [-?|h|H] [-version] [-noconsole]
 [-tracefile:<file>] [-tracefilter:<[type|!type],...>]
 [-instance:<instance>] [-low] [-high] [-queryplans] [-detach]
 [-internalpassword:<[password/newpassword]>] [-postupgrade]
 [-nogenschema] [-force] [-allinstances]
 [-addinstance:<instance/DNS masks[/language]>]
 [-setdblogin:<[dbms:]account[:database][/password]@server>]
 [-monoinstance]
 [-addtrackinginstance:<instance/masks DNS[/databaseId/[/language[/password]]]>]
 [-trackingpassword:<[password][/newpassword]>]
 [-setproxy:<protocol/server:port[/login]>] [-reload]
 [-applyxsl:<schema/file.xsl>] [-filter:<file>]
 [-setactivationkey:<activation key>]
 [-getactivationkey:<client identifier>]
-verbose : verbose mode
-? : display this help message
-version : display version number
-noconsole : no longer display logs and traces on the console
-tracefile : name of trace file to be generated (without extension)
-tracefilter : filter for the traces to be generated e.g.: wdbc,soap,!xtkquery.
-instance : instance to be used (default instance if this option is not present).
-low : start up with low priority
-high : start up with high priority (not recommended)
-queryplans : generate traces with the execution plans of SQL queries.
-detach : detaches the process from its parent (internal option)
-internalpassword : changes the password of the server internal account.
-postupgrade : updates the database following upgrade to a higher version. 
-nogenschema : does not recompute the schemas during database update
-force : updates the database even if this has already been done with the current build 
-allinstances : updates the database over all configured instances
-addinstance : adds a new instance.
-setdblogin : sets the parameters for connection to the database of an instance. The DBMS can be 'oracle', 'postgresql', 'mssql' or 'odbc' (default=postgresql)
-monoinstance : initialises for a single instance ().
-addtrackinginstance : adds a new tracking instance.
-trackingpassword : changes the tracking password of an instance
-setproxy : sets the parameters for connection to a proxy server. The protocol can be 'http', 'https' or 'all'.
-reload : asks the server to reload the configuration of the instances. 
-applyxsl : applies an XSL stylesheet to all entities of a schema. 
-filter : applies the XTK filter contained in the file during loading of the schema entities.
-setactivationkey : sets the activation key
```
