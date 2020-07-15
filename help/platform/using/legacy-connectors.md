---
title: Conectores heredados
seo-title: Conectores heredados
description: Conectores heredados
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
source-wordcount: '1233'
ht-degree: 97%

---


# Conectores heredados {#legacy-connectors}

Los conectores FDA heredados siguen siendo compatibles con Adobe. Sin embargo, recomendamos reemplazarlos con alternativas más recientes enumeradas en esta [página](../../platform/using/specific-configuration-database.md).

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

La conexión a una base de datos externa de Teradata en FDA requiere ciertas configuraciones adicionales en el servidor de Adobe Campaign. For more information on how to configure your Teradata database, refer to this [page](../../platform/using/appendices-fda.md#teradata-configuration).

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
