---
title: Seguimiento de hipótesis
seo-title: Seguimiento de hipótesis
description: Seguimiento de hipótesis
seo-description: null
page-status-flag: never-activated
uuid: cb949a9d-8bbe-446b-b5b4-22234a91a68b
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: campaign
content-type: reference
topic-tags: response-manager
discoiquuid: 4452bfc6-9ac4-4d81-a63c-879a163c13ee
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: b47dcfa0e4ee2e5e43e7aa14b94e12fd70ff9c2d

---


# Seguimiento de hipótesis{#hypothesis-tracking}

El resultado de los cálculos de hipótesis está disponible en varios niveles de la plataforma Adobe Campaign: los indicadores calculados por hipótesis y las reacciones de las poblaciones objetivo se pueden ver a través de la hipótesis real, así como en los informes de hipótesis disponibles a través de campañas y envíos.

## Resultados de hipótesis {#hypothesis-results}

### Indicadores {#indicators}

Una vez que se ha calculado la hipótesis, se actualizan automáticamente varios indicadores de medida. These are available in the **[!UICONTROL General]** tab of the hypothesis.

![](assets/response_hypothesis_delivery_example_010.png)

Estos indicadores son:

* **Number of respondent contacts**: número de individuos contactados que coinciden con la hipótesis.
* **Contacted response rate**: número de contactos encuestados/cantidad total de personas contactadas durante el envío.
* **Number of respondent control group contacts**: número de grupos de control que coinciden con la hipótesis.
* **Response rate of the control group**: número de grupos de control encuestados/número total de grupos de control de envíos.
* **Number of reactions**: número de registros de la tabla que contiene la relación entre individuos, la hipótesis y la tabla de transacciones.

For the full list of indicators, click the **[!UICONTROL Display the list]** link:

![](assets/response_hypothesis_indicators_002.png)

Estos indicadores proporcionan la siguiente información:

* **Total revenue of population contacted**: ingresos totales en función del número de personas contactadas.
* **Total revenue of the control group**: ingresos totales en función del número de grupos de control.
* **Average revenue per contact**: media de ingresos totales por contacto.
* **Average revenue of control group**: media de ingresos totales por grupo de control.
* **Total margin per contact**: margen total de cada contacto.
* **Total margin of control group**: margen total de cada grupo de control.
* **Average margin per contact**: media del margen total por contacto.
* **Average margin of control groups**: media de los márgenes totales por grupo de control.
* **Ingresos** adicionales: (Ingresos medios del grupo de control contactado: ingresos medios)*Número de usuarios contactados
* **Margen** adicional: (Margen medio del grupo de control establecido en contacto - Margen medio del grupo de control) / número de personas contactadas
* **Average cost per contact**: coste calculado del envío/número de contactos.
* **ROI**: coste calculado del envío/margen total por contacto
* **Effective ROI**: coste calculado del envío/margen adicional (additional margin).
* **Significance**: contiene valores entre 0 y 3 según la relevancia de la campaña.

### Reacciones {#reactions}

You can view recipients&#39; reactions to the hypotheses via the **[!UICONTROL Reactions]** tab.

1. Once hypothesis calculation is complete, go to the **[!UICONTROL Campaign management > Measurement hypotheses]** node of the Adobe Campaign tree.
1. Select the desired hypothesis and click the **[!UICONTROL Reactions]** tab to view the list of recipients likely to purchase something following the marketing campaign.

   ![](assets/response_hypothesis_reactions_001.png)

## Informes {#reports}

The **[!UICONTROL Hypothesis report]** lets you view the results of the hypotheses performed on campaigns and deliveries. This report contains the indicators calculated by the hypothesis (for more on this, refer to [Indicators](#indicators)).

* **A nivel** de campaña: haga clic en el **[!UICONTROL Reports]** vínculo de la campaña relevante y seleccione la **[!UICONTROL Hypothesis report]**. Este informe contiene la lista de envíos de campañas y la hipótesis calculada para cada envío.

   ![](assets/response_hypothesis_campaign_report_001.png)

* **A nivel** de entrega: para acceder al informe, abra el envío correspondiente, haga clic en el **[!UICONTROL Reports]** en la ficha **[!UICONTROL Summary]** y seleccione el **[!UICONTROL Hypothesis report]**. Si se han calculado hipótesis para el mismo envío, el informe contendrá todas ellas.

   ![](assets/response_hypothesis_delivery_report_001.png)
