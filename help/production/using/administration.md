---
product: campaign
title: Administración
description: Administración
feature: Monitoring
badge-v7-prem: label="Solo local/híbrido" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=es" tooltip="Se aplica solo a implementaciones On-premise e híbridas"
audience: production
content-type: reference
topic-tags: production-procedures
exl-id: 12a255fe-66f9-40ce-b19e-c24322c2e009
source-git-commit: 14ba450ebff9bba6a36c0df07d715b7279604222
workflow-type: tm+mt
source-wordcount: '425'
ht-degree: 3%

---

# Administración{#administration}



Inicio automático de los módulos de Adobe Campaign (**web**, **mta**, **wfserver**, etc.) es proporcionada por el **nlserver** servidor.

La instalación de Adobe Campaign configura automáticamente el equipo para que la **nlserver** el servicio se inicia durante la secuencia de arranque.

Los siguientes comandos se utilizan para iniciar y cerrar el servicio de Adobe Campaign manualmente:

* En Windows:

   * **net start nlserver6**
   * **net stop nlserver6**

* En Linux (como raíz):

   * **Inicio de /etc/init.d/nlserver6**
   * **/etc/init.d/nlserver6 stop**

>[!NOTE]
>
>A partir de la versión 20.1, se recomienda utilizar el siguiente comando (para Linux): **systemctl start nlserver** / **systemctl stop nlserver**

Esta es una lista de los comandos de administración habituales accesibles en Linux (como **Adobe Campaign**):

* Mostrar todos los módulos de Adobe Campaign iniciados: **/etc/init.d/nlserver6 pdump** o **Estado de /etc/init.d/nlserver6**

  >[!NOTE]
  >
  >Añadir el **-who** al parámetro **volcado** El comando permite recopilar información sobre las conexiones actuales (usuarios y procesos).\
  >El **Estado de /etc/init.d/nlserver6** (sin el parámetro &quot;-who&quot;) devolverá:
  >
  >    * 0 si se están ejecutando todos los procesos.
  >    * 1 si falta un proceso.
  >    * 2 si no se está ejecutando ningún proceso.
  >    * otro valor si hay un error.
  >

* Iniciar/detener un módulo de instancia múltiple o mono (**web**, **trackinglogd**, **syslogd**, **mta**, **wfserver**, **en el correo**):

  **nlserver start`<module>[@<instance>]`**

  **nlserver stop`<module>[@<instance>][-immediate][-noconsole]`**

  También puede utilizar la variable **nlserver restart`<module>[@<instance>]`** para reiniciar un módulo.

  Ejemplo:

  **nlserver start web**

  **nlserver start mta@my_instance**

  **nlserver stop syslogd**

  **nlserver stop wfserver@my_instance**

  **nlserver stop web -interim**

  **nlserver restart web**

  >[!NOTE]
  >
  >* Si no se especifica la instancia, se utilizará la instancia &quot;predeterminada&quot;.
  >* En caso de emergencia, utilice el **-inmediato** para forzar una parada inmediata del proceso (equivalente al comando Unix) **kill -9**).
  >* Utilice el **-noconsole** para garantizar que el módulo iniciado no muestre nada en la consola. Sus registros se escribirán en el disco a través del **syslogd** módulo.
  >* Utilice el **-verboso** para mostrar información adicional sobre las acciones de proceso.
  >
  >   Ejemplo:
  >
  >   **nlserver restart web: detallado**
  >
  >   **nlserver start mta@myinstance -verbose**
  >
  >   Esta opción agrega registros adicionales. Se recomienda volver a iniciar los procesos sin la variable **-verboso** una vez que haya encontrado la información deseada, para evitar la sobrecarga de registros.

* Iniciar todos los procesos de Adobe Campaign (equivalente a iniciar el **nlserver6** servicio):

  **nlserver watchdog -noconsole**

* Apagar todos los procesos de Adobe Campaign (lo que equivale a cerrar el **nlserver6** servicio):

  **apagado de nlserver**

* Vuelva a cargar **nlserver web** configuración del módulo (y el módulo de extensión del servidor web, cuando corresponda) cuando **serverConf.xml** y **config-`<instance>  .xml </instance>`** se han editado los archivos.

  **nlserver config -reload**

  >[!NOTE]
  >
  >Algunos cambios de configuración no se tienen en cuenta de forma dinámica; Adobe Campaign debe cerrarse y reiniciarse.
