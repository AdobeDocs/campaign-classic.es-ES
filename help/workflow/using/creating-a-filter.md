---
title: Creación de filtros
description: Aprenda a crear un filtro al realizar consultas.
page-status-flag: never-activated
uuid: 0556d53e-0fdf-47b3-b1e0-b52e85e0c662
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: workflow
content-type: reference
topic-tags: use-cases
discoiquuid: 7e5605c8-78f2-4011-b317-96a59c699848
translation-type: ht
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: ht
source-wordcount: '210'
ht-degree: 100%

---


# Creación de filtros {#creating-a-filter}

Los filtros disponibles en Adobe Campaign se definen mediante condiciones de filtrado que se crean con el mismo modo de funcionamiento que las consultas.

>[!NOTE]
>
>Para obtener más información sobre creación de filtros, consulte [esta sección](../../platform/using/filtering-options.md).

El nodo **[!UICONTROL Administration > Configuration > Predefined filters]** contiene todos los filtros utilizados en las listas y vistas generales.

Por ejemplo, la lista de operadores puede filtrarse con **[!UICONTROL Active accounts]**:

![](assets/query_editor_filter_sample_1.png)

El filtro coincidente contiene la consulta en el valor **[!UICONTROL Account disabled]** del esquema **[!UICONTROL Operators]**:

![](assets/query_editor_filter_sample_2.png)

En la misma lista, el filtro **[!UICONTROL By login or label]** permite filtrar los datos de la lista en función del valor introducido en el campo de filtro:

![](assets/query_editor_filter_sample_3.png)

Se crea de la siguiente manera:

![](assets/query_editor_filter_sample_4.png)

Para hacer coincidir las condiciones de filtrado, la cuenta de operador debe comprobar una de las siguientes condiciones:

* Su etiqueta contiene los caracteres introducidos en el campo de entrada,
* El nombre del operador contiene los caracteres introducidos en el campo de entrada,
* El contenido del área de descripción contiene los caracteres introducidos en el campo de entrada.

>[!NOTE]
>
>La función **[!UICONTROL Upper]** permite desactivar la función que distingue entre mayúsculas y minúsculas.

La columna **[!UICONTROL Taken into account if]** permite definir los criterios de aplicación para estas condiciones de filtrado. En este caso, los caracteres **$(/tmp/@text)** representan el contenido del campo de entrada vinculado al filtro:

![](assets/query_editor_filter_sample_5.png)

Aquí, **$(/tmp/@text)=&#39;agency&#39;**

La expresión **$(/tmp/@text)!=&#39;&#39;** aplica cada condición cuando el campo de entrada no está vacío.
