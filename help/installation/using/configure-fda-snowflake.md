---
product: campaign
title: Configuración del acceso al Snowflake
description: Obtenga información sobre cómo configurar el acceso al Snowflake en FDA
feature: Installation, Federated Data Access
audience: platform
content-type: reference
topic-tags: connectors
exl-id: bdb5e422-ecfe-42eb-bd15-39fe5ec0ff1d
source-git-commit: 22420452d4df2e8161c91a42ad0d20ceb4796e82
workflow-type: tm+mt
source-wordcount: '503'
ht-degree: 31%

---

# Configuración del acceso al Snowflake {#configure-access-to-snowflake}

Utilice la opción **Acceso de datos federado** (FDA) de Campaign para procesar la información almacenada en una base de datos externa. Siga los pasos a continuación para configurar el acceso a [!DNL Snowflake].

1. Configurar [!DNL Snowflake] en [Linux](#snowflake-linux).
1. Configurar la [!DNL Snowflake] [cuenta externa](#snowflake-external) en Campaign

>[!CAUTION]
>
>* [!DNL Snowflake]El conector está disponible para implementaciones alojadas y on-premise. Para obtener más información, consulte [esta página](../../installation/using/capability-matrix.md).
>
>* La versión mínima admitida del controlador ODBC [!DNL Snowflake] es **2.24.4**.
>

![](assets/snowflake_3.png)

## Snowflake en Linux {#snowflake-linux}

Para configurar [!DNL Snowflake] en Linux, siga los pasos a continuación:

1. Antes de la instalación de ODBC, compruebe que los siguientes paquetes estén instalados en la distribución Linux:

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

1. Antes de ejecutar el script, puede tener acceso a más información con la opción `--help`:

   ```
   cd /usr/local/neolane/nl6/bin/fda-setup-scripts/
   ./snowflake_odbc-setup.sh --help
   ```

1. Acceda al directorio en el que se encuentra la secuencia de comandos y ejecute la siguiente secuencia de comandos como usuario raíz:

   ```
   cd /usr/local/neolane/nl6/bin/fda-setup-scripts
   ./snowflake_odbc-setup.sh
   ```

1. Después de instalar los controladores ODBC, debe reiniciar el Campaign Classic. Para ello, ejecute el siguiente comando:

   ```
   systemctl stop nlserver.service
   systemctl start nlserver.service
   ```

1. En Campaign, puede configurar la cuenta externa [!DNL Snowflake]. Para obtener más información sobre cómo configurar su cuenta externa, consulte [esta sección](#snowflake-external).

## Cuenta externa de Snowflake {#snowflake-external}

Debe crear una cuenta externa [!DNL Snowflake] para conectar la instancia de Campaign a la base de datos externa [!DNL Snowflake].

1. En la campaña **[!UICONTROL Explorer]**, haga clic en **[!UICONTROL Administration]** &#39;>&#39; **[!UICONTROL Platform]** &#39;>&#39; **[!UICONTROL External accounts]**.

1. Haga clic en **[!UICONTROL New]**.

1. Seleccione **[!UICONTROL External database]** como **[!UICONTROL Type]** de su cuenta externa.

1. En **[!UICONTROL Configuration]**, seleccione [!DNL Snowflake] de la lista desplegable **[!UICONTROL Type]**.

   ![](assets/snowflake_5.png)

1. Agregue su dirección URL **[!UICONTROL Server]** y **[!UICONTROL Database]**.

1. Configure la autenticación de cuenta externa **[!UICONTROL Snowflake]**:

   * Para la autenticación de cuenta/contraseña, debe especificar:

      * **[!UICONTROL Account]**: Nombre del usuario

      * **[!UICONTROL Password]**: contraseña de cuenta de usuario.

     ![](assets/snowflake.png)

   * Para la autenticación de par de claves, haga clic en la ficha **[!UICONTROL Keypair Auth]** para usar su **[!UICONTROL Private key]** para autenticar y copiar y pegar su **[!UICONTROL Private key]**.

     ![](assets/snowflake_4.png)

1. Haga clic en la pestaña **[!UICONTROL Parameters]** y luego en el botón **[!UICONTROL Deploy functions]** para crear funciones.

   >[!NOTE]
   >
   >Para que todas las funciones estén disponibles, debe crear las funciones SQL de Adobe Campaign en la base de datos remota. Para obtener más información, consulte esta [página](../../configuration/using/adding-additional-sql-functions.md).

   ![](assets/snowflake_2.png)

1. Haga clic en **[!UICONTROL Save]** cuando finalice la configuración.

El conector admite las siguientes opciones:

| Opción | Descripción |
|---|---|
| esquema de trabajo | Esquema de base de datos que se va a utilizar para tablas de trabajo |
| almacén | Nombre del almacén predeterminado que se va a utilizar. Anula el valor predeterminado del usuario. |
| TimeZoneName | De forma predeterminada, vacío, lo que significa que se utiliza la zona horaria del sistema del servidor de aplicaciones de Campaign Classic. La opción se puede utilizar para forzar el parámetro de sesión TIMEZONE. <br>[Para obtener más información, consulte esta página](https://docs.snowflake.net/manuals/sql-reference/parameters.html#timezone). |
| WeekStart | Parámetro de sesión WEEK_START. De forma predeterminada, se establece en 0. <br>[Para obtener más información, consulte esta página](https://docs.snowflake.com/en/sql-reference/parameters.html#week-start). |
| UseCachedResult | Parámetro de sesión USE_CACHED_RESULTS. De forma predeterminada, se establece en TRUE. Esta opción se puede utilizar para deshabilitar los resultados en caché del Snowflake. <br>[Para obtener más información, consulte esta página](https://docs.snowflake.net/manuals/user-guide/querying-persisted-results.html). |
| bulkThreads | Número de subprocesos que se utilizarán para el cargador en bloque del Snowflake; si hay más subprocesos, se obtiene un mejor rendimiento para cargas en bloque más grandes. De forma predeterminada, se establece en 1. El número se puede ajustar en función del número de hilos de la máquina. |
| chunkSize | Determina el tamaño de archivo del fragmento del cargador en bloque. De forma predeterminada, se establece en 128 MB. Se puede modificar para obtener un rendimiento más óptimo, cuando se utiliza con bulkThreads. Los hilos más activos simultáneamente significan un mejor rendimiento. <br>Para obtener más información, consulte [Documentación del Snowflake](https://docs.snowflake.net/manuals/sql-reference/sql/put.html). |
| StageName | Nombre de la fase interna preaprovisionada. Se utilizará en la carga masiva en lugar de crear una nueva etapa temporal. |
