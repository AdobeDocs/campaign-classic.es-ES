---
title: Adición de un campo calculado de tipo de lista desglosada
description: Aprenda cómo añadir un Campo calculado de tipo de enumeración.
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
source-wordcount: '412'
ht-degree: 75%

---


# Adición de un campo calculado de tipo de lista desglosada {#adding-an-enumeration-type-calculated-field}

Aquí se desea crear una consulta con un campo calculado de tipo **[!UICONTROL Enumerations]**. Este campo genera una columna adicional en la ventana de vista previa de datos. Esta columna especifica los valores numéricos devueltos como resultado de cada destinatario (0, 1 y 2). Se asigna un sexo a cada valor de la nueva columna: “Hombre” para “1”, “Mujer” para “2” o “No indicado” si el valor es igual a “0”.

* ¿Qué tabla se debe seleccionar?

   La tabla de destinatario (nms:recipient).

* ¿Campos que se desea seleccionar en la columna de salida?

   Apellidos, Nombre, Sexo

* ¿Con qué criterios se va a filtrar la información?

   El lenguaje del destinatario.

Siga estos pasos:

1. Abra el Editor de consultas genérico y seleccione la tabla de destinatarios (**[!UICONTROL nms:recipient]**).
1. In the **[!UICONTROL Data to extract]** window, select **[!UICONTROL Last name]**, **[!UICONTROL First name]** and **[!UICONTROL Gender]**.

   ![](assets/query_editor_nveau_73.png)

1. En la ventana **[!UICONTROL Sorting]**, haga clic en **[!UICONTROL Next]**: en este ejemplo, no es necesario ordenar.
1. En **[!UICONTROL Data filtering]**, seleccione **[!UICONTROL Filtering conditions]**.
1. En la ventana **[!UICONTROL Target element]**, defina una condición de filtro para recopilar los destinatarios que hablan en inglés.

   ![](assets/query_editor_nveau_74.png)

1. En la ventana **[!UICONTROL Data formatting]**, haga clic en **[!UICONTROL Add a calculated field]**.

   ![](assets/query_editor_nveau_75.png)

1. Go to the **[!UICONTROL Type]** window of the **[!UICONTROL Export calculated field definition]** window and select **[!UICONTROL Enumerations]**.

   Defina la columna a la que debe hacer referencia el nuevo campo calculado. Para ello, en el menú desplegable **[!UICONTROL Gender]**, seleccione **[!UICONTROL Source column]** en la columna: los valores de destino coinciden con la columna **[!UICONTROL Gender]**.

   ![](assets/query_editor_nveau_76.png)

   Defina los valores de **Origen** y **Destino**: el valor de destino facilita la lectura del resultado de la consulta. Esta consulta debe devolver el sexo del destinatario y el resultado será 0, 1 o 2.

   For each &quot;source-destination&quot; line to be entered, click **[!UICONTROL Add]** in the **[!UICONTROL List of enumeration values]**:

   * En la columna **[!UICONTROL Source]**, introduzca el valor de origen de cada sexo (0, 1, 2) en una nueva línea.
   * En la columna **[!UICONTROL Destination]**, introduzca los valores: “No indicado” para la línea “0”, “Hombre” para la línea “1” y “Mujer” para la línea “2”.

   Seleccione la **[!UICONTROL Keep the source value]** función.

   Haga clic en **[!UICONTROL OK]** para aprobar el campo calculado.

   ![](assets/query_editor_nveau_77.png)

1. En la ventana **[!UICONTROL Data formatting]**, haga clic en **[!UICONTROL Next]**.
1. En la ventana previsualización, **[!UICONTROL start the preview of the data]**.

   La columna adicional define el género de 0, 1 y 2:

   * 0 para “No indicado”,
   * 1 para “Masculino”,
   * 2 para “Femenino”.

   ![](assets/query_editor_nveau_78.png)

   For example, if you don&#39;t enter gender &quot;2&quot; in the **[!UICONTROL List of enumeration values]**, and the **[!UICONTROL Generate a warning and continue]** function of the **[!UICONTROL In other cases]** field is selected, you will get a warning log. Este registro indica que no se ha introducido el género “2” (Femenino). It is displayed in the **[!UICONTROL Logs generated during export]** field of the data preview window.

   ![](assets/query_editor_nveau_79.png)

   Tomemos otro ejemplo y digamos que el valor de la enumeración “2” no se ingresó. Select the **[!UICONTROL Generate an error and reject the line]** function: all gender &quot;2&quot; recipients will raise anomalies and the other information in the line (first and last name, etc.) no se exporta. An error log is displayed in the **[!UICONTROL Logs generated during export]** field of the data preview window. Este registro indica que no se ha introducido el valor de enumeración “2”.

   ![](assets/query_editor_nveau_80.png)
