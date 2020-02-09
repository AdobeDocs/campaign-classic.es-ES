---
title: Creación de categorías de oferta
seo-title: Creación de categorías de oferta
description: Creación de categorías de oferta
seo-description: null
page-status-flag: never-activated
uuid: 5ac0ae5e-1731-4699-b4ef-f3867ad0ab58
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: interaction
content-type: reference
topic-tags: managing-an-offer-catalog
discoiquuid: a9fad813-3256-4a00-ba74-7dbaba9e8e23
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 579329d9194115065dff2c192deb0376c75e67bd

---


# Creación de categorías de oferta{#creating-offer-categories}

The creation of offer categories can only take place in the **[!UICONTROL Design]** environment. They are deployed automatically in the **[!UICONTROL Live]** environment (i.e. made available) when the created/modified offer(s) they contain are approved. By default, the **[!UICONTROL Design]** environment contains a category to receive all offers. Se puede crear subcategorías para añadir jerarquía a las ofertas del catálogo.

Para cada categoría, se pueden definir las fechas de idoneidad, es decir, un punto más allá del cual las ofertas contenidas en la categoría ya no puedan presentarse al objetivo. Si se desea que las ofertas de una categoría específica se seleccionen como una prioridad por el motor de oferta, para exponer mejor un producto por ejemplo, se puede aumentar sus ponderaciones para un período determinado añadiendo una ponderación de multiplicación a la categoría.

Para crear una categoría adicional, siga los siguientes pasos:

1. Vaya a la **[!UICONTROL Offer catalog]** carpeta.

   ![](assets/offer_cat_create_001.png)

1. Haga clic con el botón derecho y seleccione **[!UICONTROL Create a new "Offer category" folder]** en la lista desplegable.

   ![](assets/offer_cat_create_002.png)

1. Cambie el nombre de la categoría. You can edit the label later using the **[!UICONTROL General]** tab.

   ![](assets/offer_cat_create_003.png)

   >[!NOTE]
   >
   >Repita estos pasos para crear tantas categorías como sea necesario.

   A continuación, según sea necesario, se puede:

   * assign eligibility dates from the **[!UICONTROL Eligibility]** tab.

      ![](assets/offer_cat_create_004.png)

   * enter key words that may be used to select offers from within this category, using the **[!UICONTROL Themes]** field.

      ![](assets/offer_cat_create_005.png)

      >[!NOTE]
      >
      >Al llamar al motor de oferta, solo se selecciona la parte del catálogo en la que coinciden los temas o categorías con los parámetros.

   * You can temporarily &quot;boost&quot; the offer weight of a category for a given period via the **[!UICONTROL Multiplier weight]** field.

      ![](assets/offer_cat_create_006.png)

Un resumen de las reglas de idoneidad está disponible en el panel de las ofertas incluidas en la categoría. Para verlos, haga clic en el **[!UICONTROL Schedule and eligibility rules of the offer]** vínculo.

![](assets/offer_create_006.png)

