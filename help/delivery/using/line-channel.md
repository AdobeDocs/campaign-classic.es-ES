---
title: Canal LINE
seo-title: Canal LINE
description: Canal LINE
seo-description: null
page-status-flag: never-activated
uuid: 94b4e044-3f5d-42a6-b249-29f417386156
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: delivery
content-type: reference
topic-tags: sending-messages-on-mobiles
discoiquuid: 1d3cc650-3c79-4a1d-b2bc-e7eb6d59d2f1
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 0ce6e5277c32bc18c20dca62e5b276f654d1ace5

---


# Canal LINE{#line-channel}

LINE es una aplicación gratuita de mensajería instantánea, llamadas de voz y vídeo, disponible en todos los teléfonos inteligentes (iPhone, Android, Windows Phone, Blackberry, Nokia) y PC. Adobe Campaign le permite enviar mensajes por LINE.

LINE solo está disponible para instalaciones de servicios locales o gestionados.

LINE también se puede combinar con el módulo de mensajes de transacción para enviar mensajes en tiempo real en la aplicación LINE instalada en los dispositivos móviles de los consumidores. Para obtener más información, consulte [esta página](../../message-center/using/transactional-messaging-architecture.md#transactional-messaging-and-line).

![](assets/line_message.png)

Las secciones a continuación proporcionan información específica del canal LINE. For global information on how to create a delivery, refer to [this section](../../delivery/using/steps-about-delivery-creation-steps.md).

Los pasos para utilizar el canal LINE son los siguientes:

1. Creación de envíos
1. Configuración del contenido del mensaje.
1. Selección de la población objetivo
1. Envío de mensajes
1. Monitorización del envío (seguimiento, cuarentena, informes, etc.).

## Configuración del canal LINE {#setting-up-line-channel}

### Creación de una cuenta de LINE y una cuenta externa {#creating-a-line-account-and-an-external-account-}

>[!NOTE]
>
>Antes de crear una cuenta de LINE y una cuenta externa, primero debe instalar el paquete de LINE en su instancia. Para obtener más información, consulte la sección [LINE](../../installation/using/installing-campaign-standard-packages.md#line-package) en la guía de instalación.

Primero debe crear una cuenta LINE para poder vincularla a Adobe Campaign. A continuación, puede enviar mensajes a través de LINE a los usuarios que hayan añadido su cuenta de LINE a su aplicación móvil. Solamente el administrador funcional de la plataforma puede administrar las cuentas externas y la cuenta de LINE.

Para crear y configurar una cuenta de LINE, consulte [https://developers.line.me/](https://developers.line.me/).

To create and configure a LINE service, see [Managing subscriptions](../../delivery/using/managing-subscriptions.md).

![](assets/line_service.png)

Por último, para crear una cuenta externa en Adobe Campaign:

1. En la estructura de árbol **Administración**, **Plataforma**, haga clic en la pestaña **Cuentas externas**.
1. A continuación, haga clic en el icono **Nueva**.

   ![](assets/line_config.png)

1. Rellene los campos **Etiqueta** y **Nombre interno**.
1. In the **[!UICONTROL Type]** field, select Routing and in the **Channel** field, select LINE.
1. Click **[!UICONTROL Save]** to create your LINE external account.
1. Un campo personalizado **LINE** aparece bajo el icono **General**, rellene los campos siguientes:

   ![](assets/line_config_2.png)

   * **Alias** de canal: se proporciona a través de su cuenta LINE en la ficha **[!UICONTROL Channels]** > **[!UICONTROL Technical configuration]** .
   * **ID de canal**: se proporciona a través de su cuenta LINE en la pestaña **Canales**, **Panel de información básica**.
   * **Clave secreta del canal**: se proporciona a través de su cuenta LINE en la pestaña **Canales**, **Panel de información básica**.
   * **Testigo** de acceso: se proporciona a través de su cuenta LINE en el portal para desarrolladores o haciendo clic en el **[!UICONTROL Get access token]** botón .
   * **Fecha de caducidad del token de acceso**: permite especificar la fecha de caducidad del token de acceso.
   * **Servicio de suscripción LINE**: permite especificar los servicios a los que se suscriben los usuarios.

>[!NOTE]
>
>Debe comprobar que se han iniciado los flujos de trabajo **[!UICONTROL LINE access token update (updateLineAccessToken)]** y **[!UICONTROL Delete blocked LINE users (deleteBlockedLineUsers)]** . From the explorer, click **[!UICONTROL Administration > Production > Technical workflows > LINE workflows]** to check the status of the workflows.

## Creación del envío {#creating-the-delivery}

Para crear un envío de **LINE** , debe seguir estos pasos:

>[!NOTE]
>
>En [esta sección](../../delivery/using/steps-about-delivery-creation-steps.md) se exponen conceptos globales sobre la creación de envíos.

1. En la **[!UICONTROL Campaigns]** ficha, seleccione **[!UICONTROL Deliveries]** y haga clic en el **[!UICONTROL Create]** botón.
1. In the window that appears, select **[!UICONTROL LINE V2 delivery]** delivery template.

   ![](assets/line_message_01.png)

1. Identifique su envío con una etiqueta, un código y una descripción. Para obtener más información, consulte [esta sección](../../delivery/using/steps-create-and-identify-the-delivery.md#identifying-the-delivery).
1. Haga clic **[!UICONTROL Continue]** para crear la entrega.

## Definición del contenido {#defining-the-content}

Para definir el contenido de un envío LINE, primero debe añadir el tipo de mensaje al envío. Cada envío LINE puede contener hasta 5 mensajes.

Puede elegir entre dos tipos de mensaje:

* Mensaje de texto
* Imagen y enlace

### Configuración de un envío de mensaje de texto {#configuring-a-text-message-delivery}

Un envío de un **mensaje de texto** de LINE es un mensaje enviado a los destinatarios en forma de texto.

![](assets/line_message_02.png)

La configuración de este tipo de mensaje es similar a la configuración del **texto** de un mensaje de correo electrónico. Para obtener más información, consulte esta [página](../../delivery/using/defining-the-email-content.md#message-content).

### Configuración de un envío de imagen y enlace {#configuring-an-image-and-link-delivery}

Un envío de **imagen y enlace** de LINE es un mensaje enviado a los destinatarios en forma de imagen que puede contener una URL o varias.

Puede utilizar:

* una **imagen personalizada**,

   >[!NOTE]
   >
   >Puede utilizar la variable **%SIZE%**: esta variable permite optimizar la visualización de la imagen según el tamaño de pantalla del dispositivo móvil del destinatario.

   ![](assets/line_message_04.png)

* una **URL con imagen**,

   ![](assets/line_message_03.png)

   Las direcciones URL con imágenes permiten utilizar distintas resoluciones de imagen para optimizar la visibilidad del envío en dispositivos móviles. Solo se admiten imágenes con la misma altura y anchura.

   Las imágenes se pueden definir en función del tamaño de la pantalla:

   * 1040px
   * 700px
   * 460px
   * 300px
   * 240px
   >[!NOTE]
   >
   >El tamaño de 1040 x 1040 píxeles es obligatorio para cada imagen de LINE con enlace.

   A continuación, debe añadir el texto alternativo que aparece en el dispositivo móvil del destinatario.

* y **[!UICONTROL Links]**.

   ![](assets/line_message_05.png)

   The **[!UICONTROL Links]** section allows you to choose between different layouts that will divide your image in multiple clickable regions. A continuación, puede asignar a cada una de ellas un enlace dedicado.

>[!NOTE]
>
>La sintaxis &lt;%@ include option=&#39;NmsServer_URL&#39; %>/webApp/APP3?id=&lt;%=escapeUrl(cryptString(visitor.id))%> permite incluir un enlace a una aplicación web en un mensaje de LINE.

### Recomendaciones {#recommendations}

* Cuando realice un envío de LINE a un nuevo destinatario por primera vez, debe añadir al envío el mensaje oficial de LINE sobre los términos de uso y el consentimiento. El mensaje oficial está disponible en el siguiente enlace: [https://terms.line.me/OA_privacy/](https://terms.line.me/OA_privacy/sp?lang=fr).

## Selección de la población objetivo {#selecting-the-target-population}

La selección de los destinatarios de un envío LINE es similar a la definición de los destinatarios del envío del correo electrónico. Para obtener más información, consulte [Identificación de poblaciones](../../delivery/using/steps-defining-the-target-population.md)objetivo.

Se realiza la segmentación de los **visitantes**.

## Envío de mensajes {#sending-messages}

Cuando el envío se haya creado y configurado correctamente, puede enviarlo al objetivo definido anteriormente.

Realizar envíos de LINE funciona de forma similar a un envío de correo electrónico. For more information on sending a delivery, refer to [Sending messages](../../delivery/using/sending-messages.md).

## Acceso a informes {#accessing-reports}

You can view reports on the LINE service by clicking **[!UICONTROL Profiles and Targets > Services and Subscriptions > LINE]** in the explorer. Then click the **[!UICONTROL Reports]** icon in the LINE service.

![](assets/line_reports.png)

To view reports on LINE deliveries, click **[!UICONTROL Campaign Management > Deliveries]** then select the delivery you want. Los informes de seguimiento indican la tasa de seguimiento de los enlaces. LINE no tiene en cuenta la tasa de apertura.

![](assets/line_reports_01.png)

## Ejemplo: creación y envío de un mensaje personalizado de LINE {#example--create-and-send-a-personalized-line-message}

En este ejemplo, se crea y configura un mensaje de texto y una imagen que contiene datos que se van a personalizar según el destinatario.

1. Create your LINE delivery by clicking the **[!UICONTROL Create]** button from the **[!UICONTROL Campaign]** tab.

   ![](assets/line_usecase.png)

1. Select the **[!UICONTROL LINE V2 delivery]** delivery template and name your delivery.

   ![](assets/line_usecase_01.png)

1. En la ventana de configuración del envío, seleccione la población objetivo.

   ![](assets/line_usecase_02.png)

1. Click **[!UICONTROL Add]** to create your message and select the **[!UICONTROL Message type]**.

   En primer lugar queremos crear un mensaje de texto.

   ![](assets/line_usecase_03.png)

1. Place your cursor in the place where you want to insert the personalized text and click the drop-down icon then select **[!UICONTROL Visitor > First name]**.

   ![](assets/line_usecase_05.png)

1. Follow the same procedure to add an image, selecting **[!UICONTROL Image and links]** in the **[!UICONTROL Message type]** drop-down.

   Añada la URL de imagen.

   ![](assets/line_usecase_07.png)

1. In the **[!UICONTROL Links]** section, select the layout that will divide your image in multiple clickable regions.
1. Asigne una URL a cada región de la imagen.

   ![](assets/line_usecase_08.png)

1. Save your delivery then click **[!UICONTROL Send]** to analyze and send it to the target.

   El envío se manda a los destinatarios.

   ![](assets/line_usecase_06.png)
