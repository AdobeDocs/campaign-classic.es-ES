---
product: campaign
title: Campaign - Conector de Salesforce CRM
description: Obtenga información sobre cómo conectar Campaign y Salesforce
feature: Salesforce Integration
exl-id: 94a1f00d-e952-4edd-9012-f71c87b897ca
hide: true
TQID: https://experienceleague.adobe.com/LeUJ-F5dAECUrtkbvgwL0BN88Alofnh2rBWe7hIVGgI
product_v2: id: dfc56824-e8b9-499e-85d4-21aedb507314
feature_v2: id: c5474392-5419-4296-9e41-f6f4ce4f6e9bid: afa4204e-6d08-4e29-bc35-26aafb656d48
topic_v2: id: d095671a-1355-40aa-8b5f-06c33c68080bid: eddd9b14-83bd-4ff4-9072-54a4a484abb7
subfeature_v2: id: f529d0bd-1401-4c88-9833-43228cc1d40fid: d6330382-c886-4f7a-a4f7-74e3f36c0d9cid: f5293531-9312-4099-bfa3-9e67df6a8750id: efa38731-2723-4334-8d8b-a778af834835
source-git-commit: 38eab6b8da73163e4476e91c0ef73f25c3f57546
workflow-type: ht
source-wordcount: 323
ht-degree: 100%

---

# Conectar Campaign y Salesforce.com{#connect-to-sfdc}



En esta página, aprenderá a conectar Campaign Classic a **Salesforce**.

La sincronización de datos se realiza mediante una actividad de flujo de trabajo dedicada. [Más información](../../platform/using/crm-data-sync.md).


La cuenta externa le permite importar y exportar datos de Salesforce a Adobe Campaign. Para configurar el conector de CRM para Salesforce, siga estos pasos:

1. Cree una nueva cuenta externa a través del nodo **[!UICONTROL Administration > Platform > External accounts]** del árbol de Adobe Campaign.
1. Seleccione **[!UICONTROL Salesforce.com]**.
1. Introduzca la configuración para habilitar la conexión.

   ![](assets/ext_account_17.png)

   Para configurar la cuenta externa de Salesforce CRM para que funcione con Adobe Campaign, proporcione los siguientes detalles:

   * **[!UICONTROL Account]**
Cuenta utilizada para iniciar sesión en Salesforce CRM.

   * **[!UICONTROL Password]**
Contraseña utilizada para iniciar sesión en Salesforce CRM.

   * **[!UICONTROL Client identifier]**
Para saber dónde encontrar el identificador de cliente, consulte esta [página](https://help.salesforce.com/articleView?id=000205876&type=1).

   * **[!UICONTROL Security token]**
Para saber dónde encontrar el token de seguridad, consulte esta [página](https://help.salesforce.com/articleView?id=000205876&type=1).

   * **[!UICONTROL API version]**
Seleccione la versión de la API.
1. Ejecute el asistente de configuración para generar la tabla CRM disponible: el asistente de configuración permite recopilar tablas y crear el esquema correspondiente.

   ![](assets/crm_connectors_sfdc_launch.png)

   >[!NOTE]
   >
   >Para aprobar la configuración, debe cerrar la sesión y volver a iniciarla en la consola de Adobe Campaign.

1. Compruebe el esquema generado en Adobe Campaign en el nodo **[!UICONTROL Administration > Configuration > Data schemas]**.

   Ejemplo de esquema de **Salesforce**:

   ![](assets/crm_connectors_sfdc_table.png)

1. Una vez creado el esquema, puede sincronizar las enumeraciones automáticamente con Adobe Campaign a través de Salesforce.

   Para ello, haga clic en el enlace **[!UICONTROL Synchronizing enumerations...]** y seleccione la enumeración de Adobe Campaign que coincida con la de Salesforce.



   ![](assets/crm_connectors_sfdc_enum.png)

   >[!NOTE]
   >
   >Puede reemplazar todos los valores de una enumeración de Adobe Campaign con los del CRM: para hacerlo, seleccione **[!UICONTROL Yes]** en la columna **[!UICONTROL Replace]**.


   Haga clic en **[!UICONTROL Next]** y a continuación **[!UICONTROL Start]** para iniciar la importación de la lista.

1. Compruebe los valores importados en el menú **[!UICONTROL Administration > Platform > Enumerations]**.

   ![](assets/crm_connectors_sfdc_exe.png)

   >[!NOTE]
   >
   > No se admiten enumeraciones de varias selecciones.

Campaign y Salesforce.com ya están conectados. Puede configurar la sincronización de datos entre los dos sistemas.

Para sincronizar datos entre los datos de Adobe Campaign y el sistema CRM, debe crear un flujo de trabajo y utilizar la actividad **[!UICONTROL CRM connector]**.

![](assets/crm_connectors_sfdc_wf.png)

Obtenga más información acerca de la sincronización de datos [en esta página](../../platform/using/crm-data-sync.md).
