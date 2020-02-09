---
title: Exportación de datos
seo-title: Exportación de datos
description: Exportación de datos
seo-description: null
page-status-flag: never-activated
uuid: 818de79a-587f-4735-b333-4bc702c3b450
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: platform
content-type: reference
topic-tags: importing-and-exporting-data
discoiquuid: fecadb66-b81d-4fb6-9971-7bfd024d70b7
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 0ce6e5277c32bc18c20dca62e5b276f654d1ace5

---


# Exportación de datos{#exporting-data}

## Asistente de exportación {#export-wizard}

Los parámetros de exportación se registran mediante un asistente. El módulo de exportación está disponible como estándar y permite acceder y extraer datos de la base de datos: contactos, clientes, listas, segmentos, etc. Puede ser útil utilizar los datos de seguimiento de Campaign (historial de seguimiento, etc.) en una hoja de cálculo. Los datos de salida pueden estar en formato txt, csv, tab o xml.

### Paso 1: Selección de la plantilla de exportación {#step-1---choosing-the-export-template}

Al iniciar el asistente de exportación, primero debe seleccionar una plantilla. Por ejemplo, para configurar la exportación de destinatarios que se hayan registrado recientemente, siga los pasos a continuación:

1. Seleccione la **[!UICONTROL Profiles and Targets > Job > Generic imports and exports]** carpeta.
1. Haga clic en **Nuevo** y, a continuación, en **Exportar** para crear la plantilla de exportación.

   ![](assets/s_ncs_user_export_wizard01.png)

1. Click the arrow to the right of the **[!UICONTROL Export template]** field to select your template, or click **[!UICONTROL Select link]** to browse the tree.

   La plantilla nativa es **[!UICONTROL New text export]**. Esta plantilla no debe modificarse, pero puede duplicarla para configurar una nueva plantilla. By default, export templates are saved in the **[!UICONTROL Resources > Templates > Job templates]** node.

1. Enter a name for export in the **[!UICONTROL Label]** field. Puede añadir una descripción.
1. Seleccione el tipo de exportación. Existen dos tipos posibles de exportación: **[!UICONTROL Simple export]** para exportar sólo un archivo y **[!UICONTROL Multiple export]** exportar varios archivos en una sola ejecución, desde uno o varios tipos de documento de origen.

### Paso 2: Tipo de archivo de exportación {#step-2---type-of-file-to-export}

Seleccione el tipo de documento que desea exportar, por ejemplo, el esquema de los datos que desea exportar.

By default, when the export is launched from the **[!UICONTROL Jobs]** node the data comes from the recipient table. When the export is launched from a list of data (from the **[!UICONTROL right click > Export]** menu), the table to which the data belongs is automatically filled in in the **[!UICONTROL Document type]** field.

![](assets/s_ncs_user_export_wizard02.png)

* De forma predeterminada, la **[!UICONTROL Download the file generated on the server after the export]** opción está seleccionada. In the **[!UICONTROL Local file]** field, fill in the name and path of the file to be created, or browse your local disk by clicking the folder to the right of the field. Puede desmarcar esta opción para introducir la ruta de acceso y el nombre del archivo de salida del servidor.

   >[!NOTE]
   >
   >Los trabajos de importación y exportación automáticos siempre se realizan en el servidor.
   >
   >To export only some of the data, click **[!UICONTROL Advanced parameters]** and enter the number of lines to be exported in the appropriate field.

* Puede crear una exportación diferencial para exportar solo los registros que se han modificado desde la última ejecución. Para ello, haga clic en el **[!UICONTROL Advanced parameters]** vínculo, luego haga clic en la **[!UICONTROL Differential export]** ficha y, a continuación, seleccione **[!UICONTROL Activate differential export]**.

   ![](assets/s_ncs_user_export_wizard02_b.png)

   Debe especificar la fecha de la última modificación. Puede recuperarla de un campo o calcularla.

### Paso 3: Definición del formato de salida {#step-3---defining-the-output-format}

Seleccione un formato de salida para el archivo de exportación. Se pueden utilizar los siguientes formatos: texto, texto de ancho fijo, csv y xml.

![](assets/s_ncs_user_export_wizard03.png)

