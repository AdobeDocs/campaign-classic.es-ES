---
product: campaign
title: Configuración del acceso a Oracle
description: Obtenga información sobre cómo configurar el acceso al Oracle en FDA
audience: platform
content-type: reference
topic-tags: connectors
exl-id: 320bfbb4-533b-4c45-a46f-c3c8dd68221f
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: tm+mt
source-wordcount: '352'
ht-degree: 74%

---

# Configuración del acceso a Oracle {#configure-access-to-oracle}

Utilice la opción [Federated Data Access](../../installation/using/about-fda.md) (FDA) de Campaign para procesar la información almacenada en una base de datos externa. Siga los pasos a continuación para configurar el acceso a Oracle.

1. Configurar el Oracle en [Linux](#oracle-linux) o [Windows](#azure-windows)
1. Configurar el Oracle [cuenta externa](#oracle-external) en Campaign

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

1. En Campaign Classic, puede configurar la cuenta externa [!DNL Oracle]. Para obtener más información sobre cómo configurar la cuenta externa, consulte [esta sección](#oracle-external).

## Oracle en Windows {#oracle-windows}

La conexión a una base de datos externa de Oracle en FDA requiere ciertas configuraciones adicionales en el servidor de Adobe Campaign.

1. Instale el cliente Oracle.

1. En la carpeta C:\Oracle, cree un archivo **tnsnames.ora** con la definición de TNS.

1. Añada una variable de entorno TNS_ADMIN con C:\Oracle como valor y reinicie el equipo.

1. En Campaign Classic, puede configurar la cuenta externa [!DNL Oracle]. Para obtener más información sobre cómo configurar la cuenta externa, consulte [esta sección](#oracle-external).

## Cuenta externa de Oracle {#oracle-external}

La cuenta externa [!DNL Oracle] permite conectar la instancia de Campaign a la base de datos externa de Oracle.

1. En Campaña **[!UICONTROL Explorer]**, seleccione **[!UICONTROL Administration]** &#39;>&#39; **[!UICONTROL Platform]** &#39;>&#39; **[!UICONTROL External accounts]**.

1. Elija **[!UICONTROL New]**.

1. Seleccione **[!UICONTROL External database]** como **[!UICONTROL Type]** de su cuenta externa.

1. Configure la cuenta externa **[!UICONTROL Oracle]**. Debe especificar:

   * **[!UICONTROL Type]**: Oracle

   * **[!UICONTROL Server]**: Nombre del DNS

   * **[!UICONTROL Account]**: Nombre del usuario

   * **[!UICONTROL Password]**: Contraseña de la cuenta de usuario

   * **[!UICONTROL Time zone]**: Zona horaria del servidor
   ![](assets/oracle_config.png)
