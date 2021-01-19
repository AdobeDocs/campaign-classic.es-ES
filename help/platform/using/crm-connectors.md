---
solution: Campaign Classic
product: campaign
title: Conectores CRM
description: Introducción a Conectores CRM en Campaña
audience: platform
content-type: reference
topic-tags: connectors
translation-type: tm+mt
source-git-commit: 2838ced5f5d562914c0791e6a0b8f02dd61006b4
workflow-type: tm+mt
source-wordcount: '356'
ht-degree: 62%

---


# Conectores CRM{#crm-connectors}

## Introducción a los conectores CRM {#about-crm-connectors}

Adobe Campaign ofrece varios conectores CRM para vincular la plataforma de Adobe Campaign a los sistemas de terceros. Estos conectores de CRM le permiten sincronizar contactos, cuentas, compras, etc., para facilitar la integración de la aplicación con diversas aplicaciones de terceros y de negocios.

Estos conectores permiten una integración de datos rápida y sencilla: Adobe Campaign proporciona un asistente dedicado para recopilar y seleccionar de las tablas disponibles en CRM. De este modo, se garantiza la sincronización bidireccional para garantizar que los datos estén actualizados en todo momento a lo largo de los sistemas.

>[!NOTE]
>
>Esta función está disponible en Adobe Campaign a través del paquete de **conectores de CRM** dedicados.


### Sistemas compatibles {#compatible-crm-systems-and-limitations}

Las versiones y CRM admitidas se detallan en la Campaña [Tabla de compatibilidad](../../rn/using/compatibility-matrix.md).

>[!NOTE]
>
>Los conectores de CRM solo funcionan con una URL segura (https).

### Pasos de implementación {#crm-implementation-steps}

Aprenda el procedimiento paso a paso para conectar Campaña y Microsoft Dynamics [en esta sección](../../platform/using/crm-ms-dynamics.md)

En general, para utilizar los conectores CRM en Adobe Campaign, siga estos pasos:

1. Cree una nueva cuenta externa a través del nodo **[!UICONTROL Administration > Platform > External accounts]** en el árbol de Adobe Campaign.
1. Seleccione el sistema CRM al que debe conectar la Campaña.
1. Introduzca la configuración para activar la conexión.
1. Ejecute el asistente de configuración para generar la tabla CRM disponible: el asistente de configuración permite recopilar tablas y crear el esquema correspondiente.

   Ejemplo del asistente de configuración **Salesforce**:

   ![](assets/crm_connectors_sfdc_launch.png)

   >[!NOTE]
   >
   >Para aprobar la configuración, debe cerrar la sesión y volver a iniciarla en la consola de Adobe Campaign.

1. Compruebe el esquema generado en Adobe Campaign en el nodo **[!UICONTROL Administration > Configuration > Data schemas]**.

   Ejemplo de esquema **Salesforce**:

   ![](assets/crm_connectors_sfdc_table.png)

1. Una vez creado el esquema, puede sincronizar las enumeraciones automáticamente con Adobe Campaign a través de CRM.

   Para ello, haga clic en el enlace  **[!UICONTROL Synchronizing enumerations...]** y seleccione la lista desglosada de Adobe Campaign que coincida con la de CRM.

   >[!NOTE]
   >
   >Puede reemplazar todos los valores de una enumeración de Adobe Campaign con los del CRM: para hacerlo, seleccione **[!UICONTROL Yes]** en la columna **[!UICONTROL Replace]**.

   Ejemplo de listas desglosadas **Salesforce**:

   ![](assets/crm_connectors_sfdc_enum.png)

   Haga clic en **[!UICONTROL Next]** y a continuación **[!UICONTROL Start]** para iniciar la importación de la lista.

1. Compruebe los valores importados en el menú **[!UICONTROL Administration > Platform > Enumerations]**.

   ![](assets/crm_connectors_sfdc_exe.png)

   >[!NOTE]
   >
   > No se admiten varias listas desglosadas de selección en Salesforce.

1. Para sincronizar datos entre los datos de Adobe Campaign y el sistema CRM, debe crear un flujo de trabajo y utilizar la actividad **[!UICONTROL CRM connector]**.

   ![](assets/crm_connectors_sfdc_wf.png)

   Obtenga más información sobre la sincronización de datos [en esta página](../../platform/using/crm-data-sync.md).
