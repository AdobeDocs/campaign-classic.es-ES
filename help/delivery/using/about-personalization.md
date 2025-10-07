---
product: campaign
title: Introducción a la personalización
description: Obtenga información sobre cómo personalizar mensajes y utilizar contenido condicional en Campaign
badge-v8: label="También se aplica a v8" type="Positive" tooltip="También se aplica a Campaign v8"
feature: Personalization
role: User
exl-id: 555082a2-1b62-4aa4-b80c-77b1a1ef9491
source-git-commit: a1e9fec0e9c85bf25b79e24a7432dfb45bd1a0cb
workflow-type: tm+mt
source-wordcount: '437'
ht-degree: 81%

---

# Introducción a la personalización{#about-personalization}

Los mensajes enviados por Adobe Campaign pueden personalizarse de varias formas diferentes, teniendo en consideración el contenido o el aspecto de los mensajes. Estas formas se pueden combinar de acuerdo con criterios tomados especialmente de los perfiles de destinatario. En el caso de las entregas de correo electrónico, se pueden definir los elementos y las condiciones de personalización de una entrega directamente en JavaScript desde la pestaña **[!UICONTROL Source]**. En general, Adobe Campaign le permite:

* Personalizar el formato del mensaje. Consultar [Contenido del mensaje](defining-the-email-content.md#message-content).
* Insertar campos personalizados dinámicos. Consultar [Personalización de campos](personalization-fields.md).
* Insertar bloques de personalización predefinidos. Consultar [Bloques de personalización](personalization-blocks.md).
* Cree contenido condicional. Consulte la sección [Contenido condicional](conditional-content.md).

>[!CAUTION]
>
>Las siguientes variables son variables internas que pueden utilizarse para la personalización pero que no deben modificarse: **delivery**, **message**, **dataSource**, **targetData**, **provider**, **coupon**, **couponValue**, **proposition**.


Con Adobe Campaign, personalice las entregas para enviar mensajes que coincidan con el perfil y los intereses de cada destinatario.

Personalization le ayuda a hacer que sus mensajes sean más relevantes y atractivos. Puede utilizar los datos del destinatario para adaptar el contenido, añadir campos dinámicos o mostrar diferente información en función de las condiciones. Aprenda a configurar y utilizar funciones de personalización en los envíos en [Documentación de Adobe Campaign v8](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/personalize/personalize.html?lang=es){target=_blank}.

Como parte de la iniciativa de promoción de la versión 8 de Campaign, se ha reorganizado la documentación de Campaign Classic. Ahora, las funciones comunes solo están disponibles en el conjunto de documentación de la versión 8 de Campaign.

>[!BEGINTABS]

>[!TAB Documentación de personalización de contenido]

Para obtener más información acerca de la personalización de contenido, consulte la [documentación de Campaign v8](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/personalize/personalize.html?lang=es){target=_blank}.


[![imagen](../../assets/do-not-localize/learn-more-button.svg)](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/personalize/personalize.html?lang=es){target=_blank}


>[!TAB Creación de envío de correo electrónico]

Conozca los pasos clave relacionados con la creación de envíos de correo electrónico en la documentación de la versión 8 de Campaign:

* [Crear un envío de correo electrónico](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/emails/email.html?lang=es){target="_blank"}: obtenga información sobre los diferentes pasos necesarios para crear un envío de correo electrónico.
* [Definir el contenido del correo electrónico](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/emails/defining-the-email-content.html?lang=es){target="_blank"}: defina lo que incluirá el correo electrónico, remitente, asunto, contenido, imágenes.
* [Definir contenido interactivo](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/emails/defining-interactive-content.html?lang=es){target="_blank"}: use el formato interactivo AMP para correo electrónico para enviar correos electrónicos dinámicos.
* [Enviar correos electrónicos en móviles japoneses](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/emails/sending-emails-on-japanese-mobiles.html?lang=es){target="_blank"}: use uno de los tres formatos japoneses específicos para correos electrónicos en móviles.
* [Adjuntar archivos a un correo electrónico](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/emails/attaching-files.html?lang=es){target="_blank"}: descubra las diferentes formas de adjuntar uno o más archivos a un correo electrónico.


>[!TAB Parámetros de correo electrónico]

Consulte estas páginas para obtener más información sobre los parámetros de correo electrónico en la documentación de la versión 8 de Campaign:

* [Vínculo a la página espejo](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/emails/mirror-page.html?lang=es){target="_blank"}: configure la página espejo para asegurarse de que sus clientes siempre obtengan la mejor experiencia de procesamiento.
* [Añadir una dirección CCO](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/emails/email-bcc.html?lang=es){target="_blank"}: configure Adobe Campaign para que conserve una copia de los mensajes de correo electrónico enviados desde su plataforma.
* [Definir parámetros de correo electrónico adicionales](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/emails/email-parameters.html?lang=es){target="_blank"}: obtenga más información sobre las opciones y los parámetros disponibles en las propiedades de envío.

Consulte también esta [página](sending-with-enhanced-mta.md) para obtener más información sobre el MTA mejorado.

>[!ENDTABS]





<!--
Adobe Campaign lets you mass deliver personalized electronic messages to a target population.

Before starting sending emails:

* Make sure recipient profiles contain at least an email address.
* Learn more about the Adobe Campaign [Delivery best practices](delivery-best-practices.md).
* Read out these sections to learn more about Deliverability: [Deliverability management in Campaign](about-deliverability.md) and [Deliverability best practices guide](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/introduction.html?lang=es).

The key steps to send an email are as follows:

* [Create an email delivery](creating-an-email-delivery.md)
* [Define the target population](steps-defining-the-target-population.md)
* [Define the email content](defining-the-email-content.md)
* [Send the email](sending-messages.md)
* [Monitor the delivery](about-delivery-monitoring.md)

The sections below provide information that is specific to the email channel. For global information on how to create a delivery, refer to [this section](steps-about-delivery-creation-steps.md).
-->