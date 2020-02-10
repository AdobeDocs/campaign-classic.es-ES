---
title: Creación de una tabla
seo-title: Creación de una tabla
description: Creación de una tabla
seo-description: null
page-status-flag: never-activated
uuid: c5bca799-a5d6-4d98-8fc5-25d7f71be5f7
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: reporting
content-type: reference
topic-tags: creating-new-reports
discoiquuid: 74084618-2b35-42c5-8a86-87ce137abb71
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 209ac4d81d2d27c264ee6b288bcb7fcb1900ffc5

---


# Creación de una tabla{#creating-a-table}

Puede añadir una tabla a un informe para visualizar los datos. Puede ser una tabla dinámica creada en función de las medidas del cubo, una lista con un grupo o una tabla que contenga un desglose de valores.

![](assets/s_advuser_report_page_activity_05.png)

## Creación de una lista con grupo {#creating-a-list-with-group}

A **[!UICONTROL List with group]** type table lets you group data in the table and produce statistics on it. Por ejemplo, puede crear totales y subtotales de los datos. Cada grupo tiene su propio encabezado, detalle y pie de página.

>[!CAUTION]
>
>The **[!UICONTROL Page]** activity containing the table must be preceded by a **[!UICONTROL Query]** or **[!UICONTROL Script]** activity to collect the data to be analyzed in the report. Para obtener más información sobre estas actividades, consulte [Recopilación de datos para analizar](../../reporting/using/collecting-data-to-analyze.md) y [secuencia de comandos](../../reporting/using/advanced-functionalities.md#script-activity).

### Principio de funcionamiento {#operating-principle}

Puede que necesite analizar varias categorías de datos a la vez. Una lista con grupo permite combinar datos y crear estadísticas sobre varios grupos de datos dentro de la misma tabla. Para ello, puede crear un grupo en la tabla.

En el siguiente ejemplo, el grupo muestra todas las campañas de la base de datos, los envíos y el número de mensajes enviados por envío y por campaña.

It lets you list the campaigns (**[!UICONTROL Label (Campaign)]**, the list of deliveries (**[!UICONTROL Label]** ) linked to the campaign, and lets you count the number of messages sent per delivery (**[!UICONTROL Processed)]**, before adding them up for each campaign (**[!UICONTROL Sum(@processed)]** ).

![](assets/s_advuser_ergo_listgroup_005.png)

### Pasos de implementación {#implementation-steps}

Aquí se proporciona un ejemplo completo de implementación: Caso [de uso: Cree un informe con una lista](#use-case--create-a-report-with-a-group-list)de grupos.

Tenga en cuenta los siguientes pasos para crear una tabla de tipo “Lista con grupo”:

1. Go to the report chart and place a **[!UICONTROL Query]** activity. Consulte [Recopilación de datos para analizar](../../reporting/using/collecting-data-to-analyze.md).
1. Rellene la tabla de origen y seleccione los campos de la tabla que corresponden a las estadísticas.
1. Place a **[!UICONTROL Page]** activity in the chart. Para obtener más información, consulte [Elementos estáticos](../../reporting/using/creating-a-new-report.md#static-elements).
1. Inserte una tabla de **[!UICONTROL List with group]** tipos en la página.
1. Especifique la ruta de datos o la tabla seleccionada como fuente de datos en la consulta.

   Este paso es obligatorio si desea recuperar los campos de la tabla de origen posteriormente e insertarlos en las celdas de la tabla.

1. Creación de una tabla y su contenido.
1. Display the finalized report in the **[!UICONTROL Preview]** tab. Luego puede publicar el informe y exportarlo a un formato diferente en caso necesario. Para obtener más información, consulte [Exportación de un informe](../../reporting/using/actions-on-reports.md#exporting-a-report).

### Adición de líneas y columnas {#adding-lines-and-columns}

By default, a **[!UICONTROL List with group]** type table includes a header, a detail line, and a footer line.

El propio grupo incluye líneas de encabezado, detalle y pie de página.

* **Línea de encabezado**: esta línea permite asignar un título a las columnas de la tabla.

   ![](assets/s_advuser_ergo_listgroup_003a.png)

* **Línea de detalle**: esta línea contiene los valores estadísticos.

   ![](assets/s_advuser_ergo_listgroup_004.png)

* **Línea de pie de página**: esta línea permite mostrar los valores totales.

   ![](assets/s_advuser_ergo_listgroup_003.png)

Puede añadir líneas y columnas según sus necesidades.

El grupo se puede colocar en cualquier línea de la tabla e incluir su propio encabezado, detalle y líneas de pie de página.

![](assets/s_advuser_ergo_listgroup_019.png)

**Línea y columna**: para añadir o eliminar una línea o una columna, vaya a una línea o columna existente y utilice el menú contextual.

![](assets/s_advuser_ergo_listgroup_006.png)

El tipo de línea que añada depende de la ubicación del cursor. For example, to add a header line, place your cursors on a header, then click **[!UICONTROL Add > A line above/below]**.

![](assets/s_advuser_ergo_listgroup_006a.png)

The width of the columns can be modified via the **[!UICONTROL Column format]** item.

**Grupo**: para añadir un grupo, vaya a una línea y seleccione el elemento correspondiente del menú desplegable.

![](assets/s_advuser_ergo_listgroup_007.png)

### Definición del contenido de la celda {#defining-cell-content}

Para editar una celda de la tabla y definir su contenido y formato, vaya a la celda y utilice el menú contextual.

Use the **[!UICONTROL Expression]** menu entry to select the values to display.

![](assets/s_advuser_ergo_listgroup_010.png)

* Para insertar los valores que se van a analizar directamente en la tabla, selecciónelos entre los campos disponibles.

   La lista de campos disponibles coincide con el contenido de la consulta antes de la tabla en el gráfico de creación de informes.

   ![](assets/s_advuser_ergo_listgroup_011.png)

* Introduzca una etiqueta para una celda, por ejemplo, de encabezado.

   Para ello, utilice el mismo proceso que para insertar un campo en la base de datos, pero no seleccione una expresión. Enter the label in the **[!UICONTROL Label]** field. Se muestra tal cual.

* Cálculo de un acumulado (un promedio, una suma, etc.) para mostrarlo en la celda.

   To do this, use the **[!UICONTROL Aggregates]** menu entry and select the desired campaign.

   ![](assets/s_advuser_ergo_listgroup_008.png)

### Definición del formato de la celda {#defining-cell-format}

![](assets/s_advuser_ergo_listgroup_017.png)

To define the cell format, the **[!UICONTROL Cell format...]** menu lets you access all formatting options available for the selected cell.

Estas opciones permiten personalizar la renderización final del informe y facilitar la lectura de la información.

Use the **[!UICONTROL Carriage return]** field when exporting data to Excel: select the **[!UICONTROL Yes]** value to force the carriage return. Este valor se mantiene al exportar. Para obtener más información, consulte [Exportación de un informe](../../reporting/using/actions-on-reports.md#exporting-a-report).

The **[!UICONTROL Cell format]** window lets you access the following tab:

* La **[!UICONTROL Value]** ficha
* La **[!UICONTROL Borders]** ficha
* La **[!UICONTROL Click]** ficha
* La **[!UICONTROL Extra]** ficha

The **[!UICONTROL Value]** tab lets you change the font and the various value attributes or to define a format based on their nature.

![](assets/s_advuser_ergo_listgroup_009.png)

The format changes data display: for example, the **[!UICONTROL Number]**, **[!UICONTROL Monetary]** and **[!UICONTROL Percentage]** formats allow you to align the figures on the right and display decimal points.

Ejemplo de cómo configurar un formato de divisas: puede especificar la moneda en la que se expresan los valores, elegir si se separan o no los millares y mostrar los valores negativos en rojo. La posición del símbolo de divisa depende del idioma del operador definido en su perfil.

![](assets/s_advuser_ergo_listgroup_012.png)

Ejemplo de configuración para fechas: puede elegir si desea mostrar o no la hora.

![](assets/s_advuser_ergo_listgroup_013.png)

La pestaña **Bordes** le permite añadir bordes a las líneas y columnas de la tabla. La adición de bordes a las celdas puede dar lugar a problemas de rendimiento al exportar informes de gran tamaño a Excel.

![](assets/s_advuser_ergo_listgroup_014.png)

If necessary, you can define borders in the table template (**[!UICONTROL Administration > Configuration > Form rendering]** ).

En este caso, se encuentra con la siguiente sintaxis:

En la pestaña web:

```
 .tabular td {
 border: solid 1px #000000;
 }
```

En la pestaña Excel:

```
 <style name="odd" fillColor="#fdfdfd">
  <border>
   <borderTop value="solid 0.05pt #000000" />
   <borderBottom value="solid 0.05pt #000000" />
   <borderLeft value="solid 0.05pt #000000" />
   <borderRight value="solid 0.05pt #000000" />
  </border>
 </style> 
 
 <style name="even" fillColor="#f7f8fa">
  <border>
   <borderTop value="solid 0.05pt #000000" />
   <borderBottom value="solid 0.05pt #000000" />
   <borderLeft value="solid 0.05pt #000000" />
   <borderRight value="solid 0.05pt #000000" />
  </border>
 </style> 
```

The **[!UICONTROL Click]** tab lets you define an action when the user clicks the content of a cell or of the table.

En el ejemplo que se muestra a continuación, al hacer clic en el valor de la celda se muestra la segunda página del informe, que contiene información sobre el envío en la celda.

![](assets/s_advuser_ergo_listgroup_015.png)

La pestaña **Extra** le permite vincular un campo visual a los datos, como una marca de color o una barra de valor. La marca de color se utiliza cuando la tabla se muestra como una leyenda en un gráfico. Para obtener más información sobre esto, consulte el ejemplo de implementación: [Paso 5: Crear la segunda página](#step-5---create-the-second-page)

![](assets/s_advuser_ergo_listgroup_016.png)

## Use case: Create a report with a group list {#use-case--create-a-report-with-a-group-list}

En este ejemplo creamos un informe de dos páginas: la primera página contiene la lista y el total de envíos por campaña, así como el número de mensajes enviados. Los nombres de envío son vínculos en los que puede hacer clic y le permiten ir a la segunda página del informe para ver el desglose de envíos por dominio de correo electrónico, según el envío seleccionado, con una tabla y un gráfico. En la segunda página, la tabla sirve como una leyenda para el gráfico.

![](assets/reporting_quick_start_report-final.png)

### Paso 1: Creación de un informe {#step-1---create-a-report}

Create a new report that concerns the campaign schema, **[!UICONTROL Campaigns (nms)]**.

![](assets/s_advuser_report_listgroup_001.png)

Haga clic **[!UICONTROL Save]** para crear el informe.

Vaya al gráfico y añada los primeros componentes que va a utilizar para diseñar el contenido del informe: una primera consulta y una primera página.

![](assets/reporting_quick_start_diagram.png)

### Paso 2: Creación de la primera consulta {#step-2---create-the-first-query}

La primera consulta le permite recopilar los envíos vinculados a cada campaña. El objetivo es mostrar un informe sobre los distintos envíos de la base de datos de Adobe Campaign enlazados a cada campaña.

Haga doble clic en la primera consulta para editarla y luego siga los pasos descritos a continuación para configurarla:

1. Start by changing the schema on which the query&#39;s source is applied: select the **[!UICONTROL Deliveries (nms)]** schema.
1. Click the **[!UICONTROL Edit query]** link and display the advanced fields.

   ![](assets/reporting_quick_start_query-1.png)

1. Seleccione los campos siguientes:

   * la etiqueta de envío,
   * la clave principal del envío,
   * la etiqueta de campaña,
   * el indicador de envíos procesados,
   * la clave externa del vínculo de la campaña,
   * el indicador de tasa de error.
   ![](assets/s_advuser_report_listgroup_002.png)

   Se recomienda enlazar un alias a cada campo para facilitar la selección de datos de la tabla que se añade a la primera página del informe.

   Para este ejemplo, se utilizan los siguientes alias:

   * Etiqueta: **@label**
   * Clave principal: **@deliveryId**
   * Etiqueta (campaña): **@label1**
   * Procesado: **@procesado**
   * Foreign key of the &#39;Campaign&#39; (&#39;id&#39; field) link: **@operationId**
   * Frecuencia de error: **@errorRatio**


1. Haga clic en el **[!UICONTROL Next]** botón dos veces para ir al **[!UICONTROL Data filtering]** paso.

   Añada una condición de filtro para recopilar solamente los envíos vinculados a una campaña.

   La sintaxis de este filtro es la siguiente: &quot;Clave externa del vínculo &#39;Campañas&#39; mayor que 0&quot;.

   ![](assets/reporting_quick_start_query_filter.png)

1. Click **[!UICONTROL Finish]** to save these conditions, then click **[!UICONTROL Ok]** to close the query editor.

### Step 3: Create the first page {#step-3--create-the-first-page}

En este paso, configuramos la primera página del informe. Para ello, siga los siguientes pasos:

1. Open the **[!UICONTROL Page]** activity and enter its title, for instance **Deliveries** in this case.

   ![](assets/s_advuser_report_listgroup_003.png)

1. Inserte una lista con un grupo mediante la barra de herramientas e introduzca su etiqueta, por ejemplo: Lista de envíos por campaña.

   ![](assets/s_advuser_report_listgroup_004.png)

1. Click the **[!UICONTROL Table data XPath...]** link and select the delivery link, i.e. `[query/delivery]`.

   ![](assets/s_advuser_report_listgroup_005.png)

1. Click the **[!UICONTROL Data]** tab and change layout of the table: add three columns on the right.

   ![](assets/s_advuser_report_listgroup_006.png)

1. Añada un grupo.

   ![](assets/s_advuser_report_listgroup_008.png)

   Este grupo le permite agrupar las campañas y los envíos vinculados a ellas.

1. En la ventana del grupo, haga referencia a la **la clave externa del vínculo “Campaña”** y cierre la ventana.

   ![](assets/s_advuser_report_listgroup_007.png)

1. Edit the first cell of the group header and insert the **[!UICONTROL Label]** field of the campaigns as an expression.

   ![](assets/s_advuser_report_listgroup_009.png)

1. Edit the second cell of the details line and select the deliveries **[!UICONTROL Label]**.

   ![](assets/s_advuser_report_listgroup_011.png)

1. Edit the format of this cell and open the **[!UICONTROL Click]** tab. Configure las opciones adecuadas para que cuando los usuarios hagan clic en el nombre de un envío, se abra en la misma ventana.

   ![](assets/s_advuser_report_listgroup_0111.png)

   Para ello, seleccione una acción de **[!UICONTROL Next page]** tipo y seleccione **[!UICONTROL In the same window]** como opción abierta.

   ![](assets/s_advuser_report_listgroup_0112.png)

1. En la sección inferior de la ventana, haga clic en **[!UICONTROL Add]** y especifique la **`/vars/selectedDelivery`** ruta y la **[!UICONTROL @deliveryId]** expresión que coincida con el alias de la clave principal de la entrega, tal como se define en la consulta creada anteriormente. Esta fórmula permite acceder al envío seleccionado.

   ![](assets/s_advuser_report_listgroup_010.png)

1. Edit the second cell of the footer line of the group and enter **[!UICONTROL Total per campaign]** as a label.

   ![](assets/s_advuser_report_listgroup_012.png)

1. Edit the third cell of the header line of the group and enter **[!UICONTROL Number of messages sent]** as a label.

   ![](assets/s_advuser_report_listgroup_013.png)

   Esta información coincide con el título de la columna.

1. Edite la tercera celda de la línea de detalle y seleccione el indicador de mensaje procesado como expresión.

   ![](assets/s_advuser_report_listgroup_014.png)

1. Edit the third cell of the footer line of the group, select the processed delivery indicator and apply the **[!UICONTROL Sum]** aggregate to it.

   ![](assets/s_advuser_report_listgroup_015.png)

1. Edite la cuarta celda de la línea de detalle y seleccione la **tasa de error de envío** como expresión.

   ![](assets/s_advuser_report_listgroup_016.png)

1. Seleccione esta celda para visualizar una barra de valores que represente la tasa de errores de envío.

   To do this, access the cell format, then go to the **[!UICONTROL More]** tab. Seleccione la **[!UICONTROL Value bar]** entrada en la lista desplegable y seleccione la **[!UICONTROL Hide the cell value]** opción.

   ![](assets/s_advuser_report_listgroup_023.png)

   Ahora puede ver una renderización del informe. Click the **[!UICONTROL Preview]** tab and select the **[!UICONTROL Global]** option: this shows the list of all deliveries in the Adobe Campaign database that are linked to a campaign.

   ![](assets/s_advuser_report_listgroup_025.png)

   We recommend using the **[!UICONTROL Preview]** tab to make sure the data in your table is properly selected and configured. Una vez realizada esta acción, puede ir al formato de la tabla.

1. Apply the **[!UICONTROL Bold]** style to the cells that show the total per campaign and the total number of messages processed.

   ![](assets/s_advuser_report_listgroup_024.png)

1. Click the 1st cell of the group header line, the one that displays the campaign name, and select **[!UICONTROL Edit > Merge to right]**.

   ![](assets/s_advuser_report_listgroup_026.png)

   Al combinar las dos primeras celdas de la línea del encabezado del grupo, se realinean el título de la campaña y la lista de envíos vinculada.

   ![](assets/s_advuser_report_listgroup_027.png)

   >[!CAUTION]
   >
   >Se recomienda esperar hasta que el informe se haya creado antes de combinar las celdas, ya que la combinación es irreversible.

### Paso 4: Creación de la segunda consulta {#step-4---create-the-second-query}

Queremos añadir una segunda consulta y una segunda página para mostrar el detalle de un envío cuando el usuario haga clic en el informe. Antes de añadir la consulta, edite la página que ha creado y habilite la transición saliente para que se pueda enlazar a la consulta.

1. Add a new query after the **[!UICONTROL Page]** activity and edit its schema: select the **[!UICONTROL Recipient delivery logs]** schema.

   ![](assets/reporting_quick_start_query-2.png)

1. Edite la consulta y defina las columnas de salida. Para mostrar el número de envíos por dominio de correo electrónico, debe hacer lo siguiente:

   * calcular la suma de las claves principales para contar el número de “logs” de envío:

      ![](assets/reporting_quick_start_query-2_count.png)

   * collect recipient email domains and group information on this field: to do this, select the **[!UICONTROL Group]** option in the domain name column.
   ![](assets/reporting_quick_start_query-2_filter.png)

   vínculo los siguientes alias a los campos:

   * count(clave principal): **@count**
   * Dominio de correo electrónico (destinatario): **@domain**

      ![](assets/reporting_quick_start_query-2_alias.png)


1. Haga clic en el **[!UICONTROL Next]** botón dos veces: esto te lleva al **[!UICONTROL Data filtering]** paso.

   Añada una condición de filtrado para recopilar únicamente la información vinculada al envío seleccionado.

   La sintaxis es la siguiente: La clave externa del vínculo &#39;Entrega&#39; es igual al valor de la configuración `$([vars/selectedDelivery])`

   ![](assets/s_advuser_report_listgroup_017.png)

1. Cierre la ventana de configuración de consulta y añada una página al gráfico justo después de la segunda consulta.

### Paso 5: Creación de la segunda página {#step-5---create-the-second-page}

1. Edit the page and enter its label: **Email domains**.
1. Uncheck the **[!UICONTROL Enable output transitions]** option: this is the last page of the report and will not be followed by another activity.

   ![](assets/s_advuser_report_listgroup_028.png)

1. Añada una nueva lista con un grupo mediante el menú contextual y denomínela **Dominios de correo electrónico por destinatario**.
1. Haga clic en el **[!UICONTROL Table data XPath...]** y seleccione el **[!UICONTROL Recipient delivery logs]** vínculo.

   ![](assets/s_advuser_report_listgroup_029.png)

1. In the **[!UICONTROL Data]** tab, adapt the table as follows:

   * Añada dos columnas a la derecha.
   * In the first cell of the detail line, add the **[!UICONTROL rowNum()-1]** expression to count the number of lines. A continuación, modifique el formato de la celda: en la **[!UICONTROL Extra]** ficha, seleccione **[!UICONTROL Color tab]** y haga clic en **[!UICONTROL Ok]**.

      ![](assets/s_advuser_report_listgroup_018.png)

      Esta configuración le permite utilizar la tabla como pie de ilustración para el gráfico.

   * In the second cell of the detail line, add the **[!UICONTROL Email domain(Recipient)]** expression.
   * In the third cell of the detail line, add the **[!UICONTROL count(primary key)]** expression.
   ![](assets/s_advuser_report_listgroup_019.png)

1. Añada un gráfico circular a la página mediante el menú contextual y asígnele la etiqueta **dominios de correo electrónico.** Para obtener más información, consulte Tipos [de gráficos y variantes](../../reporting/using/creating-a-chart.md#chart-types-and-variants).
1. Haga clic en el **[!UICONTROL Variants]** vínculo y anule la selección de las opciones **[!UICONTROL Display label]** y **[!UICONTROL Display caption]** .
1. Compruebe que no esté configurada ninguna ordenación de valores. Para obtener más información, consulte [esta sección](../../reporting/using/processing-a-report.md#configuring-the-layout-of-a-descriptive-analysis-report).

   ![](assets/s_advuser_report_listgroup_0191.png)

1. In the **[!UICONTROL Data]** tab, change the data source: select **[!UICONTROL Context data]** from the drop-down list.

   ![](assets/s_advuser_report_listgroup_020.png)

1. Then click **[!UICONTROL Advanced settings]** and select the link to the recipient delivery logs.

   ![](assets/s_advuser_report_listgroup_0201.png)

1. En la **[!UICONTROL Chart type]** sección, seleccione la **[!UICONTROL Email domain]** variable.
1. A continuación, añada el cálculo que desea llevar a cabo: seleccione la suma como operador.

   ![](assets/s_advuser_report_listgroup_0202.png)

1. Click the **[!UICONTROL Detail]** button to select the field which the count will concern, then close the configuration window.

   ![](assets/s_advuser_report_listgroup_030.png)

1. Guarde el informe.

   La página está configurada.

### Paso 6: Visualización del informe {#step-6---viewing-the-report}

To view the result of this configuration, click the **[!UICONTROL Preview]** tab and select the **[!UICONTROL Global]** option.

La primera página del informe detalla la lista de todos los envíos incluidos en la base de datos.

![](assets/s_advuser_report_listgroup_021.png)

Si hace clic en el vínculo de uno de estos envíos, se muestra el gráfico con el desglose de los dominios de correo electrónico para este envío. Ahora se encuentra en la segunda página del informe y puede regresar a la página anterior haciendo clic en el botón correspondiente.

![](assets/s_advuser_report_listgroup_022.png)

## Creación de un desglose o tabla dinámica {#creating-a-breakdown-or-pivot-table}

Este tipo de tabla le permite mostrar estadísticas calculadas en los datos de la base de datos.

El asistente de análisis descriptivo utiliza una configuración similar a estos tipos de informes. Para obtener más información, consulte [esta página](../../reporting/using/using-the-descriptive-analysis-wizard.md#configuring-the-quantitative-distribution-template).

Para obtener más información sobre la creación de una tabla dinámica, consulte [esta sección](../../reporting/using/using-cubes-to-explore-data.md).
