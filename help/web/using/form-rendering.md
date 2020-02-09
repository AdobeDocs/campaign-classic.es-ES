---
title: Renderización de formularios
seo-title: Renderización de formularios
description: Renderización de formularios
seo-description: null
page-status-flag: never-activated
uuid: 714ce201-5535-4fde-b388-1605ac54edcb
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: web
content-type: reference
topic-tags: web-forms
discoiquuid: 669635bd-868b-4550-b075-6294ccb71297
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 1c86322fa95aee024f6c691b61a10c21a9a22eb7

---


# Renderización de formularios{#form-rendering}

## Selección de la plantilla de renderización del formulario {#selecting-the-form-rendering-template}

La configuración de formulario permite seleccionar la plantilla utilizada para generar las páginas. To access them, click the **[!UICONTROL Settings]** button in the form detail toolbar, and select the **[!UICONTROL Rendering]** tab. Existe una cantidad de plantillas (hojas de estilo) disponibles de forma predeterminada.

![](assets/s_ncs_admin_survey_rendering_select.png)

La sección inferior del editor permite ver una renderización de la plantilla seleccionada.

La funcionalidad de zoom permite editar la plantilla seleccionada.

![](assets/s_ncs_admin_survey_render_edit.png)

Puede modificar o desactivar estas plantillas. To do this, click the **[!UICONTROL Page layout...]** link and personalize the information.

![](assets/s_ncs_admin_survey_render_edit_param.png)

Se puede:

* Cambiar la imagen utilizada como logotipo y adaptar su tamaño,
* Especificar también la ruta para acceder a la imagen de previsualización cuando los usuarios seleccionen esta plantilla de renderización.

The **[!UICONTROL Headers/Footers]** tab lets you change the information displayed in the headers and footers of each form page using this template.

![](assets/s_ncs_admin_survey_render_edit_header.png)

Each line of the **[!UICONTROL Page headers]** and **[!UICONTROL Page footers]** section corresponds to a line in the HTML page. Click **[!UICONTROL Add]** to create a new line.

Select an existing line and click the **[!UICONTROL Detail]** button to personalize it.

![](assets/s_ncs_admin_survey_render_edit_header_detail.png)

Puede cambiar el contenido de la línea, añadir bordes y cambiar los atributos de fuente a través de las pestañas correspondientes. Haga clic en **[!UICONTROL OK]** para confirmar estos cambios.

The **[!UICONTROL Position]** fields let you define the position of elements in the page header and footer.

![](assets/s_ncs_admin_survey_render_edit_header_position.png)

