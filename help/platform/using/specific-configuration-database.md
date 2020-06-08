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
source-git-commit: cc9ea59a9925930d4a4b260ce73a6bd4b615db5a
workflow-type: tm+mt
source-wordcount: '2857'
ht-degree: 78%

---


# Configuraciones específicas por tipo de base de datos {#specific-configurations-by-database-type}

En función de las bases de datos externas a las que desee tener acceso desde Adobe Campaign, debe realizar determinadas configuraciones específicas. Estas configuraciones implican esencialmente la instalación de controladores y la declaración de variables de entorno que pertenecen a cada RDBMS en el servidor de Adobe Campaign.

Como regla general, debe instalar la capa del cliente correspondiente en la base de datos externa en el servidor de Adobe Campaign.

>[!NOTE]
>
>Las versiones compatibles se enumeran en la [Matriz de compatibilidad de Campaign](https://helpx.adobe.com/es/campaign/kb/compatibility-matrix.html#FederatedDataAccessFDA).

## Configurar el acceso a la sinapsis de Azure {#configure-access-to-azure-synapse}

### Azure synapse external account {#azure-external}

The [!DNL Azure] external account allows you to connect your Campaign instance to your Azure Synapse external database.
Para crear la cuenta externa [!DNL Azure Synapse] de cuenta externa:

1. En Campaign Classic, configure la [!DNL Azure Synapse] cuenta externa. En **[!UICONTROL Explorer]**, haga clic en **[!UICONTROL Administration]** / **[!UICONTROL Platform]** / **[!UICONTROL External accounts]**.

1. Haga clic **[!UICONTROL Create]**.

1. Configure la cuenta externa [!DNL Azure Synapse]. Debe especificar:

   * **[!UICONTROL Type]**:: Análisis de sinapsis de Azure

   * **[!UICONTROL Server]**:: URL del servidor de Azure Synapse

   * **[!UICONTROL Account]**: Nombre del usuario

   * **[!UICONTROL Password]**: Contraseña de la cuenta de usuario

   * **[!UICONTROL Database]**: Nombre de la base de datos
   ![](assets/azure_1.png)

### Sinapsis de Azure en CentOS {#azure-centos}

**Requisitos previos:**

* Necesitará privilegios de raíz para instalar un controlador ODBC.
* Los controladores ODBC de Red Hat Enterprise proporcionados por Microsoft también se pueden utilizar con CentOS para conectarse a SQL Server.
* La versión 13.0 funcionará con Red Hat 6 y 7.

Para configurar la sinapsis de Azure en CentOS:

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

1. En Campaign Classic, puede configurar la cuenta externa [!DNL Azure Synapse]. Para obtener más información sobre cómo configurar la cuenta externa, consulte esta [sección](../../platform/using/specific-configuration-database.md#azure-external).

1. Dado que Azure Synapse Analytics se comunica a través del puerto TCP 1433, debe abrir este puerto en el servidor de seguridad. Utilice el siguiente comando:

   ```
   firewall-cmd --permanent --add-rich-rule='rule family="ipv4" source address="[server_ip_here]/32" port port="1433" protocol="tcp" accept'
   # you can ping your hostname and the ping command will translate the hostname to IP address which you can use here
   ```

   >[!NOTE]
   >
   >Para permitir la comunicación desde Azure Synapse Analytics, es posible que deba incluir en la lista blanca su IP pública. Para ello, consulte la documentación [de](https://docs.microsoft.com/en-us/azure/sql-database/sql-database-firewall-configure#use-the-azure-portal-to-manage-server-level-ip-firewall-rules)Azure.

1. En el caso de iptables, ejecute el siguiente comando:

   ```
   iptables -A OUTPUT -p tcp -d [server_hostname_here] --dport 1433 -j ACCEPT
   ```

### Sinapsis de Azure en Windows {#azure-windows}

>[!NOTE]
>
>Esto es exclusivo de la versión 13 del controlador ODBC, pero Adobe Campaign Classic también puede utilizar los controladores 11.0 y 10.0 del cliente nativo de SQL Server.

Para configurar la sinapsis de Azure en Windows:

1. En primer lugar, instale el controlador ODBC de Microsoft. Puede encontrarlo en esta [página](https://www.microsoft.com/en-us/download/details.aspx?id=50420).

1. Elija los siguientes archivos para instalar:

   ```
   your_language\your_architecture\msodbcsql.msi (i.e: English\X64\msodbcsql.msi)
   ```

1. Una vez instalado el controlador ODBC, puede probarlo si es necesario. Para obtener más información, consulte [esta página](https://docs.microsoft.com/en-us/sql/connect/odbc/windows/system-requirements-installation-and-driver-files?view=sql-server-ver15#installing-microsoft-odbc-driver-for-sql-server).

1. En Campaign Classic, puede configurar la cuenta externa [!DNL Azure Synapse]. Para obtener más información sobre cómo configurar la cuenta externa, consulte esta [sección](../../platform/using/specific-configuration-database.md#azure-external).

1. Dado que Azure Synapse Analytics se comunica a través del puerto TCP 1433, debe abrir este puerto en el Firewall de Windows Defender. For more on this, refer to [Windows documentation](https://docs.microsoft.com/en-us/windows/security/threat-protection/windows-firewall/create-an-outbound-program-or-service-rule).

### Sinapsis de Azure en Debian {#azure-debian}

**Requisitos previos:**

* Necesitará privilegios de raíz para instalar un controlador ODBC.
* Curl es necesario para instalar el paquete msodbcsql. Si no lo tiene instalado, ejecute el siguiente comando:

   ```
   sudo apt-get install curl
   ```

Para configurar Azure Synapse en Debian:

1. En primer lugar, instale el controlador ODBC de Microsoft para SQL Server. Utilice los siguientes comandos para instalar el controlador ODBC 13.1 para SQL Server:

   ```
   sudo su
   curl https://packages.microsoft.com/keys/microsoft.asc | apt-key add -
   curl https://packages.microsoft.com/config/debian/8/prod.list > /etc/apt/sources.list.d/mssql-release.list
   exit
   sudo apt-get update
   sudo ACCEPT_EULA=Y apt-get install msodbcsql
   ```

1. Si recibe el siguiente error **&quot;No se encontró el controlador de método /usr/lib/apt/methods/https&quot;** al llamar a la actualización **de** sudo apt-get, debe ejecutar el comando:

   ```
   sudo apt-get install apt-transport-https ca-certificates
   ```

1. Ahora necesita instalar mssql-tools con los siguientes comandos. Se necesitan herramientas Mssq para utilizar la utilidad de programa de copia masiva (o BCP) y para ejecutar consultas.

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

1. In Campaign Classic, you can now configure your [!DNL Azure Synapse] external account. Para obtener más información sobre cómo configurar la cuenta externa, consulte esta [sección](../../platform/using/specific-configuration-database.md#azure-external).

1. Para configurar iptables en Debian para garantizar la conexión con Azure Synapse Analytics, habilite el puerto TCP 1433 saliente para su nombre de host con el siguiente comando:

   ```
   iptables -A OUTPUT -p tcp -d [server_hostname_here] --dport 1433 -j ACCEPT
   ```

   >[!NOTE]
   >
   >Para permitir la comunicación desde Azure Synapse Analytics, es posible que deba incluir en la lista blanca su IP pública. Para ello, consulte la documentación [de](https://docs.microsoft.com/en-us/azure/sql-database/sql-database-firewall-configure#use-the-azure-portal-to-manage-server-level-ip-firewall-rules)Azure.

## Configuración del acceso a Snowflake {#configure-access-to-snowflake}

>[!NOTE]
>
>[!DNL Snowflake]El conector está disponible para implementaciones alojadas y on-premise. Para obtener más información, consulte [este artículo](https://helpx.adobe.com/es/campaign/kb/acc-on-prem-vs-hosted.html).

![](assets/snowflake_3.png)

### Cuenta externa Snowflake {#snowflake-external}

La cuenta externa [!DNL Snowflake] permite conectar la instancia de Campaign a la base de datos externa Snowflake.

1. En Campaign Classic, configure la [!DNL Snowflake] cuenta externa. En **[!UICONTROL Explorer]**, haga clic en **[!UICONTROL Administration]** / **[!UICONTROL Platform]** / **[!UICONTROL External accounts]**.

1. Seleccione la cuenta externa **[!UICONTROL Snowflake]** incorporada.

1. Configure la cuenta externa **[!UICONTROL Snowflake]**. Debe especificar:

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

1. En Campaign Classic, puede configurar la cuenta externa [!DNL Snowflake]. Para obtener más información sobre cómo configurar la cuenta externa, consulte esta [sección](../../platform/using/specific-configuration-database.md#snowflake-external).

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

1. En Campaign Classic, puede configurar la cuenta externa [!DNL Snowflake]. Para obtener más información sobre cómo configurar la cuenta externa, consulte esta [sección](../../platform/using/specific-configuration-database.md#snowflake-external).

### Snowflake en Windows {#snowflake-windows}

1. Descargue [el controlador ODBC para Windows](https://docs.snowflake.net/manuals/user-guide/odbc-download.html). Tenga en cuenta que necesita privilegios de administrador para instalar el controlador. Para obtener más información, consulte [esta página](https://docs.snowflake.net/manuals/user-guide/admin-user-management.html)

1. Configure el controlador ODBC. Para obtener más información, consulte [esta página](https://docs.snowflake.net/manuals/user-guide/odbc-windows.html#step-2-configure-the-odbc-driver)

1. En Campaign Classic, puede configurar la cuenta externa [!DNL Snowflake]. Para obtener más información sobre cómo configurar la cuenta externa, consulte esta [sección](../../platform/using/specific-configuration-database.md#snowflake-external).

## Configuración del acceso a Hadoop 3.0 {#configure-access-to-hadoop-3}

La conexión a una base de datos externa de Hadoop en FDA requiere las siguientes configuraciones en el servidor de Adobe Campaign. Tenga en cuenta que esta configuración está disponible tanto para Windows como para Linux.

1. Descargue los controladores ODBC para Hadoop en función de su versión del sistema operativo. Los controladores se encuentran en [esta página](https://www.cloudera.com/downloads.html).

1. A continuación, debe instalar los controladores ODBC y crear un DSN para la conexión de Hive. Las instrucciones se encuentran en [esta página](https://docs.cloudera.com/documentation/other/connectors/hive-odbc/2-6-5/Cloudera-ODBC-Driver-for-Apache-Hive-Install-Guide.pdf).

1. Después de descargar e instalar los controladores ODBC, debe reiniciar Campaign Classic. Para ello, ejecute el siguiente comando:

   ```
   systemctl stop nlserver.service
   systemctl start nlserver.service
   ```

1. En Campaign Classic, puede configurar la cuenta externa de Snowflake. En **[!UICONTROL Explorer]**, haga clic en **[!UICONTROL Administration]** / **[!UICONTROL Platform]** / **[!UICONTROL External accounts]**.

1. Haga clic en **[!UICONTROL Create]** y seleccione **[!UICONTROL External database]** como tipo de cuenta.

1. Para configurar la cuenta externa **[!UICONTROL  Hadoop]**, debe especificar:

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

## Configuración del acceso a Hadoop 2.1 {#configure-access-to-hadoop}

### Para Windows {#for-windows}

1. Instale controladores de [perspectiva de ODBC y Azure HD](https://www.microsoft.com/en-us/download/details.aspx?id=40886) para Windows.
1. Cree el DSN (Nombre de Fuente de Datos) ejecutando la herramienta ODBC DataSource Adminstrator. Se proporciona una muestra de DSN del sistema para Hive para que usted la modifique.

   ```
   Description: vorac (or any name you like)
   Host: vorac.azurehdinsight.net
   Port: 443
   Database: sm_tst611 (or your database name)
   Mechanism: Azure HDInsight Service
   User/Password: admin/<your password here>
   ```

1. Cree la cuenta externa de Hadoop como se detalla en la sección de [esta página](../../platform/using/external-accounts.md#hadoop-external-account).

### Para Linux {#for-linux}

1. Instale unixodbc para Linux.

   ```
   apt-get install unixodbc
   ```

1. Descargue e instale controladores ODBC para Apache Hive de HortonWorks: [https://www.hortonworks.com/downloads/](https://www.hortonworks.com/downloads/).

   ```
   dpkg -i hive-odbc-native_2.1.10.1014-2_amd64.deb
   ```

1. Compruebe la ubicación de los archivos ODBC.

   ```
   root@campadpac71:/tmp# odbcinst -j
   unixODBC 2.3.1
   DRIVERS............: /etc/odbcinst.ini
   SYSTEM DATA SOURCES: /etc/odbc.ini
   FILE DATA SOURCES..: /etc/ODBCDataSources
   USER DATA SOURCES..: /root/.odbc.ini
   SQLULEN Size.......: 8
   SQLLEN Size........: 8
   SQLSETPOSIROW Size.: 8
   ```

1. Cree el DSN (Nombre de la Fuente de Datos) y edite el archivo odbc.ini. A continuación, cree un DSN para su conexión Hive.

   A continuación se muestra un ejemplo de HDInsight para configurar una conexión denominada “viral”:

   ```
   [ODBC Data Sources]
   vorac 
   
   [vorac]
   Driver=/usr/lib/hive/lib/native/Linux-amd64-64/libhortonworkshiveodbc64.so
   HOST=vorac.azurehdinsight.net
   PORT=443
   Schema=sm_tst611
   HiveServerType=2
   AuthMech=6
   UID=admin
   PWD=<your password here>
   HTTPPath=
   UseNativeQuery=1
   ```

   >[!NOTE]
   >
   >El parámetro **UseNativeQuery** es muy importante. Campaign tiene en cuenta Hive y no funciona correctamente a menos que se configure UseNativeQuery. Normalmente, el controlador o el conector SQL de Hive reescribe las consultas y altera el orden de las columnas.

   La configuración de autenticación depende de la configuración de Hive/Hadoop. Por ejemplo, para HD Insight, utilice AuthMech=6 para la autenticación de usuario/contraseña, como se describe [aquí](https://www.simba.com/products/Spark/doc/ODBC_InstallGuide/unix/content/odbc/hi/configuring/authenticating/azuresvc.htm).

1. Exporte las variables.

   ```
   export ODBCINI=/etc/myodbc.ini
   export ODBCSYSINI=/etc/myodbcinst.ini
   ```

1. Configure controladores Hortonworks mediante /usr/lib/hive/lib/native/Linux-amd64-64/hortonworks.hiveodbc.ini.

   Debe utilizar UTF-16 para poder conectar con Campaign y unix-odbc (libodbcinst).

   ```
   [Driver]
   
   DriverManagerEncoding=UTF-16
   ErrorMessagesPath=/usr/lib/hive/lib/native/hiveodbc/ErrorMessages/
   LogLevel=0
   LogPath=/tmp/hive
   SwapFilePath=/tmp
   
   ODBCInstLib=libodbcinst.so
   ```

1. Ahora puede probar la conexión usando isql.

   ```
   isql vorac
   isql vorac -v
   ```

1. Cree la cuenta externa de Hadoop como se detalla en la sección de [esta página](../../platform/using/external-accounts.md#hadoop-external-account).

## Configuración del acceso a Netezza {#configure-access-to-netezza}

La conexión a una base de datos externa de Netezza en FDA requiere ciertas configuraciones adicionales en el servidor de Adobe Campaign:

1. Instale los controladores ODBC para Netezza según el sistema operativo que utilice:

   * **nz-linuxclient-v7.2.0.0.tar.gz para Linux.** Seleccione la carpeta correspondiente a su sistema operativo (linux o linux64) e inicie el comando descomprimir. Puede dejar que la instalación se realice en el repositorio que sugerido de forma predeterminada: &quot;/usr/local/nz&quot;.
   * **nz-winclient-v7.2.0.0.zip para Windows.** Descomprima el archivo e inicie la secuencia de comandos ejecutable correspondiente a su sistema operativo: nzodbcsetup.exe o nzodbcsetup64.exe. Siga las instrucciones del asistente para finalizar la instalación de los controladores.

1. Configure el controlador ODBC. La configuración se puede realizar en los archivos estándar: **/etc/odbc.ini** para obtener parámetros generales y **/etc/odbcinst.ini** para declarar controladores.

   * **/etc/odbc.ini**

      ```
      [ODBC]
      InstallDir=/etc/
      ```

      “InstallDir” corresponde a la ubicación del archivo odbcinst.ini.

   * **/etc/odbcinst.ini**

      ```
      [ODBC Drivers]
      NetezzaSQL = Installed
      
      [NetezzaSQL]
      Driver           = /usr/local/nz/lib/libnzsqlodbc3.so
      Setup            = /usr/local/nz/lib/libnzsqlodbc3.so
      APILevel         = 1
      ConnectFunctions = YYN
      Description      = Netezza ODBC driver
      DriverODBCVer    = 03.51
      DebugLogging     = false
      LogPath          = /tmp
      UnicodeTranslationOption = utf8
      CharacterTranslationOption = all
      PreFetch         = 256
      Socket           = 16384
      ```

1. Especifique las variables de entorno del servidor de Adobe Campaign:

   * **LD_LIBRARY_PATH**: /usr/local/nz/lib y /usr/local/nz/lib64. “/usr/local/nz” corresponde al repositorio de instalación ofrecido de forma predeterminada al instalar los controladores. Aquí debe especificar el repositorio que ha seleccionado para la instalación.
   * **ODBCINI**: ubicación del archivo odbc.ini (por ejemplo, /etc/odbc.ini).
   * **NZ_ODBC_INI_PATH**: ubicación del archivo odbc.ini. Netezza también requiere esta segunda variable para utilizar el archivo odbc.ini.

1. En Campaign Classic, puede configurar la cuenta externa de Netezza. En **[!UICONTROL Explorer]**, haga clic en **[!UICONTROL Administration]** / **[!UICONTROL Platform]** / **[!UICONTROL External accounts]**.

1. Haga clic en **[!UICONTROL New]** y seleccione **[!UICONTROL External database]** como **[!UICONTROL Type]**.

1. Para configurar la cuenta externa **[!UICONTROL Netezza]**, debe especificar:

   * **[!UICONTROL Type]**: Netezza

   * **[!UICONTROL Server]**: URL del servidor de Netezza

   * **[!UICONTROL Account]**: Nombre del usuario

   * **[!UICONTROL Password]**: Contraseña de la cuenta de usuario

   * **[!UICONTROL Database]**: Nombre de la base de datos

>[!NOTE]
>
>Las operaciones en los esquemas que contienen claves principales generadas automáticamente no se tienen en cuenta.
>
>La tabla utiliza la cláusula **Organize on** en el primer índice definido en el esquema. Dado que esta cláusula está limitada a entre 1 y 4 columnas con Netezza, este índice no puede contener más de 4 columnas.

## Configuración del acceso a Oracle {#configure-access-to-oracle}

La conexión a una base de datos externa de Oracle en FDA requiere ciertas configuraciones adicionales en el servidor de Adobe Campaign.

### Para Linux {#for-linux-1}

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

### Para Windows {#for-windows-1}

1. Instale el cliente Oracle.
1. En la carpeta C:\Oracle, cree un archivo **tnsnames.ora** con la definición de TNS.

   Añada una variable de entorno TNS_ADMIN con C:\Oracle como valor y reinicie el equipo.

## Configuración del acceso a Sybase IQ {#configure-access-to-sybase-iq}

La conexión a una base de datos externa de Sybase IQ en FDA requiere determinadas configuraciones adicionales en el servidor de Adobe Campaign:

1. Asegúrese de que el paquete unixodbc está en el servidor.
1. Instale **iq_odbc**. Se puede producir un error al final de la instalación. Puede ignorar este error.
1. Instale **iq_client_common**. Puede producirse un error de Java al final de la instalación. Puede ignorar este error.
1. Configure el controlador ODBC. La configuración se puede realizar en los archivos estándar: /etc/odbc.ini para obtener parámetros generales y /etc/odbcinst.ini para declarar controladores:

   * **/etc/odbc.ini** (reemplace valores como`<server_alias>` por sus propios valores):

      ```
      [ODBC Data Sources]
      <server_alias>=libdbodbc.so
      
      [<server_alias>]
      Driver=/opt/sybase/IQ-16_0/lib64/libdbodbc16.so
      Description=<description>
      Username=<username>
      Password=<password>
      ServerName=<server_name>
      CommLinks=tcpip(host=<host>)
      ```

   * **/etc/odbcinst.ini**

      ```
      [ODBC DRIVERS]
      SAP SybaseIQ=Installed
      
      [SAP SybaseIQ]
      Driver=/opt/sybase/IQ-16_0/lib64/libdbodbc16.so
      ```

1. Añada la ruta para la nueva biblioteca libodbc16.so en la variable LD_LIBRARY_PATH. Para ello:

   * Si utiliza un archivo customer.sh para declarar la ruta: añada la ruta /opt/sybase/IQ-16_0/lib64 para la variable LD_LIBRARY_PATH.
   * En caso contrario, utilice un comando Unix.

1. En Campaign Classic, puede configurar la cuenta externa Sybase IQ. En **[!UICONTROL Explorer]**, haga clic en **[!UICONTROL Administration]** / **[!UICONTROL Platform]** / **[!UICONTROL External accounts]**.

1. Haga clic en **[!UICONTROL New]** y seleccione **[!UICONTROL External database]** como **[!UICONTROL Type]**.

1. Para configurar la cuenta externa **[!UICONTROL Sybase IQ]**, debe especificar:

   * **[!UICONTROL Type]**: ODBC (Sybase ASE, Sybase IQ)

   * **[!UICONTROL Server]**: corresponde a la conexión ODBC (`<server_alias>`) definida en el paso 5. No es necesariamente el nombre del servidor.

   * **[!UICONTROL Account]**: Nombre del usuario

   * **[!UICONTROL Password]**: Contraseña de la cuenta de usuario

   * **[!UICONTROL Database]**: Nombre de la base de datos

>[!NOTE]
>
>Para Windows, debe instalar el cliente de Sybase IQ en el servidor de Adobe Campaign y crear una conexión ODBC. Asegúrese de crear una fuente de datos del sistema cuando el servidor Adobe Campaign (nlserver) se esté ejecutando como un servicio en Windows.

## Configuración del acceso a Teradata {#configure-access-to-teradata}

La conexión a una base de datos externa de Teradata en FDA requiere ciertas configuraciones adicionales en el servidor de Adobe Campaign. Para obtener más información sobre cómo configurar la base de datos Teradata, consulte este [artículo](https://helpx.adobe.com/es/campaign/kb/campaign_fda_teradata.html).

1. Instale [el controlador ODBC para Teradata](https://downloads.teradata.com/download/connectivity/odbc-driver/linux).

   Se compone de tres paquetes que pueden instalarse en Red Hat (o CentOS)/Suse en el siguiente orden:

   * TeraGSS
   * tdicu1510 (instálelo con setup_wrapper.sh)
   * tdodbc1510 (install it using setup_wrapper.sh)

1. Configure el controlador ODBC. La configuración se puede realizar en los archivos estándar: **/etc/odbc.ini** para obtener parámetros generales y /etc/odbcinst.ini para declarar controladores:

   * **/etc/odbc.ini**

      ```
      [ODBC]
      InstallDir=/etc/
      ```

      “InstallDir” corresponde a la ubicación del archivo **odbcinst.ini**.

   * **/etc/odbcinst.ini**

      ```
      [ODBC DRIVERS]
      teradata=Installed
      
      [teradata]
      Driver=/opt/teradata/client/15.10/lib64/tdata.so
      APILevel=CORE
      ConnectFunctions=YYY
      DriverODBCVer=3.51
      SQLLevel=1
      ```

1. Especifique las variables de entorno del servidor de Adobe Campaign:

   * **LD_LIBRARY_PATH**: /opt/teradata/client/15.10/lib64 and /opt/teradata/client/15.10/odbc_64/lib.
   * **ODBCINI**: ubicación del archivo odbc.ini (por ejemplo, /etc/odbc.ini).
   * **NLSPATH: ubicación del archivo opermsgs.cat (/opt/teradata/client/15.10/msg/opermsgs.cat)**

1. En Campaign Classic, puede configurar la cuenta externa Teradata. En **[!UICONTROL Explorer]**, haga clic en **[!UICONTROL Administration]** / **[!UICONTROL Platform]** / **[!UICONTROL External accounts]**.

1. Haga clic en **[!UICONTROL New]** y seleccione **[!UICONTROL External database]** como **[!UICONTROL Type]**.

1. Para configurar la cuenta externa **[!UICONTROL Teradata]**, debe especificar:

   * **[!UICONTROL Type]**: Teradata

   * **[!UICONTROL Server]**: URL del servidor Teradata

   * **[!UICONTROL Account]**: Nombre del usuario

   * **[!UICONTROL Password]**: Contraseña de la cuenta de usuario

   * **[!UICONTROL Database]**: Nombre de la base de datos

## Configuración de acceso a SAP HANA {#configure-access-to-sap-hana}

La conexión a una base de datos externa de SAP HANA en FDA requiere determinadas configuraciones adicionales en el servidor de Adobe Campaign:

1. Instale los controladores ODBC para SAP HANA según el sistema operativo que utilice:

   * **hdb_client_linux.tgz para Linux.** Una vez descomprimido, inicie el comando hdbinst y siga las instrucciones para finalizar la instalación de los controladores.
   * **hdb_client_windows.zip para Windows.** Descomprima el archivo e inicie el archivo ejecutable: **hdbinst.exe**. Siga las instrucciones del asistente para finalizar la instalación de los controladores.

1. Configure el controlador ODBC. La configuración se puede realizar en los archivos estándar: /etc/odbc.ini para obtener parámetros generales y /etc/odbcinst.ini para declarar controladores.

   * **/etc/odbc.ini**

      ```
      [ODBC]
      InstallDir=/etc/
      
      [HDB]
      Driver=HDBODBC
      servernode=localhost:39013 (this value depend of your server)
      User:SYSTEM
      ```

      “InstallDir” corresponde a la ubicación del archivo **odbcinst.ini**.

   * **/etc/odbcinst.ini**

      ```
      [HDBODBC]
      Description = "SmartCloudPT HANA"
      Driver = /usr/sap/hdbclient/libodbcHDB.so
      ```

1. Especifique las variables de entorno del servidor de Adobe Campaign:

   * **LD_LIBRARY_PATH**: Debe incluir el enlace a su cliente de SAP Hana (/usr/sap/hdbclient/libodbcHDB.so) de forma predeterminada).
   * **ODBCINI**: ubicación del archivo odbc.ini (por ejemplo, /etc/odbc.ini).

1. En Campaign Classic, puede configurar la cuenta externa SAP Hana. En **[!UICONTROL Explorer]**, haga clic en **[!UICONTROL Administration]** / **[!UICONTROL Platform]** / **[!UICONTROL External accounts]**.

1. Haga clic en **[!UICONTROL New]** y seleccione **[!UICONTROL External database]** como **[!UICONTROL Type]**.

1. Para configurar la cuenta externa **[!UICONTROL SAP Hana]**, debe especificar:

   * **[!UICONTROL Type]**: SAP Hana

   * **[!UICONTROL Server]**: URL del servidor SAP Hana

   * **[!UICONTROL Account]**: Nombre del usuario

   * **[!UICONTROL Password]**: Contraseña de la cuenta de usuario
