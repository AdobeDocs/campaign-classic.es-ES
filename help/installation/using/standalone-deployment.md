---
product: campaign
title: Implementación independiente
description: Implementación independiente
feature: Installation, Architecture, Deployment
audience: installation
content-type: reference
topic-tags: deployment-types-
exl-id: 194366ab-fd9f-4431-9163-ae16c1f96db2
source-git-commit: 1be1528d657537786c430ea9c8bdb3aad58ba20d
workflow-type: tm+mt
source-wordcount: '1077'
ht-degree: 5%

---

# Implementación independiente{#standalone-deployment}



Esta configuración incluye todos los componentes del mismo equipo:

* proceso de solicitud (web),
* proceso de envío (mta),
* proceso de redirección (seguimiento),
* proceso de flujo de trabajo y tareas programadas (wfserver),
* proceso de correo rechazado (inMail),
* proceso de estadísticas (stat).

La comunicación general entre los procesos se realiza según el siguiente esquema:

![](assets/s_900_ncs_install_standaloneconfig.png)

Este tipo de configuración se puede ejecutar al administrar listas de menos de 100 000 destinatarios y, por ejemplo, con las siguientes capas de software:

* Linux,
* Apache,
* PostgreSQL,
* Qmail.

A medida que el volumen crece, una variante de esta arquitectura mueve el servidor de base de datos a otro equipo para obtener un mejor rendimiento.

>[!NOTE]
>
>También se puede utilizar un servidor de base de datos existente si tiene recursos suficientes.

## Funciones {#features}

### Ventajas {#advantages}

* Completamente independiente y bajo coste de configuración (no se requieren licencias facturables si se utiliza el software de código abierto que se indica a continuación).
* Instalación y configuración de red simplificadas.

### Desventajas {#disadvantages}

* Una computadora crítica en caso de incidente.
* Ancho de banda limitado al transmitir mensajes (en nuestra experiencia, unas decenas de miles de correos por hora).
* Posible ralentización de la aplicación durante la retransmisión.
* El servidor de aplicaciones debe estar disponible desde el exterior (aunque esté ubicado en la DMZ, por ejemplo), ya que aloja el servidor de redirección.

## Pasos de instalación y configuración {#installation-and-configuration-steps}

### Requisitos previos {#prerequisites}

* JDK,
* Servidor web (IIS, Apache),
* Acceso a un servidor de base de datos,
* Buzón de rechazos accesible a través de POP3,
* Creación de dos alias DNS:

   * el primero expuesto al público para rastrear y apuntar al ordenador en su IP pública;
   * el segundo alias expuesto a los usuarios internos para el acceso a la consola y que señala al mismo equipo.

* Firewall configurado para abrir SMTP (25), DNS (53), HTTP (80), HTTPS (443), SQL (1521 para Oracle, 5432 para PostgreSQL, etc.) puertos. Para obtener más información, consulte [Configuración de red](../../installation/using/network-configuration.md).

En los ejemplos siguientes, los parámetros de la instancia son:

* Nombre de la instancia: **demo**
* Máscara DNS: **console.campaign.net&#42;** (solo para conexiones de consola de cliente y para informes)
* Base de datos: **campaign:demo@dbsrv**

### Instalación y configuración (un solo equipo) {#installing-and-configuring--single-machine-}

Siga estos pasos:

1. Siga el procedimiento de instalación del servidor de Adobe Campaign: paquete **nlserver** en Linux o **setup.exe** en Windows.

   Para obtener más información, consulte [Requisitos previos para la instalación de Campaign en Linux](../../installation/using/prerequisites-of-campaign-installation-in-linux.md) (Linux) y [Requisitos previos para la instalación de Campaign en Windows](../../installation/using/prerequisites-of-campaign-installation-in-windows.md) (Windows).

