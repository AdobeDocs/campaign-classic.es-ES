---
product: campaign
title: Implementación empresarial
description: Implementación empresarial
feature: Installation, Architecture, Deployment
badge-v7-only: label="v7" type="Informative" tooltip="Se aplica solo a Campaign Classic v7"
audience: installation
content-type: reference
topic-tags: deployment-types-
exl-id: 38c14010-203a-47ab-b23d-6f431dab9a88
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: tm+mt
source-wordcount: '1225'
ht-degree: 7%

---

# Implementación empresarial{#enterprise-deployment}



Esta es la configuración más completa. Se basa en la configuración estándar para una mayor seguridad y disponibilidad:

* servidores de redirección dedicados detrás de un equilibrador de carga HTTP o TCP, para escalabilidad y disponibilidad,
* dos servidores de aplicaciones para mejorar el rendimiento y la capacidad de recuperación ante fallos (tolerancia ante fallos) y que están aislados en la LAN.

La comunicación general entre servidores y procesos se realiza según el siguiente esquema:

![](assets/s_901_ncs_install_enterpriseconfig.png)

Con este tipo de configuración, el rendimiento esperado puede superar los 100 000 correos por hora con el ancho de banda y el ajuste adecuados.

## Funciones {#features}

### Ventajas {#advantages}

* Seguridad optimizada: solo los servidores que necesitan estar expuestos al exterior se instalan en el equipo en la DMZ.
* Alta disponibilidad más fácil de garantizar: solo el ordenador visible desde el exterior debe gestionarse teniendo en cuenta la alta disponibilidad.

### Desventajas {#disadvantages}

Mayores costes de hardware y administración.

### Equipo recomendado {#recommended-equipment}

* Servidores de aplicaciones: CPU de núcleo cuádruple a 2 GHz, 4 GB de RAM, RAID de software, disco duro SATA de 80 GB.
* Servidores de redirección: CPU de núcleo cuádruple a 2 GHz, 4 GB de RAM, disco duro SATA de 80 GB RAID por software.

>[!NOTE]
>
>Es posible reutilizar un equilibrador de carga existente para el tráfico a los servidores de redirección.

## Pasos de instalación y configuración {#installation-and-configuration-steps}

### Requisitos previos {#prerequisites}

* JDK en ambos servidores de aplicaciones,
* Servidor web (IIS, Apache) en ambos frentes,
* Acceso a un servidor de base de datos en ambos servidores de aplicaciones,
* Buzón de rechazos accesible a través de POP3,
* Creación de dos alias DNS en el equilibrador de carga:

   * VIP la primera expuesta al público para el seguimiento y señalamiento del equilibrador de carga en una dirección IP virtual () y que luego se distribuye a los dos servidores frontales,
   * VIP el segundo expuesto a los usuarios internos para el acceso a través de la consola y que apunta a un equilibrador de carga en una dirección IP virtual () y que luego se distribuye a los dos servidores de aplicaciones.

