---
solution: Campaign Classic
product: campaign
title: Pasos de implementación
description: Pasos de implementación
audience: interaction
content-type: reference
topic-tags: general-operation
exl-id: 82b88ab7-6a95-4bb3-b8b3-abea0fdd4ca0
translation-type: ht
source-git-commit: 6854d06f8dc445b56ddfde7777f02916a60f2b63
workflow-type: ht
source-wordcount: '284'
ht-degree: 100%

---

# Pasos de implementación{#implementation-steps}

## Configuración de la interacción {#configuring-interaction}

>[!NOTE]
>
>Los siguientes pasos debe realizarlos un perfil **Administrator** y solo en entornos de diseño.

1. Creación de perfiles de usuario. Para obtener más información, consulte [Perfiles de operadores](../../interaction/using/operator-profiles.md).
1. Creación de un entorno de oferta mediante la dimensión de segmentación. Para obtener más información, consulte [Creación de un entorno de ofertas](../../interaction/using/live-design-environments.md#creating-an-offer-environment).
1. Creación de reglas tipológicas para cada entorno. Para obtener más información, consulte [Creación y referencia de una regla de presentación de ofertas](../../interaction/using/managing-offer-presentation.md#creating-and-referencing-an-offer-presentation-rule). 
1. Creación de espacios de oferta para cada entorno y configuración de funciones de renderización. Para obtener más información, consulte [Creación de espacios de ofertas](../../interaction/using/creating-offer-spaces.md).

   >[!NOTE]
   >
   >Si el espacio está definido mediante un canal unitario en modo identificado, se deben especificar los parámetros avanzados para este espacio.

1. Configuración del motor de oferta para interacciones entrantes a fin de presentar y actualizar una o varias ofertas.

   Los distintos modos de integración se detallan en [Acerca de los canales de entrada](../../interaction/using/about-inbound-channels.md).

   >[!NOTE]
   >
   >Cuando se crea un espacio en el canal web entrante, también es preciso configurar el sitio en el que se visualizará la oferta.

## Gestión del catálogo de ofertas {#managing-the-offer-catalog-}

>[!NOTE]
>
>Los siguientes pasos debe realizarlos un **Offer manager**.

1. Creación de categorías de oferta en entornos de diseño. Para obtener más información, consulte [Creación de categorías de oferta](../../interaction/using/creating-offer-categories.md).
1. Creación de ofertas en entornos de diseño. Para obtener más información, consulte [Creación de una oferta](../../interaction/using/creating-an-offer.md).
1. Aprobación y publicación de ofertas en uno o varios espacios a fin de que estén disponibles en entornos interactivos para el gestor de envíos. Para obtener más información, consulte [Aprobación y activación de una oferta](../../interaction/using/approving-and-activating-an-offer.md).

## Uso del catálogo de ofertas {#using-the-offer-catalog-}

>[!NOTE]
>
>Los siguientes pasos debe realizarlos un perfil **Delivery manager.** Sólo se pueden editar ofertas en entornos interactivos.

1. Creación de una campaña
1. Hacer referencia a una oferta en una campaña o en la entrega de una campaña. Para obtener más información, consulte [Sobre canales salientes](../../interaction/using/about-outbound-channels.md).
