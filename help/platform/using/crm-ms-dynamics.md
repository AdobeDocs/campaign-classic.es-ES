---
solution: Campaign Classic
product: campaign
title: Campaign - Conector de Microsoft Dynamics CRM
description: Conectar Campaign y Microsoft Dynamics
audience: platform
content-type: reference
topic-tags: connectors
exl-id: 26737940-b3ce-425c-9604-f4cefd19afaa
translation-type: tm+mt
source-git-commit: 37802e52f1d1d38d9c3d59c439f23114a594bfef
workflow-type: tm+mt
source-wordcount: '947'
ht-degree: 99%

---

# Conectar Campaign y Microsoft Dynamics 365{#connect-to-msdyn}

En esta página, aprenderá a conectar Campaign Classic a **Microsoft Dynamics CRM 365**.

Las implementaciones posibles son:

* mediante **API web** (recomendado). Consulte [la siguiente sección](#microsoft-dynamics-implementation-step) para aprender a configurar la conexión con Microsoft Dynamics.
* con **Office 365**. Consulte [este vídeo](#microsoft-dynamics-office-365) para conocer los pasos clave para configurar esta integración.
* para una implementación **On-premise**, aplique los pasos clave de Office 365.

La sincronización de datos se realiza mediante una actividad de flujo de trabajo dedicada. [Más información](../../platform/using/crm-data-sync.md).

## Pasos de implementación{#microsoft-dynamics-implementation-steps}

Para conectar Microsoft Dynamics 365 y trabajar con Adobe Campaign mediante **API web**, debe aplicar los siguientes pasos:

En Microsoft Dynamics CRM:
1. Obtenga el ID de cliente de Microsoft Dynamics
1. Genere el secreto de cliente de Microsoft Dynamics
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

>



## Configurar Microsoft Dynamics CRM {#config-crm-microsoft}

Para generar el token de acceso y las claves para configurar la cuenta, debe iniciar sesión en [Microsoft Azure Directory](https://portal.azure.com) mediante credenciales de **administrador global**. Luego, siga los pasos descritos a continuación.

### Obtener el ID de cliente de Microsoft Dynamics {#get-client-id-microsoft}

Para obtener el ID de cliente, debe registrar una aplicación en Azure Active Directory. El ID de cliente es el mismo que el ID de aplicación.

1. Vaya a **Azure Active Directory > Registros de aplicación** y haga clic en **Registro de nueva aplicación**.
1. Asigne un nombre único que pueda ayudar a identificar una instancia, como **adobecampaña`<instance identifier>`**.
1. Elija **Tipo de aplicación** como **aplicación web/API**.
1. Utilice `http://localhost` para **URL de inicio de sesión**.

Una vez guardado, obtendrá un **ID de aplicación** que es el identificador de cliente para Campaign.

Obtenga más información en [esta página](https://docs.microsoft.com/en-us/powerapps/developer/common-data-service/walkthrough-register-app-azure-active-directory).

### Generar secreto de cliente de Microsoft Dynamics {#config-client-secret-microsoft}

El secreto de cliente es la clave exclusiva del ID de cliente. Para obtener el identificador de clave de certificado, siga los pasos a continuación:

1. Vaya a **Azure Active Directory > Registros de aplicación** y seleccione la aplicación que se creó anteriormente.
1. Haga clic en **Certificados y secretos**.
1. Haga clic en **Cargar certificado**, y busque y cargue el certificado público generado.
1. Para generar el certificado, puede utilizar openssl.

   Por ejemplo:

   ```
   - openssl req -x509 -sha256 -nodes -days 365 -newkey rsa:2048 -keyout '<'private key name'>' -out '<'public certificate name'>
   ```

1. Haga clic en el vínculo **manifest** para obtener el **identificador de clave de certificado** y el **identificador de clave**.

### Configurar permisos {#config-permissions-microsoft}

Debe configurar los **permisos requeridos** para la aplicación que se creó.

1. Vaya a **Azure Active Directory > Registros de aplicación** y seleccione la aplicación que se creó anteriormente.
1. Haga clic en **Configuración** en la parte superior izquierda.
1. En **Permisos requeridos**, haga clic en **Añadir** y, luego, en **Seleccionar una API > Dynamics CRM en línea**.
1. A continuación, haga clic en **Seleccionar**, active la casilla **Acceder a Dynamics 365 como usuarios de la organización** y haga clic en **Seleccionar**.

### Crear un usuario de aplicación {#create-app-user-microsoft}

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

1. Asigne el **ID de aplicación** para [la aplicación que creó anteriormente](#get-client-id-microsoft).
1. Haga clic en **Administrar funciones** y elija la función **Administrador del sistema** para el usuario.

## Configurar Campaign {#configure-acc-for-microsoft}

Para conectar Microsoft Dynamics 365 y Campaign, debe crear y configurar una cuenta externa dedicada en Campaign.

1. Vaya a **[!UICONTROL Administration > Platform > External accounts]**.

1. Cree una nueva cuenta externa, seleccione el tipo **[!UICONTROL Microsoft Dynamics CRM]** y la opción **[!UICONTROL Enable]**.

1. Seleccione el tipo de implementación **[!UICONTROL Web API]**:

   Adobe Campaign Classic es compatible con la interfaz de Dynamics 365 REST con el protocolo de oAuth authentication con **[!UICONTROL Certificate]** o **[!UICONTROL Password Credentials]**.

   Use la configuración [definida previamente](#get-client-id-microsoft) en Azure Directory para configurar la cuenta externa.

   ![](assets/crm-ms-dynamics-ext-account.png)

   >[!NOTE]
   >
   >La configuración de cuenta externa de Microsoft Dynamics CRM se detalla [en esta sección](../../installation/using/external-accounts.md#microsoft-dynamics-crm-external-account).

1. Haga clic en el vínculo **[!UICONTROL Microsoft CRM configuration wizard...]**: Adobe Campaign detecta automáticamente las tablas de la plantilla de datos de Microsoft Dynamics.

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

## Configurar la integración de Microsoft Dynamics CRM Office 365{#microsoft-dynamics-office-365}

Vea este vídeo para aprender a integrar Dynamics 365 con Adobe Campaign Classic en el contexto de una implementación de Office 365.

>[!VIDEO](https://video.tv.adobe.com/v/23837?quality=12)


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
