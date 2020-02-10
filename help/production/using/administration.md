---
title: Administración
seo-title: Administración
description: Administración
seo-description: null
page-status-flag: never-activated
uuid: 376efec1-1647-43b4-b72f-2603214c7cc6
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: production
content-type: reference
topic-tags: production-procedures
discoiquuid: 860be8be-f28c-4836-b4fb-e91c6a4616c6
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 779d9162b7296339a796512838612ede1186ddcc

---


# Administración{#administration}

Inicio automático de los módulos de Adobe Campaign (**web**, **mta**, **wfserver**, etc.) es proporcionado por el **servidor** nlserver.

La instalación de Adobe Campaign configura automáticamente el equipo para que el servicio **nlserver** se inicie durante la secuencia de inicio.

Los siguientes comandos se utilizan para iniciar y cerrar el servicio Adobe Campaign manualmente:

* En Windows:

   * **net start nlserver6**
   * **net stop nlserver6**

* En Linux (como raíz):

   * **/etc/init.d/nlserver6 start**
   * **/etc/init.d/nlserver6 stop**

Esta es una lista de los comandos de administración habituales a los que se puede acceder en Linux (como **Adobe Campaign**):

* Mostrar todos los módulos de Adobe Campaign iniciados: **/etc/init.d de** InServer6 pdump **o/etc/init.d/nlserver6**

   >[!NOTE]
   >
   >La adición del parámetro **-who** al comando **pdump** permite recopilar información sobre las conexiones actuales (usuarios y procesos).\
   >El **comando de estado** /etc/init.d/nlserver6 (sin el parámetro &quot;-who&quot;) devolverá:
   >
   >    * 0 si se están ejecutando todos los procesos.
   >    * 1 si falta un proceso.
   >    * 2 si no se está ejecutando ningún proceso.
   >    * otro valor si hay un error.


* Inicie/detenga un módulo de instancia múltiple o mono (**web**, **trackinglogd**, **syslogd**, **mta**, **wfserver******, inmail):

   **inicio de nlserver`<module>[@<instance>]`**

   **nlserver stop`<module>[@<instance>][-immediate][-noconsole]`**

   También puede utilizar el comando **nlserver Restart`<module>[@<instance>]`**para reiniciar un módulo.

   Ejemplo:

   **nlserver start web**

   **nlserver start mta@my_instance**

   **nlserver stop syslogd**

   **nlserver stop wfserver@my_instance**

   **nlserver stop web -inmediatamente**

   **nlserver reinicie web**

   >[!NOTE]

   >* Si no se especifica la instancia, se utilizará la instancia &quot;predeterminada&quot;.
   >    
   >    
   >    * En caso de emergencia, utilice la opción **-inmediata** para forzar una parada inmediata del proceso (equivalente al comando Unix **kill -9**).
   * Utilice la opción **-noconsole** para asegurarse de que el módulo iniciado no se mostrará en la consola. Sus registros se escribirán en el disco a través del **módulo syslogd** .
   * Utilice la opción **-verbose** para mostrar información adicional sobre las acciones de proceso.


      Ejemplo:


      **nlserver Restart web -verbose**


      **nlserver start mta@myinstance -verbose**


      Esta opción agrega registros adicionales. Recomendamos volver a iniciar los procesos sin la opción **-verbose** una vez que haya encontrado la información deseada, para evitar la sobrecarga de registros.


* Inicie todos los procesos de Adobe Campaign (equivalente a iniciar el servicio **nlserver6** ):

   **nlserver watchdog -noconsole**

* Cierre todos los procesos de Adobe Campaign (equivalente a cerrar el servicio **nlserver6** ):

   **apagado de nlserver**

* Vuelva a cargar la configuración del módulo web **** nlserver (y el módulo de extensión del servidor web, cuando proceda) cuando se hayan editado los **archivos serverConf.xml** y **config-`<instance>  .xml </instance>`**.

   **nlserver config -reload**

   >[!NOTE]
   Algunos cambios de configuración no se tienen en cuenta de forma dinámica; Adobe Campaign debe cerrarse y reiniciarse.

