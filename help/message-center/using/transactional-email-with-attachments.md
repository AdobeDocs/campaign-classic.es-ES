---
title: Añadir archivos adjuntos a mensajes transaccionales con Adobe Campaign Classic
description: Aprenda a enviar correos electrónicos transaccionales con datos adjuntos individuales o personalizados mediante Adobe Campaign Classic
page-status-flag: never-activated
uuid: 4452d839-318a-49d8-8abb-4ba04c803e9f
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: message-center
content-type: reference
topic-tags: use-case
discoiquuid: 7b8ab9d6-e47e-46d8-99df-da793486654c
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 24a50fcaad4d9081e5504652eb5b73aa7db1e65f
workflow-type: tm+mt
source-wordcount: '560'
ht-degree: 39%

---


# Caso de uso: Envío de correos electrónicos transaccionales con datos adjuntos{#transactional-email-with-attachments}

El propósito de este caso de uso es añadir archivos adjuntos de los correos electrónicos sobre la marcha a las entregas salientes.

## Pasos clave {#key-steps}

En este escenario, aprenderá a enviar correos electrónicos transaccionales con datos adjuntos individuales o personalizados. Los archivos adjuntos no se cargarán previamente en el servidor de Transactional Messaging: en su lugar, se generarán sobre la marcha.

Al capturar las interacciones o los detalles del cliente, es posible que necesite volver a enviar esta información al cliente al final del proceso, por ejemplo, en un archivo PDF adjunto a un correo electrónico.

A continuación se muestran los pasos principales de este escenario:

1. El cliente introduce el sitio web y busca el producto que desea comprar.
1. El cliente selecciona el producto y personaliza algunas opciones.
1. El cliente completa la transacción.
1. Se envía un correo electrónico al cliente que confirma la transacción. Dado que no se recomienda enviar la información PII (Información de identificación personal) en el correo electrónico, se genera un PDF seguro y se adjunta al correo electrónico.
1. El cliente recibe el correo electrónico y sus datos adjuntos, que contienen los datos relevantes.

En este escenario, los archivos adjuntos no se crean previamente, sino que se agregan sobre la marcha a los correos electrónicos salientes, lo que oferta los siguientes beneficios:

* Esto le permite personalizar el contenido del archivo adjunto.
* Si el archivo adjunto está asociado a una transacción (como en el escenario de ejemplo descrito anteriormente), puede contener datos dinámicos que se generan durante el proceso del cliente.
* Al adjuntar archivos PDF, se optimiza la seguridad, ya que se puede codificar y enviarlos a través de HTTPS.

## Recomendaciones {#important-notes}

Antes de implementar este escenario, lea atentamente las directrices siguientes:

* Las instancias de Mensajería transaccional no deben utilizarse para almacenar, exportar o cargar archivos o datos. Solo se pueden utilizar para datos de evento e información relacionada. No deben considerarse como un sistema de almacenamiento de archivos.
* Dado que no hay acceso directo a las instancias o al servidor de mensajería transaccional fuera de Adobe, no hay una forma estándar de insertar dichos archivos en estos servidores (sin acceso a FTP).
* No es contractualmente correcto utilizar el espacio en disco de las instancias de Mensajería transaccional para almacenar archivos de cualquier tipo, ni siquiera para archivos adjuntos.
* Para hospedar estos archivos debe utilizar otro sistema de discos en línea. Necesita un acceso FTP a este sistema y debe poder escribir y eliminar archivos.

## Implementación {#implementation}

El diagrama siguiente muestra los diferentes pasos para implementar este escenario:

![](assets/message-center-uc1.png)

Para agregar datos adjuntos de correo electrónico sobre la marcha a un mensaje transaccional, siga los pasos a continuación:

1. Inicio diseñando los datos adjuntos. Para obtener más información, consulte [esta sección](../../delivery/using/attaching-files.md#attach-a-personalized-file).

   Esto permite adjuntar archivos a un correo electrónico, incluso si no están hospedados en la instancia de ejecución.

1. Puede enviar correos electrónicos a través de un activador de mensaje SOAP. En la llamada SOAP, hay un parámetro de URL (attachmentURL).

   Para obtener más información sobre las solicitudes SOAP, consulte [Descripción de eventos](../../message-center/using/event-description.md).

1. When designing your email, click **[!UICONTROL Attachment]**.

1. In the **[!UICONTROL Attachment definition]** screen, enter the SOAP attachment parameter:

   ```
   <%= rtEvent.ctx.attachementUrl %>
   ```

1. Cuando se procesa el mensaje, el sistema obtiene el archivo desde la ubicación remota (servidor de terceros) y lo adjunta al mensaje individual.

   Dado que este parámetro puede ser una variable, debe aceptar la variable URL remota completamente formada del archivo, enviada a través de la llamada SOAP.

   ![](assets/message-center-uc2.png)
