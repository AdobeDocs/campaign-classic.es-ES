---
title: Configuración del acceso a Sybase IQ
description: Obtenga información sobre cómo configurar el acceso a Sybase IQ en FDA
page-status-flag: never-activated
uuid: b84359b9-c584-431d-80d5-71146d9b6854
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: platform
content-type: reference
topic-tags: connectors
discoiquuid: dd3d14cc-5153-428d-a98a-32b46f0fe811
translation-type: tm+mt
source-git-commit: 9bbde65aea6735e30e95e75c2b6ae5445d4a2bdd
workflow-type: tm+mt
source-wordcount: '319'
ht-degree: 73%

---


# Configuración del acceso a Sybase IQ {#configure-access-to-sybase-iq}

Utilice la opción **Acceso de datos federado** de Campaña (FDA) para procesar la información almacenada en una base de datos externa. Siga los pasos a continuación para configurar el acceso a Sybase IQ.

1. Configuración de la base de datos [Sybase IQ](#configuring-sybase)
1. Configurar la [cuenta externa](#sybase-external) Sybase IQ en Campaña

## Configuración de Sybase IQ {#configuring-sybase}

La conexión a una base de datos externa de Sybase IQ en FDA requiere determinadas configuraciones adicionales en el servidor de Adobe Campaign.

>[!NOTE]
>
>Before starting, make sure the **unixodbc** package is on the server.

1. Instale **iq_odbc**. Se puede producir un error al final de la instalación. Puede ignorar este error.

1. Instale **iq_client_common**. Puede producirse un error de Java al final de la instalación. Puede ignorar este error.

1. Configure el controlador ODBC. La configuración se puede realizar en los archivos estándar: /etc/odbc.ini para obtener parámetros generales y /etc/odbcinst.ini para declarar controladores:

   * **/etc/odbc.ini** (reemplace valores como`<server_alias>` por sus propios valores):

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

## Cuenta externa Sybase IQ {#sybase-external}

La cuenta externa Sybase IQ permite conectar la instancia de Campaña a la base de datos externa Sybase IQ.

1. En la Campaña **[!UICONTROL Explorer]**, haga clic en **[!UICONTROL Administration]** &#39;>&#39; **[!UICONTROL Platform]** &#39;>&#39; **[!UICONTROL External accounts]**.

1. Haga clic en **[!UICONTROL New]** y seleccione **[!UICONTROL External database]** como **[!UICONTROL Type]**.

1. Para configurar la cuenta externa **[!UICONTROL Sybase IQ]**, debe especificar:

   * **[!UICONTROL Type]**: ODBC (Sybase ASE, Sybase IQ)

   * **[!UICONTROL Server]**: corresponde a la conexión ODBC (`<server_alias>`) definida en el paso 5. No es necesariamente el nombre del servidor.

   * **[!UICONTROL Account]**: Nombre del usuario

   * **[!UICONTROL Password]**: Contraseña de la cuenta de usuario

   * **[!UICONTROL Database]**: Nombre de la base de datos

>[!NOTE]
>
>Para Windows, debe instalar el cliente de Sybase IQ en el servidor de Adobe Campaign y crear una conexión ODBC. Asegúrese de crear una fuente de datos del sistema cuando el servidor Adobe Campaign (nlserver) se esté ejecutando como un servicio en Windows.

