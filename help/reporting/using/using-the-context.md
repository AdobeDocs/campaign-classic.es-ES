---
solution: Campaign Classic
product: campaign
title: Uso del contexto
description: Uso del contexto
audience: reporting
content-type: reference
topic-tags: creating-new-reports
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '485'
ht-degree: 100%

---


# Uso del contexto{#using-the-context}

Si desea representar datos en forma de **[!UICONTROL tables]** o **[!UICONTROL charts]**, puede tomarlos de dos fuentes: una nueva consulta (consulte [Definición de un filtro directo en los datos](#defining-a-direct-filter-on-data)) o el contexto del informe (consulte [Uso de datos de contexto](#using-context-data)).

## Definición de un filtro directo para los datos {#defining-a-direct-filter-on-data}

### Filtrado de datos {#filtering-data}

La utilización de una actividad de tipo **[!UICONTROL Query]** no es obligatoria al crear un informe. Los datos pueden filtrarse directamente en las tablas y gráficos que conforman el informe.

Esto le permite seleccionar los datos para mostrar en el informe directamente a través de la actividad del informe **[!UICONTROL Page]**.

Para ello, haga clic en el vínculo **[!UICONTROL Filter data...]** de la pestaña **[!UICONTROL Data]**: este vínculo le permite acceder al editor de expresiones para definir una consulta de los datos que se van a analizar.

![](assets/reporting_filter_data_from_page.png)

### Ejemplo: Uso de un filtro en un gráfico {#example--use-a-filter-in-a-chart}

En el siguiente ejemplo, deseamos que el gráfico muestre solo los perfiles de destinatarios que viven en Francia y que realizaron una compra en algún momento del año.

Para definir este filtro, coloque una página en el gráfico y edítela. Haga clic en el vínculo **[!UICONTROL Filter data]** y cree un filtro que coincida con los datos que desea visualizar. Para obtener más información sobre la creación de consultas en Adobe Campaign, consulte [esta sección](../../platform/using/about-queries-in-campaign.md).

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
1. Vaya a la pestaña **[!UICONTROL Data]** y seleccione el cubo que desea utilizar.
1. Haga clic en el vínculo **[!UICONTROL Filter data...]** y defina la siguiente consulta para eliminar Adobe de la lista de empresas.

   ![](assets/s_ncs_advuser_report_display_03.png)

Solo los destinatarios que cumplan los criterios de filtrado aparecen en el informe.

![](assets/s_ncs_advuser_report_display_04.png)

## Uso de datos de contexto {#using-context-data}

Para representar los datos en forma de **[!UICONTROL table]** o **[!UICONTROL chart]**, los datos pueden provenir del contexto del informe.

En la página que contiene la tabla o el gráfico, la pestaña **[!UICONTROL Data]** permite seleccionar el origen de los datos.

![](assets/s_ncs_advuser_report_datasource_3.png)

* La opción **[!UICONTROL New query]** permite generar una consulta para recopilar datos. Para obtener más información sobre esto, consulte [Definición de un filtro directo en los datos](#defining-a-direct-filter-on-data).
* La opción **[!UICONTROL Context data]** permite utilizar los datos de entrada: el contexto del informe coincide con la información que contiene la transición entrante de la página que contiene el gráfico o la tabla. Este contexto puede, por ejemplo, contener los datos recopilados a través de la actividad **[!UICONTROL Query]** colocada ante la actividad **[!UICONTROL Page]** para la cual necesita especificar la tabla y los campos a los que afecta el informe.

Por ejemplo, en un cuadro de consulta, cree la siguiente consulta para los destinatarios:

![](assets/s_ncs_advuser_report_datasource_2.png)

Después, indique el origen de los datos en el informe, en este caso: **[!UICONTROL Data from the context]**.

La ubicación de los datos se deduce automáticamente. Si es necesario, puede forzar la ruta de datos.

![](assets/s_ncs_advuser_report_datasource_4.png)

Al seleccionar los datos a los que se refieren las estadísticas, los campos disponibles coinciden con los datos especificados en la consulta.

![](assets/s_ncs_advuser_report_datasource_1.png)

