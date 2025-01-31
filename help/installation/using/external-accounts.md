---
product: campaign
title: Cuentas externas
description: Obtenga información sobre cómo crear cuentas externas
feature: Installation, Application Settings, External Account
audience: platform
content-type: reference
topic-tags: administration-basics
exl-id: 4a17d5e8-c73f-42e7-b641-0fee6a52c5c0
source-git-commit: 0ed70b3c57714ad6c3926181334f57ed3b409d98
workflow-type: tm+mt
source-wordcount: '1784'
ht-degree: 57%

---

# Cuentas externas{#external-accounts}

Adobe Campaign viene con un conjunto de cuentas externas predefinidas. Para configurar conexiones con sistemas externos, puede crear nuevas cuentas externas.

Los procesos técnicos utilizan las cuentas externas como flujos de trabajo técnicos o flujos de trabajo de campaña. Por ejemplo, al configurar una transferencia de archivos en un flujo de trabajo o un intercambio de datos con cualquier otra aplicación (Adobe Target, Experience Manager, etc.), debe seleccionar una cuenta externa.

## Creación de una cuenta externa {#creating-an-external-account}

Para crear una nueva cuenta externa, siga los pasos a continuación. La configuración detallada depende del tipo de cuenta externa.

1. En la campaña **[!UICONTROL Explorer]**, seleccione **[!UICONTROL Administration]** &#39;>&#39; **[!UICONTROL Platform]** &#39;>&#39; **[!UICONTROL External accounts]**.

   ![](assets/ext_account_1.png)

1. Haga clic en el botón **[!UICONTROL New]**.

   ![](assets/ext_account_2.png)

1. Escriba **[!UICONTROL Label]** y **[!UICONTROL Internal Name]**.
1. Seleccione la cuenta externa **[!UICONTROL Type]** que desee crear.
1. Configure el acceso a la cuenta especificando las credenciales según el tipo de cuenta externa elegida.

   La información necesaria suele ser proporcionada por el proveedor del servidor al que está conectándose.

1. Marque la opción **[!UICONTROL Enabled]** para activar la conexión.
1. Haga clic en **[!UICONTROL Save]**.

La cuenta externa se crea y se agrega a la lista de cuentas externas.

## Cuentas externas específicas de la campaña

### Correos rechazados {#bounce-mails-external-account}

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

  SOAP Correo electrónico entrante o enrutador de