1. Una vez instalado el servidor de Adobe Campaign, inicie el servidor de aplicaciones (web) con el comando **nlserver web -tomcat** (el módulo web le permite iniciar Tomcat en modo de servidor web independiente escuchando en el puerto 8080) y asegúrese de que Tomcat se inicia correctamente:

   ```sql
   12:08:18 >   Application server for Adobe Campaign Classic (7.X YY.R build XXX@SHA1) of DD/MM/YYYY
   12:08:18 >   Starting Web server module (pid=28505, tid=-1225184768)...
   12:08:18 >   Tomcat started
   12:08:18 >   Server started
   ```

   >[!NOTE]
   >
   >La primera vez que se ejecuta el módulo web, crea los archivos **config-default.xml** y **serverConf.xml** en el directorio **conf** en la carpeta de instalación. Todos los parámetros disponibles en **serverConf.xml** se enumeran en esta [sección](../../installation/using/the-server-configuration-file.md).

   Presione **Ctrl+C** para detener el servidor.

   Para obtener más información, consulte las siguientes secciones:

   * Para Linux: [Primer inicio del servidor](../../installation/using/installing-packages-with-linux.md#first-start-up-of-the-server),
   * Para Windows: [Primer inicio del servidor](../../installation/using/installing-the-server.md#first-start-up-of-the-server).

1. Cambie la contraseña de **internal** mediante el comando:

   ```
   nlserver config -internalpassword
   ```

   Para obtener más información, consulte [esta sección](../../installation/using/configuring-campaign-server.md#internal-identifier).

1. Cree la instancia **demo** con las máscaras DNS para seguimiento (en este caso, **tracking.campaign.net**) y acceso a las consolas de cliente (en este caso, **console.campaign.net**). Hay dos formas de hacerlo:

   * Cree la instancia a través de la consola:

     ![](assets/install_create_new_connexion.png)

     Para obtener más información, consulte [Crear una instancia e iniciar sesión](../../installation/using/creating-an-instance-and-logging-on.md).

     o

   * Cree la instancia utilizando las líneas de comandos:

     ```
     nlserver config -addinstance:demo/tracking.campaign.net*,console.campaign.net*
     ```

     Para obtener más información, consulte [Creación de una instancia](../../installation/using/command-lines.md#creating-an-instance).

1. Edite el archivo **config-demo.xml** (creado en el paso anterior junto a **config-default.xml**) y asegúrese de que los procesos **mta** (entrega), **wfserver** (flujo de trabajo), **inMail** (correos rechazados) y **stat** (estadísticas) estén habilitados. A continuación, configure la dirección del servidor de estadísticas:

   ```
   <?xml version='1.0'?>
   <serverconf>  
     <shared>    
       <!-- add lang="eng" to dataStore to force English for the instance -->    
       <dataStore hosts="tracking.campaign.net*,console.campaign.net*">      
         <mapping logical="*" physical="default"/>    
       </dataStore>  </shared>  
       <mta autoStart="true" statServerAddress="localhost"/>
       <wfserver autoStart="true"/>  
       <inMail autoStart="true"/>  
       <sms autoStart="false"/>  
       <listProtect autoStart="false"/>
   </serverconf>
   ```

   Para obtener más información, consulte [esta sección](../../installation/using/configuring-campaign-server.md#enabling-processes).

1. Edite el archivo **serverConf.xml**, especifique el dominio de entrega y, a continuación, especifique las direcciones IP (o de host) de los servidores DNS utilizados por el módulo MTA para responder a consultas DNS de tipo MX.

   ```
   <dnsConfig localDomain="campaign.com" nameServers="192.0.0.1, 192.0.0.2"/>
   ```

   >[!NOTE]
   >
   >El parámetro **nameServers** solo se usa en Windows.

   Para obtener más información, consulte [Configuración del servidor de Campaign](../../installation/using/configuring-campaign-server.md).

1. Copie el programa de instalación de la consola del cliente **setup-client-7.XXX.exe** en la carpeta **/datakit/nl/eng/jsp**. [Más información](../../installation/using/client-console-availability-for-windows.md).

1. Siga el procedimiento de integración del servidor web (IIS, Apache) descrito en las siguientes secciones:

   * Para Linux: [Integración en un servidor web para Linux](../../installation/using/integration-into-a-web-server-for-linux.md)
   * Para Windows: [Integración en un servidor web para Windows](../../installation/using/integration-into-a-web-server-for-windows.md)

1. Inicie el sitio web y pruebe la redirección con la dirección URL: https://tracking.campaign.net/r/test.

   El explorador debe mostrar el siguiente mensaje:

   ```
   <redir status="OK" date="AAAA/MM/JJ HH:MM:SS" build="XXXX" host="tracking.campaign.net" localHost="localhost"/>
   ```

   Para obtener más información, consulte las siguientes secciones:

   * Para Linux: [Iniciando el servidor web y probando la configuración](../../installation/using/integration-into-a-web-server-for-linux.md#launching-the-web-server-and-testing-the-configuration)
   * Para Windows: [Iniciando el servidor web y probando la configuración](../../installation/using/integration-into-a-web-server-for-windows.md#launching-the-web-server-and-testing-the-configuration)

1. Inicie el servidor de Adobe Campaign (**net start nlserver6** en Windows, **/etc/init.d/nlserver6 start** en Linux) y ejecute el comando **nlserver pdump** una vez más para comprobar la presencia de todos los módulos habilitados.

   >[!NOTE]
   >
   >A partir de la versión 20.1, se recomienda utilizar el siguiente comando (en Linux): **systemctl start nlserver**

   ```sql
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

1. Pruebe el módulo **nlserver web** con la dirección URL: https://console.campaign.net/nl/jsp/logon.jsp

   Esta URL le permite acceder a la página de descarga del programa de instalación del cliente.

   Escriba el inicio de sesión de **internal** y la contraseña asociada cuando llegue a la página de control de acceso. [Más información](../../installation/using/client-console-availability-for-windows.md).

   ![](assets/s_ncs_install_access_client.png)

1. Inicie la consola del cliente de Adobe Campaign (desde la página de descarga anterior o iniciada directamente en el servidor para una instalación de Windows), establezca la URL de conexión del servidor en https://console.campaign.net y conéctese con el inicio de sesión **internal**.

   Consulte [esta página](../../installation/using/creating-an-instance-and-logging-on.md) y [esta sección](../../installation/using/configuring-campaign-server.md#internal-identifier).

   El asistente para la creación de bases de datos aparece cuando se inicia una sesión por primera vez:

   ![](assets/s_ncs_install_db_oracle_creation01.png)

   Siga los pasos del asistente y cree la base de datos asociada a la instancia de conexión.

   Para obtener más información, consulte [Creación y configuración de la base de datos](../../installation/using/creating-and-configuring-the-database.md).

   Una vez creada la base de datos, cierre la sesión.

1. Vuelva a iniciar sesión en la consola del cliente con el inicio de sesión de **admin** sin contraseña e inicie el asistente de implementación (menú **[!UICONTROL Tools > Advanced]**) para finalizar la configuración de la instancia.

   Para obtener más información, consulte [Implementación de una instancia](../../installation/using/deploying-an-instance.md).

   Los parámetros principales que se van a establecer son los siguientes:

   * Entrega de correo electrónico: direcciones de remitente y respuesta y el buzón de error para el correo rechazado.
   * Seguimiento: Rellene la dirección URL externa utilizada para la redirección y la dirección URL interna, haga clic en **Registro en los servidores de seguimiento** y, a continuación, valide la URL en la instancia **demo** del servidor de seguimiento.

     Para obtener más información, consulte [Configuración de seguimiento](../../installation/using/deploying-an-instance.md#tracking-configuration).

     ![](assets/s_ncs_install_deployment_wiz_09.png)

     Como el servidor de Adobe Campaign se utiliza como servidor de aplicaciones y de redirección, la URL interna utilizada para recopilar registros de seguimiento y transferir URL es una conexión interna directa a Tomcat (https://localhost:8080).

   * Administración de devoluciones: introduzca los parámetros para administrar el correo rechazado (no tenga en cuenta la sección **Correos de devolución sin procesar**).
   * Acceso desde: proporcione las dos direcciones URL para los informes, los formularios web y las páginas espejo.

     ![](assets/d_ncs_install_web_url.png)
