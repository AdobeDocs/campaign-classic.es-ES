---
product: campaign
title: Configuración del acceso a Microsoft SQL Server
description: Obtenga información sobre cómo configurar el acceso a Microsoft SQL Server
source-git-commit: 26ae7ff1f0837a9a50057d97b00422a288b9dc7a
workflow-type: tm+mt
source-wordcount: '493'
ht-degree: 8%

---

# Configuración del acceso a Microsoft SQL Server {#configure-fda-sql}

![](../../assets/v7-only.svg)

Uso de Campaign **Acceso de datos federado** (FDA) para procesar la información almacenada en una base de datos externa de Microsoft SQL Server. Siga los pasos a continuación para configurar el acceso a [!DNL Microsoft SQL Server].

1. Configurar [!DNL Microsoft SQL Server] en [CentOS](#sql-centos).
1. Configurar [!DNL Microsoft SQL Server] en [Linux](#sql-linux).
1. Configurar [!DNL Microsoft SQL Server] en [Windows](#sql-windows).
1. Configure las variables [!DNL Microsoft SQL Server] [cuenta externa](#sql-external) en Campaign

## Microsoft SQL Server en CentOS {#sql-centos}

>[!NOTE]
>
> [!DNL Microsoft SQL Server] está disponible en CentOS 7 y 6.

Para configurar [!DNL Microsoft SQL Server] en CentOS, siga los pasos a continuación:

1. Descargue e instale el controlador ODBC SQL con el siguiente comando:

   ```
   sudo su
   curl https://packages.microsoft.com/config/rhel/7/prod.repo > /etc/yum.repos.d/mssql-release.repo
   exit
   sudo yum remove unixODBC-utf16 unixODBC-utf16-devel #to avoid conflicts
   sudo ACCEPT_EULA=Y yum install msodbcsql
   ```

1. En Adobe Campaign, puede configurar la [!DNL Microsoft SQL Server] cuenta externa. Para obtener más información sobre cómo configurar la cuenta externa, consulte [esta sección](#sql-external).

## Microsoft SQL Server en Linux {#sql-linux}

>[!NOTE]
>
> Si está ejecutando una versión anterior de Adobe Campaign (anterior a la 7.2.1), debe instalar `unix ODBC drivers`.

1. Descargue el controlador ODBC de MS desde [esta página](https://packages.microsoft.com/ubuntu/16.04/prod/pool/main/m/msodbcsql17/).

1. Ejecute el siguiente comando como usuario raíz:

   ```
   # install the mssql odbc that was downloaded
   dpkg -i msodbcsql17_17.7.1.1-1_amd64.deb
   # accept the license terms
   ```

1. En Adobe Campaign, puede configurar la [!DNL Microsoft SQL Server] cuenta externa. Para obtener más información sobre cómo configurar la cuenta externa, consulte [esta sección](#sql-external).

## Microsoft SQL Server en Windows {#sql-windows}

Para configurar [!DNL Microsoft SQL Server] en Windows:

1. En Windows, haga clic en **[!UICONTROL Control Panel]** &#39;>&#39; **[!UICONTROL System and Security]** &#39;>&#39; **[!UICONTROL Administrative Tools]**&#39;>&#39; **[!UICONTROL ODBC Data Sources (64-bit)]**.

1. En el **[!UICONTROL ODBC Data Sources (64-bit)]** nueva ventana, haga clic en **[!UICONTROL Add...]**.

1. Compruebe si el cliente nativo de SQL Server v11 aparece en la lista **[!UICONTROL Create New Data Source]** ventana.

1. Si el cliente nativo de SQL Server no aparece en la lista, puede descargarlo en [esta página](https://www.microsoft.com/en-my/download/details.aspx?id=36434).

1. En Adobe Campaign, puede configurar la [!DNL Microsoft SQL Server] cuenta externa. Para obtener más información sobre cómo configurar la cuenta externa, consulte [esta sección](#sql-external).

## Cuenta externa de Microsoft SQL Server {#sql-external}

Debe crear un [!DNL Microsoft SQL Server] cuenta externa para conectar la instancia de Campaign con el [!DNL Microsoft SQL Server] base de datos externa.

1. Desde campaña **[!UICONTROL Explorer]**, haga clic en **[!UICONTROL Administration]** &#39;>&#39; **[!UICONTROL Platform]** &#39;>&#39; **[!UICONTROL External accounts]**.

1. Haga clic en **[!UICONTROL New]**.

1. Seleccione **[!UICONTROL External database]** como **[!UICONTROL Type]** de su cuenta externa.

1. En **[!UICONTROL Configuration]**, seleccione [!DNL Microsoft SQL Server] de la variable **[!UICONTROL Type]** lista desplegable.

   ![](assets/sql.png)

1. Configure las variables **[!UICONTROL Microsoft SQL Server]** autenticación de cuenta externa:

   * **[!UICONTROL Server]**: URL del [!DNL Microsoft SQL Server] servidor.

   * **[!UICONTROL Account]**: Nombre del usuario.

   * **[!UICONTROL Password]**: Contraseña de la cuenta de usuario.

   * **[!UICONTROL Database]**: Nombre de la base de datos (opcional).

   * **[!UICONTROL Timezone]**: Zona horaria definida en [!DNL Microsoft SQL Server]. [Más información](https://docs.microsoft.com/en-us/sql/t-sql/functions/current-timezone-transact-sql?view=sql-server-ver15)

1. Haga clic en la pestaña **[!UICONTROL Parameters]** y luego en el botón **[!UICONTROL Deploy functions]** para crear funciones.

   >[!NOTE]
   >
   >Para que todas las funciones estén disponibles, debe crear las funciones SQL de Adobe Campaign en la base de datos remota. Para obtener más información, consulte esta [página](../../configuration/using/adding-additional-sql-functions.md).

1. Haga clic en **[!UICONTROL Save]** cuando la configuración haya finalizado.

El conector admite las siguientes opciones:

| Opción | Descripción |
|---|---|
| Autenticación | Tipo de autenticación admitida por el conector. Valor actual admitido: ActiveDirectoryMSI. <br> Para obtener más información, consulte el ejemplo 8 de [Documentación de Microsoft](https://docs.microsoft.com/en-us/sql/connect/odbc/using-azure-active-directory?view=sql-server-ver15#example-connection-strings). |
| Codificar | Especifica si las conexiones utilizan el cifrado TLS en la red. Los valores posibles son **sí/obligatorio (18.0 y posterior)**, **no/opcional (18.0 y posterior)** y **estricta (18.0 y posterior)**. El valor predeterminado se establece en **yes** en la versión 18.0 y posteriores y **no** en versiones anteriores. <br>Para obtener más información, consulte [Documentación de Microsoft](https://docs.microsoft.com/en-us/sql/connect/odbc/dsn-connection-string-attribute?view=azure-sqldw-latest#encrypt). |
| TrustServerCertificate | Habilita el cifrado mediante un certificado de servidor autofirmado, cuando se utiliza con **Codificar**. <br>Valores aceptados: **yes** o **no** (valor predeterminado, lo que significa que el certificado del servidor se validará). |
