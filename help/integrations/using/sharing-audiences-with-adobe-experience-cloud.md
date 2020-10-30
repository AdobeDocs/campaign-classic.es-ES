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
translation-type: ht
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: ht
source-wordcount: '216'
ht-degree: 100%

---


# Uso compartido con Adobe Experience Cloud{#sharing-audiences-with-adobe-experience-cloud}

>[!NOTE]
>
>El uso de esta integración requiere la implementación del IMS. Consulte la sección sobre [IMS](../../integrations/using/about-adobe-id.md).

Adobe Campaign permite intercambiar y compartir audiencias y segmentos con las soluciones y servicios básicos de Adobe Experience Cloud. Para ello, debe integrar **Adobe Campaign** con el **servicio principal Personas** (también conocido como **servicio principal Perfiles y audiencias**) o Adobe Audience Manager. Esto le permite:

* Importar audiencias y segmentos compartidos desde distintas soluciones de Adobe Experience Cloud a Adobe Campaign. Las audiencias se pueden importar mediante listas en Adobe Campaign.
* Exportación de listas en la forma de audiencias compartidas de Adobe Experience Cloud. Estas audiencias pueden utilizarse con las diferentes soluciones de Adobe Experience Cloud que utiliza. Las audiencias se pueden exportar después de la segmentación en un flujo de trabajo con la actividad específica **[!UICONTROL Update shared audience]**.

>[!CAUTION]
>
>Según el tipo de datos, la importación de audiencias en Adobe Campaign puede estar sujeta a restricciones legales.

La integración es compatible con dos tipos de Adobe ID Experience Cloud:

* **ID de visitante**: este tipo de ID concilia los visitantes de Adobe Experience Cloud con los destinatarios de Adobe Campaign.
* **ID declarada**: este tipo de ID concilia todo tipo de datos con los elementos de la base de datos de Adobe Campaign. Se representa en Adobe Campaign como una clave de conciliación predefinida.
