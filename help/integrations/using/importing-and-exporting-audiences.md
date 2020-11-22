---
solution: Campaign Classic
product: campaign
title: Importación y exportación de audiencias
description: Importación y exportación de audiencias
audience: integrations
content-type: reference
topic-tags: audience-sharing
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '629'
ht-degree: 100%

---


# Importación y exportación de audiencias{#importing-and-exporting-audiences}

## Importación de una audiencia {#importing-an-audience}

Se pueden importar audiencias o segmentos a Adobe Campaign desde Audience Manager o el servicio principal Personas mediante las listas de destinatarios.

1. Vaya al nodo **[!UICONTROL Profiles and Targets]** > **[!UICONTROL Lists]** en el explorador de Adobe Campaign.
1. En la barra de herramientas, seleccione **[!UICONTROL New]** > **[!UICONTROL Create a shared audience...]**.

   ![](assets/aam_import_audience.png)

1. En la ventana que se abre, haga clic en **[!UICONTROL Select a shared audience]** para ir a la lista de audiencias y segmentos compartidos disponibles en las otras soluciones de Adobe Experience Cloud.
1. Seleccione una audiencia y confirme. La información de la audiencia se completa automáticamente.

   Tenga en cuenta que para poder importar la audiencia compartida, debe asignarse a usted el producto **[!UICONTROL Audience library]** en la consola de administración y ser administrador en Audience Manager. Para obtener más información, consulte [documentación de la consola de administración](https://helpx.adobe.com/es/enterprise/managing/user-guide.html).

   ![](assets/aam_import_audience_3.png)

1. Seleccione la fuente de datos AMC del campo **[!UICONTROL AMC Data source]** para definir el tipo de datos deseados.

   ![](assets/aam_import_audience_2.png)

1. Guarde la audiencia.

La audiencia se importa mediante un flujo de trabajo técnico. La lista importada contiene elementos que se pueden conciliar mediante la fuente de datos AMC. Los elementos no reconocidos por Adobe Campaign no se importan.

El proceso de importación tarda en sincronizarse de 24 a 36 horas cuando los segmentos se importan directamente desde el servicio principal Personas o Audience Manager. Después de este periodo, puede encontrar y utilizar la nueva audiencia en Adobe Campaign.

>[!NOTE]
>
>Si se están importando audiencias de Adobe Analytics a Adobe Campaign, dichas audiencias deben compartirse primero en el servicio principal Personas o en Audience Manager. Este proceso tarda de 12 a 24 horas, que se deben añadir a la sincronización de 24 a 36 horas con Campaign.
>
>En ese caso específico, el tiempo que tarda en compartirse la audiencia puede alcanzar las 60 horas. Para obtener más información sobre el uso compartido de las audiencias de Adobe Analytics en el servicio principal Personas y Audience Manager, consulte esta [documentación](https://docs.adobe.com/content/help/es-ES/analytics/components/segmentation/segmentation-workflow/seg-publish.html).

Los datos de audiencias se sustituyen por completo cada vez que se sincronizan. Solo se pueden importar segmentos. No se admiten datos granulares, lo que incluye pares de valor clave, características y reglas.

## Exportación de un público {#exporting-an-audience}

Se puede exportar una audiencia de Adobe Campaign a Audience Manager o al servicio principal Personas mediante un flujo de trabajo. Los procesos para crear y utilizar un flujo de trabajo se describen en [este documento](../../workflow/using/building-a-workflow.md). Las audiencias exportadas se guardan como segmentos en el servicio principal Personas:

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

La sincronización entre Adobe Campaign y el servicio principal Personas tarda de 24 a 36 horas. Después de este periodo, puede encontrar la nueva audiencia en el servicio principal Personas y reutilizarla en otras soluciones de Adobe Experience Cloud. Para obtener más información sobre el uso de una audiencia compartida de Adobe Campaign en el servicio principal Personas de Adobe, consulte la siguiente [documentación](https://docs.adobe.com/content/help/es-ES/core-services/interface/audiences/t-audience-create.html).

>[!NOTE]
>
>Para poder conciliarlos, los registros deben tener una Adobe Experience Cloud ID (“ID de visitante” o “ID declarada”). Los registros sin Adobe Experience Cloud ID se omiten al exportar e importar audiencias.

