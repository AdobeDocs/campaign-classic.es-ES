---
product: campaign
title: Configuración del acceso a Snowflake
description: Obtenga información sobre cómo configurar el acceso al Snowflake en FDA
audience: platform
content-type: reference
topic-tags: connectors
exl-id: bdb5e422-ecfe-42eb-bd15-39fe5ec0ff1d
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: tm+mt
source-wordcount: '495'
ht-degree: 72%

---

# Configuración del acceso a Snowflake {#configure-access-to-snowflake}

Utilice la opción **Federated Data Access** (FDA) de Campaign para procesar la información almacenada en una base de datos externa. Siga los pasos a continuación para configurar el acceso a [!DNL Snowflake].

1. Configure [!DNL Snowflake] en [CentOS](#snowflake-centos), [Windows](#snowflake-windows) o [Debian](#snowflake-debian)
1. Configurar la [!DNL Snowflake] [cuenta externa](#snowflake-external) en Campaign


>[!NOTE]
>
>[!DNL Snowflake]El conector está disponible para implementaciones alojadas y on-premise. Para obtener más información, consulte [esta página](../../installation/using/capability-matrix.md).

![](assets/snowflake_3.png)

## Snowflake en CentOS {#snowflake-centos}

Para configurar [!DNL Snowflake] en CentOS, siga los pasos a continuación:

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

1. En Campaign, puede configurar la cuenta externa [!DNL Snowflake] . Para obtener más información sobre cómo configurar la cuenta externa, consulte [esta sección](#snowflake-external).

## Snowflake en Windows {#snowflake-windows}

1. Descargue [el controlador ODBC para Windows](https://docs.snowflake.net/manuals/user-guide/odbc-download.html). Tenga en cuenta que necesita privilegios de administrador para instalar el controlador. Para obtener más información, consulte [esta página](https://docs.snowflake.net/manuals/user-guide/admin-user-management.html)

1. Configure el controlador ODBC. Para obtener más información, consulte [esta página](https://docs.snowflake.net/manuals/user-guide/odbc-windows.html#step-2-configure-the-odbc-driver)

1. En Campaign, puede configurar la cuenta externa [!DNL Snowflake] . Para obtener más información sobre cómo configurar la cuenta externa, consulte [esta sección](#snowflake-external).

## Snowflake en Debian {#snowflake-debian}

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

1. En Campaign, puede configurar la cuenta externa [!DNL Snowflake] . Para obtener más información sobre cómo configurar la cuenta externa, consulte [esta sección](#snowflake-external).

## Cuenta externa Snowflake {#snowflake-external}

Debe crear una cuenta externa [!DNL Snowflake] para conectar la instancia de Campaign a la base de datos externa [!DNL Snowflake].

1. En Campaña **[!UICONTROL Explorer]**, haga clic en **[!UICONTROL Administration]** &#39;>&#39; **[!UICONTROL Platform]** &#39;>&#39; **[!UICONTROL External accounts]**.

1. Haga clic en **[!UICONTROL New]**.

1. Seleccione **[!UICONTROL External database]** como **[!UICONTROL Type]** de su cuenta externa.

1. Configure la cuenta externa **[!UICONTROL Snowflake]**. Debe especificar:

   * **[!UICONTROL Type]**: [!DNL Snowflake]

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
