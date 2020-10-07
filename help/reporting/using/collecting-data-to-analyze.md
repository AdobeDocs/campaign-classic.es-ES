---
title: Recopilación de datos para analizar
seo-title: Recopilación de datos para analizar
description: Recopilación de datos para analizar
seo-description: null
page-status-flag: never-activated
uuid: 5a611786-6e56-4fce-b232-dd8428f3a5f2
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: reporting
content-type: reference
topic-tags: creating-new-reports
discoiquuid: 594a333d-1fc3-49a0-b3f6-7ea8fa4321e9
translation-type: tm+mt
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: tm+mt
source-wordcount: '507'
ht-degree: 86%

---


# Recopilación de datos para analizar{#collecting-data-to-analyze}

Los datos que se utilizan para crear el informe pueden seleccionarse directamente en la página del informe (para más información, consulte [) o recopilarse mediante una o más consultas.](../../reporting/using/using-the-context.md)

Esta actividad ofrece tres métodos diferentes:

1. Creación de una consulta utilizando los datos de la base de datos.
1. Procesamiento de los datos contenidos en una lista.
1. Uso de datos contenidos en un cubo existente.

La elección del método depende del tipo de cálculo, el volumen de datos y su durabilidad, etc. Todos estos parámetros deben examinarse con cuidado para evitar sobrecargar la base de datos de Adobe Campaign y para optimizar la generación y manipulación de los informes creados. Para obtener más información, consulte [esta página](../../reporting/using/best-practices.md#optimizing-report-creation).

En todos los casos, los datos se recopilan mediante una actividad de tipo **[!UICONTROL Query]**.

![](assets/reporting_query_edit.png)

Este modo de selección de datos es adecuado cuando es necesario recopilar o crear los datos del informe utilizando los datos de la base de datos. En algunos casos, también puede seleccionar los datos directamente desde los elementos utilizados en el informe. Por ejemplo, al insertar un gráfico puede seleccionar los datos de origen directamente. Para obtener más información, consulte [Uso del contexto](../../reporting/using/using-the-context.md).

## Uso de los datos de un esquema {#using-the-data-from-a-schema}

Para utilizar datos vinculados a un esquema de base de datos, seleccione la opción adecuada en el editor de consultas y configure la consulta que desea aplicar.

El ejemplo siguiente permite recopilar el número de destinatarios de cada país entre los perfiles de la base de datos. Después se pueden visualizar en un informe en forma de tabla.

![](assets/reporting_query_from_schema.png)

## Uso de una lista importada {#using-an-imported-list}

Para crear un informe, puede utilizar datos de una lista de datos importados.

To do this, select the **[!UICONTROL Use an imported list]** option in the query box and select the concerned list.

![](assets/reporting_query_from_list.png)

Click the **[!UICONTROL Edit query...]** link to define the data to collect among the elements in this list for building the report.

## Uso de un cubo {#using-a-cube}

Se puede seleccionar un cubo para definir la consulta.

![](assets/reporting_query_from_cube.png)

Los cubos permiten ampliar la capacidad de análisis y exploración de la base de datos al mismo tiempo que facilitan la configuración de los informes y las tablas para los usuarios finales: simplemente seleccione un cubo ya existente y completamente configurado y utilice sus cálculos, medidas y estadísticas. Para obtener más información sobre la creación de cubos, consulte [esta sección](../../reporting/using/about-cubes.md).

Click the **[!UICONTROL Edit query...]** link and select the indicators that you want to display or use in your report.

![](assets/reporting_query_from_cube_edit_query.png)

## Opciones de filtrado en las consultas {#filtering-options-in-the-queries}

Para evitar la ejecución de consultas en toda la base de datos, es necesario filtrar los datos.

### Filtro simplificado {#simplified-filter}

Puede seleccionar la opción **[!UICONTROL Filter automatically with the context]** para poder acceder al informe a través de un nodo específico del árbol, como una lista, un destinatario o una entrega.

The **[!UICONTROL Filter with the folder]** option lets you specify a folder and take into account only its contents. Esto permite filtrar los datos del informe para mostrar solo los datos de una de las carpetas del árbol, como se muestra a continuación:

![](assets/reporting_control_folder.png)

### Limitación de la cantidad de datos recopilados {#limiting-the-amount-of-data-collected}

Configure el número de registros que desea que extraiga la consulta a través de las opciones de limitación de resultados:

* **[!UICONTROL Limit to first record]** para extraer un resultado,
* **[!UICONTROL Size]** para extraer un número determinado de registros.