* For **[!UICONTROL Text]** format, select the delimiters to separate the columns (tabs, commas, semi-colons, or custom) and the strings (single or double quotes, or none).
* Para **[!UICONTROL text]** y **[!UICONTROL CSV]**, puede seleccionar la opción **[!UICONTROL Use first lines as column titles]**.
* Indique el formato de fecha y el formato de número. To do this, click the **[!UICONTROL Edit]** button for the field concerned and use the editor.
* Para los campos que contienen valores enumerados, puede seleccionar **[!UICONTROL Export labels instead of internal values of enumerations]**. For example, the title can be stored in the form **1=Mr.**, **2=Miss**,** 3=Mrs.**. Si se selecciona esta opción, se exportan **Mr.** **,** y **Mrs.**

### Paso 4: Selección de datos {#step-4---data-selection}

Seleccione los campos que desea exportar. Para ello:

1. Double-click the desired fields in the **[!UICONTROL Available fields]** list in order to add them to the **[!UICONTROL Output columns]** section.
1. Utilice las flechas de la derecha de la lista para definir el orden de los campos en el archivo de salida.

   ![](assets/s_ncs_user_export_wizard04.png)

1. Click the **[!UICONTROL Add]** button to call on functions. Para obtener más información sobre esto, consulte [Lista de funciones](../../platform/using/defining-filter-conditions.md#list-of-functions).

### Paso 5: Orden de las columnas {#step-5---sorting-columns}

Seleccione el orden de las columnas.

![](assets/s_ncs_user_export_wizard05.png)

### Paso 6: Condiciones de filtro {#step-6---filter-conditions-}

Puede añadir condiciones de filtro para evitar la exportación de todos los datos. La configuración de este filtro es la misma que la segmentación de destinatarios en el asistente de envíos. Consulte [esta página](../../delivery/using/steps-defining-the-target-population.md).

![](assets/s_ncs_user_export_wizard05_b.png)

### Paso 7: Formato de datos {#step-7---data-formatting}

Puede modificar el orden y las etiquetas de los campos del archivo de salida y aplicar transformaciones a los datos de origen.

* Para cambiar el orden de las columnas que desea exportar, seleccione la columna y utilice las flechas azules a la derecha de la tabla.
* To change the label of a field, click in the cell of the **[!UICONTROL Label]** column that matches the field to be modified, and enter the new label. Pulse Enter en el teclado para confirmar.
* To apply a case transformation to the content of a field, select it from the **[!UICONTROL Transformation]** column. Puede seleccionar:

   * Cambiar a minúsculas
   * Cambiar a mayúsculas
   * Primera letra en mayúsculas
   ![](assets/s_ncs_user_export_wizard06.png)

* Click **[!UICONTROL Add a calculated field]** if you want to create a new calculated field (for example, a column containing last name + first name). For more on this, refer to [Calculated fields](../../platform/using/importing-data.md#calculated-fields).

Si desea exportar una recopilación de elementos (por ejemplo, suscripciones de destinatarios, listas a las que pertenecen, etc.), debe especificar el número de elementos de la recopilación que desea exportar.

![](assets/s_ncs_user_export_wizard06_c.png)

### Paso 8: Previsualización de datos {#step-8---data-preview}

Haga clic en **[!UICONTROL Start the preview of the data]** para obtener una vista previa del resultado de exportación. De forma predeterminada, se muestran las 200 primeras líneas. To change this value, click the arrows to the right of the **[!UICONTROL Lines to display]** field.

![](assets/s_ncs_user_export_wizard07.png)

Haga clic en las pestañas en la parte inferior del asistente para cambiar de la vista previa de los resultados en columnas a los resultados en xml. También puede ver las consultas SQL generadas.

### Paso 9: Inicio de la exportación {#step-9---launching-the-export}

Haga clic en **[!UICONTROL Start]** para iniciar la exportación de datos.

![](assets/s_ncs_user_export_wizard08.png)

## Exportación de datos mediante un flujo de trabajo {#exporting-data-via-a-workflow}

Los flujos de trabajo pueden ser una forma útil de automatizar algunos de los procesos de exportación o de exportar conjuntos de datos precisos después de utilizar algunas de las actividades disponibles de gestión de datos para transformar los datos.

Para obtener más información sobre la exportación de datos desde un flujo de trabajo, consulte [esta sección](../../workflow/using/how-to-use-workflow-data.md).
