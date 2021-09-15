---
product: campaign
title: Configuración del acceso a Vertica
description: Aprenda a configurar el acceso a Vertica en FDA
audience: platform
content-type: reference
topic-tags: connectors
exl-id: 8b2a9c73-807a-4936-9fd6-9d26c805a31f
source-git-commit: 0cfe8439007b56014eba497c511904c4f11b39ce
workflow-type: tm+mt
source-wordcount: '361'
ht-degree: 19%

---

# Configuración del acceso a Vertica {#configure-fda-vertica}

![](../../assets/v7-only.svg)

Utilice la opción **Federated Data Access** (FDA) de Campaign para procesar la información almacenada en una base de datos externa. Siga los pasos a continuación para configurar el acceso a [!DNL Vertica].

1. Configure [!DNL Vertica] en [CentOS](#vertica-centos), [Windows](#vertica-windows) o [Debian](#vertica-debian)
1. Configurar la [!DNL Vertica] [cuenta externa](#vertica-external) en Campaign


>[!NOTE]
>
>[!DNL Vertica] El conector está disponible para implementaciones híbridas y locales. Para obtener más información, consulte [esta página](../../installation/using/capability-matrix.md).

![](assets/snowflake_3.png)

## Vertica en CentOS {#vertica-centos}

Para configurar [!DNL Vertica] en CentOS, siga los pasos a continuación:

1. Descargue los controladores ODBC para [!DNL Vertica]. [Haga clic ](https://www.vertica.com/download/vertica/client-drivers/) aquí y descargue las últimas RPM de Linux.

1. A continuación, debe instalar unixODBC con el siguiente comando:

   ```
   yum search unixODBC
   yum install unixODBC.x86_64
   ```

1. Si ha instalado anteriormente el servidor [!DNL Vertica], ya se instalará un controlador ODBC. En este caso, actualice la unidad de la siguiente manera:

   ```
   #Switch to root
   sudo su
   
   #Install the package (add --force to update it)
   rpm -Uvh vertica-client-x.x.x-x.x86_64.rpm [--force]
   
   #Open odbcinst.ini
   vi /etc/odbcinst.ini
   
   #Add a section for Vertica and save
   [Vertica]
   Description = Vertica ODBC Driver
   Driver = /opt/vertica/lib64/libverticaodbc.so
   
   #Open odbc.ini
   vi /etc/odbc.ini
   
   #Add your DSN in ODBC Data Sources section, for example:
   [ODBC Data Sources]
   VMart = "VMart database on Vertica"
   
   #Add a DSN definition section below, for example:
   [VMart]
   Description = Vmart Database
   Driver = Vertica
   Database = VMart
   Servername = # The name of the server where Vertica is installed. Use localhost if Vertica is installed on the same machine.
   UID = dbadmin
   PWD = <password>
   Port = 5433
   
   #Cleanup
   #Remove the ODBC package
   rm vertica-client-x.x.x-x.x86_64.rpm
   ```

1. En Adobe Campaign, puede configurar la cuenta externa [!DNL Vertica] . Para obtener más información sobre cómo configurar la cuenta externa, consulte [esta sección](#vertica-external).

## Vertica en Windows {#vertica-windows}

1. Descargue [el controlador ODBC para Windows](https://www.vertica.com/download/vertica/client-drivers/). Para instalar el controlador para Windows, deberá habilitar .NET Framework 3.5 o el asistente de instalación intentará habilitarlo y descargarlo automáticamente.

1. Configure el controlador ODBC en Windows. Para obtener más información, consulte [esta página](https://www.vertica.com/docs/9.2.x/HTML/Content/Authoring/ConnectingToVertica/ClientODBC/SettingUpADSN.htm)

1. En Adobe Campaign, puede configurar la cuenta externa [!DNL Vertica] . Para obtener más información sobre cómo configurar la cuenta externa, consulte [esta sección](#vertical-external).

## Vertica en Debian {#vertica-debian}

1. Descargue los controladores ODBC para [!DNL Vertica]. [Haga clic aquí](https://sfc-repo.snowflakecomputing.com/odbc/linux/latest/index.html) para iniciar la descarga.

1. A continuación, debe instalar unixODBC con el siguiente comando:

   ```
   apt-get install unixODBC
   ```

1. Si ha instalado anteriormente el servidor [!DNL Vertica], ya se instalará un controlador ODBC. En este caso, actualice la unidad de la siguiente manera:

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
   
   #Add a section for Vertica and save
   [Vertica]
   Description = Vertica ODBC Driver
   Driver = /opt/vertica/lib64/libverticaodbc.so
   
   #Open odbc.ini
   vi /etc/odbc.ini
   
   #Add your DSN in ODBC Data Sources section, for example:
   [ODBC Data Sources]
   VMart = "VMart database on Vertica"
   
   #Add a DSN definition section below, for example:
   [VMart]
   Description = Vmart Database
   Driver = Vertica
   Database = VMart
   Servername = # The name of the server where Vertica is installed. Use localhost if Vertica is installed on the same machine.
   UID = dbadmin
   PWD = <password>
   Port = 5433
   ```

1. En Adobe Campaign, puede configurar la cuenta externa [!DNL Vertica] . Para obtener más información sobre cómo configurar la cuenta externa, consulte [esta sección](#vertica-external).

## Cuenta externa vertical {#vertica-external}

Debe crear una cuenta externa [!DNL Vertica] para conectar la instancia de Campaign a la base de datos externa [!DNL Vertica].

1. En Campaña **[!UICONTROL Explorer]**, haga clic en **[!UICONTROL Administration]** &#39;>&#39; **[!UICONTROL Platform]** &#39;>&#39; **[!UICONTROL External accounts]**.

1. Haga clic en **[!UICONTROL New]**.

1. Seleccione **[!UICONTROL External database]** como **[!UICONTROL Type]** de su cuenta externa.

1. Configure la cuenta externa **[!UICONTROL Vertica]**. Debe especificar:

   * **[!UICONTROL Type]**: [!DNL Vertica Analytics]

   * **[!UICONTROL Server]**: URL del servidor [!DNL Vertica]

   * **[!UICONTROL Account]**: Nombre del usuario

   * **[!UICONTROL Password]**: Contraseña de la cuenta de usuario

   * **[!UICONTROL Database]**: Nombre de la base de datos
   ![](assets/vertica.png)
