---
title: Definición de contenido condicional
seo-title: Definición de contenido condicional
description: Definición de contenido condicional
seo-description: null
page-status-flag: never-activated
uuid: 2b49958d-6429-445d-a7dc-caaca072f4e4
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: reporting
content-type: reference
topic-tags: creating-new-reports
discoiquuid: 0ca5e0f6-cc81-4da9-aecf-a095cc1a19f9
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 209ac4d81d2d27c264ee6b288bcb7fcb1900ffc5

---


# Definición de contenido condicional{#defining-a-conditional-content}

Se puede condicionar la visualización de elementos o páginas específicas del informe.

Para que los elementos específicos sean condicionales, adapte su configuración de visibilidad. For more on this, refer to [Conditioning item display](#conditioning-item-display).

To make the display of one or more pages conditional, use a **[!UICONTROL Test]** type activity. Para obtener más información, consulte [Determinación de la visualización de la página](#conditioning-page-display).

## Condicionamiento de la visualización de elementos {#conditioning-item-display}

Para que la visualización de parte de un informe sea condicional, debe definir sus condiciones de visibilidad: si no se cumplen, los elementos no se muestran.

Las condiciones de visibilidad pueden depender del estado del operador o de los elementos seleccionados o introducidos en la página del informe.

En [esta sección](../../web/using/form-rendering.md#defining-fields-conditional-display) se ofrecen ejemplos de visualización condicional de elementos en una página.

En el ejemplo siguiente, la condición de visualización depende del idioma:

![](assets/reporting_display_condition.png)

## Condiciones de visualización de la página {#conditioning-page-display}

In the chart of a report, the **[!UICONTROL Test]** activity lets you change the sequence of pages depending on one or more conditions.

Esta actividad se basa en el siguiente principio operativo:

1. Place a **[!UICONTROL Test]** in a chart and edit it.
1. Click the **[!UICONTROL Add]** button to create the various possible cases.

   ![](assets/reporting_test_sample.png)

   For each case, an output transition is added to the **[!UICONTROL Test]** activity.

   ![](assets/reporting_test_transitions.png)

1. Select the **[!UICONTROL Enable default transition]** to add a transition, in case one of the configured conditions isn&#39;t met.

   Para obtener más información, consulte [esta sección](../../web/using/defining-web-forms-page-sequencing.md#conditional-page-display).

A **[!UICONTROL Test]** activity can be placed at the start of the chart to condition the display depending on context or operator profile for instance.
