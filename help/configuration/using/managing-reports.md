---
solution: Campaign Classic
product: campaign
title: Administración de informes
description: Administración de informes
audience: configuration
content-type: reference
topic-tags: use-a-custom-recipient-table
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '144'
ht-degree: 4%

---


# Administración de informes{#managing-reports}

Los informes basados en un esquema específico de los destinatarios predeterminados de Adobe Campaign (nm:destinatario o esquema vinculados) deben redesarrollarse para tener en cuenta los datos de la tabla personalizada y sus tablas vinculadas mediante la asignación de destino (consulte la sección [Asignación de destino](../../configuration/using/target-mapping.md)).

Para crear nuevos informes, consulte [esta sección](../../reporting/using/about-reports-creation-in-campaign.md).

En algunos casos, también debe poner en marcha nuevos cubos específicos de estas tablas. Los cubos se detallan en [esta sección](../../reporting/using/about-cubes.md).

Se trata de los siguientes informes:

* **[!UICONTROL Recent proposition tracking]** (recentPropositions): seguimiento de propuestas en tiempo real.
* **[!UICONTROL Breakdown of opens]** (openByUserAgent): se abre desglosado según el software del usuario.
* **[!UICONTROL Statistics of the sharing activities]** (forwardActivities): análisis de compartir actividades, aperturas y suscripciones por período de tiempo.
* **[!UICONTROL Tracking indicators]** (mobileAppDeliveryFeedback): indicadores de seguimiento de un envío en una aplicación móvil.
* **[!UICONTROL Offer analysis]** (offerAnalysis): análisis de oferta por fecha y canal.
* **[!UICONTROL Reactivity rate]** (mobileAppDistribution): tasa de reactividad de los últimos envíos.
* **[!UICONTROL Breakdown of subscriptions]** (mobileAppDistribution): desglose de suscripciones activas por aplicación móvil.

