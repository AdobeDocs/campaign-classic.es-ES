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
translation-type: tm+mt
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: tm+mt
source-wordcount: '324'
ht-degree: 66%

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

1. Si es necesario, puede añadir nuevas columnas al archivo de salida, como, por ejemplo, calcular o procesar resultados. To do this, click the **[!UICONTROL Add]** icon.

   ![](assets/s_advuser_extract_file_add_col.png)

   En la línea adicional, haga clic en el icono **[!UICONTROL Edit expression]** para definir el contenido de la nueva columna.

   ![](assets/s_advuser_extract_file_add_exp.png)

   A continuación, tendrá acceso a la ventana de selección. Haga clic **[!UICONTROL Advanced selection]** para elegir el proceso que se aplicará a los datos.

   ![](assets/s_advuser_extract_file_advanced_selection.png)

   Elija la fórmula deseada de la lista.

   ![](assets/s_advuser_extract_file_agregate_values.png)

Puede definir un proceso posterior que se va a ejecutar durante la extracción de datos, permitiéndole comprimir o cifrar los archivos. Para ello, se debe agregar el comando deseado en la **[!UICONTROL Script]** ficha de la actividad.

Para obtener más información sobre esto, consulte esta sección: [Cifrado o captura de un archivo](../../workflow/using/how-to-use-workflow-data.md#zipping-or-encrypting-a-file).

![](assets/postprocessing_dataextraction.png)

## Lista de funciones acumuladas {#list-of-aggregate-functions}

A continuación, se muestra una lista de funciones acumuladas disponibles:

* **[!UICONTROL Count]** para contar todos los valores no nulos del campo que se van a acumular, incluidos los valores duplicados (del campo acumulado).

   **[!UICONTROL Distinct]** para contar el número total de valores diferentes y no nulos del campo acumulado (los valores duplicados se excluyen antes del cálculo).

* **[!UICONTROL Sum]** para calcular la suma de los valores de un campo numérico.
* **[!UICONTROL Minimum value]** para calcular los valores mínimos de un campo (numérico o de otro tipo),
* **[!UICONTROL Maximum value]** para calcular los valores máximos de un campo (numérico o de otro tipo),
* **[!UICONTROL Average]** para calcular el promedio de los valores de un campo numérico,

