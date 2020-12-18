---
solution: Campaign Classic
product: campaign
title: Implementación independiente
description: Implementación independiente
audience: installation
content-type: reference
topic-tags: deployment-types-
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '1132'
ht-degree: 1%

---


# Implementación independiente{#standalone-deployment}

Esta configuración incluye todos los componentes del mismo equipo:

* proceso de solicitud (web),
* proceso de envío (mta),
* proceso de redirección (seguimiento),
* proceso de flujo de trabajo y tareas programadas (wfserver),
* proceso de devolución de correo (enMail),
* proceso de estadísticas (stat).

La comunicación general entre los procesos se realiza con arreglo al siguiente esquema:

![](assets/s_900_ncs_install_standaloneconfig.png)

Este tipo de configuración se puede ejecutar al administrar listas de menos de 100.000 destinatarios y, por ejemplo, con las siguientes capas de software:

* Linux,
* Apache,
* PostgreSQL,
* Correo electrónico.

A medida que aumenta el volumen, una variante de esta arquitectura mueve el servidor de la base de datos a otro equipo para obtener un mejor rendimiento.

>[!NOTE]
>
>También se puede utilizar un servidor de base de datos existente si tiene recursos suficientes.

## Funciones {#features}

### Ventajas {#advantages}

* Costo de configuración completamente independiente y bajo (no se requieren licencias facturables si se utiliza el software de código abierto que se indica a continuación).
* Instalación y configuración de red simplificadas.

### Desventajas {#disadvantages}

* Un equipo crítico en caso de incidente.
* Ancho de banda limitado al transmitir mensajes (en nuestra experiencia, alrededor de varias decenas de miles de correos por hora).
* Posible ralentización de la aplicación durante la retransmisión.
* El servidor de aplicaciones debe estar disponible desde el exterior (mientras se encuentra en DMZ, por ejemplo) ya que aloja el servidor de redirección.

## Pasos de instalación y configuración {#installation-and-configuration-steps}

### Requisitos previos {#prerequisites}

* JDK,
* Servidor web (IIS, Apache),
* Acceso a un servidor de bases de datos,
* Buzón de salida hacia otro sitio accesible mediante POP3,
* Creación de dos alias DNS:

   * el primero expuesto al público para rastrear y apuntar al ordenador en su IP pública;
   * el segundo alias expuesto a los usuarios internos para el acceso a la consola y que apunta al mismo equipo.

* Servidor de seguridad configurado para abrir SMTP (25), DNS (53), HTTP (80), HTTPS (443), SQL (1521 para Oracle, 5432 para PostgreSQL, etc.) puertos. Para obtener más información, consulte [Configuración de red](../../installation/using/network-configuration.md).

En los siguientes ejemplos, los parámetros de la instancia son:

* Nombre de la instancia: **demostración**
* Máscara DNS: **console.campaña.net*** (solo para conexiones de consola de cliente y para informes)
* Base de datos: **campaña:demo@dbsrv**

### Instalación y configuración (una sola máquina) {#installing-and-configuring--single-machine-}

Siga estos pasos:

1. Siga el procedimiento de instalación del servidor de Adobe Campaign: **paquete nlserver** en Linux o **setup.exe** en Windows.

   Para obtener más información sobre esto, consulte [Requisitos previos para la instalación de Campaña en Linux](../../installation/using/prerequisites-of-campaign-installation-in-linux.md) (Linux) y [Requisitos previos para la instalación de Campaña en Windows](../../installation/using/prerequisites-of-campaign-installation-in-windows.md) (Windows).

