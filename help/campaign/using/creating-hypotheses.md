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
translation-type: tm+mt
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: tm+mt
source-wordcount: '1063'
ht-degree: 70%

---


# Creación de hipótesis{#creating-hypotheses}

Existen varias formas para crear y vincular hipótesis a una oferta o entrega de campaña:

* Via the **[!UICONTROL Measurement hypotheses]** folder by creating a new hypothesis based on an existing template and linking it to an existing delivery.
* Mediante la **[!UICONTROL Edit]** ficha > **[!UICONTROL Measurement]** de una campaña.
* Via the **[!UICONTROL Measurement]** option of a delivery created from a campaign.

Las hipótesis solo se pueden calcular una vez que se haya iniciado la campaña de marketing y los destinatarios hayan recibido la entrega. Si la hipótesis se basa en una propuesta de oferta, la última debe estar presente y permanecer activa. Offer and delivery hypotheses are created via the **[!UICONTROL Measurement hypotheses]** folder and are based on a hypothesis template. Sin embargo, es posible hacer referencia a una hipótesis directamente en la entrega o la campaña antes de que comience la campaña. En este caso, la hipótesis se calculará automáticamente una vez que se inicie la campaña de marketing, según la configuración de ejecución (para obtener más información, consulte).[](../../campaign/using/hypothesis-templates.md#hypothesis-template-execution-settings)

## Creación de una hipótesis sobre la marcha {#creating-a-hypothesis-on-the-fly-on-a-delivery}

Para crear una hipótesis en una entrega existente, aplique el siguiente proceso:

>[!NOTE]
>
>Esta operación solo es posible para envíos pendientes.

1. En el árbol de Adobe Campaign, vaya a **[!UICONTROL Campaign management > Measurement hypotheses]**.
1. Click the **[!UICONTROL New]** button or right-click on the list of hypotheses and select **[!UICONTROL New]** in the drop-down list.

   ![](assets/response_hypothesis_instance_creation_002.png)

1. En la ventana de hipótesis, seleccione una plantilla creada previamente (consulte).[](../../campaign/using/hypothesis-templates.md)

   ![](assets/response_hypothesis_instance_creation_003.png)

   El contexto de hipótesis tal como se definió en el modelo seleccionado se muestra en la ventana.

   >[!NOTE]
   >
   >Los ajustes definidos en la plantilla y no visibles en este paso se mantendrán también en la memoria y se vuelven a asignar a la hipótesis en curso.

   ![](assets/response_hypothesis_instance_creation_004.png)

1. Seleccione la entrega para la que desea crear una hipótesis.

   ![](assets/response_hypothesis_instance_creation_005.png)

1. You can personalize your hypothesis by editing the **[!UICONTROL General]**, **[!UICONTROL Transactions]** and **[!UICONTROL Scope]** tabs. Para más información, consulte [Creación de un modelo de hipótesis](../../campaign/using/hypothesis-templates.md#creating-a-hypothesis-model).
1. Start the hypothesis by clicking **[!UICONTROL Start]**.

   Se crea un flujo de trabajo automáticamente para realizar la medición. El nombre se define automáticamente según la configuración de hipótesis.

   >[!CAUTION]
   >
   >You can access this if you have checked the **[!UICONTROL Keep execution workflow]** box.\
   >Esta opción debe activarse solo para fines de depuración, en caso de error al ejecutar la hipótesis. Workflows generated automatically are saved in the **[!UICONTROL Administration]** > **[!UICONTROL Production]** > **[!UICONTROL Objects created automatically]** > **[!UICONTROL Campaign workflows]** folder in the Adobe Campaign explorer.
   > 
   >Además, los flujos de trabajo generados automáticamente no se deben modificar. No se tendrá en cuenta ninguna modificación para realizar cálculos más adelante.
   >
   >Si ha comprobado esta opción, elimine el flujo de trabajo una vez que se haya ejecutado.

   ![](assets/response_hypothesis_instance_creation_006.png)

   Una vez finalizado el cálculo, los indicadores de medición se actualizan automáticamente.

   ![](assets/response_hypothesis_instance_creation_007.png)

1. Si es necesario, cambie la configuración y vuelva a iniciar la hipótesis.

## Hacer referencia a una hipótesis en una entrega de campaña {#referencing-a-hypothesis-in-a-campaign-delivery}

Puede hacer referencia a una hipótesis en una campaña de marketing antes de que se inicie. En este caso, la hipótesis se iniciará automáticamente una vez realizado la entrega, según la configuración de ejecución definida en la plantilla de hipótesis. Para crear una hipótesis en una entrega, aplique el siguiente proceso:

1. Depending on your needs, you can create one or more **[!UICONTROL Delivery]** type templates, as described in [Creating a hypothesis model](../../campaign/using/hypothesis-templates.md#creating-a-hypothesis-model)
1. Cree una campaña de marketing y flujos de trabajo de segmentación.
1. In the delivery window, click the **[!UICONTROL Delivery measurement]** icon.
1. Seleccione la plantilla de hipótesis (la consulta configurada en el modelo se muestra en la ventana de hipótesis).

   La hipótesis se calculará automáticamente una vez finalizada la campaña, según las fechas configuradas en el modelo (consulte).[Configurar la ejecución de una plantilla de hipótesis](../../campaign/using/hypothesis-templates.md#hypothesis-template-execution-settings)

   ![](assets/response_hypothesis_instance_creation_008.png)

## Añadir una hipótesis predeterminada a los envíos para una campaña {#adding-a-default-hypothesis-to-deliveries-for-a-campaign}

Puede hacer referencia directamente a una hipótesis en el nivel de campaña. En este caso, la hipótesis se vincula automáticamente a todas las entregas creadas en la campaña. Para ello:

1. Go to the **[!UICONTROL Edit]** tab of the campaign.
1. In the measurement section, click the **[!UICONTROL Default hypotheses]** tab.

   ![](assets/response_hypothesis_instance_creation_010.png)

1. Click **[!UICONTROL Add]** and select a hypothesis template.

   ![](assets/response_hypothesis_instance_creation_011.png)

   Ahora se hará referencia a una hipótesis basada en esta plantilla por defecto en cada nueva entrega de la campaña.

   ![](assets/response_hypothesis_instance_creation_012.png)

The hypothesis results can be viewed in the **[!UICONTROL General]** and **[!UICONTROL Reactions]** tabs of the hypothesis (refer to [Hypothesis tracking](../../campaign/using/hypothesis-tracking.md))

Para obtener más información, también puede consultar [Ejemplo: crear una hipótesis vinculada a una entrega](#example--creating-a-hypothesis-linked-to-a-delivery).

## Creación de una hipótesis sobre una oferta {#creating-a-hypothesis-on-an-offer}

Crear una hipótesis sobre una propuesta de oferta es similar a crear una hipótesis de entrega sobre la marcha. La hipótesis se puede ejecutar siempre que la oferta esté activa. El periodo de cálculo se basa en la fecha de la propuesta de oferta. Cuando la hipótesis le permite vincular un destinatario a una compra, el estado de la propuesta de oferta susceptible de ser aceptada puede cambiar automáticamente (para obtener más información, consulte).[Transacciones](../../campaign/using/hypothesis-templates.md#transactions)

1. Create one or more **[!UICONTROL Offer]** type models as described in [Creating a hypothesis model](../../campaign/using/hypothesis-templates.md#creating-a-hypothesis-model).
1. Vaya al nodo **[!UICONTROL Campaign management > Measurement hypotheses]**.
1. Create an **[!UICONTROL Offers]** type hypothesis by selecting the model created previously.

   ![](assets/response_hypothesis_instance_offer_001.png)

   La consulta creada en el modelo aparece en la ventana.

   ![](assets/response_hypothesis_instance_offer_003.png)

1. Elija la oferta para la que desea crear una hipótesis.

   ![](assets/response_hypothesis_instance_offer_004.png)

1. Refine la consulta si es necesario.
1. Click **[!UICONTROL Start]** to run the hypothesis.
1. The hypothesis results can be viewed in its **[!UICONTROL General]** and **[!UICONTROL Reactions]** tabs (refer to [Hypothesis tracking](../../campaign/using/hypothesis-tracking.md)).

   Hypotheses made on an offer are referenced in the **[!UICONTROL Measurement]** tab.

   ![](assets/response_hypothesis_instance_offer_007.png)

   If the **[!UICONTROL Update offer proposition status]** option was enabled in the hypothesis template, the status of the offer proposition is changed automatically, thereby providing feedback on the impact of the campaign (for more on this, refer to [Transactions](../../campaign/using/hypothesis-templates.md#transactions)).

## Ejemplo: Creación de una hipótesis vinculada a una entrega {#example--creating-a-hypothesis-linked-to-a-delivery}

En este ejemplo, queremos crear una hipótesis vinculada a una entrega. Esta hipótesis se basará en el modelo creado anteriormente (consulte [Ejemplo: creación de una plantilla de hipótesis en una entrega](../../campaign/using/hypothesis-templates.md#example--creating-a-hypothesis-template-on-a-delivery)). Luego, afinaremos la consulta heredada del modelo para hacer una hipótesis sobre un artículo específico de la tabla de compras.

1. Cree una campaña y una entrega (para obtener más información, consulte).[Crear una campaña](../../campaign/using/setting-up-marketing-campaigns.md#creating-a-campaign)

   En nuestro ejemplo, utilizaremos una entrega de correo postal.

1. Configurar una dirección semilla: la plantilla de hipótesis creada anteriormente se configuró para tener en cuenta un grupo de control en los resultados de la reacción.

   ![](assets/response_hypothesis_delivery_example_007.png)

   >[!NOTE]
   >
   >Para obtener más información, consulte [Definición de un grupo de control](../../campaign/using/marketing-campaign-deliveries.md#defining-a-control-group).

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

1. Inicie el flujo de trabajo de segmentación y ejecute las comprobaciones necesarias hasta que finalice la campaña (para obtener más información, consulte).[Comenzar la entrega](../../campaign/using/marketing-campaign-deliveries.md#starting-a-delivery)

   ![](assets/response_hypothesis_delivery_example_009.png)

1. In the Adobe Campaign tree, go to the **[!UICONTROL Campaign management > Measurement hypotheses]** node to check the indicators calculated by the hypothesis.

   ![](assets/response_hypothesis_delivery_example_010.png)

