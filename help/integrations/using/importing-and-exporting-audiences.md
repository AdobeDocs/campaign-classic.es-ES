---
title: Importación y exportación de audiencias
seo-title: Importación y exportación de audiencias
description: Importación y exportación de audiencias
seo-description: null
page-status-flag: never-activated
uuid: af03ce68-8a58-4909-83e9-23c385820284
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: integrations
content-type: reference
topic-tags: audience-sharing
discoiquuid: f26cc65a-76be-4b7a-bde3-d0cbe3eedaaf
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 0745b9c9d72538b8573ad18ff4054ecf788905f2

---


# Importación y exportación de audiencias{#importing-and-exporting-audiences}

## Importación de una audiencia {#importing-an-audience}

Se pueden importar audiencias o segmentos a Adobe Campaign desde Audience Manager o el servicio principal Personas mediante las listas de destinatarios.

1. Vaya al nodo **[!UICONTROL Profiles and Targets]** > **[!UICONTROL Lists]** en el explorador de Adobe Campaign.
1. En la barra de acciones, seleccione **[!UICONTROL New]** > **[!UICONTROL Create a shared audience...]**.

   ![](assets/aam_import_audience.png)

1. In the window that opens, click **[!UICONTROL Select a shared audience]** to go to the list of shared audiences/segments available from the other Adobe Experience Cloud solutions.
1. Seleccione una audiencia y confirme. La información de la audiencia se completa automáticamente.

   Please note that to be able to import shared audience, you should be assigned the **[!UICONTROL Audience library]** product in the admin console and be an administrator in Audience Manager. Para obtener más información, consulte [documentación de la consola de administración](https://helpx.adobe.com/enterprise/managing/user-guide.html).

   ![](assets/aam_import_audience_3.png)

1. Select the AMC Data source from the **[!UICONTROL AMC Data source]** field to define the type of data expected.

   ![](assets/aam_import_audience_2.png)

1. Guarde la audiencia.

La audiencia se importa mediante un flujo de trabajo técnico. La lista importada contiene elementos que se pueden conciliar mediante la fuente de datos AMC. Los elementos no reconocidos por Adobe Campaign no se importan.

El proceso de importación tarda en sincronizarse de 24 a 36 horas cuando los segmentos se importan directamente desde el servicio principal Personas o Audience Manager. Después de este periodo, puede encontrar y utilizar la nueva audiencia en Adobe Campaign.

>[!NOTE]
>
>Si se están importando audiencias de Adobe Analytics a Adobe Campaign, dichas audiencias deben compartirse primero en el servicio principal Personas o en Audience Manager. Este proceso tarda de 12 a 24 horas, que se deben añadir a la sincronización de 24 a 36 horas con Campaign.
>
>En ese caso específico, el tiempo que tarda en compartirse la audiencia puede alcanzar las 60 horas. Para obtener más información sobre el uso compartido de las audiencias de Adobe Analytics en el servicio principal Personas y Audience Manager, consulte esta [documentación](https://marketing.adobe.com/resources/help/en_US/mcloud/t_publish_audience_segment.html).

Los datos de audiencias se sustituyen por completo cada vez que se sincronizan. Solo se pueden importar segmentos. No se admiten datos granulares, lo que incluye pares de valor clave, características y reglas.

## Exportación de un público {#exporting-an-audience}

Se puede exportar una audiencia de Adobe Campaign a Audience Manager o al servicio principal Personas mediante un flujo de trabajo. Los procesos para crear y utilizar un flujo de trabajo se describen en [este documento](../../workflow/using/building-a-workflow.md). Las audiencias exportadas se guardan como segmentos en el servicio principal Personas:

1. Cree un nuevo flujo de trabajo de objetivos.
1. Mediante las distintas actividades disponibles, establezca como objetivo un conjunto de destinatarios.
1. After the targeting, drag and drop an **[!UICONTROL Update shared audience]** activity, then open it.

   ![](assets/aam_export_example.png)

1. Define the audience that you want to export via the **[!UICONTROL Select a shared audience]** option. En la ventana que se abre, puede seleccionar una audiencia existente o crear una nueva.

   Si selecciona una audiencia existente, solo se añaden los registros nuevos a la audiencia.

   To export your recipient list in a new audience, complete the **[!UICONTROL Segment name]** field then click **[!UICONTROL Create]** before selecting the newly created audience.

   Finish the operation by clicking the check symbol at the top right of the window, then the **[!UICONTROL OK]** button.

1. Select the **[!UICONTROL AMC Data source]** to specify the expected data type. El esquema se determina automáticamente.

   ![](assets/aam_export_audience_activity.png)

1. Guarde la audiencia.

A continuación, se exporta la audiencia. La actividad de guardar la audiencia tiene dos transiciones salientes. La transición principal contiene los destinatarios exportados correctamente. La transición adicional contiene los destinatarios que no pueden asignarse a una ID de visitante o a una ID declarada.

La sincronización entre Adobe Campaign y el servicio principal Personas tarda de 24 a 36 horas. Después de este periodo, puede encontrar la nueva audiencia en el servicio principal Personas y reutilizarla en otras soluciones de Adobe Experience Cloud. Para obtener más información sobre el uso de una audiencia compartida de Adobe Campaign en el servicio principal Personas de Adobe, consulte la siguiente [documentación](https://marketing.adobe.com/resources/help/en_US/mcloud/t_audience_create.html).

>[!NOTE]
>
>Para poder conciliarlos, los registros deben tener una Adobe Experience Cloud ID (“ID de visitante” o “ID declarada”). Los registros sin Adobe Experience Cloud ID se omiten al exportar e importar audiencias.

