---
product: campaign
title: Principio de funcionamiento
description: Principio de funcionamiento
feature: Monitoring
badge-v7-prem: label="On-premise/híbrido solo" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=es" tooltip="Se aplica solo a implementaciones On-premise e híbridas"
audience: production
content-type: reference
topic-tags: production-procedures
exl-id: 1c032ef9-af11-4947-90c6-76cb9434ae85
TQID: https://experienceleague.adobe.com/HCoIXlpEtxAHVh-rj51UD1GTNRnXh8Ir8x4t3QZT9YU
product_v2: id: dfc56824-e8b9-499e-85d4-21aedb507314
feature_v2: id: b12f6872-9271-4369-85e5-86969a0b99a2id: b82389f8-9b5e-4083-8e3b-3cef299fb8b9id: c5474392-5419-4296-9e41-f6f4ce4f6e9b
subfeature_v2: id: c03a11ff-bdf9-4e5b-b279-f468b4293464id: e519a22f-a06a-42fc-9d09-d78a3ab2c434
topic_v2: id: eddd9b14-83bd-4ff4-9072-54a4a484abb7
source-git-commit: 38eab6b8da73163e4476e91c0ef73f25c3f57546
workflow-type: tm+mt
source-wordcount: 530
ht-degree: 9%

---

# Principio de funcionamiento{#operating-principle}



Técnicamente, la plataforma Adobe Campaign se basa en varios módulos.

Hay muchos módulos de Adobe Campaign. Algunos funcionan de forma continua, mientras que otros se inician ocasionalmente para realizar tareas administrativas (por ejemplo, configurar la conexión a la base de datos) o para ejecutar una tarea recurrente (por ejemplo, consolidar la información de seguimiento).

Existen tres tipos de módulos de Adobe Campaign:

* Módulos de varias instancias: se ejecuta un solo proceso para todas las instancias. Esto se aplica a los siguientes módulos: **web**, **syslogd**, **trackinglogd** y **watchdog** (actividades del archivo **config-default.xml**).
* Módulos de instancia mono: se ejecuta un proceso por instancia. Esto se aplica a los siguientes módulos: **mta**, **wfserver**, **inMail**, **sms** y **stat** (actividades del archivo **config-`<instance>`.xml**).
* Módulos de utilidad: son módulos que se ejecutan ocasionalmente para realizar operaciones ocasionales o recurrentes (**cleanup**, **config**, descargar registros de seguimiento, etc.).

La administración del módulo se realiza mediante la herramienta de línea de comandos **nlserver** instalada en el directorio **bin** de la carpeta de instalación.

La sintaxis general de la herramienta **nlserver** es la siguiente:

**nlserver `<command>``<command arguments>`**

Para obtener la lista de módulos disponibles, use el comando **nlserver**.

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
| javascript | Ejecución de scripts de JavaScript con acceso a las API de SOAP. |
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
| sql | Nombre del script SQL |
| iniciar | Inicios adicionales |
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

**configuración de nlserver -?**

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
