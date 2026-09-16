---
product: campaign
title: Restauración
description: Restauración
feature: Monitoring
badge-v7-prem: label="On-premise/hybrid only" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=es" tooltip="Applies to on-premise and hybrid deployments only"
audience: production
content-type: reference
topic-tags: data-processing
exl-id: ba4db1af-778c-4c34-9a3c-49f41faa49b5
TQID: https://experienceleague.adobe.com/ZXUhBpNXWOjaLlJ0U1ToxAi9HlC0AKenRKIIu0z-63c
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
    internal-label: Campaign
feature_v2: []
subfeature_v2:
  - id: c03a11ff-bdf9-4e5b-b279-f468b4293464
    internal-label: Performance Monitoring
  - id: e519a22f-a06a-42fc-9d09-d78a3ab2c434
    internal-label: Monitoring guidelines
source-git-commit: 38eab6b8da73163e4476e91c0ef73f25c3f57546
workflow-type: tm+mt
source-wordcount: '84'
ht-degree: 25%
---
# Restauración{#restoration}



En un servidor limpio, el procedimiento de restauración es el siguiente:

* en un sistema operativo instalado y configurado (redes),
* instalar aplicaciones de terceros: servidor web, JDK (si es necesario),
* instalar binarios de Adobe Campaign con la misma compilación que el sistema de origen,
* copiar archivos de configuración, registros de seguimiento y archivos de redirección,
* crear y reconstruir la base de datos,
* inicie Adobe Campaign.

Para obtener más información, consulte la **Guía de instalación**.
