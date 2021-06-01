---
product: campaign
title: Creación de un flujo de trabajo de segmentación
description: Obtenga información sobre cómo realizar pruebas A/B mediante un caso de uso dedicado.
audience: delivery
content-type: reference
topic-tags: a-b-testing
exl-id: aa21fa33-aef9-484a-b454-0cd5a6868a98
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: tm+mt
source-wordcount: '136'
ht-degree: 100%

---

# Creación de un flujo de trabajo de segmentación {#step-1--creating-a-targeting-workflow}

Se debe crear el flujo de trabajo en la pestaña **[!UICONTROL Targeting and Workflows]** de una campaña. Se compone de una actividad **[!UICONTROL Query]**, una actividad **[!UICONTROL Split]** vinculada a dos actividades **[!UICONTROL Email delivery]**, una actividad **[!UICONTROL Wait]**, una actividad **[!UICONTROL JavaScript code]** y una actividad **[!UICONTROL Delivery]**.

1. Si aún no lo ha hecho, cree una campaña (para obtener más información, consulte esta [sección](../../campaign/using/setting-up-marketing-campaigns.md#creating-a-campaign)).

   ![](assets/use_case_abtesting_targetwkfl_001.png)

1. Vaya a la pestaña **[!UICONTROL Targeting and Workflows]**.

   ![](assets/use_case_abtesting_targetwkfl_002.png)

1. Cambie la etiqueta del flujo de trabajo existente o haga clic en **[!UICONTROL Add]** para crear una nueva (para obtener más información, consulte esta [sección](../../campaign/using/marketing-campaign-deliveries.md#selecting-the-target-population)).

   ![](assets/use_case_abtesting_targetwkfl_003.png)

1. Utilice el ratón para arrastrar y colocar actividades en el diagrama de flujo de trabajo, incluido una **[!UICONTROL Query]** (pestaña **[!UICONTROL Target]**), un **[!UICONTROL Split]** (pestaña **[!UICONTROL Target]**), dos **[!UICONTROL Email deliveries]**(pestaña **[!UICONTROL Deliveries]**), una actividad **[!UICONTROL Wait]** (pestaña **[!UICONTROL Flow Control]**), una actividad **[!UICONTROL JavaScript code]** (pestaña **[!UICONTROL Actions]**) y una actividad **[!UICONTROL Delivery]** (pestaña **[!UICONTROL Actions]**).

![](assets/use_case_abtesting_targetwkfl_004.png)

Ahora puede configurar las muestras de población (consulte [Paso 2: Configuración de muestras de población](../../delivery/using/a-b-testing-uc-population-samples.md)).
