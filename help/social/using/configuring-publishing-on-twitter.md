---
title: Configuración de una publicación en Twitter
seo-title: Configuración de una publicación en Twitter
description: Configuración de una publicación en Twitter
seo-description: null
page-status-flag: never-activated
uuid: 88867881-fb59-4f0d-862e-537d498e9aef
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: social
content-type: reference
topic-tags: configuration
discoiquuid: 9d74ed9c-0055-4556-a205-6e5fea11816b
translation-type: tm+mt
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: tm+mt
source-wordcount: '714'
ht-degree: 79%

---


# Configuración de una publicación en Twitter{#configuring-publishing-on-twitter}

Para que Adobe Campaign pueda enviar tweets a sus cuentas de Twitter, debe delegar el acceso de escritura a Adobe Campaign para estas cuentas. Para ello, siga los siguientes pasos de configuración:

* Cree una cuenta de Twitter.
* Cree una cuenta de Twitter de prueba para enviar pruebas.
* Cree una aplicación de Twitter por cuenta de Twitter.
* Para cada aplicación de , cree un nuevo servicio de tipo **[!UICONTROL Twitter]** Twitter.

![](assets/social_diagram_twitter_service.png)

## Requisitos previos {#prerequisites}

Comience creando una o varias cuentas de Twitter a las que desee enviar los tweets.

