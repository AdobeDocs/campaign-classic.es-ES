---
title: Publicación en Twitter
seo-title: Publicación en Twitter
description: Publicación en Twitter
seo-description: null
page-status-flag: never-activated
uuid: 405bce50-a63c-4bd3-8f03-c71809bb1cfd
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: social
content-type: reference
topic-tags: publishing-on-facebook-twitter
discoiquuid: 2dc278ce-477c-493d-8abb-8bbdf2e988a5
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 20174427735b90129cd4cbd9ee1ba5fd705fa302

---


# Publicación en Twitter{#publishing-on-twitter}

## Publicación en sus cuentas de Twitter {#publishing-on-your-twitter-accounts}

Una vez completada la configuración, Social Marketing le permite enviar tweets a sus cuentas de Twitter.

### Limitaciones {#limitations}

Las siguientes limitaciones son restricciones inherentes a Twitter.

* El mensaje no puede exceder los 140 caracteres.
* No se admite el formato HTML.

### Creación del envío {#creating-the-delivery}

Cree una nueva entrega basada en la plantilla de envío **[!UICONTROL Tweet (twitter)]** .

![](assets/social_twitter_delivery_001.png)

### Selección del objetivo principal {#selecting-the-main-target}

Seleccione las cuentas a las que desee enviar tweets.

1. Haga clic en el **[!UICONTROL To]** vínculo.

   ![](assets/social_twitter_delivery_002.png)

1. Haga clic en el botón **[!UICONTROL Add]**.

   ![](assets/social_twitter_delivery_006.png)

1. Select **[!UICONTROL A Twitter account]**.

   ![](assets/social_twitter_delivery_007.png)

1. En el **[!UICONTROL Folder]** campo, seleccione la carpeta de servicio que contiene la cuenta de Twitter. A continuación, seleccione la cuenta de Twitter a la que desee enviar el tweet.

   ![](assets/social_twitter_delivery_011.png)

### Selección del objetivo de la prueba {#selecting-the-target-of-the-proof}

