---
title: Administración de informes
seo-title: Administración de informes
description: Administración de informes
seo-description: null
page-status-flag: never-activated
uuid: 3b8e6f11-4cbd-450e-871b-50fd0ead96db
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: configuration
content-type: reference
topic-tags: use-a-custom-recipient-table
discoiquuid: 21777423-0c8a-4bb1-b210-972f660648bd
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 20f835c357d016643ea1f3209ee4dfb6d3239f90

---


# Administración de informes{#managing-reports}

Los informes basados en un esquema específico de los destinatarios predeterminados de Adobe Campaign (nm:destinatario o esquema vinculado) deben redesarrollarse para tener en cuenta los datos de la tabla personalizada y sus tablas vinculadas mediante la asignación de objetivos (consulte la sección Asignación [de](../../configuration/using/target-mapping.md) Target).

Para crear nuevos informes, consulte [esta sección](../../reporting/using/about-reports-creation-in-campaign.md).

En algunos casos, también debe colocar nuevos cubos específicos de estas tablas. Cubes are detailed in [this section](../../reporting/using/about-cubes.md).

Se trata de los siguientes informes:

* **[!UICONTROL Recent proposition tracking]** (recentPropositions): seguimiento de propuestas en tiempo real.
* **[!UICONTROL Breakdown of opens]** (openByUserAgent): se abre desglosado según el software del usuario.
* **[!UICONTROL Statistics of the sharing activities]** (forwardActivities): análisis de actividades de uso compartido, aperturas y suscripciones por período de tiempo.
* **[!UICONTROL Tracking indicators]** (mobileAppDeliveryFeedback): indicadores de seguimiento para una entrega en una aplicación móvil.
* **[!UICONTROL Offer analysis]** (offerAnalysis): análisis de ofertas por fecha y canal.
* **[!UICONTROL Reactivity rate]** (mobileAppDistribution): tasa de reactividad de los últimos envíos.
* **[!UICONTROL Breakdown of subscriptions]** (mobileAppDistribution): desglose de las suscripciones activas por aplicación móvil.

