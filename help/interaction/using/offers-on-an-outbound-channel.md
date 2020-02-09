---
title: Ofertas en un canal saliente
seo-title: Ofertas en un canal saliente
description: Ofertas en un canal saliente
seo-description: null
page-status-flag: never-activated
uuid: a8a7ce5f-0d18-47f2-b258-34b9471de769
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: interaction
content-type: reference
topic-tags: case-study
discoiquuid: 3bd113c3-da67-4f4f-aa40-f4c7860a8569
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 215e4d1ca78938b38b53cae0357612deebf7727b

---


# Ofertas en un canal saliente{#offers-on-an-outbound-channel}

## Envío de ofertas por correo electrónico {#email-offer-delivery}

En nuestra base de datos, existe una categoría de ofertas de viajes a África. Se han configurado los requisitos, los contextos y las representaciones de cada oferta. Ahora queremos crear una campaña para presentar las ofertas por correo electrónico.

1. Cree una campaña de marketing y los flujos de trabajo de segmentación.

   ![](assets/offer_delivery_example_001.png)

1. Edit the email delivery and click the **[!UICONTROL Offers]** icon.

   ![](assets/offer_delivery_example_002.png)

1. Elija el espacio del correo electrónico para el entorno de la oferta que coincida con los días festivos.

   ![](assets/offer_delivery_example_003.png)

1. Elija la categoría que contiene las ofertas de viajes de África.

   ![](assets/offer_delivery_example_004.png)

1. Defina el número de ofertas en el envío a dos.

   ![](assets/offer_delivery_example_005.png)

1. Cierre la ventana de administración de ofertas y cree el contenido de su envío.

   ![](assets/offer_delivery_example_006.png)

1. Utilice los menús para insertar una primera propuesta de oferta y elija la función de procesamiento HTML.

   ![](assets/offer_delivery_example_007.png)

1. Inserte la segunda propuesta de oferta.

   ![](assets/offer_delivery_example_008.png)

1. Click **[!UICONTROL Preview]** to preview your offers in the delivery then select a recipient to preview the offers as they will receive them.

   ![](assets/offer_delivery_example_009.png)

1. Guarde el envío e inicie el flujo de trabajo de objetivos.
1. Open your delivery and click the **[!UICONTROL Audit]** tab of your delivery: you can see that the offer engine has selected the propositions to be made from the various offers in the catalog.

   ![](assets/offer_delivery_example_010.png)

## Realizar una simulación de oferta {#perform-an-offer-simulation}

1. En el **[!UICONTROL Profiles and Targets]** universo, haga clic en el **[!UICONTROL Simulations]** vínculo y, a continuación, haga clic en el **[!UICONTROL Create]** botón .

   ![](assets/offer_simulation_001.png)

1. Elija una etiqueta y especifique la configuración de ejecución si es necesario.

   ![](assets/offer_simulation_example_002.png)

1. Guarde la simulación. A continuación, se abre en una nueva pestaña.

   ![](assets/offer_simulation_example_003.png)

1. Haga clic en la **[!UICONTROL Edit]** ficha y, a continuación, **[!UICONTROL Scope]**.

   ![](assets/offer_simulation_example_004.png)

1. Elija la categoría para la que desea simular las ofertas.

   ![](assets/offer_simulation_example_005.png)

1. Seleccione el espacio de oferta que se utilizará para la simulación.

   ![](assets/offer_simulation_example_006.png)

1. Introduzca las fechas de validez. Debe introducir al menos una fecha de inicio. Esto permite que el filtro del motor de ofertas ofrezca y elija las que son válidas en una fecha determinada.
1. Si es necesario, especifique uno o varios temas para restringir el número de ofertas a aquellas que contengan una palabra clave en su configuración.

   En nuestro ejemplo, la categoría **Viaje** contiene dos subcategorías con dos temas independientes. Queremos ejecutar una simulación para las ofertas con el tema de los **clientes>1 año**.

   ![](assets/offer_simulation_example_007.png)

1. Elija los destinatarios a los que desea destinarlas.

   ![](assets/offer_simulation_example_008.png)

1. Configure el número de ofertas que se enviarán a cada destinatario.

   En nuestro ejemplo, el motor de oferta elegirá las 3 ofertas con el peso más alto para cada destinatario.

   ![](assets/offer_simulation_example_009.png)

1. Save your settings, then click **[!UICONTROL Start]** in the **[!UICONTROL Dashboard]** tab to run the simulation.

   ![](assets/offer_simulation_example_010.png)

1. Once the simulation is finished, consult the **[!UICONTROL Results]** for a detailed breakdown of propositions per offer.

   En nuestro ejemplo, el motor de oferta basa el desglose de las ofertas en 3 propuestas.

   ![](assets/offer_simulation_example_011.png)

1. Display the **[!UICONTROL Breakdown of offers by rank]** to view the list of offers selected by the offer engine.

   ![](assets/offer_simulation_example_012.png)

1. If necessary, you can change the scope settings and run the simulation again by clicking **[!UICONTROL Start simulation]**.

   ![](assets/offer_simulation_example_010.png)

1. Para guardar los datos de simulación, utilice las funciones del historial o de exportación disponibles en el informe.

   ![](assets/offer_simulation_example_013.png)

