---
product: campaign
title: Aprovisionamiento del conector de Adobe Analytics
description: Más información acerca del aprovisionamiento del conector de Adobe Analytics
badge-v7-prem: label="On-premise/híbrido solo" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=es" tooltip="Se aplica solo a implementaciones On-premise e híbridas v7"
feature: Analytics Integration
role: User, Admin
level: Beginner
exl-id: 24e002aa-4e86-406b-92c7-74f242ee4b86
TQID: https://experienceleague.adobe.com/d7BixCjNjofJbMlbLbTFVN9BiPArA4uCms0QdV5uW-0
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
feature_v2:
  - id: d5ef99fa-df0c-4153-bf94-105ad0724167
subfeature_v2:
  - id: c3bf7e1e-1db5-4c72-9293-e2f0b1ab73d0
  - id: cbcf4d90-26be-46e2-b16a-aebc529dc41e
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
level_v2:
  - id: e8ccd51f-da0d-4e3b-939b-e30d5ebb1ea5
topic_v2:
  - id: b5ce8718-c3af-4fdb-a1a9-fca32f83a87c
source-git-commit: 4c295c0dabae8aba298390a3da2422a3fa1219f9
workflow-type: tm+mt
source-wordcount: 702
ht-degree: 81%

---

# Aprovisionamiento del Conector de Adobe Analytics {#adobe-analytics-connector-provisioning}

