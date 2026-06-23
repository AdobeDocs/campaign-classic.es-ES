---
product: campaign
title: Uso compartido con Adobe Experience Cloud
description: Uso compartido con Adobe Experience Cloud
feature: Audiences
badge-v8: label="También se aplica a v8" type="Positive" tooltip="También se aplica a Campaign v8"
audience: integrations
content-type: reference
topic-tags: audience-sharing
exl-id: 1c90e913-3375-476c-ab60-89f20239eb0d
TQID: https://experienceleague.adobe.com/MGzMyGtmzaVGZy6oWHcirPPdSSpu9YYcuR30KIVZ9bc
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
feature_v2:
  - id: d5ef99fa-df0c-4153-bf94-105ad0724167
subfeature_v2:
  - id: cbcf4d90-26be-46e2-b16a-aebc529dc41e
  - id: df0d6518-6f49-46e2-b46e-3bcc513f553f
  - id: eb007b6d-6e57-46ab-9485-3f24d6102304
  - id: b1fd1501-3105-4d6b-b4d4-9af53126df75
source-git-commit: 38eab6b8da73163e4476e91c0ef73f25c3f57546
workflow-type: ht
source-wordcount: 253
ht-degree: 100%

---

# Uso compartido con Adobe Experience Cloud {#sharing-audiences-with-adobe-experience-cloud}


>[!CAUTION]
>
>Para compartir públicos con las soluciones de Adobe Experience Cloud, debe implementar Adobe Identity Management System. [Obtenga más información sobre IMS](../../integrations/using/about-adobe-id.md).

Con Adobe Campaign, puede compartir públicos y segmentos con los servicios de Adobe Experience Cloud. Hay dos opciones disponibles:

1. Enviar datos de segmentos de Adobe Experience Platform a Adobe Campaign. Para implementar esta integración, debe conectar su plataforma de datos del cliente en tiempo real (RTCDP) con Campaign. [Obtenga más información en esta sección](https://experienceleague.adobe.com/docs/experience-platform/destinations/catalog/email-marketing/adobe-campaign.html?lang=es#catalog){target="_blank"}.

1. Integre **Adobe Campaign** con **Experience Cloud Audiences** o **Adobe Audience Manager**. Esto le permite:

   * Importar públicos y segmentos compartidos desde distintas soluciones de Adobe Experience Cloud a Adobe Campaign. Los públicos se pueden importar mediante listas en Adobe Campaign.

   * Exportación de listas en la forma de públicos compartidos de Adobe Experience Cloud. Estos públicos pueden utilizarse con las diferentes soluciones de Adobe Experience Cloud que utiliza. Los públicos se pueden exportar después de la segmentación en un flujo de trabajo con la actividad específica **[!UICONTROL Update shared audience]**.

Esta integración es compatible con dos tipos de ID de Adobe Experience Cloud:

* **ID de visitante**: este tipo de identificador reconcilia los visitantes de Adobe Experience Cloud con los destinatarios de Adobe Campaign.
* **ID declarada**: este tipo de identificador reconcilia todo tipo de datos con los elementos de la base de datos de Adobe Campaign. Se representa en Adobe Campaign como una clave de reconciliación predefinida.

  >[!NOTE]
  >
  > Ahora, la fuente de datos de ID declarada también se puede utilizar con la integración de Experience Cloud Assets.
  >
