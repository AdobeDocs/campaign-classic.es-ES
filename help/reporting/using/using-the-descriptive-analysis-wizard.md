---
title: Uso del asistente de análisis descriptivo
seo-title: Uso del asistente de análisis descriptivo
description: Uso del asistente de análisis descriptivo
seo-description: null
page-status-flag: never-activated
uuid: 30554909-4b91-46ff-bd8d-fa57ab6304f9
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: reporting
content-type: reference
topic-tags: analyzing-populations
discoiquuid: 18ba04d9-7bab-4eea-8dbb-6c2c138c5293
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 1c86322fa95aee024f6c691b61a10c21a9a22eb7

---


# Uso del asistente de análisis descriptivo{#using-the-descriptive-analysis-wizard}

Para crear un informe de análisis descriptivo, utilice el asistente dedicado. La configuración depende de los datos que se analicen y de la renderización deseada.

## Análisis de los datos de la base de datos {#analyzing-data-in-the-database}

The descriptive analysis wizard can be launched via the **[!UICONTROL Tools > Descriptive analysis]** menu: in this case, the analysis concerns recipients by default (**nms:recipient**). Se aplica a todos los datos de la base de datos de Adobe Campaign.

![](assets/reporting_descriptive_wz_launch.png)

To analyze a table other than the standard recipients one (**nms:recipient**), click the **[!UICONTROL Advanced settings...]** link in the last stage of the wizard and select the table that matches your settings, in this case **cus:individual**:

![](assets/reporting_descriptive_other_schema.png)

If you want to produce statistics on part of the data, you can define a filter: to do this, click the **[!UICONTROL Advanced settings...]** link and define the filter to apply, as shown below:

![](assets/reporting_descriptive_wz_filter.png)

El análisis solo corresponde a los destinatarios de la base de datos mayores a 16 años y que viven en Londres.

## Análisis de un conjunto de datos {#analyzing-a-set-of-data}

Puede utilizar el asistente de análisis descriptivo a través de un contexto diferente: una lista, una transición de flujo de trabajo, uno o varios envíos, una selección de destinatarios, etc.

Se puede acceder a él a través de varios nodos del árbol de Adobe Campaign que señalan a la tabla de destinatarios.

Abra el asistente de análisis descriptivo seleccionando elementos y haciendo clic con el botón derecho. Solo se analizan los datos seleccionados.

![](assets/reporting_descriptive_from_recipients.png)

