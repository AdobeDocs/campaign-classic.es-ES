---
product: campaign
title: Principio de funcionamiento
description: Principio de funcionamiento
feature: Monitoring
badge-v7-only: label="v7" type="Informative" tooltip="Se aplica solo a Campaign Classic v7"
badge-v7-prem: label="On-Premise e híbrido" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=es" tooltip="Se aplica solo a implementaciones On-premise e híbridas"
audience: production
content-type: reference
topic-tags: production-procedures
exl-id: 1c032ef9-af11-4947-90c6-76cb9434ae85
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: tm+mt
source-wordcount: '512'
ht-degree: 5%

---

# Principio de funcionamiento{#operating-principle}



Técnicamente, la plataforma Adobe Campaign se basa en varios módulos.

Hay muchos módulos de Adobe Campaign. Algunos funcionan de forma continua, mientras que otros se inician ocasionalmente para realizar tareas administrativas (por ejemplo, configurar la conexión a la base de datos) o para ejecutar una tarea recurrente (por ejemplo, consolidar la información de seguimiento).

Existen tres tipos de módulos de Adobe Campaign:

* Módulos de varias instancias: se ejecuta un solo proceso para todas las instancias. Esto se aplica a los siguientes módulos: **web**, **syslogd**, **trackinglogd** y **perro guardián** (actividades de la **config-default.xml** file).
* Módulos de instancia mono: se ejecuta un proceso por instancia. Esto se aplica a los siguientes módulos: **mta**, **wfserver**, **inMail**, **sms** y **estadísticas** (actividades de la **config-`<instance>`.xml** file).
* Módulos de utilidad: son módulos que se ejecutan ocasionalmente para realizar operaciones ocasionales o recurrentes (**cleanup**, **config**, descargar registros de seguimiento, etc.).

La administración de módulos se realiza mediante la herramienta de línea de comandos **nlserver** instalado en el **cubo** de la carpeta de instalación.

La sintaxis general del **nlserver** La herramienta es la siguiente:

**nlserver `<command>``<command arguments>`**

Para ver la lista de módulos disponibles, utilice el **nlserver** comando.

Los módulos disponibles se detallan en la tabla siguiente:

| Comando | Descripción |
|---|---|
| aliasCleansing | Estandarización de valores de enumeración |
| facturación | Envío del informe de actividad del sistema a billing@neolane.net |
| cleanup | Limpieza de la base de datos: elimina los datos obsoletos de la base de datos y ejecuta una actualización de las estadísticas utilizadas por el optimizador del motor de base de datos. |
| config | Modificación de la configuración del servidor |
| exportar | Exportar a la línea de comandos: permite enviar a la línea de comandos un modelo de exportación creado en la consola del cliente de Adobe Campaign |
| fileconvert | Conversión de un archivo de tamaño definido |
| importar | Importing to command line: permite enviar a la línea de comandos un modelo de importación creado en la consola del cliente de Adobe Campaign. |
| inMail | Analizador de correo entrante |
| installsetup | Disponibilidad del archivo de instalación del cliente |
| javascript | Ejecución de scripts JavaScript con acceso a las API de SOAP. |
| trabajo | Procesamiento de línea de comandos |
| fusionar | Combinación de formularios |
| midSourcing | Recuperación de información de envío en modo intermediario |
| monitor | XML Visualización del estado de los procesos del servidor y las tareas programadas, por instancia. |
| mta. | Mensaje de transferencia del agente principal |
| paquete | Importación o exportación de archivos del paquete de entidades |
| volcado | Visualización de estados de procesos del servidor |
| preparado | Preparación de una acción de envío |
| reiniciar | Reinicio parcial del servidor |
| runwf | Ejecución de una instancia de flujo de trabajo |
| parada | Apagado completo del sistema |
| sms | Procesamiento de notificaciones SMS |
| sql | Ejecución de script SQL |
| start | Inicios adicionales |
| estadísticas | Mantiene estadísticas de conexión MTA |
| parada | Apagado parcial del sistema |
| submitda | Envío de una acción de envío |
| syslogd | Servidor de escritura de registro y seguimiento |
| seguimiento | Consolidación y recuperación de registros de seguimiento |
| trackinglogd | Seguimiento de la escritura y depuración del registro del servidor |
| perro guardián | Instancia de inicio y monitorización |
| web | Servidor de aplicaciones (HTTP y SOAP) |
| wfserver | Servidor de flujo de trabajo |

>[!IMPORTANT]
>
>Hay un último módulo: el módulo de seguimiento y retransmisión vinculado al servidor de aplicaciones que, en aras del rendimiento, se integra a través de mecanismos nativos en un servidor web Apache o IIS a través de una biblioteca dinámica. No hay ningún comando de Adobe Campaign que le permita iniciar o administrar este módulo. Por lo tanto, debe utilizar los comandos del propio servidor Web.

El uso del módulo y la sintaxis de sus parámetros se muestran mediante el siguiente comando: **nlserver `[module]` -?**

Ejemplo:

**Configuración de nlserver -?**

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
-monoinstance : initializes for a single instance ().
-addtrackinginstance : adds a new tracking instance.
-trackingpassword : changes the tracking password of an instance
-setproxy : sets the parameters for connection to a proxy server. The protocol can be 'http', 'https' or 'all'.
-reload : asks the server to reload the configuration of the instances. 
-applyxsl : applies an XSL stylesheet to all entities of a schema. 
-filter : applies the XTK filter contained in the file during loading of the schema entities.
-setactivationkey : sets the activation key
```
