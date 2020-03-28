---
title: Implementación
seo-title: Implementación
description: Implementación
seo-description: null
page-status-flag: never-activated
uuid: 12b5fbbf-fe0d-4598-8845-f7b8ee7672c3
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: message-center
content-type: reference
topic-tags: use-case
discoiquuid: ac1c0a00-41ef-4cc2-bb51-2808ef400bb1
index: y
internal: n
snippet: y
translation-type: ht
source-git-commit: 20f835c357d016643ea1f3209ee4dfb6d3239f90

---


# Implementación{#implementation}

Aquí se muestra un diagrama con los diferentes pasos involucrados en este escenario.

![](assets/message-center-uc1.png)

Primero, comience por diseñar el archivo adjunto. Consulte este [artículo](../../delivery/using/attaching-files.md#attach-a-personalized-file). Esto permite adjuntar archivos a un correo electrónico, incluso si no están hospedados en la instancia de ejecución.

Puede enviar correos electrónicos a través de un activador de mensaje SOAP. Para obtener más información sobre las solicitudes SOAP, consulte [Descripción de eventos](../../message-center/using/event-description.md). En la llamada SOAP, hay un parámetro de URL (attachmentURL).

Al diseñar el correo electrónico, haga clic en **[!UICONTROL Attachment]**. En la pantalla de **[!UICONTROL Attachment definition]** introduzca el parámetro de archivo adjunto SOAP:

```
<%= rtEvent.ctx.attachementUrl %>
```

Cuando el mensaje se procesa/implementa, el sistema obtiene el archivo desde la ubicación remota (servidor de terceros) y lo adjunta al mensaje individual.

Dado que este parámetro puede ser una variable, debe aceptar la variable URL remota completamente formada del archivo, enviada a través de la llamada SOAP.

![](assets/message-center-uc2.png)