La **[!UICONTROL Target of the proofs]** ficha permite definir la cuenta de Twitter que se utilizará para las entregas de prueba antes de la entrega final. Por lo tanto, recomendamos crear una cuenta privada de Twitter dedicada al envío de pruebas. Para obtener más información sobre cómo crear una cuenta privada de Twitter, consulte [Creación de una cuenta de prueba en Twitter](../../social/using/configuring-publishing-on-twitter.md#creating-a-test-account-on-twitter). Los pasos para seleccionar el objetivo de prueba son los mismos que para seleccionar el objetivo principal. Consulte [Creación de una cuenta de prueba en Twitter](../../social/using/configuring-publishing-on-twitter.md#creating-a-test-account-on-twitter).

![](assets/social_twitter_delivery_004.png)

>[!NOTE]
>
>Si utiliza la misma cuenta de prueba de Twitter para todas las entregas, puede guardar el destino de prueba en la plantilla de envío, a la que se accede a través del **[!UICONTROL Tweet]** **[!UICONTROL Resources > Templates > Delivery templates]** nodo. El objetivo de prueba se especificará de forma predeterminada para cada nueva entrega.

### Definición del contenido del mensaje {#defining-the-message-content}

Escriba el contenido del tweet en la **[!UICONTROL Content]** ficha.

![](assets/social_twitter_delivery_005.png)

### Visualización de la vista previa {#viewing-the-preview}

La **[!UICONTROL Preview]** ficha permite ver una representación del tweet.

1.  Haga clic en la **[!UICONTROL Preview]** ficha.
1. Haga clic en el menú **[!UICONTROL Test personalization]** desplegable y seleccione **[!UICONTROL Service]**.
1. En el **[!UICONTROL Folder]** campo, seleccione la carpeta de servicio que contiene su cuenta de Twitter.
1. Elija la cuenta de Twitter con la que desea probar la vista previa.

![](assets/social_twitter_delivery_008.png)

>[!NOTE]
>
>La vista previa puede diferir ligeramente del tweet final. Recomendamos encarecidamente enviar una prueba antes de la entrega final para ver una representación exacta del tweet. Consulte [Envío de la prueba](#sending-the-proof).

### Configuración del seguimiento {#configuring-tracking}

El seguimiento se puede ver en los informes de envío y en la **[!UICONTROL Edit > Tracking]** ficha del envío y el servicio.

La configuración de seguimiento es la misma que para un envío de correo electrónico. Para obtener más información, consulte [esta sección](../../delivery/using/monitoring-a-delivery.md).

>[!NOTE]
>
>En la plantilla de envío, el seguimiento está habilitado de forma predeterminada. **[!UICONTROL Tweet]**

>[!CAUTION]
>
>No podemos distinguir entre robots que analizan tweets y usuarios que hacen clic.

### Envío de la prueba {#sending-the-proof}

Le recomendamos encarecidamente que envíe una prueba de su publicación antes de la entrega final para obtener una representación exacta de la publicación en una página privada de prueba de Twitter. Para obtener más información sobre la creación de una cuenta privada de Twitter, consulte [Creación de una cuenta de prueba en Twitter](../../social/using/configuring-publishing-on-twitter.md#creating-a-test-account-on-twitter). Los pasos para seleccionar el objetivo de prueba se detallan en [Selección del objetivo de la prueba](#selecting-the-target-of-the-proof).

La entrega de la prueba es idéntica a las entregas por correo electrónico. Consulte [esta sección](../../delivery/using/steps-validating-the-delivery.md#sending-a-proof).

### Envío del mensaje {#sending-the-message}

1. Una vez aprobado el contenido, haga clic en el **[!UICONTROL Send]** botón .
1. Seleccione **[!UICONTROL Deliver as soon as possible]** y haga clic en el **[!UICONTROL Analyze]** botón.

   >[!NOTE]
   >
   >La **[!UICONTROL Postpone the delivery]** opción le permite posponer el envío a una fecha posterior.

   ![](assets/social_twitter_delivery_012.png)

1. Una vez finalizado el análisis, compruebe el resultado.
1. Haga clic en **[!UICONTROL Confirm delivery]** y luego en **[!UICONTROL Yes]**.

![](assets/social_facebook_delivery_016.png)

## Envío de mensajes directos a los suscriptores {#sending-direct-messages-to-subscribers}

### Principio de funcionamiento {#operating-principle}

El **[!UICONTROL Synchronize Twitter accounts]** flujo de trabajo (consulte [Sincronización de cuentas](../../social/using/configuring-publishing-on-twitter.md#synchronizing-twitter-accounts)de Twitter) recupera la lista de suscriptores de Twitter para que pueda enviarles mensajes directos. Los seguidores recuperados se almacenan en una tabla específica: la tabla de visitantes. Para mostrar la lista de seguidores de Twitter, vaya al **[!UICONTROL Profiles and Targets > Visitors]** nodo.

![](assets/social_twitter_visitors_001.png)

>[!CAUTION]
>
>Para que el flujo de trabajo pueda recuperar la lista de seguidores de Twitter, la **[!UICONTROL Synchronize Twitter accounts]** casilla debe activarse en la pantalla Editar del servicio vinculado a la cuenta. Para obtener más información sobre esto, consulte: [Delegación del acceso de escritura a Adobe Campaign](../../social/using/configuring-publishing-on-twitter.md#delegating-write-access-to-adobe-campaign).

Para cada seguidor, Adobe Campaign recupera la siguiente información:

* **[!UICONTROL Origin]**:: nombre de la red social (**Twitter** en este caso)
* **[!UICONTROL External ID]**:: identificador de usuario
* **[!UICONTROL User name]**:: nombre de cuenta del usuario
* **[!UICONTROL Full name]**:: nombre del usuario
* **[!UICONTROL Language]**:: idioma del usuario
* **[!UICONTROL Number of friends]**:: número de seguidores
* **[!UICONTROL Time zone]**:: zona horaria del usuario
* **[!UICONTROL Verified]**:: este campo indica si el usuario tiene una cuenta de Twitter verificada

### Limitaciones {#limitations-1}

Las siguientes limitaciones son restricciones inherentes a Twitter.

* El mensaje no puede exceder los 140 caracteres.
* No se admite HTML.
* No puede enviar más de 250 mensajes directos al día. Para evitar superar este umbral, puede realizar entregas en varias ondas. Las entregas en oleadas están configuradas como las entregas por correo electrónico. Para obtener más información, consulte [esta sección](../../delivery/using/steps-sending-the-delivery.md#sending-using-multiple-waves).

### Creación del envío {#creating-the-delivery-}

Cree una nueva entrega basada en la plantilla de envío **[!UICONTROL Tweet (Direct Message)]** .

![](assets/social_twitter_delivery_010.png)

### Selección del objetivo principal {#selecting-the-main-target-1}

Seleccione los seguidores a los que desee enviar el mensaje directo.

1. Haga clic en el **[!UICONTROL To]** vínculo.

   ![](assets/social_twitter_delivery_016.png)

1. Haga clic en el botón **[!UICONTROL Add]**.

   ![](assets/social_twitter_delivery_006.png)

1. Seleccione un tipo de objetivo.

   ![](assets/social_twitter_delivery_017.png)

   * Seleccione **[!UICONTROL Twitter subscribers]** enviar un mensaje directo a todos los seguidores de la cuenta.

      >[!CAUTION]
      >
      >No puede enviar más de 250 mensajes al día. Si su cuenta de Twitter tiene más de 250 seguidores, le recomendamos encarecidamente que realice entregas en oleadas. Esto implica el mismo proceso que los envíos por correo electrónico. Consulte [esta sección](../../delivery/using/steps-sending-the-delivery.md#sending-using-multiple-waves).

   * Seleccione **[!UICONTROL Filter conditions]** para definir una consulta y ver su resultado. Esta opción es la misma que para los envíos por correo electrónico. Consulte [esta sección](../../platform/using/defining-filter-conditions.md) para obtener más información.

      ![](assets/social_twitter_delivery_018.png)

### Selección del objetivo de la prueba {#selecting-the-target-of-the-proof-1}

La **[!UICONTROL Target of the proofs]** ficha permite seleccionar el seguidor que recibirá la prueba del mensaje directo. El proceso de selección es el mismo que para el objetivo principal. Consulte [Selección del destino](#selecting-the-main-target)principal.

![](assets/social_twitter_delivery_020.png)

>[!NOTE]
>
>Si desea enviar todas las pruebas de mensajes directos al mismo seguidor de Twitter, puede guardar el destino de prueba en la plantilla de envío, a la que se accede a través del **[!UICONTROL Tweet (Direct Message)]** **[!UICONTROL Resources > Templates > Delivery templates]** nodo. El objetivo de prueba se especificará de forma predeterminada para cada nueva entrega.

### Definición del contenido del mensaje {#defining-message-content-}

Introduzca el contenido del tweet en la **[!UICONTROL Content]** ficha.

![](assets/social_twitter_delivery_015.png)

Los campos de personalización se pueden usar del mismo modo que para las entregas por correo electrónico, por ejemplo, para agregar el nombre del seguidor en el cuerpo del mensaje. La personalización del contenido se detalla en [esta sección](../../delivery/using/about-personalization.md).

![](assets/social_twitter_delivery_021.png)

Los siguientes pasos son los mismos que para enviar un tweet a una cuenta de Twitter. Consulte [Publicación en sus cuentas](#publishing-on-your-twitter-accounts)de Twitter.
