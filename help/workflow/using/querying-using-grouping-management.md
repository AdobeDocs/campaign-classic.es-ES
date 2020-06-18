---
title: Realización de consultas mediante la administración de agrupación
description: Obtenga información sobre cómo realizar consultas mediante la administración de grupos
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
source-git-commit: f99e3a4f69cb2b0122f2f6957d419d6b95ad54b1
workflow-type: tm+mt
source-wordcount: '251'
ht-degree: 64%

---


# Realización de consultas mediante la administración de agrupación {#querying-using-grouping-management}

En este ejemplo, se desea ejecutar una consulta para buscar todos los dominios de correo electrónico que han sido objetivos más de 30 veces durante las entregas anteriores.

* ¿Qué tabla se debe seleccionar?

   La tabla de destinatario (nms:recipient).

* ¿Campos que se van a seleccionar en las columnas de salida?

   Dominio de correo electrónico y clave principal (con recuento).

* ¿Agrupación de datos?

   En función del dominio de correo electrónico con un recuento de claves principales por encima de 30. This operation is carried out with the **[!UICONTROL Group by + Having]** option. **[!UICONTROL Group by + Having]** permite agrupar los datos (“Group by”) y realizar una selección de lo que se ha agrupado (“Having”).

Para crear este ejemplo, aplique los pasos siguientes:

1. Open the **[!UICONTROL Generic query editor]** and choose the Recipient table (**nms:recipient**).

   ![](assets/query_editor_02.png)

1. En la **[!UICONTROL Data to extract]** ventana, seleccione los campos **[!UICONTROL Email domain]** y **[!UICONTROL Primary key]** . Run a count on the **[!UICONTROL Primary key]** field.

   Para obtener más información sobre el recuento de claves principales, consulte [esta sección](../../platform/using/defining-filter-conditions.md#building-expressions).

1. Marque la casilla **[!UICONTROL Handle groupings (GROUP BY + HAVING)]**.

   ![](assets/query_editor_nveau_29.png)

1. En la ventana **[!UICONTROL Sorting]**, ordene los dominios de correo electrónico en orden descendente. To do this, check **[!UICONTROL Yes]** in the **[!UICONTROL Descending sort]** column. Haga clic **[!UICONTROL Next]**.

   ![](assets/query_editor_nveau_70.png)

1. En **[!UICONTROL Data filtering]**, seleccione **[!UICONTROL Filtering conditions]**. Go to the **[!UICONTROL Target elements]** window and click **[!UICONTROL Next]**.
1. En la **[!UICONTROL Data grouping]** ventana, seleccione la opción **[!UICONTROL Email domain]** haciendo clic en **[!UICONTROL Add]**.

   This data grouping window is only displayed if the **[!UICONTROL Handle groupings (GROUP BY + HAVING]**) box was checked.

   ![](assets/query_editor_blocklist_04.png)

1. En la ventana **[!UICONTROL Grouping condition]**, indique un recuento de clave principal mayor que 30, ya que solo se desea que los dominios de correo electrónico que han sido objetivos más de 30 veces sean devueltos como resultados.

   This window appears when the **[!UICONTROL Manage groupings (GROUP BY + HAVING)]** box was checked: this is where the grouping result is filtered (HAVING).

   ![](assets/query_editor_blocklist_05.png)

1. In the **[!UICONTROL Data formatting]** window, click **[!UICONTROL Next]**: no formatting is necessary here.
1. En la ventana de vista previa de datos, haga clic en **[!UICONTROL Launch data preview]**: aquí se devuelven tres dominios de correo electrónico que han sido objetivos más de 30 veces.

   ![](assets/query_editor_blocklist_06.png)
