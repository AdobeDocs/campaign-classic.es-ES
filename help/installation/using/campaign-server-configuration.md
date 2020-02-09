---
title: Configuración del servidor de campañas
seo-title: Configuración del servidor de campañas
description: Configuración del servidor de campañas
seo-description: null
page-status-flag: never-activated
uuid: a1fadad2-e888-4dd8-bc1f-04df16ba7d46
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: installation
content-type: reference
topic-tags: initial-configuration
discoiquuid: f296676e-3bf1-47da-8239-f5ae54e52fc0
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 4869eb41f942a89c48bc213913c44b70ae777bfc

---


# Configuración del servidor de campañas{#campaign-server-configuration}

En las siguientes secciones se detallan las configuraciones obligatorias del servidor que garantizarán el funcionamiento eficiente de Adobe Campaign en la mayoría de las configuraciones.

Se ofrecen configuraciones adicionales en [Configuración del servidor](../../installation/using/configuring-campaign-server.md)de campañas.

>[!NOTE]
>
>Adobe solo puede realizar las configuraciones del lado del servidor para implementaciones alojadas en Adobe. Para obtener más información sobre las diferentes implementaciones, consulte la sección [Hosting models](../../installation/using/hosting-models.md) o este [artículo](https://helpx.adobe.com/campaign/kb/acc-on-prem-vs-hosted.html).

## Identificador interno {#internal-identifier}

El identificador **interno** es un inicio de sesión técnico que se utiliza con fines de instalación, administración y mantenimiento. Este inicio de sesión no está asociado a una instancia.

Los operadores conectados mediante este inicio de sesión tendrán todos los derechos en todas las instancias. Este inicio de sesión no tendrá una contraseña en el caso de una nueva instalación. Debe definir manualmente esta contraseña.

Utilice el siguiente comando:

```
nlserver config -internalpassword
```

A continuación se muestra la siguiente información. Introduzca y confirme la contraseña:

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

* **`config-<instance>.xml`** (donde **instancia** es el nombre de la instancia): configuración específica de la instancia. Si comparte el servidor entre varias instancias, introduzca los parámetros específicos de cada instancia en el archivo correspondiente.
* **serverConf.xml**: configuración general para todas las instancias. Este archivo combina los parámetros técnicos del servidor de Adobe Campaign: todas las instancias las comparten. La descripción de algunos de estos parámetros se detalla a continuación. Consulte el propio archivo para ver todos los parámetros disponibles. Los diferentes nodos y parámetros que se enumeran en esta [sección](../../installation/using/the-server-configuration-file.md).

Puede configurar el directorio de almacenamiento (**var** directory) de los datos de Adobe Campaign (registros, descargas, redirecciones, etc.). Para ello, utilice la variable de sistema **XTK_VAR_DIR** :

* En Windows, indique el siguiente valor en la variable de sistema **XTK_VAR_DIR** .

   ```
   D:\log\AdobeCampaign
   ```

* En Linux, vaya al archivo **customer.sh** e indique: **exporte XTK_VAR_DIR=/app/log/AdobeCampaign**.

   For more on this, refer to [Personalizing parameters](../../installation/using/installing-packages-with-linux.md#personalizing-parameters).

## Habilitar procesos {#enabling-processes}

Los procesos de Adobe Campaign en el servidor están activados (y desactivados) mediante los **archivos config-default.xml** y **`config-<instance>.xml`** .

Para aplicar los cambios a estos archivos, si se inicia el servicio Adobe Campaign, debe ejecutar el comando **nlserver config -reload** .

Existen dos tipos de procesos: instancia múltiple y instancia única.

* **varias instancias**: se inicia un solo proceso para todas las instancias. Este es el caso de los procesos **web**, **syslogd** y **trackinglogd** .

   La habilitación se puede configurar desde el archivo **config-default.xml** .

   Declaración de un servidor de Adobe Campaign para acceder a las consolas de cliente y para redirección (seguimiento):

   ```
   vi nl6/conf/config-default.xml
   <web args="-tomcat" autoStart="true"/>  
   <!-- to start if the machine is also a redirection server -->  
   <trackinglogd autoStart="true"/>
   ```

   En este ejemplo, el archivo se edita mediante un comando **vi** en Linux. Se puede editar con cualquier editor **.txt** o **.xml** .

* **instancia** mono: se inicia un proceso para cada instancia (módulos: **mta**, **wfserver**, **inMail**, **sms** y **stat**).

   La habilitación se puede configurar mediante el archivo de configuración de la instancia:

   ```
   config-<instance>.xml
   ```

   Declaración de un servidor para su envío, ejecución de instancias de flujo de trabajo y recuperación de correo de devolución:

   ```
   <mta autoStart="true" statServerAddress="localhost"/>
   <wfserver autoStart="true"/>  
   <inMail autoStart="true"/>
   <stat autoStart="true"/>
   ```

## Configuración de envío {#delivery-settings}

Los parámetros de entrega deben configurarse en la carpeta **serverConf.xml** .

* **Configuración** DNS: especifique el dominio de entrega y las direcciones IP (o host) de los servidores DNS utilizados para responder a las consultas DNS de tipo MX realizadas por el módulo MTA a partir de **`<dnsconfig>`** entonces.

   >[!NOTE]
   >
   >El parámetro **nameServers** es esencial para una instalación en Windows. Para una instalación en Linux, debe quedar vacía.

   ```
   <dnsConfig localDomain="domain.com" nameServers="192.0.0.1,192.0.0.2"/>
   ```

Los demás parámetros de entrega disponibles en este archivo se presentan en [Personalización de los parámetros](../../installation/using/configuring-campaign-server.md#personalizing-delivery-parameters)de entrega.

Consulte también la posibilidad de entrega por [correo electrónico](../../installation/using/email-deliverability.md).
