---
product: campaign
title: Acerca de la configuración inicial
description: Acerca de la configuración inicial
feature: Installation, Configuration
badge-v7-prem: label="On-Premise e híbrido" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=es" tooltip="Se aplica solo a implementaciones On-premise e híbridas"
audience: installation
content-type: reference
topic-tags: initial-configuration
exl-id: f77ba178-0dfb-4a2e-b33b-971765d42298
source-git-commit: b666535f7f82d1b8c2da4fbce1bc25cf8d39d187
workflow-type: tm+mt
source-wordcount: '177'
ht-degree: 10%

---

# Pasos clave para configurar e implementar su instancia{#about-initial-configuration}



Una vez finalizada la instalación de Adobe Campaign, debe configurarla para asegurarse de que funciona de forma eficaz con sus restricciones y arquitectura técnica. Los pasos para configurar una instancia de Adobe Campaign se detallan en este capítulo, en la siguiente secuencia:

1. Cree la instancia y la conexión relacionada, consulte [Creación de una instancia e inicio de sesión](../../installation/using/creating-an-instance-and-logging-on.md).
1. Crear y configurar la base de datos, consulte [Creación y configuración de la base de datos](../../installation/using/creating-and-configuring-the-database.md).
1. Configure el servidor de Adobe Campaign, consulte [Configuración del servidor de Campaign](../../installation/using/configuring-campaign-server.md).
1. Implemente la instancia, consulte [Implementación de una instancia](../../installation/using/deploying-an-instance.md).

Configurar la instancia implica habilitar procesos (web, mta, wfserver, etc.) para iniciarse en el servidor y configurar módulos para enviar correo electrónico, para seguimiento, etc. Para cada instancia, los procesos de Adobe Campaign se activan en el servidor. Para obtener más información, consulte [esta sección](../../installation/using/configuring-campaign-server.md#enabling-processes).

Se pueden requerir configuraciones adicionales para cada instancia (según los módulos utilizados, la arquitectura y las necesidades) para optimizar el funcionamiento de Adobe Campaign.
