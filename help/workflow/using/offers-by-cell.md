---
title: Ofertas por celda
seo-title: Ofertas por celda
description: Ofertas por celda
seo-description: null
page-status-flag: never-activated
uuid: 731bfdde-abd2-400e-9e22-3dbaad37c5b9
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: workflow
content-type: reference
topic-tags: targeting-activities
discoiquuid: d90594bb-e3ba-4fb1-9e11-83d519c1ca7d
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 20f835c357d016643ea1f3209ee4dfb6d3239f90

---


# Ofertas por celda{#offers-by-cell}

The **[!UICONTROL Offers by cell]** activity lets you distribute the inbound population (from a query for example) into several segments and to specify an offer to present for each of these segments.

Esta actividad solo se puede utilizar con **Interaction**. Para obtener más información, consulte esta [sección](../../interaction/using/about-outbound-channels.md).

Para ello:

1. Add the **[!UICONTROL Offers by cell]** activity once you have specified the target population, then open it.
1. In the **[!UICONTROL General]** tab, select the offer space on which you want to present the offers.
1. En la **[!UICONTROL Cells]** ficha, especifique los distintos subconjuntos utilizando el **[!UICONTROL Add]** botón:

   * Especifique la población del subconjunto utilizando las reglas de filtrado y limitación disponibles.
   * A continuación, seleccione la oferta que desee presentar al subconjunto. Las ofertas disponibles son aquellas aptas en el espacio de oferta seleccionado en el paso anterior.

      ![](assets/int_offer_per_cell1.png)

1. A continuación, configure una actividad de envío que corresponda al canal elegido. Consulte Entregas [](../../workflow/using/cross-channel-deliveries.md)multicanal.

