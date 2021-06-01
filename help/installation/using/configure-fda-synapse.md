---
product: campaign
title: Configuración del acceso a Synapse
description: Obtenga información sobre cómo configurar el acceso a Synapse en FDA
audience: platform
content-type: reference
topic-tags: connectors
exl-id: 59d0277a-7588-4504-94e3-50f87b60da8a
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: tm+mt
source-wordcount: '703'
ht-degree: 79%

---

# Configurar el acceso a Azure Synapse {#configure-access-to-azure-synapse}

Utilice la opción [Federated Data Access](../../installation/using/about-fda.md) (FDA) de Campaign para procesar la información almacenada en una base de datos externa. Siga los pasos a continuación para configurar el acceso a Microsoft Azure synapse Analytics.

1. Configure el Azure synapse en [CentOS](#azure-centos), [Windows](#azure-windows) o [Debian](#azure-debian)
1. Configurar el Azure synapse [cuenta externa](#azure-external) en Campaign

## Azure Synapse en CentOS {#azure-centos}

>[!CAUTION]
>
>* Necesitará privilegios de raíz para instalar un controlador ODBC.
>* Los controladores ODBC de Red Hat Enterprise que proporciona Microsoft también se pueden utilizar con CentOS para conectarse a SQL Server.
>* La versión 13.0 funciona con Red Hat 6 y 7.


Para configurar el Azure synapse en CentOS, siga los pasos a continuación:

1. En primer lugar, instale el controlador ODBC. Puede encontrarlo en esta [página](https://www.microsoft.com/en-us/download/details.aspx?id=50420).

   >[!NOTE]
   >
   >Esto es exclusivo de la versión 13 del controlador ODBC.

   ```
   sudo su
   curl https://packages.microsoft.com/config/rhel/6/prod.repo > /etc/yum.repos.d/mssql-release.repo
   exit
   # Uninstall if already installed Unix ODBC driver
   sudo yum remove unixODBC-utf16 unixODBC-utf16-devel #to avoid conflicts
   
   sudo ACCEPT_EULA=Y yum install msodbcsql
   
   sudo ACCEPT_EULA=Y yum install mssql-tools
   echo 'export PATH="$PATH:/opt/mssql-tools/bin"' >> ~/.bash_profile
   echo 'export PATH="$PATH:/opt/mssql-tools/bin"' >> ~/.bashrc
   source ~/.bashrc
   
   # the Microsoft driver expects unixODBC to be here /usr/lib64/libodbc.so.1, so add soft links to the '.so.2' files
   cd /usr/lib64
   sudo ln -s libodbccr.so.2   libodbccr.so.1
   sudo ln -s libodbcinst.so.2 libodbcinst.so.1
   sudo ln -s libodbc.so.2     libodbc.so.1
   
   # Set the path for unixODBC
   export ODBCINI=/usr/local/etc/odbc.ini
   export ODBCSYSINI=/usr/local/etc
   source ~/.bashrc
   
   #Add a DSN information to /etc/odbc.ini
   sudo vi /etc/odbc.ini
   
   #Add the following:
   [Azure Synapse Analytics]
   Driver      = ODBC Driver 13 for SQL Server
   Description = Azure Synapse Analytics DSN
   Trace       = No
   Server      = [insert your server here]
   ```

1. Si es necesario, puede instalar los encabezados de desarrollo unixODBC ejecutando el siguiente comando:

   ```
   sudo yum install unixODBC-devel
   ```

1. Después de instalar los controladores, puede probar y comprobar el controlador ODBC y realizar la consulta de la base de datos si es necesario. Ejecute el siguiente comando:

   ```
   /opt/mssql-tools/bin/sqlcmd -S yourServer -U yourUserName -P yourPassword -q "your query" # for example -q "select 1"
   ```

1. En Campaign, puede configurar la cuenta externa [!DNL Azure Synapse] . Para obtener más información sobre cómo configurar la cuenta externa, consulte [esta sección](#azure-external).

1. Dado que Azure Synapse Analytics se comunica a través del puerto TCP 1433, debe abrir este puerto en el cortafuegos. Utilice el siguiente comando:

   ```
   firewall-cmd --permanent --add-rich-rule='rule family="ipv4" source address="[server_ip_here]/32" port port="1433" protocol="tcp" accept'
   # you can ping your hostname and the ping command will translate the hostname to IP address which you can use here
   ```

   >[!NOTE]
   >
   >Para permitir la comunicación desde Azure Synapse Analytics, es posible que tenga que añadir su IP pública a la lista de permitidos. Para ello, consulte la [documentación de Azure](https://docs.microsoft.com/en-us/azure/sql-database/sql-database-firewall-configure#use-the-azure-portal-to-manage-server-level-ip-firewall-rules).

1. En el caso de iptables, ejecute el siguiente comando:

   ```
   iptables -A OUTPUT -p tcp -d [server_hostname_here] --dport 1433 -j ACCEPT
   ```

## Azure Synapse en Windows {#azure-windows}

>[!NOTE]
>
>Esto es exclusivo de la versión 13 del controlador ODBC, pero Adobe Campaign Classic también puede utilizar los controladores 11.0 y 10.0 del cliente nativo de SQL Server.

Para configurar Azure Synapse en Windows:

1. Primero, instale el controlador ODBC de Microsoft. Puede encontrarlo en [esta página](https://www.microsoft.com/en-us/download/details.aspx?id=50420).

1. Elija los siguientes archivos para instalar:

   ```
   your_language\your_architecture\msodbcsql.msi (i.e: English\X64\msodbcsql.msi)
   ```

1. Una vez instalado el controlador ODBC, puede probarlo si es necesario. Para obtener más información, consulte [esta página](https://docs.microsoft.com/en-us/sql/connect/odbc/windows/system-requirements-installation-and-driver-files?view=sql-server-ver15#installing-microsoft-odbc-driver-for-sql-server).

1. En Campaign Classic, puede configurar la cuenta externa [!DNL Azure Synapse]. Para obtener más información sobre cómo configurar la cuenta externa, consulte [esta sección](#azure-external).

1. Dado que Azure Synapse Analytics se comunica a través del puerto TCP 1433, debe abrir este puerto en Windows Defender Firewall. Para más información, consulte la [documentación de Windows](https://docs.microsoft.com/en-us/windows/security/threat-protection/windows-firewall/create-an-outbound-program-or-service-rule).

## Azure Synapse en Debian {#azure-debian}

**Requisitos previos:**

* Necesita privilegios de raíz para instalar un controlador ODBC.
* Curl es necesario para instalar el paquete msodbcsql. Si no lo tiene instalado, ejecute el siguiente comando:

   ```
   sudo apt-get install curl
   ```

Para configurar Azure Synapse en Debian:

1. Primero, instale el controlador ODBC de Microsoft para SQL Server. Utilice los siguientes comandos para instalar el controlador ODBC 13.1 para SQL Server:

   ```
   sudo su
   curl https://packages.microsoft.com/keys/microsoft.asc | apt-key add -
   curl https://packages.microsoft.com/config/debian/8/prod.list > /etc/apt/sources.list.d/mssql-release.list
   exit
   sudo apt-get update
   sudo ACCEPT_EULA=Y apt-get install msodbcsql
   ```

1. Si recibe el siguiente error **&quot;No se encontró el controlador de método /usr/lib/apt/methods/https&quot;** al consultar la **actualización de sudo apt-get**, debe ejecutar el comando:

   ```
   sudo apt-get install apt-transport-https ca-certificates
   ```

1. Ahora debe instalar mssql-tools con los siguientes comandos. Se necesitan herramientas Mssq para utilizar la utilidad de programa de copia masiva (o BCP) y ejecutar consultas.

   ```
   sudo ACCEPT_EULA=Y apt-get install mssql-tools
   echo 'export PATH="$PATH:/opt/mssql-tools/bin"' >> ~/.bash_profile
   echo 'export PATH="$PATH:/opt/mssql-tools/bin"' >> ~/.bashrc
   source ~/.bashrc
   ```

1. Si es necesario, puede instalar los encabezados de desarrollo unixODBC ejecutando el siguiente comando:

   ```
   sudo yum install unixODBC-devel
   ```

1. Después de instalar los controladores, puede probar y comprobar el controlador ODBC y realizar la consulta de la base de datos si es necesario. Ejecute el siguiente comando:

   ```
   /opt/mssql-tools/bin/sqlcmd -S yourServer -U yourUserName -P yourPassword -q "your query" # for example -q "select 1"
   ```

1. En Campaign Classic, ahora puede configurar la cuenta externa [!DNL Azure Synapse]. Para obtener más información sobre cómo configurar la cuenta externa, consulte [esta sección](#azure-external).

1. Para configurar iptables en Debian para garantizar la conexión con Azure Synapse Analytics, habilite el puerto TCP 1433 saliente para su nombre de host con el siguiente comando:

   ```
   iptables -A OUTPUT -p tcp -d [server_hostname_here] --dport 1433 -j ACCEPT
   ```

   >[!NOTE]
   >
   >Para permitir la comunicación desde Azure Synapse Analytics, es posible que tenga que añadir su IP pública a la lista de permitidos. Para ello, consulte la [documentación de Azure](https://docs.microsoft.com/en-us/azure/sql-database/sql-database-firewall-configure#use-the-azure-portal-to-manage-server-level-ip-firewall-rules).


## Cuenta externa de azure synapse {#azure-external}

La cuenta externa [!DNL Azure Synapse] permite conectar la instancia de Campaign a la base de datos externa Azure Synapse.

Para crear su cuenta externa [!DNL Azure Synapse], siga los pasos a continuación:

1. En Campaña **[!UICONTROL Explorer]**, haga clic en **[!UICONTROL Administration]** &#39;>&#39; **[!UICONTROL Platform]** &#39;>&#39; **[!UICONTROL External accounts]**.

1. Haga clic en **[!UICONTROL New]**.

1. Seleccione **[!UICONTROL External database]** como **[!UICONTROL Type]** de su cuenta externa.

   ![](assets/azure_1.png)

1. Configure la cuenta externa [!DNL Azure Synapse]. Debe especificar:

   * **[!UICONTROL Type]**: Azure Synapse Analytics

   * **[!UICONTROL Server]**: URL del servidor Azure Synapse

   * **[!UICONTROL Account]**: Nombre del usuario

   * **[!UICONTROL Password]**: Contraseña de la cuenta de usuario

   * **[!UICONTROL Database]**: Nombre de la base de datos
