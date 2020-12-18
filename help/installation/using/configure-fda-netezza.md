---
solution: Campaign Classic
product: campaign
title: Configuración del acceso a Netezza
description: Obtenga información sobre cómo configurar el acceso a Netezza en FDA
audience: platform
content-type: reference
topic-tags: connectors
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '374'
ht-degree: 81%

---


# Configuración del acceso a Netezza {#configure-access-to-netezza}

Utilice la opción Campaña [Acceso de datos federado](../../installation/using/about-fda.md) (FDA) para procesar la información almacenada en una base de datos externa. Siga los pasos a continuación para configurar el acceso a Netezza.

1. Instalar y configurar [controladores de Netezza](#netezza-config)
1. Configurar la cuenta externa [de Netezza](#netezza-external) en Campaña

## Configuración de netezza {#netezza-config}

La conexión a una base de datos externa de Netezza en FDA requiere ciertas configuraciones adicionales en el servidor de Adobe Campaign:

1. Instale los controladores ODBC para Netezza según el sistema operativo que utilice:

   * **nz-linuxclient-v7.2.0.0.tar.gz para Linux.** Seleccione la carpeta correspondiente a su sistema operativo (linux o linux64) e inicie el comando descomprimir. Puede dejar que la instalación se realice en el repositorio que sugerido de forma predeterminada: &quot;/usr/local/nz&quot;.
   * **nz-winclient-v7.2.0.0.zip para Windows.** Descomprima el archivo e inicie la secuencia de comandos ejecutable correspondiente a su sistema operativo: nzodbcsetup.exe o nzodbcsetup64.exe. Siga las instrucciones del asistente para finalizar la instalación de los controladores.

1. Configure el controlador ODBC. La configuración se puede realizar en los archivos estándar: **/etc/odbc.ini** para obtener parámetros generales y **/etc/odbcinst.ini** para declarar controladores.

   * **/etc/odbc.ini**

      ```
      [ODBC]
      InstallDir=/etc/
      ```

      &quot;InstallDir&quot; corresponde a la ubicación del archivo odbcinst.ini.

   * **/etc/odbcinst.ini**

      ```
      [ODBC Drivers]
      NetezzaSQL = Installed
      
      [NetezzaSQL]
      Driver           = /usr/local/nz/lib/libnzsqlodbc3.so
      Setup            = /usr/local/nz/lib/libnzsqlodbc3.so
      APILevel         = 1
      ConnectFunctions = YYN
      Description      = Netezza ODBC driver
      DriverODBCVer    = 03.51
      DebugLogging     = false
      LogPath          = /tmp
      UnicodeTranslationOption = utf8
      CharacterTranslationOption = all
      PreFetch         = 256
      Socket           = 16384
      ```

1. Especifique las variables de entorno del servidor de Adobe Campaign:

   * **LD_LIBRARY_PATH**: /usr/local/nz/lib y /usr/local/nz/lib64. &quot;/usr/local/nz&quot; corresponde al repositorio de instalación ofrecido de forma predeterminada al instalar los controladores. Aquí debe especificar el repositorio que ha seleccionado para la instalación.
   * **ODBCINI**: ubicación del archivo odbc.ini (por ejemplo, /etc/odbc.ini).
   * **NZ_ODBC_INI_PATH**: ubicación del archivo odbc.ini. Netezza también requiere esta segunda variable para utilizar el archivo odbc.ini.

## Cuenta externa de netezza {#netezza-external}

La cuenta externa de Netezza permite conectar la instancia de Campaña a la base de datos externa de Netezza.

1. En la Campaña **[!UICONTROL Explorer]**, haga clic en **[!UICONTROL Administration]** &#39;>&#39; **[!UICONTROL Platform]** &#39;>&#39; **[!UICONTROL External accounts]**.

1. Haga clic en **[!UICONTROL New]** y seleccione **[!UICONTROL External database]** como **[!UICONTROL Type]**.

1. Para configurar la cuenta externa **[!UICONTROL Netezza]**, debe especificar:

   * **[!UICONTROL Type]**: Netezza

   * **[!UICONTROL Server]**: URL del servidor de Netezza

   * **[!UICONTROL Account]**: Nombre del usuario

   * **[!UICONTROL Password]**: Contraseña de la cuenta de usuario

   * **[!UICONTROL Database]**: Nombre de la base de datos

>[!NOTE]
>
>Las operaciones en los esquemas que contienen claves principales generadas automáticamente no se tienen en cuenta.
>
>La tabla utiliza la cláusula **Organize on** en el primer índice definido en el esquema. Dado que esta cláusula está limitada a entre 1 y 4 columnas con Netezza, este índice no puede contener más de 4 columnas.
