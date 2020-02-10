---
title: Publicación de plantilla
seo-title: Publicación de plantilla
description: Publicación de plantilla
seo-description: null
page-status-flag: never-activated
uuid: f83dbe5f-762c-4c58-aeed-6ec289eb522f
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: message-center
content-type: reference
topic-tags: message-templates
discoiquuid: 43908738-a71a-49be-ac00-175f57a0555c
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 579329d9194115065dff2c192deb0376c75e67bd

---


# Publicación de plantilla{#template-publication}

Una vez completada la plantilla de mensaje creada en la instancia de control, se puede publicarla en todas las instancias de ejecución. La publicación permite crear automáticamente dos plantillas de mensajes en la instancia de ejecución, lo que permite enviar mensajes vinculados a los eventos en tiempo real y por lotes.

>[!CAUTION]
>
>Recuerde publicar la plantilla cuando realice cambios en ella para que estos cambios puedan ser efectivos durante el envío del mensaje transaccional.

>[!NOTE]
>
>Al publicar plantillas de mensaje transaccional, las reglas de tipología se publican automáticamente en las instancias de ejecución.

1. In the control instance, go to the **[!UICONTROL Message Center > Transactional message templates]** folder of the tree.
1. Seleccione la plantilla que desee publicar en las instancias de ejecución.
1. Haga clic **[!UICONTROL Publication]** .

   ![](assets/messagecenter_publish_model_008.png)

Once publication is complete, both message templates to be applied to batch and real time type events are created in the tree of the production instance in the **[!UICONTROL Administration > Production > Message Center > Default > Transactional message templates]** folder.

![](assets/messagecenter_deployed_model_001.png)

>[!NOTE]
>
>Si se sustituye un campo existente de la plantilla de mensaje transaccional,
      como la dirección del remitente, con un valor vacío, el campo correspondiente
        de las instancias de ejecución no se actualizará una vez que se vuelva a publicar el mensaje transaccional. Aún contiene el valor anterior. Sin embargo, si se agrega un valor no vacío,                                                                                 
        el campo correspondiente se actualiza de la forma habitual después de la siguiente publicación.

