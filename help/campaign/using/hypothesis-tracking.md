---
product: campaign
title: Seguimiento de hipótesis
description: Seguimiento de hipótesis
audience: campaign
content-type: reference
topic-tags: response-manager
exl-id: 1dc6d03b-698c-4750-9563-0676fcd185df
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: tm+mt
source-wordcount: '448'
ht-degree: 100%

---

# Seguimiento de hipótesis{#hypothesis-tracking}

El resultado de los cálculos de hipótesis está disponible en varios niveles de la plataforma Adobe Campaign: los indicadores calculados por hipótesis y las reacciones de las poblaciones objetivo se pueden ver a través de la hipótesis real, así como en los informes de hipótesis disponibles a través de campañas y envíos.

## Resultados de hipótesis {#hypothesis-results}

### Indicadores {#indicators}

Una vez que se ha calculado la hipótesis, se actualizan automáticamente varios indicadores de medida. Están disponibles en la pestaña **[!UICONTROL General]** de la hipótesis.

![](assets/response_hypothesis_delivery_example_010.png)

Estos indicadores son:

* **Number of respondent contacts**: número de individuos contactados que coinciden con la hipótesis.
* **Contacted response rate**: número de contactos encuestados/cantidad total de personas contactadas durante la entrega.
* **Number of respondent control group contacts**: número de grupos de control que coinciden con la hipótesis.
* **Response rate of the control group**: número de grupos de control encuestados/número total de grupos de control de envíos.
* **Number of reactions**: número de registros de la tabla que contiene la relación entre individuos, la hipótesis y la tabla de transacciones.

Para ver la lista completa de los indicadores, haga clic en el vínculo **[!UICONTROL Display the list]**:

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
* **Additional revenue**: (media de ingresos de los contactos-Media de ingresos por grupo de control)*Número de contactos
* **Additional margin**: (Media de ingresos de los contactos-Media de ingresos por grupo de control)/Número de contactos
* **Average cost per contact**: coste calculado de la entrega/número de contactos.
* **ROI**: coste calculado de la entrega/margen total por contacto
* **Effective ROI**: coste calculado de la entrega/margen adicional (additional margin).
* **Significance**: contiene valores entre 0 y 3 según la relevancia de la campaña.

### Reacciones {#reactions}

Se pueden ver las reacciones de los destinatarios a las hipótesis a través de la pestaña **[!UICONTROL Reactions]**.

1. Una vez completado el cálculo de la hipótesis, vaya a **[!UICONTROL Campaign management > Measurement hypotheses]** en el árbol de Adobe Campaign.
1. Seleccione la hipótesis deseada y haga clic en la pestaña **[!UICONTROL Reactions]** para ver la lista de destinatarios que probablemente compren algo después de la campaña de marketing.

   ![](assets/response_hypothesis_reactions_001.png)

## Informes {#reports}

El informe **[!UICONTROL Hypothesis report]** permite ver los resultados de las hipótesis realizadas en las campañas y envíos. Este informe contiene los indicadores calculados por la hipótesis (para obtener más información, consulte [Indicators](#indicators)).

* **At campaign level**: haga clic en el vínculo **[!UICONTROL Reports]** de la campaña correspondiente y seleccione el **[!UICONTROL Hypothesis report]**. Este informe contiene la lista de envíos de campañas y la hipótesis calculada para cada envío.

   ![](assets/response_hypothesis_campaign_report_001.png)

* **At delivery level**: para acceder al informe, abra la entrega correspondiente, haga clic en **[!UICONTROL Reports]** en la pestaña **[!UICONTROL Summary]** y seleccione **[!UICONTROL Hypothesis report]**. Si se han calculado hipótesis para el mismo envío, el informe contendrá todas ellas.

   ![](assets/response_hypothesis_delivery_report_001.png)
