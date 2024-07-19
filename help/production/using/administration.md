---
product: campaign
title: Administración
description: Administración
feature: Monitoring
badge-v7-prem: label="On-premise/híbrido solo" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=es" tooltip="Se aplica solo a implementaciones On-premise e híbridas"
audience: production
content-type: reference
topic-tags: production-procedures
exl-id: 12a255fe-66f9-40ce-b19e-c24322c2e009
source-git-commit: b7dedddc080d1ea8db700fabc9ee03238b3706cc
workflow-type: tm+mt
source-wordcount: '425'
ht-degree: 3%

---

# Administración{#administration}

Inicio automático de los módulos Adobe Campaign (**web**, **mta**, **wfserver**, etc.) lo proporciona el servidor **nlserver**.

La instalación de Adobe Campaign configura automáticamente el equipo para que el servicio **nlserver** se inicie durante la secuencia de arranque.

Los siguientes comandos se utilizan para iniciar y cerrar el servicio de Adobe Campaign manualmente:

* En Windows:

   * **net start nlserver6**
   * **net stop nlserver6**

* En Linux (como raíz):

   * **/etc/init.d/nlserver6 start**
   * **/etc/init.d/nlserver6 stop**

>[!NOTE]
>
>A partir de la versión 20.1, se recomienda utilizar el siguiente comando en su lugar (para Linux): **systemctl start nlserver** / **systemctl stop nlserver**

Esta es una lista de los comandos de administración habituales accesibles en Linux (como **Adobe Campaign**):

* Mostrar todos los módulos de Adobe Campaign iniciados: **/etc/init.d/nlserver6 pdump** o **/etc/init.d/nlserver6 status**

  >[!NOTE]
  >
  >Si agrega el parámetro **-who** al comando **pdump**, podrá recopilar información sobre las conexiones actuales (usuarios y procesos).\
  >El comando **/etc/init.d/nlserver6 status** (sin el parámetro &quot;-who&quot;) devolverá:
  >
  >    * 0 si se están ejecutando todos los procesos.
  >    * 1 si falta un proceso.
  >    * 2 si no se está ejecutando ningún proceso.
  >    * otro valor si hay un error.
  >

* Iniciar o detener un módulo de instancia múltiple o mono (**web**, **trackinglogd**, **syslogd**, **mta**, **wfserver**, **inmail**):

  **nlserver start`<module>[@<instance>]`**

  **nlserver stop`<module>[@<instance>][-immediate][-noconsole]`**

  También puede usar el comando **nlserver restart`<module>[@<instance>]`** para reiniciar un módulo.

  Ejemplo:

  **nlserver start web**

  **nlserver start mta@my_instance**

  **nlserver stop syslogd**

  **nlserver stop wfserver@my_instance**

  **nlserver stop web -middle**

  **nlserver reinicie la web**

  >[!NOTE]
  >
  >* Si no se especifica la instancia, se utilizará la instancia &quot;predeterminada&quot;.
  >* En caso de emergencia, use la opción **-interim** para forzar una detención inmediata del proceso (equivalente al comando Unix **kill -9**).
  >* Utilice la opción **-noconsole** para asegurarse de que el módulo iniciado no mostrará nada en la consola. Sus registros se escribirán en el disco a través del módulo **syslogd**.
  >* Utilice la opción **-verbose** para mostrar información adicional sobre las acciones de proceso.
  >
  >   Ejemplo:
  >
  >   **nlserver reinicie la web -verbose**
  >
  >   **nlserver start mta@myinstance -verbose**
  >
  >   Esta opción agrega registros adicionales. Se recomienda volver a iniciar los procesos sin la opción **-verbose** una vez que haya encontrado la información deseada, para evitar la sobrecarga de registros.

* Iniciar todos los procesos de Adobe Campaign (equivalente a iniciar el servicio **nlserver6**):

  **nlserver watchdog -noconsole**

* Apagar todos los procesos de Adobe Campaign (equivalente a apagar el servicio **nlserver6**):

  **apagado de nlserver**

* Vuelva a cargar la configuración del módulo **nlserver web** (y el módulo de extensión del servidor web, donde corresponda) cuando se hayan editado los archivos **serverConf.xml** y **config-`<instance>  .xml </instance>`**.

  **nlserver config -reload**

  >[!NOTE]
  >
  >Algunos cambios de configuración no se tienen en cuenta de forma dinámica; Adobe Campaign debe cerrarse y reiniciarse.
