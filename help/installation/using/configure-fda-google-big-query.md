---
product: campaign
title: Configuración del acceso a Google BigQuery
description: Obtenga información sobre cómo configurar el acceso a Google BigQuery en FDA
audience: platform
content-type: reference
topic-tags: connectors
exl-id: ebaad59f-0607-4090-92d0-e457fbf9a348
source-git-commit: 5ad84f77b0618f2e8b948a3712bc106c19b03788
workflow-type: tm+mt
source-wordcount: '795'
ht-degree: 9%

---

# Configuración del acceso a Google BigQuery {#configure-fda-google-big-query}

![](../../assets/v7-only.svg)

Uso de Adobe Campaign Classic **Acceso de datos federado** (FDA) para procesar la información almacenada en una base de datos externa. Siga los pasos a continuación para configurar el acceso a [!DNL Google BigQuery].

1. Configurar [!DNL Google BigQuery] en [Windows](#google-windows) o [Linux](#google-linux)
1. Configure las variables [!DNL Google BigQuery] [cuenta externa](#google-external) en Adobe Campaign Classic
1. Configuración [!DNL Google BigQuery] carga masiva de conectores activada [Windows](#bulk-load-windows) o [Linux](#bulk-load-linux)

>[!NOTE]
>
> [!DNL Google BigQuery] El conector está disponible para implementaciones alojadas, híbridas y locales. Para obtener más información, consulte [esta página](../../installation/using/capability-matrix.md).

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

Antes de configurar el controlador, tenga en cuenta que el usuario raíz debe ejecutar la secuencia de comandos y los comandos. También se recomienda utilizar Google DNS 8.8.8.8 mientras se ejecuta el script.

Para configurar [!DNL Google BigQuery] en Linux, siga los pasos a continuación:

1. Antes de la instalación de ODBC, compruebe que los siguientes paquetes estén instalados en su distribución Linux:

   * Para Red Hat/CentOS:

      ```
      yum update
      yum upgrade
      yum install -y grep sed tar wget perl curl
      ```

   * Para Debian:

      ```
      apt-get update
      apt-get upgrade
      apt-get install -y grep sed tar wget perl curl
      ```

1. Actualizar el sistema antes de la instalación:

   * Para Red Hat/CentOS:

      ```
      # install unixODBC driver manager
      yum install -y unixODBC
      ```

   * Para Debian:

      ```
      # install unixODBC driver manager
      apt-get install -y odbcinst1debian2 libodbc1 odbcinst unixodbc
      ```

1. Antes de ejecutar la secuencia de comandos, puede obtener más información especificando el argumento —help:

   ```
   cd /usr/local/neolane/nl6/bin/fda-setup-scripts
   ./bigquery_odbc-setup.sh --help
   ```

1. Acceda al directorio donde se encuentra el script y ejecute el siguiente script como usuario raíz:

   ```
   cd /usr/local/neolane/nl6/bin/fda-setup-scripts
   ./bigquery_odbc-setup.sh
   ```

### Carga masiva configurada en Linux {#bulk-load-linux}

>[!NOTE]
>
>Necesita Python instalado para que funcione el SDK de Google Cloud.
>
>Recomendamos utilizar Python3, consulte esto [página](https://www.python.org/downloads/).

La utilidad de carga masiva permite una transferencia más rápida, que se logra mediante el SDK de Google Cloud.

1. Antes de la instalación de ODBC, compruebe que los siguientes paquetes estén instalados en su distribución Linux:

   * Para Red Hat/CentOS:

      ```
      yum update
      yum upgrade
      yum install -y python3
      ```

   * Para Debian:

      ```
      apt-get update
      apt-get upgrade
      apt-get install -y python3
      ```

1. Acceda al directorio donde se encuentra el script y ejecute el siguiente script:

   ```
   cd /usr/local/neolane/nl6/bin/fda-setup-scripts
   ./bigquery_sdk-setup.sh
   ```

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

El conector admite las siguientes opciones:

| Opción | Descripción |
|:-:|:-:|
| ProxyType | Tipo de proxy utilizado para conectarse a BigQuery mediante conectores ODBC y SDK. </br>Actualmente se admiten HTTP (predeterminado), http_no_tunel, socks4 y socks5. |
| ProxyHost | Nombre de host o dirección IP desde donde se puede acceder al proxy. |
| ProxyPort | Número de puerto en el que se ejecuta el proxy, por ejemplo, 8080 |
| ProxyUid | Nombre de usuario utilizado para el proxy autenticado |
| ProxyPwd | Contraseña de ProxyUid |
| bqpath | Tenga en cuenta que esto solo es aplicable a la herramienta de carga masiva (Cloud SDK). </br> Para evitar usar la variable PATH o si el directorio google-cloud-sdk tiene que moverse a otra ubicación, puede especificar con esta opción la ruta exacta al directorio de bin del sdk en la nube en el servidor. |
