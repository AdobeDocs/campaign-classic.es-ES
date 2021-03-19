---
solution: Campaign Classic
product: campaign
title: Configuración del servidor de Campaign
description: Configuración del servidor de Campaign
audience: installation
content-type: reference
topic-tags: initial-configuration
translation-type: tm+mt
source-git-commit: 95d0686c4ddeb4e25eb918ca92cbd6a0b1aa1f3c
workflow-type: tm+mt
source-wordcount: '547'
ht-degree: 2%

---


# Configuración del servidor de Campaign{#campaign-server-configuration}

Las siguientes secciones detallan las configuraciones de servidor obligatorias que garantizarán el funcionamiento eficiente de Adobe Campaign para la mayoría de las configuraciones.

Se ofrecen configuraciones adicionales en [Configuración del servidor de Campaign](../../installation/using/configuring-campaign-server.md).

>[!NOTE]
>
>Las configuraciones del lado del servidor solo se pueden realizar mediante Adobe para implementaciones alojadas en Adobe. Para obtener más información sobre las diferentes implementaciones, consulte la sección [Hosting models](../../installation/using/hosting-models.md) o [the capacity matrix](../../installation/using/capability-matrix.md).

## Identificador interno {#internal-identifier}

El identificador **internal** es un inicio de sesión técnico que se utilizará con fines de instalación, administración y mantenimiento. Este inicio de sesión no está asociado a una instancia.

Los operadores conectados mediante este inicio de sesión tendrán todos los derechos en todas las instancias. Este inicio de sesión no tendrá contraseña en el caso de una nueva instalación. Debe definir manualmente esta contraseña.

Utilice el siguiente comando:

```
nlserver config -internalpassword
```

A continuación, se muestra la siguiente información. Introduzca y confirme la contraseña:

```
17:33:57 >   Application server for Adobe Campaign Classic (7.X YY.R build XXX@SHA1) of DD/MM/YYYY
Enter the current password.
Password:
Enter the new password.
Password: XXXX
Confirmation: XXXX
17:34:02 >   Password successfully changed for account 'internal' (authentication mode 'nl')
```

## Archivos de configuración {#configuration-files}

Los archivos de configuración se almacenan en la carpeta **conf** de la carpeta de instalación de Adobe Campaign. La configuración se distribuye en dos archivos:

* **`config-<instance>.xml`** (donde  **** instancia es el nombre de la instancia): configuración específica de la instancia. Si comparte el servidor entre varias instancias, introduzca los parámetros específicos de cada instancia en su archivo correspondiente.
* **serverConf.xml**: configuración general para todas las instancias. Este archivo combina los parámetros técnicos del servidor Adobe Campaign: todas las instancias las comparten. A continuación se detalla la descripción de algunos de estos parámetros. Consulte el archivo para ver todos los parámetros disponibles. Los diferentes nodos y parámetros y enumerados en esta [sección](../../installation/using/the-server-configuration-file.md).

Puede configurar el directorio de almacenamiento (directorio **var**) de datos de Adobe Campaign (registros, descargas, redirecciones, etc.). Para ello, utilice la variable del sistema **XTK_VAR_DIR**:

* En Windows, indique el siguiente valor en la variable de sistema **XTK_VAR_DIR**

   ```
   D:\log\AdobeCampaign
   ```

* En Linux, vaya al archivo **customer.sh** e indique: **exportar XTK_VAR_DIR=/app/log/AdobeCampaign**.

   Para obtener más información, consulte [Personalize parameters](../../installation/using/installing-packages-with-linux.md#personalizing-parameters).

## Habilitar procesos {#enabling-processes}

Los procesos de Adobe Campaign en el servidor están habilitados (y deshabilitados) a través de los archivos **config-default.xml** y **`config-<instance>.xml`** .

Para aplicar los cambios a estos archivos, si se inicia el servicio de Adobe Campaign, debe ejecutar el comando **nlserver config -reload**.

Existen dos tipos de procesos: instancia múltiple y instancia única.

* **varias instancias**: se inicia un solo proceso para todas las instancias. Este es el caso de los procesos **web**, **syslogd** y **trackinglogd**.

   La habilitación se puede configurar desde el archivo **config-default.xml**.

   Declaración de un servidor de Adobe Campaign para acceder a las consolas de cliente y para la redirección (seguimiento):

   ```
   vi nl6/conf/config-default.xml
   <web args="-tomcat" autoStart="true"/>  
   <!-- to start if the machine is also a redirection server -->  
   <trackinglogd autoStart="true"/>
   ```

   En este ejemplo, el archivo se edita mediante un comando **vi** en Linux. Se puede editar con cualquier editor **.txt** o **.xml**.

* **instancia** mono: se inicia un proceso para cada instancia (módulos:  **mta**,  **wfserver**,  **inMail**,  **** smand  **stat**).

   La habilitación se puede configurar utilizando el archivo de configuración de la instancia:

   ```
   config-<instance>.xml
   ```

   Declarar un servidor para su envío, ejecutar instancias de flujo de trabajo y recuperar el correo rechazado:

   ```
   <mta autoStart="true" statServerAddress="localhost"/>
   <wfserver autoStart="true"/>  
   <inMail autoStart="true"/>
   <stat autoStart="true"/>
   ```

## Configuración de envío {#delivery-settings}

Los parámetros de envío deben configurarse en la carpeta **serverConf.xml**.

* **Configuración** de DNS: especifique el dominio de entrega y las direcciones IP (o host) de los servidores DNS utilizados para responder a consultas DNS de tipo MX realizadas por el módulo MTA a partir de  **`<dnsconfig>`** entonces.

   >[!NOTE]
   >
   >El parámetro **nameServers** es esencial para una instalación en Windows. Para una instalación en Linux, debe dejarse vacía.

   ```
   <dnsConfig localDomain="domain.com" nameServers="192.0.0.1,192.0.0.2"/>
   ```

Los demás parámetros de envío disponibles en este archivo se presentan en [Personalize delivery parameters](../../installation/using/configuring-campaign-server.md#personalizing-delivery-parameters).

Consulte también [Email deliverability](../../installation/using/email-deliverability.md).
