---
title: Publicación en muros de Facebook
seo-title: Publicación en muros de Facebook
description: Publicación en muros de Facebook
seo-description: null
page-status-flag: never-activated
uuid: 02288473-a0d7-42b5-9f86-3c96550ab1a8
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: social
content-type: reference
topic-tags: configuration
discoiquuid: 8577db0b-f1fc-41af-aa0f-ec4d02dac376
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 0386ae88a1b4d9ebda64283d874e01b14e9e5af4
workflow-type: tm+mt
source-wordcount: '941'
ht-degree: 76%

---


# Publicación en muros de Facebook{#publishing-on-facebook-walls}

Para que Adobe Campaign pueda enviar publicaciones a los muros de Facebook, debe delegar el acceso de escritura para estas páginas a Adobe Campaign. Esto implica los siguientes pasos de configuración:

1. Cree una cuenta de Facebook con una o varias páginas.
1. Cree una página de prueba de Facebook para enviar pruebas.
1. Cree una aplicación de Facebook.
1. Introduzca la configuración de la aplicación de Facebook en Adobe Campaign, en la cuenta externa de **[!UICONTROL Facebook routing]**.

## Requisitos previos {#prerequisites}

Comience creando una cuenta de Facebook y varias páginas: se van a utilizar para enviar publicaciones.

