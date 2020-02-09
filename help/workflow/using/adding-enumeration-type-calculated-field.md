---
title: Adición de un campo calculado de tipo de enumeración
description: Aprenda a agregar un campo calculado de tipo Enumeración
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


# Adición de un campo calculado de tipo de enumeración {#adding-an-enumeration-type-calculated-field}

Here we want to create a query with an **[!UICONTROL Enumerations]** type calculated field. Este campo genera una columna adicional en la ventana de vista previa de datos. Esta columna especifica los valores numéricos devueltos como resultado de cada destinatario (0, 1 y 2). Se asignará un sexo a cada valor de la nueva columna: &quot;Hombre&quot; para &quot;1&quot;, &quot;Mujer&quot; para &quot;2&quot; o &quot;No indicado&quot; si el valor es igual a &quot;0&quot;.

* ¿Qué tabla se debe seleccionar?

   La tabla de destinatario (nms:recipient).

* ¿Campos que se desea seleccionar en la columna de salida?

   Apellidos, Nombre, Sexo

* ¿Con qué criterios se va a filtrar la información?

   El lenguaje del destinatario.

Siga estos pasos:

1. Open the Generic query editor and select the Recipient table (**[!UICONTROL nms:recipient]**).
1. En la **[!UICONTROL Data to extract]** ventana, seleccione **[!UICONTROL Last name]**, **[!UICONTROL First name]** y **[!UICONTROL Gender]**.

   ![](assets/query_editor_nveau_73.png)

1. In the **[!UICONTROL Sorting]** window, click **[!UICONTROL Next]**: no sort is necessary for this example.
1. En **[!UICONTROL Data filtering]**, seleccione **[!UICONTROL Filtering conditions]**.
1. In the **[!UICONTROL Target element]** window, set a filter condition to collect recipients who speak English.

   ![](assets/query_editor_nveau_74.png)

1. En la **[!UICONTROL Data formatting]** ventana, haga clic en **[!UICONTROL Add a calculated field]**.

   ![](assets/query_editor_nveau_75.png)

1. Vaya a la **[!UICONTROL Type]** ventana de la **[!UICONTROL Export calculated field definition]** ventana y seleccione **[!UICONTROL Enumerations]**.

   Defina la columna a la que debe hacer referencia el nuevo campo calculado. To do this, select the **[!UICONTROL Gender]** column in the drop-down menu of the **[!UICONTROL Source column]** field: the destination values will coincide with the **[!UICONTROL Gender]** column.

   ![](assets/query_editor_nveau_76.png)

   Defina los valores de **Origen** y **Destino**: el valor de destino facilita la lectura del resultado de la consulta. Esta consulta debe devolver el sexo del destinatario y el resultado será 0, 1 o 2.

   Para cada línea de &quot;origen-destino&quot; que se va a introducir, haga clic **[!UICONTROL Add]** en la **[!UICONTROL List of enumeration values]**:

   * In the **[!UICONTROL Source]** column, enter the source value for each gender (0,1,2) in a new line.
   * En la **[!UICONTROL Destination]** columna, introduzca los valores: &quot;No indicado&quot; para la línea &quot;0&quot;, &quot;Hombre&quot; para la línea &quot;1&quot; y &quot;Mujer&quot; para la línea &quot;2&quot;.
   Seleccione la **[!UICONTROL Keep the source value]** función.

   Click **[!UICONTROL OK]** to approve the calculated field.

   ![](assets/query_editor_nveau_77.png)

1. En la **[!UICONTROL Data formatting]** ventana, haga clic en **[!UICONTROL Next]**.
1. En la ventana de vista previa, **[!UICONTROL start the preview of the data]**.

   La columna adicional define el género de 0, 1 y 2:

   * 0 para “No indicado”,
   * 1 para “Masculino”,
   * 2 para “Femenino”.
   ![](assets/query_editor_nveau_78.png)

   Por ejemplo, si no introduce el sexo &quot;2&quot; en la **[!UICONTROL List of enumeration values]**, y la **[!UICONTROL Generate a warning and continue]** función del **[!UICONTROL In other cases]** campo está seleccionada, obtendrá un registro de advertencia. Este registro indica que no se ha introducido el género “2” (Femenino). It is displayed in the **[!UICONTROL Logs generated during export]** field of the data preview window.

   ![](assets/query_editor_nveau_79.png)

   Tomemos otro ejemplo y digamos que el valor de la enumeración “2” no se ingresó. Seleccione la **[!UICONTROL Generate an error and reject the line]** función: todos los destinatarios de &quot;2&quot; de sexo generarán anomalías y la otra información de la línea (nombre y apellidos, etc.) no se exportará. An error log is displayed in the **[!UICONTROL Logs generated during export]** field of the data preview window. Este registro indica que no se ha introducido el valor de enumeración “2”.

   ![](assets/query_editor_nveau_80.png)
