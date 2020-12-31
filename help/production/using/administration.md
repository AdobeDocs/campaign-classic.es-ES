---
solution: Campaign Classic
product: campaign
title: Administración
description: Administración
audience: production
content-type: reference
topic-tags: production-procedures
translation-type: tm+mt
source-git-commit: 9c78d8f469bade41717eb854e8cec00859c1d4e3
workflow-type: tm+mt
source-wordcount: '411'
ht-degree: 1%

---


# Administración{#administration}

Inicio automático de los módulos de Adobe Campaign (**web**, **mta**, **wfserver**, etc.) es proporcionado por el servidor **nlserver**.

La instalación de Adobe Campaign configura automáticamente el equipo para que el servicio **nlserver** se inicio durante la secuencia de inicio.

Los siguientes comandos se utilizan para realizar inicios y apagar el servicio Adobe Campaign manualmente:

* En Windows:

   * **net inicio nlserver6**
   * **net stop nlserver6**

* En Linux (como raíz):

   * **/etc/init.d/nlserver6 inicio**
   * **/etc/init.d/nlserver6 stop**

>[!NOTE]
>
>A partir de 20.1, se recomienda utilizar el siguiente comando en su lugar (para Linux): **inicio de sistema nlserver** / **systemctl stop nlserver**

Esta es una lista de los comandos de administración habituales accesibles en Linux (como **Adobe Campaign**):

* Mostrar todos los módulos de Adobe Campaign iniciados: **/etc/init.d/nlserver6 pdump** o **/etc/init.d/nlserver6 status**

   >[!NOTE]
   >
   >Añadir el parámetro **-who** en el comando **pdump** permite recopilar información sobre las conexiones actuales (usuarios y procesos).\
   >El comando **/etc/init.d/nlserver6 status** (sin el parámetro &quot;-who&quot;) devolverá:
   >
   >    * 0 si se están ejecutando todos los procesos.
   >    * 1 si falta un proceso.
   >    * 2 si no se está ejecutando ningún proceso.
   >    * otro valor si hay un error.


* Inicio/parada de un módulo de varias instancias o de una instancia (**web**, **trackinglogd**, **syslogd**, **mta**, **wfserver**, &lt;a 10/>inmail **):**

   **inicio nlserver`<module>[@<instance>]`**

   **nlserver stop`<module>[@<instance>][-immediate][-noconsole]`**

   También puede utilizar el comando **nlserver Restart`<module>[@<instance>]`** para reiniciar un módulo.

   Ejemplo:

   **nlserver inicio web**

   **nlserver inicio mta@my_instance**

   **nlserver stop syslogd**

   **nlserver stop wfserver@my_instance**

   **nlserver stop web -inmediatamente**

   **nlserver reinicie web**

   >[!NOTE]
   >
   >* Si no se especifica la instancia, se utilizará la instancia &quot;predeterminada&quot;.
   >* En el evento de una emergencia, utilice la opción **-inmediata** para forzar una parada inmediata del proceso (equivalente al comando Unix **kill -9**).
   >* Utilice la opción **-noconsole** para asegurarse de que el módulo iniciado no muestre nada en la consola. Sus registros se escribirán en el disco mediante el módulo **syslogd**.
   >* Utilice la opción **-verbose** para mostrar información adicional sobre las acciones del proceso.

      >
      >   
      Ejemplo:
      >
      >   
      **nlserver Restart web -verbose**
      >
      >   
      **nlserver inicio mta@myinstance -verbose**
      >
      >   
      Esta opción agrega registros adicionales. Recomendamos volver a iniciar los procesos sin la opción **-verbose** una vez que haya encontrado la información deseada, para evitar la sobrecarga de registros.


* Inicio de todos los procesos de Adobe Campaign (equivalente a iniciar el servicio **nlserver6**):

   **nlserver watchdog -noconsole**

* Cierre todos los procesos de Adobe Campaign (equivalente a cerrar el servicio **nlserver6**):

   **apagado de nlserver**

* Vuelva a cargar la configuración del módulo **nlserver web** (y el módulo de extensión del servidor web, cuando proceda) cuando se hayan editado los archivos **serverConf.xml** y **config-`<instance>  .xml </instance>`**.

   **nlserver config -reload**

   >[!NOTE]
   >
   >Algunos cambios de configuración no se tienen en cuenta de forma dinámica; Adobe Campaign debe cerrarse y reiniciarse.

