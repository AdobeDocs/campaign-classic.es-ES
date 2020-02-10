---
title: Uso de agregados
seo-title: Uso de agregados
description: Uso de agregados
seo-description: null
page-status-flag: never-activated
uuid: 70556745-56b2-4f22-bbc5-7f8106fb0d4a
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: workflow
content-type: reference
topic-tags: use-cases
discoiquuid: 9ca649b4-2226-4cfe-bae1-4632c421975b
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: c10a0a11c6e9952aa47da1f7a15188c79c62508d

---


# Uso de agregados{#using-aggregates}

Este caso de uso detalla cómo identificar automáticamente los últimos destinatarios agregados a la base de datos.

Con el proceso siguiente, la fecha de creación de los destinatarios de la base de datos se compara con la última fecha conocida en la que se creó un destinatario con un agregado. Asimismo, se seleccionan todos los destinatarios creados en el mismo día.

Para realizar un filtro **Creation date = max (Creation date)** en los destinatarios, se debe ejecutar un flujo de trabajo para seguir estos pasos:

1. Recupere los destinatarios de la base de datos utilizando una consulta básica. Para obtener más información sobre este paso, consulte [Creación de una consulta](../../workflow/using/query.md#creating-a-query).
1. Calcule la última fecha conocida en que se creó un destinatario con el resultado generado a partir de la función de agregación **max (Creation date)** .
1. Enlace cada destinatario al resultado de la función de agregación en el mismo esquema.
1. Filtre los destinatarios con el agregado a través del esquema editado.

![](assets/datamanagement_usecase_1.png)

## Step 1: Calculating the aggregate result {#step-1--calculating-the-aggregate-result}

1. Cree una consulta. En este caso, el objetivo es calcular la última fecha de creación conocida de todos los destinatarios de la base de datos. Por lo tanto, la consulta no contiene ningún filtro.
1. Select **[!UICONTROL Add data]**.
1. En las ventanas que se abren, seleccione **[!UICONTROL Data linked to the filtering dimension]** y luego **[!UICONTROL Filtering dimension data]**.
1. In the **[!UICONTROL Data to add]** window, add a column that calculates the maximum value for the **Creation date** field in the table of recipients. You can use the expression editor or enter **max(@created)** directly into a field in the **[!UICONTROL Expression]** column. Then click the **[!UICONTROL Finish]** button.

   ![](assets/datamanagement_usecase_2.png)

1. Haga clic en **[!UICONTROL Edit additional data]** luego **[!UICONTROL Advanced parameters...]**. Marque la **[!UICONTROL Disable automatic adding of the primary keys of the targeting dimension]** opción.

   Esta opción garantiza que todos los destinatarios no se muestren como resultado y que los datos agregados explícitamente no se mantengan. En este caso, hace referencia a la última fecha de creación de un destinatario.

   Deje la **[!UICONTROL Remove duplicate rows (DISTINCT)]** opción activada.

## Step 2: Linking the recipients and the aggregation function result {#step-2--linking-the-recipients-and-the-aggregation-function-result}

Para vincular la consulta de los destinatarios a la consulta que lleva a cabo el cálculo de la función de agregación, se debe utilizar una actividad de edición de esquema.

1. Defina la consulta para los destinatarios como un conjunto principal.
1. In the **[!UICONTROL Links]** tab, add a new link and enter the information in the window that opens as follows:

   * Seleccione el esquema temporal relacionado con el agregado. Los datos de este esquema se agregan a los miembros del conjunto principal.
   * Select **[!UICONTROL Use a simple join]** to link the aggregate result to every recipient of the main set.
   * Finalmente, especifique que el vínculo es un **[!UICONTROL Type 11 simple link]**.
   ![](assets/datamanagement_usecase_3.png)

Así, el resultado de la agregación se vincula a todos los destinatarios.

## Step 3: Filtering recipients using the aggregate. {#step-3--filtering-recipients-using-the-aggregate-}

Una vez establecido el enlace, el resultado del agregado y los destinatarios forman parte del mismo esquema temporal. Por lo tanto, es posible crear un filtro en el esquema para comparar la fecha de creación de los destinatarios y la última fecha de creación conocida, representada mediante la función de agregación. Este filtro se lleva a cabo mediante una actividad de división.

1. In the **[!UICONTROL General]** tab, select **Recipients** as the targeting dimension and **Edit schema** as the filtering dimension (to filter on the inbound transition schema activity).
1. En la **[!UICONTROL subsets]** ficha, seleccione **[!UICONTROL Add a filtering condition on the inbound population]** y haga clic en **[!UICONTROL Edit...]**.
1. Mediante el editor de expresiones, agregue un criterio de igualdad entre la fecha de creación de los destinatarios y la fecha de creación calculada mediante el agregado.

   Los campos de fecha de la base de datos suelen guardarse en milisegundos. Por lo tanto, se deben ampliar para todo el día a fin de evitar recuperar destinatarios creados solo en ese mismo milisegundo.

   Para ello, utilice la función **ToDate**, disponible en el editor de expresiones, que convierte fechas y horas en fechas simples.

   Por lo tanto, las expresiones que se utilizan en los criterios son:

   * **[!UICONTROL Expression]**: `toDate([target/@created])`.
   * **[!UICONTROL Value]**:: `toDate([datemax/expr####])`, donde expr#### se relaciona con el agregado especificado en la consulta de la función de agregación.
   ![](assets/datamanagement_usecase_4.png)

De ese modo, el resultado de la actividad de división se relaciona con los destinatarios creados el mismo día que la última fecha de creación conocida.

A continuación, se puede agregar otras actividades como una actualización de lista o un envío para enriquecer el flujo de trabajo.