To create a Twitter account, go to [https://twitter.com](https://twitter.com).

## Creación de una cuenta de prueba en Twitter {#creating-a-test-account-on-twitter}

También recomendamos crear una cuenta privada de Twitter que pueda utilizar para enviar pruebas de tweet (para más información, consulte [Envío de la prueba](../../social/using/publishing-on-twitter.md#sending-the-proof)):

* Cree una nueva cuenta de Twitter.
* Haga clic en el menú en la esquina superior derecha y seleccione **[!UICONTROL Settings]**.
* Select the **[!UICONTROL Security and privacy]** tab, and check the **[!UICONTROL Protect my Tweets]** box.
* Haga clic en el botón **[!UICONTROL Save Changes]** en la parte inferior de la página.

![](assets/social_twitter_test_page.png)

## Creación de una aplicación en Twitter {#creating-an-application-on-twitter}

Para que Adobe Campaign pueda enviar tweets a sus cuentas de Twitter, debe crear una aplicación de Twitter por cuenta de Twitter. Para ello, siga los siguientes pasos:

1. Inicie sesión en su cuenta de Twitter.
1. Escriba la siguiente dirección en el explorador de Internet: [https://apps.twitter.com/](https://apps.twitter.com/).
1. Then click the **[!UICONTROL Create New App]** button on the right.

   ![](assets/social_create_twitter_app_001.png)

1. Permita que el asistente lo guíe a través del proceso.

   Para que esta aplicación permita que Adobe Campaign envíe tweets a su cuenta, vaya a la pestaña **[!UICONTROL Permissions]** de la aplicación y seleccione **[!UICONTROL Read and Write]** en la sección **[!UICONTROL Access]**. In the **[!UICONTROL Settings]** tab, you also need to leave the **[!UICONTROL Callback URL]** field empty.

   ![](assets/social_create_twitter_app_002.png)

## Delegación del acceso de escritura a Adobe Campaign {#delegating-write-access-to-adobe-campaign}

Para cada aplicación de , debe crear un servicio de tipo **[!UICONTROL Twitter]** Twitter diferente que incluya la configuración de la aplicación.

Este paso requiere acceso simultáneo a la consola de Adobe Campaign y a un explorador de Internet que haya iniciado sesión en su cuenta de Twitter:

* **Twitter**: seleccione la aplicación creada anteriormente ([https://dev.twitter.com/apps](https://dev.twitter.com/apps)) y haga clic en la **[!UICONTROL Keys and Access Tokens]** ficha.

   ![](assets/social_twitter_service_002.png)

* **Adobe Campaign**: vaya al **[!UICONTROL Profiles and targets]** universo, haga clic en el **[!UICONTROL Services and Subscriptions]** vínculo y haga clic en el **[!UICONTROL Create]** botón.

   ![](assets/social_twitter_service_007.png)

1. Select the **[!UICONTROL Twitter]** type.

   ![](assets/social_twitter_service_008.png)

   >[!NOTE]
   >
   >The **[!UICONTROL Synchronize subscriptions]** option is enabled by default. Cuando se marca la casilla, el flujo de trabajo de sincronización de cuentas de Twitter (consulte [Sincronización de cuentas de Twitter](#synchronizing-twitter-accounts)) recupera la lista de seguidores de Twitter para que pueda enviarles mensajes directos (consulte [Envío de mensajes directos a suscriptores](../../social/using/publishing-on-twitter.md#sending-direct-messages-to-subscribers)). Si no desea recuperar la lista de seguidores, desactive esta casilla.

1. Introduzca la etiqueta y el nombre interno del servicio.

   ![](assets/social_twitter_service_009.png)

   >[!IMPORTANT]
   >
   >The **[!UICONTROL Internal name]** of the service must be identical to the name of the Twitter account. Para asegurarse de que no haya errores de entrada, aplique los siguientes pasos a continuación.

   * Haga clic en el botón **[!UICONTROL Save]**.
   * En la descripción general de los servicios, haga clic en el servicio de tipo de Twitter que acaba de crear.
   * Seleccione la pestaña **[!UICONTROL Twitter page]** Se debe mostrar la cuenta de Twitter.

      ![](assets/social_twitter_service_010.png)

1. En el campo **[!UICONTROL Visitor folder]**, seleccione la carpeta del visitante en la que se deben crear los seguidores. Para obtener más información, consulte [Principio de funcionamiento](../../social/using/publishing-on-twitter.md#operating-principle). De forma predeterminada, los seguidores se crean en la raíz de la carpeta **[!UICONTROL Visitors]**.

   ![](assets/social_twitter_service_010_b.png)

1. On Twitter, copy the content of the **[!UICONTROL Consumer Key (API Key)]** and **[!UICONTROL Consumer Secret (API Secret)]** fields and paste it into the **[!UICONTROL Consumer key]** and **[!UICONTROL Consumer secret]** fields of the console.

   ![](assets/social_twitter_service_012.png)

1. On Twitter, copy the content of the **[!UICONTROL Access Token]** and **[!UICONTROL Access Token Secret]** fields and paste it into the **[!UICONTROL Access token]** and **[!UICONTROL Access token secret]** fields of the console.

   ![](assets/social_twitter_service_013.png)

1. En la consola de Adobe Campaign, haga clic en **[!UICONTROL Save]**. Ya se ha completado la delegación de acceso de escritura a Adobe Campaign.

   ![](assets/social_twitter_service_014.png)

>[!NOTE]
>
>Debe crear un servicio de tipo **[!UICONTROL Twitter]** por aplicación de Twitter.

The **[!UICONTROL Twitter account Synchronization]** workflow synchronizes Twitter accounts in Adobe Campaign. Para obtener más información, consulte [Sincronización de páginas de Facebook](../../social/using/publishing-on-facebook-walls.md#synchronizing-facebook-pages).

## Sincronización de cuentas de Twitter {#synchronizing-twitter-accounts}

>[!IMPORTANT]
>
>Para que el flujo de trabajo recupere la lista de suscriptores de Twitter, se debe marcar la casilla **[!UICONTROL Twitter account synchronization]** en la sección de edición del servicio asociado a la cuenta. Para obtener más información, consulte [Delegación de acceso de escritura a Adobe Campaign](#delegating-write-access-to-adobe-campaign).

The **[!UICONTROL Twitter account synchronization]** workflow, which is accessed via the **[!UICONTROL Administration > Production > Technical workflows > Managing social networks]** node, lets you synchronize Twitter accounts configured previously with Adobe Campaign. De forma predeterminada, este flujo de trabajo se activa todos los jueves a las 7:30 a.m.

>[!NOTE]
>
>Es posible iniciar el flujo de trabajo en cualquier momento ejecutando el procesamiento de tareas previsto. También puede editar el planificador para cambiar la frecuencia de activación del flujo de trabajo. Para obtener más información sobre el planificador, consulte [esta sección](../../workflow/using/scheduler.md).

Ahora puede enviar tweets a sus cuentas de Twitter y mensajes directos a sus seguidores. Para obtener más información, consulte [Publicación en Twitter](../../social/using/publishing-on-twitter.md).