* Firewall configurado para abrir STMP (25), DNS (53), HTTP (80), HTTPS (443), SQL (1521 para Oracle, 5432 para PostgreSQL, etc.) puertos. Para obtener más información, consulte esta sección [Acceso a base de datos](../../installation/using/network-configuration.md#database-access).

>[!CAUTION]
>
>Si los servidores de aplicaciones apuntan a una sola instancia de base de datos, después de importar un paquete estándar en una instancia, el esquema contenido en el paquete no se carga en la otra instancia.
>  
>Si los servidores de aplicaciones apuntan a una sola instancia de base de datos, después de cambiar el esquema en una instancia, el esquema no se carga en la otra instancia.
>
>Para recuperar estos problemas, debe reiniciar el proceso &quot;web@default&quot; en la segunda instancia en la que se produjo el error.

### Instalación y configuración del servidor de aplicaciones 1 {#installing-and-configuring-the-application-server-1}

En los ejemplos siguientes, los parámetros de la instancia son:

* Nombre de la instancia: demo
* Máscara DNS: tracking.campaign.net&#42;, console.campaign.net&#42; (el servidor de aplicaciones administra las direcciones URL de las conexiones e informes de la consola del cliente y de las páginas espejo y las páginas de baja)
* Idioma: inglés
* Base de datos: campaign:demo@dbsrv

Los pasos para instalar el primer servidor son los siguientes:

1. Siga el procedimiento de instalación del servidor de Adobe Campaign: **nlserver** paquete en Linux o **setup.exe** en Windows.

   Para obtener más información, consulte [Requisitos previos para la instalación de Campaign en Linux](../../installation/using/prerequisites-of-campaign-installation-in-linux.md) (Linux) y [Requisitos previos para la instalación de Campaign en Windows](../../installation/using/prerequisites-of-campaign-installation-in-windows.md) (Windows).

1. Una vez instalado el servidor de Adobe Campaign, inicie el servidor de aplicaciones (web) con el comando **nlserver web -tomcat** (el módulo Web le permite iniciar Tomcat en modo de servidor web independiente escuchando en el puerto 8080) y asegurarse de que Tomcat se inicia correctamente:

   ```
   12:08:18 >   Application server for Adobe Campaign Classic (7.X YY.R build XXX@SHA1) of DD/MM/YYYY
   12:08:18 >   Starting Web server module (pid=28505, tid=-1225184768)...
   12:08:18 >   Tomcat started
   12:08:18 >   Server started
   ```


   >[!NOTE]
   >
   >La primera vez que se ejecuta el módulo web, crea el **config-default.xml** y **serverConf.xml** archivos en la **conf** en la carpeta de instalación. Todos los parámetros disponibles en **serverConf.xml** se enumeran en esta [sección](../../installation/using/the-server-configuration-file.md).

   Prensa **Ctrl + C** para detener el servidor.

   Para obtener más información, consulte las siguientes secciones:

   * Para Linux: [Primer inicio del servidor](../../installation/using/installing-packages-with-linux.md#first-start-up-of-the-server)
   * Para Windows: [Primer inicio del servidor](../../installation/using/installing-the-server.md#first-start-up-of-the-server)

1. Cambie el **interno** contraseña con el comando:

   ```
   nlserver config -internalpassword
   ```

   Para obtener más información, consulte [esta sección](../../installation/using/configuring-campaign-server.md#internal-identifier).

1. Cree el **demostración** instancia con las máscaras DNS para el seguimiento (en este caso, **tracking.campaign.net**) y acceso a las consolas de cliente (en este caso, **console.campaign.net**). Hay dos formas de hacerlo:

   * Cree la instancia a través de la consola:

     ![](assets/install_create_new_connexion.png)

     Para obtener más información, consulte [Creación de una instancia e inicio de sesión](../../installation/using/creating-an-instance-and-logging-on.md).

     o

   * Cree la instancia utilizando las líneas de comandos:

     ```
     nlserver config -addinstance:demo/tracking.campaign.net*,console.campaign.net*
     ```

     Para obtener más información, consulte [Creación de una instancia](../../installation/using/command-lines.md#creating-an-instance).

1. Edite el **config-demo.xml** (creado mediante el comando anterior y ubicado junto al archivo **config-default.xml** ), compruebe que la variable **mta** (envío), **wfserver** (flujo de trabajo), **inMail** (correos electrónicos de rebote) y **estadísticas** (estadísticas) los procesos están activados y, a continuación, configure la dirección del **aplicación** servidor de estadísticas:

   ```
   <?xml version='1.0'?>
   <serverconf>  
     <shared>    
       <!-- add lang="eng" to dataStore to force English for the instance -->    
       <dataStore hosts="tracking.campaign.net*,console.campaign.net*">      
         <mapping logical="*" physical="default"/>    
       </dataStore>  </shared>  
       <mta autoStart="true" statServerAddress="app">
       <wfserver autoStart="true"/>  
       <inMail autoStart="true"/>  
       <sms autoStart="false"/>  
       <listProtect autoStart="false"/>
   </serverconf>
   ```

   Para obtener más información, consulte [esta sección](../../installation/using/configuring-campaign-server.md#enabling-processes).

1. Edite el **serverConf.xml** y especifique el dominio de entrega y, a continuación, especifique las direcciones IP (o host) de los servidores DNS utilizados por el módulo MTA para responder consultas DNS de tipo MX.

   ```
   <dnsConfig localDomain="campaign.com" nameServers="192.0.0.1, 192.0.0.2"/>
   ```

   >[!NOTE]
   >
   >El **nameServers** solo se usa en Windows.

   Para obtener más información, consulte [Configuración del servidor de Campaign](../../installation/using/configuring-campaign-server.md).

1. Copiar el programa de configuración de la consola del cliente **setup-client-7.XX**, **YYYY.exe** a la **/datakit/nl/eng/jsp** carpeta. [Más información](../../installation/using/client-console-availability-for-windows.md).

1. Inicie el servidor de Adobe Campaign (**net start nlserver6** en Windows, **Inicio de /etc/init.d/nlserver6** en Linux) y ejecute el comando **nlserver pdump** una vez más para comprobar la presencia de todos los módulos habilitados.

   >[!NOTE]
   >
   >A partir de la versión 20.1, se recomienda utilizar el siguiente comando (para Linux): **systemctl start nlserver**


   ```
   12:09:54 >   Application server for Adobe Campaign Classic (7.X YY.R build XXX@SHA1) of DD/MM/YYYY
   syslogd@default (7611) - 9.2 MB
   stat@demo (5988) - 1.5 MB
   inMail@demo (7830) - 11.9 MB
   watchdog (27369) - 3.1 MB
   mta@demo (7831) - 15.6 MB
   wfserver@demo (7832) - 11.5 MB
   web@default (28671) - 40.5 MB
   ```

   Este comando también le permite conocer la versión y el número de compilación del servidor de Adobe Campaign instalado en el equipo.

1. Pruebe el **nlserver web** mediante la dirección URL: [https://console.campaign.net/nl/jsp/logon.jsp](https://tracking.campaign.net/r/test).

   Esta URL le permite acceder a la página de descarga del programa de instalación del cliente. [Más información](../../installation/using/client-console-availability-for-windows.md).

   Introduzca el **interno** inicio de sesión y contraseña asociada al llegar a la página de control de acceso.

   ![](assets/s_ncs_install_access_client.png)

### Instalación y configuración del servidor de aplicaciones 2 {#installing-and-configuring-the-application-server-2}

Siga estos pasos:

1. Instale el servidor de Adobe Campaign.
1. Copie los archivos de la instancia que ha creado en el servidor de aplicaciones 1.

   Mantenemos el mismo nombre de instancia que el servidor de aplicaciones 1.

1. Cambie el **interno** al igual que el servidor de aplicaciones 1.
1. Vincule la base de datos a la instancia:

   ```
   nlserver config -setdblogin:PostgreSQL:campaign:demo@dbsrv -instance:demo
   ```

1. Edite el **config-demo.xml** (creado mediante el comando anterior y ubicado junto al archivo **config-default.xml** ), compruebe que la variable **mta** (envío), **wfserver** (flujo de trabajo), **inMail** (correos electrónicos de rebote) y **estadísticas** (estadísticas) los procesos están activados y, a continuación, configure la dirección del **aplicación** servidor de estadísticas:

   ```
   <?xml version='1.0'?>
   <serverconf>  
     <shared>    
       <!-- add lang="eng" to dataStore to force English for the instance -->    
       <dataStore hosts="tracking.campaign.net*,console.campaign.net*">      
         <mapping logical="*" physical="default"/>    
       </dataStore>  </shared>  
       <mta autoStart="true" statServerAddress="app">
       <wfserver autoStart="true"/>  
       <inMail autoStart="true"/>  
       <sms autoStart="false"/>  
       <listProtect autoStart="false"/>
   </serverconf>
   ```

   Para obtener más información, consulte [esta sección](../../installation/using/configuring-campaign-server.md#enabling-processes).

1. Edite el **serverConf.xml** y rellenar la configuración DNS del módulo MTA:

   ```
   <dnsConfig localDomain="campaign.com" nameServers="192.0.0.1, 192.0.0.2"/>
   ```

   >[!NOTE]
   >
   >El **nameServers** El parámetro solo se utiliza en Windows.

   Para obtener más información, consulte [Configuración del servidor de Campaign](../../installation/using/configuring-campaign-server.md).

1. Inicie los servidores de Adobe Campaign.

   Para obtener más información, consulte las siguientes secciones:

   * Para Linux: [Primer inicio del servidor](../../installation/using/installing-packages-with-linux.md#first-start-up-of-the-server)
   * Para Windows: [Primer inicio del servidor](../../installation/using/installing-the-server.md#first-start-up-of-the-server)

### Instalación y configuración de los servidores frontales {#installing-and-configuring-the-frontal-servers}

Los procedimientos de instalación y configuración son idénticos en ambos equipos.

Los pasos son los siguientes:

1. Instale el servidor de Adobe Campaign,
1. Siga el procedimiento de integración del servidor web (IIS, Apache) descrito en las siguientes secciones:

   * Para Linux: [Integración en un servidor web para Linux](../../installation/using/integration-into-a-web-server-for-linux.md),
   * Para Windows: [Integración en un servidor web para Windows](../../installation/using/integration-into-a-web-server-for-windows.md).

1. Copie el **config-demo.xml** y **serverConf.xml** archivos creados durante la instalación. En el **config-demo.xml** , active el archivo **trackinglogd** procesar y desactivar el **mta**, **en el correo**, **wfserver** y **estadísticas** procesos.
1. Edite el **serverConf.xml** y rellene los servidores de seguimiento redundantes en los parámetros de la redirección:

   ```
   <spareServer enabledIf="$(hostname)!='front_srv1'" id="1" url="https://front_srv1:8080"/>
   <spareServer enabledIf="$(hostname)!='front_srv2'" id="2" url="https://front_srv2:8080"/>
   ```

1. Inicie el sitio web y pruebe la redirección desde la dirección URL: [https://tracking.campaign.net/r/test](https://tracking.campaign.net/r/test)

   El explorador debe mostrar los siguientes mensajes (según la URL redirigida por el equilibrador de carga):

   ```
   <redir status="OK" date="AAAA/MM/JJ HH:MM:SS" build="XXXX" host="tracking.campaign.net" localHost="front_srv1"/>
   ```

   o

   ```
   <redir status="OK" date="AAAA/MM/JJ HH:MM:SS" build="XXXX" host="tracking.campaign.net" localHost="front_srv2"/>
   ```

   Para obtener más información, consulte las siguientes secciones:

   * Para Linux: [Inicio del servidor web y prueba de la configuración](../../installation/using/integration-into-a-web-server-for-linux.md#launching-the-web-server-and-testing-the-configuration),
   * Para Windows: [Inicio del servidor web y prueba de la configuración](../../installation/using/integration-into-a-web-server-for-windows.md#launching-the-web-server-and-testing-the-configuration).

1. Inicie el servidor de Adobe Campaign.