* Para crear una cuenta de Facebook, utilice el vínculo [https://www.facebook.com](https://www.facebook.com).
* To create a Facebook page, use the [https://www.facebook.com/pages/create](https://www.facebook.com/pages/create) link.

   Se recomienda usar la misma cuenta de Facebook para administrar todas las páginas. De este modo solo necesita una aplicación de Facebook y una cuenta externa para escribir en todas las páginas de la cuenta.

   ![](assets/social_diagram_fb_external_account.png)

## Creación de una página de Facebook de prueba {#creating-a-test-facebook-page}

Se recomienda crear una página privada de Facebook para enviar pruebas de publicación (para obtener más información, consulte [Envío de la prueba](../../social/using/publishing-on-facebook.md#sending-the-proof).

1. Inicie sesión en la cuenta de Facebook que utiliza para administrar sus páginas.
1. Cree una nueva página de Facebook.
1. Haga clic en el botón **[!UICONTROL Settings]** en la esquina superior derecha.
1. In the **[!UICONTROL General]** tab, modify the page&#39;s visibility parameters: check the **[!UICONTROL Page unpublished]** box.
1. Haga clic en el botón **[!UICONTROL Save Changes]**.

![](assets/social_facebook_test_page.png)

## Creación de una aplicación de Facebook {#creating-a-facebook-application}

Para que Adobe Campaign pueda publicar en los muros de sus páginas, debe crear una aplicación de Facebook. Para ello, siga los siguientes pasos:

1. Inicie sesión en la cuenta de Facebook que utiliza para administrar páginas.
1. Escriba la siguiente dirección en el explorador: [https://developers.facebook.com/apps](https://developers.facebook.com/apps).

   >[!IMPORTANT]
   >
   >Según el tipo de cuenta que tenga, puede que se necesiten una o más autorizaciones.
   >
   >Para crear una aplicación de Facebook, necesita una cuenta de Facebook **verificada**.

1. Click the **[!UICONTROL Add a New App]** button in the top right-hand corner of the page. Introduzca un nombre de aplicación y un correo electrónico de contacto. Luego, pase la comprobación de seguridad.

   ![](assets/social_create_facebook_app_002.png)

1. En **[!UICONTROL Settings > Basic]**, haga clic en **[!UICONTROL Add a platform]** y seleccione el **[!UICONTROL Facebook Web Games]** tipo.

   ![](assets/social_create_facebook_app_003.png)

1. In the **[!UICONTROL Products]** section, in the left menu, check that you see the **[!UICONTROL Facebook Login]** product. If not, add a new product and select **[!UICONTROL Facebook Login]**.

   ![](assets/social_create_facebook_app_003bis.png)

1. Una vez creada la aplicación, seleccione la pestaña **[!UICONTROL App Review]** y publique la aplicación.

   ![](assets/social_create_facebook_app_004.png)

## Delegación del acceso de escritura a Adobe Campaign {#delegating-write-access-to-adobe-campaign}

Para delegar el acceso de escritura a Adobe Campaign para publicarlo en los muros de sus páginas, debe introducir los parámetros de la aplicación de Facebook creada anteriormente.

Este paso requiere acceso a la consola de Adobe Campaign y a un explorador de Internet que haya iniciado sesión en la cuenta de Facebook que utilice para la administración de páginas:

>[!IMPORTANT]
>
>El operador de Adobe Campaign debe tener derechos de administración para llevar a cabo esta configuración.

* **Facebook**: seleccione la aplicación creada anteriormente ([https://developers.facebook.com/apps](https://developers.facebook.com/apps)) y seleccione la pestaña **[!UICONTROL Settings > Basic]**.

   ![](assets/social_facebook_external_account_002.png)

   >[!NOTE]
   >
   >If the **[!UICONTROL Facebook Web Games]** section does not appear, click the **[!UICONTROL Add Platform]** button, at the bottom of the page, and select **[!UICONTROL Facebook Web Games]**.

* **Adobe Campaign**: vaya al **[!UICONTROL Administration > Platform > External Accounts]** nodo del árbol, seleccione la **[!UICONTROL Facebook routing]** cuenta externa y haga clic en la **[!UICONTROL Connector]** ficha.

   ![](assets/social_facebook_external_account_001.png)

1. In the Adobe Campaign console, copy the address contained in the **[!UICONTROL Secure Canvas URL]** field and paste it into the **[!UICONTROL Secure Web Games URL (https)]** field on Facebook (in the **[!UICONTROL Facebook Web Games]** section).

   ![](assets/social_facebook_external_account_006.png)

   >[!IMPORTANT]
   >
   >Evite utilizar la dirección URL no segura bajo cualquier circunstancia.

   Copie y pegue esta dirección URL también en **[!UICONTROL Products]** > **[!UICONTROL Facebook Login]** > **[!UICONTROL Settings]** > **[!UICONTROL Valid OAuth Redirect URIs]**. To check the validity of the URL, save the application, copy and paste the URL in the **[!UICONTROL Redirect URI to Check]** field and click on **[!UICONTROL Check URI]**.

   ![](assets/social_facebook_external_account_007bis.png)

1. En Facebook, copie el contenido de los campos **[!UICONTROL App ID]** y **[!UICONTROL App Secret]** y péguelo en los campos coincidentes de la consola.

   ![](assets/social_facebook_external_account_007.png)

1. En Facebook, haga clic en el botón **[!UICONTROL Save Changes]** en la parte inferior de la página.
1. Vaya a la consola de Adobe Campaign y guarde la cuenta externa.

   >[!NOTE]
   >
   >The **[!UICONTROL Marketing URL]** field is optional.

1. In the Adobe Campaign console, click the **[!UICONTROL Request the authorization from the application]** link at the bottom of the **[!UICONTROL Connector]** tab. El flujo de trabajo **[!UICONTROL Synchronize Facebook pages]** se activa automáticamente y recopila todas las páginas de Facebook gestionadas por el administrador. Para obtener más información, consulte [Sincronización de páginas de Facebook](#synchronizing-facebook-pages).

   ![](assets/social_facebook_external_account_004.png)

   >[!NOTE]
   >
   >By default, the pages are added to the **[!UICONTROL Facebook]** service folder, available via the **[!UICONTROL Profiles and Targets > Services and Subscriptions]** node. El campo **[!UICONTROL Folder]** de la pestaña **[!UICONTROL Connector]** permite cambiar la carpeta de servicio en la que se crean las páginas de Facebook después de la sincronización. También puede seleccionar las páginas de Facebook que desea sincronizar en Adobe Campaign gracias al campo **[!UICONTROL Filter]**. Si deja este campo vacío, se sincronizan todas las páginas de Facebook gestionadas por el administrador.

1. Se muestra un cuadro de diálogo con los diferentes ajustes de permisos de Facebook. Esto permite a Adobe Campaign enviar publicaciones a las páginas de cuenta de Facebook.

   Acepte las distintas solicitudes de permiso.

   ![](assets/social_facebook_external_account_003.png)

1. Se ha concedido a Adobe Campaign el derecho de publicar en los muros de las páginas de la cuenta de Facebook.

   ![](assets/social_facebook_external_account_011.png)

>[!NOTE]
>
>Si la cuenta de Facebook administra varias páginas, simplemente configure una cuenta externa para escribir en cualquier página de la cuenta de Facebook. Para cada nueva cuenta de Facebook, debe crear una nueva cuenta externa de tipo **[!UICONTROL Routing]**.

El flujo de trabajo **[!UICONTROL Synchronization of Facebook pages]** sincroniza todas las páginas administradas por la cuenta de Facebook, para permitirle publicar en su muro directamente a través de Adobe Campaign. Para obtener más información, consulte [Sincronización de páginas de Facebook](#synchronizing-facebook-pages).

## Sincronización de páginas de Facebook {#synchronizing-facebook-pages}

The **[!UICONTROL Synchronization of Facebook pages]** workflow, which is accessed via the **[!UICONTROL Administration > Production > Technical workflows > Managing social networks]** node, lets you synchronize (in Adobe Campaign) the pages of the Facebook account configured previously. De forma predeterminada, este flujo de trabajo está configurado para ejecutarse una vez al día o siempre que un administrador haga clic en el vínculo **[!UICONTROL Request an authorization from the application]** en la pantalla de configuración del servicio (consulte [Delegación de acceso de escritura a Adobe Campaign](#delegating-write-access-to-adobe-campaign)).

Una vez finalizada la sincronización, las páginas recopiladas aparecen en la carpeta de servicios introducida en la cuenta externa (consulte [Delegación del acceso de escritura a Adobe Campaign](#delegating-write-access-to-adobe-campaign)). By default, pages are added to the root of the **[!UICONTROL Facebook]** service folder which is available via the **[!UICONTROL Profiles and Targets > Services and subscriptions]** menu.

![](assets/social_facebook_service_002.png)

Ahora puede publicar en los muros de sus páginas de Facebook directamente a través de Adobe Campaign. Para obtener más información, consulte [Publicación en Facebook](#publishing-on-facebook-walls).
