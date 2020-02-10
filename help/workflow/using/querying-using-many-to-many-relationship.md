---
title: Realización de consultas con una relación de varios a varios
description: Aprenda a realizar consultas mediante una relación de varios a varios
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
source-git-commit: cf7c90f0ea9fbce3a4fd53f24189617cbd33fc40

---


# Realización de consultas con una relación de varios a varios {#querying-using-a-many-to-many-relationship}

En este ejemplo, se desea recuperar los destinatarios no contactados durante los últimos 7 días. Esta consulta se refiere a todos los envíos.

En este ejemplo también muestra el modo de configurar un filtro relacionado con la selección de un elemento de recopilación (o nodo naranja). Los elementos de la colección están disponibles en la **[!UICONTROL Field to select]** ventana.

* ¿Qué tabla se debe seleccionar?

   La tabla de destinatario (**nms:recipient**).

* Campos que se desea seleccionar para la columna de salida.

   Clave principal, Apellido, Nombre y Correo electrónico.

* ¿En función de qué criterios se filtra la información?

   En función de los registros de entrega de los destinatarios que van desde los 7 días anteriores a la fecha actual.

Siga estos pasos:

1. Open the Generic query editor and select the Recipient table **[!UICONTROL (nms:recipient)]**.
1. En la **[!UICONTROL Data to extract]** ventana, seleccione **[!UICONTROL Primary key]**, **[!UICONTROL First name]** y **[!UICONTROL Last name]****[!UICONTROL Email]**.

   ![](assets/query_editor_nveau_33.png)

1. En la ventana de ordenación, ordene los nombres alfabéticamente.

   ![](assets/query_editor_nveau_34.png)

1. En la **[!UICONTROL Data filtering]** ventana, seleccione **[!UICONTROL Filtering conditions]**.
1. In the **[!UICONTROL Target element]** window, the filtering condition for extracting profiles with no tracking log for the last 7 days involves two steps. El elemento que se debe seleccionar es un enlace de varios a varios.

   * Comience seleccionando el elemento de **[!UICONTROL Recipient delivery logs (broadlog)]** colección (nodo naranja) para la primera **[!UICONTROL Value]** columna.

      ![](assets/query_editor_nveau_67.png)

      Seleccione el **[!UICONTROL do not exist as]** operador. No es necesario seleccionar un segundo valor en esta línea.

   * El contenido de la segunda condición de filtrado depende de la primera. Here, the **[!UICONTROL Event date]** field is offered directly in the **[!UICONTROL Recipient delivery logs]** table since there is a link to this table.

      ![](assets/query_editor_nveau_36.png)

      Se selecciona **[!UICONTROL Event date]** con el **[!UICONTROL greater than or equal to]** operador. Seleccione el **[!UICONTROL DaysAgo (7)]** valor. Para ello, haga clic **[!UICONTROL Edit expression]** en el **[!UICONTROL Value]** campo. En la **[!UICONTROL Formula type]** ventana, seleccione **[!UICONTROL Process on dates]** y **[!UICONTROL Current date minus n days]**, dando &quot;7&quot; como valor.

      ![](assets/query_editor_nveau_37.png)

      Se ha configurado la condición de filtro.

      ![](assets/query_editor_nveau_38.png)

1. In the **[!UICONTROL Data formatting]** window, switch the last names to upper-case. Haga clic en la **[!UICONTROL Last name]** línea de la **[!UICONTROL Transformation]** columna y selecciónela **[!UICONTROL Switch to upper case]** en el menú desplegable.

   ![](assets/query_editor_nveau_39.png)

1. Use the **[!UICONTROL Add a calculated field]** function to insert a column into the data preview window.

   En este ejemplo, agregue un campo calculado con los nombres y apellidos de los destinatarios en una sola columna. Haga clic en la **[!UICONTROL Add a calculated field]** función. En la **[!UICONTROL Export calculated field definition]** ventana, introduzca una etiqueta y un nombre interno y elija el **[!UICONTROL JavaScript Expression]** tipo. A continuación, introduzca la siguiente expresión:

   ```
   var rep = source._firstName+" - "+source._lastName
   return rep
   ```

   ![](assets/query_editor_nveau_40.png)

   Haga clic **[!UICONTROL OK]**. Se ha configurado la **[!UICONTROL Data formatting]** ventana.

   Para obtener más información sobre la adición de campos calculados, consulte esta sección.

1. The result is shown in the **[!UICONTROL Data preview]** window. Los destinatarios que no hayan sido contactados en los últimos 7 días se muestran en orden alfabético. Los nombres se muestran en mayúsculas y se ha creado la columna con el nombre y los apellidos.

   ![](assets/query_editor_nveau_41.png)
