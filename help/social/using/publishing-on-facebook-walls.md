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
source-git-commit: 2e18121e4094bc4cb215e5471091810df56b3ef5

---


# Publicación en muros de Facebook{#publishing-on-facebook-walls}

Para que Adobe Campaign pueda enviar publicaciones a los muros de Facebook, debe delegar el acceso de escritura para estas páginas a Adobe Campaign. Esto implica los siguientes pasos de configuración:

1. Cree una cuenta de Facebook con una o varias páginas.
1. Cree una página de prueba de Facebook para enviar pruebas.
1. Cree una aplicación de Facebook.
1. Introduzca la configuración de la aplicación de Facebook en Adobe Campaign, en la cuenta **[!UICONTROL Facebook routing]** externa.

## Requisitos previos {#prerequisites}

Comience creando una cuenta de Facebook y varias páginas: se utilizarán para enviar publicaciones.

* Para crear una cuenta de Facebook, utilice el vínculo [https://www.facebook.com](https://www.facebook.com) .
* Para crear una página de Facebook, utilice el vínculo [https://www.facebook.com/pages/create.php](https://www.facebook.com/pages/create.php) .

   Recomendamos usar la misma cuenta de Facebook para administrar todas las páginas. De este modo solo necesitará una aplicación de Facebook y una cuenta externa para escribir en todas las páginas de la cuenta.

   ![](assets/social_diagram_fb_external_account.png)

## Creación de una página de Facebook de prueba {#creating-a-test-facebook-page}

Recomendamos crear una página privada de Facebook para entregar pruebas de publicación (para obtener más información sobre esto, consulte [Envío de la prueba](#sending-the-proof)).

1. Inicie sesión en la cuenta de Facebook que utiliza para administrar sus páginas.
1. Cree una nueva página de Facebook.
1. Haga clic en el **[!UICONTROL Settings]** botón en la esquina superior derecha.
1. En la **[!UICONTROL General]** ficha, modifique los parámetros de visibilidad de la página: marque la **[!UICONTROL Page unpublished]** casilla.
1. Haga clic en el botón **[!UICONTROL Save Changes]**.

![](assets/social_facebook_test_page.png)

## Creación de una aplicación de Facebook {#creating-a-facebook-application}

Para que Adobe Campaign pueda publicar en los muros de sus páginas, debe crear una aplicación de Facebook. Para ello, siga los siguientes pasos:

1. Inicie sesión en la cuenta de Facebook que utiliza para administrar páginas.
1. Escriba la siguiente dirección en el explorador: [https://developers.facebook.com/apps](https://developers.facebook.com/apps).

   >[!IMPORTANT]
   >
   >Según el tipo de cuenta que tenga, puede que sea necesaria una o más autorizaciones.
   >
   >Para crear una aplicación de Facebook, necesitará una cuenta de Facebook **verificada** .

1. Haga clic en el **[!UICONTROL Add a New App]** botón en la esquina superior derecha de la página. Introduzca un nombre de aplicación y un correo electrónico de contacto y, a continuación, pase la comprobación de seguridad.

   ![](assets/social_create_facebook_app_002.png)

1. En **[!UICONTROL Settings > Basic]**, haga clic en **[!UICONTROL Add a platform]** y seleccione el **[!UICONTROL Facebook Web Games]** tipo.

   ![](assets/social_create_facebook_app_003.png)

1. En la **[!UICONTROL Products]** sección del menú de la izquierda, compruebe que ve el **[!UICONTROL Facebook Login]** producto. Si no es así, agregue un nuevo producto y seleccione **[!UICONTROL Facebook Login]**.

   ![](assets/social_create_facebook_app_003bis.png)

1. Una vez creada la aplicación, seleccione la **[!UICONTROL App Review]** ficha y publíquela.

   ![](assets/social_create_facebook_app_004.png)

## Delegación del acceso de escritura a Adobe Campaign {#delegating-write-access-to-adobe-campaign}

Para delegar el acceso de escritura a Adobe Campaign para publicarlo en los muros de sus páginas, debe introducir los parámetros de la aplicación de Facebook creada anteriormente.

Este paso requiere acceso a la consola de Adobe Campaign y a un explorador de Internet que haya iniciado sesión en la cuenta de Facebook que utilice para la administración de páginas:

>[!IMPORTANT]
>
>El operador de Adobe Campaign debe tener derechos de administración para llevar a cabo esta configuración.

* **Facebook**: seleccione la aplicación creada anteriormente ( [https://developers.facebook.com/apps](https://developers.facebook.com/apps)) y seleccione la **[!UICONTROL Settings > Basic]** ficha.

   ![](assets/social_facebook_external_account_002.png)

   >[!NOTE]
   >
   >Si la **[!UICONTROL Facebook Web Games]** sección no aparece, haga clic en el **[!UICONTROL Add Platform]** botón, en la parte inferior de la página, y seleccione **[!UICONTROL Facebook Web Games]**.

* **Adobe Campaign**: vaya al **[!UICONTROL Administration > Platform > External Accounts]** nodo del árbol, seleccione la cuenta **[!UICONTROL Facebook routing]** externa y haga clic en la **[!UICONTROL Connector]** ficha.

   ![](assets/social_facebook_external_account_001.png)

1. En la consola de Adobe Campaign, copie la dirección contenida en el **[!UICONTROL Secure Canvas URL]** campo y péguela en el **[!UICONTROL Secure Web Games URL (https)]** campo de Facebook (en la **[!UICONTROL Facebook Web Games]** sección).

   ![](assets/social_facebook_external_account_006.png)

   >[!IMPORTANT]
   >
   >No debe utilizar la dirección URL no segura bajo ninguna circunstancia.

   Copie y pegue esta dirección URL también en **[!UICONTROL Products]** > **[!UICONTROL Facebook Login]** > **[!UICONTROL Settings]** > **[!UICONTROL Valid OAuth Redirect URIs]**. Para comprobar la validez de la URL, guarde la aplicación, copie y pegue la URL en el **[!UICONTROL Redirect URI to Check]** campo y haga clic en **[!UICONTROL Check URI]**.

   ![](assets/social_facebook_external_account_007bis.png)

1. En Facebook, copie el contenido de los campos **[!UICONTROL App ID]** y **[!UICONTROL App Secret]** y péguelo en los campos coincidentes de la consola.

   ![](assets/social_facebook_external_account_007.png)

1. En Facebook, haga clic en el **[!UICONTROL Save Changes]** botón en la parte inferior de la página.
1. Vaya a la consola de Adobe Campaign y guarde la cuenta externa.

   >[!NOTE]
   >
   >El **[!UICONTROL Marketing URL]** campo es opcional.

1. En la consola de Adobe Campaign, haga clic en el **[!UICONTROL Request the authorization from the application]** vínculo situado en la parte inferior de la **[!UICONTROL Connector]** ficha. El flujo de trabajo se activa automáticamente y recopila todas las páginas de Facebook administradas por el administrador. **[!UICONTROL Synchronize Facebook pages]** Para obtener más información sobre esto, consulte [Sincronización de páginas](#synchronizing-facebook-pages)de Facebook.

   ![](assets/social_facebook_external_account_004.png)

   >[!NOTE]
   >
   >De forma predeterminada, las páginas se agregan a la carpeta de **[!UICONTROL Facebook]** servicio, disponible a través del **[!UICONTROL Profiles and Targets > Services and Subscriptions]** nodo. El **[!UICONTROL Folder]** campo de la **[!UICONTROL Connector]** ficha permite cambiar la carpeta de servicio en la que se crean las páginas de Facebook después de la sincronización. También puede seleccionar las páginas de Facebook que desea sincronizar en Adobe Campaign gracias al **[!UICONTROL Filter]** campo. Si deja este campo vacío, se sincronizarán todas las páginas de Facebook administradas por el administrador.

1. Se muestra un cuadro de diálogo con los diferentes ajustes de permisos de Facebook. Esto permite a Adobe Campaign enviar publicaciones a las páginas de cuenta de Facebook.

   Acepte las distintas solicitudes de permiso.

   ![](assets/social_facebook_external_account_003.png)

1. Se ha concedido a Adobe Campaign el derecho de publicar en los muros de las páginas de la cuenta de Facebook.

   ![](assets/social_facebook_external_account_011.png)

>[!NOTE]
>
>Si la cuenta de Facebook administra varias páginas, simplemente configure una cuenta externa para escribir en cualquier página de la cuenta de Facebook. Para cada nueva cuenta de Facebook, deberá crear un nuevo **[!UICONTROL Routing]** tipo de cuenta externa.

El flujo de trabajo sincroniza todas las páginas administradas por la cuenta de Facebook para permitirle publicar en su muro directamente a través de Adobe Campaign. **[!UICONTROL Synchronization of Facebook pages]** Para obtener más información sobre esto, consulte [Sincronización de páginas](#synchronizing-facebook-pages)de Facebook.

## Sincronización de páginas de Facebook {#synchronizing-facebook-pages}

El flujo de trabajo **[!UICONTROL Synchronization of Facebook pages]** , al que se accede a través del **[!UICONTROL Administration > Production > Technical workflows > Managing social networks]** nodo, permite sincronizar (en Adobe Campaign) las páginas de la cuenta de Facebook configurada previamente. De forma predeterminada, este flujo de trabajo está configurado para ejecutarse una vez al día o siempre que un administrador haga clic en el **[!UICONTROL Request an authorization from the application]** vínculo en la pantalla de configuración del servicio (consulte [Delegación de acceso de escritura a Adobe Campaign](#delegating-write-access-to-adobe-campaign)).

Una vez finalizada la sincronización, las páginas recopiladas aparecen en la carpeta de servicios introducida en la cuenta externa (consulte [Delegación del acceso de escritura a Adobe Campaign](#delegating-write-access-to-adobe-campaign)). De forma predeterminada, las páginas se agregan a la raíz de la carpeta del **[!UICONTROL Facebook]** servicio, que está disponible a través del **[!UICONTROL Profiles and Targets > Services and subscriptions]** menú.

![](assets/social_facebook_service_002.png)

Ahora puede publicar en los muros de sus páginas de Facebook directamente a través de Adobe Campaign. Para obtener más información sobre esto, consulte [Publicación en Facebook](#publishing-on-facebook-walls).
