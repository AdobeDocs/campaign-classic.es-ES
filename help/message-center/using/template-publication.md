---
solution: Campaign Classic
product: campaign
title: Publicación de plantilla
description: Publicación de plantilla de mensaje transaccional
audience: message-center
content-type: reference
topic-tags: message-templates
translation-type: ht
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: ht
source-wordcount: '206'
ht-degree: 100%

---


# Publicación de plantilla{#template-publication}

Una vez completada la plantilla de mensaje creada en la instancia de control, se puede publicarla en todas las instancias de ejecución. La publicación permite crear automáticamente dos plantillas de mensajes en la instancia de ejecución, lo que permite enviar mensajes relacionados con los eventos en tiempo real y por lotes.

>[!IMPORTANT]
>
>Recuerde publicar la plantilla cuando realice cambios en ella para que estos cambios puedan ser efectivos durante la entrega del mensaje transaccional.

>[!NOTE]
>
>Al publicar plantillas de mensaje transaccional, las reglas de tipología se publican automáticamente en las instancias de ejecución.

1. En la instancia de control, vaya a la carpeta **[!UICONTROL Message Center > Transactional message templates]** del árbol.
1. Seleccione la plantilla que desee publicar en las instancias de ejecución.
1. Haga clic **[!UICONTROL Publish]**.

   ![](assets/messagecenter_publish_model_008.png)

Una vez terminada la publicación, las dos plantillas de mensaje que se aplican a los eventos de tipo por lote y en tiempo real se crean en el árbol de la instancia de producción de la carpeta **[!UICONTROL Administration > Production > Message Center Execution> Default > Transactional message templates]**.

![](assets/messagecenter_deployed_model_001.png)

>[!NOTE]
>
>Si se sustituye un campo existente de la plantilla de mensaje transaccional, como la dirección del remitente, con un valor vacío, el campo correspondiente de las instancias de ejecución no se actualizará una vez que se vuelva a publicar el mensaje transaccional. Aún contiene el valor anterior. Sin embargo, si se agrega un valor no vacío, el campo correspondiente se actualiza de la forma habitual después de la siguiente publicación.
