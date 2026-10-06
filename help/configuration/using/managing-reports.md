---
product: campaign
title: Administrar informes
description: Administrar informes
feature: Reporting, Configuration
role: Developer
badge-v8: label="Also applies to v8" type="Positive" tooltip="Also applies to Campaign v8"
exl-id: 68908664-3cf6-4a6c-a327-c7f059c27aa3
TQID: 'https://experienceleague.adobe.com/LA4v5oODC9n5K2Ttox9SF7lwcGQOU7IDEvL1P4Sls-4'
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
    internal-label: Campaign
  - id: fd6e6e36-54e4-4f1a-96fc-1a750e400d50
    internal-label: Campaign Classic v7
feature_v2:
  - id: c309ee4e-82e4-4f7e-b608-ef345678c34e
    internal-label: Dynamic reporting
  - id: c5474392-5419-4296-9e41-f6f4ce4f6e9b
    internal-label: Administration
subfeature_v2:
  - id: b3a4149f-2b3a-44d1-894e-e3ac4c77fb47
    internal-label: Reporting interface
  - id: a14877cc-63b1-41d9-bf0b-5f97cadd0417
    internal-label: Configuration guidelines
role_v2:
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
topic_v2:
  - id: aa2f3246-cb95-4b30-8899-fdf7d73550cc
    internal-label: Reporting
source-git-commit: a43e591a565a18d79f583d975e3e812c5435b0c0
workflow-type: tm+mt
source-wordcount: '145'
ht-degree: 4%
---
# Administrar informes{#managing-reports}



Los informes basados en un esquema específico de los destinatarios de Adobe Campaign predeterminados (nm:recipient o esquema vinculado) deben volver a desarrollarse para tener en cuenta los datos de la tabla personalizada y sus tablas vinculadas mediante la asignación de destino (consulte la sección [Asignación de destino](../../configuration/using/target-mapping.md) ).

Para crear nuevos informes, consulte [esta sección](../../reporting/using/about-reports-creation-in-campaign.md).

En algunos casos, también debe colocar nuevos cubos específicos de estas tablas. Los cubos están detallados en [esta sección](../../reporting/using/ac-cubes.md).

Los siguientes informes son motivo de preocupación:

* **[!UICONTROL Recent proposition tracking]** (recentPropositions): seguimiento de propuestas en tiempo real.
* **[!UICONTROL Breakdown of opens]** (opensByUserAgent): se abre desglosado según el software del usuario.
* **[!UICONTROL Statistics of the sharing activities]** (forwardActivities): análisis de las actividades de uso compartido, las aperturas y las suscripciones por periodo.
* **[!UICONTROL Tracking indicators]** (mobileAppDeliveryFeedback): indicadores de seguimiento para un envío en una aplicación móvil.
* **[!UICONTROL Offer analysis]** (offerAnalysis): análisis de ofertas por fecha y canal.
* **[!UICONTROL Reactivity rate]** (mobileAppDistribution): tasa de reacción de los envíos más recientes.
* **[!UICONTROL Breakdown of subscriptions]** (mobileAppDistribution): desglose de suscripciones activas por aplicación móvil.
