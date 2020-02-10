---
title: Extracción de datos (archivo)
description: Obtenga más información sobre la actividad del flujo de trabajo de extracción de datos (archivo).
page-status-flag: never-activated
uuid: c1e3fde3-183c-4602-9cef-760e4648fcf7
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: workflow
content-type: reference
topic-tags: action-activities
discoiquuid: fe4e6f64-eb0a-44bc-8221-6c9bfb99871f
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 5eb82bb5dae589cb18d42695565b25dad36006bd

---


# Extracción de datos (archivo){#extraction-file}

You can extract data from a workflow table in an external file using the **[!UICONTROL Data extraction (file)]** activity.

>[!CAUTION]
>
>Esta actividad siempre debe tener una transición entrante que contenga los datos que se extraerán.

Para configurar la extracción de datos, siga estos pasos:

1. Especifique el nombre del archivo de salida: este nombre puede contener variables insertadas mediante el botón de personalización a la derecha del campo.
1. Haga clic en **[!UICONTROL Edit the file format...]** para seleccionar los datos que desea extraer.

   ![](assets/s_advuser_extract_file_param.png)

   The **[!UICONTROL Handle groupings (GROUP BY + HAVING)]** option adds an extra step to filter the final result of the aggregate, for example on a given purchase order type, customers who have ordered more than 10 times, etc.

1. Si es necesario, puede añadir nuevas columnas al archivo de salida, como, por ejemplo, calcular o procesar resultados. To do this, click the **[!UICONTROL Add]** icon

   ![](assets/s_advuser_extract_file_add_col.png)

   In the additional line, click the **[!UICONTROL Edit expression]** icon to define the content of the new column.

   ![](assets/s_advuser_extract_file_add_exp.png)

   A continuación, tendrá acceso a la ventana de selección. Click **[!UICONTROL Advanced selection]** to choose the process to be applied to the data.

   ![](assets/s_advuser_extract_file_advanced_selection.png)

   Elija la fórmula deseada de la lista.

   ![](assets/s_advuser_extract_file_agregate_values.png)

## Lista de funciones acumuladas {#list-of-aggregate-functions}

A continuación, se muestra una lista de funciones acumuladas disponibles:

* **[!UICONTROL Count]** contar todos los valores no nulos del campo que se van a agregar, incluidos los valores duplicados (del campo agregado),

   **[!UICONTROL Distinct]** para contar el número total de valores distintos y no nulos del campo que se agregarán (los valores duplicados se excluyen antes del cálculo),

* **[!UICONTROL Sum]** calcular la suma de los valores de un campo numérico,
* **[!UICONTROL Minimum value]** calcular los valores mínimos de un campo (numéricos o de otro tipo),
* **[!UICONTROL Maximum value]** calcular los valores máximos de un campo (numéricos o de otro tipo),
* **[!UICONTROL Average]** para calcular la media de los valores de un campo numérico.

