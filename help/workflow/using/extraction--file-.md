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
translation-type: ht
source-git-commit: 5eb82bb5dae589cb18d42695565b25dad36006bd

---


# Extracción de datos (archivo){#extraction-file}

Puede extraer datos de una tabla de flujo de trabajo desde un archivo externo mediante la actividad **[!UICONTROL Extracción de datos (archivo)]**.

>[!CAUTION]
>
>Esta actividad siempre debe tener una transición entrante que contenga los datos que se extraerán.

Para configurar la extracción de datos, siga estos pasos:

1. Especifique el nombre del archivo de salida: este nombre puede contener variables insertadas mediante el botón de personalización a la derecha del campo.
1. Haga clic en **[!UICONTROL Editar formato de archivo...]** para seleccionar los datos que desee extraer.

   ![](assets/s_advuser_extract_file_param.png)

   La opción **[!UICONTROL Handle groupings (GROUP BY + HAVING)]** añade un paso adicional para filtrar el resultado final del acumulado, por ejemplo, en un tipo de orden de compra determinado, clientes que hayan hecho un orden más de 10 veces, etc.

1. Si es necesario, puede añadir nuevas columnas al archivo de salida, como, por ejemplo, calcular o procesar resultados. Para hacer esto, haga clic en el icono **[!UICONTROL Add]**.

   ![](assets/s_advuser_extract_file_add_col.png)

   En la línea adicional, haga clic en el icono **[!UICONTROL Edit expression]** para definir el contenido de la nueva columna.

   ![](assets/s_advuser_extract_file_add_exp.png)

   A continuación, tendrá acceso a la ventana de selección. Haga clic **[!UICONTROL Advanced selection]** para elegir el proceso que se aplicará a los datos.

   ![](assets/s_advuser_extract_file_advanced_selection.png)

   Elija la fórmula deseada de la lista.

   ![](assets/s_advuser_extract_file_agregate_values.png)

## Lista de funciones acumuladas {#list-of-aggregate-functions}

A continuación, se muestra una lista de funciones acumuladas disponibles:

* **[!UICONTROL Count]** para contar todos los valores no nulos del campo que se van a acumular, incluidos los valores duplicados (del campo acumulado).

   **[!UICONTROL Distinct]** para contar el número total de valores diferentes y no nulos del campo acumulado (los valores duplicados se excluyen antes del cálculo).

* **[!UICONTROL Sum]** para calcular la suma de los valores de un campo numérico.
* **[!UICONTROL Minimum value]** para calcular los valores mínimos de un campo (numérico o de otro tipo),
* **[!UICONTROL Maximum value]** para calcular los valores máximos de un campo (numérico o de otro tipo),
* **[!UICONTROL Average]** para calcular el promedio de los valores de un campo numérico,