>[!NOTE]
>
>Las plantillas de procesamiento se almacenan en el **[!UICONTROL Administration > Configuration > Form rendering]** nodo.\
>Para obtener más información sobre esto, consulte [Personalización del procesamiento de formularios](#customizing-form-rendering)

## Personalización de la renderización de formularios {#customizing-form-rendering}

### Modificación del diseño de los elementos {#changing-the-layout-of-elements}

Se puede sobrecargar la hoja de estilo para cada elemento del formulario (campos de entrada, imágenes, botones de opción, etc.).

To do this, use the **[!UICONTROL Advanced]** tab.

![](assets/s_ncs_admin_survey_advanced_tab.png)

Permite definir las siguientes propiedades:

* **[!UICONTROL Label position]**:: consulte [Definición de la posición de las etiquetas](../../web/using/defining-web-forms-layout.md#defining-the-position-of-labels),
* **[!UICONTROL Label format]**: Ajuste de palabra o sin ajuste de palabra,
* **[!UICONTROL Number of cells]** :: consulte [Colocación de los campos en la página](../../web/using/defining-web-forms-layout.md#positioning-the-fields-on-the-page),
* **[!UICONTROL Horizontal alignment]** (Izquierda, Derecha, Centrado) y **[!UICONTROL Vertical alignment]** (Alta, Baja, Media),
* **[!UICONTROL Width]** de la zona: esto puede expresarse como porcentaje o en ems, puntos o píxeles (valor predeterminado),
* Maximum **[!UICONTROL Length]**: Maximum number of characters allowed (for Text, Number and Password type controls),
* **[!UICONTROL Lines]**:: número de líneas para una zona de **[!UICONTROL Multi-line text]** tipo,
* **[!UICONTROL Style inline]**:: le permite sobrecargar la hoja de estilo CSS con ajustes adicionales. Estos se separan con caracteres **;** como se muestra en el ejemplo siguiente:

   ![](assets/s_ncs_admin_survey_advanced_tab_inline.png)

### Definición de encabezados y pies de página {#defining-headers-and-footers}

Los campos se agrupan en una estructura de directorio cuya raíz tiene el mismo nombre que la página. Selecciónela para modificar el nombre.

The title of the window must be entered in the **[!UICONTROL Page]** tab of the form property window. También puede agregar un contenido definido al encabezado y al pie de la página (esta información se muestra en todas las páginas). This content is entered in the matching sections of the **[!UICONTROL Texts]** tab, as shown below:

![](assets/s_ncs_admin_survey_titles_config.png)

### Adición de elementos al encabezado HTML {#adding-elements-to-html-header}

Puede introducir elementos adicionales para su inserción en el encabezado HTML de una página de formulario. To do this, enter the elements in the **[!UICONTROL Header]** tab of the relevant page.

Esto permite hacer referencia a un icono que se que se muestra en la barra de título de la página, por ejemplo.

![](assets/webform_header_page_tab.png)

## Definición de una configuración de control {#defining-control-settings}

Cuando el usuario rellena el formulario, se realiza una comprobación automática de ciertos campos según su formato o configuración. This lets you make certain fields mandatory (refer to [Defining mandatory fields](#defining-mandatory-fields)) or check the format of the data entered (refer to [Checking data format](#checking-data-format)). Las comprobaciones se realizan durante la aprobación de la página (haciendo clic en un enlace o en un botón que habilita una transición de salida).

### Definición de campos obligatorios {#defining-mandatory-fields}

Para hacer que ciertos campos sean obligatorios, seleccione esta opción al crear el campo.

![](assets/s_ncs_admin_survey_required_field.png)

Si el usuario aprueba esta página sin haber introducido el campo, se muestra el siguiente mensaje:

![](assets/s_ncs_admin_survey_required_default_msg.png)

You can personalize this message by clicking the **[!UICONTROL Personalize this message]** link.

![](assets/s_ncs_admin_survey_required_custom_msg.png)

Si el usuario aprueba esta página sin haber introducido el campo, se muestra el siguiente mensaje:

![](assets/s_ncs_admin_survey_required_custom_msg2.png)

### Comprobación del formato de datos {#checking-data-format}

Para las comprobaciones de formularios cuyos valores se almacenen en un campo existente de la base de datos, se aplican las reglas del campo de almacenamiento.

Para las comprobaciones de formularios cuyos valores se almacenan en una variable, las reglas de aprobación dependen del formato de la variable.

For example, if you create a **[!UICONTROL Number]** check to store the client number, as shown below:

![](assets/s_ncs_admin_survey_choose_format.png)

El usuario debe introducir un número entero en el campo de formulario.

## Definición de la visualización condicional de campos {#defining-fields-conditional-display}

Se puede configurar la visualización de campos en la página para que se muestren en función de los valores que el usuario elija. Esto se puede aplicarse a un campo o a un grupo de campos (cuando se agrupan en un contenedor).

For each element of the page, the **[!UICONTROL Visibility]** section lets you define the display conditions.

![](assets/s_ncs_admin_survey_condition_edit.png)

Las condiciones pueden afectar al valor de los campos o de las variables de la base de datos.

En la ventana de selección de campos, se puede elegir entre los siguientes datos:

![](assets/s_ncs_admin_survey_condition_select.png)

* El directorio principal contiene los parámetros del contexto del formulario. Los parámetros predeterminados son el identificador (que coincide con el identificador encriptado del destinatario), idioma y origen.

   Para obtener más información, consulte [esta página](../../web/using/defining-web-forms-properties.md#form-url-parameters).

* The **[!UICONTROL Recipients]** sub-tree contains the input fields inserted into the form and stored in the database.

   Para obtener más información sobre esto, consulte [Almacenamiento de datos en la base de datos](../../web/using/web-forms-answers.md#storing-data-in-the-database).

* The **[!UICONTROL Variables]** sub-tree contains the available variables for this form. Para obtener más información sobre esto, consulte [Almacenamiento de datos en una variable](../../web/using/web-forms-answers.md#storing-data-in-a-local-variable)local.

Para obtener más información sobre este tema, consulte el caso de uso disponible aquí: [Mostrar diferentes opciones en función de los valores](../../web/using/use-cases--web-forms.md#displaying-different-options-depending-on-the-selected-values)seleccionados.

You can also condition the display of form pages using the **[!UICONTROL Test]** object. Para obtener más información, consulte [esta página](../../web/using/defining-web-forms-page-sequencing.md#conditional-page-display).

## Importación de elementos desde un formulario existente {#importing-elements-from-an-existing-form}

Se pueden importar campos o contenedores de otros formularios web. Esto permite crear una biblioteca de bloques reutilizables que se insertan en formularios, como el bloque de direcciones, el área de suscripción del boletín informativo, etc.

Para importar un elemento en un formulario, siga los siguientes pasos:

1. Edit the page which you want to insert one or more elements into, then click **[!UICONTROL Import an existing block]** in the toolbar.

   ![](assets/s_ncs_admin_survey_import_block.png)

1. Seleccione el formulario web que contiene los campos que desea importar y seleccione los contenedores y campos que desea importar.

   ![](assets/s_ncs_admin_survey_import_block_selection.png)

   >[!NOTE]
   >
   >The **[!UICONTROL Edit link]** icon to the right of the source form name lets you view the selected Web form.

1. Haga clic en **[!UICONTROL Ok]** para confirmar la inserción.

   ![](assets/s_ncs_admin_survey_import_block_rendering.png)

