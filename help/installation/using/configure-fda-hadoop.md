---
solution: Campaign Classic
product: campaign
title: Configuración del acceso a Hadoop
description: Obtenga información sobre cómo configurar el acceso a Hadoop en FDA
audience: platform
content-type: reference
topic-tags: connectors
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '602'
ht-degree: 81%

---


# Configuración del acceso a Hadoop {#configure-access-to-hadoop}

Utilice la opción Campaña **Acceso de datos federado** (FDA) para procesar la información almacenada en una base de datos externa. Siga los pasos a continuación para configurar el acceso a Hadoop.

1. Configurar [base de datos de Hadoop](#configuring-hadoop)
1. Configurar la cuenta externa [de Hadoop](#hadoop-external) en Campaña

## Configuración de Hadoop 3.0 {#configuring-hadoop}

La conexión a una base de datos externa de Hadoop en FDA requiere las siguientes configuraciones en el servidor de Adobe Campaign. Tenga en cuenta que esta configuración está disponible tanto para Windows como para Linux.

1. Descargue los controladores ODBC para Hadoop en función de su versión del sistema operativo. Los controladores se encuentran en [esta página](https://www.cloudera.com/downloads.html).

1. A continuación, debe instalar los controladores ODBC y crear un DSN para la conexión de Hive. Las instrucciones se encuentran en [esta página](https://docs.cloudera.com/documentation/other/connectors/hive-odbc/2-6-5/Cloudera-ODBC-Driver-for-Apache-Hive-Install-Guide.pdf).

1. Después de descargar e instalar los controladores ODBC, debe reiniciar Campaign Classic. Para ello, ejecute el siguiente comando:

   ```
   systemctl stop nlserver.service
   systemctl start nlserver.service
   ```

1. En Campaign Classic, puede configurar la cuenta externa [!DNL Hadoop]. Para obtener más información sobre cómo configurar su cuenta externa, consulte [esta sección](#hadoop-external).

## Cuenta externa de Hadoop {#hadoop-external}

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

| Nombre | Valor | Descripción |
|---|---|---|
| bulkKey | Clave de acceso de Azure blob o DataLake | Para cargadores masivos wasb:// o wasbs:// (es decir, si la herramienta de carga masiva inicio con wasb:// o wasbs://). <br>Es la clave de acceso para blob o el bloque DataLake para la carga masiva. |
| hdfsPort | número de puerto <br>establecido de forma predeterminada en 8020. | Para la carga masiva de HDFS (es decir, si la herramienta de carga masiva inicia con webhdfs:// o webhdfss://). |
| bucketsNumber | 20 | Número de bloques al crear una tabla agrupada. |
| fileFormat | PARQUET | Formato de archivo predeterminado para tablas de trabajo. |


## Configuración de Hadoop 2.1 {#configure-access-hadoop-2}

Si necesita conectarse a Hadoop 2.1, siga los pasos descritos a continuación para [Windows](#for-windows) o [Linux](#for-linux).

### Hadoop 2.1 para Windows {#for-windows}

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

1. Cree la cuenta externa de Hadoop, tal como se detalla en [esta sección](#hadoop-external).

### Hadoop 2.1 para Linux {#for-linux}

1. Instale unixodbc para Linux.

   ```
   apt-get install unixodbc
   ```

1. Descargue e instale controladores ODBC para Apache Hive desde HortonWorks: [https://www.cloudera.com/downloads.html](https://www.cloudera.com/downloads.html).

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

   A continuación se muestra un ejemplo de HDInsight para configurar una conexión denominada &quot;viral&quot;:

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

1. Cree la cuenta externa de Hadoop, tal como se detalla en [esta sección](#hadoop-external).

