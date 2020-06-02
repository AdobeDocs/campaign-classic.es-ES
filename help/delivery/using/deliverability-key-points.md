---
title: Puntos clave a la hora de administrar la entrega en Adobe Campaign Classic
description: ¿Cuáles son los puntos clave que hay que comprobar al administrar la capacidad de entrega en Adobe Campaign Classic?
page-status-flag: never-activated
uuid: 2681042b-3018-42ae-b252-2367b56616bd
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: delivery
content-type: reference
topic-tags: deliverability-management
discoiquuid: 6a394eeb-fbe1-4712-bb13-db5d7965fb73
index: y
internal: n
snippet: y
translation-type: ht
source-git-commit: 4582ea496fff35c5b586049b8daa379464bd78fc
workflow-type: ht
source-wordcount: '574'
ht-degree: 100%

---


# Puntos clave de la entrega{#deliverability-key-points}

Para optimizar la entrega de los correos electrónicos de Adobe Campaign, recomendamos que utilice las optimizaciones que se enumeran a continuación. Los problemas de entrega generalmente están vinculados a medidas de protección contra spam implementadas por los proveedores de servicios de Internet y los administradores de servidores de correo.

**La capacidad de envío de correo electrónico hace referencia al conjunto de características que determinan la capacidad de un mensaje para llegar a su destino a través de una dirección de correo electrónico personal, en poco tiempo y con la calidad esperada en términos de contenido y formato.**

Estas características se dividen en cuatro categorías principales:
* Calidad de los datos
* Mensaje y contenido
* Infraestructura de envío
* Reputación

Juntas forman la base del éxito de un programa de envío de correo electrónico.

La **tasa de entrega** es el número de correos electrónicos enviados correctamente a sus destinatarios.

La tasa de entrega depende de numerosos factores, en particular:
* Configuración correcta de las instancias
* Su reputación de dirección IP
* Calidad de las direcciones objetivo
* Baja cantidad de quejas y tasas de devolución
* Su contenido del mensaje
* Autenticación de mensajes (SPF, DKIM, DMARC)
* Conocimiento del remitente

A continuación se muestra una lista de los puntos clave que se deben comprobar para garantizar una buena entrega.

## Comprobar configuración de red {#network-configuration}

Los remitentes de spam intentan ocultar su identidad real y, como consecuencia, dificultan la identificación de sus servidores. Una configuración de red legítima que no intente ocultar la identidad del servidor es esencial para enviar correos electrónicos en grandes volúmenes.

## Enviar a direcciones válidas {#valid-addresses}

Los remitentes de spam suelen utilizar generadores de direcciones basados en listas de nombres y apellidos frecuentes; además, rara vez procesan las notificaciones técnicas enviadas por los servidores de correo. Una tasa alta de direcciones no válidas se interpreta a menudo como un signo de spam. Los mecanismos de doble inclusión y el manejo eficaz de los mensajes de devolución técnicos permiten evitar esto.

## Reducir las quejas y las tasas de devoluciones {#reduce-complaint-rates}

Los proveedores de servicios de Internet generalmente tienen un medio prominente para informar un mensaje recibido como correo no deseado. Esto permite identificar fuentes no fiables. Al cumplir con rapidez las solicitudes de exclusión, utilizar con regularidad una lista determinada, verificar el consentimiento a través de un sistema de doble inclusión e implementar círculos de retroalimentación, puede reducir las tasas de quejas.

## Enviar a direcciones de honeypot {#honeypot-addresses}

Los ISP y otras organizaciones (consulte [http://www.projecthoneypot.org/](https://www.projecthoneypot.org/)) utilizan buzones de correo que no corresponden a personas físicas pero que se crean simplemente para engañar a los remitentes de correo no deseado. Estas llamadas &quot;honey pot&quot; se publican en la web para ser recogidas por los spambots y así atrapar a remitentes ilegítimos. El uso de un mecanismo de doble inclusión impide que este tipo de dirección se agregue a una lista. Al utilizar una lista de terceros, debe estar seguro de los métodos empleados por su mantenedor.

## Configuración del contenido del mensaje {#message-content}

En menor medida, el contenido de ciertos mensajes puede llevar a ciertos filtros a detectarlo como correo no deseado. El uso de ciertas palabras, el uso de exclamaciones en la línea del asunto y dentro de los mensajes se interpretan como signos reveladores de spam. También se sabe que los remitentes de spam reemplazan el texto con imágenes para evitar que el texto ofensivo se analice automáticamente mediante filtros antispam. En respuesta a esto, un mensaje (en formato HTML) con una alta proporción de imágenes, o imágenes como archivos adjuntos, puede terminar siendo bloqueado.

## Trabaje en su reputación {#reputation}

Los remitentes de spam realizan entregas programadas para mantener su reputación con el tiempo. A veces necesitan adaptar su plan de mercadotecnia para cumplir con las mejores prácticas impuestas por los ISP y así, después de un pico de reputación (aumento), configuran entregas regulares.