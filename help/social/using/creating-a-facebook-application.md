---
title: Creación de una aplicación de Facebook
seo-title: Creación de una aplicación de Facebook
description: Creación de una aplicación de Facebook
seo-description: null
page-status-flag: never-activated
uuid: f02129b9-6f64-41ee-8b56-d85211a58f69
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: social
content-type: reference
topic-tags: configuration
discoiquuid: c1d880bb-256e-451c-8c52-198711907f8e
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 2e18121e4094bc4cb215e5471091810df56b3ef5

---


# Creación de una aplicación de Facebook{#creating-a-facebook-application}

Gracias a las aplicaciones web, Social Marketing permite mostrar contenido personalizado en las aplicaciones de Facebook, lo que facilita la adquisición de posibles clientes a través de esta red social. Para obtener más ejemplos de aplicaciones web de tipo Facebook, consulte [Ejemplos de aplicaciones](../../social/using/examples-of-facebook-apps.md)de Facebook.

>[!NOTE]
>
>También es posible integrar Adobe Campaign con una aplicación de Facebook desarrollada por un socio. En este caso, no es necesario utilizar la aplicación web de Adobe Campaign para adquirir perfiles de Facebook. For more on this, refer to [Configuring external accounts](#configuring-external-accounts).

![](assets/social_webapp_fb_000.png)

Aplique los siguientes pasos de configuración:

1. Cree una o varias aplicaciones de Facebook. Para obtener más información sobre esto, consulte: [Creación de una aplicación](../../social/using/publishing-on-facebook-walls.md#creating-a-facebook-application)de Facebook.
1. Introduzca los vínculos **[!UICONTROL terms of service]** y **[!UICONTROL Privacy policy]** que se mostrarán en la pantalla de solicitud de permisos de Facebook. Para obtener más información sobre esto, consulte: [Introducción de los enlaces](#entering-the-terms-of-service-and-privacy-policy-links)de Condiciones de servicio y Política de privacidad.
1. Para cada aplicación de Facebook, cree una cuenta **[!UICONTROL Facebook Connect]** de tipo externo. For more on this, refer to: [Configuring external accounts](#configuring-external-accounts).
1. Para cada aplicación de Facebook, cree una aplicación web de tipo Facebook en Adobe Campaign. Para obtener más información sobre esto, consulte: [Creación de una aplicación](#creating-a-facebook-type-web-application)web de tipo Facebook.
1. Configure las aplicaciones de Facebook para que se muestren como fichas en la página de Facebook. For more on this, refer to: [Configuring Facebook tabs](#configuring-facebook-tabs).

## Configuración de cuentas externas {#configuring-external-accounts}

For each Facebook application, you need to create a **[!UICONTROL Facebook Connect]** type external account.

Este paso requiere acceso a la consola de Adobe Campaign y a un explorador de Internet que haya iniciado sesión en la cuenta de Facebook que utilice para la administración de páginas:

* **Facebook**: seleccione la aplicación creada anteriormente ( [https://developers.facebook.com/apps](https://developers.facebook.com/apps)) y seleccione la **[!UICONTROL Settings]** > **[!UICONTROL Basic]** ficha.

   ![](assets/social_webapp_fb_008.png)

   >[!NOTE]
   >
   >Si la **[!UICONTROL Facebook Web Games]** sección no aparece, haga clic en el **[!UICONTROL Add Platform]** botón, en la parte inferior de la página, y seleccione **[!UICONTROL Facebook Web Games]**.

* **Adobe Campaign**: vaya al **[!UICONTROL Administration > Platform > External accounts]** nodo del árbol y haga clic en **[!UICONTROL New]**.

   ![](assets/social_webapp_fb_005.png)

1. Introduzca una etiqueta y un nombre interno y seleccione el **[!UICONTROL Facebook Connect]** tipo.

   ![](assets/social_webapp_fb_006.png)

1. Seleccione un modo de alojamiento para la aplicación: **[!UICONTROL hosted by a partner]** o **[!UICONTROL hosted by this instance]**.

   ![](assets/social_webapp_fb_012.png)

   **Aplicación alojada por un socio**

   Es posible integrar Adobe Campaign con una aplicación de Facebook desarrollada por un socio. En este caso, no es necesario utilizar las aplicaciones web de Adobe Campaign para adquirir perfiles de Facebook. Cuando el usuario de Facebook instala la aplicación, se genera una clave (autentificador de acceso). El socio reenvía este autentificador de acceso a Adobe Campaign llamando a un servicio web. A continuación, Adobe Campaign utiliza este token para iniciar sesión en la base de datos de Facebook y recopilar los datos compartidos por el usuario a través de la aplicación.

   >[!NOTE]
   >
   >Los parámetros del servicio Web se detallan en el archivo WSDL disponible aquí: **`https://<Instance name>/nl/jsp/schemawsdl.jsp?schema=nms:visitor`**

   Para integrar la aplicación de terceros en Adobe Campaign, debe copiar el contenido de los campos **[!UICONTROL App ID]** y **[!UICONTROL App Secret]** Facebook y pegarlo en los **[!UICONTROL Application ID]** campos y **[!UICONTROL Application secret]** campos de la consola.

   ![](assets/social_facebook_external_account_013.png)

   **Aplicación alojada en esta instancia**

   Si desea alojar la aplicación en esta instancia (si no tiene una aplicación de terceros), debe utilizar las aplicaciones web de Adobe Campaign para adquirir perfiles de Facebook. Para obtener más información sobre esto, consulte [Ejemplos de aplicaciones](../../social/using/examples-of-facebook-apps.md)de Facebook.

   En la consola de Adobe Campaign, copie la dirección contenida en el **[!UICONTROL Secure Canvas URL]** campo y péguela en el **[!UICONTROL Facebook Web games (https)]** campo de Facebook (en la **[!UICONTROL Facebook Web Games]** sección).

   ![](assets/social_facebook_external_account_009.png)

   >[!IMPORTANT]
   >
   >No debe utilizar la dirección URL no segura bajo ninguna circunstancia.

   En Facebook, copie el contenido de los campos **[!UICONTROL App ID]** y **[!UICONTROL App Secret]** y péguelo en los campos **[!UICONTROL Application ID]** y **[!UICONTROL Application secret]** de la consola.

   ![](assets/social_facebook_external_account_008.png)

1. En Facebook, haga clic en el **[!UICONTROL Save Changes]** botón en la parte inferior de la página.
1. En la consola de Adobe Campaign, haga clic en el **[!UICONTROL Subscribe]** botón para permitir que Adobe Campaign recupere los datos en tiempo real cada vez que un seguidor realice una comprobación mediante esta aplicación. Para obtener más información sobre esto, consulte: [Ejemplos de aplicaciones](../../social/using/examples-of-facebook-apps.md)de Facebook.

   ![](assets/social_webapp_fb_013.png)

## Introducción de los vínculos Condiciones de servicio y Política de privacidad {#entering-the-terms-of-service-and-privacy-policy-links}

Se recomienda enfáticamente agregar los vínculos **[!UICONTROL Terms of service]** y **[!UICONTROL Privacy policy]** , que se mostrarán en la pantalla de solicitud de permisos de Facebook.

![](assets/social_fb_terms_of_services_001.png)

Las etapas de configuración son las siguientes:

1. Introduzca la siguiente dirección: [https://developers.facebook.com/apps](https://developers.facebook.com/apps)y, a continuación, seleccione la aplicación de Facebook.
1. Seleccione la **[!UICONTROL Settings > Basic]** ficha e introduzca los campos **[!UICONTROL Privacy Policy URL]** y **[!UICONTROL Terms of Service URL]** .

   ![](assets/social_fb_terms_of_services.png)

## Creación de una aplicación web de tipo Facebook {#creating-a-facebook-type-web-application}

La aplicación de Facebook de Adobe Campaign permite mostrar contenido personalizado en la aplicación de Facebook. Para cada aplicación de Facebook, debe crear una aplicación web en Adobe Campaign. Para crear una aplicación web de Facebook, siga estos pasos:

1. Vaya al **[!UICONTROL Social networks]** universo, haga clic en el **[!UICONTROL Applications]** vínculo y luego en el **[!UICONTROL Create]** botón.

   ![](assets/social_webapp_001.png)

1. Seleccione una plantilla de aplicación web de Facebook en la lista e introduzca la etiqueta.

   ![](assets/social_webapp_002.png)

   >[!NOTE]
   >
   >Hay cuatro plantillas de aplicación web de Facebook disponibles de forma predeterminada:
   >
   >* **[!UICONTROL New Facebook application]**:: seleccione esta plantilla si desea comenzar desde una aplicación en blanco.
   >* **[!UICONTROL Pre-entered form]**:: Aplicación de Facebook con un formulario y un botón de inicio de sesión de Facebook que permite a los usuarios rellenar automáticamente los campos del formulario utilizando los datos de su perfil. Esto permite que los usuarios completen el formulario más rápidamente y que las marcas obtengan información de mejor calidad.
   >* **[!UICONTROL "Canvas page" competition]**:: Aplicación de Facebook que se muestra en la pantalla para una mejor experiencia visual para los usuarios.
   >* **[!UICONTROL "Page Tab" competition]**:: Aplicación de Facebook totalmente integrada en las fichas de la página de marca.


1. En el **[!UICONTROL Application]** campo, introduzca la cuenta externa vinculada a la aplicación Facebook. For more on this, refer to: [Configuring external accounts](#configuring-external-accounts).

   ![](assets/social_webapp_005.png)

1. Seleccione la **[!UICONTROL Edit]** ficha y, a continuación, edite la aplicación web. Para obtener más información sobre esto, consulte: [Ejemplos de aplicaciones](../../social/using/examples-of-facebook-apps.md)de Facebook.

   ![](assets/social_webapp_003.png)

1. Una vez finalizada la aplicación web, seleccione la **[!UICONTROL Dashboard]** ficha y haga clic en **[!UICONTROL Publish]** para publicarla en línea.

   ![](assets/social_webapp_004.png)

## Configuración de fichas de Facebook {#configuring-facebook-tabs}

Puede configurar las aplicaciones de Facebook para que se muestren como fichas en la página de Facebook. Para ello, siga los siguientes pasos:

1. Seleccione la aplicación de Facebook ([https://developers.facebook.com/apps](https://developers.facebook.com/apps)) y seleccione la **[!UICONTROL Settings > Basic]** ficha.

   ![](assets/social_webapp_fb_008.png)

1. En la parte inferior de la página, haga clic en el **[!UICONTROL Add Platform]** botón y seleccione **[!UICONTROL Page Tab]**.

   ![](assets/social_webapp_fb_008bis.png)

1. En el **[!UICONTROL Page Tab Name]** campo de la **[!UICONTROL Page Tab]** sección, escriba la etiqueta como desee que aparezca en la página de Facebook.

   ![](assets/social_webapp_fb_001.png)

1. En el **[!UICONTROL Secure Page Tab URL]** campo, introduzca la URL pública de la aplicación web, a la que se puede acceder desde la **[!UICONTROL Dashboard]** ficha de la aplicación web. Para obtener más información sobre la creación de aplicaciones web de tipo Facebook, consulte [Creación de una aplicación](#creating-a-facebook-type-web-application)web de tipo Facebook.

   ![](assets/social_webapp_fb_002.png)

1. En la parte superior **[!UICONTROL Dashboard]** de la aplicación web, haga clic en el **[!UICONTROL Add a page tab]** vínculo.

   ![](assets/social_webapp_fb_0010.png)

1. Seleccione la página de Facebook a la que desee agregar la ficha y haga clic en **[!UICONTROL Add Page Tab]**.

   ![](assets/social_webapp_fb_0011.png)

