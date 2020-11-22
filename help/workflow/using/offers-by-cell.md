---
solution: Campaign Classic
product: campaign
title: Ofertas por celda
description: Ofertas por celda
audience: workflow
content-type: reference
topic-tags: targeting-activities
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '150'
ht-degree: 100%

---


# Ofertas por celda{#offers-by-cell}

La actividad **[!UICONTROL Offers by cell]** permite distribuir la población entrante (desde una consulta por ejemplo) en varios segmentos y especificar una oferta para presentar a cada uno de estos segmentos.

Esta actividad solo se puede utilizar con **Interaction**. Para obtener más información, consulte esta [sección](../../interaction/using/about-outbound-channels.md).

Para ello:

1. Una vez que haya especificado la población destinataria, añada la actividad **[!UICONTROL Offers by cell]** y ábrala.
1. En la pestaña **[!UICONTROL General]**, seleccione el espacio de oferta en el que desea presentar las ofertas.
1. En la pestaña **[!UICONTROL Cells]**, especifique los diferentes subconjuntos con el botón **[!UICONTROL Add]**:

   * Especifique la población del subconjunto utilizando las reglas de filtrado y limitación disponibles.
   * A continuación, seleccione la oferta que desee presentar al subconjunto. Las ofertas disponibles son aquellas aptas en el espacio de oferta seleccionado en el paso anterior.

      ![](assets/int_offer_per_cell1.png)

1. A continuación, configure una actividad de entrega que corresponda al canal elegido. Consulte [Envíos multicanal](../../workflow/using/cross-channel-deliveries.md).