* For a set of **recipients**, select the recipients to be analyzed, then right-click and select **[!UICONTROL Actions > Explore...]**, as shown above. Si se aplica un filtro a la lista de destinatarios, solo se analiza el contenido resultante.

   Para seleccionar todos los destinatarios de la carpeta o el filtro actual, utilice el atajo de teclado CTRL+A. Esto hace que se seleccionen incluso los destinatarios ocultos.

   For an example of the descriptive analysis of recipients, refer to: [Qualitative data analysis](../../reporting/using/use-cases.md#qualitative-data-analysis).

* In the context of a **workflow**, place the cursor on a transition that points towards the recipients table, right-click and select **[!UICONTROL Analyze target]**. Para obtener más información sobre esto, consulte el ejemplo en [Análisis de un destino de transición en un flujo de trabajo](../../reporting/using/use-cases.md#analyzing-a-transition-target-in-a-workflow).
* Para las **listas**, seleccione una o varias listas y aplique el mismo proceso que para los destinatarios.
* In the context of a **delivery**, select the deliveries whose target you want to analyze, right-click and select **[!UICONTROL Actions > Explore the target]**, as shown below:

   ![](assets/reporting_descriptive_from_deliveries.png)

   A continuación se proporcionan ejemplos de análisis descriptivos de las entregas: [Analizando una población](../../reporting/using/use-cases.md#analyzing-a-population) y aquí: [Análisis de los registros](../../reporting/using/use-cases.md#analyzing-recipient-tracking-logs)de seguimiento de destinatarios.

## Configuración de la plantilla de distribución cualitativa {#configuring-the-qualitative-distribution-template}

The **[!UICONTROL Qualitative distribution]** template lets you create statistics on all types of data (e.g. company name, email domain).

Las opciones de configuración disponibles para un informe creado mediante la **[!UICONTROL Qualitative distribution]** plantilla se detallan en [Visualización de datos en la tabla](#displaying-data-in-the-table). Un ejemplo completo se detalla en [Análisis de una población](../../reporting/using/use-cases.md#analyzing-a-population).

Cuando utiliza el asistente de análisis descriptivo para analizar los datos, las opciones disponibles dependen de la configuración elegida. A continuación se detallan dichas acciones.

### Agrupamiento de datos {#data-binning}

Cuando se seleccionan las variables que se van a mostrar, puede definir el agrupamiento de datos, o en otras palabras, configurar criterios de agrupación para los datos seleccionados.

![](assets/s_ncs_user_report_wizard_031.png)

>[!NOTE]
>
>When the field concerned by the calculation is computed using an aggregate, check **[!UICONTROL The data is already aggregated]** to improve performances.

Las opciones difieren según el contenido del campo:

* **[!UICONTROL None]** :: esta opción le permite mostrar todos los valores disponibles para la variable, sin necesidad de enlazarla.

   >[!CAUTION]
   >
   >Esta opción debe utilizarse con cuidado: puede tener un impacto importante sobre el informe y el rendimiento del equipo.

* **[!UICONTROL Auto]** :: esta opción le permite mostrar los n valores representados con más frecuencia. Se calculan automáticamente y cada uno representa un porcentaje de las variables en comparación con el número de intervalos. En el caso de los valores numéricos, Adobe Campaign genera automáticamente “n” clases para ordenar los datos.
* **[!UICONTROL Manual]** :: esta opción funciona como la **[!UICONTROL Auto]** opción, excepto que puede establecer estos valores manualmente. To do this, click the **[!UICONTROL Add]** button to the right of the value table.

   Values can be initialized automatically by Adobe Campaign before personalization: to do this, enter the number of bins you want to generate and click the **[!UICONTROL Initialize with]** link, as shown below:

   ![](assets/reporting_descriptive_initialize.png)

   A continuación, ajuste su contenido para adaptarlo a sus necesidades:

   ![](assets/reporting_descriptive_initialize_perso.png)

   Según el nivel de precisión deseado, los campos que contengan fechas pueden agruparse por hora, día, mes, año, etc.

   ![](assets/reporting_descriptive_group_by_year.png)

* **[!UICONTROL Modulo]** :: permite crear grupos de valores en caso de valores numéricos. Por ejemplo, un módulo con un valor de 10 le permite crear un intervalo de valores que cambian de diez en diez.

   ![](assets/reporting_descriptive_initialize_modulo.png)

   Este ejemplo permite ver el desglose de los destinatarios por grupo de edad.

   ![](assets/reporting_descriptive_initialize_modulo_result.png)

### Visualización de datos en la tabla {#displaying-data-in-the-table}

Utilice la barra de herramientas para personalizar la visualización de variables en la tabla: elimine una columna, muestre datos en líneas en lugar de columnas, mueva una columna a la izquierda o a la derecha, visualice o modifique el cálculo de valores.

![](assets/s_ncs_user_report_wizard_toolbar.png)

La sección superior de la ventana permite seleccionar la configuración de visualización.

Puede mostrar u ocultar el nombre de las estadísticas y los subtotales y elegir la orientación de las estadísticas. Para obtener más información sobre esto, consulte Configuración [de visualización de informes de](../../reporting/using/processing-a-report.md#analysis-report-display-settings)análisis.

### Visualización de datos en el gráfico {#displaying-data-in-the-chart}

En el primer paso del asistente de análisis descriptivos, puede elegir mostrar los datos en el formulario de gráficos únicamente, sin tabla. En este caso, debe seleccionar variables al configurar el gráfico. Primero debe seleccionar el número de variables a mostrar y seleccionar los campos de la base de datos correspondiente.

![](assets/s_ncs_user_report_wizard_023.png)

A continuación, seleccione el tipo de gráfico deseado.

![](assets/s_ncs_user_report_wizard_024.png)

>[!NOTE]
>
>Puede mostrar las variables en un gráfico y en una tabla al mismo tiempo. To do this, enter the variables in the **[!UICONTROL Table configuration]** window. Click **[!UICONTROL Next]** and select the type of chart in the chart configuration window. Si se definen las subdimensiones en la tabla, no se muestran en el gráfico.

Click the **[!UICONTROL Variants]** link to modify the chart properties.

![](assets/reporting_descriptive_graphe_options.png)

Las opciones ofrecidas dependen del tipo de gráfico seleccionado. Para obtener más información, consulte [esta página](../../reporting/using/creating-a-chart.md#chart-types-and-variants).

### Cálculo de estadísticas {#statistics-calculation}

El asistente de análisis descriptivo le permite calcular varios tipos de estadísticas relacionadas con los datos. De forma predeterminada, solo se configura un recuento simple.

Click **[!UICONTROL Add]** to create a new statistic.

![](assets/reporting_descriptive_create_stat.png)

Las siguientes operaciones son posibles:

* **[!UICONTROL Count]** para contar todos los valores no nulos del campo que se van a agregar, incluidos los valores duplicados (del campo agregado),
* **[!UICONTROL Average]** calcular la media de los valores de un campo numérico,
* **[!UICONTROL Minimum]** calcular el mínimo de los valores de un campo numérico,
* **[!UICONTROL Maximum]** calcular el máximo de los valores de un campo numérico,
* **[!UICONTROL Sum]** calcular la suma de los valores de un campo numérico,
* **[!UICONTROL Standard deviation]** para calcular cómo se dispersan los valores devueltos alrededor de la media,
* **[!UICONTROL Row percentage distribution]** para calcular la relación entre el valor de una columna y el valor de una fila (disponible solo para tablas),
* **[!UICONTROL Column percentage distribution]** para calcular la relación entre el valor de una fila y el valor de una columna (disponible solo para tablas),
* **[!UICONTROL Total percentage distribution]** calcular la distribución de los destinatarios afectados por los valores,

   ![](assets/s_ncs_user_report_wizard_026.png)

* **[!UICONTROL Calculated field]** para crear un operador personalizado (disponible solo para tablas). The **[!UICONTROL User function]** field lets you enter the calculation to be applied to the data.

   Ejemplo: Calcular el importe promedio de compra por cliente en función del país y el origen

   ![](assets/report_compute_data_sample1.png)

   Para mostrar la información anterior en una tabla, debe crear un campo calculado para almacenar el importe promedio de compra por cliente.

   Para ello:

   1. Calcule el total de la compra.

      ![](assets/report_compute_data_sample2.png)

   1. Esta estadística no se muestra en la tabla. Debe desmarcar la **[!UICONTROL Display in the table]** opción de la **[!UICONTROL Advanced]** ficha.

      ![](assets/report_compute_data_sample3.png)

   1. Cree una nueva estadística de **[!UICONTROL Calculated field]** tipo e introduzca la fórmula siguiente en el **[!UICONTROL User function]** campo: **@purchase/@count**.

      ![](assets/report_compute_data_sample4.png)

### Visualización del informe {#displaying-the-report}

El último paso del asistente le permite mostrar el informe, es decir la tabla o el gráfico como se han configurado.

Cuando el informe contiene una tabla, la celda del resultado del cálculo aparece coloreada. Cuanto mayor sea el resultado, más intenso es el color.

![](assets/report_compute_data_sample1.png)

Es posible cambiar el diseño de los resultados. Para ello, haga clic con el botón derecho en la variable correspondiente y seleccione la entrada en el menú de acceso directo.

![](assets/s_ncs_user_report_wizard_029.png)

Cuando el informe incluye un gráfico, las etiquetas del pie de ilustración permiten filtrar la información mostrada: haga clic en una etiqueta para habilitar o deshabilitar la visualización en el gráfico.

![](assets/report_display_data_in_graph.png)

## Configuración de la plantilla de distribución cuantitativa {#configuring-the-quantitative-distribution-template}

Para generar un análisis descriptivo, seleccione la opción **análisis descriptivo nuevo desde una plantilla** si no está seleccionada de forma predeterminada.

The **[!UICONTROL Quantitative distribution]** template that lets you generate statistics on data which can be measured or counted (e.g. invoice amount, age of recipients).

The configuration mode of an analysis report created via the **[!UICONTROL Quantitative distribution]** template is detailed in an implementation example [Quantitative data analysis](../../reporting/using/use-cases.md#quantitative-data-analysis).

Las opciones disponibles al utilizar el asistente de análisis descriptivo para crear un informe cuantitativo se describen a continuación.

Comience por seleccionar la variable a la que corresponden los cálculos:

![](assets/s_ncs_user_report_wizard_017.png)

De forma predeterminada, Adobe Campaign ofrece una serie de estadísticas a calcular para los datos seleccionados. Puede cambiar esta lista y añadir o eliminar estadísticas según sus necesidades.

Las siguientes operaciones son posibles:

* **[!UICONTROL Count]** para contar todos los valores no nulos del campo que se van a agregar, incluidos los valores duplicados (del campo agregado),
* **[!UICONTROL Average]** calcular la media de los valores de un campo numérico,
* **[!UICONTROL Minimum]** calcular el mínimo de los valores de un campo numérico,
* **[!UICONTROL Maximum]** para calcular el máximo de los valores de un campo numérico.
* **[!UICONTROL Sum]** calcular la suma de los valores de un campo numérico,
* **[!UICONTROL Standard deviation]** para calcular cómo se distribuyen los valores devueltos alrededor del promedio.
* **[!UICONTROL Number of missing values]** para calcular el número de campos numéricos sin valores definidos.
* **[!UICONTROL Decile distribution]** para distribuir los valores devueltos de forma que cada uno represente 1/10 de los valores de un campo numérico.
* **[!UICONTROL Custom distribution]** para distribuir los valores devueltos en función de los umbrales definidos por el usuario.

   The **[!UICONTROL Detail...]** button lets you edit a statistic and, if needed, personalize its calculation or its display:

   ![](assets/s_ncs_user_report_wizard_030.png)

   El último paso del asistente muestra el informe de análisis cuantitativo.

   ![](assets/reporting_descriptive_view_report.png)

   Para realizar cambios en el informe, consulte [Procesamiento de un informe](../../reporting/using/processing-a-report.md).

