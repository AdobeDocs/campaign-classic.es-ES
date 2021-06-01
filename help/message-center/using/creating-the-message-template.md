---
product: campaign
title: Diseñar plantillas de mensajes transaccionales
description: Aprenda a crear y diseñar una plantilla de mensaje transaccional en Adobe Campaign Classic.
audience: message-center
content-type: reference
topic-tags: message-templates
exl-id: a52bc140-072e-4f81-b6da-f1b38662bce5
source-git-commit: e86350cf12db37e3f2c227563057b97922601729
workflow-type: tm+mt
source-wordcount: '498'
ht-degree: 72%

---

# Diseñar plantillas de mensajes transaccionales {#creating-the-message-template}

Para asegurarse de que cada evento se pueda cambiar a un mensaje personalizado, debe crear una plantilla de mensaje para que coincida con cada tipo de evento.

>[!IMPORTANT]
>
>Los tipos de eventos deben crearse de antemano. Para obtener más información, consulte [Crear tipos de eventos](../../message-center/using/creating-event-types.md).

Las plantillas de mensajes transaccionales contienen la información necesaria para personalizar el mensaje transaccional. También puede utilizar plantillas para probar la vista previa del mensaje y enviar pruebas utilizando las direcciones semilla antes de enviar al destinatario final. Para obtener más información, consulte [Probar plantillas de mensajes transaccionales](../../message-center/using/testing-message-templates.md).

## Creación de la plantilla del mensaje {#creating-message-template}

1. Vaya a la carpeta **[!UICONTROL Message Center >Transactional message templates]** en el árbol de Adobe Campaign.

1. En la lista de las plantillas de mensajes transaccionales, haga clic con el botón derecho y seleccione **[!UICONTROL New]** en el menú desplegable o haga clic en el botón **[!UICONTROL New]** situado sobre la lista de las plantillas de mensajes transaccionales.

   ![](assets/messagecenter_create_model_001.png)

1. En la ventana de envío, seleccione la plantilla de envío adecuada para el canal que desee utilizar.

   ![](assets/messagecenter_create_model_002.png)

1. Cambie la etiqueta si es necesario.

1. Seleccione el tipo de evento que coincida con el mensaje que desea enviar.

   ![](assets/messagecenter_create_model_003.png)

   Es necesario crear previamente los tipos de eventos en la consola. Para obtener más información, consulte [Crear tipos de eventos](../../message-center/using/creating-event-types.md).

   >[!IMPORTANT]
   >
   >Un tipo de evento no se puede vincular a más de una plantilla.

1. Introduzca una naturaleza y una descripción y, a continuación, haga clic en **[!UICONTROL Continue]** para crear el cuerpo del mensaje (consulte [Create the message content](#creating-message-content)).

   ![](assets/messagecenter_create_model_004.png)

## Crear el contenido del mensaje {#creating-message-content}

La definición del contenido de mensajería transaccional es la misma que para las entregas normales en Adobe Campaign. Por ejemplo, para una entrega de correo electrónico, puede crear contenido en formato HTML o texto, añadir archivos adjuntos o personalizar el objeto de envío. Para obtener más información, consulte el capítulo [Email delivery](../../delivery/using/about-email-channel.md) .

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

1. En el cuerpo del texto, inserte la etiqueta utilizando el menú **[!UICONTROL Real time events > Event XML]** .

   ![](assets/messagecenter_create_custo_002.png)

1. Complete la etiqueta con la siguiente sintaxis: **element name**.@**attribute name** como se muestra a continuación.

   ![](assets/messagecenter_create_custo_003.png)

1. Guarde el contenido.

El mensaje ya está listo para [probarse](../../message-center/using/testing-message-templates.md).
