---
solution: Campaign Classic
product: campaign
title: Instalación del servidor
description: Instalación del servidor
audience: installation
content-type: reference
topic-tags: installing-campaign-in-windows-
exl-id: c0cb4efa-cae9-4312-88fb-738857a89595
translation-type: tm+mt
source-git-commit: b0a1e0596e985998f1a1d02236f9359d0482624f
workflow-type: tm+mt
source-wordcount: '402'
ht-degree: 3%

---

# Instalación del servidor{#installing-the-server}

## Ejecución del programa de instalación {#executing-the-installation-program}

Para una plataforma de Windows de 32 bits, instale Adobe Campaign de 32 bits. Para una plataforma Windows de 64 bits, instale Adobe Campaign de 64 bits.

Los pasos de instalación del servidor Adobe Campaign son los siguientes:

1. Ejecute el archivo **setup.exe**.

   ![](assets/s_ncs_install_installer_01.png)

1. Seleccione el tipo de instalación.

   ![](assets/s_ncs_install_installer_01a.png)

   Hay varios tipos de instalación disponibles:

   * **[!UICONTROL Installation of an application server]** : Instale el servidor de aplicaciones de Adobe Campaign y la consola del cliente.
   * **[!UICONTROL Minimal installation (Network)]** : Instalación del equipo cliente desde la red. Sólo se instalará un número limitado de DLL en el equipo, si es necesario, y todos los demás componentes se utilizarán desde una unidad de red.
   * **[!UICONTROL Installation of a client]** : Instalación de los componentes necesarios para el cliente de Adobe Campaign.
   * **[!UICONTROL Custom installation]** : El usuario elige los elementos que desea instalar.

   Seleccione **Instalación de un servidor de aplicaciones** y siga los diferentes pasos como se muestra a continuación:

   ![](assets/s_ncs_install_installer_02.png)

1. Seleccione el directorio de instalación:

   ![](assets/s_ncs_install_installer_03.png)

1. Haga clic en **[!UICONTROL Finish]** para iniciar la instalación:

   ![](assets/s_ncs_install_installer_04.png)

   La barra de progreso muestra hasta dónde se encuentra la instalación:

   ![](assets/s_ncs_install_installer_05.png)

   Una vez completada la instalación, aparece un mensaje que le informa:

   ![](assets/s_ncs_install_installer_06.png)

   >[!NOTE]
   >
   >Una vez finalizada la instalación del servidor, es necesario reiniciar el servidor para evitar posibles problemas de red.

   Una vez finalizada la instalación, inicie Adobe Campaign para crear los archivos de configuración. Consulte [Primer inicio del servidor](#first-start-up-of-the-server).

## Prueba de instalación de resumen {#summary-installation-testing}

Puede probar la instalación inicial utilizando el siguiente comando:

```
nlserver pdump
```

Si Adobe Campaign no se inicia, la respuesta es:

```
No task
```

## Primer inicio del servidor {#first-start-up-of-the-server}

Una vez finalizada la prueba de instalación, abra un símbolo del sistema a través del menú **[!UICONTROL Start > Programs > Adobe Campaign]** e introduzca el siguiente comando:

```
nlserver web
```

![](assets/s_ncs_install_cmd_nlserverweb.png)

Los archivos del directorio de instalación se utilizan para configurar los módulos de servidor de Adobe Campaign.

Se muestra la siguiente información:

```
15:30:12 >   Application server for Adobe Campaign Classic (7.X YY.R build XXX@SHA1) of DD/MM/YYYY
15:30:12 >   Web server start (pid=664, tid=4188)...
15:30:12 >   Creation of server configuration file '[INSTALL]bin..confserverConf.xml' server via '[INSTALL]bin..conffraserverConf.xml.sample
15:30:12 >   Creation of server configuration file '[INSTALL]bin..confconfig-default.xml' server via '[INSTALL]bin..confmodelsconfig-default.xml
15:30:12 >   Server started
15:30:12 >   Stop requested (pid=664)
15:30:12 >   Web server stop (pid=664, tid=4188)...
```

Pulse **Ctrl+C** para detener el proceso e introduzca el siguiente comando:

```
nlserver start web
```

Se muestra la siguiente información:

```
12:17:21 >   Application server for Adobe Campaign Classic (7.X YY.R build XXX@SHA1) of DD/MM/YYYY
12:17:21 >   Start of the 'web@default' ('nlserver web -tracefile:web@default -instance:default -detach -tomcat -autorepair') task in a new process 
12:17:21 >   Application server for Adobe Campaign Classic (7.X YY.R build XXX@SHA1) of DD/MM/YYYY
12:17:21 >   Web server start (pid=29188, tid=-1224824320)...
12:17:21 >   Generation of configuration changes '[INSTALL]bin..confserverConf.xml.diff' between '[INSTALL]bin..confserverConf.xml' and '[INSTALL]bin..conffraserverConf.xml.sample'
12:17:22 >   Tomcat started
12:17:22 >   Server started
```

Para detenerlo, introduzca:

```
nlserver stop web
```

Se muestra la siguiente información:

```
12:18:31 >   Application server for Adobe Campaign Classic (7.X YY.R build XXX@SHA1) of DD/MM/YYYY
12:18:31 >   Stop requested for 'web@default' ('nlserver web -tracefile:web@default -instance:default -detach -tomcat -autorepair', pid=29188, tid=-1224824320)...
12:18:31 >   Stop requested (pid=29188)
12:18:31 >   Web server stopped (pid=29188, tid=-1224824320)...
```

## Contraseña del identificador interno {#password-for-the-internal-identifier}

El servidor de Adobe Campaign define un inicio de sesión técnico llamado **internal** que tiene todos los derechos en todas las instancias. Justo después de la instalación, el inicio de sesión no tiene contraseña. Es obligatorio definir una.

Obtenga más información en [esta sección](../../installation/using/configuring-campaign-server.md#internal-identifier).

## Inicio de los servicios de Adobe Campaign {#starting-adobe-campaign-services}

Para iniciar los servicios de Adobe Campaign, puede utilizar el administrador de servicios o introducir lo siguiente en la línea de comandos (con los derechos adecuados):

```
net start nlserver6
```

Si necesita detener los procesos de Adobe Campaign más adelante, utilice el comando :

```
net stop nlserver6
```

## Instalación de LibreOffice {#installing-libreoffice}

Descargue LibreOffice, por ejemplo de [https://www.libreoffice.org/download/libreoffice-fresh/](https://www.libreoffice.org/download/libreoffice-fresh/) y siga los pasos de instalación habituales.

Agregue la siguiente variable de entorno:

```
OOO_BASIS_INSTALL_DIR="C:\Program Files (x86)\LibreOffice 6\"
```
