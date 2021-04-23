---
solution: Campaign Classic
product: campaign
title: Uso compartido con Adobe Experience Cloud
description: Uso compartido con Adobe Experience Cloud
audience: integrations
content-type: reference
topic-tags: audience-sharing
exl-id: 1c90e913-3375-476c-ab60-89f20239eb0d
translation-type: ht
source-git-commit: 6854d06f8dc445b56ddfde7777f02916a60f2b63
workflow-type: ht
source-wordcount: '305'
ht-degree: 100%

---

# Uso compartido con Adobe Experience Cloud{#sharing-audiences-with-adobe-experience-cloud}

>[!CAUTION]
>
>Para compartir audiencias con las soluciones de Adobe Experience Cloud, debe implementar Adobe Identity Management System. [Obtenga más información sobre IMS](../../integrations/using/about-adobe-id.md).

Con Adobe Campaign, puede compartir audiencias y segmentos con las soluciones y los servicios principales de Adobe Experience Cloud. Hay dos opciones disponibles:

1. Enviar datos de segmentos de Adobe Experience Platform a Adobe Campaign. Para implementar esta integración, debe conectar su plataforma de datos del cliente en tiempo real (RTCDP) con Campaign. [Obtenga más información en esta sección](https://docs.adobe.com/content/help/es-ES/experience-platform/rtcdp/destinations/destinations-cat/adobe-destinations/adobe-campaign-destination.html).


1. Integre **Adobe Campaign** con el **servicio principal Personas** (también conocido como **servicio principal Perfiles y audiencias**) o Adobe Audience Manager. Esto le permite:

   * Importar audiencias y segmentos compartidos desde distintas soluciones de Adobe Experience Cloud a Adobe Campaign. Las audiencias se pueden importar mediante listas en Adobe Campaign.

   * Exportación de listas en la forma de audiencias compartidas de Adobe Experience Cloud. Estas audiencias pueden utilizarse con las diferentes soluciones de Adobe Experience Cloud que utiliza. Las audiencias se pueden exportar después de la segmentación en un flujo de trabajo con la actividad específica **[!UICONTROL Update shared audience]**.

Esta integración es compatible con dos tipos de Adobe ID Experience Cloud:

* **ID de visitante**: este tipo de ID concilia los visitantes de Adobe Experience Cloud con los destinatarios de Adobe Campaign.
* **ID declarada**: este tipo de ID concilia todo tipo de datos con los elementos de la base de datos de Adobe Campaign. Se representa en Adobe Campaign como una clave de conciliación predefinida.

   >[!NOTE]
   >
   > Ahora, la fuente de datos de ID declarado también se puede utilizar con la integración del servicio principal Personas.
   >
   >Si utiliza la integración del servicio principal Personas y desea añadir la integración de Audience Manager, necesitará la ayuda de un consultor de Adobe Audience Manager para evitar perder todas las sincronizaciones de ID recopiladas al realizar la transición al uso de esta fuente de datos de ID declarados en un contexto de Adobe Audience Manager.
