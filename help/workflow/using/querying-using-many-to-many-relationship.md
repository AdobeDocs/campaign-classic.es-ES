---
title: Realización de consultas con una relación de varios a varios
description: Aprenda a hacer consultas mediante una relación de varios a varios
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
source-wordcount: '385'
ht-degree: 68%

---


# Realización de consultas con una relación de varios a varios {#querying-using-a-many-to-many-relationship}

En este ejemplo, se desea recuperar los destinatarios no contactados durante los últimos 7 días. Esta consulta se refiere a todas las entregas.

En este ejemplo también muestra el modo de configurar un filtro relacionado con la selección de un elemento de recopilación (o nodo naranja). Collection elements are available in the **[!UICONTROL Field to select]** window.

* ¿Qué tabla se debe seleccionar?

   La tabla de destinatario (**nms:recipient**).

* Campos que se desea seleccionar para la columna de salida.

   Clave principal, Apellido, Nombre y Correo electrónico.

* ¿En función de qué criterios se filtra la información?

   En función de los registros de entrega de los destinatarios que van desde los 7 días anteriores a la fecha actual.

Siga estos pasos:

1. Abra el Editor de consultas genérico y seleccione la tabla de destinatarios **[!UICONTROL (nms:recipient)]**.
1. In the **[!UICONTROL Data to extract]** window, select **[!UICONTROL Primary key]**, **[!UICONTROL First name]**, **[!UICONTROL Last name]** and **[!UICONTROL Email]**.

   ![](assets/query_editor_nveau_33.png)

1. En la ventana de ordenación, ordene los nombres alfabéticamente.

   ![](assets/query_editor_nveau_34.png)

1. In the **[!UICONTROL Data filtering]** window, select **[!UICONTROL Filtering conditions]**.
1. En la ventana **[!UICONTROL Target element]**, la condición de filtrado para extraer perfiles sin registro de seguimiento para los últimos 7 días implica dos pasos. El elemento que se debe seleccionar es un vínculo de varios a varios.

   * Start by selecting the **[!UICONTROL Recipient delivery logs (broadlog)]** collection element (orange node) for the first **[!UICONTROL Value]** column.

      ![](assets/query_editor_nveau_67.png)

      Seleccione el **[!UICONTROL do not exist as]** operador. No es necesario seleccionar un segundo valor en esta línea.

   * El contenido de la segunda condición de filtrado depende de la primera. Here, the **[!UICONTROL Event date]** field is offered directly in the **[!UICONTROL Recipient delivery logs]** table since there is a link to this table.

      ![](assets/query_editor_nveau_36.png)

      Se selecciona **[!UICONTROL Event date]** con el **[!UICONTROL greater than or equal to]** operador. Select the **[!UICONTROL DaysAgo (7)]** value. To do this, click **[!UICONTROL Edit expression]** in the **[!UICONTROL Value]** field. En la **[!UICONTROL Formula type]** ventana, seleccione **[!UICONTROL Process on dates]** y **[!UICONTROL Current date minus n days]**, dando &quot;7&quot; como valor.

      ![](assets/query_editor_nveau_37.png)

      Se ha configurado la condición de filtro.

      ![](assets/query_editor_nveau_38.png)

1. En la ventana **[!UICONTROL Data formatting]**, cambie los apellidos a mayúscula. Click the **[!UICONTROL Last name]** line in the **[!UICONTROL Transformation]** column and select **[!UICONTROL Switch to upper case]** in the drop-down menu.

   ![](assets/query_editor_nveau_39.png)

1. Use the **[!UICONTROL Add a calculated field]** function to insert a column into the data preview window.

   En este ejemplo, agregue un campo calculado con los nombres y apellidos de los destinatarios en una sola columna. Haga clic en la **[!UICONTROL Add a calculated field]** función. In the **[!UICONTROL Export calculated field definition]** window, enter a label and an internal name and choose the **[!UICONTROL JavaScript Expression]** type. A continuación, introduzca la siguiente expresión:

   ```
   var rep = source._firstName+" - "+source._lastName
   return rep
   ```

   ![](assets/query_editor_nveau_40.png)

   Haga clic en **[!UICONTROL OK]**. The **[!UICONTROL Data formatting]** window is configured.

   Para obtener más información sobre la adición de campos calculados, consulte esta sección.

1. The result is shown in the **[!UICONTROL Data preview]** window. Los destinatarios que no hayan sido contactados en los últimos 7 días se muestran en orden alfabético. Los nombres se muestran en mayúsculas y se ha creado la columna con el nombre y los apellidos.

   ![](assets/query_editor_nveau_41.png)
