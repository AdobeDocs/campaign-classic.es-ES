---
title: Reglas de presentación
seo-title: Reglas de presentación
description: Reglas de presentación
seo-description: null
page-status-flag: never-activated
uuid: 460f06f8-cdb9-401d-a45e-e54e56d66781
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: interaction
content-type: reference
topic-tags: case-study
discoiquuid: 8ef303b4-d9ce-40ee-a6c6-ed5012ab8eb8
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 28614a6b0c45deef17d9b3275a16e65bdff4538b

---


# Reglas de presentación{#presentation-rules}

## Creación de una regla de presentación {#creating-a-presentation-rule}

En nuestra base de datos existen varias ofertas de viajes para Europa, África, Estados Unidos y Canadá. Queremos enviar ofertas para un viaje a Canadá, pero si el destinatario rechaza este tipo de oferta, no queremos enviarlas de nuevo.

Vamos a configurar nuestra regla para que el viaje a Canadá se ofrezca solo una vez por destinatario y no se ofrezca nuevamente si se rechaza.

1. En el árbol de Adobe Campaign, vaya al nodo **[!UICONTROL Administration]** > **[!UICONTROL Campaign management]** > **[!UICONTROL Typology management]** > **[!UICONTROL Typology rules]** .
1. Cree una nueva regla **[!UICONTROL Offer presentation]** de tipo.

   ![](assets/offer_typology_example_001.png)

1. Cambie la etiqueta y la descripción si es necesario.

   ![](assets/offer_typology_example_002.png)

1. Choose the **[!UICONTROL All channels]** option to extend the rule to all channels.

   ![](assets/offer_typology_example_003.png)

1. Haga clic en el **[!UICONTROL Edit expression]** vínculo y elija el **[!UICONTROL Category]** nodo como expresión.

   ![](assets/offer_typology_example_004.png)

1. Choose the category that matches your travel offer for Canada and click **[!UICONTROL OK]** to close the query window.

   ![](assets/offer_typology_example_005.png)

1. In the **[!UICONTROL Offer presentation]** tab, choose the same dimensions as those configured in the environment.

   ![](assets/offer_typology_example_006.png)

1. Indique el período durante el que se aplica la regla.

   ![](assets/offer_typology_example_007.png)

1. Limite la propuesta a una de forma que los destinatarios que ya hayan rechazado el viaje a Canadá no reciban otra oferta similar.

   ![](assets/offer_typology_example_008.png)

1. Select the **[!UICONTROL Offers for the same category]** filter to exclude all offers from the **Canada** category.

   ![](assets/offer_typology_example_020.png)

1. Select the **[!UICONTROL Rejected propositions]** filter to take into account only propositions rejected by the recipient.

   ![](assets/offer_typology_example_021.png)

1. Indique los destinatarios para los cuales se asigna la regla.

   En nuestro ejemplo, elegimos los destinatarios **viajeros frecuentes**.

   ![](assets/offer_typology_example_009.png)

1. Cite la regla en la tipología de ofertas.

   ![](assets/offer_typology_example_013.png)

1. Go to the offer environment, (**Environment - Recipient** in this case) and reference the new typology just created using the drop-down list in the **[!UICONTROL Eligibility]** tab.

   ![](assets/offer_typology_example_014.png)

## Aplicación de la regla de presentación {#applying-the-presentation-rule}

A continuación se muestra un ejemplo de aplicación de la regla de tipología creada anteriormente.

Queremos enviar una primera propuesta de oferta perteneciente a la categoría Canadá. Si la oferta se rechaza una vez por cualquiera de los destinatarios, no se ofrece de nuevo.

1. In the **Frequent travelers** recipient folder, choose one of the profiles to check the offers for which they are eligible: click the **[!UICONTROL Propositions]** tab, then the **[!UICONTROL Preview]** tab.

   En nuestro ejemplo, **Tim Ramsey** es apto para una oferta que forma parte de la categoría **América**.

   ![](assets/offer_typology_example_015.png)

1. Comience creando un envío por correo electrónico dirigido a sus destinatarios **viajeros frecuentes** con ofertas.
1. Seleccione los parámetros para visualizar el motor de ofertas.

   En nuestro ejemplo, se elige la categoría **Viaje en América**, que contiene las subcategorías de **Canadá** y **Estados Unidos**.

   ![](assets/offer_typology_example_016.png)

1. Inserte sus ofertas en el cuerpo del mensaje y mande el envío. For more on this, refer to [About outbound channels](../../interaction/using/about-outbound-channels.md).

   El destinatario recibió la oferta para la cual es apto.

1. El destinatario rechazó la oferta de Canadá como se muestra en el historial de propuestas.

   ![](assets/offer_typology_example_018.png)

1. Compruebe las ofertas para las que ahora son aptos.

   Podemos ver que no se han elegido ofertas para Canadá.

   ![](assets/offer_typology_example_019.png)

**Tema relacionado**

* [Administre ofertas y controle la redundancia entre canales](https://helpx.adobe.com/campaign/kb/simplifying-campaign-management-acc.html#Manageoffersandcontrolredundancyacrosschannels)