---
product: campaign
title: Servidor de mensajería
description: Servidor de mensajería
feature: Installation, Instance Settings
badge-v7-prem: label="On-premise/hybrid only" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=es" tooltip="Applies to on-premise and hybrid deployments only"
audience: installation
content-type: reference
topic-tags: prerequisites-and-recommendations-
exl-id: d9ffa58d-81e3-4291-8502-3cb7c326b666
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
    internal-label: Campaign
  - id: fd6e6e36-54e4-4f1a-96fc-1a750e400d50
    internal-label: Campaign Classic v7
feature_v2:
  - id: 7f0a1ee5-eeb8-5478-a9cd-b1896f033118
    internal-label: Instance Settings
  - id: c5474392-5419-4296-9e41-f6f4ce4f6e9b
    internal-label: Administration
subfeature_v2:
  - id: e656c701-3899-4db3-989c-de0980ddfffa
    internal-label: Installation
source-git-commit: a43e591a565a18d79f583d975e3e812c5435b0c0
workflow-type: tm+mt
source-wordcount: '186'
ht-degree: 12%
---
# Servidor de mensajería{#messaging-server}



Adobe Campaign gestiona el correo electrónico saliente de forma nativa, aunque se necesita un servidor de correo electrónico tradicional para recibir mensajes entrantes vinculados al correo electrónico devuelto (de demonios de mailer). La aplicación procesará automáticamente los buzones configurados en este servidor.

Todos los servidores configurados para el acceso POP3 pueden utilizarse para recibir el correo devuelto si conservan los encabezados &quot;Message-ID&quot; de SMTP al recoger el correo. Por ejemplo, las implementaciones que utilizan Qmail, SendMail y Microsoft Exchange están actualmente en producción. Sin embargo, algunas instalaciones de Lotus Notes/domino revelaron un problema con el mantenimiento de los encabezados &quot;Message-Id&quot;.

>[!CAUTION]
>
>Es posible que este servidor de correo tenga que gestionar cargas pesadas: en las fases iniciales, las listas típicas pueden producir tasas de devolución de hasta el 10 % (si envía 100 000 mensajes, espera recibir 10 000 devoluciones).
>
>Por este motivo, recomendamos no utilizar el servidor de mensajería de su empresa para esta tarea, ya que puede verse muy afectada.
>
>Se recomienda configurar un subdominio específico de su DNS y un servidor dedicado para el correo rechazado.
