---
product: campaign
title: Migración de una plataforma Linux a Adobe Campaign v7
description: Descubra cómo migrar una plataforma Linux a Adobe Campaign v7
feature: Upgrade
badge-v7-only: label="v7" type="Informative" tooltip="Solo se aplica a Campaign Classic v7"
audience: migration
content-type: reference
topic-tags: migrating-to-adobe-campaign-7
hide: true
hidefromtoc: true
exl-id: 9dc0699c-0fbf-4f8e-81f7-8ca3d7e98798
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: tm+mt
source-wordcount: '500'
ht-degree: 0%

---

# Migración de una plataforma Linux a Campaign v7{#migrating-in-linux-for-adobe-campaign-v}



Los pasos de migración en Linux son los siguientes:

1. Detener todos los servicios: [Más información](#service-stop).
1. Guardar la base de datos - [Más información](#back-up-the-database).
1. Desinstalar paquetes de versiones anteriores de Adobe Campaign: [Más información](#uninstalling-adobe-campaign-previous-version-packages).
1. Migración de la plataforma: [Más información](#deploying-adobe-campaign-v7).
1. Volver a iniciar el servicio - [Más información](#re-starting-services).

## Detención de servicio {#service-stop}

En primer lugar, detenga todos los procesos con acceso a la base de datos en todos los equipos correspondientes.

1. Iniciar sesión como **raíz**.
1. Todos los servidores que utilizan el módulo de redirección (**webmdl** service) se deben detener. Para Apache, ejecute el siguiente comando:

   ```
   /etc/init.d/apache2 stop
   ```

1. Inicie sesión de nuevo como **raíz**.
1. Detenga los servicios de versiones anteriores de Adobe Campaign en todos los servidores.

   ```
   /etc/init.d/nlserver6 stop
   ```

<!--
   If you are migrating from v5.11, run the following command:

   ```
   /etc/init.d/nlserver5 stop
   ```

-->

1. Asegúrese de que los servicios de Adobe Campaign estén detenidos en cada servidor.

   ```
   ps waux | grep nlserver
   ```

   La lista de los procesos activos se muestra junto con su ID (PID).

1. Si uno o más procesos de Adobe Campaign siguen activos o bloqueados después de unos minutos, elimínelos.

   ```
   killall nlserver
   ```

1. Si algunos procesos siguen activos después de unos minutos, puede forzarlos a cerrarse con el comando:

   ```
   killall -9 nlserver
   ```

## Realizar una copia de seguridad de la base de datos {#back-up-the-database}

<!--

### For Adobe Campaign v5.11 {#migrating-from-adobe-campaign-v5-11}

1. Make a backup of the Adobe Campaign database. 
1. Log in as **neolane** and make a backup of the **nl5** directory using the following command:

   ```
   su - neolane
   mv nl5 nl5.back
   ```

   >[!IMPORTANT]
   >
   >As a precaution, we recommend that you zip the **nl5.back** folder and save it to a secure location other than the server.

1. Edit the **config-`<instance name>`.xml** (in the **nl5.back** folder), to prevent the **mta**, **wfserver**, **stat** etc. services from starting automatically. For instance, replace **autoStart** with **_autoStart** (still as **neolane**).

   ```
   <?xml version='1.0'?>
   <serverconf>
     <shared>
       <dataStore hosts="myServer*" lang="en_US">
         <dataSource name="default">
           <dbcnx encrypted="1" login="myLogin" password="myPassword"  provider="postgresql" server="myServer"/>
         </dataSource>
       </dataStore>
     </shared>
   
     <mta _autoStart="true" statServerAddress="myStatServer"/>
     <stat _autoStart="true"/>
     <wfserver _autoStart="true"/>
     <inMail _autoStart="true"/>
     <sms _autoStart="false"/>
   </serverconf>
   ```

-->

<!--

### For Adobe Campaign v6.02 {#migrating-from-adobe-campaign-v6-02}

1. Make a backup of the Adobe Campaign database. 
1. Log in as **neolane** and make a backup of the **nl6** directory using the following command:

   ```
   su - neolane
   mv nl6 nl6.back
   ```

   >[!IMPORTANT]
   >
   >As a precaution, we recommend that you zip the **nl6.back** folder and save it to a secure location other than the server.

1. Edit the **config-`<instance name>`.xml** (in the **nl6.back** folder) to prevent the **mta**, **wfserver**, **stat**, etc. services from starting automatically. For instance, replace **autoStart** with **_autoStart** (still as **Adobe Campaign**).

   ```
   <?xml version='1.0'?>
   <serverconf>
     <shared>
       <dataStore hosts="myServer*" lang="en_US">
         <dataSource name="default">
           <dbcnx encrypted="1" login="myLogin" password="myPassword"  provider="postgresql" server="myServer"/>
         </dataSource>
       </dataStore>
     </shared>
   
     <mta _autoStart="true" statServerAddress="myStatServer"/>
     <stat _autoStart="true"/>
     <wfserver _autoStart="true"/>
     <inMail _autoStart="true"/>
     <sms _autoStart="false"/>
   </serverconf>
   ```

-->

1. Realice una copia de seguridad de la base de datos de Adobe Campaign.
1. Iniciar sesión como **neolano** y realice una copia de seguridad del **nl6** mediante el siguiente comando:

   ```
   su - neolane
   mv nl6 nl6.back
   ```

   >[!IMPORTANT]
   >
   >Como medida de precaución, le recomendamos que comprima el **nl6.back** y guárdelo en una ubicación segura que no sea el servidor.

## Desinstalar paquetes de versiones anteriores de Adobe Campaign {#uninstalling-adobe-campaign-previous-version-packages}

<!--

### For v5 packages {#uninstalling-adobe-campaign-v5-packages}

1. Log in as **root**.
1. Identify the Adobe Campaign packages installed using the following command.

    * In **Debian**:

      ```    
      dpkg -l | grep nl
      ```    
    
      The list of installed packages is displayed:

      ```    
      ii  nlserver5                       5762                     nlserver5-5762
      ii  nlthirdparty5                   5660                     nlthirdparty5-5660
      ```

    * In **Red Hat**:

      ```    
      rpm -qa | grep nl
      ```

1. Uninstall Adobe Campaign v5 packages.

    * In **Debian**:

      ```    
      dpkg --purge nlserver5 nlthirdparty5
      ```

    * In **Red Hat**:

      ```    
      rprm -ev nlserver5 nlthirdparty5
      ```

-->

Esta sección muestra cómo desinstalar paquetes de Adobe Campaign v6.1.

1. Iniciar sesión como **raíz**.
1. Identifique los paquetes de Adobe Campaign instalados con el siguiente comando.

   * Entrada **Debian**:

     ```
     dpkg -l | grep nl
     ```

     Se muestra la lista de paquetes instalados:

     ```
     ii  nlserver6                       XXXX                     nlserver6-XXXX
     ii  nlthirdparty6                   XXXX                     nlthirdparty6-XXXX
     ```

   * Entrada **Red Hat**:

     ```
     rpm -qa | grep nl
     ```

1. Desinstale los paquetes de Adobe Campaign v6.

   * Entrada **Debian**:

     ```
     dpkg --purge nlserver6 nlthirdparty6
     ```

   * Entrada **Red Hat**:

     ```
     rprm -ev nlserver6 nlthirdparty6
     ```

## Implementación de Adobe Campaign v7 {#deploying-adobe-campaign-v7}

Este es el procedimiento para implementar v7.

<!--

### From Adobe Campaign v5.11 {#migrating-from-adobe-campaign-v5_11-1}

Deploying Adobe Campaign involves two stages:

* Installing Adobe Campaign v7 packages: this operation must be performed on each server.
* The post upgrade: this command must be started on each instance.

To deploy Adobe Campaign, apply the following steps:

1. Install the most recent Adobe Campaign v7 packages using the following command:

    * In **Debian**:

      ```    
      dpkg -i nlserver6-XXXX-linux-2.6-intel.deb
      ```

    * In **Red Hat**:

      ```    
      rpm -Uvh nlserver6-XXXX-0.x86_64.rpm
      ```

   >[!IMPORTANT]
   >
   >You must install the packages successfully before going on to the next step.

   >[!NOTE]
   >
   >When migrating from v5.11, Adobe Campaign is installed in the **/usr/local/neolane/nl6/** directory by default.
   >
   >Once the packages are installed, the following message is displayed: **'WdbcTimeZone' option is missing**. This is normal.

1. To make the client console installation program available, copy it into the Adobe Campaign installation directory:

   ```
   cp setup-client-7.0.XXXX.exe /usr/local/neolane/nl6/datakit/nl/eng/jsp
   ```

   >[!NOTE]
   >
   >For more on how to install Adobe Campaign in Linux, refer to [this section](../../installation/using/installing-campaign-standard-packages.md).

1. Modify the **.bashrd** file which matches the **neolane** user. Log on as **neolane** and run the following command:

   ```
   su - neolane
   vim ~/.bashrc
   ```

   >[!NOTE]
   >
   >When you log in as **neolane**, the following message is displayed: **nl5/env.sh : No such file or directory**. This is normal.

   At the end of the file, replace **nl5/env.sh** with **nl6/env.sh**.

1. Log in as **root** and prepare the instance using the following commands:

   ```
   /etc/init.d/nlserver6 start   
   Starting nlserver6: [  OK  ]
   ```

   ```
   /etc/init.d/nlserver6 stop
   Stopping nlserver6: [  OK  ]
   ```

   >[!NOTE]
   >
   >These commands let you create the Adobe Campaign v6 internal files system: **conf** directory (with the **config-default.xml** and **serverConf.xml** files), **var** directory.

1. Go to the **nl5.back** backup folder and copy (overwrite) the configuration files and sub-folders of each instance. Log in as **neolane** and run the following command:

   >[!IMPORTANT]
   >
   >For the first command below, do not copy the **config-default.xml** file.

   ```
   su - neolane
   
   cp nl5.back/conf/config-<instance name>.xml nl6/conf/
   cp nl5.back/customer.sh nl6/
   cp -r nl5.back/customers/* nl6/customers/
   cp -r nl5.back/var/* nl6/var/
   ```

1. In the Adobe Campaign v7 **serverConf.xml** and **config-default.xml** files, apply the specific configurations that you had for Adobe Campaign v5. For the **serverConf.xml** file, use the **nl5/conf/serverConf.xml.diff** file.

   >[!NOTE]
   >
   >When reporting configurations from Adobe Campaign v5 to Adobe Campaign v7, make sure the paths to the physical directories lead to Adobe Campaign v7 and not Adobe Campaign v5.

1. Since migration is not a generic installation, you need to force the re-starting of the **trackinglogd** service. To do this, open the **nl6/conf/config-default.xml** file and make sure the **trackinglogd** service is activated (only on the tracking/redirection server(s)):

   ```
   <trackinglogd autoStart="true"/>
   ```

   >[!IMPORTANT]
   >
   >If the **trackinglogd** service is not started on the tracking server, no tracking information will be forwarded.

1. Reload the Adobe Campaign v7 configuration using the following command:

   ```
   nlserver config -reload
   ```

1. Start the postupgrade process using the following command (still as **neolane**):

   ```
   su - neolane
   nlserver config -timezone:<time zone> -postupgrade -instance:<instance name>
   ```

   >[!IMPORTANT]
   >
   >You must specify which timezone to use as a reference during the postupgrade (using the **-timezone** option). In this case, we are using the Europe/Paris timezone **-timezone: "Europe/Paris"**.

   >[!NOTE]
   >
   >We strongly recommend upgrading your base to "multi timezone". For further information about timezone options, refer to the [Time zones](../../migration/using/general-configurations.md#time-zones) section.

>[!IMPORTANT]
>
>Do not start Adobe Campaign services yet: changes still need to be made in Apache.

### From Adobe Campaign v6.02 {#migrating-from-adobe-campaign-v6_02-1}

Deploying Adobe Campaign involves two stages:

* Installing Adobe Campaign v7 packages: this operation must be performed on each server.
* The post upgrade: this command must be started on each instance.

To deploy Adobe Campaign, apply the following steps:

1. Install the most recent Adobe Campaign v7 packages using the following command:

    * In **Debian**:

      ```    
      dpkg -i nlserver6-XXXX-amd64_debX.deb
      ```

    * In **Red Hat**:

      ```    
      rpm -Uvh nlserver6-XXXX-x86_64_rhX.rpm
      ```

   >[!IMPORTANT]
   >
   >You must install the packages successfully before going on to the next step.

   >[!NOTE]
   >
   >Adobe Campaign v7 is installed in the same directory by default as Adobe Campaign v6.02: **/usr/local/neolane/nl6/**.

1. To make the client console installation program available, copy it into the Adobe Campaign installation directory:

   ```
   cp setup-client-7.0.XXXX.exe /usr/local/neolane/nl6/datakit/nl/eng/jsp
   ```

   >[!NOTE]
   >
   >For more on how to install Adobe Campaign in Linux, refer to [this section](../../installation/using/installing-campaign-standard-packages.md).

1. Since migration is not a generic installation, you need to force the re-starting of the **trackinglogd** service. To do this, open the **nl6/conf/config-default.xml** file and make sure the **trackinglogd** service is activated (only on the tracking/redirection server(s)):

   ```
   <trackinglogd autoStart="true"/>
   ```

   >[!IMPORTANT]
   >
   >If the **trackinglogd** service is not started on the tracking server, no tracking information will be forwarded.

1. Go to the **nl6.back** backup folder and copy (overwrite) the configuration files and sub-folders of each instance. Log in as **neolane** and run the following command:

   ```
   su - neolane
   
   cp nl6.back/conf/config*.xml nl6/conf/
   cp nl6.back/customer.sh nl6/
   cp -r nl6.back/customers/* nl6/customers/
   cp -r nl6.back/var/* nl6/var/
   ```

1. Reload the Adobe Campaign v7 configuration using the following command:

   ```
   nlserver config -reload
   ```

1. Start the postupgrade process using the following command (still as **neolane**):

   ```
   su - neolane
   nlserver config -postupgrade -instance:<instance name>
   ```

   >[!NOTE]
   >
   >The "multi timezone" mode was only available in v6.02 for PostgreSQL database engines. It is now available no matter what version of database engine is being used. We strongly recommend upgrading your base to "multi timezone". For further information about timezone options, refer to the [Time zones](../../migration/using/general-configurations.md#time-zones) section.

-->

La implementación de Adobe Campaign consta de dos fases:

* Instalación de paquetes de Adobe Campaign v7: esta operación debe realizarse en cada servidor.
* Después de la actualización: este comando debe iniciarse en cada instancia.

Para implementar Adobe Campaign, siga los siguientes pasos:

1. Instale los paquetes más recientes de Adobe Campaign v7 con el siguiente comando:

   * Entrada **Debian**:

     ```
     dpkg -i nlserver6-XXXX-amd64_debX.deb
     ```

   * Entrada **Red Hat**:

     ```
     rpm -Uvh nlserver6-XXXX-x86_64_rhX.rpm
     ```

   >[!IMPORTANT]
   >
   >Debe instalar correctamente los paquetes antes de pasar al siguiente paso.

   >[!NOTE]
   >
   >Adobe Campaign v7 está instalado en **/usr/local/neolane/nl6/** de forma predeterminada.

1. Para que el programa de instalación de la consola del cliente esté disponible, cópielo en el directorio de instalación de Adobe Campaign:

   ```
   cp setup-client-7.0.XXXX.exe /usr/local/neolane/nl6/datakit/nl/eng/jsp
   ```

   >[!NOTE]
   >
   >Para obtener más información sobre cómo instalar Adobe Campaign en Linux, consulte [esta sección](../../installation/using/installing-campaign-standard-packages.md).

1. Vaya a la **nl6.back** haga una copia de seguridad de la carpeta y copie (sobrescriba) los archivos de configuración y las subcarpetas de cada instancia. Iniciar sesión como **neolano** y ejecute el siguiente comando:

   ```
   su - neolane
   
   cp nl6.back/conf/config*.xml nl6/conf/
   cp nl6.back/customer.sh nl6/
   cp -r nl6.back/customers/* nl6/customers/
   cp -r nl6.back/var/* nl6/var/
   ```

1. Vuelva a cargar la configuración de Adobe Campaign v7 con el siguiente comando:

   ```
   nlserver config -reload
   ```

1. Inicie el proceso posterior a la actualización mediante el siguiente comando (sin modificar como **neolano**):

   ```
   su - neolane
   nlserver config -postupgrade -instance:<instance name>
   ```

<!--

## Migrate the redirection server (Apache) {#migrating-the-redirection-server--apache-}

>[!NOTE]
>
>This section only applies when migrating from Adobe Campaign v5.11.

At this stage, Apache needs to be stopped. Refer to: [Service stop](#service-stop).

1. Log in as **root**.
1. Change the Apache environment variables to make them link to the **nl6** directory.

    * In **Debian**:

      ```    
      vi /etc/apache2/envvars
      ```

    * In **Red Hat**:

      ```    
      vi /usr/local/apache2/bin/envvars
      ```

1. Then run the following commands:

    * In **Debian**:

      In the **nlsrv.load** file, replace **nl5** with **nl6**.

      ```    
      vi /etc/apache2/mods-available/nlsrv.load
      ```    
    
      Delete the link of the **nlsrv.conf** file and create a new one.

      ```    
      rm /etc/apache2/mods-available/nlsrv.conf 
      ln -s /usr/local/neolane/nl6/tomcat-6/conf/apache_neolane.conf /etc/apache2/
      mods-available/nlsrv.conf
      ```

    * In **Red Hat**:

      Go to the **/usr/local/apache2/conf** directory, edit the **http.conf** file and replace **nl5** with **nl6** in the following lines.

      In **RHEL 7/Debian 8**:

      ```    
      LoadModule requesthandler24_module /usr/local/neolane/nl6/lib/libnlsrvmod.so
      Include /usr/local/neolane/nl6/tomcat-6/conf/apache_neolane.conf
      ```

1. Go to the **alias.conf** file and replace all **nl5** with **nl6**. To do this in Debian, run the following command:

   ```
   vi /etc/apache2/mods-available/alias.conf
   ```

-->

<!--

## Security zones {#security-zones}

If you are migrating from v6.02 or earlier, you must configure your security zones before starting services. For more information, refer to [Security](../../migration/using/general-configurations.md#security).

-->

## Volver a iniciar servicios {#re-starting-services}

Este es el procedimiento para reiniciar los servicios.

<!--

### For Adobe Campaign v5 {#migrating-from-adobe-campaign-v5_11-2}

In the **config-`<instance name>`.xml** files, reactivate the automatic startup of the **mta**, **wfserver**, **stat**, etc. services.

```
<?xml version='1.0'?>
<serverconf>
  <shared>
    <dataStore hosts="myServer*" lang="en_US">
      <dataSource name="default">
        <dbcnx encrypted="1" login="myLogin" password="myPassword"  provider="postgresql" server="myServer"/>
      </dataSource>
    </dataStore>
  </shared>

  <mta autoStart="true" statServerAddress="localhost"/>
  <stat autoStart="true"/>
  <wfserver autoStart="true"/>
  <inMail autoStart="true"/>
  <sms autoStart="false"/>
</serverconf>
```

Start Apache and Adobe Campaign services on each of the following servers:

1. Tracking and redirection server.
1. Mid-sourcing server.
1. Marketing server.

Before going on to the next step, run a full test of the new installation, make sure there are no regressions and that everything works by following all the recommendations in the [General configurations](../../migration/using/general-configurations.md) section.

### For Adobe Campaign v6.02 {#migrating-from-adobe-campaign-v6_02-2}

In the **config-`<instance name>`.xml** files, reactivate the automatic startup of the **mta**, **wfserver**, **stat**, etc. services.

```
<?xml version='1.0'?>
<serverconf>
  <shared>
    <dataStore hosts="myServer*" lang="en_US">
      <dataSource name="default">
        <dbcnx encrypted="1" login="myLogin" password="myPassword"  provider="postgresql" server="myServer"/>
      </dataSource>
    </dataStore>
  </shared>

  <mta autoStart="true" statServerAddress="myStatServer"/>
  <stat autoStart="true"/>
  <wfserver autoStart="true"/>
  <inMail autoStart="true"/>
  <sms autoStart="false"/>
</serverconf>
```

Start Apache and Adobe Campaign services on each of the following servers:

1. Tracking and redirection server.
1. Mid-sourcing server.
1. Marketing server.

Fully test the new installation, check that it does not regress and make sure that everything is working correctly by following all the recommendations in the [General configurations](../../migration/using/general-configurations.md) section.

-->

Inicie los servicios de Apache y Adobe Campaign en cada uno de los siguientes servidores:

1. Servidor de seguimiento y redirección.
1. Servidor intermediario.
1. Servidor de marketing.

Pruebe completamente la nueva instalación, compruebe que no vuelve a funcionar y asegúrese de que todo funciona correctamente.

<!--

## Delete the Adobe Campaign previous version {#deleting-and-cleansing-adobe-campaign-v5}

>[!NOTE]
>
>This section only applies when migrating from Adobe Campaign v5.11.

Before you delete and cleanse the Adobe Campaign v5 installation, you must apply the following recommendations:

* Get the functional teams to run a full check of the new installation.
* Only uninstall Adobe Campaign v5 once you are certain that no rollback is necessary.

Delete the **nl5.back** directory. Log in as **neolane** and run the following command:

```
su - neolane
rm -rf nl5.back
```

Re-start the server.

-->
