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
source-git-commit: a0698ad55afb391bdc652a00b43b20df6fb9851b

---


# Configuraciones específicas por tipo de base de datos {#specific-configurations-by-database-type}

En función de las bases de datos externas a las que desee tener acceso desde Adobe Campaign, debe realizar determinadas configuraciones específicas. Estas configuraciones implican esencialmente la instalación de controladores y la declaración de variables de entorno que pertenecen a cada RDBMS en el servidor de Adobe Campaign.

Como regla general, debe instalar la capa del cliente correspondiente en la base de datos externa en el servidor de Adobe Campaign.

>[!NOTE]
>
>Las versiones compatibles se enumeran en la [Matriz de compatibilidad de Campaign](https://helpx.adobe.com/campaign/kb/compatibility-matrix.html#FederatedDataAccessFDA).

<!--
## Configure access to Azure Synapse {#configure-access-to-azure-synapse}

### Azure Synapse on CentOS {#azure-centos}

1. Download mysql57-community-release.noarch.rpm. You can find it in this [page](https://dev.mysql.com/downloads/repo/yum).

1. Install the client library:

    ```
    $ yum install mysql57-community-release-el7-9.noarch.rpm
    $ yum install mysql-community-libs
    ```

1. You now need to configure the external account. In Campaign Classic, unfold the **[!UICONTROL Platform]** menu and click **[!UICONTROL External accounts]**.

1. Select the out-of-the box **[!UICONTROL Azure Synapse]** external account.

1. To configure the **[!UICONTROL Azure Synapse]** external account:

    * **[!UICONTROL Server]**
  
      URL of the Azure Synapse server.

    * **[!UICONTROL Account]**

      Name of the user.

    * **[!UICONTROL Password]**

      User account password.

    * **[!UICONTROL Database]**

      Name of your database

    >[!NOTE]
    >
    >Make sure the **[!UICONTROL Time zone]** and **[!UICONTROL Unicode data]** are set according to your database.

### Azure Synapse on Debian {#azure-debian}

1. Download mysql-apt-config.deb. You can find it in this [page](https://dev.mysql.com/doc/mysql-apt-repo-quick-guide/en).

1. Install the client library:

    ```
    $ dpkg -i mysql-apt-config_*_all.deb # choose mysql-5.7 in the configuration menu
    $ apt update
    $ apt install libmysqlclient20
    ```

1. You now need to configure the external account. In Campaign Classic, unfold the **[!UICONTROL Platform]** menu and click **[!UICONTROL External accounts]**.

1. Select the out-of-the box **[!UICONTROL Azure Synapse]** external account.

1. To configure the **[!UICONTROL Azure Synapse]** external account:

    * **[!UICONTROL Server]**
  
      URL of the Azure Synapse server.

    * **[!UICONTROL Account]**

      Name of the user.

    * **[!UICONTROL Password]**

      User account password.

    * **[!UICONTROL Database]**

      Name of your database

    >[!NOTE]
    >
    >Make sure the **[!UICONTROL Time zone]** and **[!UICONTROL Unicode data]** are set according to your database.

### Azure Synapse on Windows {#azure-windows}

1. Download the C connector. You can find it in this [page](https://dev.mysql.com/downloads/connector/c).

1. Make sure the directory that contains libmysqlclient.dll is added to the PATH environment variable that nlserver will use.

1. You now need to configure the external account. In Campaign Classic, unfold the **[!UICONTROL Platform]** menu and click **[!UICONTROL External accounts]**.

1. You now need to configure the external account. In Campaign Classic, unfold the **[!UICONTROL Platform]** menu and click **[!UICONTROL External accounts]**.

1. Select the out-of-the box **[!UICONTROL Azure Synapse]** external account.

1. To configure the **[!UICONTROL Azure Synapse]** external account:

    * **[!UICONTROL Server]**
  
      URL of the Azure Synapse server.

    * **[!UICONTROL Account]**

      Name of the user.

    * **[!UICONTROL Password]**

      User account password.

    * **[!UICONTROL Database]**

      Name of your database

    >[!NOTE]
    >
    >Make sure the **[!UICONTROL Time zone]** and **[!UICONTROL Unicode data]** are set according to your database.

-->

## Configurar el acceso a Snowflake {#configure-access-to-snowflake}

>[!NOTE]
>
>El conector Snowflake está disponible para implementaciones alojadas y locales. Para obtener más información, consulte [esta página](https://helpx.adobe.com/campaign/kb/acc-on-prem-vs-hosted.html).

![](assets/snowflake_3.png)

### Copo de nieve en CentOS {#snowflake-centos}

1. Descargue los controladores ODBC para Snowflake. Los conductores de Snowflake pueden encontrarse [aquí](https://sfc-repo.snowflakecomputing.com/odbc/linux/latest/snowflake-odbc-2.20.2.x86_64.rpm).

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

1. En Campaign Classic, configure su cuenta externa de copo de nieve en Campaign Classic. En el **[!UICONTROL Explorer]**, despliegue el **[!UICONTROL Administration]** menú.

1. Abra el **[!UICONTROL Platform]** menú y haga clic en **[!UICONTROL External accounts]**.

1. Seleccione la cuenta externa predeterminada **[!UICONTROL Snowflake]** .

1. To configure the **[!UICONTROL Snowflake]** external account:

   * **[!UICONTROL Server]**

      URL del servidor Snowflake.

   * **[!UICONTROL Account]**

      Nombre del usuario.

   * **[!UICONTROL Password]**

      Contraseña de la cuenta de usuario.

   * **[!UICONTROL Database]**

      Nombre de la base de datos.
   ![](assets/snowflake.png)

1. Haga clic en la **[!UICONTROL Parameters]** ficha y, a continuación, en el **[!UICONTROL Deploy function]** botón para crear funciones.

   ![](assets/snowflake_2.png)

El conector admite las siguientes opciones:

| Opción | Valor | Descripción |
|---|---|---|
| esquema de trabajo |  | Esquema de base de datos que se va a utilizar para tablas de trabajo |
| almacén |  | Nombre del almacén predeterminado que se va a utilizar. Anulará el valor predeterminado del usuario. |
| TimeZoneName |  | De forma predeterminada, vacío, lo que significa que se utiliza la zona horaria del sistema del servidor de aplicaciones de Campaign Classic. La opción se puede utilizar para forzar el parámetro de sesión TIMEZONE. <br>[Para obtener más información, consulte esta página](https://docs.snowflake.net/manuals/sql-reference/parameters.html#timezone). |
| WeekStart | 0, 1-7 | De forma predeterminada, se establece en 0. (parámetro de sesión WEEK_START) <br>Para obtener más información sobre esto, consulte esta [página](https://docs.snowflake.net/manuals/sql-reference/parameters.html#week-start). |
| UseCachedResult | TRUE/FALSE | De forma predeterminada, se establece en TRUE. Esta opción se puede utilizar para deshabilitar los resultados en caché de Copo de nieve (parámetro de sesión USE_CACHED_RESULTS) <br>Para obtener más información sobre esto, consulte esta [página](https://docs.snowflake.net/manuals/user-guide/querying-persisted-results.html). |

### Snowflake en Debian {#snowflake-debian}

1. Descargue los controladores ODBC para Snowflake. Los conductores de Snowflake pueden encontrarse [aquí](https://sfc-repo.snowflakecomputing.com/odbc/linux/latest/index.html).

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

1. En Campaign Classic, configure su cuenta externa de copo de nieve en Campaign Classic. En el **[!UICONTROL Explorer]**, despliegue el **[!UICONTROL Administration]** menú.

1. Abra el **[!UICONTROL Platform]** menú y haga clic en **[!UICONTROL External accounts]**.

1. Seleccione la cuenta externa predeterminada **[!UICONTROL Snowflake]** .

1. To configure the **[!UICONTROL Snowflake]** external account:

   * **[!UICONTROL Server]**

      URL del servidor Snowflake.

   * **[!UICONTROL Account]**

      Nombre del usuario.

   * **[!UICONTROL Password]**

      Contraseña de la cuenta de usuario.

   * **[!UICONTROL Database]**

      Nombre de la base de datos
   ![](assets/snowflake.png)

1. Haga clic en la **[!UICONTROL Parameters]** ficha y, a continuación, en el **[!UICONTROL Deploy function]** botón para crear funciones.

   ![](assets/snowflake_2.png)

El conector admite las siguientes opciones:

| Opción | Valor | Descripción |
|---|---|---|
| esquema de trabajo |   | Esquema de base de datos que se va a utilizar para tablas de trabajo |
| almacén |   | Nombre del almacén predeterminado que se va a utilizar. Anulará el valor predeterminado del usuario. |
| TimeZoneName |   | De forma predeterminada, vacío, lo que significa que se utiliza la zona horaria del sistema del servidor de aplicaciones de Campaign Classic. La opción se puede utilizar para forzar el parámetro de sesión TIMEZONE. <br>[Para obtener más información, consulte esta página](https://docs.snowflake.net/manuals/sql-reference/parameters.html#timezone). |
| WeekStart | 0, 1-7 | De forma predeterminada, se establece en 0. (parámetro de sesión WEEK_START) <br>Para obtener más información sobre esto, consulte esta [página](https://docs.snowflake.net/manuals/sql-reference/parameters.html#week-start). |
| UseCachedResult | TRUE/FALSE | De forma predeterminada, se establece en TRUE. Esta opción se puede utilizar para deshabilitar los resultados en caché de Copo de nieve (parámetro de sesión USE_CACHED_RESULTS) <br>Para obtener más información sobre esto, consulte esta [página](https://docs.snowflake.net/manuals/user-guide/querying-persisted-results.html). |

### Copo de nieve en Windows {#snowflake-windows}

1. Descargue el controlador [ODBC para Windows](https://docs.snowflake.net/manuals/user-guide/odbc-download.html). Tenga en cuenta que necesita privilegios de administrador para instalar el controlador. Para obtener más información, consulte [esta página](https://docs.snowflake.net/manuals/user-guide/admin-user-management.html)

1. Configure el controlador ODBC. Para obtener más información, consulte [esta página](https://docs.snowflake.net/manuals/user-guide/odbc-windows.html#step-2-configure-the-odbc-driver)

1. Una vez que el controlador ODBC se haya instalado y configurado, deberá configurar su cuenta externa de Copo de nieve en Campaign Classic. En el **[!UICONTROL Explorer]**, despliegue el **[!UICONTROL Administration]** menú.

1. Abra el **[!UICONTROL Platform]** menú y haga clic en **[!UICONTROL External accounts]**.

1. Seleccione la cuenta externa predeterminada **[!UICONTROL Snowflake]** .

1. To configure the **[!UICONTROL Snowflake]** external account:

   * **[!UICONTROL Server]**

      URL del servidor Snowflake.

   * **[!UICONTROL Account]**

      Nombre del usuario.

   * **[!UICONTROL Password]**

      Contraseña de la cuenta de usuario.

   * **[!UICONTROL Database]**

      Nombre de la base de datos
   ![](assets/snowflake.png)

1. Haga clic en la **[!UICONTROL Parameters]** ficha y, a continuación, en el **[!UICONTROL Deploy function]** botón para crear funciones.

   ![](assets/snowflake_2.png)

El conector admite las siguientes opciones:

| Opción | Valor | Descripción |
|---|---|---|
| esquema de trabajo |   | Esquema de base de datos que se va a utilizar para tablas de trabajo |
| almacén |   | Nombre del almacén predeterminado que se va a utilizar. Anulará el valor predeterminado del usuario. |
| TimeZoneName |   | De forma predeterminada, vacío, lo que significa que se utiliza la zona horaria del sistema del servidor de aplicaciones de Campaign Classic. La opción se puede utilizar para forzar el parámetro de sesión TIMEZONE. <br>[Para obtener más información, consulte esta página](https://docs.snowflake.net/manuals/sql-reference/parameters.html#timezone). |
| WeekStart | 0, 1-7 | De forma predeterminada, se establece en 0. (parámetro de sesión WEEK_START) <br>Para obtener más información sobre esto, consulte esta [página](https://docs.snowflake.net/manuals/sql-reference/parameters.html#week-start). |
| UseCachedResult | TRUE/FALSE | De forma predeterminada, se establece en TRUE. Esta opción se puede utilizar para deshabilitar los resultados en caché de Copo de nieve (parámetro de sesión USE_CACHED_RESULTS) <br>Para obtener más información sobre esto, consulte esta [página](https://docs.snowflake.net/manuals/user-guide/querying-persisted-results.html). |

## Configure access to Hadoop 3.0 {#configure-access-to-hadoop-3}

La conexión a una base de datos externa Hadoop en FDA requiere las siguientes configuraciones en el servidor de Adobe Campaign. Tenga en cuenta que esta configuración está disponible tanto para Windows como para Linux.

1. Descargue los controladores ODBC para Hadoop en función de su versión del sistema operativo. Se pueden encontrar controladores en esta [página](https://www.cloudera.com/downloads.html).

1. A continuación, debe instalar los controladores ODBC y crear un DSN para la conexión de Hive. Las instrucciones se pueden encontrar [aquí](https://docs.cloudera.com/documentation/other/connectors/hive-odbc/2-6-5/Cloudera-ODBC-Driver-for-Apache-Hive-Install-Guide.pdf)

1. Después de descargar e instalar los controladores ODBC, debe reiniciar Campaign Classic. Para ello, ejecute el siguiente comando:

   ```
   systemctl stop nlserver.service
   systemctl start nlserver.service
   ```

1. En Campaign Classic, configure su cuenta externa de Hadoop en Campaign Classic. En el **[!UICONTROL Explorer]**, despliegue el **[!UICONTROL Administration]** menú.

1. Abra el **[!UICONTROL Platform]** menú y haga clic en **[!UICONTROL External accounts]**.

1. Haga clic **[!UICONTROL Create]** y seleccione **[!UICONTROL External database]** como tipo de cuenta.

1. To configure the **[!UICONTROL  Hadoop]** external account:

   * **[!UICONTROL Type]**

      ODBC (Sybase ASE, Sybase IQ)

   * **[!UICONTROL Server]**

      Nombre del DNS.

   * **[!UICONTROL Account]**

      Nombre del usuario.

   * **[!UICONTROL Password]**

      Contraseña de la cuenta de usuario.

   * **[!UICONTROL Database]**

      Nombre de la base de datos si no se especifica en DSN. Se puede dejar vacío si se especifica en el DSN.

   * **[!UICONTROL Time zone]**

      Zona horaria del servidor
   ![](assets/hadoop3.png)

El conector admite las siguientes opciones de ODBC:

| Name | Valor |
|---|---|
| ODBCMgr | iODBC |
| almacén | 1/2/4 |

El conector también admite las siguientes opciones de Hive:

| Name | Valor | Descripción |
|---|---|---|
| globalKey | Clave de acceso de Azure blob o DataLake | Para wasb:// o wasbs:// cargadores masivos (es decir, si la herramienta de carga masiva comienza con wasb:// o wasbs://). <br>Es la clave de acceso para blob o el bloque DataLake para la carga masiva. |
| hdfsPort | número de puerto <br>establecido de forma predeterminada en 8020 | Para la carga masiva de HDFS (es decir, si la herramienta de carga masiva comienza con webhdfs:// o webhdfss://). |
| bucketNumber | 20 | Número de bloques al crear una tabla agrupada. |
| fileFormat | PARQUÉ | Formato de archivo predeterminado para tablas de trabajo. |

## Configure access to Hadoop 2.1 {#configure-access-to-hadoop}

For more information on how to configure your Hadoop external database in FDA, refer to this [article](https://helpx.adobe.com/campaign/kb/access-hadoop-2.html).

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

1. Cree la cuenta externa de Hadoop, tal como se detalla en la sección [Creación de una conexión](#creating-a-shared-connection) compartida.

### Para Linux {#for-linux}

1. Instale unixodbc para Linux.

   ```
   apt-get install unixodbc
   ```

1. Download and install ODBC drivers for Apache Hive from HortonWorks: [https://www.hortonworks.com/downloads/](https://www.hortonworks.com/downloads/).

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

   La configuración de autenticación depende de la configuración de Hive/Hadoop. Por ejemplo, para HD Insight, utilice AuthMech=6 para la autenticación de usuario/contraseña, como se describe [aquí](http://www.simba.com/products/Spark/doc/ODBC_InstallGuide/unix/content/odbc/hi/configuring/authenticating/azuresvc.htm).

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

1. Cree la cuenta externa de Hadoop, tal como se detalla en la sección [Creación de una conexión](#creating-a-shared-connection) compartida.

## Configuración del acceso a Netezza {#configure-access-to-netezza}

La conexión a una base de datos externa de Netezza en FDA requiere ciertas configuraciones adicionales en el servidor de Adobe Campaign:

1. Instale los controladores ODBC para Netezza según el sistema operativo que utilice:

   * **nz-linuxclient-v7.2.0.0.tar.gz para Linux.** Seleccione la carpeta correspondiente a su sistema operativo (linux o linux64) e inicie el comando descomprimir. Puede dejar que la instalación se realice en el repositorio que se sugiere de forma predeterminada: &quot;/usr/local/nz&quot;.
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

1. Cree la cuenta externa de Netezza, tal como se detalla en la sección [Creación de una conexión](#creating-a-shared-connection) compartida.

>[!NOTE]
>
>Las operaciones en los esquemas que contienen claves principales generadas automáticamente no se tienen en cuenta.
>
>La tabla utiliza la cláusula **Organize on** en el primer índice definido en el esquema. Dado que esta cláusula está limitada a entre 1 y 4 columnas con Netezza, este índice no puede contener más de 4 columnas.

## Configuración del acceso a Oracle {#configure-access-to-oracle}

La conexión a una base de datos externa de Oracle en FDA requiere ciertas configuraciones adicionales en el servidor de Adobe Campaign.

### Para Linux {#for-linux-1}

1. Instale el cliente completo Oracle correspondiente a su versión de Oracle.
1. Añada sus definiciones de TNS a la instalación. To do this, specify them in a **tnsnames.ora** file in the /etc/oracle repository. Si este repositorio no existe, créelo.

   A continuación, cree una nueva variable de entorno TNS_ADMIN: exporte TNS_ADMIN=/etc/oracle y reinicie el equipo.

1. Integre Oracle en el servidor de Adobe Campaign (nlserver). To do this, check that the **customer.sh** file is present in the &quot;nl6&quot; folder of the Adobe Campaign server tree structure and that it includes the links to the Oracle libraries.

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
1. In the C:Oracle folder, create a **tnsnames.ora** file containing your TNS definition.

   Agregue una variable de entorno TNS_ADMIN con C:Oracle como valor y reinicie el equipo.

## Configuración del acceso a Sybase IQ {#configure-access-to-sybase-iq}

La conexión a una base de datos externa de Sybase IQ en FDA requiere determinadas configuraciones adicionales en el servidor de Adobe Campaign:

1. Asegúrese de que el paquete unixodbc está en el servidor.
1. Instale **iq_odbc**. Se puede producir un error al final de la instalación. Puede ignorar este error.
1. Instale **iq_client_common**. Puede producirse un error de Java al final de la instalación. Puede ignorar este error.
1. Configure el controlador ODBC. La configuración se puede realizar en los archivos estándar: /etc/odbc.ini para obtener parámetros generales y /etc/odbcinst.ini para declarar controladores:

   * **/etc/odbc.ini** (reemplace valores como `<server_alias>` caracteres por el suyo propio):

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

1. Cree una nueva cuenta externa de la FDA, tal como se describe en la sección [Creación de una conexión](#creating-a-shared-connection) compartida. For Sybase IQ, the server name corresponds to the ODBC connection (`<server_alias>`) defined in step 5. No es necesariamente el nombre del servidor.

>[!NOTE]
>
>Para Windows, debe instalar el cliente de Sybase IQ en el servidor de Adobe Campaign y crear una conexión ODBC. Asegúrese de crear un origen de datos del sistema cuando el servidor de Adobe Campaign (nlserver) se esté ejecutando como un servicio en Windows.

## Configuración del acceso a Teradata {#configure-access-to-teradata}

La conexión a una base de datos externa de Teradata en FDA requiere ciertas configuraciones adicionales en el servidor de Adobe Campaign. Para obtener más información sobre cómo configurar la base de datos Teradata, consulte este [artículo](https://helpx.adobe.com/campaign/kb/campaign_fda_teradata.html).

1. Instale [el controlador ODBC para Teradata](http://downloads.teradata.com/download/connectivity/odbc-driver/linux).

   Se compone de tres paquetes que pueden instalarse en Red Hat (o CentOS)/Suse en el siguiente orden:

   * TeraGSS
   * tdicu1510 (instálelo con setup_wrapper.sh)
   * tdodbc1510 (instálelo con setup_wrapper.sh)

1. Configure el controlador ODBC. La configuración se puede realizar en los archivos estándar: **/etc/odbc.ini** para obtener parámetros generales y /etc/odbcinst.ini para declarar controladores:

   * **/etc/odbc.ini**

      ```
      [ODBC]
      InstallDir=/etc/
      ```

      &quot;InstallDir&quot; corresponds to the location of the **odbcinst.ini** file.

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

   * **LD_LIBRARY_PATH**: /opt/teradata/client/15.10/lib64 y /opt/teradata/client/15.10/odbc_64/lib.
   * **ODBCINI**: ubicación del archivo odbc.ini (por ejemplo, /etc/odbc.ini).
   * **NLSPATH**: ubicación del archivo opermsgs.cat (/opt/teradata/client/15.10/msg/opermsgs.cat)

## Configuración de acceso a SAP HANA {#configure-access-to-sap-hana}

La conexión a una base de datos externa de SAP HANA en FDA requiere determinadas configuraciones adicionales en el servidor de Adobe Campaign:

1. Instale los controladores ODBC para SAP HANA según el sistema operativo que utilice:

   * **hdb_client_linux.tgz para Linux.** Una vez descomprimido, inicie el comando hdbinst y siga las instrucciones para finalizar la instalación de los controladores.
   * **hdb_client_windows.zip para Windows.** Unzip the file and start the executable: **hdbinst.exe**. Siga las instrucciones del asistente para finalizar la instalación de los controladores.

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

      &quot;InstallDir&quot; corresponds to the location of the **odbcinst.ini** file.

   * **/etc/odbcinst.ini**

      ```
      [HDBODBC]
      Description = "SmartCloudPT HANA"
      Driver = /usr/sap/hdbclient/libodbcHDB.so
      ```

1. Especifique las variables de entorno del servidor de Adobe Campaign:

   * **LD_LIBRARY_PATH**: Debe incluir el vínculo a su cliente SAP Hana (/usr/sap/hdbclient/libodbcHDB.so) de forma predeterminada.
   * **ODBCINI**: ubicación del archivo odbc.ini (por ejemplo, /etc/odbc.ini).

1. Cree la cuenta externa de SAP Hana, tal como se detalla en la sección [Creación de una conexión](#creating-a-shared-connection) compartida.
