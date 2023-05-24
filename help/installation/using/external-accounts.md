---
product: campaign
title: Cuentas externas
description: Obtenga información sobre cómo crear cuentas externas
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
audience: platform
content-type: reference
topic-tags: administration-basics
exl-id: 4a17d5e8-c73f-42e7-b641-0fee6a52c5c0
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: tm+mt
source-wordcount: '1714'
ht-degree: 65%

---

# Cuentas externas{#external-accounts}



Adobe Campaign viene con un conjunto de cuentas externas predefinidas. Para configurar conexiones con sistemas externos, puede crear nuevas cuentas externas.

Los procesos técnicos utilizan las cuentas externas como flujos de trabajo técnicos o flujos de trabajo de campaña. Por ejemplo, al configurar una transferencia de archivos en un flujo de trabajo o un intercambio de datos con cualquier otra aplicación (Adobe Target, Experience Manager, etc.), debe seleccionar una cuenta externa.

## Creación de una cuenta externa {#creating-an-external-account}

Para crear una nueva cuenta externa, siga los pasos a continuación. La configuración detallada depende del tipo de cuenta externa.

1. Desde Campaign **[!UICONTROL Explorer]**, seleccione **[!UICONTROL Administration]** &#39;>&#39; **[!UICONTROL Platform]** &#39;>&#39; **[!UICONTROL External accounts]**.

   ![](assets/ext_account_1.png)

1. Haga clic en el botón **[!UICONTROL New]**.

   ![](assets/ext_account_2.png)

1. Introduzca una **[!UICONTROL Label]** y un **[!UICONTROL Internal Name]**.
1. Seleccione la cuenta externa **[!UICONTROL Type]** que desee crear.
1. Configure el acceso a la cuenta especificando las credenciales según el tipo de cuenta externa elegida.

   La información necesaria suele ser proporcionada por el proveedor del servidor al que está conectándose.

1. Compruebe la **[!UICONTROL Enabled]** para activar la conexión.
1. Haga clic en **[!UICONTROL Save]**.

La cuenta externa se crea y se agrega a la lista de cuentas externas.

## Cuentas externas específicas de la campaña

### Correos devueltos {#bounce-mails-external-account}

La cuenta externa **Rebote de correos electrónicos** especifica la cuenta POP3 externa que se utilizará para conectar con el servicio de correo electrónico. Para obtener más información sobre esta cuenta externa, consulte esta [página](../../workflow/using/inbound-emails.md).

Todos los servidores configurados para el acceso POP3 pueden utilizarse para recibir el correo electrónico devuelto.

![](assets/ext_account_6.png)

Para configurar la cuenta externa **[!UICONTROL Bounce mails (defaultPopAccount)]**:

* **[!UICONTROL Server]**

   URL del servidor POP3.

* **[!UICONTROL Port]**

   Número de puerto de conexión POP3. El puerto predeterminado es 110.

* **[!UICONTROL Account]**

   Nombre del usuario.

* **[!UICONTROL Password]**

   Contraseña de la cuenta de usuario.

* **[!UICONTROL Encryption]**

   Tipo de cifrado elegido entre **[!UICONTROL By default]**, **[!UICONTROL POP3 + STARTTLS]**, **[!UICONTROL POP3]** o **[!UICONTROL POP3S]**.

* **[!UICONTROL Function]**

   Correo electrónico entrante o enrutador SOAP

