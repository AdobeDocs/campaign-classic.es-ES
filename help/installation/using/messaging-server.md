---
solution: Campaign Classic
product: campaign
title: Servidor de mensajería
description: Servidor de mensajería
audience: installation
content-type: reference
topic-tags: prerequisites-and-recommendations-
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '162'
ht-degree: 3%

---


# Servidor de mensajería{#messaging-server}

Adobe Campaign gestiona el correo electrónico saliente de forma nativa, pero se necesita un servidor de correo electrónico tradicional para recibir mensajes entrantes vinculados al correo electrónico devuelto (de maileres daemones). La aplicación procesará automáticamente los buzones configurados en este servidor.

Todos los servidores configurados para acceso POP3 pueden utilizarse para recibir correo de retorno si conservan los encabezados &quot;Message-ID&quot; SMTP al recoger el correo. Por ejemplo, las implementaciones que utilizan Qmail, SendMail y Microsoft Exchange están actualmente en producción. Sin embargo, algunas instalaciones de Lotus Notes/domino revelaron un problema con el mantenimiento de los encabezados &quot;Message-Id&quot;.

>[!CAUTION]
>
>Es posible que este servidor de correo tenga que manejar cargas pesadas: En las fases iniciales, las listas típicas pueden producir tasas de salida hacia otro sitio de hasta el 10 % (si envía 100 000 mensajes, espera recibir 10 000 devoluciones).
>
>Es por eso que recomendamos que no utilice su servidor de mensajería de compañía para esta tarea, ya que puede tener un gran impacto.
>
>Es aconsejable configurar un subdominio específico de su DNS y un servidor dedicado para el correo de devolución.
