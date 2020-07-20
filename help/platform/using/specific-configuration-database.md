---
title: Acceso a una base de datos externa
seo-title: Acceso a una base de datos externa
description: Acceso a una base de datos externa
seo-description: null
page-status-flag: never-activated
uuid: b84359b9-c584-431d-80d5-71146d9b6854
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: platform
content-type: reference
topic-tags: connectors
discoiquuid: dd3d14cc-5153-428d-a98a-32b46f0fe811
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 959455ec92b40581f04cf0e357b6c0d3f3fba81c
workflow-type: tm+mt
source-wordcount: '1833'
ht-degree: 99%

---


# Configuración de los conectores FDA {#specific-configurations-by-database-type}

En función de las bases de datos externas a las que desee tener acceso desde Adobe Campaign, debe realizar determinadas configuraciones específicas. Estas configuraciones implican esencialmente la instalación de controladores y la declaración de variables de entorno que pertenecen a cada RDBMS en el servidor de Adobe Campaign.

Para obtener más información sobre los conectores heredados como Teradata, Hadoop 2.1 o Netezza, consulte esta [página](../../platform/using/legacy-connectors.md).

Como regla general, debe instalar la capa del cliente correspondiente en la base de datos externa en el servidor de Adobe Campaign.

>[!NOTE]
>
>Las versiones compatibles se enumeran en la [Matriz de compatibilidad de Campaign](https://helpx.adobe.com/es/campaign/kb/compatibility-matrix.html#FederatedDataAccessFDA).

## Configurar el acceso a Azure Synapse {#configure-access-to-azure-synapse}

### Cuenta externa de Azure Synapse {#azure-external}

La cuenta externa [!DNL Azure] permite conectar la instancia de Campaign a la base de datos externa Azure Synapse.
Para crear la cuenta externa [!DNL Azure Synapse] de cuenta externa:

1. En Campaign Classic, configure la cuenta externa [!DNL Azure Synapse]. En **[!UICONTROL Explorer]**, haga clic en **[!UICONTROL Administration]** / **[!UICONTROL Platform]** / **[!UICONTROL External accounts]**.

1. Haga clic **[!UICONTROL New]**.

1. Seleccione **[!UICONTROL External database]** como **[!UICONTROL Type]** de su cuenta externa.

1. Configure la cuenta externa [!DNL Azure Synapse]. Debe especificar:

   * **[!UICONTROL Type]**: Azure Synapse Analytics

   * **[!UICONTROL Server]**: URL del servidor Azure Synapse

   * **[!UICONTROL Account]**: Nombre del usuario

   * **[!UICONTROL Password]**: Contraseña de la cuenta de usuario

   * **[!UICONTROL Database]**: Nombre de la base de datos

   ![](assets/azure_1.png)

### Azure Synapse en CentOS {#azure-centos}

**Requisitos previos:**

* Necesita privilegios de raíz para instalar un controlador ODBC.
* Los controladores ODBC de Red Hat Enterprise que proporciona Microsoft también se pueden utilizar con CentOS para conectarse a SQL Server.
* La versión 13.0 funciona con Red Hat 6 y 7.

Para configurar la Azure Synapse en CentOS:

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

1. En Campaign Classic, puede configurar la cuenta externa [!DNL Azure Synapse]. Para más información sobre cómo configurar la cuenta externa, consulte esta [sección](../../platform/using/specific-configuration-database.md#azure-external).

1. Dado que Azure Synapse Analytics se comunica a través del puerto TCP 1433, debe abrir este puerto en el cortafuegos. Utilice el siguiente comando:

   ```
   firewall-cmd --permanent --add-rich-rule='rule family="ipv4" source address="[server_ip_here]/32" port port="1433" protocol="tcp" accept'
   # you can ping your hostname and the ping command will translate the hostname to IP address which you can use here
   ```

   >[!NOTE]
   >
   >Para permitir la comunicación desde Azure Synapse Analytics, es posible que tenga que agregar su IP pública a la lista de permitidos. Para ello, consulte la [documentación de Azure](https://docs.microsoft.com/en-us/azure/sql-database/sql-database-firewall-configure#use-the-azure-portal-to-manage-server-level-ip-firewall-rules).

1. En el caso de iptables, ejecute el siguiente comando:

   ```
   iptables -A OUTPUT -p tcp -d [server_hostname_here] --dport 1433 -j ACCEPT
   ```

### Azure Synapse en Windows {#azure-windows}

>[!NOTE]
>
>Esto es exclusivo de la versión 13 del controlador ODBC, pero Adobe Campaign Classic también puede utilizar los controladores 11.0 y 10.0 del cliente nativo de SQL Server.

Para configurar Azure Synapse en Windows:

1. Primero, instale el controlador ODBC de Microsoft. Puede encontrarlo en esta [página](https://www.microsoft.com/en-us/download/details.aspx?id=50420).

1. Elija los siguientes archivos para instalar:

   ```
   your_language\your_architecture\msodbcsql.msi (i.e: English\X64\msodbcsql.msi)
   ```

1. Una vez instalado el controlador ODBC, puede probarlo si es necesario. Para obtener más información, consulte [esta página](https://docs.microsoft.com/en-us/sql/connect/odbc/windows/system-requirements-installation-and-driver-files?view=sql-server-ver15#installing-microsoft-odbc-driver-for-sql-server).

1. En Campaign Classic, puede configurar la cuenta externa [!DNL Azure Synapse]. Para más información sobre cómo configurar la cuenta externa, consulte esta [sección](../../platform/using/specific-configuration-database.md#azure-external).

1. Dado que Azure Synapse Analytics se comunica a través del puerto TCP 1433, debe abrir este puerto en Windows Defender Firewall. Para más información, consulte la [documentación de Windows](https://docs.microsoft.com/en-us/windows/security/threat-protection/windows-firewall/create-an-outbound-program-or-service-rule).

### Azure Synapse en Debian {#azure-debian}

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

1. Si recibe el siguiente error **“No se encontró el controlador de método /usr/lib/apt/methods/https”** al consultar la **actualización de sudo apt-get**, debe ejecutar el comando:

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

1. En Campaign Classic, puede configurar la cuenta externa [!DNL Azure Synapse]. Para más información sobre cómo configurar la cuenta externa, consulte esta [sección](../../platform/using/specific-configuration-database.md#azure-external).

1. Para configurar iptables en Debian para garantizar la conexión con Azure Synapse Analytics, habilite el puerto TCP 1433 saliente para su nombre de host con el siguiente comando:

   ```
   iptables -A OUTPUT -p tcp -d [server_hostname_here] --dport 1433 -j ACCEPT
   ```

   >[!NOTE]
   >
   >Para permitir la comunicación desde Azure Synapse Analytics, es posible que tenga que agregar su IP pública a la lista de permitidos. Para ello, consulte la  [documentación de Azure](https://docs.microsoft.com/en-us/azure/sql-database/sql-database-firewall-configure#use-the-azure-portal-to-manage-server-level-ip-firewall-rules).

## Configuración del acceso a Snowflake {#configure-access-to-snowflake}

>[!NOTE]
>
>[!DNL Snowflake]El conector está disponible para implementaciones alojadas y on-premise. Para obtener más información, consulte [este artículo](https://helpx.adobe.com/es/campaign/kb/acc-on-prem-vs-hosted.html).

![](assets/snowflake_3.png)

### Cuenta externa Snowflake {#snowflake-external}

La cuenta externa [!DNL Snowflake] permite conectar la instancia de Campaign a la base de datos externa Snowflake.

1. En Campaign Classic, configure la cuenta externa [!DNL Snowflake]. En **[!UICONTROL Explorer]**, haga clic en **[!UICONTROL Administration]** / **[!UICONTROL Platform]** / **[!UICONTROL External accounts]**.

1. Haga clic **[!UICONTROL New]**.

1. Seleccione **[!UICONTROL External database]** como **[!UICONTROL Type]** de su cuenta externa.

1. Configure la cuenta externa **[!UICONTROL Snowflake]**. Debe especificar:

   * **[!UICONTROL Type]**: [!DNL Snowflake]

   * **[!UICONTROL Server]**: URL del servidor [!DNL Snowflake]

   * **[!UICONTROL Account]**: Nombre del usuario

   * **[!UICONTROL Password]**: Contraseña de la cuenta de usuario

   * **[!UICONTROL Database]**: Nombre de la base de datos

   ![](assets/snowflake.png)

1. Haga clic en la pestaña **[!UICONTROL Parameters]** y luego en el botón **[!UICONTROL Deploy functions]** para crear funciones.

   ![](assets/snowflake_2.png)

El conector admite las siguientes opciones:

| Opción | Descripción |
|---|---|
| esquema de trabajo | Esquema de base de datos que se va a utilizar para tablas de trabajo |
| almacén | Nombre del almacén predeterminado que se va a utilizar. Anula el valor predeterminado del usuario. |
| TimeZoneName | De forma predeterminada, vacío, lo que significa que se utiliza la zona horaria del sistema del servidor de aplicaciones de Campaign Classic. La opción se puede utilizar para forzar el parámetro de sesión TIMEZONE. <br>[Para obtener más información, consulte esta página](https://docs.snowflake.net/manuals/sql-reference/parameters.html#timezone). |
| WeekStart | Parámetro de sesión WEEK_START. De forma predeterminada, se establece en 0. <br>[Para obtener más información, consulte esta página](https://docs.snowflake.com/en/sql-reference/parameters.html#week-start). |
| UseCachedResult | Parámetro de sesión USE_CACHED_RESULTS. De forma predeterminada, se establece en TRUE. Esta opción se puede utilizar para deshabilitar los resultados en caché de Snowflake. <br>Para obtener más información, consulte [esta página](https://docs.snowflake.net/manuals/user-guide/querying-persisted-results.html). |

### Snowflake en CentOS {#snowflake-centos}

1. Descargue los controladores ODBC para [!DNL Snowflake]. [Haga clic aquí](https://sfc-repo.snowflakecomputing.com/odbc/linux/latest/snowflake-odbc-2.20.2.x86_64.rpm) para iniciar la descarga.
1. A continuación, debe instalar los controladores ODBC en CentOs con el siguiente comando:

   ```
   rpm -Uvh unixodbc
   rpm -Uvh snowflake-odbc-2.20.2.x86_64.rpm
   ```

1. Después de descargar e instalar los controladores ODBC, debe reiniciar Campaign Classic. Para ello, ejecute el siguiente comando:

   ```
   /etc/init.d/nlserver6 stop
   /etc/init.d/nlserver6 start
   ```

1. En Campaign Classic, puede configurar la cuenta externa [!DNL Snowflake]. Para más información sobre cómo configurar la cuenta externa, consulte esta [sección](../../platform/using/specific-configuration-database.md#snowflake-external).

### Snowflake en Debian {#snowflake-debian}

1. Descargue los controladores ODBC para [!DNL Snowflake]. [Haga clic aquí](https://sfc-repo.snowflakecomputing.com/odbc/linux/latest/index.html) para iniciar la descarga.

1. Luego debe instalar los controladores ODBC en Debian con el siguiente comando:

   ```
   apt-get install unixodbc
   apt-get install snowflake-odbc-x.xx.x.x86_64.deb
   ```

1. Después de descargar e instalar los controladores ODBC, debe reiniciar Campaign Classic. Para ello, ejecute el siguiente comando:

   ```
   systemctl stop nlserver.service
   systemctl start nlserver.service
   ```

1. En Campaign Classic, puede configurar la cuenta externa [!DNL Snowflake]. Para más información sobre cómo configurar la cuenta externa, consulte esta [sección](../../platform/using/specific-configuration-database.md#snowflake-external).

### Snowflake en Windows {#snowflake-windows}

1. Descargue [el controlador ODBC para Windows](https://docs.snowflake.net/manuals/user-guide/odbc-download.html). Tenga en cuenta que necesita privilegios de administrador para instalar el controlador. Para obtener más información, consulte [esta página](https://docs.snowflake.net/manuals/user-guide/admin-user-management.html)

1. Configure el controlador ODBC. Para obtener más información, consulte [esta página](https://docs.snowflake.net/manuals/user-guide/odbc-windows.html#step-2-configure-the-odbc-driver)

1. En Campaign Classic, puede configurar la cuenta externa [!DNL Snowflake]. Para más información sobre cómo configurar la cuenta externa, consulte esta [sección](../../platform/using/specific-configuration-database.md#snowflake-external).

## Configuración del acceso a Hadoop 3.0 {#configure-access-to-hadoop-3}

### Cuenta externa de Hadoop {#hadoop-external}

La cuenta externa [!DNL Hadoop] permite conectar la instancia de Campaign a la base de datos externa de Hadoop.

1. En Campaign Classic, configure la cuenta externa [!DNL Hadoop]. En **[!UICONTROL Explorer]**, haga clic en **[!UICONTROL Administration]** / **[!UICONTROL Platform]** / **[!UICONTROL External accounts]**.

1. Haga clic **[!UICONTROL New]**.

1. Seleccione **[!UICONTROL External database]** como **[!UICONTROL Type]** de su cuenta externa.

1. Configure la cuenta externa **[!UICONTROL Hadoop]**. Debe especificar:

   * **[!UICONTROL Type]**: ODBC (Sybase ASE, Sybase IQ)

   * **[!UICONTROL Server]**: Nombre del DNS

   * **[!UICONTROL Account]**: Nombre del usuario

   * **[!UICONTROL Password]**: Contraseña de la cuenta de usuario

   * **[!UICONTROL Database]**: Nombre de la base de datos si no se especifica en DSN. Se puede dejar vacío si se especifica en el DSN

   * **[!UICONTROL Time zone]**: Zona horaria del servidor

   ![](assets/hadoop3.png)

El conector admite las siguientes opciones de ODBC:

| Name | Valor |
|---|---|
| ODBCMgr | iODBC |
| almacén | 1/2/4 |

El conector también admite las siguientes opciones de Hive:

| Name | Valor | Descripción |
|---|---|---|
| bulkKey | Clave de acceso de Azure blob o DataLake | Para cargadores masivos wasb:// o wasbs:// (es decir, si la herramienta de carga masiva inicio con wasb:// o wasbs://). <br>Es la clave de acceso para blob o el bloque DataLake para la carga masiva. |
| hdfsPort | número de puerto <br>establecido de forma predeterminada en 8020. | Para la carga masiva de HDFS (es decir, si la herramienta de carga masiva inicia con webhdfs:// o webhdfss://). |
| bucketNumber | 20 | Número de bloques al crear una tabla agrupada. |
| fileFormat | PARQUET | Formato de archivo predeterminado para tablas de trabajo. |

### Configuración de Hadoop 3.0 {#configuring-hadoop}

La conexión a una base de datos externa de Hadoop en FDA requiere las siguientes configuraciones en el servidor de Adobe Campaign. Tenga en cuenta que esta configuración está disponible tanto para Windows como para Linux.

1. Descargue los controladores ODBC para Hadoop en función de su versión del sistema operativo. Los controladores se encuentran en [esta página](https://www.cloudera.com/downloads.html).

1. A continuación, debe instalar los controladores ODBC y crear un DSN para la conexión de Hive. Las instrucciones se encuentran en [esta página](https://docs.cloudera.com/documentation/other/connectors/hive-odbc/2-6-5/Cloudera-ODBC-Driver-for-Apache-Hive-Install-Guide.pdf).

1. Después de descargar e instalar los controladores ODBC, debe reiniciar Campaign Classic. Para ello, ejecute el siguiente comando:

   ```
   systemctl stop nlserver.service
   systemctl start nlserver.service
   ```

1. En Campaign Classic, puede configurar la cuenta externa [!DNL Hadoop]. Para más información sobre cómo configurar la cuenta externa, consulte esta [sección](../../platform/using/specific-configuration-database.md#hadoop-external).

## Configuración del acceso a Oracle {#configure-access-to-oracle}

### Cuenta externa de Oracle {#oracle-external}

La cuenta externa [!DNL Oracle] permite conectar la instancia de Campaign a la base de datos externa de Hadoop.

1. En Campaign Classic, configure la cuenta externa [!DNL oracle]. En **[!UICONTROL Explorer]**, haga clic en **[!UICONTROL Administration]** / **[!UICONTROL Platform]** / **[!UICONTROL External accounts]**.

1. Haga clic **[!UICONTROL New]**.

1. Seleccione **[!UICONTROL External database]** como **[!UICONTROL Type]** de su cuenta externa.

1. Configure la cuenta externa **[!UICONTROL Oracle]**. Debe especificar:

   * **[!UICONTROL Type]**: Oracle

   * **[!UICONTROL Server]**: Nombre del DNS

   * **[!UICONTROL Account]**: Nombre del usuario

   * **[!UICONTROL Password]**: Contraseña de la cuenta de usuario

   * **[!UICONTROL Time zone]**: Zona horaria del servidor

   ![](assets/oracle_config.png)

### Oracle en Linux {#for-linux-1}

La conexión a una base de datos externa de Oracle en FDA requiere ciertas configuraciones adicionales en el servidor de Adobe Campaign.

1. Instale el cliente completo Oracle correspondiente a su versión de Oracle.
1. Añada sus definiciones de TNS a la instalación. Para ello, debe especificarlas en un archivo **tnsnames.ora** en el repositorio /etc/oracle. Si este repositorio no existe, créelo.

   A continuación, cree una nueva variable de entorno TNS_ADMIN: exporte TNS_ADMIN=/etc/oracle y reinicie el equipo.

1. Integre Oracle en el servidor de Adobe Campaign (nlserver). Para ello, compruebe que el archivo **customer.sh** esté presente en la carpeta “nl6” de la estructura del árbol de servidor de Adobe Campaign y que incluye los enlaces a las bibliotecas de Oracle.

   Por ejemplo, para un cliente en 11.2:

   ```
   export ORACLE_HOME=/usr/lib/oracle/11.2
   export TNS_ADMIN=/etc/oracle
   export LD_LIBRARY_PATH=$ORACLE_HOME/client64/lib:$LD_LIBRARY_PATH
   ```

   >[!NOTE]
   >
   >Estos valores (especialmente ORACLE_HOME) dependen de los repositorios de instalación. Asegúrese de comprobar la estructura del árbol antes de hacer referencia a estos valores.

1. Instale las bibliotecas necesarias para Oracle:

   * **libclntsh.so**

      ```
      cd /usr/lib/oracle/<version>/client<architecture>/lib
      ln -s libclntsh.so.<version> libclntsh.so
      ```

   * **libaio1**

      ```
      aptitude install libaio1
      or
      yum install libaio1
      ```

1. En Campaign Classic, puede configurar la cuenta externa [!DNL Oracle]. Para más información sobre cómo configurar la cuenta externa, consulte esta [sección](../../platform/using/specific-configuration-database.md#oracle-external).

### Oracle en Windows {#for-windows-1}

La conexión a una base de datos externa de Oracle en FDA requiere ciertas configuraciones adicionales en el servidor de Adobe Campaign.

1. Instale el cliente Oracle.

1. En la carpeta C:\Oracle, cree un archivo **tnsnames.ora** con la definición de TNS.

1. Añada una variable de entorno TNS_ADMIN con C:\Oracle como valor y reinicie el equipo.

1. En Campaign Classic, puede configurar la cuenta externa [!DNL Oracle]. Para más información sobre cómo configurar la cuenta externa, consulte esta [sección](../../platform/using/specific-configuration-database.md#oracle-external).