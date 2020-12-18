---
solution: Campaign Classic
product: campaign
title: Configuración de acceso a SAP HANA
description: Obtenga información sobre cómo configurar el acceso a SAP HANA en FDA
audience: platform
content-type: reference
topic-tags: connectors
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '263'
ht-degree: 71%

---


# Configuración de acceso a SAP HANA {#configure-access-to-sap-hana}

Utilice la opción Campaña [Acceso de datos federado](../../installation/using/about-fda.md) (FDA) para procesar la información almacenada en una base de datos externa. Siga los pasos a continuación para configurar el acceso a SAP HANA.

1. Configurar [base de datos de SAP HANA](#sap-config)
1. Configurar la cuenta externa [de SAP HANA](#sap-external) en Campaña

## Controladores de SAP HANA {#sap-config}

La conexión a una base de datos externa de SAP HANA en FDA requiere determinadas configuraciones adicionales en el servidor de Adobe Campaign:

1. Instale los controladores ODBC para SAP HANA según el sistema operativo que utilice:

   * **hdb_client_linux.tgz para Linux.** Una vez descomprimido, inicie el comando hdbinst y siga las instrucciones para finalizar la instalación de los controladores.
   * **hdb_client_windows.zip para Windows.** Descomprima el archivo e inicie el archivo ejecutable: **hdbinst.exe**. Siga las instrucciones del asistente para finalizar la instalación de los controladores.

1. Configure el controlador ODBC. La configuración se puede realizar en los archivos estándar: /etc/odbc.ini para obtener parámetros generales y /etc/odbcinst.ini para declarar controladores.

   * **/etc/odbc.ini**

      ```
      [ODBC]
      InstallDir=/etc/
      
      [HDB]
      Driver=HDBODBC
      servernode=localhost:39013 (this value depend of your server)
      User:SYSTEM
      ```

      &quot;InstallDir&quot; corresponde a la ubicación del archivo **odbcinst.ini**.

   * **/etc/odbcinst.ini**

      ```
      [HDBODBC]
      Description = "SmartCloudPT HANA"
      Driver = /usr/sap/hdbclient/libodbcHDB.so
      ```

1. Especifique las variables de entorno del servidor de Adobe Campaign:

   * **LD_LIBRARY_PATH**: Debe incluir el enlace a su cliente de SAP Hana (/usr/sap/hdbclient/libodbcHDB.so) de forma predeterminada).
   * **ODBCINI**: ubicación del archivo odbc.ini (por ejemplo, /etc/odbc.ini).

## CUENTA EXTERNA de SAP HANA{#sap-external}

La cuenta externa de SAP HANA permite conectar la instancia de Campaña a la base de datos externa de SAP HANA.

1. En la Campaña **[!UICONTROL Explorer]**, haga clic en **[!UICONTROL Administration]** &#39;>&#39; **[!UICONTROL Platform]** &#39;>&#39; **[!UICONTROL External accounts]**.

1. Haga clic en **[!UICONTROL New]** y seleccione **[!UICONTROL External database]** como **[!UICONTROL Type]**.

1. Para configurar la cuenta externa **[!UICONTROL SAP Hana]**, debe especificar:

   * **[!UICONTROL Type]**: SAP Hana

   * **[!UICONTROL Server]**: URL del servidor SAP Hana

   * **[!UICONTROL Account]**: Nombre del usuario

   * **[!UICONTROL Password]**: Contraseña de la cuenta de usuario
