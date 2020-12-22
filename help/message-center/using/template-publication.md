---
solution: Campaign Classic
product: campaign
title: Publicación de plantilla
description: Publicación de plantilla de mensaje transaccional
audience: message-center
content-type: reference
topic-tags: message-templates
translation-type: tm+mt
source-git-commit: 02dee9c4cc03784ccc20f147f816798248bd10f2
workflow-type: tm+mt
source-wordcount: '246'
ht-degree: 45%

---


# Publicación de plantilla{#template-publication}

When the message template created on the control instance is complete, you can publish it. Este proceso también lo publicará en todas las instancias de ejecución.

Publication lets you automatically create two message templates on the execution instances, which will allow you to send messages linked to real-time and batch events.

>[!NOTE]
>
>Al publicar Plantillas de mensaje transaccional, las reglas de tipología también se publican automáticamente en las instancias de ejecución.

>[!IMPORTANT]
>
>Siempre que realice cambios en una plantilla, asegúrese de publicarla de nuevo para que estos cambios sean efectivos durante el envío de mensaje transaccional.

1. En la instancia de control, vaya a la carpeta **[!UICONTROL Message Center > Transactional message templates]** del árbol.
1. Seleccione la plantilla que desee publicar en las instancias de ejecución.
1. Haga clic **[!UICONTROL Publish]**.

   ![](assets/messagecenter_publish_model_008.png)

Una vez terminada la publicación, las dos plantillas de mensaje que se aplican a los eventos de tipo por lote y en tiempo real se crean en el árbol de la instancia de producción de la carpeta **[!UICONTROL Administration > Production > Message Center Execution> Default > Transactional message templates]**.

![](assets/messagecenter_deployed_model_001.png)

Una vez publicada una plantilla, si se activa el evento correspondiente, la instancia de ejecución recibirá el evento, lo vinculará a la plantilla transaccional y enviará el mensaje transaccional correspondiente a cada destinatario.

>[!NOTE]
>
>Si se sustituye un campo existente de la plantilla de mensaje transaccional, como la dirección del remitente, con un valor vacío, el campo correspondiente de las instancias de ejecución no se actualizará una vez que se vuelva a publicar el mensaje transaccional. Aún contiene el valor anterior.
>
>Sin embargo, si se agrega un valor no vacío, el campo correspondiente se actualiza de la forma habitual después de la siguiente publicación.
