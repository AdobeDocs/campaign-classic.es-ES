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
source-git-commit: 209ac4d81d2d27c264ee6b288bcb7fcb1900ffc5

---


# Acceso a una base de datos externa{#accessing-an-external-database}

## Acerca del Acceso a Datos Federados {#about-federated-data-access}

Adobe Campaign proporciona la opción **Acceso de Datos Federados** (FDA) para procesar la información almacenada en una o más bases de datos externas: puede acceder a datos externos sin cambiar la estructura de los datos de Adobe Campaign.

>[!CAUTION]
>
>El módulo de **Acceso a Datos Federados** (FDA) es opcional. Compruebe el acuerdo de licencia de Adobe Campaign.
>  
>Además, el acceso a una base de datos externa mediante FDA solo es posible para instalaciones locales o híbridas.

### Principio de funcionamiento {#operating-principle}

La opción FDA permite recopilar datos de las fuentes SQL y detectar automáticamente la estructura de las tablas de objetivo.

Para utilizar esta función, tiene que:

1. Poseer una base de datos externa compatible con el módulo FDA de Adobe Campaign. La lista de sistemas de bases de datos y versiones compatibles se detalla en la [matriz de compatibilidad](https://helpx.adobe.com/campaign/kb/compatibility-matrix.html). Los usuarios también deben tener los [permisos necesarios](#remote-database-access-rights) en Adobe Campaign y en la base de datos externa.
1. [Instalar los controladores](#specific-configurations-by-database-type) correspondientes a su base de datos en el servidor de Adobe Campaign.
1. [Crear y configurar una cuenta externa](#connecting-to-the-database) que permita establecer la conexión entre Adobe Campaign y la base de datos externa. Para obtener más información sobre las cuentas externas disponibles, consulte esta [página](../../platform/using/external-accounts.md).
1. [Crear el esquema de lectura](#creating-the-data-schema) de la base de datos externa en Adobe Campaign. Esto permite reconocer la estructura de datos de la base de datos externa.
1. Finalmente, [crear una nueva asignación de objetivo](#defining-data-mapping) desde el esquema creado anteriormente, en caso de que los destinatarios de los envíos provengan de la base de datos externa. Esto presenta ciertas limitaciones, especialmente en relación con la personalización de los envíos.

Una vez que se haya creado el esquema de lectura de datos, los datos se pueden procesar en los flujos de trabajo de Adobe Campaign. Para obtener más información, consulte [esta sección](../../workflow/using/executing-a-workflow.md#architecture).

### Buenas prácticas y recomendaciones {#best-practices-and-recommendations}

La opción FDA se realiza para manipular los datos en bases de datos externas en modo de lote en los flujos de trabajo. El uso de FDA en otro contexto, por ejemplo para las operaciones unitarias, se debe llevar a cabo con precaución (personalización, interacción, envíos en tiempo real, etc.).

Antes de comenzar a aprovechar la base de datos externa, realice pruebas de rendimiento para detectar posibles problemas y optimizar en función de esta opción.

Evite en la medida de lo posible las operaciones que requieran utilizar tanto Adobe Campaign como la base de datos externa. Para ello, puede hacer lo siguiente:

* Exporte la base de datos de Adobe Campaign a la base de datos externa y ejecute las operaciones solo desde la base de datos externa antes de volver a importar los resultados en Adobe Campaign.
* Recopile los datos de la base de datos externa de Adobe Campaign y ejecute las operaciones localmente.

Si desea personalizar los envíos utilizando datos de la base de datos externa, recopile los datos para utilizarlos en un flujo de trabajo para que estén disponibles en una tabla temporal. A continuación, utilice los datos de la tabla temporal para personalizar su envío.

### Limitaciones {#limitations}

La opción FDA está sujeta a la limitación del sistema externo de base de datos que utiliza.

Por motivos de rendimiento, no se recomienda utilizar esta funcionalidad para llevar a cabo operaciones unitarias (personalización de entrega, módulo de interacción, tiempo real).

## Configuraciones específicas por tipo de base de datos {#specific-configurations-by-database-type}

En función de las bases de datos externas a las que desee tener acceso desde Adobe Campaign, debe realizar determinadas configuraciones específicas. Estas configuraciones implican esencialmente la instalación de controladores y la declaración de variables de entorno que pertenecen a cada RDBMS en el servidor de Adobe Campaign.

Como regla general, debe instalar la capa del cliente correspondiente en la base de datos externa en el servidor de Adobe Campaign.

>[!NOTE]
>
>Las versiones compatibles se enumeran en la [Matriz de compatibilidad de Campaign](https://helpx.adobe.com/campaign/kb/compatibility-matrix.html#FederatedDataAccessFDA) .

### Configuración del acceso a Hadoop {#configure-access-to-hadoop}

La conexión a una base de datos externa de Hadoop en FDA requiere las siguientes configuraciones en el servidor de Adobe Campaign.

#### Para Windows {#for-windows}

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

#### Para Linux {#for-linux}

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

### Configuración del acceso a MySQL {#configure-access-to-mysql}

Para obtener más información sobre cómo configurar la base de datos MySQL , consulte este [artículo](https://helpx.adobe.com/campaign/kb/campaign_fda_mysql.html).

### Configuración del acceso a Netezza {#configure-access-to-netezza}

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

### Configuración del acceso a Oracle {#configure-access-to-oracle}

La conexión a una base de datos externa de Oracle en FDA requiere ciertas configuraciones adicionales en el servidor de Adobe Campaign.

#### Para Linux {#for-linux-1}

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

#### Para Windows {#for-windows-1}

1. Instale el cliente Oracle.
1. In the C:Oracle folder, create a **tnsnames.ora** file containing your TNS definition.

   Agregue una variable de entorno TNS_ADMIN con C:Oracle como valor y reinicie el equipo.

### Configuración del acceso a Sybase IQ {#configure-access-to-sybase-iq}

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
>Para Windows, debe instalar el cliente de Sybase IQ en el servidor de Adobe Campaign y crear una conexión ODBC. Asegúrese de crear una fuente de datos del sistema cuando el servidor Adobe Campaign (nlserver) se esté ejecutando como un servicio en Windows.

### Configuración del acceso a Teradata {#configure-access-to-teradata}

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

### Configuración de acceso a SAP HANA {#configure-access-to-sap-hana}

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

   * **LD_LIBRARY_PATH**: Debe incluir el vínculo a su cliente SAP Hana (/usr/sap/hdbclient/ [libodbcHDB.so](http://libodbchdb.so/) de forma predeterminada).
   * **ODBCINI**: ubicación del archivo odbc.ini (por ejemplo, /etc/odbc.ini).

1. Cree la cuenta externa de SAP Hana, tal como se detalla en la sección [Creación de una conexión](#creating-a-shared-connection) compartida.

## Derechos de acceso a bases de datos remotas {#remote-database-access-rights}

En primer lugar, para que el usuario pueda llevar a cabo operaciones en una base de datos externa a través de FDA, el último debe tener un derecho específico en Adobe Campaign.

1. Seleccione el **[!UICONTROL Administration > Access Management > Named Rights]** nodo en el explorador de Adobe Campaign.
1. Cree un nuevo derecho especificando la etiqueta elegida.
1. The **[!UICONTROL Name]** field must take the following format **user:base@server**, where :

   * **user** corresponde al nombre del usuario en la base de datos externa.
   * **base** corresponde al nombre de la base de datos externa.
   * **server** corresponde al nombre del servidor de base de datos externo.

      >[!NOTE]
      >
      >La parte **:base** es opcional en Oracle.

1. Save the named right then link it to your chosen user from the **[!UICONTROL Administration > Access Management > Operators]** node of the Adobe Campaign explorer.

A continuación, para procesar los datos contenidos en una base de datos externa, el usuario de Adobe Campaign debe tener al menos derechos de escritura en la base de datos para poder crear tablas de trabajo. Adobe Campaign los elimina automáticamente.

En general, son necesarios los siguientes derechos:

* **CONEXIÓN**: conexión con la base de datos remota,
* **LECTURA DE Datos**: acceso de sólo lectura a tablas que contienen datos de clientes,
* **LECTURA DE MetaDatos**: acceso a los catálogos de datos del servidor para obtener la estructura de la tabla,
* **CARGA**: carga masiva en tablas de trabajo (requerido cuando se trabaja en colecciones y uniones),
* **CREACIÓN/ELIMINACIÓN** de **TABLA/ÍNDICE/PROCEDIMIENTO/FUNCIÓN**,
* **EXPLICACIÓN** (recomendado): para controlar el rendimiento en caso de problemas,
* **ESCRITURA DE Datos** (según el escenario de integración).

>[!NOTE]
>
>El administrador de la base de datos debe hacer coincidir estos derechos con los derechos específicos de cada motor de base de datos. Para obtener más información, consulte [Derechos específicos de RDBMS](https://docs.campaign.adobe.com/doc/AC6.1/en/technicalResources/technicalResources.html).

## Conexión a la base de datos {#connecting-to-the-database}

Para activar una conexión con la base de datos externa, debe indicar los parámetros de conexión, es decir, el origen de datos objetivo y el nombre de la tabla con los datos que sea necesario cargar.

>[!CAUTION]
>
>El usuario de Adobe Campaign necesita derechos específicos para la base de datos externa y el servidor de aplicaciones de Adobe Campaign para procesar datos desde una base de datos externa. Para obtener más información sobre esto, consulte la sección Derechos [de acceso a bases de datos](#remote-database-access-rights) remotas.
>
>Para evitar errores de funcionamiento, los operadores que accedan a datos compartidos remotos deben trabajar desde espacios independientes.

### Creación de una conexión compartida {#creating-a-shared-connection}

Para activar una conexión con una base de datos externa compartida, siempre y cuando esta conexión esté activa, se puede acceder a la base de datos a través de Adobe Campaign.

1. The configuration must be defined beforehand via the **[!UICONTROL Administration > Platform > External accounts]** node.
1. Haga clic en el **[!UICONTROL New]** botón y seleccione el **[!UICONTROL External database]** tipo.
1. Define the **[!UICONTROL Connection]** parameters of the external database.

   For connections to an **ODBC** type database the **[!UICONTROL Server]** field must contain the name of the ODBC data source and not the server name. Además, pueden ser necesarias determinadas configuraciones adicionales según las bases de datos utilizadas. Consulte la sección Configuraciones [específicas por tipo](#specific-configurations-by-database-type) de base de datos.

1. Once the parameters are entered, click the **[!UICONTROL Test the connection]** button to approve them.

   ![](assets/wf-external-account-create.png)

1. If necessary, uncheck the **[!UICONTROL Enabled]** option to disable access to this database without deleting its configuration.
1. Para permitir que Adobe Campaign acceda a esta base de datos, debe implementar las funciones SQL. Haga clic en la **[!UICONTROL Parameters]** ficha y, a continuación, en el **[!UICONTROL Deploy functions]** botón.

   ![](assets/wf-external-account-functions.png)

You can define specific work tablespaces for the tables and for the index in the **[!UICONTROL Parameters]** tab.

### Creación de una conexión con autenticación de Windows {#creating-a-connection-with-windows-authentication}

También puede conectarse mediante FDA usando la autenticación de Windows. Para ello:

* Asegúrese de que el servicio Adobe Campaign se ejecuta en una cuenta de Windows distinta de la cuenta del sistema local.
* Asegúrese de que el operador de Adobe Campaign dispone de suficientes derechos para el servidor de aplicaciones de Adobe Campaign y la base de datos externa.
* Create the corresponding external account without specifying the **[!UICONTROL Account]** and the **[!UICONTROL Password]**. Especifique solo el nombre de la base de datos.

### Creación de una conexión temporal {#creating-a-temporary-connection}

Puede definir directamente una conexión con una base de datos externa desde las actividades de flujo de trabajo. En este caso, se trata de una base de datos externa local, reservada para utilizarse dentro de un flujo de trabajo actual: no se guarda en las cuentas externas. Este tipo de conexión puntual se puede crear en diferentes actividades del flujo de trabajo, en particular la **[!UICONTROL Query]**, la **[!UICONTROL Data loading (RDBMS)]**, la **[!UICONTROL Enrichment]** actividad o la **[!UICONTROL Split]** actividad.

>[!CAUTION]
>
>No se recomienda este tipo de configuración, pero puede utilizarse periódicamente para recopilar datos. Sin embargo, debe crear una cuenta externa, como se muestra en la sección [Creación de una conexión compartida](#creating-a-shared-connection).

Por ejemplo, en la actividad de consulta, los pasos para crear una conexión periódica con una base de datos externa son los siguientes:

1. Haga clic en el **[!UICONTROL Add data...]** y seleccione las **[!UICONTROL External data]** opciones.
1. Seleccione la **[!UICONTROL Locally defining the data source]** opción.

   ![](assets/wf_add_data_local_external_data.png)

1. Seleccionar el motor de base de datos de objetivo en la lista desplegable. Introducir el nombre del servidor y especificar los parámetros de autenticación.

   Especificar también el nombre de la base de datos externa.

   ![](assets/wf_add_data_local_external_data_param.png)

   Haga clic en el botón **[!UICONTROL Next]**.

1. Seleccionar la tabla en la que se almacenan los datos.

   Puede introducir el nombre de la tabla directamente en el campo correspondiente o hacer clic en el icono de edición para acceder a la lista de las tablas de la base de datos.

   ![](assets/wf_add_data_local_external_data_select_table.png)

1. Click the **[!UICONTROL Add]** button to define one or several reconciliation fields between the external database data and the data in the Adobe Campaign database. Los **[!UICONTROL Edit expression]** iconos de la tabla **[!UICONTROL Remote field]** y **[!UICONTROL Local field]** le permiten acceder a la lista de campos de cada una de las tablas.

   ![](assets/wf_add_data_local_external_data_join.png)

1. Si es necesario, especifique una condición de filtrado y el modo de clasificación de datos.
1. Seleccione los datos adicionales que se recopilarán en la base de datos externa. To do this, double click on the fields(s) that you want to add to display them in the **[!UICONTROL Output columns]**.

   ![](assets/wf_add_data_local_external_data_select.png)

   Haga clic **[!UICONTROL Finish]** para confirmar esta configuración.

### Conexión segura {#secure-connection}

Puede proteger el acceso a una base de datos externa al configurar una cuenta externa de FDA.

Para ello, añada “**:ssl**” después de la dirección del servidor y dirección del puerto utilizado. Por ejemplo: **192.168.0.52:4501:ssl**.

A continuación, los datos se envían mediante el protocolo SSL seguro.

### Configuraciones adicionales {#additional-configurations}

Si es necesario, puede crear el esquema para procesar datos en una base de datos externa. Del mismo modo, Adobe Campaign permite definir la asignación en los datos de una tabla externa. Estas configuraciones son generales y no se aplican exclusivamente a flujos de trabajo.

>[!NOTE]
>
>Para obtener más información sobre la creación de esquemas en Adobe Campaign y la definición de una nueva asignación de datos, consulte [esta página](../../configuration/using/about-schema-edition.md).

## Creación del esquema de datos {#creating-the-data-schema}

To create a schema on an external database, click the **[!UICONTROL New]** button above the list of data schemas and choose **[!UICONTROL Access external data]**.

![](assets/wf_new_schema_fda.png)

Introduzca un nombre y una descripción para el esquema y seleccione la cuenta externa que activa la conexión con la base de datos. Esto permite acceder a la lista de tablas disponibles en la base externa. Seleccione la tabla que contiene los datos que se van a recopilar.

![](assets/wf_new_schema_select_table_fda.png)

Click **[!UICONTROL OK]** to confirm. Adobe Campaign detecta automáticamente la estructura de la tabla seleccionada y genera el esquema lógico.

>[!NOTE]
>
>Adobe Campaign no genera enlaces.

Click **[!UICONTROL Save]** to confirm creation.

![](assets/wf_new_schema_generate_fda.png)

Los índices se crean automáticamente al asignar una tabla (asignación estándar o FDA).

## Definición de asignación de datos {#defining-data-mapping}

Adobe Campaign le permite definir la asignación en los datos de una tabla externa.

Para ello, una vez que se haya creado el esquema de la tabla externa, debe crear una nueva asignación de envío para utilizar los datos de esta tabla como objetivo de envío.

Para ello, siga los siguientes pasos:

1. Cree una nueva asignación de envíos y elija la dimensión de objetivo, como por ejemplo el esquema que acaba de crear.

   ![](assets/wf_new_mapping_create_fda.png)

1. Indique los campos donde se almacena la información de envío (apellidos, nombre, correo electrónico, dirección, etc.).

   ![](assets/wf_new_mapping_define_join.png)

1. Especifique los parámetros para el almacenamiento de información, incluido el sufijo de los esquemas de extensión para que se puedan identificar fácilmente.

   ![](assets/wf_new_mapping_define_names.png)

   Puede elegir si desea almacenar las exclusiones (**excludelog**), con mensajes (**broadlog**) o en una tabla independiente.

   También puede elegir si desea administrar el seguimiento para esta asignación de envíos (**trackinglog**).

1. A continuación, seleccione las extensiones que se van a tener en cuenta. El tipo de extensión depende de los parámetros y opciones de la plataforma (consulte el contrato de licencia).

   ![](assets/wf_new_mapping_define_extensions.png)

   Click the **[!UICONTROL Save]** button to launch delivery mapping creation: all linked tables are created automatically based on the selected parameters.

## Opciones adicionales {#additional-options}

### Retransmisión HTTP a una instancia remota {#http-relay-to-a-remote-instance}

Puede acceder a bases de datos externas configuradas en instancias remotas mediante el protocolo HTTP.

>[!NOTE]
>
>Esta función no es compatible con todos los tipos de datos SQL. Los tipos de datos BLOB no son compatibles. Es posible que otros tipos de datos no funcionen en función de la base de datos de destino (Timestamp en Microsoft SQL Server, por ejemplo). Póngase en contacto con el servicio de asistencia de Adobe para obtener más información.

Esto simplifica la transferencia y sincronización de datos entre dos instancias. También le permite evitar cualquier tunelización entre una instancia y una base de datos remota, así como la instalación de las capas de cliente para acceder a esta base de datos. La instancia de destino puede ser una instancia alojada.

>[!CAUTION]
>
>Esta opción solo sirve para facilitar los flujos de replicación de datos (ETL).
>
>Por ejemplo, permite que una instancia alojada en la nube tenga acceso directo a los datos de una base de datos alojada de forma local. Sin embargo, no pretende permitir que la segmentación se lleve a cabo en una base de datos alojada de forma local directamente desde la nube.

Para ello, debe configurar las cuentas externas de las dos instancias para que la instancia local pueda comunicarse con la instancia remota mediante el protocolo HTTP:

* Instancia local: seleccione el nuevo tipo de **[!UICONTROL HTTP relay to a remote database]** conexión.

   En caso de carga masiva de datos, especifique también el tamaño del búfer. Seleccione la opción de compresión si desea reducir el tamaño de los datos transferidos.

   El **[!UICONTROL Data source]** debe definirse con la siguiente sintaxis: &quot;nms:extAccount : `<internal_name_of_the_external_account>`&quot;

   ![](assets/fda_over_http_1.png)

   >[!NOTE]
   >
   >Se recomienda utilizar una conexión HTTPS.

* Remote instance: in the FDA external account of the database accessed via the HTTP relay, check the Target of an **[!UICONTROL 'HTTP relay to a remote database' account option]**.

   ![](assets/fda_over_http_2.png)

El ejemplo siguiente muestra el nuevo modo de funcionamiento posible:

![](assets/schema_fda_over_http_2.png)

>[!CAUTION]
>
>Se debe acceder a la base de datos predeterminada de la instancia remota a través de una cuenta externa.

Este método operativo evita que el flujo de trabajo de limpieza de cada instancia elimine las tablas de trabajo de las bases de datos que utilizan la instancia como relé.

Por lo tanto, en el ejemplo anterior, el flujo de trabajo de limpieza de la instancia remota no realiza ninguna acción en la base de datos FDA roja porque la utiliza la instancia local.

### Creación directa de esquemas temporales {#directly-creating-temporary-schemas}

Si desea administrar varios accesos a una base de datos externa de FDA, una nueva opción le permite crear un esquema de trabajo de forma directa al configurar una cuenta externa.

>[!NOTE]
>
>Esta opción solo funciona con PostgreSQL.

![](assets/fda_work_table.png)

### Optimización de la personalización de correo electrónico con datos externos {#optimizing-email-personalization-with-external-data}

Desde la compilación 8740, la opción **[!UICONTROL Prepare the personalization data with a workflow]** está ahora disponible en la **[!UICONTROL Analysis]** ficha de las propiedades de entrega.

Durante el análisis de envío, esta opción crea y ejecuta automáticamente un flujo de trabajo que almacena todos los datos vinculados con el objetivo en una tabla temporal, incluidos los datos de tablas vinculadas en FDA.

Si marca esta opción, puede mejorar de forma significativa el rendimiento de la ejecución de la personalización.

### Cloud Messaging: Sincronización de FDA {#cloud-messaging---fda-synchronization}

Si el servidor de Cloud Messaging y el servidor de Marketing no se han sincronizado desde hace mucho tiempo, el volumen de registros faltantes en el servidor de Marketing puede ser significativo. Para optimizar la sincronización de registros mediante FDA, se ha añadido la opción **NmsMidSourcing_LogsPeriodHour** . Esto permite especificar un periodo máximo (expresado en horas) para limitar el número de registros recuperados cada vez que se ejecuta el flujo de trabajo de sincronización.

The option is to be added in the console, in the **[!UICONTROL Administration > Options]** node.

>[!CAUTION]
>
>Esta opción debe utilizarse **únicamente** para sincronizar un volumen significativo de registros a través de FDA.

>[!NOTE]
>
>La opción solo se toma en cuenta si existe una fecha de última recuperación (opción **NmsMidSourcing_LastBroadLog_***).

### Message Center: acceso de lectura en la tabla XtkFolder {#message-center---read-access-on-the-xtkfolder-table}

En la versión 8141 y posteriores, es necesario realizar la acción manualmente si Message Center utiliza el archivo FDA como modo de almacenamiento.

Debe conceder acceso de lectura en la tabla XtKFolder al usuario vinculado con la cuenta externa de FDA.

Por ejemplo, en una base de datos PostgreSQL, el comando es el siguiente:

```
GRANT SELECT ON XtkFolder TO DBUSER;
```

Este usuario debe tener acceso de lectura a las tablas siguientes:

* NmsBroadLogRtEvent
* NmsBroadLogBatchEvent
* NmsTrackingLogRtEvent
* NmsTrackingLogBatchEvent
* NmsRtEvent
* NmsBatchEvent
* NmsBroadLogMsg
* NmsTrackingUrl
* NmsDelivery
* NmsWebTrackingLog

>[!NOTE]
Esta modificación elimina el mensaje de error “Permiso denegado para la relación xtkfolder”.

Si el esquema de trabajo seleccionado en la cuenta de FDA externa no es la cuenta de Neolane, esta modificación a los derechos de acceso no es necesaria.

## Uso de datos de una base de datos externa en un flujo de trabajo {#using-data-from-an-external-database-in-a-workflow}

En varias actividades del flujo de trabajo de Adobe Campaign, puede utilizar los datos almacenados en una base de datos externa.

### Filtrado en datos externos {#filtering-on-external-data}

La actividad de consulta permite agregar datos externos y utilizarlos en las configuraciones de filtro definidas.

Para obtener más información, consulte la sección de [Consulta](../../workflow/using/targeting-data.md#selecting-data).

### Creación de subgrupos {#creating-sub-sets}

La actividad de partición permite crear subgrupos. Puede utilizar datos externos para definir los criterios de filtrado que deben utilizarse.

Para obtener más información, consulte la sección de [Partición](../../workflow/using/split.md).

### Carga de la base de datos externa {#loading-external-database}

Puede utilizar los datos externos en la carga de datos (RDBMS). Esta actividad se presenta en la sección [Carga de datos](../../workflow/using/data-loading--rdbms-.md) .

### Adición de información y enlaces {#adding-information-and-links}

La actividad de enriquecimiento permite añadir datos adicionales a la tabla de trabajo del flujo de trabajo, así como enlaces a una tabla externa. Por este motivo, puede aprovechar los datos de una base de datos externa. Esta actividad se presenta en la sección [Enriquecimiento](../../workflow/using/enrichment.md) .
