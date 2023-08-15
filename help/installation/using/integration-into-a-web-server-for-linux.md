---
product: campaign
title: Integración en un servidor web para Linux
description: Aprenda a integrar Campaign en un servidor web (Linux)
feature: Installation, Instance Settings
badge-v7-only: label="v7" type="Informative" tooltip="Se aplica solo a Campaign Classic v7"
badge-v7-prem: label="on-premise e híbrido" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=es" tooltip="Se aplica solo a implementaciones On-premise e híbridas"
audience: installation
content-type: reference
topic-tags: installing-campaign-in-linux-
exl-id: 4f8ea358-a38d-4137-9dea-f398e60c5f5d
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: tm+mt
source-wordcount: '579'
ht-degree: 9%

---

# Integración en un servidor web para Linux{#integration-into-a-web-server-for-linux}



Adobe Campaign incluye Apache Tomcat, que actúa como punto de entrada en el servidor de aplicaciones a través de HTTP (y SOAP).

Puede utilizar este servidor Tomcat integrado para servir solicitudes HTTP.

En este caso:

* el puerto de escucha predeterminado es 8080. Para cambiarlo, consulte [esta sección](configure-tomcat.md).
* A continuación, las consolas de cliente se conectan mediante una dirección URL como:

  ```
  http://<computer>:8080
  ```

Sin embargo, por motivos de seguridad y administración, se recomienda utilizar un servidor Web específico como punto de entrada principal para el tráfico HTTP cuando el equipo que ejecuta Adobe Campaign está expuesto en Internet y desea abrir el acceso a la consola fuera de la red.

Un servidor web también permite garantizar la confidencialidad de los datos con el protocolo HTTP.

Del mismo modo, debe utilizar un servidor web cuando desee utilizar la funcionalidad de seguimiento, que solo está disponible como módulo de extensión para un servidor web.

>[!NOTE]
>
>Si no utiliza la funcionalidad de seguimiento, puede realizar una instalación estándar de Apache o IIS con una redirección a Campaign. El módulo de extensión del servidor web de seguimiento no es obligatorio.

## Configuración del servidor web Apache con Debian {#configuring-the-apache-web-server-with-debian}

Este proceso se aplica si ha instalado Apache en una distribución basada en APT.

Siga estos pasos:

1. Deshabilite los módulos cargados de forma predeterminada mediante el siguiente comando:

   ```
   a2dismod auth_basic authn_file authz_default authz_user autoindex cgi dir env negotiation userdir
   ```

   Asegúrese de que la variable **alias**, **authz_host** y **mimo** Los módulos de aún están activados. Para ello, utilice el siguiente comando:

   ```
   a2enmod  alias authz_host mime
   ```

1. Cree el archivo **nlsrv.load** in **/etc/apache2/mods-available** e inserte el siguiente contenido:

   En Debian 8:

   ```
   LoadModule requesthandler24_module /usr/local/[INSTALL]/nl6/lib/libnlsrvmod.so
   ```

1. Cree el archivo **nlsrv.conf** in **/etc/apache2/mods-available** mediante el siguiente comando:

   ```
   ln -s /usr/local/[INSTALL]/nl6/conf/apache_neolane.conf /etc/apache2/mods-available/nlsrv.conf
   ```

1. Active este módulo con el siguiente comando:

   ```
    a2enmod nlsrv
   ```

   Si utiliza el complemento **mod_rewrite** para las páginas de Adobe Campaign, debe cambiar el nombre del módulo **nlsrv.load** y **nlsrv.conf** archivos a **zz-nlsrv.load** y **zz-nlsrv.conf**. Para activar el módulo, ejecute el siguiente comando:

   ```
   a2enmod zz-nlsrv
   ```

1. Edite el **/etc/apache2/envvars** , añada las líneas siguientes:

   ```
   # Added Neolane
   if [ "$LD_LIBRARY_PATH" != "" ]; then export LD_LIBRARY_PATH="/usr/local/neolane/nl6/lib:$LD_LIBRARY_PATH"; else export LD_LIBRARY_PATH=/usr/local/neolane/nl6/lib; fi
   export USERPATH=/usr/local/neolane
   ```

   Guarde los cambios.