1. Una vez instalado el servidor de Adobe Campaign, inicio el servidor de aplicaciones (web) mediante el comando **nlserver web -tomcat** (el módulo Web le permite inicio de Tomcat en modo de servidor Web independiente escuchando en el puerto 8080) y para asegurarse de que Tomcat inicio correctamente:

   ```
   12:08:18 >   Application server for Adobe Campaign Classic (7.X YY.R build XXX@SHA1) of DD/MM/YYYY
   12:08:18 >   Starting Web server module (pid=28505, tid=-1225184768)...
   12:08:18 >   Tomcat started
   12:08:18 >   Server started
   ```

   >[!NOTE]
   >
   >La primera vez que se ejecuta el módulo Web, crea los archivos **config-default.xml** y **serverConf.xml** en el directorio **conf** de la carpeta de instalación. Todos los parámetros disponibles en **serverConf.xml** se enumeran en esta [sección](../../installation/using/the-server-configuration-file.md).

   Presione **Ctrl+C** para detener el servidor.

   Para obtener más información sobre esto, consulte las siguientes secciones:

   * Para Linux: [Primer inicio del servidor](../../installation/using/installing-packages-with-linux.md#first-start-up-of-the-server),
   * Para Windows: [Primer inicio del servidor](../../installation/using/installing-the-server.md#first-start-up-of-the-server).

1. Cambie la contraseña **interna** mediante el comando:

   ```
   nlserver config -internalpassword
   ```

   Para obtener más información sobre esto, consulte [Identificador interno](../../installation/using/campaign-server-configuration.md#internal-identifier).

1. Cree la instancia **demo** con las máscaras DNS para el seguimiento (en este caso, **tracking.campaña.net**) y el acceso a consolas de cliente (en este caso, **console.campaña.net**). Hay dos formas de hacerlo:

   * Cree la instancia a través de la consola:

      ![](assets/install_create_new_connexion.png)

      Para obtener más información sobre esto, consulte [Creación de una instancia e inicio de sesión](../../installation/using/creating-an-instance-and-logging-on.md).

      o

   * Cree la instancia mediante líneas de comandos:

      ```
      nlserver config -addinstance:demo/tracking.campaign.net*,console.campaign.net*
      ```

      Para obtener más información sobre esto, consulte [Creación de una instancia](../../installation/using/command-lines.md#creating-an-instance).

1. Edite el archivo **config-demo.xml** (creado en el paso anterior junto a **config-default.xml**) y asegúrese de que **mta** (envío), **wfserver** (flujo de trabajo), **enMail** (correos electrónicos de devolución) y correos electrónicos) Los procesos **stat** (estadísticas) están habilitados. A continuación, configure la dirección del servidor de estadísticas:

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

   Para obtener más información sobre esto, consulte [Habilitación de procesos](../../installation/using/campaign-server-configuration.md#enabling-processes).

1. Edite el archivo **serverConf.xml** y especifique el dominio de envío, luego especifique las direcciones IP (o host) de los servidores DNS utilizados por el módulo MTA para responder consultas DNS de tipo MX.

   ```
   <dnsConfig localDomain="campaign.com" nameServers="192.0.0.1, 192.0.0.2"/>
   ```

   >[!NOTE]
   >
   >El parámetro **nameServers** solo se utiliza en Windows.

   Para obtener más información sobre esto, consulte [configuración del servidor de Campaña](../../installation/using/campaign-server-configuration.md).

1. Copie el programa de configuración de la consola de cliente (**setup-client-7.XX**, **YYYY.exe** para v7 o **setup-client-6.XX**, **YYYY.exe** para v6.1) en **/datakit/nl carpeta /eng/jsp**.

   Para obtener más información sobre esto, consulte las siguientes secciones:

   * Para Linux: [Disponibilidad de la consola del cliente para Linux](../../installation/using/client-console-availability-for-linux.md)
   * Para Windows: [Disponibilidad de la consola de cliente para Windows](../../installation/using/client-console-availability-for-windows.md)

1. Siga el procedimiento de integración del servidor Web (IIS, Apache) descrito en las siguientes secciones:

   * Para Linux: [Integración en un servidor Web para Linux](../../installation/using/integration-into-a-web-server-for-linux.md)
   * Para Windows: [Integración en un servidor Web para Windows](../../installation/using/integration-into-a-web-server-for-windows.md)

1. Inicio del sitio web y prueba la redirección mediante la URL: https://tracking.campaign.net/r/test.

   El explorador debe mostrar el siguiente mensaje:

   ```
   <redir status="OK" date="AAAA/MM/JJ HH:MM:SS" build="XXXX" host="tracking.campaign.net" localHost="localhost"/>
   ```

   Para obtener más información sobre esto, consulte las siguientes secciones:

   * Para Linux: [Inicio del servidor Web y prueba de la configuración](../../installation/using/integration-into-a-web-server-for-linux.md#launching-the-web-server-and-testing-the-configuration)
   * Para Windows: [Inicio del servidor Web y prueba de la configuración](../../installation/using/integration-into-a-web-server-for-windows.md#launching-the-web-server-and-testing-the-configuration)

1. Inicio el servidor Adobe Campaign (**net inicio nlserver6** en Windows, **/etc/init.d/nlserver6 inicio** en Linux) y ejecute el comando **nlserver pdump** una vez más para comprobar la presencia de todos los módulos habilitados.

   >[!NOTE]
   >
   >A partir de 20.1, se recomienda utilizar el siguiente comando en su lugar (para Linux): **inicio de sistema nlserver**

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

1. Pruebe el módulo **nlserver web** con la dirección URL: https://console.campaign.net/nl/jsp/logon.jsp

   Esta URL le permite acceder a la página de descarga del programa de configuración del cliente.

   Introduzca el inicio de sesión **interno** y la contraseña asociada cuando llegue a la página de control de acceso.

   ![](assets/s_ncs_install_access_client.png)

   Para obtener más información sobre esto, consulte las siguientes secciones:

   * Para Linux: [Disponibilidad de la consola del cliente para Linux](../../installation/using/client-console-availability-for-linux.md)
   * Para Windows: [Disponibilidad de la consola de cliente para Windows](../../installation/using/client-console-availability-for-windows.md)

1. Inicio la consola de cliente de Adobe Campaign (desde la página de descarga anterior o se inicia directamente en el servidor para una instalación de Windows), establezca la dirección URL de conexión del servidor en https://console.campaign.net y conéctese mediante el inicio de sesión **interno**.

   Consulte [Creación de una instancia e inicio de sesión en](../../installation/using/creating-an-instance-and-logging-on.md) y [Identificador interno](../../installation/using/campaign-server-configuration.md#internal-identifier).

   El asistente para la creación de bases de datos aparece cuando inicia sesión por primera vez:

   ![](assets/s_ncs_install_db_oracle_creation01.png)

   Siga los pasos del asistente y cree la base de datos asociada a la instancia de conexión.

   Para obtener más información sobre esto, consulte [Creación y configuración de la base de datos](../../installation/using/creating-and-configuring-the-database.md).

   Una vez creada la base de datos, cierre la sesión.

1. Vuelva a iniciar sesión en la consola del cliente mediante el inicio de sesión **admin** sin contraseña y inicio el asistente de implementación ( **[!UICONTROL Tools > Advanced]** menú) para finalizar la configuración de la instancia.

   Para obtener más información sobre esto, consulte [Implementación de una instancia](../../installation/using/deploying-an-instance.md).

   Los parámetros principales que se deben configurar son los siguientes:

   * Envío de correo electrónico: direcciones de remitente y respuesta y el buzón de correo de error para el correo de devolución.
   * Seguimiento: Rellene la dirección URL externa utilizada para la redirección y la dirección URL interna, haga clic en **Registro en los servidores de seguimiento** y, a continuación, valide la misma en la instancia **demo** del servidor de seguimiento.

      Para obtener más información sobre esto, consulte [Configuración de seguimiento](../../installation/using/deploying-an-instance.md#tracking-configuration).

      ![](assets/s_ncs_install_deployment_wiz_09.png)

      Dado que el servidor de Adobe Campaign se utiliza como servidor de aplicaciones y como servidor de redirección, la URL interna utilizada para recopilar registros de seguimiento y transferir direcciones URL es una conexión interna directa con Tomcat (https://localhost:8080).

   * Gestión de devoluciones: Introduzca los parámetros para gestionar el correo de devolución (no tenga en cuenta la sección **Correos de devolución sin procesar**).
   * Acceso desde: Proporcione las dos direcciones URL para informes, Formularios web y páginas espejo.

      ![](assets/d_ncs_install_web_url.png)

