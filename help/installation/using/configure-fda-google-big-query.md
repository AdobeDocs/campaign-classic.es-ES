---
product: campaign
title: Configuración del acceso a Google BigQuery
description: Obtenga información sobre cómo configurar el acceso a Google BigQuery en FDA
audience: platform
content-type: reference
topic-tags: connectors
exl-id: ebaad59f-0607-4090-92d0-e457fbf9a348
source-git-commit: 6d53ba957fb567a9a921544418a73a9bde37c97b
workflow-type: tm+mt
source-wordcount: '903'
ht-degree: 7%

---

# Configuración del acceso a Google BigQuery {#configure-fda-google-big-query}

![](../../assets/v7-only.svg)

Uso de Adobe Campaign Classic **Acceso de datos federado** (FDA) para procesar la información almacenada en una base de datos externa. Siga los pasos a continuación para configurar el acceso a [!DNL Google BigQuery].

1. Configurar [!DNL Google BigQuery] en [Windows](#google-windows) o [Linux](#google-linux)
1. Configure las variables [!DNL Google BigQuery] [cuenta externa](#google-external) en Adobe Campaign Classic
1. Configuración [!DNL Google BigQuery] carga masiva de conectores activada [Windows](#bulk-load-windows) o [Linux](#bulk-load-linux)

>[!NOTE]
>
> [!DNL Google BigQuery] El conector está disponible para implementaciones híbridas y locales. Para obtener más información, consulte [esta página](../../installation/using/capability-matrix.md).

![](assets/snowflake_3.png)

## Google BigQuery en Windows {#google-windows}

### Controlador configurado en Windows {#driver-window}

1. Descargue [el controlador ODBC para Windows](https://cloud.google.com/bigquery/docs/reference/odbc-jdbc-drivers).

1. Configure el controlador ODBC en Windows. Para obtener más información, consulte [esta página](https://storage.googleapis.com/simba-bq-release/jdbc/Simba%20JDBC%20Driver%20for%20Google%20BigQuery%20Install%20and%20Configuration%20Guide.pdf).

1. Para la variable [!DNL Google BigQuery] para que funcione, Adobe Campaign Classic requiere los siguientes parámetros para conectarse:

   * **[!UICONTROL Project]**: cree o use un proyecto existente.

      Para obtener más información, consulte esta [página](https://cloud.google.com/resource-manager/docs/creating-managing-projects).

   * **[!UICONTROL Service account]**: cree una cuenta de servicio.

      Para obtener más información, consulte esta [página](https://cloud.google.com/iam/docs/creating-managing-service-accounts).

   * **[!UICONTROL Key File Path]**: el **[!UICONTROL Service account]** requiere un **[!UICONTROL Key File]** para un [!DNL Google BigQuery] conexión mediante ODBC.

      Para obtener más información, consulte esta [página](https://cloud.google.com/iam/docs/creating-managing-service-account-keys).

   * **[!UICONTROL Dataset]**: **[!UICONTROL Dataset]** es opcional para una conexión ODBC. Dado que cada consulta debe proporcionar el conjunto de datos donde se encuentra la tabla, al especificar una **[!UICONTROL Dataset]** es obligatorio para [!DNL Google BigQuery] Conector FDA en Adobe Campaign Classic.

      Para obtener más información, consulte esta [página](https://cloud.google.com/bigquery/docs/datasets).

1. En Adobe Campaign Classic, puede configurar la [!DNL Google BigQuery] cuenta externa. Para obtener más información sobre cómo configurar la cuenta externa, consulte [esta sección](#google-external).

### Carga masiva configurada en Windows {#bulk-load-window}

>[!NOTE]
>
>Necesita Python instalado para que funcione el SDK de Google Cloud.
>
>Recomendamos utilizar Python3, consulte esto [página](https://www.python.org/downloads/).

La utilidad de carga masiva permite una transferencia más rápida, que se logra mediante el SDK de Google Cloud.

1. Descargue el archivo de 64 bits (x86_64) de Windows de esta [página](https://cloud.google.com/sdk/docs/downloads-versioned-archives) y extráigalo en el directorio correspondiente.

1. Ejecute el `google-cloud-sdk\install.sh` secuencia de comandos. Debe aceptar la configuración de la variable de ruta.

1. Después de la instalación, compruebe que la variable de ruta `...\google-cloud-sdk\bin` está configurado. Si no es así, agréguelo manualmente.

1. En el  `..\google-cloud-sdk\bin\bq.cmd` , agregue la variable `CLOUDSDK_PYTHON` variable local, que redireccionará a la ubicación de la instalación de Python.

   Por ejemplo:

   ![](assets/google-big-query_1.png)

1. Reinicie Adobe Campaign Classic para que se tengan en cuenta los cambios.

## Google BigQuery en Linux {#google-linux}

### Configuración del controlador en Linux {#driver-linux}

1. Antes de instalar el controlador ODBC, debe actualizar el sistema. En Linux o CentOS, ejecute el siguiente comando:

   ```
   yum update
   # install unixODBC driver manager
   yum install unixODBC
   ```

1. A continuación, debe instalar el administrador de controladores unixODBC con el siguiente comando:

   ```
   # switch to root user
   sudo su
   ```

   En Debian:

   ```
   apt-get update
   apt-get upgrade
   # install unixODBC driver manager
   apt-get install unixODBC
   ```

1. Descargue el [Controlador ODBC de Simba Linux de Magnitude (.tar.gz)](https://cloud.google.com/bigquery/docs/reference/odbc-jdbc-drivers). A continuación, transfiera el archivo tarball a una carpeta temporal de su equipo o utilice el comando wget:

   ```
   # in this example driver version is 2.3.1.1001
   wget https://storage.googleapis.com/simba-bq-release/odbc/SimbaODBCDriverforGoogleBigQuery_[Version]-Linux.tar.gz
   ```

1. Extraiga el archivo tarball principal como se indica a continuación, donde **TarballName** es el nombre del paquete tarball que contiene el controlador:

   ```
   tar --directory=/tmp -zxvf [TarballName]
   ```

1. Acceda a la carpeta extraída y extraiga el archivo de tarball interno correspondiente a la versión del controlador. Instálelo en otra carpeta temporal, en el siguiente ejemplo BigQueryDriver:

   ```
   mkdir /tmp/BigQueryDriver/
   cd /tmp/SimbaODBCDriverforGoogleBigQuery_[Version]-Linux/
   tar --directory=/tmp/BigQueryDriver/ -zxvf SimbaODBCDriverforGoogleBigQuery[Bitness]_[Version].tar.gz
   ```

1. Acceda a la ubicación temporal en la que se extrajo el archivo .tarball principal y copie el `GoogleBigQueryODBC.did` y `setup/simba.googlebigqueryodbc.ini` en la nueva carpeta creada en el paso anterior:

   ```
   cd /tmp/SimbaODBCDriverforGoogleBigQuery_[Version]-Linux/
   cp GoogleBigQueryODBC.did /tmp/BigQueryDriver/SimbaODBCDriverforGoogleBigQuery[Bitness]_[Version]/lib/
   cp setup/simba.googlebigqueryodbc.ini /tmp/BigQueryDriver/SimbaODBCDriverforGoogleBigQuery[Bitness]_[Version]/lib/
   ```

1. Cree el directorio de instalación de la siguiente manera:

   ```
   mkdir -p /opt/simba/googlebigqueryodbc/
   ```

1. Copie el contenido del directorio en el nuevo directorio de instalación:

   ```
   cp -r /tmp/BigQueryDriver/SimbaODBCDriverforGoogleBigQuery[Bitness]_[Version]/* /opt/simba/googlebigqueryodbc/
   ```

1. Reemplazar `<INSTALLDIR>` con `/opt/simba/googlebigqueryodbc` en `simba.googlebigqueryodbc.ini` en el directorio de instalación:

   ```
   cd /opt/simba/googlebigqueryodbc/lib/
   sed -i 's/<INSTALLDIR>/\/opt\/simba\/googlebigqueryodbc/g' simba.googlebigqueryodbc.ini
   ```

1. Cambie el `DriverManagerEncoding` a UTF-16 y `SwapFilePath` en `simba.googlebigqueryodbc.ini`. Si es necesario, también puede cambiar la configuración de registro.

   El siguiente es un ejemplo de archivo de configuración actualizado en todo el controlador:

   ```
   # /opt/simba/googlebigqueryodbc/lib/simba.googlebigqueryodbc.ini
   [Driver]
   DriverManagerEncoding=UTF-16
   ErrorMessagesPath=opt/simba/googlebigqueryodbc/ErrorMessages
   LogLevel=6
   LogPath=/tmp
   SwapFilePath=/tmp
   ```

1. Si utiliza un archivo de controladores del sistema o cualquier `odbcinst.ini` archivo, configurar `/etc/odbcinst.ini` para señalar a la ubicación del controlador BigQuery de Google `/opt/simba/googlebigqueryodbc/lib/libgooglebigqueryodbc_sb[Bitness].so`.

   Por ejemplo:

   ```
   # /etc/odbcinst.ini
   # Make sure to use Simba ODBC Driver for Google BigQuery as a driver name.
   
   [ODBC Drivers]
   Simba ODBC Driver for Google BigQuery=Installed
   
   [Simba ODBC Driver for Google BigQuery]
   Description=Simba ODBC Driver for Google BigQuery(64-bit)
   Driver=/opt/simba/googlebigqueryodbc/lib/libgooglebigqueryodbc_sb64.so
   ```

1. Busque la ubicación de las bibliotecas del administrador de controladores unixODBC y agregue la variable `unixODBC` y `googlebigqueryodbc` rutas de biblioteca a `LD_LIBRARY_PATH environment` variable.

   ```
   find / -name 'lib*odbc*.so*' -print
   #output:
   /usr/lib/x86_64-linux-gnu/libodbccr.so.2
   /usr/lib/x86_64-linux-gnu/libodbcinst.so.2.0.0
   /usr/lib/x86_64-linux-gnu/libodbccr.so.1
   .
   .
   /opt/simba/googlebigqueryodbc/lib/libgooglebigqueryodbc_sb64.so
   
   #the command would look like this
   export LD_LIBRARY_PATH=$LD_LIBRARY_PATH:/opt/simba/googlebigqueryodbc:/usr/lib
   ```

1. En Adobe Campaign Classic, puede configurar la [!DNL Google BigQuery] cuenta externa. Para obtener más información sobre cómo configurar la cuenta externa, consulte [esta sección](#google-external).

### Carga masiva configurada en Linux {#bulk-load-linux}

>[!NOTE]
>
>Necesita Python instalado para que funcione el SDK de Google Cloud.
>
>Recomendamos utilizar Python3, consulte esto [página](https://www.python.org/downloads/).

La utilidad de carga masiva permite una transferencia más rápida, que se logra mediante el SDK de Google Cloud.

1. Descargue el archivo de 64 bits (x86_64) de Linux en esta [página](https://cloud.google.com/sdk/docs/downloads-versioned-archives) y extraiga en el directorio correspondiente.

1. Ejecute el `google-cloud-sdk\install.sh` secuencia de comandos. Debe aceptar la configuración de la variable de ruta.

1. Después de la instalación, compruebe que la variable de ruta `...\google-cloud-sdk\bin` está configurado. Si no es así, agréguelo manualmente.

1. Si desea evitar usar la variable `PATH` o si desea mover la variable `google-cloud-sdk` a otra ubicación, use el `bqpath` valor de opción al configurar la variable **[!UICONTROL External account]** para especificar la ruta exacta al directorio bin de su sistema.

1. Reinicie Adobe Campaign Classic para que se tengan en cuenta los cambios.

## Cuenta externa Google BigQuery {#google-external}

Debe crear un [!DNL Google BigQuery] cuenta externa para conectar la instancia de Adobe Campaign Classic con el [!DNL Google BigQuery] base de datos externa.

1. Desde Adobe Campaign Classic **[!UICONTROL Explorer]**, haga clic en **[!UICONTROL Administration]** &#39;>&#39; **[!UICONTROL Platform]** &#39;>&#39; **[!UICONTROL External accounts]**.

1. Haga clic en **[!UICONTROL New]**.

1. Seleccione **[!UICONTROL External database]** como **[!UICONTROL Type]** de su cuenta externa.

1. Configure la cuenta externa [!DNL Google BigQuery]. Debe especificar:

   * **[!UICONTROL Type]**: [!DNL Google BigQuery]

   * **[!UICONTROL Service account]**: Correo electrónico de su **[!UICONTROL Service account]**. Para obtener más información, consulte [Documentación de Google Cloud](https://cloud.google.com/iam/docs/creating-managing-service-accounts).

   * **[!UICONTROL Project]**: Nombre del **[!UICONTROL Project]**. Para obtener más información, consulte [Documentación de Google Cloud](https://cloud.google.com/resource-manager/docs/creating-managing-projects).

   * **[!UICONTROL Key file Path]**:
      * **[!UICONTROL Upload key file to the server]**: select **[!UICONTROL Click here to upload]** si decide cargar la clave a través de Adobe Campaign Classic.

      * **[!UICONTROL Enter manually the key file path]**: copie/pegue la ruta absoluta en este campo si elige utilizar una clave preexistente.
   * **[!UICONTROL Dataset]**: Nombre del **[!UICONTROL Dataset]**. Para obtener más información, consulte [Documentación de Google Cloud](https://cloud.google.com/bigquery/docs/datasets-intro).
   ![](assets/google-big-query.png)
