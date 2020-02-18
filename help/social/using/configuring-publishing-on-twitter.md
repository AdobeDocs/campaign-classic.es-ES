---
title: Configuración de la publicación en Twitter
seo-title: Configuración de la publicación en Twitter
description: Configuración de la publicación en Twitter
seo-description: null
page-status-flag: never-activated
uuid: 88867881-fb59-4f0d-862e-537d498e9aef
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: social
content-type: reference
topic-tags: configuration
discoiquuid: 9d74ed9c-0055-4556-a205-6e5fea11816b
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 2e18121e4094bc4cb215e5471091810df56b3ef5

---


# Configuración de la publicación en Twitter{#configuring-publishing-on-twitter}

Para que Adobe Campaign pueda enviar tweets a sus cuentas de Twitter, debe delegar el acceso de escritura a Adobe Campaign para estas cuentas. Para ello, aplique los siguientes pasos de configuración:

* Cree una cuenta de Twitter.
* Cree una cuenta de Twitter de prueba para enviar pruebas.
* Cree una aplicación de Twitter por cuenta de Twitter.
* Para cada aplicación de Twitter, cree un nuevo servicio de **[!UICONTROL Twitter]** tipo.

![](assets/social_diagram_twitter_service.png)

## Requisitos previos {#prerequisites}

Comience creando una o varias cuentas de Twitter a las que enviar los tweets.

