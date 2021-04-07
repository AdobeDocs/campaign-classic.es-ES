---
solution: Campaign Classic
product: campaign
title: Introducción al seguimiento de vínculos personalizados
description: Obtenga información sobre cómo escribir vínculos en correos electrónicos que se pueden personalizar y admiten el seguimiento en Campaign Classic.
audience: delivery
content-type: reference
topic-tags: tracking-messages
translation-type: ht
source-git-commit: 6b81d0ea22bf9d8f33e486535b4ce02fbae7b9ae
workflow-type: ht
source-wordcount: '219'
ht-degree: 100%

---


# Introducción al seguimiento de vínculos personalizados {#tracking-personalized-links}

Los vínculos del contenido del correo electrónico que contienen personalización necesitan rastrearse con una sintaxis específica.

El uso de JavaScript en el contenido del correo electrónico (HTML o texto) le permite generar y enviar contenido dinámico a los destinatarios, con dos limitaciones:

* La secuencia de comandos no puede acceder directamente a la base de datos (la función SQL y las funciones API no están disponibles),
* Adobe Campaign debe poder detectar direcciones URL para poder rastrear los vínculos. [Obtenga más información](detecting-tracking-urls.md)

Puede añadir instrucciones de preprocesamiento específicas para crear una secuencia de comandos de la dirección URL y rastrearla. [Obtenga más información](pre-processing-instructions.md)

Para la detección de seguimiento, Adobe Campaign incrusta [Tidy](http://www.html-tidy.org/) para analizar la fuente HTML y detectar el patrón. Enumera todas las direcciones URL del contenido para que se puedan rastrear individualmente. Adobe Campaign utiliza de nuevo Tidy para reemplazar la dirección URL (`http://myurl.com`) por otra URL que apunte al servidor de redirección de Adobe Campaign.

Por ejemplo, en el contenido inicial: `http://myurl.com/a.php?name=<%=escapeUrl(recipient.lastName)%>` se sustituye por un destinatario en particular con: `http://emailing.customer.com/r/?id=h617791,71ffa3,71ffa8&p1=CustomerName`

Donde:

* &quot;h&quot; significa contenido HTML (o &quot;t&quot; para contenido de texto).
* 617791 es el ID del mensaje/el ID de broadLog (hexadecimal).
* 71ffa3 es el ID de NmsDelivery (hexadecimal).
* 71ffa8 es el ID de NmsTrackingUrl (hexadecimal).
* p1, p2, etc., son todos los parámetros que se sustituirán en la dirección URL.
