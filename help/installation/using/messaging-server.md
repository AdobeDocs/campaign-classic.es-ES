---
product: campaign
title: Servidor de mensajería
description: Servidor de mensajería
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
badge-v7-prem: label="on-premise & hybrid" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=en" tooltip="Applies to on-premise and hybrid deployments only"
audience: installation
content-type: reference
topic-tags: prerequisites-and-recommendations-
exl-id: d9ffa58d-81e3-4291-8502-3cb7c326b666
source-git-commit: a5762cd21a1a6d5a5f3a10f53a5d1f43542d99d4
workflow-type: tm+mt
source-wordcount: '162'
ht-degree: 3%

---

# Servidor de mensajería{#messaging-server}



Adobe Campaign gestiona el correo electrónico saliente de forma nativa, pero se necesita un servidor de correo electrónico tradicional para recibir mensajes entrantes vinculados al correo electrónico devuelto (de los demonios del remitente). La aplicación procesará automáticamente los buzones configurados en este servidor.

Todos los servidores configurados para el acceso POP3 pueden utilizarse para recibir el correo devuelto si conservan los encabezados SMTP &quot;Message-ID&quot; al recoger el correo. Por ejemplo, las implementaciones que utilizan Qmail, SendMail y Microsoft Exchange están actualmente en producción. Sin embargo, algunas instalaciones de Lotus Notes/domino revelaron un problema con el mantenimiento de los encabezados &quot;Message-Id&quot;.

>[!CAUTION]
>
>Este servidor de correo puede tener que gestionar cargas pesadas: En las fases iniciales, las listas típicas pueden producir tasas de salida hacia otro sitio de hasta el 10 % (si envía 100 000 mensajes, recibirá 10 000 devoluciones).
>
>Por este motivo, recomendamos que no utilice su servidor de mensajería de la empresa para esta tarea, ya que puede tener un gran impacto.
>
>Se recomienda configurar un subdominio específico del DNS y un servidor dedicado para el correo rechazado.
