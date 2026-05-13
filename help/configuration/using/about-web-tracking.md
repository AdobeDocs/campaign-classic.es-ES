---
product: campaign
title: Acerca del seguimiento web
feature: Configuration, Instance Settings
description: Acerca del seguimiento web
role: User, Developer
exl-id: 91c31703-75e6-47a4-a877-35682dd687a9
TQID: https://experienceleague.adobe.com/FfA6FEH5WP2JJGVR4BhpjO19Yj4mt8irvyJLwuzCThs
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
topic_v2:
  - id: d3cdead0-685a-4489-9250-4bb709942f66
source-git-commit: 4c295c0dabae8aba298390a3da2422a3fa1219f9
workflow-type: tm+mt
source-wordcount: 192
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
