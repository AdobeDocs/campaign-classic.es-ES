---
title: Conceptos y metodología
seo-title: Conceptos y metodología
description: Conceptos y metodología
seo-description: null
page-status-flag: never-activated
uuid: 595e9183-97f5-470d-9d82-dcd756e1fc83
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: reporting
content-type: reference
topic-tags: designing-reports-with-cubes
discoiquuid: 4655ad65-7eba-44d5-b3f9-f4b8f44d9d5c
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 62b2f1f6cfcaadd10880d428b8b94d73d2addcdb

---


# Prácticas recomendadas para cubos{#concepts-and-methodology}

## Agrupamiento de datos {#data-binning}

El agrupamiento permite simplificar la visualización de los datos reuniendo valores según ciertos criterios. Según la información disponible, puede definir grupos de edad, agrupar dominios de correo electrónico, restringir a una enumeración de valores, restringir explícitamente los datos que desea mostrar y agrupar todos los demás datos en una línea o columna dedicada, etc.

En general, hay tres tipos de agrupamiento disponibles:

1. Uso de intervalos de valores definidos manualmente. Por ejemplo: edad, carro de compras promedio, número de envíos abiertos, etc.). Para obtener más información sobre esto, consulte [Definición de cada bandeja](#defining-each-bin).
1. De forma dinámica, dependiendo de los valores de una enumeración: solo se muestran los valores contenidos en la enumeración; los demás valores se agrupan en “Otros”. Para obtener más información sobre esto, consulte Administración [dinámica de bandejas](#dynamically-managing-bins).
1. Uso de intervalos de valores; todos los demás se agrupan. Por ejemplo, de 18 a 25 años de edad, de 26 a 59 años de edad y el resto. Para obtener más información sobre esto, consulte [Creación de intervalos](#creating-value-ranges)de valores.

Para activar el agrupamiento, marque la casilla adecuada al crear la dimensión.

![](assets/s_advuser_cube_class_00.png)

Puede crear bandejas manualmente o enlazarlas a una enumeración existente.

Adobe Campaign también ofrece un asistente para el agrupamiento automático: los valores se pueden desglosar en “n” grupos o agrupar según los valores más frecuentes de la base de datos.

### Definición de cada grupo {#defining-each-bin}

To create each bin individually, select the **[!UICONTROL Define each bin]** option and use the table to create the various bins.

![](assets/s_advuser_cube_class_01.png)

Click the **[!UICONTROL Add]** button to create a new bin and list the values which will be grouped into the bin.

![](assets/s_advuser_cube_class_02.png)

En el siguiente ejemplo, los idiomas se agrupan en tres categorías: Inglés/alemán/holandés, francés/italiano/español y otros.

![](assets/s_advuser_cube_class_03.png)

Puede utilizar una máscara SQL para combinar varios valores en un filtro. Para ello, desproteja **[!UICONTROL Yes]** la columna **[!UICONTROL Use an SQL mask]** e introduzca el filtro SQL que se aplicará en la **[!UICONTROL Value or expression]** columna.

En el ejemplo siguiente, todos los dominios de correo electrónico que comienzan con **yahoo** (yahoo.fr, yahoo.com, yahoo.be, etc.) o con **ymail** (ymail.com, ymail.eu, etc.) se agrupan en la etiqueta **YAHOO!**, así como las direcciones con el dominio **rocketmail.com**.

![](assets/s_advuser_cube_class_03b.png)

### Administración dinámica de grupos {#dynamically-managing-bins}

Los valores se pueden administrar dinámicamente mediante enumeraciones. Esto significa que solo se muestran los valores contenidos en la enumeración. Cuando cambian los valores de la enumeración, el contenido del cubo se adapta automáticamente.

Para crear este tipo de agrupamiento de valores, siga los pasos siguientes:

1. Cree una nueva dimensión y habilite un agrupamiento.
1. Seleccione la **[!UICONTROL Dynamically link the values to an enumeration]** opción y seleccione la enumeración coincidente.

   ![](assets/s_advuser_cube_class_04.png)

   Siempre que se actualizan los valores de la enumeración, los grupos coincidentes se adaptan automáticamente.

### Creación de rangos de valores {#creating-value-ranges}

Puede agrupar los valores en rangos basados en un intervalo deseado.

Para definir rangos manualmente, haga clic en el **[!UICONTROL Add]** botón y seleccione **[!UICONTROL Define a range]** :

![](assets/s_advuser_cube_class_05.png)

Then specify the lower and upper limits and click **[!UICONTROL Ok]** to confirm.

### Generación automática de grupos {#generating-bins-automatically}

También es posible generar grupos automáticamente. Para ello, haga clic en el **[!UICONTROL Generate bins...]** vínculo.

![](assets/s_advuser_cube_class_06.png)

Puede:

* Recuperar los valores utilizados más frecuentemente

   En el ejemplo siguiente, se muestran los 4 valores utilizados con mayor frecuencia, mientras que los demás se cuentan y se agrupan en la categoría “Otros”.

* Generación de grupos en forma de ranuras

   En el ejemplo siguiente, Adobe Campaign crea automáticamente 4 ranuras de valor con el mismo tamaño para mostrar los valores en la base de datos.

En este caso, el filtro seleccionado en el esquema de hechos se omite.

### Enumeraciones {#enumerations}

Para mejorar la relevancia y legibilidad de un informe, Adobe Campaign permite crear enumeraciones específicas para reagrupar valores diferentes en el mismo grupo. Se hace referencia en los cubos a estas enumeraciones, reservadas para las agrupaciones, y después se muestran en los informes.

Adobe Campaign también ofrece una enumeración de dominios que permite mostrar una lista de los dominios de correo electrónico de todos los contactos de la base de datos, reagrupados por ISP, como se muestra en el siguiente ejemplo:

![](assets/nmx_report_sample.png)

Se crea mediante la siguiente plantilla:

![](assets/nmx_enum_domain.png)

To create a report using this enumeration, create a Cube using the **[!UICONTROL Email domain]** dimension. Elija la **[!UICONTROL Enable binning]** opción y luego **[!UICONTROL Dynamically link the values to an enumeration]**. A continuación, seleccione la enumeración **Dominios** como se muestra arriba. Todos los valores que no tengan un alias especificado se reagrupan con la etiqueta **Otros**.

![](assets/nmx_add_dimension.png)

Luego, cree un informe basado en este cubo para mostrar los valores.

Solo se debe modificar la enumeración para actualizar el informe relacionado. Por ejemplo, cree el valor **Adobe** y añada el alias **adobe.com**, y el informe se actualiza automáticamente con el valor de Adobe al nivel de la enumeración.

![](assets/nmx_add_alias.png)

The **[!UICONTROL Domains]** enumeration is used to generate built-in reports that display the list of domains. Para adaptar el contenido de estos informes, se puede editar esta lista.

Puede crear otras enumeraciones reservadas para agrupamiento y utilizarlas en otros cubos: todos los valores de alias se reagrupan en las bandejas especificadas en la primera pestaña de enumeración.

## Cálculo y uso de acumulados {#calculating-and-using-aggregates}

Los volúmenes de datos más grandes se pueden calcular en acumulados.

Los acumulados son útiles para manipular grandes volúmenes de datos. Se actualizan automáticamente según la configuración definida en la casilla de flujo de trabajo dedicado para integrar los datos recopilados recientemente en los indicadores.

Los acumulados se definen en la pestaña correspondiente de cada cubo.

![](assets/s_advuser_cube_agregate_01.png)

>[!NOTE]
>
>El flujo de trabajo para actualizar los cálculos acumulados se puede configurar en el propio acumulado, o el acumulado se puede actualizar a través de un flujo de trabajo externo vinculado al cubo correspondiente.

Para crear un nuevo acumulado, siga los siguientes pasos:

1. Haga clic en la **[!UICONTROL Aggregates]** ficha del cubo y, a continuación, haga clic en el **[!UICONTROL Add]** botón.

   ![](assets/s_advuser_cube_agregate_02.png)

1. Introduzca una etiqueta del acumulado y añada las dimensiones que desea calcular.

   ![](assets/s_advuser_cube_agregate_03.png)

1. Seleccione una dimensión y un nivel. Repita este proceso para cada dimensión y cada nivel.
1. Click the **[!UICONTROL Workflow]** tab to create the aggregation workflow.

   ![](assets/s_advuser_cube_agregate_04.png)

   * The **[!UICONTROL Scheduler]** activity lets you define the frequency of calculation updates. El planificador se detalla en [esta sección](../../workflow/using/scheduler.md).
   * The **[!UICONTROL Aggregate update]** activity lets you select the update mode which you want to apply: full or partial.

      De forma predeterminada, se lleva a cabo una actualización completa durante cada cálculo. Para activar una actualización parcial, seleccione la opción correspondiente y defina las condiciones de actualización.

      ![](assets/s_advuser_cube_agregate_05.png)

## Definición de medidas {#defining-measures}

The types of measures are defined in the **[!UICONTROL Measures]** tab of the cube. Puede calcular sumas, promedios, desviaciones, etc.

Puede crear tantas medidas como sea necesario: después, seleccione la medida que desee mostrar u ocultar en la tabla. Para más información, consulte [Muestra de medidas](#displaying-measures).

Para definir una nueva medida, siga los siguientes pasos:

1. Click the **[!UICONTROL Add]** button above the list of measures and select the type of measure and the formula to be calculated.

   ![](assets/s_advuser_cube_create_a_measure.png)

1. Si es necesario, y dependiendo el operador, elija la expresión correspondiente a la operación.

   The **[!UICONTROL Advanced selection]** button lets you create complex calculation formulas. Para obtener más información, consulte [esta sección](../../platform/using/about-queries-in-campaign.md).

   ![](assets/s_advuser_cube_create_a_measure_01.png)

1. The **[!UICONTROL Filter the measure data...]** link lets you restrict the calculation field and only apply it to specific data in the database.

   ![](assets/s_advuser_cube_create_a_measure_02.png)

1. Enter the label of the measure and add a description, then click **[!UICONTROL Finish]** to create it.

## Visualización de medidas {#displaying-measures}

Se puede configurar la visualización de las medidas en la tabla según sus necesidades:

* the display sequence of measures (refer to [Display sequence](#display-sequence)),
* the information to show/hide in the report (refer to [Configuring the display](#configuring-the-display))
* qué medidas se deben mostrar: porcentaje, total, número de decimales, etc. (consulte [Cambio del tipo de medida mostrada](#changing-the-type-of-measure-displayed)).

### Secuencia de visualización {#display-sequence}

The measures calculated in the cube are configured via the **[!UICONTROL Measures]** button.

Mueva las líneas para cambiar la secuencia de visualización. En el ejemplo siguiente, los datos franceses se mueven al final de la lista: esto significa que se muestran en la última columna.

![](assets/s_advuser_cube_in_report_config_04.png)

### Configuración de la visualización {#configuring-the-display}

La configuración de las medidas, líneas y columnas se puede realizar individualmente para cada medida o en general. Un icono específico permite acceder a la ventana de selección del modo de visualización.

* Haga clic en el **[!UICONTROL Edit the configuration of the pivot table]** icono para acceder a la ventana de configuración.

   Puede elegir si desea mostrar o no las etiquetas de las medidas, así como configurar su diseño (líneas o columnas).

![](assets/s_advuser_cube_in_report_config_05.png)

Las opciones de color permiten resaltar valores importantes para facilitar la lectura.

![](assets/s_advuser_cube_in_report_config_06.png)

### Modificación del tipo de medida mostrada {#changing-the-type-of-measure-displayed}

En cada medida, se puede definir la unidad y el formato que se va a aplicar.

![](assets/s_advuser_cube_in_report_config_07.png)

## Difusión de informes {#sharing-a-report}

Una vez configurado el informe, puede guardarlo y compartirlo con otros operadores.

Para ello, haga clic en el **[!UICONTROL Show the report properties]** icono y habilite la **[!UICONTROL Share this report]** opción.

![](assets/cube_share_option.png)

Especifique la categoría a la que pertenece el informe, así como su importancia. Para obtener más información, consulte en [esta página](../../reporting/using/configuring-access-to-the-report.md#report-display-context) las secciones **Secuencia de visualización** y **Definición del filtrado de opciones**.

Para confirmar estos cambios, debe guardar el informe.

![](assets/cube_share_confirm.png)

## Creación de filtros {#creating-filters}

Es posible crear filtros para ver una sección de los datos.

Para ello:

1. Haga clic en el **[!UICONTROL Add a filter]** icono.

   ![](assets/neolap_add_filter.png)

1. Seleccione la dimensión del filtro correspondiente.

   ![](assets/neolap_define_filter.png)

1. Seleccione el tipo de filtro y su nivel de precisión.

   ![](assets/neolap_ceate_filter.png)

1. Una vez creado, el filtro se muestra encima del informe.

   ![](assets/neolap_filter_zone.png)

   Haga clic en el filtro para editarlo.

   Haga clic en la cruz para eliminarlo.

   Puede combinar tantos filtros como sea necesario: todos se muestran en esta área.

   ![](assets/neolap_multiple_filters.png)

Cada vez que se modifica un filtro (añadir, eliminar, modificar), se debe volver a calcular el informe.

Los filtros también se pueden crear en función de una selección. To do this, select your source cells, lines and columns, then click the **[!UICONTROL Add a filter]** icon.

Para seleccionar una línea, columna o celda, haga clic en ella. Para anular la selección, haga clic de nuevo.

![](assets/neolap_create_filter_from_selection.png)

El filtro se aplica automáticamente y se añade a la zona de filtro encima del informe.

![](assets/neolap_create_filter_display.png)

