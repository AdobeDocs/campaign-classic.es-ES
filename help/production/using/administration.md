---
product: campaign
title: Administración
description: Administración
audience: production
content-type: reference
topic-tags: production-procedures
exl-id: 12a255fe-66f9-40ce-b19e-c24322c2e009
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '411'
ht-degree: 1%

---

# Administración{#administration}

![](../../assets/v7-only.svg)

Inicio automático de los módulos Adobe Campaign (**web**, **mta**, **wfserver**, etc.) la proporciona el **nlserver** servidor.

La instalación de Adobe Campaign configura automáticamente el equipo para que **nlserver** se inicia durante la secuencia de arranque.

Los siguientes comandos se utilizan para iniciar y apagar el servicio Adobe Campaign manualmente:

* En Windows:

   * **net start nlserver6**
   * **net stop nlserver6**

* En Linux (como raíz):

   * **/etc/init.d/nlserver6 start**
   * **/etc/init.d/nlserver6 stop**

>[!NOTE]
>
>A partir de 20.1, se recomienda utilizar el siguiente comando en su lugar (para Linux): **systemctl start nlserver** / **systemctl stop nlserver**

A continuación se muestra una lista de los comandos de administración habituales accesibles en Linux (como **Adobe Campaign**):

* Mostrar todos los módulos de Adobe Campaign iniciados: **/etc/init.d/nlserver6 pdump** o **/etc/init.d/nlserver6 status**

   >[!NOTE]
   >
   >Adición de la variable **-who** para **pdump** permite recopilar información sobre las conexiones actuales (usuarios y procesos).\
   >La variable **/etc/init.d/nlserver6 status** (sin el parámetro &quot;-who&quot;) devolverá:
   >
   >    * 0 si se están ejecutando todos los procesos.
   >    * 1 si falta un proceso.
   >    * 2 si no se está ejecutando ningún proceso.
   >    * otro valor si hay un error.


* Iniciar/detener un módulo de varias instancias o de una instancia única (**web**, **trackinglogd**, **syslogd**, **mta**, **wfserver**, **inmail**):

   **inicio de nlserver`<module>[@<instance>]`**

   **nlserver stop`<module>[@<instance>][-immediate][-noconsole]`**

   También puede usar la variable **nlserver restart`<module>[@<instance>]`** para reiniciar un módulo.

   Ejemplo:

   **nlserver start web**

   **inicio de nlserver mta@my_instance**

   **nlserver stop syslogd**

   **nlserver stop wfserver@my_instance**

   **nlserver stop web -inmediate**

   **nlserver restart web**

   >[!NOTE]
   >
   >* Si no se especifica la instancia, se utilizará la instancia &quot;predeterminada&quot;.
   >* En caso de emergencia, utilice el **-inmediato** para forzar una parada inmediata del proceso (equivalente al comando Unix) **kill -9**).
   >* Utilice la variable **-noconsole** para asegurarse de que el módulo iniciado no mostrará nada en la consola. Sus registros se escribirán en el disco a través del **syslogd** módulo.
   >* Utilice la variable **-verbose** para mostrar información adicional sobre las acciones de proceso.
   >
   >   Ejemplo:
   >
   >   **nlserver restart web-verbose**
   >
   >   **nlserver start mta@myinstance -verbose**
   >
   >   Esta opción agrega registros adicionales. Se recomienda volver a iniciar los procesos sin el **-verbose** una vez que haya encontrado la información deseada, para evitar sobrecargar los registros.


* Inicie todos los procesos de Adobe Campaign (equivalente a iniciar la variable **nlserver6** servicio):

   **nlserver watchdog -noconsole**

* Cierre todos los procesos de Adobe Campaign (equivalente a cerrar el **nlserver6** servicio):

   **nlserver shutdown**

* Vuelva a cargar el **nlserver web** configuración del módulo (y el módulo de extensión del servidor web, si corresponde) cuando se usa la variable **serverConf.xml** y **config-`<instance>  .xml </instance>`** se han editado.

   **nlserver config -reload**

   >[!NOTE]
   >
   >Algunos cambios de configuración no se tienen en cuenta de forma dinámica; Adobe Campaign debe cerrarse y luego reiniciarse.
