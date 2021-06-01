---
product: campaign
title: Configuración del acceso a Sybase IQ
description: Obtenga información sobre cómo configurar el acceso a la Sybase IQ en FDA
audience: platform
content-type: reference
topic-tags: connectors
exl-id: 0fdf8259-5cab-4a9d-adb3-6c55ec5c8851
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: tm+mt
source-wordcount: '319'
ht-degree: 73%

---

# Configuración del acceso a Sybase IQ {#configure-access-to-sybase-iq}

Utilice la opción **Federated Data Access** (FDA) de Campaign para procesar la información almacenada en una base de datos externa. Siga los pasos a continuación para configurar el acceso a la Sybase IQ.

1. Configurar [base de datos de Sybases IQ](#configuring-sybase)
1. Configuración de la Sybase IQ [cuenta externa](#sybase-external) en Campaign

## Configuración de sybase IQ {#configuring-sybase}

La conexión a una base de datos externa de Sybase IQ en FDA requiere determinadas configuraciones adicionales en el servidor de Adobe Campaign.

>[!NOTE]
>
>Antes de empezar, asegúrese de que el paquete **unixodbc** está en el servidor.

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

## Cuenta externa de sybase IQ {#sybase-external}

La cuenta externa de Sybase IQ permite conectar la instancia de Campaign a la base de datos externa de Sybase IQ.

1. En Campaña **[!UICONTROL Explorer]**, haga clic en **[!UICONTROL Administration]** &#39;>&#39; **[!UICONTROL Platform]** &#39;>&#39; **[!UICONTROL External accounts]**.

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
