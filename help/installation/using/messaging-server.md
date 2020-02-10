---
title: Servidor de mensajería
seo-title: Servidor de mensajería
description: Servidor de mensajería
seo-description: null
page-status-flag: never-activated
uuid: d7de0405-23eb-4a0d-80a5-c75d661771bb
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: installation
content-type: reference
topic-tags: prerequisites-and-recommendations-
discoiquuid: 1556e87f-9d92-4548-a75a-4f44030ab8d5
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 46f5bfb41bfe9c938ac0ffa767ead3e47a32047d

---


# Servidor de mensajería{#messaging-server}

Adobe Campaign maneja el correo electrónico saliente de forma nativa, pero se necesita un servidor de correo electrónico tradicional para recibir los mensajes entrantes vinculados al correo electrónico devuelto (de los demonios del remitente). La aplicación procesará automáticamente los buzones configurados en este servidor.

Todos los servidores configurados para acceso POP3 pueden utilizarse para recibir correo de retorno si conservan los encabezados &quot;Message-ID&quot; SMTP al recoger el correo. Por ejemplo, las implementaciones que utilizan Qmail, SendMail y Microsoft Exchange están actualmente en producción. Sin embargo, algunas instalaciones de Lotus Notes/domino revelaron un problema con el mantenimiento de los encabezados &quot;Message-Id&quot;.

>[!CAUTION]
>
>Es posible que este servidor de correo tenga que manejar cargas pesadas: En las fases iniciales, las listas típicas pueden producir tasas de salida hacia otro sitio de hasta el 10 % (si envía 100.000 mensajes, espera recibir 10.000 devoluciones).
>
>Es por eso que recomendamos que no utilice su servidor de mensajería de la empresa para esta tarea, ya que puede tener un gran impacto.
>
>Es aconsejable configurar un subdominio específico de su DNS y un servidor dedicado para el correo de devolución.
