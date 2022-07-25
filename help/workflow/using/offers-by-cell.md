---
product: campaign
title: Ofertas por celda
description: Ofertas por celda
feature: Workflows, Targeting Activity, Interaction
exl-id: 72b17b48-093a-4eb9-a848-3c1570e49b61
source-git-commit: 381538fac319dfa075cac3db2252a9cc80b31e0f
workflow-type: ht
source-wordcount: '150'
ht-degree: 100%

---

# Ofertas por celda{#offers-by-cell}

![](../../assets/v7-only.svg)

La actividad **[!UICONTROL Offers by cell]** permite distribuir la población entrante (desde una consulta por ejemplo) en varios segmentos y especificar una oferta para presentar a cada uno de estos segmentos.

Esta actividad solo se puede utilizar con **Interaction**. Para obtener más información, consulte esta [sección](../../interaction/using/about-outbound-channels.md).

Para ello:

1. Una vez que haya especificado la población destinataria, añada la actividad **[!UICONTROL Offers by cell]** y ábrala.
1. En la pestaña **[!UICONTROL General]**, seleccione el espacio de oferta en el que desea presentar las ofertas.
1. En la pestaña **[!UICONTROL Cells]**, especifique los diferentes subconjuntos con el botón **[!UICONTROL Add]**:

   * Especifique la población del subconjunto utilizando las reglas de filtrado y limitación disponibles.
   * A continuación, seleccione la oferta que desee presentar al subconjunto. Las ofertas disponibles son aquellas aptas en el espacio de oferta seleccionado en el paso anterior.

      ![](assets/int_offer_per_cell1.png)

1. A continuación, configure una actividad de entrega que corresponda al canal elegido. Consulte [Envíos multicanal](cross-channel-deliveries.md).
