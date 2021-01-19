---
solution: Campaign Classic
product: campaign
title: Conector de Microsoft Dynamics CRM
description: Campaña de Connect y Microsoft Dynamics
audience: platform
content-type: reference
topic-tags: connectors
translation-type: tm+mt
source-git-commit: 7478ae37aee5e8b0d9c904f5b9d810375d9d6481
workflow-type: tm+mt
source-wordcount: '888'
ht-degree: 4%

---


# Campaña de Connect y Microsoft Dynamics 365{#connect-to-msdyn}

En esta página, aprenderá a conectar Campaign Classic a **Microsoft Dynamics CRM 365**.

Las implementaciones posibles son:

* mediante **API web** (recomendado). Consulte [la sección siguiente](#microsoft-dynamics-implementation-step) para conocer los pasos para configurar la conexión con Microsoft Dynamics.
* con **Office 365**. Consulte [este vídeo](#microsoft-dynamics-office-365) para conocer los pasos clave para configurar esta integración.
* para una implementación **in situ**, aplique los pasos clave de Office 365.

La sincronización de datos se realiza mediante una actividad de flujo de trabajo dedicada. [Más información](../../platform/using/crm-data-sync.md).


>[!NOTE]
>
> La versión de sistemas CRM compatible con la Campaña se enumera en la [matriz de compatibilidad](../../rn/using/compatibility-matrix.md#CRMconnectors).


## Pasos de implementación{#microsoft-dynamics-implementation-steps}

Para conectar Microsoft Dynamics 365 y trabajar con Adobe Campaign mediante **API web**, debe aplicar los siguientes pasos:

En Microsoft Dynamics CRM:
1. Obtener ID de cliente de Microsoft Dynamics
1. Generar secreto de cliente de Microsoft Dynamics
1. Configurar permisos
1. Crear un usuario de aplicación
1. Codificar la clave privada

[Obtenga más información en esta sección](#config-crm-microsoft)

En Campaign Classic:
1. Crear una nueva cuenta externa
1. Configurar la cuenta externa con la configuración de Microsoft Dynamics
1. Utilice el asistente de configuración para asignar tablas y sincronizar listas desglosadas
1. Cree el flujo de trabajo de sincronización

[Obtenga más información en esta sección](#configure-acc-for-microsoft)


>[!CAUTION]
> Al conectar Adobe Campaign con Microsoft Dynamics, no puede:
> * Instale complementos que puedan cambiar el comportamiento de CRM y provocar problemas de compatibilidad con Adobe Campaign
> * Seleccionar varias listas desglosadas

>



## Configurar Microsoft Dynamics CRM {#config-crm-microsoft}

Para generar el token de acceso y las claves para configurar la cuenta, debe iniciar sesión en [Microsoft Azure Directory](https://portal.azure.com) con **credenciales de administrador global**. Luego siga los pasos descritos a continuación.

### Obtener el ID de cliente de Microsoft Dynamics {#get-client-id-microsoft}

Para obtener el ID de cliente, debe registrar una aplicación en Azure Active Directory. El ID de cliente es el mismo que el ID de aplicación.

1. Vaya a **Azure Active Directory > Registros de aplicación** y haga clic en **Registro de nueva aplicación**.
1. Asigne un nombre único que pueda ayudar a identificar una instancia, como **adobecampaña`<instance identifier>`**.
1. Elija **Tipo de aplicación** como **aplicación web / API**.
1. Utilice `http://localhost` para **URL de inicio de sesión**.

Una vez guardado, obtendrá un **ID de aplicación** que es el identificador de cliente para la Campaña.

Obtenga más información en [esta página](https://docs.microsoft.com/en-us/powerapps/developer/common-data-service/walkthrough-register-app-azure-active-directory).

### Generar secreto de cliente de Microsoft Dynamics {#config-client-secret-microsoft}

El secreto de cliente es la clave exclusiva del ID de cliente. Para obtener el identificador de clave de certificado, siga los pasos a continuación:

1. Vaya a **Azure Active Directory > Registros de aplicación** y seleccione la aplicación que se creó anteriormente.
1. Haga clic en **Certificados y secretos**.
1. Haga clic en **Cargar certificado** y luego busque y cargue el certificado público generado.
1. Para generar el certificado puede utilizar openssl.

   Por ejemplo:

   ```
   - openssl req -x509 -sha256 -nodes -days 365 -newkey rsa:2048 -keyout '<'private key name'>' -out '<'public certificate name'>
   ```

1. Haga clic en el vínculo **manifest** para obtener el **identificador de clave de certificado** y el **identificador de clave**.

### Configurar permisos {#config-permissions-microsoft}

Debe configurar los **permisos requeridos** para la aplicación que se creó.

1. Vaya a **Azure Active Directory > Registros de aplicación** y seleccione la aplicación que se creó anteriormente.
1. Haga clic en **Configuración** en la parte superior izquierda.
1. En **Permisos requeridos**, haga clic en **Añadir** y **Seleccionar una API > Dynamics CRM Online**.
1. A continuación, haga clic en **Seleccionar**, active la casilla **Acceder a Dynamics 365 como usuarios de la organización** y haga clic en **Seleccionar**.

### Crear un usuario de aplicación {#create-app-user-microsoft}

El usuario de la aplicación es el usuario que usará la aplicación registrada arriba. Cualquier cambio realizado en Microsoft Dynamics mediante la aplicación registrada anteriormente se realizará mediante este usuario.

**Paso 1**: Crear un usuario no interactivo en el directorio activo de Azure

1. Haga clic en **Azure Active Directory > Usuarios** y haga clic en **Nuevo usuario**.
1. Proporcione un nombre adecuado que desee utilizar y el nombre de usuario debe ser un formato del correo electrónico.
1. Elija **Administrador de Dynamics 365** en la **Función de directorio**.

**Paso 2**: Asignar una licencia adecuada al usuario creado

1. En [Microsoft Azure](https://portal.azure.com), haga clic en **Aplicación de administración**.
1. Vaya a **Usuarios > Usuarios activos** y haga clic en el usuario recién creado.
1. Haga clic en **Editar licencias de producto** y seleccione el **Plan de compromiso del cliente de Dynamics 365**.
1. Haga clic en **Cerrar**.

**Paso 3**: Creación de un usuario de aplicación en Dynamics CRM

1. En [Microsoft Azure](https://portal.azure.com), vaya a **Configuración > Seguridad > Usuarios**.
1. Haga clic en el menú desplegable, seleccione **Usuarios de la aplicación** y haga clic en **Nuevo**.
1. Utilice el mismo nombre de usuario que el usuario creado en el directorio activo anterior

   >[!NOTE]
   >
   >El uso del mismo nombre genera un error de clave de duplicado, por lo que hasta que se confirme si este paso es necesario, utilice un nombre de usuario diferente y continúe.

1. Asigne el **ID de aplicación** para [la aplicación que creó anteriormente](#get-client-id-microsoft).
1. Haga clic en **Administrar funciones** y elija la función **Administrador del sistema** para el usuario.

## Configurar Campaña {#configure-acc-for-microsoft}

Para conectar Microsoft Dynamics 365 y Campaña, debe crear y configurar una Cuenta externa dedicada en Campaña.

1. Vaya a **[!UICONTROL Administration > Platform > External accounts]**.

1. Cree una nueva cuenta externa, seleccione el tipo **[!UICONTROL Microsoft Dynamics CRM]** y la opción **[!UICONTROL Enable]**.

1. Seleccione el tipo de implementación **[!UICONTROL Web API]**:

   Adobe Campaign Classic admite la interfaz de Dynamics 365 REST con el protocolo OAuth para la autenticación con un **[!UICONTROL Certificate]** o **[!UICONTROL Password Credentials]**.

   Use la configuración [definida previamente](#get-client-id-microsoft) en Azure Directory para configurar la cuenta externa.

   ![](assets/crm-ms-dynamics-ext-account.png)

   >[!NOTE]
   >
   >La configuración de Cuenta externa de Microsoft Dynamics CRM se detalla [en esta sección](../../installation/using/external-accounts.md#microsoft-dynamics-crm-external-account).

1. Haga clic en el vínculo **[!UICONTROL Microsoft CRM configuration wizard...]**: Adobe Campaign detecta automáticamente las tablas de la plantilla de datos de Microsoft Dynamics.

   ![](assets/crm_connectors_msdynamics_02.png)

1. Seleccionar las tablas que se van a recuperar.

   ![](assets/crm_connectors_msdynamics_03.png)

1. Haga clic en **[!UICONTROL Next]** para crear el esquema correspondiente en inicio.

   ![](assets/crm_connectors_msdynamics_04.png)

   >[!NOTE]
   >
   >Para aprobar la configuración, debe desconectarse y volver a conectarse a la consola de Adobe Campaign.

   Puede comprobar que el esquema de datos coincidente esté disponible en Adobe Campaign.

   ![](assets/crm_connectors_msdynamics_05.png)

1. Haga clic en el vínculo **[!UICONTROL Synchronizing enumerations...]** para sincronizar listas desglosadas de inicio entre Adobe Campaign y Microsoft Dynamics.

   ![](assets/crm_connectors_msdynamics_06.png)

Campaña y Microsoft Dynamics ahora están conectados. Puede configurar la sincronización de datos entre los dos sistemas. Obtenga más información en la sección [Sincronización de datos](../../platform/using/crm-data-sync.md).

## Configurar la integración de Microsoft Dynamics CRM Office 365{#microsoft-dynamics-office-365}

Vea este vídeo para aprender a integrar Dynamics 365 con Adobe Campaign Classic en el contexto de una implementación de Office 365.

>[!VIDEO](https://video.tv.adobe.com/v/23837?quality=12)
