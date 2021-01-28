---
solution: Campaign Classic
product: campaign
title: Publicación de plantilla
description: Publicación de plantilla de mensaje transaccional
audience: message-center
content-type: reference
topic-tags: message-templates
translation-type: ht
source-git-commit: 02dee9c4cc03784ccc20f147f816798248bd10f2
workflow-type: ht
source-wordcount: '246'
ht-degree: 100%

---


# Publicación de plantilla{#template-publication}

Cuando la plantilla de mensaje creada en la instancia de control esté completa, puede publicarla. Este proceso también lo publicará en todas las instancias de ejecución.

La publicación permite crear automáticamente dos plantillas de mensajes en la instancia de ejecución, lo que permite enviar mensajes relacionados con los eventos en tiempo real y por lotes.

>[!NOTE]
>
>Al publicar plantillas de mensaje transaccional, las reglas de tipología se publican automáticamente en las instancias de ejecución.

>[!IMPORTANT]
>
>Siempre que realice cambios en una plantilla, asegúrese de publicarla de nuevo para que estos cambios sean efectivos durante el envío del mensaje transaccional.

1. En la instancia de control, vaya a la carpeta **[!UICONTROL Message Center > Transactional message templates]** del árbol.
1. Seleccione la plantilla que desee publicar en las instancias de ejecución.
1. Haga clic **[!UICONTROL Publish]**.

   ![](assets/messagecenter_publish_model_008.png)

Una vez terminada la publicación, las dos plantillas de mensaje que se aplican a los eventos de tipo por lote y en tiempo real se crean en el árbol de la instancia de producción de la carpeta **[!UICONTROL Administration > Production > Message Center Execution> Default > Transactional message templates]**.

![](assets/messagecenter_deployed_model_001.png)

Una vez publicada una plantilla, si se activa el evento correspondiente, la instancia de ejecución recibirá el evento, lo vinculará a la plantilla transaccional y enviará el mensaje transaccional correspondiente a cada destinatario.

>[!NOTE]
>
>Si se sustituye un campo existente de la plantilla de mensaje transaccional, como la dirección del remitente, con un valor vacío, el campo correspondiente de la(s) instancia(s) de ejecución no se actualizará una vez que se vuelva a publicar el mensaje transaccional. Aún contendrá el valor anterior.
>
>Sin embargo, si se agrega un valor no vacío, el campo correspondiente se actualiza de la forma habitual después de la siguiente publicación.
