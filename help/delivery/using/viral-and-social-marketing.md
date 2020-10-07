---
title: Marketing viral y social
seo-title: Marketing viral y social
description: Marketing viral y social
seo-description: null
page-status-flag: never-activated
uuid: dca3db7e-cc8d-42ca-b1b8-45e9fb739c97
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: delivery
content-type: reference
topic-tags: subscriptions-and-referrals
discoiquuid: 66f2b229-92d9-4db1-97a4-2d9eb2270446
translation-type: tm+mt
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: tm+mt
source-wordcount: '568'
ht-degree: 85%

---


# Marketing viral y social{#viral-and-social-marketing}

## Acerca del marketing viral {#about-viral-marketing}

Adobe Campaign le permite configurar herramientas para potenciar el marketing viral.

Esto permite que los destinatarios o los visitantes del sitio web puedan compartir información con su red, desde añadir un vínculo a su perfil de Facebook o Twitter a enviar un mensaje a un amigo.

![](assets/s_ncs_user_viral_icons.png)

>[!CAUTION]
>
>Para que los vínculos añadidos funcionen correctamente, la página espejo correspondiente debe estar disponible. Para ello, incluya el vínculo a la página espejo en la entrega.

## Redes sociales: compartir un vínculo {#social-networks--sharing-a-link}

Para permitir que los destinatarios de una entrega compartan el contenido de los mensajes con los miembros de su red, debe incluir el bloque personalizado correspondiente.

![](assets/s_ncs_user_viral_add_link.png)

>[!NOTE]
>
>De forma predeterminada, este vínculo no está disponible en la lista de bloques. You can access it by clicking **[!UICONTROL Other...]**, and selecting the **[!UICONTROL Social network sharing links]** block.

![](assets/s_ncs_user_viral_add_link_via_others.png)

La renderización se realiza de la forma siguiente:

![](assets/s_ncs_user_viral_add_link_rendering.png)

Cuando el destinatario hace clic en el icono de una de las redes sociales mostradas, se redirige automáticamente a su cuenta y puede compartir el contenido del mensaje mediante un vínculo. Esto permite a los miembros de su red acceder a la comunicación.

>[!NOTE]
>
>Este bloque personalizado contiene todos los vínculos (para la entrega de mensajes y poder compartir con todas las redes sociales). Puede modificarse para adecuarse a sus necesidades. Sin embargo, la configuración está reservada para usuarios avanzados. To edit the matching personalization block, go to the **[!UICONTROL Resources > Campaign management > Personalization blocks]** node of the Adobe Campaign tree.

## Marketing viral: enviar a un amigo {#viral-marketing--forward-to-a-friend}

Un servicio viral permite llevar a cabo acciones de recomendación, y estas acciones permiten reenviar un mensaje a un amigo. El perfil del o los destinatarios secundarios se almacena temporalmente en la base de datos (en una tabla específica). Los mensajes reenviados incluyen un vínculo para que el destinatario secundario se suscriba: si lo hace, se añade a la base de datos de Adobe Campaign.

El reenvío de mensajes se basa en los mismos principios que los vínculos de la red social.

Siga estos pasos:

1. Add the **[!UICONTROL Social network sharing links]** personalization block into the body of the original message.
1. El destinatario del mensaje puede hacer clic en el icono **[!UICONTROL Email]** para enviar este mensaje a uno o varios amigos.

   ![](assets/s_ncs_user_viral_email_link.png)

   Un formulario de recomendación permite introducir las direcciones de correo electrónico de los destinatarios secundarios.

   ![](assets/s_ncs_user_viral_email_msg.png)

   El mensaje se envía cuando el destinatario principal hace clic en el botón **[!UICONTROL Next]**.

   >[!NOTE]
   >
   >El contenido de este mensaje se puede personalizar para adecuarse a sus necesidades. It is created based on the **[!UICONTROL Transfer of original message]** template, which is stored in the **[!UICONTROL Administration > Campaign management > Technical delivery templates]** node.
   >
   >También se puede cambiar el formulario de reenvío de mensajes que se pone a disposición del destinatario que realiza el reenvío. Para ello, es necesario cambiar la aplicación web **Viral form** almacenada en el nodo **[!UICONTROL Resources > Online > Web applications]**.

1. En el mensaje reenviado, un vínculo permite al destinatario secundario guardar su perfil en la base de datos. Se proporciona un formulario de entrada para este fin.

   ![](assets/s_ncs_user_viral_create_account_form.png)

   >[!NOTE]
   >
   >Esta configuración se puede adaptar. To do this, you need to modify the **Recipient subscription** Web application stored in the **[!UICONTROL Resources > Online > Web applications]** node.
   >
   >Para obtener más información sobre las aplicaciones web, consulte [esta sección](../../web/using/about-web-applications.md).

   Una vez validados, se les envía un mensaje de confirmación: el registro solo es definitivo cuando activen el vínculo en el mensaje de confirmación. This message is created based on the **[!UICONTROL Registration confirmation]** template, which is stored in the **[!UICONTROL Administration > Campaign management > Technical delivery templates]** node.

   El destinatario secundario se añade a la carpeta **Recipients** de la base de datos y se suscribe (de forma predeterminada) al servicio informativo **Newsletter**.

## Seguimiento del uso compartido en redes sociales {#tracking-social-network-sharing}

Se hace un seguimiento del uso compartido y acceso a la información compartida. A esta información, recopilada por Adobe Campaign, se puede acceder por dos vías:

* en la pestaña de la entrega **[!UICONTROL Tracking]** (o individualmente para cada destinatario):

   ![](assets/s_ncs_user_network_del_tracking_tab.png)

* in a dedicated **[!UICONTROL Sharing to social networks]** report:

   ![](assets/s_ncs_user_viral_report.png)

