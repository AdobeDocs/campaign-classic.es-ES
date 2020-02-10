---
title: Foros de debate
seo-title: Foros de debate
description: Foros de debate
seo-description: null
page-status-flag: never-activated
uuid: 6253bb32-c71d-45ac-bc03-027131ae95a5
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: campaign
content-type: reference
topic-tags: tasks--resources-and-budgets
discoiquuid: 88eb17b6-5206-4064-9cd9-b4645a85c609
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: d30de91002862b664249c5a704b7c0f521dd30f2

---


# Foros de debate{#discussion-forums}

Los operadores de Adobe Campaign pueden utilizar foros de debate para compartir información. Cada uno de los elementos siguientes tiene su propio foro: planes, programas, campañas, recursos, simulaciones y existencias. Cada operador también tiene un foro personal. Todos los debates son públicos, incluso en foros personales.

Los operadores pueden suscribirse a un foro para recibir un correo electrónico de notificación cada vez que se publica un mensaje.

## Acceso a un foro {#accessing-a-forum}

To visit the forum of a campaign, an operator, etc., go to its dashboard and click the **[!UICONTROL Forum]** link in the top right-hand corner. Este enlace también informa sobre la cantidad total de mensajes en el foro.

![](assets/mrm_forum_access_link.png)

## Uso de un foro {#using-a-forum}

Los mensajes y sus respuestas se muestran en orden cronológico (de más reciente a más antiguo).

Para mostrar el contenido de un mensaje, haga clic en su encabezado.

![](assets/mrm_forum_expand_msg.png)

**Iniciar una nueva conversación**

To start a new discussion, click the **[!UICONTROL Add a discussion]** button in the top right-hand corner. Se abre la **[!UICONTROL Discussion forum]** casilla (ver abajo).

![](assets/mrm_forum_new_thread.png)

**Publicar un mensaje en una conversación existente**

To post a message to an existing discussion, open the message that you want to answer, then click the **[!UICONTROL Reply]** link in the top left-hand corner. Se abre la **[!UICONTROL Discussion forum]** casilla (ver abajo).

![](assets/mrm_forum_answer_msg.png)

Al responder a un mensaje, la persona que publicó el mensaje original recibe una notificación.

**Escribir un mensaje**

En el **[!UICONTROL Discussion forum]** cuadro:

1. Enter your text in the **[!UICONTROL Message]** field and a discussion title in the **[!UICONTROL Subject]** field.

   ![](assets/mrm_forum_edit_msg.png)

1. Si es necesario:

   * If you want someone to take part in the discussion who isn&#39;t subscribed to the forum, use the **[!UICONTROL Operator to notify]** field. El operador en cuestión recibe un mensaje de correo electrónico que le notifica la publicación de ese mensaje específico (no se suscribe al foro). Para notificar a varios operadores, seleccione un grupo de operadores.
   * To add an attachment to the message, click **[!UICONTROL Browse]**. El archivo adjunto también se incluye en el mensaje de correo electrónico de notificación. Los archivos adjuntos solo se pueden enviar individualmente: para enviar varios archivos, debe comprimirlos.

1. Haga clic **[!UICONTROL Create the message]** para publicarlo en el foro.

>[!NOTE]
>
>Una vez que se ha publicado un mensaje en el foro, ya no se puede cambiar ni eliminar.

## Publicación en el foro personal de un operador {#posting-to-the-personal-forum-of-an-operator}

Puede enviar un mensaje al foro de un operador si, por ejemplo, el mensaje no está relacionado con una campaña específica, pero aun así desea realizar un seguimiento de la conversación en Adobe Campaign. Los foros personales son públicos y todos los operadores pueden ver el mensaje. El operador recibe un mensaje cada vez que alguien publica en su foro personal.

Para acceder al foro de un operador:

* If you have the necessary rights to access the **[!UICONTROL Administration > Access management > Operators]** node of the explorer, open the dashboard of the desired operator and click the **[!UICONTROL Forum]** link in the top right-hand corner.
* Si no es así, busque el nombre del operador en Adobe Campaign (en un mensaje publicado en el foro por este operador, correspondiente a una tarea asignada a él) y haga clic en él para acceder a su panel. También puede pedir al administrador que cree una vista de la carpeta del operador.

## Suscripción a un foro {#subscribing-to-a-forum}

La suscripción a un foro le permite seguir las conversaciones. Recibe una notificación por correo electrónico cada vez que se publique un mensaje en el foro. Este mensaje de correo electrónico contiene el cuerpo del mensaje y los archivos adjuntos. Para responder a un mensaje, haga clic en el cuerpo del correo electrónico y luego inicie sesión en la interfaz web de Adobe Campaign. Al suscribirse a un foro, todos los operadores pueden ver esta información.

* To subscribe to a forum, click the **[!UICONTROL Follow discussions]** button in the top right hand section above the list of messages.

   ![](assets/mrm_forum_subscribe.png)

   La sección se vuelve azul y muestra que está suscrito al foro.

* To unsubscribe from a forum, click the **[!UICONTROL Unsubscribe]** button.

   ![](assets/mrm_forum_unsubscribe.png)

* Su panel personal enumera los foros a los que está suscrito. Click the **[!UICONTROL Subscription to discussion forums]** link to display the list, then click the item that interests you to access its forum.

   ![](assets/platform_dashboard_operator_subscr_forums.png)

   Para obtener más información acerca de los paneles personales, consulte [esta sección](../../platform/using/access-management.md#operators).

* To see who is subscribed to a forum, click the **[!UICONTROL List of subscribers to this discussion forum]** link above the list of messages.

   ![](assets/mrm_forum_subscribers.png)

## Comprobación del envío de notificaciones {#checking-notification-delivery}

Si los operadores suscritos a un foro no reciben notificaciones como se espera:

* Compruebe que las direcciones de correo electrónico se han introducido correctamente en los perfiles del operador.
* Vaya al **[!UICONTROL Administration > Production > Technical workflows > Campaign processes]** nodo y compruebe que el **[!UICONTROL Jobs in discussion forums]** flujo de trabajo se ha iniciado y está libre de errores.
* Ver los registros de envío:

   * En la página de inicio de Adobe Campaign, vaya a **[!UICONTROL Campaigns > Navigation > Deliveries]** y, a continuación, abra el **[!UICONTROL Discussion forum notification]** envío.
   * En el explorador, vaya a **[!UICONTROL Administration > Production > Objects created automatically > Technical deliveries > Workflow notifications]**, luego haga clic en **[!UICONTROL Discussion forum notifications]**.
   En el **[!UICONTROL Discussion forum notifications]** cuadro, los registros de entrega se encuentran en la **[!UICONTROL Edit > Delivery]** ficha. También puede ver las fichas **[!UICONTROL Tracking > Log]** y **[!UICONTROL Exclusion causes]** .

