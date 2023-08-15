---
product: campaign
title: Servidor de mensajería
description: Servidor de mensajería
feature: Installation, Instance Settings
badge-v7-only: label="v7" type="Informative" tooltip="Se aplica solo a Campaign Classic v7"
badge-v7-prem: label="on-premise e híbrido" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=es" tooltip="Se aplica solo a implementaciones On-premise e híbridas"
audience: installation
content-type: reference
topic-tags: prerequisites-and-recommendations-
exl-id: d9ffa58d-81e3-4291-8502-3cb7c326b666
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: tm+mt
source-wordcount: '187'
ht-degree: 15%

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
