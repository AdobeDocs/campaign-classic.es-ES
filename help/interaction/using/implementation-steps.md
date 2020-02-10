---
title: Pasos de implementación
seo-title: Pasos de implementación
description: Pasos de implementación
seo-description: null
page-status-flag: never-activated
uuid: 11582071-00a2-4245-af3e-bc81174ce223
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: interaction
content-type: reference
topic-tags: general-operation
discoiquuid: 7f79c0d8-77b0-4cc6-a888-7dbd32d2f3b6
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 20f835c357d016643ea1f3209ee4dfb6d3239f90

---


# Pasos de implementación{#implementation-steps}

## Configuración de la interacción {#configuring-interaction}

>[!NOTE]
>
>Los siguientes pasos debe realizarlos un perfil **Administrator** y solo en entornos de diseño.

1. Creación de perfiles de usuario. For more on this, refer to [Operator profiles](../../interaction/using/operator-profiles.md).
1. Creación de un entorno de oferta mediante la dimensión de segmentación. Para obtener más información sobre esto, consulte [Creación de un entorno](../../interaction/using/live-design-environments.md#creating-an-offer-environment)de ofertas.
1. Creación de reglas tipológicas para cada entorno. Para obtener más información sobre esto, consulte [Creación y referencia de una regla](../../interaction/using/managing-offer-presentation.md#creating-and-referencing-an-offer-presentation-rule)de presentación de ofertas.
1. Creación de espacios de oferta para cada entorno y configuración de funciones de renderización. Para obtener más información sobre esto, consulte [Creación de espacios](../../interaction/using/creating-offer-spaces.md)de ofertas.

   >[!NOTE]
   >
   >Si el espacio está definido mediante un canal unitario en modo identificado, se deben especificar los parámetros avanzados para este espacio.

1. Configuración del motor de oferta para interacciones entrantes a fin de presentar y actualizar una o varias ofertas.

   Los distintos modos de integración se detallan en [Acerca de los canales](../../interaction/using/about-inbound-channels.md)de entrada.

   >[!NOTE]
   >
   >Cuando se crea un espacio en el canal web entrante, también es preciso configurar el sitio en el que se visualizará la oferta.

## Gestión del catálogo de ofertas {#managing-the-offer-catalog-}

>[!NOTE]
>
>Los siguientes pasos debe realizarlos un **Offer manager**.

1. Creación de categorías de oferta en entornos de diseño. Para obtener más información sobre esto, consulte [Creación de categorías](../../interaction/using/creating-offer-categories.md)de ofertas.
1. Creación de ofertas en entornos de diseño. Para obtener más información sobre esto, consulte [Creación de una oferta](../../interaction/using/creating-an-offer.md).
1. Aprobación y publicación de ofertas en uno o varios espacios a fin de que estén disponibles en entornos interactivos para el gestor de envíos. Para obtener más información sobre esto, consulte [Aprobación y activación de una oferta](../../interaction/using/approving-and-activating-an-offer.md).

## Uso del catálogo de ofertas {#using-the-offer-catalog-}

>[!NOTE]
>
>Los siguientes pasos debe realizarlos un perfil **Delivery manager.** Sólo se pueden editar ofertas en entornos interactivos.

1. Creación de una campaña
1. Hacer referencia a una oferta en una campaña o en el envío de una campaña. For more on this, refer to [About outbound channels](../../interaction/using/about-outbound-channels.md).

