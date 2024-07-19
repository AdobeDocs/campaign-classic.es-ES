---
product: campaign
title: 'Campaign: Conector CRM de Microsoft Dynamics'
description: Obtenga información sobre cómo conectar Campaign y Microsoft Dynamics
feature: Microsoft CRM Integration
exl-id: 26737940-b3ce-425c-9604-f4cefd19afaa
source-git-commit: b666535f7f82d1b8c2da4fbce1bc25cf8d39d187
workflow-type: tm+mt
source-wordcount: '1104'
ht-degree: 100%

---

# Conexión de Campaign y Microsoft Dynamics 365{#connect-to-msdyn}



En esta página, aprenderá a conectar Campaign Classic a **Microsoft Dynamics CRM 365**.

Una posible implementación es mediante **API web** (recomendado). Consulte [la siguiente sección](#microsoft-dynamics-implementation-step) para aprender a configurar la conexión con Microsoft Dynamics.

La sincronización de datos se realiza mediante una actividad de flujo de trabajo dedicada. [Más información](../../platform/using/crm-data-sync.md).

## Pasos de implementación{#microsoft-dynamics-implementation-steps}

Para conectar Microsoft Dynamics 365 y trabajar con Adobe Campaign mediante **API web**, debe aplicar los siguientes pasos:

En Microsoft Dynamics CRM:
1. Obtenga el ID de cliente de Microsoft Dynamics
1. Genere el identificador de clave de certificado de Microsoft Dynamics e ID de clave
1. Configure los permisos
1. Cree un usuario de aplicación
1. Codifique la clave privada

[Obtenga más información en esta sección](#config-crm-microsoft)

En Campaign Classic:
1. Cree una nueva cuenta externa
1. Configure la cuenta externa con la configuración de Microsoft Dynamics
1. Utilice el asistente de configuración para asignar tablas y sincronizar listas desglosadas
1. Cree el flujo de trabajo de sincronización

[Obtenga más información en esta sección](#configure-acc-for-microsoft)


>[!CAUTION]
> Al conectar Adobe Campaign con Microsoft Dynamics, las limitaciones son:
> * La instalación de complementos puede cambiar el comportamiento de CRM, lo que puede dar lugar a problemas de compatibilidad con Adobe Campaign
> * Seleccionar varias enumeraciones

## Configurar Microsoft Dynamics CRM {#config-crm-microsoft}

Para generar el token de acceso y las claves para configurar la cuenta, debe iniciar sesión en [Microsoft Azure Directory](https://portal.azure.com) mediante credenciales de **administrador global**. Luego, siga los pasos descritos a continuación.

### Obtenga el ID de cliente de Microsoft Dynamics {#get-client-id-microsoft}

Para obtener el ID de cliente, debe registrar una aplicación en Azure Active Directory. El ID de cliente es el mismo que el ID de aplicación.

1. Vaya a **Azure Active Directory > Registros de aplicación** y haga clic en **Registro de nueva aplicación**.
1. Asigne un nombre único que pueda ayudar a identificar una instancia, como **adobecampaña`<instance identifier>`**.
1. Elija **Tipo de aplicación** como **aplicación web/API**.
1. Utilice `http://localhost` para **URL de inicio de sesión**.

Una vez guardado, obtendrá un **ID de aplicación** que es el identificador de cliente para Campaign.

Obtenga más información en [esta página](https://docs.microsoft.com/es-es/powerapps/developer/common-data-service/walkthrough-register-app-azure-active-directory).

### Genere el identificador de clave de certificado de Microsoft Dynamics e ID de clave {#config-certificate-key-id}

Para obtener el **Identificador de clave de certificado (customKeyIdentifier)** y el **ID de clave (keyId)**, siga los pasos a continuación:

1. Vaya a **Azure Active Directory > Registros de aplicación** y seleccione la aplicación que se creó anteriormente.
1. Haga clic en **Certificados y secretos**.
1. Haga clic en **Cargar certificado**, y busque y cargue el certificado público generado.
1. Para generar el certificado, puede utilizar openssl.

   Por ejemplo:

   ```
   - openssl req -x509 -sha256 -nodes -days 365 -newkey rsa:2048 -keyout '<'private key name'>' -out '<'public certificate name'>
   ```

   >[!NOTE]
   >
   >Puede cambiar el número de días, aquí `-days 365`, en el ejemplo de código para un periodo de validez de certificado más largo.

1. Luego tendrá que codificarlo en base64. Para ello, puede utilizar la ayuda de un codificador Base64 o utilizar la línea de comandos `base64 -w0 private.key` para Linux.

1. Haga clic en el vínculo **Manifiesto** para obtener el **Identificador de clave de certificado (customKeyIdentifier)** y el **ID de clave (keyId)**.

El **Identificador de clave de certificado (customKeyIdentifier)** y el **ID de clave (keyId)** serán necesarios más adelante para configurar la cuenta externa de Microsoft Dynamics CRM mediante el certificado **[!UICONTROL CRM O-Auth type]**.

### Configure los permisos {#config-permissions-microsoft}

**Paso 1**: Configurar los **Permisos requeridos** para la aplicación que se creó.

1. Vaya a **Azure Active Directory > Registros de aplicación** y seleccione la aplicación que se creó anteriormente.
1. Haga clic en **Configuración** en la parte superior izquierda.
1. En **Permisos requeridos**, haga clic en **Añadir** y, luego, en **Seleccionar una API > Dynamics CRM en línea**.
1. A continuación, haga clic en **Seleccionar**, active la casilla **Acceder a Dynamics 365 como usuarios de la organización** y haga clic en **Seleccionar**.
1. A continuación, desde la aplicación, seleccione el **Manifiesto** en el menú **Administrar**.

1. En el editor **Manifiesto**, establezca la propiedad `allowPublicClient` de `null` en `true` y haga clic en **Guardar**.

**Paso 2**: Conceder consentimiento de administrador

1. Vaya a **Azure Active Directory > Aplicaciones empresariales**.

1. Seleccione la aplicación a la que desea conceder el consentimiento de administrador para todo el inquilino.

1. En el menú del panel izquierdo, seleccione **Permisos** en **Seguridad**.

1. Haga clic en **Conceder consentimiento de administrador**.

Para obtener más información, consulte [Documentación de Azure](https://docs.microsoft.com/es-es/azure/active-directory/manage-apps/grant-admin-consent#grant-admin-consent-from-the-azure-portal).

### Crear un usuario de aplicación {#create-app-user-microsoft}

>[!NOTE]
>
> Este paso es opcional con autenticación **[!UICONTROL Password credentials]**.

El usuario de la aplicación es el usuario que usará la aplicación registrada arriba. Cualquier cambio realizado en Microsoft Dynamics mediante la aplicación registrada anteriormente se realizará mediante este usuario.

**Paso 1**: Crear un usuario no interactivo en el directorio activo de Azure

1. Haga clic en **Azure Active Directory > Usuarios** y, luego, en **Nuevo usuario**.
1. Proporcione el nombre pertinente que desee utilizar; además, el nombre de usuario debe estar en formato de correo electrónico.
1. Elija **Administrador de Dynamics 365** en la **Función de directorio**.

**Paso 2**: Asignar una licencia adecuada al usuario creado

1. En [Microsoft Azure](https://portal.azure.com), haga clic en **Aplicación de administración**.
1. Vaya a **Usuarios > Usuarios activos** y haga clic en el usuario recién creado.
1. Haga clic en **Editar licencias de producto** y seleccione el **Plan de participación del cliente de Dynamics 365**.
1. Haga clic en **Cerrar**.

**Paso 3**: Crear un usuario de aplicación en Dynamics CRM

1. En [Microsoft Azure](https://portal.azure.com), vaya a **Configuración > Seguridad > Usuarios**.
1. Haga clic en el menú desplegable, seleccione **Usuarios de la aplicación** y haga clic en **Nuevo**.
1. Utilice el mismo nombre de usuario que el usuario creado en el directorio principal anterior

   >[!NOTE]
   >
   >El uso del mismo nombre genera un error de clave de duplicado, por lo que hasta que se confirme si este paso es necesario, utilice un nombre de usuario diferente y continúe.
   >

1. Asigne el **ID de aplicación** para [la aplicación que creó anteriormente](#get-client-id-microsoft).
1. Haga clic en **Administrar funciones** y elija la función **Administrador del sistema** para el usuario.

## Configuración de Campaign {#configure-acc-for-microsoft}

>[!NOTE]
>
> Tras la retirada del mercado de [RDS de Microsoft](https://docs.microsoft.com/es-es/previous-versions/dynamicscrm-2016/developers-guide/dn281891%28v=crm.8%29#microsoft-dynamics-crm-2011-endpoint), los tipos de implementaciones de CRM On-Premise y Office 365 ya no son compatibles con Campaign. Adobe Campaign ahora solo admite la implementación de la API web para la versión de CRM **Dynamic CRM 365**. [Más información](../../rn/using/deprecated-features.md#crm-connectors).

Para conectar Microsoft Dynamics 365 y Campaign, debe crear y configurar una cuenta **[!UICONTROL External Account]** dedicada en Campaign.

1. Vaya a **[!UICONTROL Administration > Platform > External accounts]**.

1. Seleccione la cuenta externa **[!UICONTROL Microsoft Dynamics CRM]**. Marque la opción **[!UICONTROL Enabled]**.

1. Rellene la información necesaria para conectar Microsoft Dynamics 365 y Campaign.

   >[!NOTE]
   >
   >La configuración de cuenta externa de Microsoft Dynamics CRM con cada **[!UICONTROL CRM O-Auth type]** se describe [ en esta sección](../../installation/using/external-accounts.md#microsoft-dynamics-crm-external-account).

   ![](assets/crm-ms-dynamics-ext-account.png)

1. Haga clic en el vínculo **[!UICONTROL Microsoft CRM configuration wizard...]**. Adobe Campaign detecta automáticamente las tablas de la plantilla de datos de Microsoft Dynamics.

   ![](assets/crm_connectors_msdynamics_02.png)

1. Seleccionar las tablas que se van a recuperar.

   ![](assets/crm_connectors_msdynamics_03.png)

1. Haga clic en **[!UICONTROL Next]** para comenzar a crear el esquema coincidente.

   ![](assets/crm_connectors_msdynamics_04.png)

   >[!NOTE]
   >
   >Para aprobar la configuración, debe desconectarse y volver a conectarse a la consola de Adobe Campaign.

   Puede comprobar que el esquema de datos coincidente esté disponible en Adobe Campaign.

   ![](assets/crm_connectors_msdynamics_05.png)

1. Haga clic en el vínculo **[!UICONTROL Synchronizing enumerations...]** para comenzar a sincronizar las enumeraciones entre Adobe Campaign y Microsoft Dynamics.

   ![](assets/crm_connectors_msdynamics_06.png)

Campaign y Microsoft Dynamics ahora están conectados. Puede configurar la sincronización de datos entre los dos sistemas. Obtenga más información en la sección [Sincronización de datos](../../platform/using/crm-data-sync.md).

>[!NOTE]
>
> Debe asegurarse de incluir en la lista de permitidos dos direcciones URL: la del servidor y `login.microsoftonline.com` en la configuración del servidor. Para obtener más información sobre cómo configurar los permisos de la URL, consulte esta [página](../../installation/using/url-permissions.md).

## Tipos de datos de campo admitidos {#ms-dyn-supported-types}

Para Microsoft Dynamics 365, los tipos de atributos admitidos o no admitidos se enumeran a continuación:


| Tipo de atributo | Admitido |
| --------------------------------------------------------------------------------- | --------- |
| Tipos básicos: booleano, datetime, decimal, flotante, doble, entero, bigint, cadena | Sí |
| Dinero (como doble) | Sí |
| memo, entityname, primarykey, uniqueidentifier (como cadenas) | Sí |
| Estado, lista de selección (almacenamos los valores posibles en listas desglosadas), estado (cadena) | Sí |
| propietario (como cadena) | Sí |
| Búsqueda (solo búsquedas de referencia de entidad única) | Sí |
| cliente | No |
| Acerca de | No |
| PartyList | No |
| ManagedProperty | No |
| Conjunto de opciones de selección múltiple | No |
