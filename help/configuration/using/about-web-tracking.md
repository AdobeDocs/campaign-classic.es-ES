---
product: campaign
title: Acerca del seguimiento web
description: Acerca del seguimiento web
audience: configuration
content-type: reference
topic-tags: setting-up-web-tracking
exl-id: 91c31703-75e6-47a4-a877-35682dd687a9
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: tm+mt
source-wordcount: '192'
ht-degree: 4%

---

# Acerca del seguimiento web{#about-web-tracking}

Además del seguimiento estándar que muestra el comportamiento de un usuario de Internet al hacer clic en un vínculo de un mensaje de correo electrónico, la plataforma de Adobe Campaign permite recopilar información sobre cómo los usuarios de Internet exploran el sitio web. Esta recopilación de datos se realiza mediante el módulo de seguimiento web.

Cuando un usuario de Internet hace clic en un vínculo rastreado en un correo electrónico de una entrega determinada, el servidor de redirección contactado deposita una cookie de sesión que contiene el identificador de broadlog (broadlogId) y el identificador de la entrega (deliveryId).

A continuación, el cliente web envía esta cookie al servidor cada vez que el usuario visita una página que contiene una etiqueta de seguimiento web. Esto continúa durante toda la sesión, es decir, hasta que se cierra el cliente web.

El servidor de redirección recopila los siguientes datos de esta manera:

* URL de la página visualizada, a través de un identificador enviado como parámetro,
* la entrega desde la que se visitó la página web, a través de la cookie de sesión,
* identificador del usuario de Internet que hizo clic, a través de la cookie de sesión,
* información adicional, como el volumen de negocio generado.

En el diagrama siguiente se muestran las etapas del cuadro de diálogo entre el cliente y los distintos servidores.

![](assets/d_ncs_integration_webtracking_structure1.png)
