---
title: Acerca del seguimiento web
seo-title: Acerca del seguimiento web
description: Acerca del seguimiento web
seo-description: null
page-status-flag: never-activated
uuid: 59d18ffb-c26e-4571-8364-5e85ec587349
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: configuration
content-type: reference
topic-tags: setting-up-web-tracking
discoiquuid: 38ba9be9-dabc-41d4-878c-d772955301fe
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 579329d9194115065dff2c192deb0376c75e67bd

---


# Acerca del seguimiento web{#about-web-tracking}

Además del seguimiento estándar que muestra el comportamiento de un usuario de Internet al hacer clic en un vínculo de un mensaje de correo electrónico, la plataforma de Adobe Campaign permite recopilar información sobre la forma en que los usuarios de Internet exploran el sitio web. Esta recopilación de datos la realiza el módulo de seguimiento Web.

Cuando un usuario de Internet hace clic en un vínculo rastreado en un mensaje de correo electrónico de una entrega determinada, el servidor de redirección contactó con un depósito de una cookie de sesión que contiene el identificador de registro de banda ancha (identificador de registro de banda ancha) y el identificador de entrega (identificador de entrega).

A continuación, el cliente web envía esta cookie al servidor cada vez que el usuario visita una página que contiene una etiqueta de seguimiento web. Esto continúa durante toda la sesión, es decir, hasta que se cierra el cliente web.

El servidor de redirección recopila los siguientes datos de esta manera:

* Dirección URL de la página visualizada, mediante un identificador enviado como parámetro,
* la entrega desde la que se visitó la página web, a través de la cookie de sesión,
* identificador del usuario de Internet que hizo clic, mediante la cookie de sesión,
* información adicional como el volumen de negocios generado.

El siguiente diagrama muestra las etapas del diálogo entre el cliente y los distintos servidores.

![](assets/d_ncs_integration_webtracking_structure1.png)

