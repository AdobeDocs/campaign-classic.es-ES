---
title: Uso del contexto
seo-title: Uso del contexto
description: Uso del contexto
seo-description: null
page-status-flag: never-activated
uuid: ac8c7068-d640-4934-b7f5-bc91b98eab4c
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: reporting
content-type: reference
topic-tags: creating-new-reports
discoiquuid: 72fe6df0-0271-48f9-bd6d-bb1ff25fbdf3
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 1c86322fa95aee024f6c691b61a10c21a9a22eb7

---


# Uso del contexto{#using-the-context}

Si desea representar datos en forma de **[!UICONTROL tables]** o **[!UICONTROL charts]**, puede tomarlos de dos fuentes: una nueva consulta (consulte [Definición de un filtro directo en los datos](#defining-a-direct-filter-on-data)) o el contexto del informe (consulte [Uso de datos](#using-context-data)de contexto).

## Definición de un filtro directo para los datos {#defining-a-direct-filter-on-data}

### Filtrado de datos {#filtering-data}

Using a **[!UICONTROL Query]** type activity isn&#39;t mandatory when building a report. Los datos pueden filtrarse directamente en las tablas y gráficos que conforman el informe.

This enables you to select the data to display in the report directly via the **[!UICONTROL Page]** activity of the report.

To do this, click the **[!UICONTROL Filter data...]** link in the **[!UICONTROL Data]** tab: this link lets you access the expressions editor to define a query on the data to be analyzed.

![](assets/reporting_filter_data_from_page.png)

### Ejemplo: Uso de un filtro en un gráfico {#example--use-a-filter-in-a-chart}

En el siguiente ejemplo, deseamos que el gráfico muestre solo los perfiles de destinatarios que viven en Francia y que realizaron una compra en algún momento del año.

Para definir este filtro, coloque una página en el gráfico y edítela. Click the **[!UICONTROL Filter data]** link and create the filter that matches the data you want to display. Para obtener más información sobre la creación de consultas en Adobe Campaign, consulte [esta sección](../../platform/using/about-queries-in-campaign.md).

![](assets/s_ncs_advuser_report_wizard_029.png)

En este caso, deseamos visualizar el desglose por ciudad de los destinatarios seleccionados.

![](assets/reporting_graph_with_2vars.png)

La renderización debería tener este aspecto:

![](assets/reporting_graph_with_2vars_preview.png)

### Ejemplo: Uso de un filtro en una tabla dinámica {#example--use-a-filter-in-a-pivot-table}

En este ejemplo, el filtro le permite visualizar solo los clientes no parisinos en la tabla dinámica, sin utilizar otra consulta de antemano.

Siga estos pasos:

1. Coloque una página en el gráfico y edítela.
1. Cree una tabla dinámica.
1. Go to the **[!UICONTROL Data]** tab and select the cube to be used.
1. Click the **[!UICONTROL Filter data...]** link and define the following query to remove Adobe from the list of companies.

   ![](assets/s_ncs_advuser_report_display_03.png)

Solo los destinatarios que cumplan los criterios de filtrado aparecen en el informe.

![](assets/s_ncs_advuser_report_display_04.png)

## Uso de datos de contexto {#using-context-data}

To represent data in the form of a **[!UICONTROL table]** or a **[!UICONTROL chart]**, the data can come from the report context.

In the page that contains the table or the chart, the **[!UICONTROL Data]** tab lets you select the data source.

![](assets/s_ncs_advuser_report_datasource_3.png)

* The **[!UICONTROL New query]** option lets you build a query to collect data. Para obtener más información sobre esto, consulte [Definición de un filtro directo en los datos](#defining-a-direct-filter-on-data).
* The **[!UICONTROL Context data]** option lets you use the input data: the context of the report coincides with the information contained in the inbound transition of the page that contains the chart or the table. This context may, for instance, contain data collected via a **[!UICONTROL Query]** activity placed before the **[!UICONTROL Page]** activity and for which you need to specify the table and the fields that the report concerns.

Por ejemplo, en un cuadro de consulta, cree la siguiente consulta para los destinatarios:

![](assets/s_ncs_advuser_report_datasource_2.png)

Después, indique el origen de los datos en el informe, en este caso: **[!UICONTROL Data from the context]**.

La ubicación de los datos se deduce automáticamente. Si es necesario, puede forzar la ruta de datos.

![](assets/s_ncs_advuser_report_datasource_4.png)

Al seleccionar los datos a los que se refieren las estadísticas, los campos disponibles coinciden con los datos especificados en la consulta.

![](assets/s_ncs_advuser_report_datasource_1.png)

