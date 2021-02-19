---
solution: Campaign Classic
product: campaign
title: Marketing viral y social
description: Marketing viral y social
audience: delivery
content-type: reference
topic-tags: subscriptions-and-referrals
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '564'
ht-degree: 100%

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
>De forma predeterminada, este vínculo no está disponible en la lista de bloques. Puede acceder a él haciendo clic en **[!UICONTROL Other...]** y seleccionando el bloque **[!UICONTROL Social network sharing links]**.

![](assets/s_ncs_user_viral_add_link_via_others.png)

La renderización se realiza de la forma siguiente:

![](assets/s_ncs_user_viral_add_link_rendering.png)

Cuando el destinatario hace clic en el icono de una de las redes sociales mostradas, se redirige automáticamente a su cuenta y puede compartir el contenido del mensaje mediante un vínculo. Esto permite a los miembros de su red acceder a la comunicación.

>[!NOTE]
>
>Este bloque personalizado contiene todos los vínculos (para la entrega de mensajes y poder compartir con todas las redes sociales). Puede modificarse para adecuarse a sus necesidades. Sin embargo, la configuración está reservada para usuarios avanzados. Para editar el bloque personalizado correspondiente, vaya al nodo **[!UICONTROL Resources > Campaign management > Personalization blocks]** en el árbol de Adobe Campaign.

## Marketing viral: enviar a un amigo {#viral-marketing--forward-to-a-friend}

Un servicio viral permite llevar a cabo acciones de recomendación, y estas acciones permiten reenviar un mensaje a un amigo. El perfil del o los destinatarios secundarios se almacena temporalmente en la base de datos (en una tabla específica). Los mensajes reenviados incluyen un vínculo para que el destinatario secundario se suscriba: si lo hace, se añade a la base de datos de Adobe Campaign.

El reenvío de mensajes se basa en los mismos principios que los vínculos de la red social.

Siga estos pasos:

1. Añada el bloque personalizado **[!UICONTROL Social network sharing links]** al cuerpo del mensaje original.
1. El destinatario del mensaje puede hacer clic en el icono **[!UICONTROL Email]** para enviar este mensaje a uno o varios amigos.

   ![](assets/s_ncs_user_viral_email_link.png)

   Un formulario de recomendación permite introducir las direcciones de correo electrónico de los destinatarios secundarios.

   ![](assets/s_ncs_user_viral_email_msg.png)

   El mensaje se envía cuando el destinatario principal hace clic en el botón **[!UICONTROL Next]**.

   >[!NOTE]
   >
   >El contenido de este mensaje se puede personalizar para adecuarse a sus necesidades. Se crea a partir de la plantilla **[!UICONTROL Transfer of original message]**, que se almacena en el nodo **[!UICONTROL Administration > Campaign management > Technical delivery templates]**.
   >
   >También se puede cambiar el formulario de reenvío de mensajes que se pone a disposición del destinatario que realiza el reenvío. Para ello, es necesario cambiar la aplicación web **Viral form** almacenada en el nodo **[!UICONTROL Resources > Online > Web applications]**.

1. En el mensaje reenviado, un vínculo permite al destinatario secundario guardar su perfil en la base de datos. Se proporciona un formulario de entrada para este fin.

   ![](assets/s_ncs_user_viral_create_account_form.png)

   >[!NOTE]
   >
   >Esta configuración se puede adaptar. Para ello, debe modificar la aplicación web **Recipient subscription** almacenada en el nodo **[!UICONTROL Resources > Online > Web applications]**.
   >
   >Para obtener más información sobre las aplicaciones web, consulte [esta sección](../../web/using/about-web-applications.md).

   Una vez validados, se les envía un mensaje de confirmación: el registro solo es definitivo cuando activen el vínculo en el mensaje de confirmación. Este mensaje se crea en función de la plantilla **[!UICONTROL Registration confirmation]**, que se almacena en el nodo **[!UICONTROL Administration > Campaign management > Technical delivery templates]**.

   El destinatario secundario se añade a la carpeta **Recipients** de la base de datos y se suscribe (de forma predeterminada) al servicio informativo **Newsletter**.

## Seguimiento del uso compartido en redes sociales {#tracking-social-network-sharing}

Se hace un seguimiento del uso compartido y acceso a la información compartida. A esta información, recopilada por Adobe Campaign, se puede acceder por dos vías:

* en la pestaña de la entrega **[!UICONTROL Tracking]** (o individualmente para cada destinatario):

   ![](assets/s_ncs_user_network_del_tracking_tab.png)

* en un informe específico **[!UICONTROL Sharing to social networks]**:

   ![](assets/s_ncs_user_viral_report.png)

