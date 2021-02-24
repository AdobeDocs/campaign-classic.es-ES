---
solution: Campaign Classic
product: campaign
title: Introducción al seguimiento de vínculos personalizados
description: Obtenga información sobre cómo escribir vínculos en correos electrónicos que se pueden personalizar y admiten el seguimiento en Campaign Classic.
audience: delivery
content-type: reference
topic-tags: tracking-messages
translation-type: tm+mt
source-git-commit: 151667637a12667f5eda1590e64e01de493be9ce
workflow-type: tm+mt
source-wordcount: '206'
ht-degree: 0%

---


# Comience con el seguimiento de vínculos personalizados {#tracking-personalized-links}

Los vínculos del contenido del correo electrónico que contienen personalización necesitan rastrearse con una sintaxis específica.

El uso de JavaScript en el contenido del correo electrónico (HTML o texto) le permite generar y enviar contenido dinámico a los destinatarios, con dos limitaciones:

* La secuencia de comandos no puede acceder directamente a la base de datos (la función SQL y las funciones API no están disponibles),
* Adobe Campaign debe poder detectar direcciones URL para poder rastrear los vínculos (objetivo de este documento).

Para la detección de seguimiento, Adobe Campaign incrusta [Tidy](http://www.html-tidy.org/) para analizar el origen HTML y detectar el patrón. Lista todas las direcciones URL del contenido para que se puedan rastrear individualmente. Adobe Campaign utiliza nuevamente Tidy para reemplazar la dirección URL (`http://myurl.com`) por una dirección URL que apunte al servidor de redirección de Adobe Campaign.

Por ejemplo, en el contenido inicial: `http://myurl.com/a.php?name=<%=escapeUrl(recipient.lastName)%>` se sustituye por un destinatario en particular con: `http://emailing.customer.com/r/?id=h617791,71ffa3,71ffa8&p1=CustomerName`

Donde:

* &quot;h&quot; significa contenido HTML (o &quot;t&quot; para contenido de texto).
* 617791 es el ID del mensaje / el ID de amplioLog (hexadecimal).
* 71ffa3 es la ID de NmsDelivery (hexadecimal).
* 71ffa8 es el ID de NmsTrackingUrl (hexadecimal).
* p1, p2, etc., son todos los parámetros que se sustituirán en la dirección URL.
