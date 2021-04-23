---
solution: Campaign Classic
product: campaign
title: Ámbito de la simulación
description: Ámbito de la simulación
audience: interaction
content-type: reference
topic-tags: simulating-offers
exl-id: 4f6b3de2-3fdf-441d-925d-476e20e75c6f
translation-type: ht
source-git-commit: 6854d06f8dc445b56ddfde7777f02916a60f2b63
workflow-type: ht
source-wordcount: '236'
ht-degree: 100%

---

# Ámbito de la simulación{#simulation-scope}

## Definición del ámbito {#definition-of-the-scope}

Abra la pestaña **[!UICONTROL Scope]** para elegir los ajustes.

Los siguientes campos son obligatorios:

* Entorno o categoría de la oferta.
* Espacio de ofertas.
* Fecha de contacto. No se tienen en cuenta las ofertas no válidas en la fecha de contacto.
* Público destinatario.

   Si no se configura un filtro de destino, se tiene en cuenta toda la lista de destinatarios.

* Número de propuestas a simular por cada destino.

   El destinatario recibe todas estas propuestas. Por ejemplo, si introduce 5, cada destinatario recibe un máximo de 5 propuestas de oferta.

   ![](assets/offer_simulation_009.png)

Para perfeccionar las ofertas que se tienen en cuenta en la simulación, se pueden añadir uno o varios temas (especificados previamente en las categorías).

También se puede optar por realizar la simulación en todas las ofertas o solo en las que están en línea. Si se desea, algunos filtros permiten modificar la selección.

>[!NOTE]
>
>Se debe especificar una fecha de contacto. Esto permite que el motor de interacción clasifique las ofertas en el entorno o categoría seleccionados. Si no se configura ninguna fecha, la simulación generará un error.

## Adición de ejes al sistema de informes {#adding-reporting-axes}

Se puede mejorar el análisis de la simulación añadiendo ejes de informe al destino o a las propias ofertas mediante la pestaña **[!UICONTROL Calculations]**.

Para ello, haga clic en el botón **[!UICONTROL Add]** y seleccione los campos adecuados. Los ejes se utilizan para determinar la simulación y se visualizan en el informe de análisis. Para obtener más información, consulte [Simulación de seguimiento](../../interaction/using/simulation-tracking.md).

![](assets/offer_simulation_011.png)
