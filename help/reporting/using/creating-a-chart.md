---
product: campaign
title: Creación de un gráfico
description: Aprenda a diseñar un gráfico
feature: Reporting, Monitoring
badge-v8: label="También se aplica a v8" type="Positive" tooltip="También se aplica a Campaign v8"
exl-id: d32b614f-82c1-4363-816c-4ebedaa5cfe9
source-git-commit: e34718caefdf5db4ddd61db601420274be77054e
workflow-type: tm+mt
source-wordcount: '538'
ht-degree: 100%

---

# Creación de un gráfico{#creating-a-chart}



Los datos de la base de datos también se pueden recopilar y mostrar en un gráfico. Adobe Campaign ofrece un conjunto de representaciones gráficas. Su configuración se detalla a continuación.

Los gráficos se insertan directamente en una página de informe mediante el menú contextual o la barra de herramientas.

## Pasos para la creación {#creation-steps}

Para crear un gráfico en un informe, siga los siguientes pasos:

1. Edite la página donde desee mostrar el gráfico y seleccione el tipo de gráfico en la barra de herramientas.

   ![](assets/s_advuser_report_page_activity_04.png)

1. Introduzca un nombre y un pie de ilustración. Si es necesario, puede cambiar la posición del pie de ilustración mediante la lista desplegable.

   ![](assets/s_ncs_advuser_report_wizard_018.png)

1. Haga clic en la pestaña **[!UICONTROL Data]** para definir el origen de los datos y la serie que se va a calcular.

   Las estadísticas que se muestran en el gráfico se pueden calcular en función de una consulta o datos de contexto, es decir, los datos proporcionados por la transición entrante de la página actual (para más información, consulte [Uso de datos de contexto](../../reporting/using/using-the-context.md#using-context-data)).

   * Haga clic en el vínculo **[!UICONTROL Filter data...]** para definir los criterios de filtrado de los datos de la base de datos.

     ![](assets/reporting_graph_add_filter.png)

   * Para utilizar datos contextuales, seleccione **[!UICONTROL Context data]** en la lista desplegable **[!UICONTROL Source]** y haga clic en el vínculo **[!UICONTROL Advanced settings...]**. Seleccione los datos a los que corresponden las estadísticas.

     ![](assets/reporting_graph_from_context.png)

     A continuación, puede acceder a los datos contextuales para definir los valores que se muestran en el gráfico:

     ![](assets/reporting_graph_select-from_context.png)

## Tipos de gráficos y variantes {#chart-types-and-variants}

Adobe Campaign ofrece distintos tipos de representaciones gráficas. Se encuentran detalladas a continuación.

El tipo de gráfico se selecciona cuando se inserta en la página.

![](assets/s_advuser_report_page_activity_04.png)

También se puede modificar a través de la sección **[!UICONTROL Chart type]** de la pestaña **[!UICONTROL General]** del gráfico.

![](assets/reporting_change_graph_type.png)

Las variantes dependen del tipo de gráfico seleccionado. Se seleccionan mediante el vínculo **[!UICONTROL Variants...]**.

### Desglose: Gráficos circulares {#breakdown--pie-charts}

Este tipo de representación gráfica le permite mostrar una descripción general de los elementos medidos.

Los gráficos circulares solo permiten analizar una variable.

![](assets/reporting_graph_type_sector_1.png)

El vínculo **[!UICONTROL Variants]** le permite personalizar la renderización general del gráfico.

![](assets/reporting_graph_type_sector_2.png)

Los gráficos circulares permiten introducir el valor del radio interior en el campo adecuado.

Por ejemplo:

0,00 traza un círculo completo.

![](assets/s_ncs_advuser_report_sector_exple1.png)

0,40 traza un círculo con un radio del 40 %.

![](assets/s_ncs_advuser_report_sector_exple2.png)

1,00 solo traza el exterior del círculo.

![](assets/s_ncs_advuser_report_sector_exple3.png)

### Evolución: Curvas y áreas {#evolution--curves-and-areas}

Este tipo de representación gráfica le permite comprender la evolución de una o más medidas a lo largo de un tiempo.

![](assets/reporting_graph_type_curve.png)

### Comparación: Histogramas {#comparison--histograms}

Los histogramas permiten comparar los valores de una o más variables.

Para estos tipos de gráficos, se ofrecen las siguientes opciones en la ventana **[!UICONTROL Variants]**.

![](assets/reporting_select_graph_var.png)

Marque la opción **[!UICONTROL Display caption]** para mostrar el pie de ilustración con el gráfico y elegir su posición:

![](assets/reporting_select_graph_legend.png)

Si procede, puede apilar los valores.

![](assets/reporting_graph_type_histo.png)

Si es necesario, puede invertir la secuencia de visualización de los valores. Para ello, seleccione la opción **[!UICONTROL Reverse stacking]**.

### Conversión: canal {#conversion--funnel}

Este tipo de gráfico le permite realizar un seguimiento de la tasa de conversión de los elementos medidos.

## Interacción con el gráfico {#interaction-with-the-chart}

Puede definir una acción cuando el usuario haga clic en el gráfico. Abra la ventana **[!UICONTROL Interaction events]** y seleccione la acción que desea realizar.

En [esta sección](../../web/using/static-elements-in-a-web-form.md#inserting-html-content) se describen los tipos de interacción posibles y sus configuraciones.

![](assets/s_ncs_advuser_report_wizard_017.png)

## Estadísticas de cómputo {#calculating-statistics}

Los gráficos permiten mostrar las estadísticas de los datos recopilados.

Estas estadísticas se definen en la sección **[!UICONTROL Series parameters]** de la pestaña **[!UICONTROL Data]**.

Para crear una nueva estadística, haga clic en el icono **[!UICONTROL Add]** y configure la ventana correspondiente. A continuación se detallan los tipos de cálculos disponibles.

![](assets/reporting_add_statistics.png)

Para obtener más información, consulte [esta sección](../../reporting/using/using-the-descriptive-analysis-wizard.md#statistics-calculation).
