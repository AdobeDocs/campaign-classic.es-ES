---
product: campaign
title: Integración en un servidor web para Linux
description: Aprenda a integrar Campaign en un servidor web (Linux)
audience: installation
content-type: reference
topic-tags: installing-campaign-in-linux-
exl-id: 4f8ea358-a38d-4137-9dea-f398e60c5f5d
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: tm+mt
source-wordcount: '558'
ht-degree: 5%

---

# Integración en un servidor web para Linux{#integration-into-a-web-server-for-linux}

Adobe Campaign incluye Apache Tomcat que actúa como punto de entrada en el servidor de aplicaciones a través de HTTP (y SOAP).

Puede utilizar este servidor Tomcat integrado para servir solicitudes HTTP.

En este caso:

* el puerto de escucha predeterminado es 8080. Para cambiarlo, consulte [esta sección](configure-tomcat.md).
* Las consolas de cliente se conectan mediante una dirección URL como:

   ```
   http://<computer>:8080
   ```

Sin embargo, por motivos de seguridad y administración, recomendamos utilizar un servidor web dedicado como punto de entrada principal para el tráfico HTTP cuando el equipo que ejecuta Adobe Campaign está expuesto en Internet y desea abrir el acceso a la consola fuera de la red.

Un servidor web también permite garantizar la confidencialidad de los datos con el protocolo HTTP.

Del mismo modo, debe utilizar un servidor web cuando desee utilizar la funcionalidad de seguimiento, que solo está disponible como módulo de extensión para un servidor web.

>[!NOTE]
>
>Si no utiliza la funcionalidad de seguimiento, puede realizar una instalación estándar de Apache o IIS con una redirección a Campaign. El módulo de extensión del servidor web de seguimiento no es necesario.

## Configuración del servidor web Apache con Debian {#configuring-the-apache-web-server-with-debian}

Este proceso se aplica si ha instalado Apache en una distribución basada en APT.

Siga estos pasos:

1. Deshabilite los módulos cargados de forma predeterminada mediante el siguiente comando:

   ```
   a2dismod auth_basic authn_file authz_default authz_user autoindex cgi dir env negotiation userdir
   ```

   Asegúrese de que los módulos **alias**, **authz_host** y **mime** siguen habilitados. Para ello, utilice el siguiente comando:

   ```
   a2enmod  alias authz_host mime
   ```

1. Cree el archivo **nlsrv.load** en **/etc/apache2/mods-available** e inserte el siguiente contenido:

   En Debian 8:

   ```
   LoadModule requesthandler24_module /usr/local/[INSTALL]/nl6/lib/libnlsrvmod.so
   ```

1. Cree el archivo **nlsrv.conf** en **/etc/apache2/mods-available** utilizando el siguiente comando:

   ```
   ln -s /usr/local/[INSTALL]/nl6/conf/apache_neolane.conf /etc/apache2/mods-available/nlsrv.conf
   ```

1. Active este módulo con el siguiente comando:

   ```
    a2enmod nlsrv
   ```

   Si utiliza el módulo **mod_rewrite** para páginas de Adobe Campaign, debe cambiar el nombre de los archivos **nlsrv.load** y **nlsrv.conf** a **zz-nlsrv.load** y **zz-nlsrv.conf a9/>.** Para activar el módulo, ejecute el siguiente comando:

   ```
   a2enmod zz-nlsrv
   ```

1. Edite el archivo **/etc/apache2/envvars** y agregue las siguientes líneas:

   ```
   # Added Neolane
   if [ "$LD_LIBRARY_PATH" != "" ]; then export LD_LIBRARY_PATH="/usr/local/neolane/nl6/lib:$LD_LIBRARY_PATH"; else export LD_LIBRARY_PATH=/usr/local/neolane/nl6/lib; fi
   export USERPATH=/usr/local/neolane
   ```

   Guarde los cambios.

1. A continuación, agregue usuarios de Adobe Campaign al grupo de usuarios de Apache y viceversa utilizando el siguiente tipo de comando:

   ```
   usermod neolane -G www-data
   usermod www-data -G neolane
   ```

1. Reinicie Apache:

   ```
   invoke-rc.d apache2 restart
   ```

## Configuración del servidor web Apache en RHEL {#configuring-apache-web-server-in-rhel}

Este procedimiento se aplica si ha instalado y protegido Apache en un paquete basado en RPM (RHEL, CentOS y Suse).

Siga estos pasos:

1. En el archivo `httpd.conf`, active los siguientes módulos de Apache:

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

1. Cree un archivo de configuración específico de Adobe Campaign en la carpeta `/etc/httpd/conf.d/` . Por ejemplo `CampaignApache.conf`

1. Para **RHEL7**, agregue las siguientes instrucciones en el archivo :

   ```
   LoadModule requesthandler24_module /usr/local/neolane/nl6/lib/libnlsrvmod.so
   Include /usr/local/neolane/nl6/conf/apache_neolane.conf
   ```

1. Para **RHEL7**:

   Añada el archivo `/etc/systemd/system/httpd.service` con el siguiente contenido:

   ```
   .include /usr/lib/systemd/system/httpd.service
   
   [Service]
   Environment=USERPATH=/usr/local/neolane LD_LIBRARY_PATH=/usr/local/neolane/nl6/lib
   ```

   Actualice el módulo utilizado por el sistema:

   ```
   systemctl daemon-reload
   ```

1. A continuación, agregue operadores de Adobe Campaign al grupo de operadores de Apache y viceversa, ejecutando el comando :

   ```
   usermod -a -G neolane apache
   usermod -a -G apache neolane
   ```

   Los nombres de grupo que se van a usar dependen de la forma en que se configure Apache.

1. Ejecute Apache y el servidor Adobe Campaign.

   Para RHEL7:

   ```
   systemctl start httpd
   systemctl start nlserver
   ```

## Inicio del servidor web y prueba de la configuración{#launching-the-web-server-and-testing-the-configuration}

Ahora puede probar la configuración iniciando Apache. El módulo Adobe Campaign debería mostrar ahora su banner en la consola (dos banners en determinados sistemas operativos):

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

Puede comprobarlo desde la línea de comandos ejecutando:

```
 telnet localhost 80  
```

Debe obtener:

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

También puede solicitar la URL [`https://<computer>`](https://myserver.adobe.com/r/test) desde un explorador web.
