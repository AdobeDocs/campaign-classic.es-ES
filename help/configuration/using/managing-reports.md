---
product: campaign
title: Administración de informes
description: Administración de informes
audience: configuration
content-type: reference
topic-tags: use-a-custom-recipient-table
exl-id: 68908664-3cf6-4a6c-a327-c7f059c27aa3
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: tm+mt
source-wordcount: '144'
ht-degree: 4%

---

# Administración de informes{#managing-reports}

Los informes basados en un esquema específico para los destinatarios predeterminados de Adobe Campaign (nm:recipient o esquema vinculado) deben redesarrollarse para tener en cuenta los datos de la tabla personalizada y sus tablas vinculadas a través de la asignación de destino (consulte la sección [Target mapping](../../configuration/using/target-mapping.md) ).

Para crear nuevos informes, consulte [esta sección](../../reporting/using/about-reports-creation-in-campaign.md).

En algunos casos, también debe colocar nuevos cubos específicos de estas tablas. Los cubos se detallan en [esta sección](../../reporting/using/about-cubes.md).

Los siguientes informes se refieren a:

* **[!UICONTROL Recent proposition tracking]** (recentPropositions): seguimiento de propuestas en tiempo real.
* **[!UICONTROL Breakdown of opens]** (opensByUserAgent): se abre desglosado según el software del usuario.
* **[!UICONTROL Statistics of the sharing activities]** (forwardActivities): análisis de actividades de difusión en redes, aperturas y suscripciones por periodo.
* **[!UICONTROL Tracking indicators]** (mobileAppDeliveryFeedback): indicadores de seguimiento para una entrega en una aplicación móvil.
* **[!UICONTROL Offer analysis]** (offerAnalysis): análisis de ofertas por fecha y canal.
* **[!UICONTROL Reactivity rate]** (mobileAppDistribution): tasa de reacción de los envíos más recientes.
* **[!UICONTROL Breakdown of subscriptions]** (mobileAppDistribution): desglose de suscripciones activas por aplicación móvil.
