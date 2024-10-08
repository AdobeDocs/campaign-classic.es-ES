---
product: campaign
title: Implementación estándar
description: Implementación estándar
feature: Installation, Architecture, Deployment
audience: installation
content-type: reference
topic-tags: deployment-types-
exl-id: 4df126fa-4a6e-46a7-af6e-1e2e97f0072e
source-git-commit: 0fba6a2ad4ffa864e2f726f241aa9d7cd39072a6
workflow-type: tm+mt
source-wordcount: '836'
ht-degree: 5%

---

# Implementación estándar{#standard-deployment}



Para esta configuración, se requieren tres equipos:

* Un servidor de aplicaciones dentro de la LAN para los usuarios finales (preparación de campañas, creación de informes, etc.),
* Dos servidores frontales en la DMZ detrás de un equilibrador de carga.

Los dos servidores de la DMZ gestionan el seguimiento, las páginas espejo y el envío, y son redundantes para una alta disponibilidad.

El servidor de aplicaciones de la LAN sirve a los usuarios finales y realiza todos los procesos recurrentes (motor de flujo de trabajo). Por lo tanto, cuando se alcanzan cargas máximas en los servidores frontales, los usuarios de la aplicación no se ven afectados.

El servidor de bases de datos puede alojarse en un equipo independiente de estos tres. De lo contrario, el servidor de aplicaciones y el servidor de base de datos comparten el mismo equipo dentro de la LAN siempre que el sistema operativo sea compatible con Adobe Campaign (Linux o Windows).

La comunicación general entre servidores y procesos se realiza según el siguiente esquema:

![](assets/s_001_ncs_install_standardconfig.png)

Este tipo de configuración puede gestionar un gran número de destinatarios (de 500 000 a 1 000 000), ya que el servidor de bases de datos (y el ancho de banda disponible) es el principal factor limitante.

## Funciones {#features}

### Ventajas {#advantages}

* Funcionalidad de conmutación por error: la capacidad de cambiar procesos a un equipo en caso de problemas de hardware en el otro.
* Mejor rendimiento general, ya que las funciones de MTA y redirección se pueden implementar en ambos equipos detrás de un equilibrador de carga. Con dos MTA activos y suficiente ancho de banda, es posible alcanzar tasas de emisión en la región de 100 000 correos por hora.

## Pasos de instalación y configuración {#installation-and-configuration-steps}

### Requisitos previos {#prerequisites}

* JDK en los tres equipos,
* Servidor web (IIS, Apache) en ambos frentes,
* Acceso a un servidor de base de datos en los tres equipos,
* Buzón de rechazos accesible a través de POP3,
* Creación de dos alias DNS:

   * VIP la primera expuesta al público para el seguimiento y señalamiento del equilibrador de carga en una dirección IP virtual () y que luego se distribuye a los dos servidores frontales,
   * el segundo se expone a los usuarios internos para que accedan a él a través de la consola y que señala al mismo servidor de aplicaciones.

