---
title: Creación de hipótesis
seo-title: Creación de hipótesis
description: Creación de hipótesis
seo-description: null
page-status-flag: never-activated
uuid: 48b74772-473f-4fbc-a228-ce8e35a7b9ba
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: campaign
content-type: reference
topic-tags: response-manager
discoiquuid: 0f73de0e-e589-4e39-9895-209dad75db75
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 1c86322fa95aee024f6c691b61a10c21a9a22eb7

---


# Creación de hipótesis{#creating-hypotheses}

Existen varias formas para crear y vincular hipótesis a una oferta o envío de campaña:

* Via the **[!UICONTROL Measurement hypotheses]** folder by creating a new hypothesis based on an existing template and linking it to an existing delivery.
* A través de la **[!UICONTROL Edit]** ficha > **[!UICONTROL Measurement]** de una campaña.
* Via the **[!UICONTROL Measurement]** option of a delivery created from a campaign.

Las hipótesis solo se pueden calcular una vez que se haya iniciado la campaña de marketing y los destinatarios hayan recibido el envío. Si la hipótesis se basa en una propuesta de oferta, la última debe estar presente y permanecer activa. Offer and delivery hypotheses are created via the **[!UICONTROL Measurement hypotheses]** folder and are based on a hypothesis template. Sin embargo, es posible hacer referencia a una hipótesis directamente en el envío o la campaña antes de que comience la campaña. In this case, the hypotheses will be calculated automatically once the marketing campaign is launched, based on execution settings (for more on this, refer to [Hypothesis template execution settings](../../campaign/using/hypothesis-templates.md#hypothesis-template-execution-settings)).

## Creación de una hipótesis sobre la marcha {#creating-a-hypothesis-on-the-fly-on-a-delivery}

Para crear una hipótesis en un envío existente, aplique el siguiente proceso:

>[!NOTE]
>
>Esta operación solo es posible para envíos pendientes.

1. En el árbol de Adobe Campaign, vaya a **[!UICONTROL Campaign management > Measurement hypotheses]**.
1. Click the **[!UICONTROL New]** button or right-click on the list of hypotheses and select **[!UICONTROL New]** in the drop-down list.

   ![](assets/response_hypothesis_instance_creation_002.png)

1. In the hypothesis window, select a previously created template (refer to [Hypothesis templates](../../campaign/using/hypothesis-templates.md)).

   ![](assets/response_hypothesis_instance_creation_003.png)

   El contexto de hipótesis tal como se definió en el modelo seleccionado se muestra en la ventana.

   >[!NOTE]
   >
   >Los ajustes definidos en la plantilla y no visibles en este paso se mantendrán también en la memoria y se vuelven a asignar a la hipótesis en curso.

   ![](assets/response_hypothesis_instance_creation_004.png)

1. Seleccione el envío para la que desea crear una hipótesis.

   ![](assets/response_hypothesis_instance_creation_005.png)

1. Puede personalizar su hipótesis editando las fichas **[!UICONTROL General]**, **[!UICONTROL Transactions]** y **[!UICONTROL Scope]** . Para obtener más información sobre esto, consulte [Creación de un modelo](../../campaign/using/hypothesis-templates.md#creating-a-hypothesis-model)de hipótesis.
1. Start the hypothesis by clicking **[!UICONTROL Start]**.

   Se crea un flujo de trabajo automáticamente para realizar la medición. El nombre se define automáticamente según la configuración de hipótesis.

   >[!CAUTION]
   >
   >You can access this if you have checked the **[!UICONTROL Keep execution workflow]** box.\
   >Esta opción debe activarse solo para fines de depuración, en caso de error al ejecutar la hipótesis. Los flujos de trabajo generados automáticamente se guardan en la carpeta **[!UICONTROL Administration]** > **[!UICONTROL Production]** > **[!UICONTROL Objects created automatically]** > **[!UICONTROL Campaign workflows]** del explorador de Adobe Campaign.
   > 
   >Además, los flujos de trabajo generados automáticamente no se deben modificar. No se tendrá en cuenta ninguna modificación para realizar cálculos más adelante.
   >
   >Si ha comprobado esta opción, elimine el flujo de trabajo una vez que se haya ejecutado.

   ![](assets/response_hypothesis_instance_creation_006.png)

   Una vez finalizado el cálculo, los indicadores de medición se actualizan automáticamente.

   ![](assets/response_hypothesis_instance_creation_007.png)

1. Si es necesario, cambie la configuración y vuelva a iniciar la hipótesis.

## Hacer referencia a una hipótesis en un envío de campaña {#referencing-a-hypothesis-in-a-campaign-delivery}

Puede hacer referencia a una hipótesis en una campaña de marketing antes de que se inicie. En este caso, la hipótesis se iniciará automáticamente una vez realizado el envío, según la configuración de ejecución definida en la plantilla de hipótesis. Para crear una hipótesis en un envío, aplique el siguiente proceso:

1. Según sus necesidades, puede crear una o varias plantillas de **[!UICONTROL Delivery]** tipo, tal como se describe en [Creación de un modelo de hipótesis](../../campaign/using/hypothesis-templates.md#creating-a-hypothesis-model)
1. Cree una campaña de marketing y flujos de trabajo de segmentación.
1. In the delivery window, click the **[!UICONTROL Delivery measurement]** icon.
1. Seleccione la plantilla de hipótesis (la consulta configurada en el modelo se muestra en la ventana de hipótesis).

   The hypothesis will be calculated automatically once the campaign is finished, based on the dates configured in the model (refer to [Hypothesis template execution settings](../../campaign/using/hypothesis-templates.md#hypothesis-template-execution-settings)).

   ![](assets/response_hypothesis_instance_creation_008.png)

## Añadir una hipótesis predeterminada a los envíos para una campaña {#adding-a-default-hypothesis-to-deliveries-for-a-campaign}

Puede hacer referencia directamente a una hipótesis en el nivel de campaña. En este caso, la hipótesis se vincula automáticamente a todos los envíos creados en la campaña. Para ello:

1. Go to the **[!UICONTROL Edit]** tab of the campaign.
1. In the measurement section, click the **[!UICONTROL Default hypotheses]** tab.

   ![](assets/response_hypothesis_instance_creation_010.png)

1. Click **[!UICONTROL Add]** and select a hypothesis template.

   ![](assets/response_hypothesis_instance_creation_011.png)

   Ahora se hará referencia a una hipótesis basada en esta plantilla por defecto en cada nuevo envío de la campaña.

   ![](assets/response_hypothesis_instance_creation_012.png)

Los resultados de la hipótesis se pueden ver en las fichas **[!UICONTROL General]** y **[!UICONTROL Reactions]** de la hipótesis (consulte Seguimiento de [hipótesis](../../campaign/using/hypothesis-tracking.md))

Para obtener más información, también puede consultar [Ejemplo: crear una hipótesis vinculada a una entrega](#example--creating-a-hypothesis-linked-to-a-delivery).

## Creación de una hipótesis sobre una oferta {#creating-a-hypothesis-on-an-offer}

Crear una hipótesis sobre una propuesta de oferta es similar a crear una hipótesis de envío sobre la marcha. La hipótesis se puede ejecutar siempre que la oferta esté activa. El periodo de cálculo se basa en la fecha de la propuesta de oferta. When the hypothesis lets you link a recipient to a purchase, the status of the offer proposition likely to be accepted can be changed automatically (for more on this, refer to [Transactions](../../campaign/using/hypothesis-templates.md#transactions)).

1. Cree uno o varios modelos **[!UICONTROL Offer]** de tipo como se describe en [Creación de un modelo](../../campaign/using/hypothesis-templates.md#creating-a-hypothesis-model)de hipótesis.
1. Vaya al **[!UICONTROL Campaign management > Measurement hypotheses]** nodo.
1. Create an **[!UICONTROL Offers]** type hypothesis by selecting the model created previously.

   ![](assets/response_hypothesis_instance_offer_001.png)

   La consulta creada en el modelo aparece en la ventana.

   ![](assets/response_hypothesis_instance_offer_003.png)

1. Elija la oferta para la que desea crear una hipótesis.

   ![](assets/response_hypothesis_instance_offer_004.png)

1. Refine la consulta si es necesario.
1. Click **[!UICONTROL Start]** to run the hypothesis.
1. Los resultados de la hipótesis pueden verse en sus fichas **[!UICONTROL General]** y **[!UICONTROL Reactions]** (consulte Seguimiento de [hipótesis](../../campaign/using/hypothesis-tracking.md)).

   Hypotheses made on an offer are referenced in the **[!UICONTROL Measurement]** tab.

   ![](assets/response_hypothesis_instance_offer_007.png)

   If the **[!UICONTROL Update offer proposition status]** option was enabled in the hypothesis template, the status of the offer proposition is changed automatically, thereby providing feedback on the impact of the campaign (for more on this, refer to [Transactions](../../campaign/using/hypothesis-templates.md#transactions)).

## Ejemplo: Creación de una hipótesis vinculada a un envío {#example--creating-a-hypothesis-linked-to-a-delivery}

En este ejemplo, queremos crear una hipótesis vinculada a un envío. Esta hipótesis se basará en el modelo creado anteriormente (consulte [Ejemplo: creación de una plantilla de hipótesis en una entrega](../../campaign/using/hypothesis-templates.md#example--creating-a-hypothesis-template-on-a-delivery)). Luego, afinaremos la consulta heredada del modelo para hacer una hipótesis sobre un artículo específico de la tabla de compras.

1. Create a campaign and a delivery (For more on this, refer to [Creating a campaign](../../campaign/using/setting-up-marketing-campaigns.md#creating-a-campaign)).

   En nuestro ejemplo, utilizaremos un envío de correo postal.

1. Configurar una dirección semilla: la plantilla de hipótesis creada anteriormente se configuró para tener en cuenta un grupo de control en los resultados de la reacción.

   ![](assets/response_hypothesis_delivery_example_007.png)

   >[!NOTE]
   >
   >Para obtener más información, consulte [Definición de un grupo](../../campaign/using/marketing-campaign-deliveries.md#defining-a-control-group)de control.

1. Abra el **[!UICONTROL Direct mail delivery]** y haga clic en el **[!UICONTROL Delivery measurement]** icono y, a continuación, haga clic en **[!UICONTROL Add]**.

   ![](assets/response_hypothesis_delivery_example_002.png)

1. Elija la plantilla de hipótesis creada anteriormente en la lista desplegable.

   ![](assets/response_hypothesis_delivery_example_004.png)

   Se muestra la consulta creada en el modelo.

   ![](assets/response_hypothesis_delivery_example_005.png)

1. Click **[!UICONTROL Edit query...]** and refine the query by entering the product that the hypothesis will concern.

   ![](assets/response_hypothesis_delivery_example_006.png)

   You can check that the hypothesis is linked to the delivery in the **[!UICONTROL Edit]** > **[!UICONTROL Measurement]** tab of the campaign.

   ![](assets/response_hypothesis_delivery_example_008.png)

1. Launch your targeting workflow and run the necessary checks until the campaign is finished (for more on this, refer to [Starting a delivery](../../campaign/using/marketing-campaign-deliveries.md#starting-a-delivery)).

   ![](assets/response_hypothesis_delivery_example_009.png)

1. In the Adobe Campaign tree, go to the **[!UICONTROL Campaign management > Measurement hypotheses]** node to check the indicators calculated by the hypothesis.

   ![](assets/response_hypothesis_delivery_example_010.png)

