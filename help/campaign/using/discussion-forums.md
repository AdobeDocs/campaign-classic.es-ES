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
translation-type: tm+mt
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: tm+mt
source-wordcount: '725'
ht-degree: 87%

---


# Foros de debate{#discussion-forums}

Los operadores de Adobe Campaign pueden utilizar foros de debate para compartir información. Cada uno de los elementos siguientes tiene su propio foro: planes, programas, campañas, recursos, simulaciones y existencias. Cada operador también tiene un foro personal. Todos los debates son públicos, incluso en foros personales.

Los operadores pueden suscribirse a un foro para recibir un correo electrónico de notificación cada vez que se publica un mensaje.

## Acceso a un foro {#accessing-a-forum}

Para visitar el foro de una campaña, un operador, etc., vaya a su panel y haga clic en el vínculo **[!UICONTROL Forum]** en la esquina superior derecha. Este vínculo también informa sobre la cantidad total de mensajes en el foro.

![](assets/mrm_forum_access_link.png)

## Uso de un foro {#using-a-forum}

Los mensajes y sus respuestas se muestran en orden cronológico (de más reciente a más antiguo).

Para mostrar el contenido de un mensaje, haga clic en su encabezado.

![](assets/mrm_forum_expand_msg.png)

**Iniciar una nueva conversación**

Para comenzar una nueva conversación, haga clic en el botón **[!UICONTROL Add a discussion]** en la esquina superior derecha. The **[!UICONTROL Discussion forum]** box comes up (see below).

![](assets/mrm_forum_new_thread.png)

**Publicar un mensaje en una conversación existente**

Para publicar un mensaje en una conversación existente, abra el mensaje al que desee responder y, a continuación, haga clic en el vínculo **[!UICONTROL Reply]** situado en la esquina superior izquierda. The **[!UICONTROL Discussion forum]** box comes up (see below).

![](assets/mrm_forum_answer_msg.png)

Al responder a un mensaje, la persona que publicó el mensaje original recibe una notificación.

**Escribir un mensaje**

En el **[!UICONTROL Discussion forum]** cuadro:

1. Introduzca el texto en el campo **[!UICONTROL Message]** y un título de conversación en el campo **[!UICONTROL Subject]**.

   ![](assets/mrm_forum_edit_msg.png)

1. Si es necesario:

   * Si desea que otra persona que no está suscrita al foro participe en la conversación, utilice el campo **[!UICONTROL Operator to notify]**. El operador en cuestión recibe un mensaje de correo electrónico que le notifica la publicación de ese mensaje específico (no se suscribe al foro). Para notificar a varios operadores, seleccione un grupo de operadores.
   * Para añadir un archivo adjunto al mensaje, haga clic en **[!UICONTROL Browse]**. El archivo adjunto también se incluye en el mensaje de correo electrónico de notificación. Los archivos adjuntos solo se pueden enviar individualmente: para enviar varios archivos, debe comprimirlos.

1. Click **[!UICONTROL Create the message]** to post it to the forum.

>[!NOTE]
>
>Una vez que se ha publicado un mensaje en el foro, ya no se puede cambiar ni eliminar.

## Publicación en el foro personal de un operador {#posting-to-the-personal-forum-of-an-operator}

Puede enviar un mensaje al foro de un operador si, por ejemplo, el mensaje no está relacionado con una campaña específica, pero aun así desea realizar un seguimiento de la conversación en Adobe Campaign. Los foros personales son públicos y todos los operadores pueden ver el mensaje. El operador recibe un mensaje cada vez que alguien publica en su foro personal.

Para acceder al foro de un operador:

* Si tiene los derechos necesarios para acceder al nodo del explorador **[!UICONTROL Administration > Access management > Operators]**, abra el panel del operador deseado y haga clic en el vínculo **[!UICONTROL Forum]** situado en la esquina superior derecha.
* Si no es así, busque el nombre del operador en Adobe Campaign (en un mensaje publicado en el foro por este operador, correspondiente a una tarea asignada a él) y haga clic en él para acceder a su panel. También puede pedir al administrador que cree una vista de la carpeta del operador.

## Suscripción a un foro {#subscribing-to-a-forum}

La suscripción a un foro le permite seguir las conversaciones. Recibe una notificación por correo electrónico cada vez que se publique un mensaje en el foro. Este mensaje de correo electrónico contiene el cuerpo del mensaje y los archivos adjuntos. Para responder a un mensaje, haga clic en el cuerpo del correo electrónico y luego inicie sesión en la interfaz web de Adobe Campaign. Al suscribirse a un foro, todos los operadores pueden ver esta información.

* Para suscribirse a un foro, haga clic en el botón **[!UICONTROL Follow discussions]** situado en la sección superior derecha de la lista de mensajes.

   ![](assets/mrm_forum_subscribe.png)

   La sección se vuelve azul y muestra que está suscrito al foro.

* Para cancelar la suscripción a un foro, haga clic en el botón **[!UICONTROL Unsubscribe]**.

   ![](assets/mrm_forum_unsubscribe.png)

* Su panel personal enumera los foros a los que está suscrito. Haga clic en el vínculo **[!UICONTROL Subscription to discussion forums]** para mostrar la lista y luego haga clic en el elemento que le interese para acceder al foro correspondiente.

   ![](assets/platform_dashboard_operator_subscr_forums.png)

   Para obtener más información acerca de los paneles personales, consulte [esta sección](../../platform/using/access-management.md#operators).

* To see who is subscribed to a forum, click the **[!UICONTROL List of subscribers to this discussion forum]** link above the list of messages.

   ![](assets/mrm_forum_subscribers.png)

## Comprobación de la entrega de notificaciones {#checking-notification-delivery}

Si los operadores suscritos a un foro no reciben notificaciones como se espera:

* Compruebe que las direcciones de correo electrónico se han introducido correctamente en los perfiles del operador.
* Go to the **[!UICONTROL Administration > Production > Technical workflows > Campaign processes]** node and check that the **[!UICONTROL Jobs in discussion forums]** workflow is started and free of errors.
* Ver los registros de envío:

   * On the Adobe Campaign home page, go to **[!UICONTROL Campaigns > Navigation > Deliveries]**, then open the **[!UICONTROL Discussion forum notification]** delivery.
   * En el explorador, vaya a **[!UICONTROL Administration > Production > Objects created automatically > Technical deliveries > Workflow notifications]**, luego haga clic en **[!UICONTROL Discussion forum notifications]**.

   In the **[!UICONTROL Discussion forum notifications]** box, the delivery logs are found in the **[!UICONTROL Edit > Delivery]** tab. You can also view the **[!UICONTROL Tracking > Log]** and the **[!UICONTROL Exclusion causes]** tabs.

