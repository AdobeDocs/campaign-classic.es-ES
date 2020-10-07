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
translation-type: tm+mt
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: tm+mt
source-wordcount: '164'
ht-degree: 4%

---


# Servidor de mensajería{#messaging-server}

Adobe Campaign gestiona el correo electrónico saliente de forma nativa, pero se necesita un servidor de correo electrónico tradicional para recibir mensajes entrantes vinculados al correo electrónico devuelto (de maileres daemones). The mailboxes configured on this server will be automatically processed by the application.

Todos los servidores configurados para acceso POP3 pueden utilizarse para recibir correo de retorno si conservan los encabezados &quot;Message-ID&quot; SMTP al recoger el correo. For example, implementations using Qmail, SendMail and Microsoft Exchange are currently in production. However, some installations of Lotus Notes/domino revealed an issue with the maintaining of &quot;Message-Id&quot; headers.

>[!CAUTION]
>
>Es posible que este servidor de correo tenga que manejar cargas pesadas: En las fases iniciales, las listas típicas pueden producir tasas de salida hacia otro sitio de hasta el 10 % (si envía 100 000 mensajes, espera recibir 10 000 devoluciones).
>
>Es por eso que recomendamos que no utilice su servidor de mensajería de compañía para esta tarea, ya que puede tener un gran impacto.
>
>Es aconsejable configurar un subdominio específico de su DNS y un servidor dedicado para el correo de devolución.
