---
title: Uso compartido con Adobe Experience Cloud
seo-title: Uso compartido con Adobe Experience Cloud
description: Uso compartido con Adobe Experience Cloud
seo-description: null
page-status-flag: never-activated
uuid: 24ac3463-69ab-48b4-85e0-4fe1948bf5ed
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: integrations
content-type: reference
topic-tags: audience-sharing
discoiquuid: 8f295058-5a78-4512-9bdf-d5f022457e10
translation-type: tm+mt
source-git-commit: 4b98c23f4120cbea6dd54cd68b61202e74bee3e1
workflow-type: tm+mt
source-wordcount: '245'
ht-degree: 61%

---


# Uso compartido con Adobe Experience Cloud{#sharing-audiences-with-adobe-experience-cloud}

>[!CAUTION]
>
>Para compartir audiencias con soluciones de Adobe Experience Cloud, debe implementar Adobe Identity Management System. [Obtenga más información sobre IMS](../../integrations/using/about-adobe-id.md).

Con Adobe Campaign, puede compartir audiencias y segmentos con soluciones y servicios principales de Adobe Experience Cloud. Hay dos opciones disponibles:

1. Enviar datos de segmentos de Adobe Experience Platform a Adobe Campaign. Para implementar esta integración, debe conectar su plataforma de datos del cliente en tiempo real con la Campaña (RTCDP). [Obtenga más información en esta sección](https://docs.adobe.com/content/help/es-ES/experience-platform/rtcdp/destinations/destinations-cat/adobe-destinations/adobe-campaign-destination.html).


1. Integrate **Adobe Campaign** with **People core service** (also known as **Profiles &amp; Audiences core service**) or Adobe Audience Manager. Esto le permite:

   * Importar audiencias y segmentos compartidos desde distintas soluciones de Adobe Experience Cloud a Adobe Campaign. Las audiencias se pueden importar mediante listas en Adobe Campaign.

   * Exportación de listas en la forma de audiencias compartidas de Adobe Experience Cloud. Estas audiencias pueden utilizarse con las diferentes soluciones de Adobe Experience Cloud que utiliza. Las audiencias se pueden exportar después de la segmentación en un flujo de trabajo con la actividad específica **[!UICONTROL Update shared audience]**.

Esta integración admite dos tipos de Adobe Experience Cloud ID:

* **ID de visitante**: este tipo de ID concilia los visitantes de Adobe Experience Cloud con los destinatarios de Adobe Campaign.
* **ID declarada**: este tipo de ID concilia todo tipo de datos con los elementos de la base de datos de Adobe Campaign. Se representa en Adobe Campaign como una clave de conciliación predefinida.
