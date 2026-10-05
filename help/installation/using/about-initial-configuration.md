---
product: campaign
title: Acerca de la configuración inicial
description: Acerca de la configuración inicial
feature: Installation, Configuration
badge-v7-prem: label="On-premise/hybrid only" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=es" tooltip="Applies to on-premise and hybrid deployments only"
audience: installation
content-type: reference
topic-tags: initial-configuration
exl-id: f77ba178-0dfb-4a2e-b33b-971765d42298
TQID: 'https://experienceleague.adobe.com/rQT-wcpjGzyYfEV3thGlY0WD7Po-A08yD0pGMr13p7s'
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
    internal-label: Campaign
  - id: fd6e6e36-54e4-4f1a-96fc-1a750e400d50
    internal-label: Campaign Classic v7
feature_v2:
  - id: c5474392-5419-4296-9e41-f6f4ce4f6e9b
    internal-label: Administration
subfeature_v2:
  - id: e656c701-3899-4db3-989c-de0980ddfffa
    internal-label: Installation
  - id: a14877cc-63b1-41d9-bf0b-5f97cadd0417
    internal-label: Configuration guidelines
source-git-commit: a43e591a565a18d79f583d975e3e812c5435b0c0
workflow-type: tm+mt
source-wordcount: '185'
ht-degree: 14%
---
# Pasos clave para configurar e implementar su instancia{#about-initial-configuration}



Una vez finalizada la instalación de Adobe Campaign, debe configurarla para asegurarse de que funciona de forma eficaz con sus restricciones y arquitectura técnica. Los pasos para configurar una instancia de Adobe Campaign se detallan en este capítulo, en la siguiente secuencia:

1. Cree la instancia y la conexión relacionada, consulte [Crear una instancia e iniciar sesión](../../installation/using/creating-an-instance-and-logging-on.md).
1. Cree y configure la base de datos, consulte [Creación y configuración de la base de datos](../../installation/using/creating-and-configuring-the-database.md).
1. Configure el servidor de Adobe Campaign, consulte [Configuración del servidor de Campaign](../../installation/using/configuring-campaign-server.md).
1. Implementar la instancia, consulte [Implementación de una instancia](../../installation/using/deploying-an-instance.md).

Configurar la instancia implica habilitar procesos (web, mta, wfserver, etc.) para iniciarse en el servidor y configurar módulos para enviar correo electrónico, para seguimiento, etc. Para cada instancia, los procesos de Adobe Campaign se activan en el servidor. Para obtener más información, consulte [esta sección](../../installation/using/configuring-campaign-server.md#enabling-processes).

Se pueden requerir configuraciones adicionales para cada instancia (según los módulos utilizados, la arquitectura y las necesidades) para optimizar el funcionamiento de Adobe Campaign.
