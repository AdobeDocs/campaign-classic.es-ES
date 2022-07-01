---
product: campaign
title: Configuración del acceso a Snowflake
description: Obtenga información sobre cómo configurar el acceso al Snowflake en FDA
audience: platform
content-type: reference
topic-tags: connectors
exl-id: bdb5e422-ecfe-42eb-bd15-39fe5ec0ff1d
source-git-commit: 26ae7ff1f0837a9a50057d97b00422a288b9dc7a
workflow-type: tm+mt
source-wordcount: '512'
ht-degree: 38%

---

# Configuración del acceso a Snowflake {#configure-access-to-snowflake}

![](../../assets/v7-only.svg)

Uso de Campaign **Acceso de datos federado** (FDA) para procesar la información almacenada en una base de datos externa. Siga los pasos a continuación para configurar el acceso a [!DNL Snowflake].

1. Configurar [!DNL Snowflake] en [Linux](#snowflake-linux).
1. Configure las variables [!DNL Snowflake] [cuenta externa](#snowflake-external) en Campaign

>[!NOTE]
>
>[!DNL Snowflake]El conector está disponible para implementaciones alojadas y on-premise. Para obtener más información, consulte [esta página](../../installation/using/capability-matrix.md).

![](assets/snowflake_3.png)

## Snowflake en Linux {#snowflake-linux}

Para configurar [!DNL Snowflake] en Linux, siga los pasos a continuación:

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

1. Antes de ejecutar el script, puede tener acceso a más información con la variable `--help` opción:

   ```
   cd /usr/local/neolane/nl6/bin/fda-setup-scripts/
   ./snowflake_odbc-setup.sh --help
   ```

1. Acceda al directorio donde se encuentra el script y ejecute el siguiente script como usuario raíz:

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

## Cuenta externa Snowflake {#snowflake-external}

Debe crear un [!DNL Snowflake] cuenta externa para conectar la instancia de Campaign con el [!DNL Snowflake] base de datos externa.

1. Desde campaña **[!UICONTROL Explorer]**, haga clic en **[!UICONTROL Administration]** &#39;>&#39; **[!UICONTROL Platform]** &#39;>&#39; **[!UICONTROL External accounts]**.

1. Haga clic en **[!UICONTROL New]**.

1. Seleccione **[!UICONTROL External database]** como **[!UICONTROL Type]** de su cuenta externa.

1. En **[!UICONTROL Configuration]**, seleccione [!DNL Snowflake] de la variable **[!UICONTROL Type]** lista desplegable.

   ![](assets/snowflake_5.png)

1. Agregue la **[!UICONTROL Server]** URL y **[!UICONTROL Database]**.

1. Configure las variables **[!UICONTROL Snowflake]** autenticación de cuenta externa:

   * Para la autenticación de cuenta/contraseña, debe especificar:

      * **[!UICONTROL Account]**: Nombre del usuario

      * **[!UICONTROL Password]**: Contraseña de la cuenta de usuario.

      ![](assets/snowflake.png)

   * Para la autenticación de par de claves, haga clic en la **[!UICONTROL Keypair Auth]** para usar su **[!UICONTROL Private key]** para autenticar y copiar y pegar su **[!UICONTROL Private key]**.

      ![](assets/snowflake_4.png)


1. Haga clic en la pestaña **[!UICONTROL Parameters]** y luego en el botón **[!UICONTROL Deploy functions]** para crear funciones.

   >[!NOTE]
   >
   >Para que todas las funciones estén disponibles, debe crear las funciones SQL de Adobe Campaign en la base de datos remota. Para obtener más información, consulte esta [página](../../configuration/using/adding-additional-sql-functions.md).

   ![](assets/snowflake_2.png)

1. Haga clic en **[!UICONTROL Save]** cuando la configuración haya finalizado.

El conector admite las siguientes opciones:

| Opción | Descripción |
|---|---|
| esquema de trabajo | Esquema de base de datos que se va a utilizar para tablas de trabajo |
| almacén | Nombre del almacén predeterminado que se va a utilizar. Anula el valor predeterminado del usuario. |
| TimeZoneName | De forma predeterminada, vacío, lo que significa que se utiliza la zona horaria del sistema del servidor de aplicaciones de Campaign Classic. La opción se puede utilizar para forzar el parámetro de sesión TIMEZONE. <br>[Para obtener más información, consulte esta página](https://docs.snowflake.net/manuals/sql-reference/parameters.html#timezone). |
| WeekStart | Parámetro de sesión WEEK_START. De forma predeterminada, se establece en 0. <br>[Para obtener más información, consulte esta página](https://docs.snowflake.com/en/sql-reference/parameters.html#week-start). |
| UseCachedResult | Parámetro de sesión USE_CACHED_RESULTS. De forma predeterminada, se establece en TRUE. Esta opción se puede utilizar para deshabilitar los resultados en caché de Snowflake. <br>Para obtener más información, consulte [esta página](https://docs.snowflake.net/manuals/user-guide/querying-persisted-results.html). |
| bulkThreads | Número de subprocesos que se utilizan para el cargador masivo de Snowflake, más subprocesos significan un mejor rendimiento para cargas masivas más grandes. De forma predeterminada, se establece en 1. El número puede ajustarse, dependiendo del recuento de subprocesos del equipo. |
| chunkSize | Determina el tamaño del archivo del fragmento del cargador masivo. De forma predeterminada, se establece en 128 MB. Se puede modificar para obtener un rendimiento más óptimo, cuando se utiliza con subprocesos masivos. Los subprocesos más activos concurrentes significan un mejor rendimiento. <br>Para obtener más información, consulte [documentación del Snowflake](https://docs.snowflake.net/manuals/sql-reference/sql/put.html). |
| StageName | Nombre de la fase interna preaprovisionada. Se utilizará en la carga masiva en lugar de crear una nueva fase temporal. |
