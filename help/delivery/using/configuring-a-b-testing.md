---
product: campaign
title: Configuración de las pruebas A/B
description: Obtenga información sobre cómo configurar las pruebas A/B en Campaign
badge-v8: label="También se aplica a v8" type="Positive" tooltip="También se aplica a Campaign v8"
feature: A/B Testing
role: User
exl-id: 6adf2e75-63b1-44ad-8925-03beb3bc0bdd
TQID: https://experienceleague.adobe.com/PHIsuJZ-o5mBRAPggyVYdzS7PBXL9GYCBc6Fr56ur5Q
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
feature_v2:
  - id: b631758a-142d-425f-b9aa-f756d85cb979
  - id: c858a28b-ea19-49b0-8d48-828717fad89c
subfeature_v2:
  - id: e95a583b-fcfa-4524-8666-46a29c828119
  - id: c8da4fdd-eb94-4751-a43c-f82733fb2d6e
  - id: d5bbe3da-ba85-4242-817e-54f7c4b943e0
  - id: f4da0e76-df77-451e-ad61-21afb7bd8810
source-git-commit: 38eab6b8da73163e4476e91c0ef73f25c3f57546
workflow-type: tm+mt
source-wordcount: 260
ht-degree: 100%

---

# Configuración de las pruebas A/B {#configuring-a-b-testing}

En esta sección, se explica cómo crear un flujo de trabajo para realizar pruebas A/B.

1. Cree un nuevo flujo de trabajo y, luego, configure una actividad de consulta para dirigirse a la población destinataria. Consulte la [documentación de Campaign v8](https://experienceleague.adobe.com/docs/campaign/automation/workflows/wf-activities/targeting-activities/query.html?lang=es){target="_blank"}.

1. Añada una actividad de división para dividir la población de destino en varios subconjuntos. Consulte la [documentación de Campaign v8](https://experienceleague.adobe.com/docs/campaign/automation/workflows/wf-activities/targeting-activities/split.html?lang=es){target="_blank"}.

1. Abra la actividad y configure cada subconjunto según sus necesidades. Para obtener más información sobre cómo configurar una actividad **[!UICONTROL Split]**, consulte [esta sección](../../workflow/using/split.md).

   En este ejemplo, queremos probar dos temas nuevos para una newsletter presentando cada uno de ellos al 10 % de la población objetivo.

   ![](assets/ab-testing-split.png)

1. Añada una transición para enviar a la población restante la newsletter con el asunto actual. Para ello, active la opción **[!UICONTROL Generate complement]** en la pestaña **[!UICONTROL General]**.

   ![](assets/ab-testing-complement.png)

1. Para cada subconjunto, añada la versión del envío que se va a probar.

   ![](assets/ab-testing-delivery.png)

Ahora puede iniciar el flujo de trabajo. Una vez enviadas las entregas, podrá rastrear el comportamiento de los tres subconjuntos en los registros de envío, para ver qué asunto ha tenido más éxito.

Los flujos de trabajo también le permiten automatizar los procesos al identificar automáticamente la variante de envío que tuvo un mejor rendimiento y, a continuación, enviarla a la población restante. Para obtener más información al respecto, consulte este [caso de uso paso a paso](a-b-testing-use-case.md).
