---
product: campaign
title: Creación de categorías de oferta
description: Creación de categorías de oferta
audience: interaction
content-type: reference
topic-tags: managing-an-offer-catalog
exl-id: ed97a1b5-c870-4b67-98b6-16adc316fd46
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: tm+mt
source-wordcount: '266'
ht-degree: 100%

---

# Creación de categorías de oferta{#creating-offer-categories}

La creación de categorías de ofertas solo puede realizarse en el entorno **[!UICONTROL Design]**. Se implementan automáticamente en el entorno **[!UICONTROL Live]** (es decir, están disponibles) cuando se aprueban las ofertas creadas o modificadas que contienen. De forma predeterminada, el entorno **[!UICONTROL Design]** una categoría para recibir todas las ofertas. Se puede crear subcategorías para añadir jerarquía a las ofertas del catálogo.

Para cada categoría, se pueden definir las fechas de idoneidad, es decir, un punto más allá del cual las ofertas contenidas en la categoría ya no puedan presentarse al objetivo. Si se desea que las ofertas de una categoría específica se seleccionen como una prioridad por el motor de oferta, para exponer mejor un producto por ejemplo, se puede aumentar sus ponderaciones para un periodo determinado añadiendo una ponderación de multiplicación a la categoría.

Para crear una categoría adicional, siga los siguientes pasos:

1. Vaya a la carpeta **[!UICONTROL Offer catalog]**.

   ![](assets/offer_cat_create_001.png)

1. Haga clic derecho en el ratón y, en la lista desplegable, seleccione **[!UICONTROL Create a new "Offer category" folder]**.

   ![](assets/offer_cat_create_002.png)

1. Cambie el nombre de la categoría. Se puede editar la etiqueta más adelante mediante la pestaña **[!UICONTROL General]**.

   ![](assets/offer_cat_create_003.png)

   >[!NOTE]
   >
   >Repita estos pasos para crear tantas categorías como sea necesario.

   A continuación, según sea necesario, se puede:

   * asignar las fechas de idoneidad en la pestaña **[!UICONTROL Eligibility]**.

      ![](assets/offer_cat_create_004.png)

   * Escribir las palabras clave que se pueden utilizar para seleccionar ofertas dentro de esta categoría, utilizando el campo **[!UICONTROL Themes]**.

      ![](assets/offer_cat_create_005.png)

      >[!NOTE]
      >
      >Al llamar al motor de oferta, solo se selecciona la parte del catálogo en la que coinciden los temas o categorías con los parámetros.

   * Se puede “incrementar” temporalmente la ponderación de la oferta de una categoría durante un periodo determinado mediante el campo **[!UICONTROL Multiplier weight]**.

      ![](assets/offer_cat_create_006.png)

Un resumen de las reglas de idoneidad está disponible en el panel de las ofertas incluidas en la categoría. Para visualizarlos, haga clic en el vínculo **[!UICONTROL Schedule and eligibility rules of the offer]**.

![](assets/offer_create_006.png)
