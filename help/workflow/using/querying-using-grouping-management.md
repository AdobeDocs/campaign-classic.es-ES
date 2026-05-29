---
product: campaign
title: Consultas mediante la administración de agrupación
description: Obtenga información sobre cómo realizar consultas mediante la administración de agrupación
feature: Query Editor, Workflows
hide: true
exl-id: 23bccb48-60ab-46c9-be26-2fa35243d61e
TQID: https://experienceleague.adobe.com/jQoIc-ceJgiBqFrlPgDR1nm7PpcqLJedI36hnBQHrl0
product_v2: id: dfc56824-e8b9-499e-85d4-21aedb507314
feature_v2: []
subfeature_v2: id: ee25c34b-ea50-427b-9369-ba0a160f7d70id: b5f0aaf4-1e48-400d-95ac-6eb3078cf22fid: d1110311-2ca4-442b-be37-088a6db845ee
source-git-commit: 38eab6b8da73163e4476e91c0ef73f25c3f57546
workflow-type: tm+mt
source-wordcount: 254
ht-degree: 100%

---

# Realización de consultas mediante la administración de agrupación {#querying-using-grouping-management}



En este ejemplo, se desea ejecutar una consulta para buscar todos los dominios de correo electrónico que han sido objetivos más de 30 veces durante las entregas anteriores.

* ¿Qué tabla se debe seleccionar?

  La tabla del destinatario (nms:recipient)

* ¿Campos que se van a seleccionar en las columnas de salida?

  Dominio de correo electrónico y clave principal (con recuento).

* ¿Agrupación de datos?

  En función del dominio de correo electrónico con un recuento de claves principales por encima de 30. Esta operación se lleva a cabo con la opción **[!UICONTROL Group by + Having]**. **[!UICONTROL Group by + Having]** permite agrupar los datos (“Group by”) y realizar una selección de lo que se ha agrupado (“Having”).

Para crear este ejemplo, aplique los pasos siguientes:

1. Abra el **[!UICONTROL Generic query editor]** y seleccione la tabla de destinatarios (**nms:recipient**).

   ![](assets/query_editor_02.png)

1. En la ventana **[!UICONTROL Data to extract]**, seleccione los campos **[!UICONTROL Email domain]** y **[!UICONTROL Primary key]**. Ejecute un recuento en el campo **[!UICONTROL Primary key]**.

   Para obtener más información sobre el recuento de claves principales, consulte [esta sección](../../platform/using/adobe-campaign-workspace.md#about-queries-in-campaign).

1. Marque la casilla **[!UICONTROL Handle groupings (GROUP BY + HAVING)]**.

   ![](assets/query_editor_nveau_29.png)

1. En la ventana **[!UICONTROL Sorting]**, ordene los dominios de correo electrónico en orden descendente. Para ello, seleccione **[!UICONTROL Yes]** en la columna **[!UICONTROL Descending sort]**. Haga clic en **[!UICONTROL Next]**.

   ![](assets/query_editor_nveau_70.png)

1. En **[!UICONTROL Data filtering]**, seleccione **[!UICONTROL Filtering conditions]**. Vaya a la ventana **[!UICONTROL Target elements]** y haga clic en **[!UICONTROL Next]**.
1. En la ventana **[!UICONTROL Data grouping]**, seleccione la opción **[!UICONTROL Email domain]** haciendo clic en **[!UICONTROL Add]**.

   Esta ventana de agrupación de datos solo se muestra si se ha marcado la casilla **[!UICONTROL Handle groupings (GROUP BY + HAVING])**.

   ![](assets/query_editor_blocklist_04.png)

1. En la ventana **[!UICONTROL Grouping condition]**, indique un recuento de clave principal mayor que 30, ya que solo se desea que los dominios de correo electrónico que han sido objetivos más de 30 veces sean devueltos como resultados.

   Esta ventana aparece cuando se ha marcado la casilla **[!UICONTROL Manage groupings (GROUP BY + HAVING)]**: aquí es donde se filtra el resultado de la agrupación (HAVING).

   ![](assets/query_editor_blocklist_05.png)

1. En la ventana **[!UICONTROL Data formatting]**, haga clic en **[!UICONTROL Next]**: aquí no es necesario ningún formato.
1. En la ventana de vista previa de datos, haga clic en **[!UICONTROL Launch data preview]**: aquí se devuelven tres dominios de correo electrónico que han sido objetivos más de 30 veces.

   ![](assets/query_editor_blocklist_06.png)
