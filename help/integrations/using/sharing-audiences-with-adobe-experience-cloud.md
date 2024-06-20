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
source-git-commit: b11185da8236d6100d98eabcc9dc1cf2cffa70af
workflow-type: tm+mt
source-wordcount: '242'
ht-degree: 81%

---

# Los distintos estados se actualizan en el panel de ofertas. {#sharing-audiences-with-adobe-experience-cloud}


>[!CAUTION]
>
>Para compartir audiencias con las soluciones de Adobe Experience Cloud, debe implementar Adobe Identity Management System. [Obtenga más información sobre IMS](../../integrations/using/about-adobe-id.md).

Con Adobe Campaign, puede compartir audiencias y segmentos con los servicios de Adobe Experience Cloud. Hay dos opciones disponibles:

1. Enviar datos de segmentos de Adobe Experience Platform a Adobe Campaign. Para implementar esta integración, debe conectar su plataforma de datos del cliente en tiempo real (RTCDP) con Campaign. [Obtenga más información en esta sección](https://experienceleague.adobe.com/docs/experience-platform/destinations/catalog/email-marketing/adobe-campaign.html?lang=es#catalog){target="_blank"}.

1. Integrar **Adobe Campaign** con  **Audiencias de Experience Cloud** o **Adobe Audience Manager**. Esto le permite:

   * Importar audiencias y segmentos compartidos desde distintas soluciones de Adobe Experience Cloud a Adobe Campaign. Las audiencias se pueden importar mediante listas en Adobe Campaign.

   * Exportación de listas en la forma de audiencias compartidas de Adobe Experience Cloud. Estas audiencias pueden utilizarse con las diferentes soluciones de Adobe Experience Cloud que utiliza. Las audiencias se pueden exportar después de la segmentación en un flujo de trabajo con la actividad específica **[!UICONTROL Update shared audience]**.

Esta integración es compatible con dos tipos de ID de Adobe Experience Cloud:

* **ID de visitante**: este tipo de identificador reconcilia los visitantes de Adobe Experience Cloud con los destinatarios de Adobe Campaign.
* **ID declarada**: este tipo de identificador reconcilia todo tipo de datos con los elementos de la base de datos de Adobe Campaign. Se representa en Adobe Campaign como una clave de reconciliación predefinida.

  >[!NOTE]
  >
  > Ahora, la fuente de datos de ID declarado también se puede utilizar con la integración de Experience Cloud Assets.
  >