>[!IMPORTANT]
>
>Antes de configurar la cuenta externa POP3 con Microsoft OAuth 2.0, primero debe registrar la aplicación en Azure Portal. Para obtener más información, consulte [esta página](https://docs.microsoft.com/en-us/azure/active-directory/develop/quickstart-register-app).

Para configurar una cuenta externa POP3 con **Microsoft OAuth 2.0**, marque la opción **[!UICONTROL Microsoft OAuth 2.0]** y rellene los campos siguientes:

* **[!UICONTROL Azure tenant]**

  Azure ID (o Directory (tenant) ID) se encuentra en la lista desplegable **Essentials** de la descripción general de la aplicación en el portal de Azure.

* **[!UICONTROL Azure Client ID]**

  El ID de cliente (o el ID de aplicación (cliente)) se encuentran en la lista desplegable **Essentials** de la descripción general de la aplicación en el portal de Azure.

* **[!UICONTROL Azure Client secret]**

  La ID de secreto de cliente se encuentra en la columna **Secretos de cliente** del menú **Certificados y secretos** de su aplicación en el portal de Azure.

* **[!UICONTROL Azure Redirect URL]**

  La URL de redireccionamiento se encuentra en el menú **Autenticación** de su aplicación en el portal de Azure. Debe finalizar con la siguiente sintaxis `nl/jsp/oauth.jsp`, p. ej. `https://redirect.adobe.net/nl/jsp/oauth.jsp`.

Se necesita acceso a Internet para configurar y utilizar el botón **[!UICONTROL Test Connection]** en la consola del cliente. Después de la configuración, el proceso de inMail puede comunicarse con los servidores de Microsoft sin Internet.

Después de escribir las diferentes credenciales, puede hacer clic en **[!UICONTROL Setup the connection]** para finalizar la configuración de la cuenta externa.

### Enrutamiento{#routing-external-account}

La cuenta externa **[!UICONTROL Routing]** permite configurar cada canal disponible en Adobe Campaign según los paquetes instalados.

![](assets/ext_account_7.png)

Se pueden configurar los siguientes canales:

* [Correo electrónico](#email-routing-external-account)
* [Móvil (SMS)](../../delivery/using/sms-set-up.md#creating-an-smpp-external-account)
* [Teléfono](../../delivery/using/communication-channels.md#other-channels)
* [Correo directo](../../delivery/using/about-direct-mail-channel.md)
* [Agencia](../../delivery/using/communication-channels.md#other-channels)
* [X (anteriormente conocido como Twitter)](../../social/using/about-social-marketing.md)
* [Canal de iOS](../../delivery/using/configuring-the-mobile-application.md)
* [Canal de Android](../../delivery/using/configuring-the-mobile-application-android.md)

### Enrutamiento de correo electrónico {#email-routing-external-account}

La cuenta externa de enrutamiento de correo electrónico se proporciona de forma predeterminada y se adapta a la configuración.

Como cliente on-premise/híbrido, puede crear nuevas cuentas externas de enrutamiento o actualizar parámetros, tal como se describe a continuación. Esta configuración está reservada para usuarios expertos y puede afectar a la capacidad de envío. Para cualquier pregunta, póngase en contacto con el Servicio de atención al cliente de Adobe o con su representante del Adobe.

* Puede usar un tipo de enrutamiento de **intermediario**, **externo** o **envío masivo**.

* Para los modos de entrega **Bulk** y **Mid-sourcing**, puede especificar los parámetros de marca en la pestaña **Branding**. Estos parámetros se usan para anular los [parámetros predeterminados](../../installation/using/deploying-an-instance.md#email-channel-parameters) de **URL de la página espejo** y **Dirección de error** con la configuración específica de su marca.

  ![](assets/ext-account-branding.png)

* Para configurar una cuenta externa intermediaria, consulte [esta sección](mid-sourcing-server.md)

### Instancia de ejecución  {#execution-instance-external-account}

Si tiene una arquitectura desglosada, es necesario especificar las instancias de ejecución vinculadas a la instancia de control y conectarlas. Las plantillas de mensajes transaccionales se implementan en la instancia de ejecución.

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

<!--To add SSH keys on Windows:

1. Create the **HOME** environment variable with value set as the installation directory.

2. Add your private key to the `/$HOME/.ssh/id_rsa` folder.

3. Restart the Adobe Campaign services.
-->

### Base de datos externa (FDA) {#external-database-external-account}

Use la cuenta externa de tipo **Base de datos externa** para conectarse a una base de datos externa. Obtenga más información acerca de la opción de acceso de datos federado (FDA) en [esta sección](../../installation/using/about-fda.md).

Las bases de datos externas compatibles con Campaign se enumeran en la [matriz de compatibilidad](../../rn/using/compatibility-matrix.md)

![](assets/ext_account_11.png)

Las opciones de configuración de cuenta externa dependen del motor de la base de datos. Obtenga más información en las siguientes secciones:

* Configurar el acceso a [Verticas analytics](../../installation/using/configure-fda-vertica.md)
* Configurar el acceso a [Snowflake](../../installation/using/configure-fda-snowflake.md)
* Configurar el acceso a [Google BigQuery](../../installation/using/configure-fda-google-big-query.md)
* Configurar el acceso a [Azure synapse](../../installation/using/configure-fda-synapse.md)
* Configurar el acceso a [Hadoop](../../installation/using/configure-fda-hadoop.md)
* Configurar el acceso a [Oracle](../../installation/using/configure-fda-oracle.md)
* Configurar el acceso a [Netezza](../../installation/using/configure-fda-netezza.md)
* Configurar el acceso a [SAP HANA](../../installation/using/configure-fda-sap-hana.md)
* Configurar el acceso a [Snowflake](../../installation/using/configure-fda-snowflake.md)
* Configurar el acceso a [Sybase IQ](../../installation/using/configure-fda-sybase.md)
* Configurar el acceso a [Teradata](../../installation/using/configure-fda-teradata.md)


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

  ID de su organización. Para encontrar su ID de organización, consulte [esta página](https://experienceleague.adobe.com/docs/core-services/interface/administration/organizations.html?lang=es){_blank}.

* **[!UICONTROL Association mask]**

  Sintaxis que permitirá nombres de configuración en Enterprise Dashboard para sincronizar con los grupos en Adobe Campaign.

* **[!UICONTROL Server]**

  URL de su instancia de Adobe Experience Cloud.

* **[!UICONTROL Tenant]**

  Nombre su inquilino de Adobe Experience Cloud.

Para obtener más información sobre esta configuración, consulte [esta página](../../integrations/using/configuring-ims.md).

## Análisis web {#web-analytics-external-account}

La cuenta externa **[!UICONTROL Web Analytics]** permite reenviar datos de Adobe Analytics a Adobe Campaign en forma de segmentos. Por el contrario, envía indicadores y atributos de las campañas de correo electrónico que envía Adobe Campaign al conector de Adobe Analytics.

![](assets/ext_account_10.png)

Para esta cuenta externa, la fórmula de cálculo para URL rastreadas debe ser enriquecida y la conexión entre las dos soluciones debe ser aprobada. Para obtener más información, consulte [esta página](../../integrations/using/gs-aa.md).

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
> Los tipos de implementación **[!UICONTROL On-premise]** y **[!UICONTROL Office 365]** ya no se utilizan. [Más información](../../rn/using/deprecated-features.md).

La cuenta externa **[!UICONTROL Microsoft Dynamics CRM]** permite importar y exportar datos de Microsoft Dynamics en Adobe Campaign.

Obtenga más información acerca del conector CRM de Campaign - Microsoft Dynamics en esta [página](../../platform/using/crm-ms-dynamics.md).

Con el tipo de implementación **[!UICONTROL Web API]** y la autenticación **[!UICONTROL Password credentials]**, debe proporcionar los siguientes detalles:

![](assets/ext_account_14.png)

* **[!UICONTROL Account]**

  Cuenta utilizada para iniciar sesión en Microsoft CRM.

* **[!UICONTROL Server]**

  URL del servidor Microsoft CRM.

  Para encontrar su Microsoft CRM **[!UICONTROL Server URL]**, acceda a su cuenta de Microsoft Dynamics CRM, haga clic en **Dynamics 365** y seleccione su aplicación. Luego puede encontrar su **[!UICONTROL Server URL]** en la barra de direcciones de su explorador, por ejemplo: `https://myserver.crm.dynamics.com/`.

* **[!UICONTROL Client identifier]**

  El ID del cliente se puede encontrar desde el portal de administración de Microsoft Azure en la categoría **[!UICONTROL Update your code]**, campo **[!UICONTROL Client ID]**.

* **[!UICONTROL CRM version]**

  Elija **[!UICONTROL Dynamics CRM 365]** versión de CRM.

Con el tipo de implementación **[!UICONTROL Web API]** y la autenticación **[!UICONTROL Certificate]**, debe proporcionar los siguientes detalles:

![](assets/ext_account_22.png)

* **[!UICONTROL Server]**

  URL del servidor Microsoft CRM.

  Para encontrar su Microsoft CRM **[!UICONTROL Server URL]**, acceda a su cuenta de Microsoft Dynamics CRM, haga clic en **Dynamics 365** y seleccione su aplicación. Luego puede encontrar su **[!UICONTROL Server URL]** en la barra de direcciones de su explorador, por ejemplo: `https://myserver.crm.dynamics.com/`.

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

Para esta cuenta externa, debe configurar Salesforce CRM con el asistente de configuración.

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

La cuenta externa **Azure Blob storage** se puede usar para importar o exportar datos a Adobe Campaign mediante una actividad de flujo de trabajo **[!UICONTROL Transfer file]**. Para obtener más información, consulte [esta sección](../../workflow/using/file-transfer.md).

![](assets/ext_account_23.png)

Para configurar **[!UICONTROL Azure external account]** para que funcione con Adobe Campaign, debe proporcionar los siguientes detalles:

* **[!UICONTROL Server]**

  URL del servidor de Azure Blob Storage.

* **[!UICONTROL Encryption]**

  Tipo de cifrado elegido entre **[!UICONTROL None]** o **[!UICONTROL SSL]**.

* **[!UICONTROL Access key]**

  Para saber dónde encontrar su **[!UICONTROL Access key]**, consulte esta [página](https://docs.microsoft.com/en-us/azure/storage/common/storage-account-keys-manage?tabs=azure-portal).