>[!CAUTION]
>
> Estos pasos solo deben realizarlos las implementaciones híbridas y locales.
>
>Para implementaciones de Managed Services alojadas y de Campaign, póngase en contacto con el equipo del [servicio de atención al cliente de Adobe](https://helpx.adobe.com/es/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html).

La integración entre Adobe Campaign Classic y la autenticación de Adobe Analytics es compatible con el servicio Identity Management de Adobe (IMS):

* Si administra una cuenta externa migrada, debe implementar Adobe IMS y conectarse a Adobe Campaign a través de un Adobe ID.

  El usuario que haya iniciado sesión mediante el IMS de Adobe ID debe ser el propietario de la cuenta del **Conector de datos** en Adobe Analytics y debe tener un conjunto de permisos para el **Perfil del producto** mencionado [a continuación](#analytics-product-profile).

El problema era que el propietario del Conector de datos era un usuario diferente al usuario que había iniciado sesión en Campaign y que estaba probando la integración con Analytics.

* Si va a implementar un conector nuevo, la implementación de Adobe IMS es opcional. Sin un usuario de Adobe ID, Adobe Campaign utilizará un usuario técnico para sincronizar con Adobe Analytics.

Para que esta integración funcione, debe crear un perfil de producto de Adobe Analytics que se utilice exclusivamente para el conector de Analytics. A continuación, deberá crear un proyecto de Developer console.

>[!AVAILABILITY]
>
> La credencial de cuenta de servicio (JWT) está en desuso en Adobe. Las integraciones de Campaign con soluciones y aplicaciones de Adobe ahora deben depender de la credencial de servidor a servidor OAuth. </br>
>
> * Si ha implementado integraciones de entrada con Campaign, debe migrar su Cuenta técnica como se detalla en [esta documentación](https://developer.adobe.com/developer-console/docs/guides/authentication/ServerToServerAuthentication/migration/#_blank). Las [credenciales de la cuenta de servicio (JWT)](oauth-technical-account.md) existentes seguirán funcionando hasta el martes, 30 de junio de 2025.</br>
>
> * Si ha implementado integraciones salientes, como la de Campaign-Analytics o la de Experience Cloud Déclencheur, seguirán funcionando hasta el 30 de junio de 2025. Sin embargo, antes de esa fecha, debe actualizar el entorno de Campaign a la versión 7.4.1 y migrar la cuenta técnica a OAuth.

## Creación de un perfil de producto de Adobe Analytics {#analytics-product-profile}

El perfil de producto determina el nivel de acceso que un usuario tiene a sus distintos componentes de Analytics.

Si ya tiene un perfil de producto de Analytics, debe crear otro que utilice exclusivamente para el conector de Analytics. Esto garantizará que el perfil de producto esté configurado con los permisos correctos para esta integración.

Para obtener más información acerca de los perfiles de producto, consulte la [documentación de Admin Console](https://helpx.adobe.com/mt/enterprise/admin-guide.html).

1. En [Admin Console](https://adminconsole.adobe.com/), seleccione su **[!UICONTROL Product]** de Adobe Analytics.

   ![](assets/do-not-localize/triggers_1.png)

1. Haga clic **[!UICONTROL New Profile]**.

   ![](assets/do-not-localize/triggers_2.png)

1. Añada un **[!UICONTROL Product profile name]**, sugerimos usar la siguiente sintaxis: `reserved_campaign_classic_<Company Name>`. A continuación, haga clic en **[!UICONTROL Next]**.

   Este **[!UICONTROL Product profile]** debe usarse exclusivamente en el Conector de Analytics para evitar errores de configuración.

1. Abra el **[!UICONTROL Product profile]** recién creado y seleccione la pestaña **[!UICONTROL Permissions]**.

   ![](assets/do-not-localize/triggers_3.png)

1. Configure las diferentes capacidades haciendo clic en **[!UICONTROL Edit]** y seleccione los permisos que desea asignar a su **[!UICONTROL Product profile]** haciendo clic en el icono de signo más (+).

   Para obtener más información sobre cómo administrar permisos, consulte la [Documentación de Admin Console](https://helpx.adobe.com/mt/enterprise/using/manage-permissions-and-roles.html).

1. Para la capacidad **[!UICONTROL Report Suites]**, añada el **[!UICONTROL Report Suites]** que debe utilizar más adelante.

   Si no tiene ningún grupo de informes, puede crearlo siguiendo [estos pasos](../../integrations/using/gs-aa.md).

   ![](assets/do-not-localize/triggers_4.png)

1. Para la capacidad **[!UICONTROL Metrics]**, añada el **[!UICONTROL Metrics]** que tendrá que configurar más adelante.

   Si es necesario, puede activar la opción Inclusión automática, que añadirá todos los elementos de permisos a la lista incluida y automáticamente agregará nuevos elementos de permisos.

   ![](assets/do-not-localize/triggers_13.png)

1. Para la capacidad **[!UICONTROL Dimensions]**, añada el **[!UICONTROL Dimensions]** necesario para la configuración futura.

   Asegúrese de que las Dimensiones seleccionadas coinciden con las que se van a configurar en la cuenta externa y se alinean con el número de eVars correspondiente de Adobe Analytics.

1. Para la capacidad **[!UICONTROL Report Suite Tools]**, agregue los siguientes permisos:

   * **[!UICONTROL Report suite Mgmt]**
   * **[!UICONTROL Conversion variables]**
   * **[!UICONTROL Success events]**
   * **[!UICONTROL Custom data Warehouse report]**
   * **[!UICONTROL Data sources manager]**
   * **[!UICONTROL Classifications]**

1. Para la capacidad **[!UICONTROL Analytics Tools]**, agregue los siguientes permisos:

   * **[!UICONTROL Code Manager - Web services]**
   * **[!UICONTROL Logs - Web services]**
   * **[!UICONTROL Web services]**
   * **[!UICONTROL Web service access]**
   * **[!UICONTROL Calculated metric creation]**
   * **[!UICONTROL Segment creation]**

El perfil de producto ya está configurado. A continuación, debe crear el proyecto de OAuth.

## Creación de un proyecto de OAuth {#create-adobe-io}

Para proseguir con la configuración del conector de Adobe Analytics, acceda a Adobe Developer Console y cree su proyecto de servidor a servidor OAuth.

Consulte [esta página](oauth-technical-account.md#oauth-service) para ver la documentación detallada.

## Configuración y uso {#adobe-analytics-connector-usage}

Aprenda a trabajar con Adobe Campaign y Adobe Analytics en [Documentación de Adobe Campaign v8](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/connect/ac-aa){target="_blank"}.