Para crear una cuenta de Twitter, vaya a [http://twitter.com](http://twitter.com).

## Creación de una cuenta de prueba en Twitter {#creating-a-test-account-on-twitter}

También recomendamos crear una cuenta privada de Twitter que pueda utilizarse para enviar pruebas de tweet (para más información, consulte [Envío de la prueba](../../social/using/publishing-on-twitter.md#sending-the-proof)):

* Cree una nueva cuenta de Twitter.
* Haga clic en el menú en la esquina superior derecha y seleccione **[!UICONTROL Settings]**.
* Seleccione la **[!UICONTROL Security and privacy]** ficha y marque la **[!UICONTROL Protect my Tweets]** casilla.
* Haga clic en el **[!UICONTROL Save Changes]** botón en la parte inferior de la página.

![](assets/social_twitter_test_page.png)

## Creación de una aplicación en Twitter {#creating-an-application-on-twitter}

Para que Adobe Campaign pueda enviar tweets a sus cuentas de Twitter, debe crear una aplicación de Twitter por cuenta de Twitter. Para ello, siga los siguientes pasos:

1. Inicie sesión en su cuenta de Twitter.
1. Escriba la siguiente dirección en el explorador de Internet: [https://apps.twitter.com/](https://apps.twitter.com/).
1. A continuación, haga clic en el **[!UICONTROL Create New App]** botón de la derecha.

   ![](assets/social_create_twitter_app_001.png)

1. Permita que el asistente lo guíe a través del proceso.

   Para que esta aplicación permita a Adobe Campaign enviar tweets a su cuenta, vaya a la **[!UICONTROL Permissions]** ficha de la aplicación y seleccione **[!UICONTROL Read and Write]** la **[!UICONTROL Access]** sección. En la **[!UICONTROL Settings]** ficha, también debe dejar vacío el **[!UICONTROL Callback URL]** campo.

   ![](assets/social_create_twitter_app_002.png)

## Delegación del acceso de escritura a Adobe Campaign {#delegating-write-access-to-adobe-campaign}

Para cada aplicación de Twitter, debe crear un servicio de **[!UICONTROL Twitter]** tipo diferente que incluya la configuración de la aplicación.

Este paso requiere acceso simultáneo a la consola de Adobe Campaign y a un explorador de Internet que haya iniciado sesión en su cuenta de Twitter:

* **Twitter**: seleccione la aplicación creada anteriormente ([https://dev.twitter.com/apps](https://dev.twitter.com/apps)) y haga clic en la **[!UICONTROL Keys and Access Tokens]** ficha.

   ![](assets/social_twitter_service_002.png)

* **Adobe Campaign**: vaya al **[!UICONTROL Profiles and targets]** universo, haga clic en el **[!UICONTROL Services and Subscriptions]** vínculo y haga clic en el **[!UICONTROL Create]** botón.

   ![](assets/social_twitter_service_007.png)

1. Select the **[!UICONTROL Twitter]** type.

   ![](assets/social_twitter_service_008.png)

   >[!NOTE]
   >
   >La **[!UICONTROL Synchronize subscriptions]** opción está activada de forma predeterminada. Cuando se marca la casilla, el flujo de trabajo de sincronización de cuentas de Twitter (consulte [Sincronización de cuentas](#synchronizing-twitter-accounts)de Twitter) recupera la lista de seguidores de Twitter para que pueda enviarles mensajes directos (consulte [Envío de mensajes directos a suscriptores](../../social/using/publishing-on-twitter.md#sending-direct-messages-to-subscribers)). Si no desea recuperar la lista de seguidores, desactive esta casilla.

1. Introduzca la etiqueta y el nombre interno del servicio.

   ![](assets/social_twitter_service_009.png)

   >[!IMPORTANT]
   >
   >El **[!UICONTROL Internal name]** del servicio debe ser idéntico al nombre de la cuenta de Twitter. Para asegurarse de que no hay errores de entrada, aplique los siguientes pasos a continuación.

   * Haga clic en el botón **[!UICONTROL Save]**.
   * En la descripción general de los servicios, haga clic en el servicio de tipo de Twitter que acaba de crear.
   * Select the **[!UICONTROL Twitter page]** tab. Se debe mostrar la cuenta de Twitter.

      ![](assets/social_twitter_service_010.png)

1. En el **[!UICONTROL Visitor folder]** campo, seleccione la carpeta de visitantes en la que se crearán los seguidores. For more on this, refer to [Operating principle](../../social/using/publishing-on-twitter.md#operating-principle). De forma predeterminada, los seguidores se crean en la raíz de la **[!UICONTROL Visitors]** carpeta.

   ![](assets/social_twitter_service_010_b.png)

1. En Twitter, copie el contenido de los campos **[!UICONTROL Consumer Key (API Key)]** y **[!UICONTROL Consumer Secret (API Secret)]** y péguelo en los **[!UICONTROL Consumer key]** campos y **[!UICONTROL Consumer secret]** de la consola.

   ![](assets/social_twitter_service_012.png)

1. En Twitter, copie el contenido de los campos **[!UICONTROL Access Token]** y **[!UICONTROL Access Token Secret]** y péguelo en los **[!UICONTROL Access token]** campos y **[!UICONTROL Access token secret]** de la consola.

   ![](assets/social_twitter_service_013.png)

1. En la consola de Adobe Campaign, haga clic en **[!UICONTROL Save]**. Ya se ha completado la delegación de acceso de escritura a Adobe Campaign.

   ![](assets/social_twitter_service_014.png)

>[!NOTE]
>
>Debe crear un servicio de **[!UICONTROL Twitter]** tipo por aplicación de Twitter.

El flujo de trabajo sincroniza las cuentas de Twitter en Adobe Campaign. **[!UICONTROL Twitter account Synchronization]** Para obtener más información sobre esto, consulte [Sincronización de páginas](../../social/using/publishing-on-facebook-walls.md#synchronizing-facebook-pages)de Facebook.

## Sincronización de cuentas de Twitter {#synchronizing-twitter-accounts}

>[!IMPORTANT]
>
>Para que el flujo de trabajo recupere la lista de suscriptores de Twitter, la **[!UICONTROL Twitter account synchronization]** casilla debe activarse en la sección de edición del servicio vinculado a la cuenta. Para obtener más información sobre esto, consulte [Delegación de acceso de escritura a Adobe Campaign](#delegating-write-access-to-adobe-campaign).

El flujo de trabajo **[!UICONTROL Twitter account synchronization]** , al que se accede a través del **[!UICONTROL Administration > Production > Technical workflows > Managing social networks]** nodo, le permite sincronizar cuentas de Twitter configuradas previamente con Adobe Campaign. De forma predeterminada, este flujo de trabajo se activa todos los jueves a las 7:30 a.m.

>[!NOTE]
>
>Es posible iniciar el flujo de trabajo en cualquier momento ejecutando el procesamiento de tareas previsto. También puede editar el programador para cambiar la frecuencia de activación del flujo de trabajo. For more on the scheduler, refer to [this section](../../workflow/using/scheduler.md).

Ahora puede enviar tweets a sus cuentas de Twitter y mensajes directos a sus seguidores. Para obtener más información sobre esto, consulte: [Publicación en Twitter](../../social/using/publishing-on-twitter.md).
