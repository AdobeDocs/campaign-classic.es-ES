---
title: Ámbito de la simulación
seo-title: Ámbito de la simulación
description: Ámbito de la simulación
seo-description: null
page-status-flag: never-activated
uuid: d3145926-0a7e-455f-9b93-55be1b2a0518
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: interaction
content-type: reference
topic-tags: simulating-offers
discoiquuid: ef658468-e20b-45d9-a714-c152e55c1c79
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 20f835c357d016643ea1f3209ee4dfb6d3239f90

---


# Ámbito de la simulación{#simulation-scope}

## Definición del ámbito {#definition-of-the-scope}

Open the **[!UICONTROL Scope]** tab to choose your settings.

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

You can enhance the simulation analysis by adding reporting axes on the target or the offers themselves via the **[!UICONTROL Calculations]** tab.

To do this, click the **[!UICONTROL Add]** button and choose the appropriate fields. Los ejes se utilizan para determinar la simulación y se visualizan en el informe de análisis. For more on this, refer to [Simulation tracking](../../interaction/using/simulation-tracking.md).

![](assets/offer_simulation_011.png)

