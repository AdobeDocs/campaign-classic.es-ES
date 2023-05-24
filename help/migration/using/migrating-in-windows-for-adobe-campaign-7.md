---
product: campaign
title: Migración de una plataforma Microsoft Windows a Adobe Campaign v7
description: Obtenga información sobre cómo migrar una plataforma de Microsoft Windows a Adobe Campaign v7
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
audience: migration
content-type: reference
topic-tags: migrating-to-adobe-campaign-7
hide: true
hidefromtoc: true
exl-id: 3743d018-3316-4ce3-ae1c-25760aaf5785
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: tm+mt
source-wordcount: '1092'
ht-degree: 0%

---

# Migración de una plataforma Microsoft Windows a Campaign v7{#migrating-in-windows-for-adobe-campaign}



Para un entorno Microsoft Windows, los pasos de migración son los siguientes:

1. Detener todos los servicios: [Más información](#service-stop).
1. Realizar copia de seguridad de la base de datos: [Más información](#back-up-the-database).
1. Migración de la plataforma: [Más información](#deploying-adobe-campaign-v7).
1. Migración del servidor de redirección (IIS): [Más información](#migrating-the-redirection-server--iis-).
1. Volver a iniciar el servicio - [Más información](#re-starting-the-services).
1. Eliminar y limpiar la versión anterior de Adobe Campaign: [Más información](#deleting-and-cleansing-adobe-campaign-previous-version).

## Detención de servicio {#service-stop}

En primer lugar, detenga todos los procesos con acceso a la base de datos en todos los equipos correspondientes.

1. Todos los servidores que utilizan el módulo de redirección (**webmdl** service) se debe detener. Para IIS, ejecute el siguiente comando:

   ```
   iisreset /stop
   ```

1. El **mta** y sus módulos secundarios (**mtachild**) debe detenerse utilizando los siguientes comandos:

   ```
   nlserver stop mta@<instance name>
   nlserver stop mtachild@<instance name>
   ```

1. Detenga los servicios de Adobe Campaign en todos los servidores. Inicie sesión con derechos de administrador y ejecute el siguiente comando:

   ```
   net stop nlserver6
   ```

<!--

   If you are migrating from v5.11, run the following command:

   ```
   net stop nlserver5
   ```

-->

1. Para cada servidor, asegúrese de que los servicios de Adobe Campaign estén correctamente detenidos. Inicie sesión con derechos de administrador y ejecute el siguiente comando:

   ```
   tasklist /FI "IMAGENAME eq nlserver*"
   ```

   Se muestra la lista de procesos activos junto con su ID (PID).

   ```
   Image Name                     PID Session Name        Session#    Mem Usage
   ========================= ======== ================ =========== ============
   nlserver.exe                  3192 Console                    1     13,108 K
   ```

1. Si uno o más procesos de Adobe Campaign siguen activos o bloqueados después de unos minutos, elimínelos. Inicie sesión con derechos de administrador y ejecute el siguiente comando:

   ```
   taskkill /IM nlserver* /T
   ```

1. Si algunos procesos siguen activos después de unos minutos, puede forzarlos a cerrarse con el comando:

   ```
   taskkill /F /IM nlserver* /T
   ```

## Copia de seguridad de la base de datos de Campaign {#back-up-the-database}

Este es el procedimiento para realizar una copia de seguridad de Adobe Campaign v6.1.

<!--

### For Adobe Campaign v5.11 {#migrating-from-adobe-campaign-v5-11}

1. Make a backup of the Adobe Campaign database.
1. Make a backup of the **Neolane v5** directory using the following command:

   ```
   ren "Neolane v5" "Neolane v5.back"
   ```

   >[!IMPORTANT]
   >
   >As a precaution, we recommend that you zip the **Neolane v5.back** folder and save it elsewhere in a safe location other than the server.

1. In the windows service management console, disable the automatic startup of the 5.11 application server service. You can also use the following command:

   ```
   sc config nlserver5 start= disabled
   ```

1. Edit the **config-`<instance name>`.xml** (in the **Neolane v5. back** folder) to prevent the **mta**, **wfserver**, **stat**, etc. services from starting automatically. For instance, replace **autoStart** with **_autoStart**.

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
1. Make a backup of the **Neolane v6** directory using the following command:

   ```
   ren "Neolane v6" "Neolane v6.back"
   ```

   >[!IMPORTANT]
   >
   >As a precaution, we recommend that you zip the **Neolane v6.back** folder and save it elsewhere in a safe location other than the server.

1. In the Windows service manager, deactivate the 6.02 application server automatic startup. You can also use the following command:

   ```
   sc config nlserver6 start= disabled
   ```

1. Edit the **config-`<instance name>`.xml** (in the **Neolane v6. back** folder) to prevent the **mta**, **wfserver**, **stat**, etc. services from starting automatically. For instance, replace **autoStart** with **_autoStart**.

   ```
   <?xml version='1.0'?>
   <serverconf>
     <shared>
       <dataStore hosts="myServer*" lang="en_US">
         <dataSource name="default">
           <dbcnx encrypted="1" login="myLogin" password="myPassword" provider="postgresql" server="myServer"/>
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
1. Realice una copia de seguridad del **Adobe Campaign v6** mediante el siguiente comando:

   ```
   ren "Adobe Campaign v6" "Adobe Campaign v6.back"
   ```

   >[!IMPORTANT]
   >
   >Como medida de precaución, le recomendamos que comprima el **Adobe Campaign v6.back** y guárdelo en otra ubicación segura que no sea el servidor.

1. En la consola de administración de servicios de Windows, deshabilite el inicio automático del servicio del servidor de aplicaciones 6.11. También puede utilizar el siguiente comando:

   ```
   sc config nlserver6 start= disabled
   ```

## Implementación de Adobe Campaign v7 {#deploying-adobe-campaign-v7}

La implementación de Adobe Campaign consta de dos fases:

* Instalación de la versión 7: esta operación debe realizarse en cada servidor.
* Después de la actualización: este comando debe iniciarse en cada instancia.

Para implementar Adobe Campaign, siga los siguientes pasos:

1. Instale la última versión de Adobe Campaign v7 ejecutando la **setup.exe** archivo de instalación. Para obtener más información sobre la instalación del servidor de Adobe Campaign en Windows, consulte [esta sección](../../installation/using/installing-the-server.md).

   ![](assets/migration_wizard_1_7.png)

   >[!NOTE]
   >
   >Adobe Campaign v7 se instala de forma predeterminada en **C:\Program Files\Adobe\Adobe Campaign v7** directorio.

1. Para que el programa de instalación de la consola del cliente esté disponible, copie el **setup-client-7.0.XXXX.exe** en el directorio de instalación de Adobe Campaign: **C:\Program Files\Adobe\Adobe Campaign v7\datakit\nl\eng\jsp**.

   >[!NOTE]
   >
   >Para obtener más información sobre la instalación de Adobe Campaign en Windows, consulte [esta sección](../../installation/using/installing-the-server.md).

1. Inicie la instancia por primera vez con los siguientes comandos:

   ```
   net start nlserver6-v7
   net stop nlserver6-v7
   ```

   >[!NOTE]
   >
   >Estos comandos permiten crear el sistema de archivos interno de Adobe Campaign v7: **conf** directorio (con el **config-default.xml** y **serverConf.xml** archivos), **var** directorio, etc.

1. Copie y pegue (sobrescriba) los archivos de configuración y subcarpetas de cada instancia a través de la variable **Neolane v5.back**, **Neolane v6.back** o **Adobe Campaign v6.back** archivo de copia de seguridad (en función de la versión desde la que migre - consulte [esta sección](#back-up-the-database-and-the-current-installation)).
1. Según la versión desde la que realice la migración, ejecute los siguientes comandos:

   ```
   copy "Neolane v5.back"/conf/config-<instance name>.xml "Adobe Campaign v7"/conf/
   copy "Neolane v5.back"/customers/* "Adobe Campaign v7"/customers/
   copy "Neolane v5.back"/var/* "Adobe Campaign v7"/var/
   ```

   ```
   copy "Neolane v6.back"/conf/config-<instance name>.xml "Adobe Campaign v7"/conf/
   copy "Neolane v6.back"/customers/* "Adobe Campaign v7"/customers/
   copy "Neolane v6.back"/var/* "Adobe Campaign v7"/var/
   ```

   ```
   copy "Adobe Campaign v6.back"/conf/config-<instance name>.xml "Adobe Campaign v7"/conf/
   copy "Adobe Campaign v6.back"/customers/* "Adobe Campaign v7"/customers/
   copy "Adobe Campaign v6.back"/var/* "Adobe Campaign v7"/var/
   ```

   >[!IMPORTANT]
   >
   >Para el primer comando anterior, no copie el **config-default.xml** archivo.

1. En el **serverConf.xml** y **config-default.xml** de Adobe Campaign v7, aplique las configuraciones específicas que tenía en la versión anterior de Adobe Campaign. Para el **serverConf.xml** , utilice el **Neolane v5/conf/serverConf.xml.diff**, **Neolane v6/conf/serverConf.xml.diff** o **Adobe Campaign v6/conf/serverConf.xml.diff** archivo.

   >[!NOTE]
   >
   >Al informar sobre configuraciones desde la versión anterior de Adobe Campaign a Adobe Campaign v7, asegúrese de que las rutas a los directorios físicos dirijan a Adobe Campaign v7 (y no a Neolane v5, Neolane v6 o Adobe Campaign v6).

1. Vuelva a cargar la configuración de Adobe Campaign v7 con el siguiente comando:

   ```
   nlserver config -reload
   ```

1. Inicie el proceso posterior a la actualización mediante el siguiente comando:

   ```
   nlserver config -postupgrade -instance:<instance name>
   ```

>[!IMPORTANT]
>
>No inicie aún los servicios de Adobe Campaign: es necesario realizar algunos cambios en IIS.

## Migración del servidor de redirección {#migrating-the-redirection-server--iis-}

En este momento, se debe detener el servidor IIS. Consulte [Detención de servicio](#service-stop).

1. Abra el **Administrador de Internet Information Services (IIS)** consola.
1. Cambie los enlaces (puertos de escucha) del sitio utilizado para la versión anterior de Adobe Campaign:

   * Haga clic con el botón derecho en el sitio utilizado para la versión anterior de Adobe Campaign y seleccione **[!UICONTROL Edit bindings]**.
   * Para cada tipo de puerto de escucha (**[!UICONTROL http]** y/o **[!UICONTROL https]**), seleccione la línea adecuada y haga clic en **[!UICONTROL Edit]**.
   * Introduzca un puerto diferente. De forma predeterminada, el puerto de escucha es 80 para http y 443 para https. Compruebe que el nuevo puerto esté disponible.

      ![](assets/_migration_iis_3_611.png)

      >[!NOTE]
      >
      >Si el servidor IIS incluye varios sitios web para Adobe Campaign con una configuración avanzada (puerto compartido y diferentes direcciones IP), póngase en contacto con el administrador.

1. Cree un nuevo sitio web para Adobe Campaign v7:

   * Haga clic con el botón derecho en **[!UICONTROL Sites]** carpeta y seleccione **[!UICONTROL Add Web Site...]**.

      ![](assets/_migration_iis_4.png)

   * Introduzca el nombre del sitio, **Adobe Campaign v7** por ejemplo.
   * La ruta de acceso al directorio básico del sitio web no se utiliza, pero la variable **[!UICONTROL Physical access path]** se debe introducir el campo. Escriba la ruta de acceso predeterminada de IIS: **C:\inetpub\wwwroot**.
   * Haga clic en **[!UICONTROL Connect as...]** como y asegúrese de que la variable **[!UICONTROL Application user]** La opción está seleccionada.
   * Puede dejar los valores predeterminados en **[!UICONTROL IP address]** y **[!UICONTROL Port]** campos. Si desea utilizar otros valores, asegúrese de que la dirección IP y/o el puerto estén disponibles.
   * Marque la casilla **[!UICONTROL Start Web site immediately]**.

      ![](assets/_migration_iis_5_7.png)

1. Ejecute el **iis_neolane_setup.vbs** para configurar automáticamente los recursos utilizados por el servidor de Adobe Campaign en el directorio virtual creado anteriormente.

   * Este archivo se encuentra en **`[Adobe Campaign v7]`\conf** directorio, donde **`[Adobe Campaign v7]`** es la ruta de acceso al directorio de instalación de Adobe Campaign. El comando para ejecutar la secuencia de comandos es el siguiente (para administradores):

      ```
      cd C:\Program Files (x86)\Adobe Campaign\Adobe Campaign v7\conf
      cscript iis_neolane_setup.vbs
      ```

   * Clic **[!UICONTROL OK]** para confirmar la ejecución del script.

      ![](assets/s_ncs_install_iis7_parameters_step2_7.png)

   * Introduzca el número del sitio web creado anteriormente para Adobe Campaign v7 y haga clic en **[!UICONTROL OK]**.

      ![](assets/s_ncs_install_iis7_parameters_step3_7.png)

   * Debe aparecer un mensaje de confirmación:

      ![](assets/s_ncs_install_iis7_parameters_step7_7.png)

   * En el **[!UICONTROL Content view]** , asegúrese de que la configuración del sitio web se configura correctamente con los recursos de Adobe Campaign:

      ![](assets/s_ncs_install_iis7_parameters_step6_7.png)

      >[!NOTE]
      >
      >Si no se muestra la estructura de árbol, reinicie IIS.
      >
      >Los siguientes pasos de configuración de IIS se detallan en [esta sección](../../installation/using/integration-into-a-web-server-for-windows.md#configuring-the-iis-web-server).

<!--
## Security zones {#security-zones}

If you are migrating from v6.02 or earlier, you must configure your security zones before starting services. [Learn more](../../migration/using/general-configurations.md#security)
-->

## Volver a iniciar servicios {#re-starting-the-services}

Inicie los servicios IIS y Adobe Campaign en cada uno de los siguientes servidores:

1. Servidor de seguimiento y redirección.
1. Servidor intermediario.
1. Servidor de marketing.

Antes de pasar al siguiente paso, realice una prueba completa de la nueva instalación, asegúrese de que no haya regresiones y de que todo funcione.

## Eliminar la versión anterior {#deleting-and-cleansing-adobe-campaign-previous-version}

Este es el procedimiento para eliminar Adobe Campaign v6.1.

<!--

### For Adobe Campaign v5 {#adobe-campaign-v5}

Before you delete and cleanse the Adobe Campaign v5 installation, you must apply the following recommendations:

* Get the functional teams to run a full check of the new installation.
* Only uninstall Adobe Campaign v5 once you are certain that no rollback is necessary.

1. In IIS, delete the **Neolane v5** website, then the **Neolane v5** application pool. 
1. Rename the **Neolane v5.back** folder as **Neolane v5**.
1. Uninstall Adobe Campaign v5 using the Add/remove components wizard. 

   ![](assets/migration_wizard_2.png)

1. Delete the **nlserver5** Windows service using the following command:

   ```
   sc delete nlserver5
   ```

1. Re-start the server.

### For Adobe Campaign v6.02 {#adobe-campaign-v6-02}

Before you delete and cleanse the Adobe Campaign v6.02 installation, you must apply the following recommendations:

* Get the functional teams to run a full check of the new installation.
* Only uninstall Adobe Campaign v6.02 once you are certain that no rollback is necessary.

1. In IIS, delete the **Neolane v6** website, then the **Neolane v6** application pool. 
1. Rename the **Neolane v6.back** folder as **Neolane v6**.
1. Uninstall Adobe Campaign v6.02 using the Add/remove components wizard. 

   ![](assets/migration_wizard_2.png)

1. Re-start the server.

-->

Antes de eliminar y limpiar la instalación de Adobe Campaign v6, debe aplicar las siguientes recomendaciones:

* Haga que los equipos funcionales realicen una comprobación completa de la nueva instalación.
* Desinstale Adobe Campaign v6 solo cuando esté seguro de que no es necesario realizar una reversión.

1. En IIS, elimine el **Adobe Campaign v6** sitio web y luego la **Adobe Campaign v6** grupo de aplicaciones.
1. Cambie el nombre del **Adobe Campaign v6.back** carpeta como **Adobe Campaign v6**.
1. Desinstale Adobe Campaign v6 mediante el asistente Agregar o quitar componentes.

   ![](assets/migration_wizard_2.png)

1. Reinicie el servidor.
