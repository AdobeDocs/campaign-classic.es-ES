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
translation-type: tm+mt
source-git-commit: 8fc3e793ec544948049fc122b44b6bffdebecba0
workflow-type: tm+mt
source-wordcount: '269'
ht-degree: 80%

---


# Creación de categorías de oferta{#creating-offer-categories}

La creación de categorías de ofertas solo puede realizarse en el entorno **[!UICONTROL Design]**. Se implementan automáticamente en el entorno **[!UICONTROL Live]** (es decir, están disponibles) cuando se aprueban las ofertas creadas o modificadas que contienen. De forma predeterminada, el entorno **[!UICONTROL Design]** una categoría para recibir todas las ofertas. Se puede crear subcategorías para añadir jerarquía a las ofertas del catálogo.

Para cada categoría, se pueden definir las fechas de idoneidad, es decir, un punto más allá del cual las ofertas contenidas en la categoría ya no puedan presentarse al objetivo. Si se desea que las ofertas de una categoría específica se seleccionen como una prioridad por el motor de oferta, para exponer mejor un producto por ejemplo, se puede aumentar sus ponderaciones para un periodo determinado añadiendo una ponderación de multiplicación a la categoría.

Para crear una categoría adicional, siga los siguientes pasos:

1. Vaya a la carpeta **[!UICONTROL Offer catalog]**.

   ![](assets/offer_cat_create_001.png)

1. Right click and select **[!UICONTROL Create a new "Offer category" folder]** from the drop-down list.

   ![](assets/offer_cat_create_002.png)

1. Cambie el nombre de la categoría. Se puede editar la etiqueta más adelante mediante la pestaña **[!UICONTROL General]**.

   ![](assets/offer_cat_create_003.png)

   >[!NOTE]
   >
   >Repita estos pasos para crear tantas categorías como sea necesario.

   A continuación, según sea necesario, se puede:

   * Assign eligibility dates from the **[!UICONTROL Eligibility]** tab.

      ![](assets/offer_cat_create_004.png)

   * Enter key words that may be used to select offers from within this category, using the **[!UICONTROL Themes]** field.

      ![](assets/offer_cat_create_005.png)

      >[!NOTE]
      >
      >Al llamar al motor de oferta, solo se selecciona la parte del catálogo en la que coinciden los temas o categorías con los parámetros.

   * Temporarily &quot;boost&quot; the offer weight of a category for a given period via the **[!UICONTROL Multiplier weight]** field.

      ![](assets/offer_cat_create_006.png)

Un resumen de las reglas de idoneidad está disponible en el panel de las ofertas incluidas en la categoría. Para vista, haga clic en el **[!UICONTROL Schedule and eligibility rules of the offer]** vínculo.

![](assets/offer_create_006.png)

