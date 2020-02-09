---
title: Procesamiento de informes
seo-title: Procesamiento de informes
description: Procesamiento de informes
seo-description: null
page-status-flag: never-activated
uuid: af8f1101-135f-49ce-bada-bd19fe32053b
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: reporting
content-type: reference
topic-tags: analyzing-populations
discoiquuid: 667746cb-b553-4a71-8523-6b2695047ab6
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 62b2f1f6cfcaadd10880d428b8b94d73d2addcdb

---


# Uso de un informe de análisis{#processing-a-report}

## Guardado de un informe de análisis {#saving-an-analysis-report}

Si tiene los derechos adecuados, puede guardar un informe de análisis creado a partir de una plantilla o exportarla en formato Excel, PDF u OpenOffice.

To save your report, click **[!UICONTROL Save]** and give your report a label.

Select **[!UICONTROL Also save data]** if you wish to create a history of your report and see the values of the report at the time of saving. Para obtener más información sobre esto, consulte [Archiving de informes](#archiving-analysis-reports)de análisis.

The **[!UICONTROL Share this report]** option allows other operators to access the report.

![](assets/s_ncs_user_report_wizard_010.png)

Una vez guardado, este informe puede volver a utilizarse para generar otros informes de análisis:

![](assets/s_ncs_user_report_wizard_08a.png)

To make changes to this report, edit the **[!UICONTROL Administration > Configuration > Adobe Campaign tree reports]** node of the Adobe Campaign tree (or the first &#39;Reports&#39; type folder for which the operator has editing rights). Para obtener más información sobre esto, consulte [Configuración del diseño de un informe](#configuring-the-layout-of-a-descriptive-analysis-report)de análisis descriptivo.

## Configuración adicional del informe de análisis {#analysis-report-additional-settings}

Una vez que se haya guardado un informe de análisis descriptivo, puede editar sus propiedades y acceder a opciones adicionales.

![](assets/s_ncs_user_report_wizard_08b.png)

Estas opciones son las mismas que los informes estándar y se encuentran detalladas en [esta página](../../reporting/using/properties-of-the-report.md).

## Configuración del diseño de un informe de análisis descriptivo {#configuring-the-layout-of-a-descriptive-analysis-report}

Puede personalizar la visualización y el diseño de los datos en los gráficos y tablas del análisis descriptivo. All options are accessed via the Adobe Campaign tree, in the **[!UICONTROL Edit]** tab of each report.

### Modo de visualización del informe del análisis {#analysis-report-display-mode}

When you create a report using the **[!UICONTROL qualitative distribution]** template, table and chart display modes are selected by default. Si solo desea un modo de visualización, desmarque la casilla correspondiente. Esto significa que solo está disponible la pestaña del modo de visualización seleccionado.

![](assets/s_ncs_advuser_report_display_01.png)

To change the schema of the report, click the **[!UICONTROL Select the link]** and select another table from the database.

![](assets/s_ncs_advuser_report_display_02.png)

### Configuración de la visualización del informe del análisis {#analysis-report-display-settings}

Se pueden ocultar o mostrar las estadísticas y los subtotales, así como elegir la orientación de las estadísticas.

![](assets/s_ncs_advuser_report_display_05.png)

Cuando genere las estadísticas, puede personalizar su etiqueta.

![](assets/s_ncs_advuser_report_display_06.png)

Sus nombres se muestran en el informe.

![](assets/s_ncs_advuser_report_display_07.png)

Sin embargo, si desmarca la etiqueta y la opción de visualizar el subtotal, no se muestran en el informe. El nombre aparece en un globo de texto cuando pasa el cursor sobre una celda de la tabla.

![](assets/s_ncs_advuser_report_display_08.png)

De forma predeterminada, las estadísticas se muestran en línea. Para cambiar la orientación, seleccione la opción adecuada en la lista desplegable.

![](assets/s_ncs_advuser_report_wizard_035a.png)

En el ejemplo siguiente, las estadísticas se muestran en columnas.

![](assets/s_ncs_advuser_report_wizard_035.png)

### Diseño de los datos del informe del análisis {#analysis-report-data-layout}

Puede personalizar el diseño de datos directamente en las tablas de análisis descriptivo. Para esto, haga clic con el botón derecho en la variable con la que desee trabajar. Seleccione las opciones disponibles en el menú desplegable:

* **[!UICONTROL Pivot]** para cambiar el eje de la variable.
* **[!UICONTROL Up]** / **[!UICONTROL Down]** para intercambiar las variables en líneas.
* **[!UICONTROL Move to the right]** / **[!UICONTROL Move to the left]** para intercambiar las variables en columnas.
* **[!UICONTROL Turn]** para invertir los ejes de variables.
* **[!UICONTROL Sort from A to Z]** para ordenar los valores de las variables de baja a alta.
* **[!UICONTROL Sort from Z to A]** para ordenar los valores de las variables de alto a bajo.

   ![](assets/s_ncs_advuser_report_wizard_016.png)

Para volver a la visualización inicial, actualice la vista.

### Opciones del gráfico del informe del análisis {#analysis-report-chart-options}

Se puede personalizar la visualización de los datos en el gráfico. To do this, click the **[!UICONTROL Variables...]** link available during the chart type selection stage.

![](assets/s_ncs_advuser_report_wizard_3c.png)

Estas son las opciones disponibles:

* La sección superior de la ventana permite modificar el área de visualización del gráfico.
* Las etiquetas se muestran en el gráfico de forma predeterminada. You can hide them by un-checking the **[!UICONTROL Show values]** option.
* The **[!UICONTROL Accumulate values]** option lets you add up values from one series to another.
* Puede decidir si desea mostrar o no el pie del gráfico: para ocultarlo, desmarque la opción correspondiente. El pie de ilustración se muestra de forma predeterminada fuera del gráfico, en la esquina superior derecha.

   El pie de ilustración también se puede mostrar sobre el gráfico para ahorrar espacio de visualización. Para ello, seleccione la opción **[!UICONTROL Include in the chart]**

   Select the vertical and horizontal alignment in the **[!UICONTROL Caption position]** drop-down list.

   ![](assets/s_ncs_advuser_report_wizard_3d.png)

## Exportación de un informe de análisis {#exporting-an-analysis-report}

Para exportar los datos de un informe de análisis, haga clic en la lista desplegable y seleccione el formato de salida deseado.

![](assets/s_ncs_user_report_wizard_09.png)

Para obtener más información, consulte [esta página](../../reporting/using/actions-on-reports.md).

## Reutilización de informes y análisis existentes {#re-using-existing-reports-and-analyses}

Puede crear informes de análisis descriptivos sobre los datos utilizando los informes existentes ya almacenados en Adobe Campaign. Este modo es posible tras guardar los análisis o cuando se hubieran creado y configurado informes a través del asistente de análisis descriptivo.

Para saber cómo guardar los análisis descriptivos, consulte [Guardar un informe](#saving-an-analysis-report)de análisis.

To create descriptive analysis reports, the descriptive analysis wizard must be executed via a workflow transition or via the **[!UICONTROL Tools > Descriptive analysis]** menu.

1. Seleccione **[!UICONTROL Existing analyses and reports]** y haga clic en **[!UICONTROL Next]**.
1. Esto le permite acceder a la lista de informes disponibles. Seleccione el informe que desea generar.

   ![](assets/s_ncs_user_report_wizard_01.png)

## Archivado de informes de análisis {#archiving-analysis-reports}

Cuando crea un análisis descriptivo basado en un análisis existente, puede crear archivos para almacenar datos y comparar los resultados de los informes.

Para crear un historial, realice los pasos siguientes:

1. Abra un análisis existente o cree un nuevo asistente de análisis descriptivo.
1. En la página de visualización del informe, haga clic en el botón para crear un historial en la barra de herramientas y, a continuación, confirme como se muestra a continuación:

   ![](assets/reporting_descriptive_historize_icon.png)

1. Utilice el botón de acceso al archivo para mostrar los análisis anteriores.

   ![](assets/reporting_descriptive_historize_access.png)

