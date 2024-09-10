---
product: campaign
title: Configuración del acceso a  [!DNL Vertica Analytics]
description: Obtenga información sobre cómo configurar el acceso a  [!DNL Vertica Analytics] en FDA
feature: Installation, Federated Data Access
audience: platform
content-type: reference
topic-tags: connectors
exl-id: 8b2a9c73-807a-4936-9fd6-9d26c805a31f
source-git-commit: c262c27e75869ae2e4bd45642f5a22adec4a5f1e
workflow-type: tm+mt
source-wordcount: '355'
ht-degree: 24%

---

# Configurar el acceso a [!DNL Vertica Analytics] {#configure-fda-vertica}



Utilice la opción **Acceso de datos federado** (FDA) de Campaign para procesar la información almacenada en una base de datos externa. Siga los pasos a continuación para configurar el acceso a [!DNL Vertica Analytics].

1. Configurar [!DNL Vertica Analytics] en [CentOS](#vertica-centos), [Windows](#vertica-windows) o [Debian](#vertica-debian)
1. Configurar la [!DNL Vertica Analytics] [cuenta externa](#vertica-external) en Campaign

![](assets/snowflake_3.png)

## [!DNL Vertica Analytics] en CentOS {#vertica-centos}

Para configurar [!DNL Vertica Analytics] en CentOS, siga los pasos a continuación:

1. Descargue los controladores ODBC para [!DNL Vertica Analytics]. [Haga clic aquí](https://www.vertica.com/download/vertica/client-drivers/) y descargue el último RPM de Linux.

1. A continuación, debe instalar unixODBC con el siguiente comando:

   ```
   yum search unixODBC
   yum install unixODBC.x86_64
   ```

1. Si ya ha instalado el servidor [!DNL Vertica Analytics], ya se instalará un controlador ODBC. En este caso, actualice la unidad como se indica a continuación:

   ```
   #Switch to root
   sudo su
   
   #Install the package (add --force to update it)
   rpm -Uvh vertica-client-x.x.x-x.x86_64.rpm [--force]
   
   #Open odbcinst.ini
   vi /etc/odbcinst.ini
   
   #Add a section for Vertica Analytics and save
   [VerVertica Analyticstica]
   Description = Vertica Analytics ODBC Driver
   Driver = /opt/vertica/lib64/libverticaodbc.so
   
   #Open odbc.ini
   vi /etc/odbc.ini
   
   #Add your DSN in ODBC Data Sources section, for example:
   [ODBC Data Sources]
   VMart = "VMart database on Vertica Analytics"
   
   #Add a DSN definition section below, for example:
   [VMart]
   Description = Vmart Database
   Driver = Vertica Analytics
   Database = VMart
   Servername = # The name of the server where Vertica Analytics is installed. Use localhost if Vertica Analytics is installed on the same machine.
   UID = dbadmin
   PWD = <password>
   Port = 5433
   
   #Cleanup
   #Remove the ODBC package
   rm vertica-client-x.x.x-x.x86_64.rpm
   ```

1. En Adobe Campaign, puede configurar su cuenta externa [!DNL Vertica Analytics]. Para obtener más información sobre cómo configurar su cuenta externa, consulte [esta sección](#vertica-external).

## [!DNL Vertica Analytics] en Windows {#vertica-windows}

1. Descargue [el controlador ODBC para Windows](https://www.vertica.com/download/vertica/client-drivers/). Para instalar el controlador para Windows, deberá habilitar .NET Framework 3.5 o el asistente de instalación intentará habilitarlo y descargarlo automáticamente.

1. Configure el controlador ODBC en Windows. Para obtener más información, consulte [esta página](https://www.vertica.com/docs/9.2.x/HTML/Content/Authoring/ConnectingToVertica/ClientODBC/SettingUpADSN.htm)

1. En Adobe Campaign, puede configurar su cuenta externa [!DNL Vertica Analytics]. Para obtener más información sobre cómo configurar su cuenta externa, consulte [esta sección](#vertical-external).

## [!DNL Vertica Analytics] en Debian {#vertica-debian}

1. Descargue los controladores ODBC para [!DNL Vertica Analytics]. [Haga clic aquí](https://sfc-repo.snowflakecomputing.com/odbc/linux/latest/index.html) para iniciar la descarga.

1. A continuación, debe instalar unixODBC con el siguiente comando:

   ```
   apt-get install unixODBC
   ```

1. Si ya ha instalado el servidor [!DNL Vertica Analytics], ya se instalará un controlador ODBC. En este caso, actualice la unidad como se indica a continuación:

   ```
   #Switch to root
   sudo su
   
   #Move or copy the downloaded file and change to /root
   mv vertica_9.3..xx_odbc_x86_64_linux.tar.gz /
   cd /
   
   #Uncompress the file you downloaded
   tar vzxf vertica_9.3..xx_odbc_x86_64_linux.tar.gz
   
   #Remove the tar.gz since it is not needed anymore
   rm vertica_9.3..xx_odbc_x86_64_linux.tar.gz
   
   #Open odbcinst.ini
   vi /etc/odbcinst.ini
   
   #Add a section for Vertica Analytics and save
   [Vertica Analytics]
   Description = Vertica Analytics ODBC Driver
   Driver = /opt/vertica/lib64/libverticaodbc.so
   
   #Open odbc.ini
   vi /etc/odbc.ini
   
   #Add your DSN in ODBC Data Sources section, for example:
   [ODBC Data Sources]
   VMart = "VMart database on Vertica Analytics"
   
   #Add a DSN definition section below, for example:
   [VMart]
   Description = Vmart Database
   Driver = Vertica Analytics
   Database = VMart
   Servername = # The name of the server where Vertica Analytics is installed. Use localhost if Vertica Analytics is installed on the same machine.
   UID = dbadmin
   PWD = <password>
   Port = 5433
   ```

1. En Adobe Campaign, puede configurar su cuenta externa [!DNL Vertica Analytics]. Para obtener más información sobre cómo configurar su cuenta externa, consulte [esta sección](#vertica-external).

## Cuenta externa [!DNL Vertica Analytics] {#vertica-external}

Debe crear una cuenta externa [!DNL Vertica Analytics] para conectar la instancia de Campaign a la base de datos externa [!DNL Vertica Analytics].

1. En la campaña **[!UICONTROL Explorer]**, haga clic en **[!UICONTROL Administration]** &#39;>&#39; **[!UICONTROL Platform]** &#39;>&#39; **[!UICONTROL External accounts]**.

1. Haga clic en **[!UICONTROL New]**.

1. Seleccione **[!UICONTROL External database]** como **[!UICONTROL Type]** de su cuenta externa.

1. Configure la cuenta externa **[!UICONTROL Vertica Analytics]**. Debe especificar:

   * **[!UICONTROL Type]**: [!DNL Vertica Analytics]

   * **[!UICONTROL Server]**: URL del servidor [!DNL Vertica Analytics]

   * **[!UICONTROL Account]**: Nombre del usuario

   * **[!UICONTROL Password]**: Contraseña de la cuenta de usuario

   * **[!UICONTROL Database]**: Nombre de la base de datos

   ![](assets/vertica.png)

El conector admite las siguientes opciones:

| Opción | Descripción |
|---|---|
| TimeZoneName | De forma predeterminada, vacío, lo que significa que se utiliza la zona horaria del sistema del servidor de aplicaciones de Campaign Classic. La opción se puede utilizar para forzar el parámetro de sesión TIMEZONE. |

