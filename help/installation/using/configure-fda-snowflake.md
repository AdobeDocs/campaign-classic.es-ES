---
product: campaign
title: Configuración del acceso al Snowflake
description: Obtenga información sobre cómo configurar el acceso al Snowflake en FDA
feature: Installation, Federated Data Access
badge-v7-only: label="v7" type="Informative" tooltip="Se aplica solo a Campaign Classic v7"
audience: platform
content-type: reference
topic-tags: connectors
exl-id: bdb5e422-ecfe-42eb-bd15-39fe5ec0ff1d
source-git-commit: 6939307c0b33ff662fe4ef9ae0192ae7b500a95c
workflow-type: tm+mt
source-wordcount: '499'
ht-degree: 33%

---

# Configuración del acceso al Snowflake {#configure-access-to-snowflake}

Uso de Campaign **Acceso de datos federado** (FDA) para procesar la información almacenada en una base de datos externa. Siga estos pasos para configurar el acceso a [!DNL Snowflake].

1. Configurar [!DNL Snowflake] el [Linux](#snowflake-linux).
1. Configure las variables [!DNL Snowflake] [cuenta externa](#snowflake-external) en Campaign

>[!NOTE]
>
>[!DNL Snowflake]El conector está disponible para implementaciones alojadas y on-premise. Para obtener más información, consulte [esta página](../../installation/using/capability-matrix.md).

![](assets/snowflake_3.png)

## Snowflake en Linux {#snowflake-linux}

Para configurar [!DNL Snowflake] En Linux, siga los pasos a continuación:

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

1. Antes de ejecutar la secuencia de comandos, puede tener acceso a más información con el `--help` opción:

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

1. En Campaign, puede configurar la [!DNL Snowflake] cuenta externa. Para obtener más información sobre cómo configurar la cuenta externa, consulte [esta sección](#snowflake-external).

## Cuenta externa de Snowflake {#snowflake-external}

Debe crear un [!DNL Snowflake] cuenta externa para conectar la instancia de Campaign a [!DNL Snowflake] base de datos externa.

1. Desde Campaign **[!UICONTROL Explorer]**, haga clic en **[!UICONTROL Administration]** &#39;>&#39; **[!UICONTROL Platform]** &#39;>&#39; **[!UICONTROL External accounts]**.

1. Haga clic en **[!UICONTROL New]**.

1. Seleccione **[!UICONTROL External database]** como **[!UICONTROL Type]** de su cuenta externa.

1. En **[!UICONTROL Configuration]**, seleccione [!DNL Snowflake] desde el **[!UICONTROL Type]** menú desplegable.

   ![](assets/snowflake_5.png)

1. Añada su **[!UICONTROL Server]** URL y **[!UICONTROL Database]**.

1. Configure las variables **[!UICONTROL Snowflake]** autenticación de cuenta externa:

   * Para la autenticación de cuenta/contraseña, debe especificar:

      * **[!UICONTROL Account]**: Nombre del usuario

      * **[!UICONTROL Password]**: contraseña de cuenta de usuario.

     ![](assets/snowflake.png)

   * Para la autenticación de par de claves, haga clic en **[!UICONTROL Keypair Auth]** para utilizar su **[!UICONTROL Private key]** para autenticar y copiar y pegar su **[!UICONTROL Private key]**.

     ![](assets/snowflake_4.png)

1. Haga clic en la pestaña **[!UICONTROL Parameters]** y luego en el botón **[!UICONTROL Deploy functions]** para crear funciones.

   >[!NOTE]
   >
   >Para que todas las funciones estén disponibles, debe crear las funciones SQL de Adobe Campaign en la base de datos remota. Para obtener más información, consulte esta [página](../../configuration/using/adding-additional-sql-functions.md).

   ![](assets/snowflake_2.png)

1. Clic **[!UICONTROL Save]** cuando finalice la configuración.

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
