---
solution: Campaign Classic
product: campaign
title: Creación del contenido de un mensaje
description: Creación del contenido de un mensaje
audience: message-center
content-type: reference
topic-tags: message-templates
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '267'
ht-degree: 100%

---


# Creación del contenido de un mensaje{#creating-message-content}

La definición del contenido de mensajería transaccional es la misma que para las entregas normales en Adobe Campaign. Por ejemplo, para una entrega de correo electrónico, puede crear contenido en formato HTML o texto, añadir archivos adjuntos o personalizar el objeto de envío. Para obtener más información, consulte el capítulo en [Envío de correo electrónico](../../delivery/using/about-email-channel.md).

>[!IMPORTANT]
>
>Las imágenes incluidas en el mensaje deben ser de fácil acceso público. Adobe Campaign no proporciona ningún mecanismo de carga de imágenes para los mensajes transaccionales.\
>A diferencia de JSSP o webApp, `<%=` no tiene ninguna omisión predeterminada.
>
>En este caso, tiene que omitir correctamente todos los datos procedentes del evento. Esta omisión depende de cómo se utilice este campo. Por ejemplo, dentro de una URL, utilice encodeURIComponent. Para mostrar en HTML, puede utilizar escapeXMLString.

Una vez definido el contenido del mensaje, puede integrar la información del evento en el cuerpo del mensaje y personalizarlo. La información del evento se inserta en el cuerpo del texto gracias a las etiquetas de personalización.

![](assets/messagecenter_create_content_001.png)

* Todos los campos de personalización proceden de la carga útil.
* Es posible hacer referencia a uno o varios bloques de personalización en un mensaje transaccional. El contenido del bloque se agrega al contenido de la envío durante la publicación en la instancia de ejecución.

Para insertar etiquetas de personalización en el cuerpo de un mensaje de correo electrónico, aplique los siguientes pasos:

1. En la plantilla de mensaje, haga clic en la pestaña que coincida con el formato de correo electrónico (HTML o texto).
1. Introduzca el cuerpo del mensaje.
1. En el cuerpo del texto, inserte la etiqueta utilizando los menús **[!UICONTROL Real time events>Event XML]**.

   ![](assets/messagecenter_create_custo_002.png)

1. Complete la etiqueta con la siguiente sintaxis: **element name**.@**attribute name** como se muestra a continuación.

   ![](assets/messagecenter_create_custo_003.png)