>[!IMPORTANT]
>
>Antes de configurar la cuenta externa POP3 con Microsoft OAuth 2.0, primero debe registrar la aplicación en Azure Portal. Para obtener más información, consulte [esta página](https://docs.microsoft.com/en-us/azure/active-directory/develop/quickstart-register-app).

Para configurar un POP3 externo mediante **Microsoft OAuth 2.0**, marque la **[!UICONTROL Microsoft OAuth 2.0]** y rellene los campos siguientes:

* **[!UICONTROL Azure tenant]**

   ID de Azure (o ID de directorio (inquilino)) se puede encontrar en la **Essentials** menú desplegable de información general de la aplicación en el portal de Azure.

* **[!UICONTROL Azure Client ID]**

   ID de cliente (o ID de aplicación (cliente)) se puede encontrar en la **Essentials** menú desplegable de información general de la aplicación en el portal de Azure.

* **[!UICONTROL Azure Client secret]**

   El ID secreto de cliente se encuentra en **Secretos de cliente** de la columna **Certificados y secretos** menú de la aplicación en el portal de Azure.

* **[!UICONTROL Azure Redirect URL]**

   La URL de redireccionamiento se encuentra en **Autenticación** menú de la aplicación en el portal de Azure. Debe finalizar con la siguiente sintaxis `nl/jsp/oauth.jsp`, p. ej. `https://redirect.adobe.net/nl/jsp/oauth.jsp`.

Después de introducir las diferentes credenciales, puede hacer clic en **[!UICONTROL Setup the connection]** para finalizar la configuración de la cuenta externa.

### Enrutamiento{#routing-external-account}

La cuenta externa **[!UICONTROL Routing]** permite configurar cada canal disponible en Adobe Campaign según los paquetes instalados.

![](assets/ext_account_7.png)

Se pueden configurar los siguientes canales:

* [Correo electrónico](../../installation/using/deploying-an-instance.md#email-channel-parameters)
* [Móvil (SMS)](../../delivery/using/sms-set-up.md#creating-an-smpp-external-account)
* [Teléfono](../../delivery/using/steps-about-delivery-creation-steps.md#other-channels)
* [Correo directo](../../delivery/using/about-direct-mail-channel.md)
* [Agencia](../../delivery/using/steps-about-delivery-creation-steps.md#other-channels)
* [Twitter](../../social/using/about-social-marketing.md)
* [Canal de iOS](../../delivery/using/configuring-the-mobile-application.md)
* [Canal de Android](../../delivery/using/configuring-the-mobile-application-android.md)

### Instancia de ejecución  {#execution-instance-external-account}

Si tiene una arquitectura desglosada, es necesario especificar las instancias de ejecución vinculadas a la instancia de control y conectarlas. Las plantillas de mensajes transaccionales se implementan en las instancias de ejecución.

![](assets/ext_account_13.png)

* **[!UICONTROL URL]**

   URL del servidor en el que está instalada la instancia de ejecución.

* **[!UICONTROL Account]**

   El nombre de la cuenta debe coincidir con el Agente del centro de mensajes definido en la carpeta del operador.

* **[!UICONTROL Password]**

   Contraseña de la cuenta tal como se define en la carpeta del operador.

Para obtener más información sobre esta configuración, consulte esta [página](../../message-center/using/configuring-instances.md#control-instance).

## Acceso a cuentas externas de sistemas externos

### FTP {#ftp-external-account}

La cuenta externa de FTP permite configurar y probar el acceso a un servidor fuera de Adobe Campaign. Para configurar conexiones con sistemas externos como servidores FTP 898 utilizados para transferencias de archivos, puede crear sus propias cuentas externas. Para obtener más información, consulte [esta página](../../workflow/using/file-transfer.md).

Especifique en esta cuenta externa la dirección y las credenciales utilizadas para establecer la conexión con el servidor FTP.

![](assets/ext_account_8.png)

* **[!UICONTROL Server]**

   Nombre del servidor FTP.

* **[!UICONTROL Port]**

   Número de puerto de conexión FTP. El puerto predeterminado es 21.

* **[!UICONTROL Account]**

   Nombre del usuario.

* **[!UICONTROL Password]**

   Contraseña de la cuenta de usuario.

* **[!UICONTROL Encryption]**

   Tipo de cifrado elegido entre **[!UICONTROL None]** o **[!UICONTROL SSL]**.

Para saber dónde ubicar estas credenciales, consulte esta [página](https://help.dreamhost.com/hc/en-us/articles/115000675027-FTP-overview-and-credentials).

### SFTP {#sftp-external-account}

La cuenta externa SFTP permite configurar y probar el acceso a un servidor fuera de Adobe Campaign. Para configurar conexiones con sistemas externos como SFTP utilizados para transferencias de archivos, puede crear cuentas externas propias. Para obtener más información, consulte [esta página](../../workflow/using/file-transfer.md).

![](assets/ext_account_4.png)

* **[!UICONTROL Server]**

   URL del servidor SFTP.

* **[!UICONTROL Port]**

   Número de puerto de conexión FTP. El puerto predeterminado es 22.

* **[!UICONTROL Account]**

   Nombre de cuenta utilizado para conectarse al servidor SFTP.

* **[!UICONTROL Password]**

   Contraseña utilizada para conectarse al servidor SFTP.

Para añadir claves SSH en Windows:

1. Cree el **INICIO** variable de entorno con valor establecido como directorio de instalación.

2. Agregue su clave privada a `/$HOME/.ssh/id_rsa` carpeta.

3. Reinicie los servicios de Adobe Campaign.

### Base de datos externa (FDA) {#external-database-external-account}

Utilice el **Base de datos externa** escriba external account para conectarse a una base de datos externa. Obtenga más información acerca de la opción de acceso de datos federado (FDA) en [esta sección](../../installation/using/about-fda.md).

Las bases de datos externas compatibles con Campaign se enumeran en la [Matriz de compatibilidad](../../rn/using/compatibility-matrix.md)

![](assets/ext_account_11.png)

Las opciones de configuración de cuenta externa dependen del motor de la base de datos. Obtenga más información en las siguientes secciones:

* Configuración del acceso a [Verticas analytics](../../installation/using/configure-fda-vertica.md)
* Configuración del acceso a [Snowflake](../../installation/using/configure-fda-snowflake.md)
* Configuración del acceso a [Google BigQuery](../../installation/using/configure-fda-google-big-query.md)
* Configuración del acceso a [Azure synapse](../../installation/using/configure-fda-synapse.md)
* Configuración del acceso a [Hadoop](../../installation/using/configure-fda-hadoop.md)
* Configuración del acceso a [Oracle](../../installation/using/configure-fda-oracle.md)
* Configuración del acceso a [Netezza](../../installation/using/configure-fda-netezza.md)
* Configuración del acceso a [SAP HANA](../../installation/using/configure-fda-sap-hana.md)
* Configuración del acceso a [Snowflake](../../installation/using/configure-fda-snowflake.md)
* Configuración del acceso a [Sybase IQ](../../installation/using/configure-fda-sybase.md)
* Configuración del acceso a [Teradata](../../installation/using/configure-fda-teradata.md)


## Adobe Integración de soluciones Cuentas externas

### Adobe Experience Cloud {#adobe-experience-cloud-external-account}

Para conectarse a la consola de Adobe Campaign mediante un Adobe ID, debe configurar la cuenta externa de **[!UICONTROL Adobe Experience Cloud (MAC)]**.

![](assets/ext_account_9.png)

* **[!UICONTROL IMS server]**

   URL del servidor IMS. Asegúrese de que las instancias de ensayo y de producción indiquen el mismo punto final de producción IMS.

* **[!UICONTROL IMS scope]**

   Los ámbitos definidos aquí deben ser un subconjunto de los que proporciona IMS.

* **[!UICONTROL IMS client identifier]**

   ID de su cliente IMS.

* **[!UICONTROL IMS client secret]**

   Credencial del secreto de su cliente IMS.

* **[!UICONTROL Callback server]**

   Acceso URL de su instancia de Adobe Campaign.

* **[!UICONTROL IMS organization ID]**

   ID de la organización Para encontrar su ID de organización, consulte [esta página](https://experienceleague.adobe.com/docs/core-services/interface/administration/organizations.html?lang=es){_blank}.

* **[!UICONTROL Association mask]**

   Sintaxis que permitirá nombres de configuración en Enterprise Dashboard para sincronizar con los grupos en Adobe Campaign.

* **[!UICONTROL Server]**

   URL de su instancia de Adobe Experience Cloud.

* **[!UICONTROL Tenant]**

   Nombre su inquilino de Adobe Experience Cloud.

Para obtener más información, consulte [esta página](../../integrations/using/configuring-ims.md).

## Web Analytics {#web-analytics-external-account}

La cuenta externa **[!UICONTROL Web Analytics]** permite reenviar datos de Adobe Analytics a Adobe Campaign en forma de segmentos. Por el contrario, envía indicadores y atributos de las campañas de correo electrónico que envía Adobe Campaign al conector de Adobe Analytics.

![](assets/ext_account_10.png)

Para esta cuenta externa, la fórmula de cálculo para URL rastreadas debe ser enriquecida y la conexión entre las dos soluciones debe ser aprobada. Para obtener más información, consulte [esta página](../../platform/using/adobe-analytics-connector.md#external-account-classic).

### Adobe Experience Manager {#adobe-experience-manager-external-account}

La cuenta externa **[!UICONTROL AEM (AEM instance)]** permite administrar el contenido de los envíos de correos electrónicos y los formularios directamente en Adobe Experience Manager.

![](assets/ext_account_5.png)

* **[!UICONTROL Server]**

   URL del servidor de Adobe Experience Manager.

* **[!UICONTROL Port]**

   Nombre de la cuenta que se utiliza para conectarse a la instancia de creación de Adobe Experience Manager.

* **[!UICONTROL Password]**

   La contraseña utilizada para conectarse a la instancia de autor de Adobe Experience Manager.

Para obtener más información, consulte [esta sección](../../integrations/using/about-adobe-experience-manager.md).

## Cuentas externas del conector CRM

### Microsoft Dynamics CRM {#microsoft-dynamics-crm-external-account}

>[!NOTE]
>
> **[!UICONTROL On-premise]** y **[!UICONTROL Office 365]** los tipos de implementación ya no se utilizan. [Más información](../../rn/using/deprecated-features.md).

La cuenta externa **[!UICONTROL Microsoft Dynamics CRM]** permite importar y exportar datos de Microsoft Dynamics en Adobe Campaign.

Obtenga más información acerca del conector CRM de Campaign - Microsoft Dynamics en esta [página](../../platform/using/crm-ms-dynamics.md).

Con el tipo de implementación **[!UICONTROL Web API]** y la autenticación **[!UICONTROL Password credentials]**, debe proporcionar los siguientes detalles:

![](assets/ext_account_14.png)

* **[!UICONTROL Account]**

   Cuenta utilizada para iniciar sesión en Microsoft CRM.

* **[!UICONTROL Server]**

   URL del servidor Microsoft CRM.

   Para encontrar su Microsoft CRM **[!UICONTROL Server URL]**, acceda a su cuenta de Microsoft Dynamics CRM y haga clic en **Dynamics 365** y seleccione su aplicación. A continuación, puede encontrar su **[!UICONTROL Server URL]** en la barra de direcciones del navegador, p. ej., `https://myserver.crm.dynamics.com/`.

* **[!UICONTROL Client identifier]**

   El ID del cliente se puede encontrar desde el portal de administración de Microsoft Azure en la categoría **[!UICONTROL Update your code]**, campo **[!UICONTROL Client ID]**.

* **[!UICONTROL CRM version]**

   Elegir **[!UICONTROL Dynamics CRM 365]** Versión de CRM.

Con el tipo de implementación **[!UICONTROL Web API]** y la autenticación **[!UICONTROL Certificate]**, debe proporcionar los siguientes detalles:

![](assets/ext_account_22.png)

* **[!UICONTROL Server]**

   URL del servidor Microsoft CRM.

   Para encontrar su Microsoft CRM **[!UICONTROL Server URL]**, acceda a su cuenta de Microsoft Dynamics CRM y haga clic en **Dynamics 365** y seleccione su aplicación. A continuación, puede encontrar su **[!UICONTROL Server URL]** en la barra de direcciones del navegador, p. ej., `https://myserver.crm.dynamics.com/`.

* **[!UICONTROL Private Key (Base64 encoded)]**

   Tenga en cuenta que la clave privada debe codificarse en Base64.

   Para ello, puede utilizar la ayuda de un codificador Base64 o utilizar la línea de comandos `base64 -w0 private.key` para Linux.

* **[!UICONTROL Custom Key identifier]**

* **[!UICONTROL Key ID]**

* **[!UICONTROL Client identifier]**

   El ID del cliente se puede encontrar desde el portal de administración de Microsoft Azure en la categoría **[!UICONTROL Update your code]**, campo **[!UICONTROL Client ID]**.

* **[!UICONTROL CRM version]**

   Versión de la CRM entre **[!UICONTROL Dynamics CRM 2007]**, **[!UICONTROL Dynamics CRM 2015]** o **[!UICONTROL Dynamics CRM 2016]**.

Para obtener más información sobre esta configuración, consulte esta [página](../../platform/using/crm-connectors.md).

### Salesforce.com CRM  {#salesforce-crm-external-account}

La cuenta externa **[!UICONTROL Salesforce CRM]** permite importar y exportar datos de Salesforce a Adobe Campaign.

![](assets/ext_account_17.png)

Para configurar la cuenta externa de Salesforce CRM para que funcione con Adobe Campaign, proporcione los siguientes detalles:

* **[!UICONTROL Account]**

   Cuenta utilizada para iniciar sesión en Salesforce CRM.

* **[!UICONTROL Password]**

   Contraseña utilizada para iniciar sesión en Salesforce CRM.

* **[!UICONTROL Client identifier]**

   Para saber dónde encontrar el identificador de cliente, consulte esta [página](https://help.salesforce.com/articleView?id=000205876&amp;type=1).

* **[!UICONTROL Security token]**

   Para saber dónde encontrar el token de seguridad, consulte esta [página](https://help.salesforce.com/articleView?id=000205876&amp;type=1).

* **[!UICONTROL API version]**

   Seleccione la versión de la API.

Para esta cuenta externa, debe configurar Salesforce CRM con el asistente para configuración.

Para obtener más información sobre esta configuración, consulte esta [página](../../platform/using/crm-connectors.md).

## Transferir datos a cuentas externas

### Amazon Simple Storage Service (S3) {#amazon-simple-storage-service--s3--external-account}

El conector de Amazon Simple Storage Service (S3) se puede utilizar para importar o exportar datos a Adobe Campaign. Se puede configurar en una actividad de flujo de trabajo. Para obtener más información, consulte [esta página](../../workflow/using/file-transfer.md).

![](assets/ext_account_3.png)

Al configurar esta nueva cuenta externa, debe proporcionar los siguientes detalles:

* **[!UICONTROL AWS S3 Account Server]**

   La URL del servidor debe completarse de la siguiente manera:

   ```
   <S3bucket name>.s3.amazonaws.com/<s3object path>
   ```

* **[!UICONTROL AWS access key ID]**

   Para saber dónde encontrar el ID de clave de acceso de AWS, consulte [esta página](https://docs.aws.amazon.com/general/latest/gr/aws-sec-cred-types.html#access-keys-and-secret-access-keys).

* **[!UICONTROL Secret access key to AWS]**

   Para saber dónde encontrar la clave de acceso secreta a AWS, consulte [esta página](https://aws.amazon.com/fr/blogs/security/wheres-my-secret-access-key/).

* **[!UICONTROL AWS Region]**

   Para obtener más información sobre la región AWS, consulte esta [página](https://aws.amazon.com/about-aws/global-infrastructure/regions_az/).

* La casilla de verificación **[!UICONTROL Use server side encryption]** permite almacenar el archivo en modo codificado S3.

Para saber dónde encontrar el ID de clave de acceso y la clave de acceso secreta, consulte la [documentación](https://docs.aws.amazon.com/general/latest/gr/aws-sec-cred-types.html#access-keys-and-secret-access-keys) de los servicios web de Amazon.

### Azure Blob Storage {#azure-blob-external-account}

El **Azure Blob Storage** una cuenta externa de se puede utilizar para importar o exportar datos a Adobe Campaign mediante una **[!UICONTROL Transfer file]** actividad de flujo de trabajo. Para obtener más información, consulte [esta sección](../../workflow/using/file-transfer.md).

![](assets/ext_account_23.png)

Para configurar la variable **[!UICONTROL Azure external account]** para trabajar con Adobe Campaign, debe proporcionar los siguientes detalles:

* **[!UICONTROL Server]**

   URL del servidor de Azure Blob Storage.

* **[!UICONTROL Encryption]**

   Tipo de cifrado elegido entre **[!UICONTROL None]** o **[!UICONTROL SSL]**.

* **[!UICONTROL Access key]**

   Para saber dónde encontrar su **[!UICONTROL Access key]**, consulte esta [página](https://docs.microsoft.com/en-us/azure/storage/common/storage-account-keys-manage?tabs=azure-portal).
