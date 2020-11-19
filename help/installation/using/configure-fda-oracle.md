---
title: Configuración del acceso a Oracle
description: Obtenga información sobre cómo configurar el acceso a Oracle en FDA
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
source-wordcount: '352'
ht-degree: 74%

---


# Configuración del acceso a Oracle {#configure-access-to-oracle}

Utilice la opción [Acceso de datos federado](../../installation/using/about-fda.md) de Campaña (FDA) para procesar la información almacenada en una base de datos externa. Siga los pasos a continuación para configurar el acceso a Oracle.

1. Configurar Oracle en [Linux](#oracle-linux) o [Windows](#azure-windows)
1. Configurar la [cuenta externa](#oracle-external) de Oracle en Campaña

## Oracle en Linux {#oracle-linux}

La conexión a una base de datos externa de Oracle en FDA requiere ciertas configuraciones adicionales en el servidor de Adobe Campaign.

1. Instale el cliente completo Oracle correspondiente a su versión de Oracle.
1. Añada sus definiciones de TNS a la instalación. Para ello, debe especificarlas en un archivo **tnsnames.ora** en el repositorio /etc/oracle. Si este repositorio no existe, créelo.

   A continuación, cree una nueva variable de entorno TNS_ADMIN: exporte TNS_ADMIN=/etc/oracle y reinicie el equipo.

1. Integre Oracle en el servidor de Adobe Campaign (nlserver). Para ello, compruebe que el archivo **customer.sh** esté presente en la carpeta &quot;nl6&quot; de la estructura del árbol de servidor de Adobe Campaign y que incluye los enlaces a las bibliotecas de Oracle.

   Por ejemplo, para un cliente en 11.2:

   ```
   export ORACLE_HOME=/usr/lib/oracle/11.2
   export TNS_ADMIN=/etc/oracle
   export LD_LIBRARY_PATH=$ORACLE_HOME/client64/lib:$LD_LIBRARY_PATH
   ```

   >[!NOTE]
   >
   >Estos valores (especialmente ORACLE_HOME) dependen de los repositorios de instalación. Asegúrese de comprobar la estructura del árbol antes de hacer referencia a estos valores.

1. Instale las bibliotecas necesarias para Oracle:

   * **libclntsh.so**

      ```
      cd /usr/lib/oracle/<version>/client<architecture>/lib
      ln -s libclntsh.so.<version> libclntsh.so
      ```

   * **libaio1**

      ```
      aptitude install libaio1
      or
      yum install libaio1
      ```

1. En Campaign Classic, puede configurar la cuenta externa [!DNL Oracle]. For more on how to configure your external account, refer to [this section](#oracle-external).

## Oracle en Windows {#oracle-windows}

La conexión a una base de datos externa de Oracle en FDA requiere ciertas configuraciones adicionales en el servidor de Adobe Campaign.

1. Instale el cliente Oracle.

1. En la carpeta C:\Oracle, cree un archivo **tnsnames.ora** con la definición de TNS.

1. Añada una variable de entorno TNS_ADMIN con C:\Oracle como valor y reinicie el equipo.

1. En Campaign Classic, puede configurar la cuenta externa [!DNL Oracle]. For more on how to configure your external account, refer to [this section](#oracle-external).

## Cuenta externa de Oracle {#oracle-external}

The [!DNL Oracle] external account allows you to connect your Campaign instance to your Oracle external database.

1. En la Campaña **[!UICONTROL Explorer]**, seleccione **[!UICONTROL Administration]** &#39;>&#39; **[!UICONTROL Platform]** &#39;>&#39; **[!UICONTROL External accounts]**.

1. Elija **[!UICONTROL New]**.

1. Seleccione **[!UICONTROL External database]** como **[!UICONTROL Type]** de su cuenta externa.

1. Configure la cuenta externa **[!UICONTROL Oracle]**. Debe especificar:

   * **[!UICONTROL Type]**: Oracle

   * **[!UICONTROL Server]**: Nombre del DNS

   * **[!UICONTROL Account]**: Nombre del usuario

   * **[!UICONTROL Password]**: Contraseña de la cuenta de usuario

   * **[!UICONTROL Time zone]**: Zona horaria del servidor

   ![](assets/oracle_config.png)

