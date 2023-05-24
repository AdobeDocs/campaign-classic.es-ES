---
product: campaign
title: Administrar informes
description: Administrar informes
badge-v7: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7"
badge-v8: label="v8" type="Positive" tooltip="Also applies to Campaign v8"
exl-id: 68908664-3cf6-4a6c-a327-c7f059c27aa3
source-git-commit: 6dc6aeb5adeb82d527b39a05ee70a9926205ea0b
workflow-type: tm+mt
source-wordcount: '144'
ht-degree: 4%

---

# Administrar informes{#managing-reports}



Los informes basados en un esquema específico de los destinatarios predeterminados de Adobe Campaign (nm:recipient o schema linked) deben volver a desarrollarse para tener en cuenta los datos de la tabla personalizada y sus tablas vinculadas a través de la asignación de destino (consulte la [Asignación de destino](../../configuration/using/target-mapping.md) ).

Para crear nuevos informes, consulte [esta sección](../../reporting/using/about-reports-creation-in-campaign.md).

En algunos casos, también debe colocar nuevos cubos específicos de estas tablas. Los cubos se detallan en [esta sección](../../reporting/using/ac-cubes.md).

Los siguientes informes son motivo de preocupación:

* **[!UICONTROL Recent proposition tracking]** (recentPropositions): seguimiento de propuestas en tiempo real.
* **[!UICONTROL Breakdown of opens]** (opensByUserAgent): se abre desglosado según el software del usuario.
* **[!UICONTROL Statistics of the sharing activities]** (forwardActivities): análisis de actividades de difusión, aperturas y suscripciones por periodo.
* **[!UICONTROL Tracking indicators]** (mobileAppDeliveryFeedback): indicadores de seguimiento para un envío en una aplicación móvil.
* **[!UICONTROL Offer analysis]** (offerAnalysis): análisis de ofertas por fecha y canal.
* **[!UICONTROL Reactivity rate]** (mobileAppDistribution): tasa de reacción de los envíos más recientes.
* **[!UICONTROL Breakdown of subscriptions]** (mobileAppDistribution): desglose de suscripciones activas por aplicación móvil.
