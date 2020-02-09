---
title: Consulta de la tabla de destinatarios
description: Obtenga información sobre cómo consultar la tabla de destinatarios
page-status-flag: never-activated
uuid: 0556d53e-0fdf-47b3-b1e0-b52e85e0c662
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: workflow
content-type: reference
topic-tags: use-cases
discoiquuid: 7e5605c8-78f2-4011-b317-96a59c699848
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: ab2c133aaa2f754e56fe8fdfc76d10526d4d1ce2

---


# Consulta de la tabla de destinatarios {#querying-recipient-table}

En este ejemplo, se desea recuperar los nombres y correos electrónicos de los destinatarios cuyo dominio de correo electrónico es “orange.co.uk” y que no viven en Londres.

* ¿Qué tabla se debe seleccionar?

   La tabla de destinatario (nms:recipient).

* Campos que se desea seleccionar como columnas de salida

   Correo electrónico, nombre, ciudad y número de cuenta

* ¿Cuáles son las condiciones de filtrado de los destinatarios?

   ciudad y dominio de correo electrónico

* ¿Se ha configurado una clasificación?

   Sí, según **[!UICONTROL Account number]** y **[!UICONTROL Last name]**

Para crear este ejemplo, aplique los pasos siguientes:

1. Click **[!UICONTROL Tools > Generic query editor...]** and choose the **Recipients** (**nms:recipient**) table. A continuación, haga clic en **[!UICONTROL Next]**.
1. Elija: **[!UICONTROL Last name]**, **[!UICONTROL First name]**, **[!UICONTROL Email]**, **[!UICONTROL City]** y **[!UICONTROL Account number]**. Estos campos se agregan a **[!UICONTROL Output columns]**. A continuación, haga clic en **[!UICONTROL Next]**.

   ![](assets/query_editor_03.png)

1. Ordene las columnas para mostrarlas en el orden correcto. Aquí se busca ordenar los números de cuenta en orden descendente y los nombres en orden alfabético. A continuación, haga clic en **[!UICONTROL Next]**.

   ![](assets/query_editor_04.png)

1. En la **[!UICONTROL Data filtering]** ventana, afine la búsqueda: elija **[!UICONTROL Filtering conditions]** y haga clic en **[!UICONTROL Next]**.
1. The **[!UICONTROL Target element]** window lets you enter the filter settings.

   Defina la siguiente condición de filtro: destinatarios con un dominio de correo electrónico igual a “orange.co.uk”. To do this, choose **Email domain (@email)** in the **[!UICONTROL Expression]** column, choose **equal to** in the **[!UICONTROL Operator]** column and enter &quot;orange.co.uk&quot; in the **[!UICONTROL Value]** column.

   ![](assets/query_editor_05.png)

1. If needed, click the **[!UICONTROL Distribution of values]** button to view a distribution based on the email domain of prospects. Hay un porcentaje disponible para cada dominio de correo electrónico de la base de datos. Los dominios que no sean “orange.co.uk” se muestran hasta que se aplique el filtro.

   En la parte inferior de la ventana se muestra un resumen de la consulta: Dominio **de correo electrónico igual a &#39;orange.co.uk&#39;**.

1. Click the **[!UICONTROL Preview]** to get an idea of the query result: only &quot;orange.co.uk&quot; email domains are displayed.

   ![](assets/query_editor_nveau_17.png)

1. Ahora, se cambia la consulta para encontrar contactos que no residen en Londres.

   Seleccione **[!UICONTROL City (location/@city)]** en la **[!UICONTROL Expression]** columna, **[!UICONTROL different from]** como operador e introduzca **[!UICONTROL London]** en la **[!UICONTROL Value]** columna.

   ![](assets/query_editor_08.png)

1. This will take you to the **[!UICONTROL Data formatting]** window. Compruebe el orden de las columnas. Desplace la columna “Ciudad” hacia arriba, debajo de la columna “Número de cuenta”.

   Anule la selección de la columna “Nombre” para quitarla de la lista.

   ![](assets/query_editor_nveau_15.png)

1. En la **[!UICONTROL Data preview]** ventana, haga clic en **[!UICONTROL Start the preview of the data]**. Esta función calcula el resultado de la consulta.

   The **[!UICONTROL Column results]** tab shows the query result in columns.

   El resultado muestra todos los destinatarios con un dominio de correo electrónico “orange.co.uk” que no residen en Londres. La columna “Nombre” no se muestra porque no se ha seleccionado durante la etapa anterior. Los números de cuenta se ordenan en orden descendente.

   ![](assets/query_editor_nveau_12.png)

   The **[!UICONTROL XML result]** tab shows the result in XML format.

   ![](assets/query_editor_nveau_13.png)

   The **[!UICONTROL Generated QSL queries]** tab shows the query result in SQL format.

   ![](assets/query_editor_nveau_14.png)
