---
solution: Campaign Classic
product: campaign
title: Configuración de una publicación en Twitter
description: Configuración de una publicación en Twitter
audience: social
content-type: reference
topic-tags: configuration
exl-id: 2d2a6e32-587d-4a7b-ba1c-d9140da53f64
translation-type: ht
source-git-commit: 6854d06f8dc445b56ddfde7777f02916a60f2b63
workflow-type: ht
source-wordcount: '710'
ht-degree: 100%

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

Para crear una cuenta de Twitter, vaya a [https://twitter.com](https://twitter.com).

## Creación de una cuenta de prueba en Twitter {#creating-a-test-account-on-twitter}

También recomendamos crear una cuenta privada de Twitter que pueda utilizar para enviar pruebas de tweet (para más información, consulte [Envío de la prueba](../../social/using/publishing-on-twitter.md#sending-the-proof)):

* Cree una nueva cuenta de Twitter.
* Haga clic en el menú en la esquina superior derecha y seleccione **[!UICONTROL Settings]**.
* Seleccione la pestaña **[!UICONTROL Security and privacy]** y marque la casilla **[!UICONTROL Protect my Tweets]**.
* Haga clic en el botón **[!UICONTROL Save Changes]** en la parte inferior de la página.

![](assets/social_twitter_test_page.png)

## Creación de una aplicación en Twitter {#creating-an-application-on-twitter}

Para que Adobe Campaign pueda enviar tweets a sus cuentas de Twitter, debe crear una aplicación de Twitter por cuenta de Twitter. Para ello, siga los siguientes pasos:

1. Inicie sesión en su cuenta de Twitter.
1. Escriba la siguiente dirección en el explorador de Internet: [https://apps.twitter.com/](https://apps.twitter.com/).
1. Luego, haga clic en el botón **[!UICONTROL Create New App]** de la derecha.

   ![](assets/social_create_twitter_app_001.png)

1. Permita que el asistente lo guíe a través del proceso.

   Para que esta aplicación permita que Adobe Campaign envíe tweets a su cuenta, vaya a la pestaña **[!UICONTROL Permissions]** de la aplicación y seleccione **[!UICONTROL Read and Write]** en la sección **[!UICONTROL Access]**. En la pestaña **[!UICONTROL Settings]**, también debe dejar vacío el campo **[!UICONTROL Callback URL]**.

   ![](assets/social_create_twitter_app_002.png)

## Delegación del acceso de escritura a Adobe Campaign {#delegating-write-access-to-adobe-campaign}

Para cada aplicación de , debe crear un servicio de tipo **[!UICONTROL Twitter]** Twitter diferente que incluya la configuración de la aplicación.

Este paso requiere acceso simultáneo a la consola de Adobe Campaign y a un explorador de Internet que haya iniciado sesión en su cuenta de Twitter:

* **Twitter**: seleccione la aplicación creada anteriormente ([https://dev.twitter.com/apps](https://dev.twitter.com/apps)) y haga clic en la pestaña **[!UICONTROL Keys and Access Tokens]**.

   ![](assets/social_twitter_service_002.png)

* **Adobe Campaign**: vaya a la pestaña **[!UICONTROL Profiles and targets]**, haga clic en el vínculo **[!UICONTROL Services and Subscriptions]** y haga clic en el botón **[!UICONTROL Create]**.

   ![](assets/social_twitter_service_007.png)

1. Seleccione el tipo **[!UICONTROL Twitter]**.

   ![](assets/social_twitter_service_008.png)

   >[!NOTE]
   >
   >La opción **[!UICONTROL Synchronize subscriptions]** está activada de forma predeterminada. Cuando se marca la casilla, el flujo de trabajo de sincronización de cuentas de Twitter (consulte [Sincronización de cuentas de Twitter](#synchronizing-twitter-accounts)) recupera la lista de seguidores de Twitter para que pueda enviarles mensajes directos (consulte [Envío de mensajes directos a suscriptores](../../social/using/publishing-on-twitter.md#sending-direct-messages-to-subscribers)). Si no desea recuperar la lista de seguidores, desactive esta casilla.

1. Introduzca la etiqueta y el nombre interno del servicio.

   ![](assets/social_twitter_service_009.png)

   >[!IMPORTANT]
   >
   >El **[!UICONTROL Internal name]** del servicio debe ser idéntico al nombre de la cuenta de Twitter. Para asegurarse de que no haya errores de entrada, aplique los siguientes pasos a continuación.

   * Haga clic en el botón **[!UICONTROL Save]**.
   * En la descripción general de los servicios, haga clic en el servicio de tipo de Twitter que acaba de crear.
   * Seleccione la pestaña **[!UICONTROL Twitter page]** Se debe mostrar la cuenta de Twitter.

      ![](assets/social_twitter_service_010.png)

1. En el campo **[!UICONTROL Visitor folder]**, seleccione la carpeta del visitante en la que se deben crear los seguidores. Para obtener más información, consulte [Principio de funcionamiento](../../social/using/publishing-on-twitter.md#operating-principle). De forma predeterminada, los seguidores se crean en la raíz de la carpeta **[!UICONTROL Visitors]**.

   ![](assets/social_twitter_service_010_b.png)

1. En Twitter, copie el contenido de los campos **[!UICONTROL Consumer Key (API Key)]** y **[!UICONTROL Consumer Secret (API Secret)]** y péguelo en los campos **[!UICONTROL Consumer key]** y **[!UICONTROL Consumer secret]** de la consola.

   ![](assets/social_twitter_service_012.png)

1. En Twitter, copie el contenido de los campos **[!UICONTROL Access Token]** y **[!UICONTROL Access Token Secret]** y péguelo en los campos **[!UICONTROL Access token]** y **[!UICONTROL Access token secret]** de la consola.

   ![](assets/social_twitter_service_013.png)

1. En la consola de Adobe Campaign, haga clic en **[!UICONTROL Save]**. Ya se ha completado la delegación de acceso de escritura a Adobe Campaign.

   ![](assets/social_twitter_service_014.png)

>[!NOTE]
>
>Debe crear un servicio de tipo **[!UICONTROL Twitter]** por aplicación de Twitter.

El flujo de trabajo **[!UICONTROL Twitter account Synchronization]** sincroniza las cuentas de Twitter en Adobe Campaign. Para obtener más información, consulte [Sincronización de páginas de Facebook](../../social/using/publishing-on-facebook-walls.md#synchronizing-facebook-pages).

## Sincronización de cuentas de Twitter {#synchronizing-twitter-accounts}

>[!IMPORTANT]
>
>Para que el flujo de trabajo recupere la lista de suscriptores de Twitter, se debe marcar la casilla **[!UICONTROL Twitter account synchronization]** en la sección de edición del servicio asociado a la cuenta. Para obtener más información, consulte [Delegación de acceso de escritura a Adobe Campaign](#delegating-write-access-to-adobe-campaign).

El flujo de trabajo **[!UICONTROL Twitter account synchronization]**, al que se accede mediante el nodo **[!UICONTROL Administration > Production > Technical workflows > Managing social networks]**, permite sincronizar cuentas de Twitter configuradas anteriormente con Adobe Campaign. De forma predeterminada, este flujo de trabajo se activa todos los jueves a las 7:30 a.m.

>[!NOTE]
>
>Es posible iniciar el flujo de trabajo en cualquier momento ejecutando el procesamiento de tareas previsto. También puede editar el planificador para cambiar la frecuencia de activación del flujo de trabajo. Para obtener más información sobre el planificador, consulte [esta sección](../../workflow/using/scheduler.md).

Ahora puede enviar tweets a sus cuentas de Twitter y mensajes directos a sus seguidores. Para obtener más información, consulte [Publicación en Twitter](../../social/using/publishing-on-twitter.md).