1. A continuación, añada usuarios de Adobe Campaign al grupo de usuarios de Apache y viceversa mediante el siguiente tipo de comando:

   ```
   usermod neolane -G www-data
   usermod www-data -G neolane
   ```

1. Reinicie Apache:

   ```
   invoke-rc.d apache2 restart
   ```

## Configuración del servidor web Apache en RHEL {#configuring-apache-web-server-in-rhel}

Este procedimiento se aplica si ha instalado y protegido Apache con un paquete basado en RPM (RHEL, CentOS y Suse).

Siga estos pasos:

1. En el `httpd.conf` , active los siguientes módulos Apache:

   ```
   alias
   authz_host
   mime
   ```

1. Desactive los siguientes módulos:

   ```
   auth_basic
   authn_file
   authz_default
   authz_user
   autoindex
   cgi
   dir
   env
   negotiation
   userdir
   ```

   Comente las funciones vinculadas a los módulos desactivados:

   ```
   DirectoryIndex
   IndexOptions    
   AddIconByEncoding    
   AddIconByType    
   AddIcon    
   DefaultIcon    
   ReadmeName    
   HeaderName    
   IndexIgnore    
   LanguagePriority    
   ForceLanguagePriority
   ```

1. Cree un archivo de configuración específico de Adobe Campaign en la `/etc/httpd/conf.d/` carpeta. Por ejemplo `CampaignApache.conf`

1. Para **RHEL7**, agregue las siguientes instrucciones al archivo:

   ```
   LoadModule requesthandler24_module /usr/local/neolane/nl6/lib/libnlsrvmod.so
   Include /usr/local/neolane/nl6/conf/apache_neolane.conf
   ```

1. Para **RHEL7**:

   Añada el `/etc/systemd/system/httpd.service` archivo con el siguiente contenido:

   ```
   .include /usr/lib/systemd/system/httpd.service
   
   [Service]
   Environment=USERPATH=/usr/local/neolane LD_LIBRARY_PATH=/usr/local/neolane/nl6/lib
   ```

   Actualice el módulo utilizado por systemd:

   ```
   systemctl daemon-reload
   ```

1. A continuación, añada los operadores de Adobe Campaign al grupo de operadores de Apache y viceversa, ejecutando el comando:

   ```
   usermod -a -G neolane apache
   usermod -a -G apache neolane
   ```

   Los nombres de grupo que se van a utilizar dependen de la forma en que se configure Apache.

1. Ejecute Apache y el servidor de Adobe Campaign.

   Para RHEL7:

   ```
   systemctl start httpd
   systemctl start nlserver
   ```

## Inicio del servidor web y prueba de la configuración{#launching-the-web-server-and-testing-the-configuration}

Ahora puede probar la configuración iniciando Apache. El módulo Adobe Campaign ahora debe mostrar su banner en la consola (dos banners en determinados sistemas operativos):

```
 /etc/init.d/apache start
```

Se muestra la siguiente información:

```
12:26:28 >   Application server for Adobe Campaign Classic (7.X YY.R build XXX@SHA1) of DD/MM/YYYY
12:26:28 >   Web server start (pid=29698, tid=-1212463424)...
12:26:28 >   Server started
12:26:28 >   Application server for Adobe Campaign Classic (7.X YY.R build XXX@SHA1) of DD/MM/YYYY
12:26:28 >   Web server start (pid=29698, tid=-1212463424)...
12:26:28 >   Server started
```

A continuación, compruebe que responde enviando una URL de prueba.

Puede probar esto desde la línea de comandos ejecutando:

```
 telnet localhost 80  
```

Debe obtener lo siguiente:

```
Trying 127.0.0.1...
Connected to localhost.localdomain.
Escape character is '^]'.
```

A continuación, introduzca:

```
GET /r/test
```

Se muestra la siguiente información:

```
<redir status='OK' date='YYYY/MM/DD HH:MM:SS' build='XXXX' host='' localHost='XXXX'/>
Connection closed by foreign host.
```

También puede solicitar la dirección URL `https://myserver.adobe.com/r/test` desde un explorador web.
