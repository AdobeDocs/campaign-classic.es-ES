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
translation-type: tm+mt
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: tm+mt
source-wordcount: '195'
ht-degree: 6%

---


# Acerca del seguimiento web{#about-web-tracking}

Además del seguimiento estándar que muestra el comportamiento de un usuario de Internet al hacer clic en un vínculo de un mensaje de correo electrónico, la plataforma de Adobe Campaign le permite recopilar información sobre cómo exploran el sitio los usuarios de Internet. Esta recopilación de datos la realiza el módulo de seguimiento Web.

Cuando un usuario de Internet hace clic en un vínculo rastreado en un mensaje de correo electrónico desde un envío determinado, el servidor de redirección se pone en contacto con un depósito de una cookie de sesión que contiene el identificador de registro de banda ancha (identificador de registro de banda ancha) y el identificador de envío (identificador de entrega).

A continuación, el cliente web envía esta cookie al servidor cada vez que el usuario visita una página que contiene una etiqueta de seguimiento web. Esto continúa durante toda la sesión, es decir, hasta que se cierra el cliente web.

El servidor de redirección recopila los siguientes datos de esta manera:

* Dirección URL de la página visualizada, mediante un identificador enviado como parámetro,
* el envío desde el que se visitó la página web, mediante la cookie de sesión,
* identificador del usuario de Internet que hizo clic, mediante la cookie de sesión,
* información adicional como el volumen de negocios generado.

El siguiente diagrama muestra las etapas del diálogo entre el cliente y los distintos servidores.

![](assets/d_ncs_integration_webtracking_structure1.png)