* Firewall configurado para abrir STMP (25), DNS (53), HTTP (80), HTTPS (443), SQL (1521 para Oracle, 5432 para PostgreSQL, etc.) puertos. Para obtener más información, consulte la sección [Acceso a la base de datos](../../installation/using/network-configuration.md#database-access).

### Instalación del servidor de aplicaciones {#installing-the-application-server}

Siga los pasos para instalar una instancia independiente desde el servidor de aplicaciones de Adobe Campaign hasta la creación de la base de datos (paso 12). Consulte [Instalar y configurar (un solo equipo)](../../installation/using/standalone-deployment.md#installing-and-configuring--single-machine-).

Dado que el equipo no es un servidor de seguimiento, no tenga en cuenta la integración con el servidor web.

En los ejemplos siguientes, los parámetros de la instancia son:

* Nombre de la instancia: **demo**
* Máscara DNS: **console.campaign.net&#42;** (solo para conexiones de consola de cliente y para informes)
* Idioma: inglés
* Base de datos: **campaign:demo@dbsrv**

### Instalación de los dos servidores frontales {#installing-the-two-frontal-servers}

El procedimiento de instalación y configuración es idéntico en ambos equipos.

Los pasos son los siguientes:

1. Instale el servidor de Adobe Campaign.

   Para obtener más información, consulte [Requisitos previos para la instalación de Campaign en Linux](../../installation/using/prerequisites-of-campaign-installation-in-linux.md) (Linux) y [Requisitos previos para la instalación de Campaign en Windows](../../installation/using/prerequisites-of-campaign-installation-in-windows.md) (Windows).

1. Siga el procedimiento de integración del servidor web (IIS, Apache) descrito en las siguientes secciones:

   * Para Linux: [Integración en un servidor web para Linux](../../installation/using/integration-into-a-web-server-for-linux.md)
   * Para Windows: [Integración en un servidor web para Windows](../../installation/using/integration-into-a-web-server-for-windows.md)

1. Cree la instancia **demo**. Hay dos formas de hacerlo:

   * Cree la instancia a través de la consola:

     ![](assets/install_create_new_connexion.png)

     Para obtener más información, consulte [Crear una instancia e iniciar sesión](../../installation/using/creating-an-instance-and-logging-on.md).

     o

   * Cree la instancia utilizando las líneas de comandos:

     ```
     nlserver config -addinstance:demo/tracking.campaign.net*
     ```

     Para obtener más información, consulte [Creación de una instancia](../../installation/using/command-lines.md#creating-an-instance).

   El nombre de la instancia es el mismo que el del servidor de aplicaciones.

   La conexión al servidor con el módulo **nlserver web** (páginas espejo, baja) se realizará desde la dirección URL del equilibrador de carga (tracking.campaign.net).

1. Cambie **internal** por el mismo que el servidor de aplicaciones.

   Para obtener más información, consulte [esta sección](../../installation/using/configuring-campaign-server.md#internal-identifier).

1. Vincule la base de datos a la instancia:

   ```
   nlserver config -setdblogin:PostgreSQL:campaign:demo@dbsrv -instance:demo
   ```

1. En los archivos **config-default.xml** y **config-demo.xml**, habilite los módulos **web**, **trackinglogd** y **mta**.

   Para obtener más información, consulte [esta sección](../../installation/using/configuring-campaign-server.md#enabling-processes).

1. Edite el archivo **serverConf.xml** y rellene lo siguiente:

   * la configuración DNS del módulo MTA:

     ```
     <dnsConfig localDomain="campaign.com" nameServers="192.0.0.1, 192.0.0.2"/>
     ```

     >[!NOTE]
     >
     >El parámetro **nameServers** solo se usa en Windows.

     Para obtener más información, consulte [Configuración de envío](configure-delivery-settings.md).

   * los servidores de seguimiento redundantes en los parámetros de redirección:

     ```
     <spareServer enabledIf="$(hostname)!='front_srv1'" id="1" url="https://front_srv1:8080"/>
     <spareServer enabledIf="$(hostname)!='front_srv2'" id="2" url="https://front_srv2:8080"/>
     ```

     Para obtener más información, consulte [Seguimiento redundante](configuring-campaign-server.md#redundant-tracking).

1. Inicie el sitio web y pruebe la redirección desde la dirección URL: [https://tracking.campaign.net/r/test](https://tracking.campaign.net/r/test).

   El explorador debe mostrar los siguientes mensajes (según la URL redirigida por el equilibrador de carga):

   ```
   <redir status="OK" date="AAAA/MM/JJ HH:MM:SS" build="XXXX" host="tracking.campaign.net" localHost="front_srv1"/>
   ```

   o

   ```
   <redir status="OK" date="AAAA/MM/JJ HH:MM:SS" build="XXXX" host="tracking.campaign.net" localHost="front_srv2"/>
   ```

   Para obtener más información, consulte las siguientes secciones:

   * Para Linux: [Iniciando el servidor web y probando la configuración](../../installation/using/integration-into-a-web-server-for-linux.md#launching-the-web-server-and-testing-the-configuration)
   * Para Windows: [Iniciando el servidor web y probando la configuración](../../installation/using/integration-into-a-web-server-for-windows.md#launching-the-web-server-and-testing-the-configuration)

1. Inicie el servidor de Adobe Campaign.
1. En la consola de Adobe Campaign, conéctese con el inicio de sesión de **admin** sin contraseña e inicie el asistente de implementación.

   Para obtener más información, consulte [Implementación de una instancia](../../installation/using/deploying-an-instance.md).

   La configuración es idéntica a una instancia independiente, aparte de la configuración del módulo de seguimiento.

1. Rellene la URL externa (la del equilibrador de carga) utilizada para la redirección y las URL internas de los dos servidores frontales.

   Para obtener más información, consulte [Configuración de seguimiento](../../installation/using/deploying-an-instance.md#tracking-configuration).

   ![](assets/d_ncs_install_tracking2.png)

   >[!NOTE]
   >
   >Utilizamos la instancia existente de los dos servidores de seguimiento creados anteriormente y usamos el inicio de sesión **interno**.
