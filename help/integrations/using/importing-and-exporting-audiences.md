---
product: campaign
title: Importación y exportación de audiencias
description: Importación y exportación de audiencias
feature: Audiences
badge-v8: label="También se aplica a v8" type="Positive" tooltip="También se aplica a Campaign v8"
audience: integrations
content-type: reference
topic-tags: audience-sharing
exl-id: c2293fc5-c9ba-4a73-8f39-fa7cdd06e8dd
source-git-commit: b11185da8236d6100d98eabcc9dc1cf2cffa70af
workflow-type: tm+mt
source-wordcount: '589'
ht-degree: 77%

---


# Importación y exportación de audiencias{#importing-and-exporting-audiences}



## Importación de una audiencia {#importing-an-audience}

Se pueden importar audiencias o segmentos a Adobe Campaign desde Audience Manager a través de las listas de destinatarios.

1. Vaya al nodo **[!UICONTROL Profiles and Targets]** > **[!UICONTROL Lists]** en Adobe Campaign Explorer.
1. En la barra de acciones, seleccione **[!UICONTROL New]** > **[!UICONTROL Create a shared audience...]**.

   ![](assets/aam_import_audience.png)

1. En la ventana que se abre, haga clic en **[!UICONTROL Select a shared audience]** para ir a la lista de audiencias y segmentos compartidos disponibles en las otras soluciones de Adobe Experience Cloud.
1. Seleccione una audiencia y confirme. La información de la audiencia se completa automáticamente.

   Tenga en cuenta que para poder importar la audiencia compartida, debe asignarse a usted el producto **[!UICONTROL Audience library]** en la consola de administración y ser administrador en Audience Manager. Para obtener más información, consulte [documentación de la consola de administración](https://helpx.adobe.com/es/enterprise/admin-guide.html).

   ![](assets/aam_import_audience_3.png)

1. Seleccione la fuente de datos AMC del campo **[!UICONTROL AMC Data source]** para definir el tipo de datos deseados.

   ![](assets/aam_import_audience_2.png)

1. Guarde la audiencia.

La audiencia se importa mediante un flujo de trabajo técnico. La lista importada contiene elementos que se pueden reconciliar mediante la fuente de datos AMC. Los elementos no reconocidos por Adobe Campaign no se importan.

El proceso de importación tarda en sincronizarse de 24 a 36 horas cuando los segmentos se importan directamente desde Audience Manager. Después de este periodo, puede encontrar y utilizar la nueva audiencia en Adobe Campaign.

>[!NOTE]
>
>Si se están importando audiencias de Adobe Analytics a Adobe Campaign, dichas audiencias deben compartirse primero en Audience Manager. Este proceso tarda de 12 a 24 horas, que se deben añadir a la sincronización de 24 a 36 horas con Campaign.
>
>En ese caso específico, el tiempo que tarda en compartirse la audiencia puede alcanzar las 60 horas. Para obtener más información sobre el uso compartido de audiencias de Adobe Analytics en Audience Manager, consulte [Documentación de Adobe Analytics](https://experienceleague.adobe.com/docs/analytics/components/segmentation/segmentation-workflow/seg-publish.html?lang=es){target="_blank"}.

Los datos de audiencias se sustituyen por completo cada vez que se sincronizan. Solo se pueden importar segmentos. No se admiten datos granulares, lo que incluye pares de valor clave, características y reglas.

## Exportación de un público {#exporting-an-audience}

Puede exportar una audiencia de Adobe Campaign a Audience Manager mediante un flujo de trabajo. Los procesos para crear y utilizar un flujo de trabajo se describen en [este documento](../../workflow/using/building-a-workflow.md). Las audiencias exportadas se guardan como segmentos:

1. Cree un nuevo flujo de trabajo de objetivos.
1. Mediante las distintas actividades disponibles, establezca como objetivo un conjunto de destinatarios.
1. Después, arrastre y suelte una actividad **[!UICONTROL Update shared audience]** y, a continuación, ábrala.

   ![](assets/aam_export_example.png)

1. Defina la audiencia que desea exportar mediante la opción **[!UICONTROL Select a shared audience]**. En la ventana que se abre, puede seleccionar una audiencia existente o crear una nueva.

   Si selecciona una audiencia existente, solo se añaden los registros nuevos a la audiencia.

   Para exportar la lista de destinatarios en una audiencia nueva, complete el campo **[!UICONTROL Segment name]** y haga clic en **[!UICONTROL Create]** antes de seleccionar la audiencia recién creada.

   Complete la operación haciendo clic en el símbolo de aprobación situado en la parte superior derecha de la ventana y luego en el botón **[!UICONTROL OK]**.

1. Seleccione **[!UICONTROL AMC Data source]** para especificar el tipo de datos esperado. El esquema se determina automáticamente.

   ![](assets/aam_export_audience_activity.png)

1. Guarde la audiencia.

A continuación, se exporta la audiencia. La actividad de guardar la audiencia tiene dos transiciones salientes. La transición principal contiene los destinatarios exportados correctamente. La transición adicional contiene los destinatarios que no pueden asignarse a una ID de visitante o a una ID declarada.

La sincronización entre soluciones tarda de 24 a 36 horas. Después de este periodo, puede encontrar la nueva audiencia y reutilizarla en otras soluciones de Adobe Experience Cloud. Para obtener más información sobre el uso de una audiencia compartida de Adobe Campaign, consulte [documentación](https://experienceleague.adobe.com/en/docs/core-services/interface/services/audiences/create){target="_blank"}.

>[!NOTE]
>
>Para poder reconciliarlos, los registros deben tener una Adobe Experience Cloud ID (“ID de visitante” o “ID declarada”). Los registros sin Adobe Experience Cloud ID se omiten al exportar e importar audiencias.
