---
title: Consulta de la tabla de destinatarios
description: Obtenga información sobre cómo consultar la tabla de destinatarios.
page-status-flag: never-activated
uuid: 0556d53e-0fdf-47b3-b1e0-b52e85e0c662
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: workflow
content-type: reference
topic-tags: use-cases
discoiquuid: 7e5605c8-78f2-4011-b317-96a59c699848
translation-type: tm+mt
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: tm+mt
source-wordcount: '392'
ht-degree: 79%

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

   Yes, based on **[!UICONTROL Account number]** and **[!UICONTROL Last name]**

Para crear este ejemplo, aplique los pasos siguientes:

1. Click **[!UICONTROL Tools > Generic query editor...]** and choose the **Recipients** (**nms:recipient**) table. A continuación, haga clic en **[!UICONTROL Next]**.
1. Elija: **[!UICONTROL Last name]**, **[!UICONTROL First name]**, **[!UICONTROL Email]**, **[!UICONTROL City]** y **[!UICONTROL Account number]**. These fields are added to **[!UICONTROL Output columns]**. A continuación, haga clic en **[!UICONTROL Next]**.

   ![](assets/query_editor_03.png)

1. Ordene las columnas para mostrarlas en el orden correcto. Aquí se busca ordenar los números de cuenta en orden descendente y los nombres en orden alfabético. A continuación, haga clic en **[!UICONTROL Next]**.

   ![](assets/query_editor_04.png)

1. In the **[!UICONTROL Data filtering]** window, refine your search: choose **[!UICONTROL Filtering conditions]** and click **[!UICONTROL Next]**.
1. The **[!UICONTROL Target element]** window lets you enter the filter settings.

   Defina la siguiente condición de filtro: destinatarios con un dominio de correo electrónico igual a “orange.co.uk”. Para ello, elija **Email domain (@email)** en la columna **[!UICONTROL Expression]**, elija **equal to** en la columna **[!UICONTROL Operator]** y escriba “orange.co.uk” en la columna **[!UICONTROL Value]**.

   ![](assets/query_editor_05.png)

1. Si es necesario, haga clic en el botón **[!UICONTROL Distribution of values]** para ver una distribución en función del dominio de correo electrónico de los posibles clientes. Hay un porcentaje disponible para cada dominio de correo electrónico de la base de datos. Los dominios que no sean “orange.co.uk” se muestran hasta que se aplique el filtro.

   En la parte inferior de la ventana se muestra un resumen de la consulta: **Email domain equal to “orange.co.uk”**.

1. Haga clic en **[!UICONTROL Preview]** para obtener una idea del resultado de la consulta: solo se muestran los dominios de correo electrónico “orange.co.uk”.

   ![](assets/query_editor_nveau_17.png)

1. Ahora, se cambia la consulta para encontrar contactos que no residen en Londres.

   Select **[!UICONTROL City (location/@city)]** in the **[!UICONTROL Expression]** column, **[!UICONTROL different from]** as an operator and enter **[!UICONTROL London]** in the **[!UICONTROL Value]** column.

   ![](assets/query_editor_08.png)

1. This will take you to the **[!UICONTROL Data formatting]** window. Compruebe el orden de las columnas. Desplace la columna “Ciudad” hacia arriba, debajo de la columna “Número de cuenta”.

   Anule la selección de la columna “Nombre” para quitarla de la lista.

   ![](assets/query_editor_nveau_15.png)

1. En la ventana **[!UICONTROL Data preview]**, haga clic en **[!UICONTROL Start the preview of the data]**. Esta función calcula el resultado de la consulta.

   The **[!UICONTROL Column results]** tab shows the query result in columns.

   El resultado muestra todos los destinatarios con un dominio de correo electrónico “orange.co.uk” que no residen en Londres. La columna “Nombre” no se muestra porque no se ha seleccionado durante la etapa anterior. Los números de cuenta se ordenan en orden descendente.

   ![](assets/query_editor_nveau_12.png)

   The **[!UICONTROL XML result]** tab shows the result in XML format.

   ![](assets/query_editor_nveau_13.png)

   The **[!UICONTROL Generated QSL queries]** tab shows the query result in SQL format.

   ![](assets/query_editor_nveau_14.png)
