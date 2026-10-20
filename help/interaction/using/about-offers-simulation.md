---
product: campaign
title: Acerca de la simulación de ofertas
description: Acerca de la simulación de ofertas
feature: Interaction, Offers
exl-id: facaa88e-1fa2-4189-9d8f-348aaef3e235
TQID: 'https://experienceleague.adobe.com/034-CFbQIFVm9QiSpDyRHlVsIrF46NSqKMwp-Gm3-mc'
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
    internal-label: Campaign
  - id: fd6e6e36-54e4-4f1a-96fc-1a750e400d50
    internal-label: Campaign Classic v7
feature_v2:
  - id: b6fcaf36-3bc4-4604-94f3-81b5d3f41ecf
    internal-label: Offer Management
  - id: 65702805-0026-5ca1-843a-144fa79f0883
    internal-label: Interaction
  - id: ea08db70-4682-59a2-9408-9aedd9548e07
    internal-label: Offers
topic_v2:
  - id: aa2f3246-cb95-4b30-8899-fdf7d73550cc
    internal-label: Reporting
  - id: bce87dde-a4ab-44c9-8a18-ad66e4ddb377
    internal-label: Customer experience
source-git-commit: 323ff901668895588a6e9587fa2a8b7804cf2fb4
workflow-type: ht
source-wordcount: '278'
ht-degree: 100%
---
# Acerca de la simulación de ofertas{#about-offers-simulation}



El módulo de **Simulation** permite probar la distribución de ofertas pertenecientes a una categoría o a un entorno antes de enviar la propuesta a los destinatarios.

La simulación tiene en cuenta los contextos y las reglas de elegibilidad aplicadas previamente a las ofertas (consulte [Información general del catálogo de ofertas](https://experienceleague.adobe.com/es/docs/campaign/campaign-v8/offers/interaction-offer-catalog){target="_blank"} [documentación de Campaign v8]), así como sus reglas de presentación (consulte [Administración de la presentación de ofertas](../../interaction/using/managing-offer-presentation.md)). Esto permite probar y perfeccionar varias versiones de la propuesta de oferta sin utilizar realmente una por encima o por debajo del objetivo, ya que la simulación no tiene ningún impacto en los destinatarios a los que va dirigida.

Para aprender a simular una oferta, lea los pasos a continuación.

![](assets/do-not-localize/how-to-video.png)[ También puede ver este vídeo](https://helpx.adobe.com/campaign/classic/how-to/simulate-offer-in-acv6.html?playlist=/ccx/v1/collection/product/campaign/classic/segment/digital-marketers/explevel/intermediate/applaunch/introduction/collection.ccx.js&ref=helpx.adobe.com).

## Pasos principales para crear una simulación {#main-steps-for-creating-a-simulation}

Para ejecutar una simulación de ofertas, siga los siguientes pasos:

1. En la pestaña **[!UICONTROL Profiles and Targets]**, haga clic en el vínculo **[!UICONTROL Simulations]** y, luego, haga clic en el botón **[!UICONTROL Create]**.

   ![](assets/offer_simulation_001.png)

1. Guarde y edite la simulación que acaba de crear.
1. Vaya a la pestaña **[!UICONTROL Edit]** y especifique la configuración de ejecución.

   Para obtener más información, consulte [Configurar una ejecución](../../interaction/using/execution-settings.md).

   ![](assets/offer_simulation_003.png)

   >[!NOTE]
   >
   >Los ajustes de ejecución solo están disponibles si se utiliza la interacción con Campaign.

1. Especifique el ámbito de la simulación.

   Para obtener más información, consulte [Definición del alcance](../../interaction/using/simulation-scope.md#definition-of-the-scope).

   ![](assets/offer_simulation_004.png)

1. Añada los ejes del sistema de informes para mejorar el informe **[!UICONTROL Offer distribution by rank]** (opcional).

   Para obtener más información, consulte [Adición de ejes al sistema de informes](../../interaction/using/simulation-scope.md#adding-reporting-axes).

   ![](assets/offer_simulation_005.png)

1. Haga clic en **[!UICONTROL Save]** para guardar los ajustes de la simulación.
1. Inicie la simulación a través del panel de control.

   ![](assets/offer_simulation_006.png)

1. Compruebe el resultado de la simulación y visualice el informe de análisis.

   Para obtener más información, consulte [Simulación de seguimiento](../../interaction/using/simulation-tracking.md).

   ![](assets/offer_simulation_007.png)
