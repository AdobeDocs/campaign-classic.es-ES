---
product: campaign
title: Configuración del acceso a Microsoft SQL Server
description: Obtenga información sobre cómo configurar el acceso a Microsoft SQL Server
feature: Installation, Federated Data Access
exl-id: 65ab4577-3126-4579-8fcc-e93772ebd1e8
source-git-commit: b666535f7f82d1b8c2da4fbce1bc25cf8d39d187
workflow-type: tm+mt
source-wordcount: '464'
ht-degree: 7%

---

# Configuración del acceso a Microsoft SQL Server {#configure-fda-sql}



Utilice la opción **Acceso de datos federado** (FDA) de Campaign para procesar la información almacenada en una base de datos externa de Microsoft SQL Server. Siga los pasos a continuación para configurar el acceso a [!DNL Microsoft SQL Server].

1. Configurar [!DNL Microsoft SQL Server] en [CentOS](#sql-centos).
1. Configurar [!DNL Microsoft SQL Server] en [Linux](#sql-linux).
1. Configurar [!DNL Microsoft SQL Server] en [Windows](#sql-windows).
1. Configurar la [!DNL Microsoft SQL Server] [cuenta externa](#sql-external) en Campaign

## Microsoft SQL Server en CentOS {#sql-centos}

>[!NOTE]
>
> [!DNL Microsoft SQL Server] está disponible en CentOS 7 y 6.

Para configurar [!DNL Microsoft SQL Server] en CentOS, siga los pasos a continuación:

1. Descargue e instale el controlador ODBC de SQL con el siguiente comando:

   ```
   sudo su
   curl https://packages.microsoft.com/config/rhel/7/prod.repo > /etc/yum.repos.d/mssql-release.repo
   exit
   sudo yum remove unixODBC-utf16 unixODBC-utf16-devel #to avoid conflicts
   sudo ACCEPT_EULA=Y yum install msodbcsql
   ```

1. En Adobe Campaign, puede configurar su cuenta externa [!DNL Microsoft SQL Server]. Para obtener más información sobre cómo configurar su cuenta externa, consulte [esta sección](#sql-external).

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

1. En Adobe Campaign, puede configurar su cuenta externa [!DNL Microsoft SQL Server]. Para obtener más información sobre cómo configurar su cuenta externa, consulte [esta sección](#sql-external).

## Microsoft SQL Server en Windows {#sql-windows}

Para configurar [!DNL Microsoft SQL Server] en Windows:

1. En Windows, haga clic en **[!UICONTROL Control Panel]** &#39;>&#39; **[!UICONTROL System and Security]** &#39;>&#39; **[!UICONTROL Administrative Tools]**&#39;>&#39; **[!UICONTROL ODBC Data Sources (64-bit)]**.

1. En la nueva ventana de **[!UICONTROL ODBC Data Sources (64-bit)]**, haga clic en **[!UICONTROL Add...]**.

1. Compruebe si SQL Server Native Client v11 aparece en la ventana **[!UICONTROL Create New Data Source]**.

1. Si SQL Server Native Client no aparece en la lista, puede descargarlo en [esta página](https://www.microsoft.com/en-my/download/details.aspx?id=36434).

1. En Adobe Campaign, puede configurar su cuenta externa [!DNL Microsoft SQL Server]. Para obtener más información sobre cómo configurar su cuenta externa, consulte [esta sección](#sql-external).

## Cuenta externa de Microsoft SQL Server {#sql-external}

Debe crear una cuenta externa [!DNL Microsoft SQL Server] para conectar la instancia de Campaign a la base de datos externa [!DNL Microsoft SQL Server].

1. En la campaña **[!UICONTROL Explorer]**, haga clic en **[!UICONTROL Administration]** &#39;>&#39; **[!UICONTROL Platform]** &#39;>&#39; **[!UICONTROL External accounts]**.

1. Haga clic en **[!UICONTROL New]**.

1. Seleccione **[!UICONTROL External database]** como **[!UICONTROL Type]** de su cuenta externa.

1. En **[!UICONTROL Configuration]**, seleccione [!DNL Microsoft SQL Server] de la lista desplegable **[!UICONTROL Type]**.

   ![](assets/sql.png)

1. Configure la autenticación de cuenta externa **[!UICONTROL Microsoft SQL Server]**:

   * **[!UICONTROL Server]**: URL del servidor [!DNL Microsoft SQL Server].

   * **[!UICONTROL Account]**: nombre del usuario.

   * **[!UICONTROL Password]**: contraseña de cuenta de usuario.

   * **[!UICONTROL Database]**: nombre de la base de datos (opcional).

   * **[!UICONTROL Timezone]**: zona horaria establecida en [!DNL Microsoft SQL Server]. [Más información](https://docs.microsoft.com/en-us/sql/t-sql/functions/current-timezone-transact-sql?view=sql-server-ver15)

1. Haga clic en la pestaña **[!UICONTROL Parameters]** y luego en el botón **[!UICONTROL Deploy functions]** para crear funciones.

   >[!NOTE]
   >
   >Para que todas las funciones estén disponibles, debe crear las funciones SQL de Adobe Campaign en la base de datos remota. Para obtener más información, consulte esta [página](../../configuration/using/adding-additional-sql-functions.md).

1. Haga clic en **[!UICONTROL Save]** cuando finalice la configuración.

El conector admite las siguientes opciones:

| Opción | Descripción |
|---|---|
| Autenticación | Tipo de autenticación admitida por el conector. Valor admitido actual: ActiveDirectoryMSI. <br> Para obtener más información, consulte el ejemplo 8 de [documentación de Microsoft](https://docs.microsoft.com/en-us/sql/connect/odbc/using-azure-active-directory?view=sql-server-ver15#example-connection-strings). |
| Cifrar | Especifica si las conexiones utilizan el cifrado TLS a través de la red. Los valores posibles son **yes/mandatory (18.0 y posterior)**, **no/optional (18.0 y posterior)**, y **strict (18.0 y posterior)**. El valor predeterminado está establecido en **yes** en la versión 18.0 y posteriores, y en **no** en versiones anteriores. <br>Para obtener más información, consulte [Documentación de Microsoft](https://docs.microsoft.com/en-us/sql/connect/odbc/dsn-connection-string-attribute?view=azure-sqldw-latest#encrypt). |
| TrustServerCertificate | Habilita el cifrado mediante un certificado de servidor firmado automáticamente, cuando se usa con **Encrypt**. <br>Valores aceptados: **sí** o **no** (valor predeterminado, lo que significa que se validará el certificado del servidor). |
