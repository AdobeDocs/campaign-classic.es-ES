---
title: Creación del contenido de un mensaje
seo-title: Creación del contenido de un mensaje
description: Creación del contenido de un mensaje
seo-description: null
page-status-flag: never-activated
uuid: 4ee013fc-fba2-4120-b796-dd4008000ea9
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: message-center
content-type: reference
topic-tags: message-templates
discoiquuid: 1f420652-c9af-4a49-8d5c-a640e960aced
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 2c0d4054fbc15a88ea0370269b62c7d647aea033

---


# Creación del contenido de un mensaje{#creating-message-content}

La definición del contenido de mensajería transaccional es la misma que para los envíos normales en Adobe Campaign. Por ejemplo, para un envío de correo electrónico, puede crear contenido en formato HTML o texto, añadir archivos adjuntos o personalizar el objeto de envío. Para obtener más información, consulte el capítulo en [Envío de correo electrónico](../../delivery/using/about-email-channel.md).

>[!CAUTION]
>
>Las imágenes incluidas en el mensaje deben ser de fácil acceso público. Adobe Campaign no proporciona ningún mecanismo de carga de imágenes para los mensajes transaccionales.\
>Unlike in JSSP or webApp, `<%=` doesn’t have any default escaping.
>
>En este caso, tiene que omitir correctamente todos los datos procedentes del evento. Esta omisión depende de cómo se utilice este campo. Por ejemplo, dentro de una URL, utilice encodeURIComponent. Para mostrar en HTML, puede utilizar escapeXMLString.

Una vez definido el contenido del mensaje, puede integrar la información del evento en el cuerpo del mensaje y personalizarlo. La información del evento se inserta en el cuerpo del texto gracias a las etiquetas de personalización.

![](assets/messagecenter_create_content_001.png)

* Todos los campos de personalización proceden de la carga útil.
* Es posible hacer referencia a uno o varios bloques de personalización en un mensaje transaccional. El contenido del bloque se agregará al contenido de la entrega durante la publicación en la instancia de ejecución.

Para insertar etiquetas de personalización en el cuerpo de un mensaje de correo electrónico, aplique los siguientes pasos:

1. En la plantilla de mensaje, haga clic en la pestaña que coincida con el formato de correo electrónico (HTML o texto).
1. Introduzca el cuerpo del mensaje.
1. In the body of the text, insert the tag using the **[!UICONTROL Real time events>Event XML]** menus.

   ![](assets/messagecenter_create_custo_002.png)

1. Fill in the tag using the following syntax: **element name**.@**attribute name** como se muestra a continuación.

   ![](assets/messagecenter_create_custo_003.png)

