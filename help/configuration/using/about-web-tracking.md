---
product: campaign
title: Acerca del seguimiento web
description: Acerca del seguimiento web
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
exl-id: 91c31703-75e6-47a4-a877-35682dd687a9
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: tm+mt
source-wordcount: '192'
ht-degree: 4%

---

# Acerca del seguimiento web{#about-web-tracking}

Además del seguimiento estándar que muestra el comportamiento de un usuario de Internet que hace clic en un vínculo de un mensaje de correo electrónico, la plataforma Adobe Campaign permite recopilar información sobre cómo los usuarios de Internet exploran el sitio web. Esta recopilación de datos se realiza mediante el módulo de seguimiento web.

Cuando un usuario de Internet hace clic en un vínculo rastreado de un correo electrónico desde una entrega determinada, el servidor de redirección contactado deposita una cookie de sesión que contiene el identificador de broadlog (broadlogId) y el identificador de entrega (deliveryId).

A continuación, el cliente web envía esta cookie al servidor cada vez que el usuario visita una página que contiene una etiqueta de seguimiento web. Esto continúa durante toda la sesión, es decir, hasta que se cierra el cliente web.

El servidor de redirección recopila los siguientes datos de esta manera:

* URL de la página visualizada, mediante un identificador enviado como parámetro,
* la entrega desde la que se visitó la página web, a través de la cookie de sesión,
* identificador del usuario de internet que hizo clic, a través de la cookie de sesión,
* información adicional, como el volumen comercial generado.

El diagrama siguiente muestra las fases del diálogo entre el cliente y los distintos servidores.

![](assets/d_ncs_integration_webtracking_structure1.png)
