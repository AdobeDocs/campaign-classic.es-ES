---
solution: Campaign Classic
product: campaign
title: 'Publicación de plantillas de mensaje '
description: Obtenga información sobre la publicación y cancelación de publicación de plantillas de mensaje transaccional en Adobe Campaign Classic.
audience: message-center
content-type: reference
topic-tags: message-templates
exl-id: 1d55f42b-64bf-4b1f-a317-c1f7456aa5b3
source-git-commit: d39b15b0efc6cbd6ab24e074713be6f8fc90e5fc
workflow-type: tm+mt
source-wordcount: '494'
ht-degree: 85%

---

# Publicar plantillas de mensaje {#publishing-template-messages}

## Publicación de plantilla {#template-publication}

Cuando la [plantilla de mensaje](../../message-center/using/creating-the-message-template.md) creada en la instancia de control esté completa y una vez que la haya [probado](../../message-center/using/testing-message-templates.md), puede publicarla. Este proceso también lo publicará en todas las instancias de ejecución.

La publicación permite crear automáticamente **dos plantillas de mensaje** en las instancias de ejecución, lo que permite enviar mensajes vinculados a **eventos en tiempo real** y **eventos por lotes**.

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

Una vez publicada una plantilla, si se activa el evento correspondiente, la instancia de ejecución recibirá el evento, lo vinculará a la plantilla transaccional y enviará el mensaje transaccional correspondiente a cada destinatario. Para obtener más información, consulte [Procesamiento de eventos](../../message-center/using/about-event-processing.md).

>[!NOTE]
>
>Si se sustituye un campo existente de la plantilla de mensaje transaccional, como la dirección del remitente, con un valor vacío, el campo correspondiente de la(s) instancia(s) de ejecución no se actualizará una vez que se vuelva a publicar el mensaje transaccional. Aún contendrá el valor anterior.
>
>Sin embargo, si se agrega un valor no vacío, el campo correspondiente se actualiza de la forma habitual después de la siguiente publicación.

## Cancelación de publicación de una plantilla {#template-unpublication}

Una vez publicada una plantilla de mensaje en las instancias de ejecución, se puede cancelar su publicación. Para obtener más información sobre el proceso de publicación de la plantilla, consulte [esta sección](#template-publication).

* De hecho, se puede seguir llamando a una plantilla publicada si se activa el evento correspondiente: si ya no utiliza una plantilla de mensaje, se recomienda cancelar la publicación. Esto es para evitar enviar un mensaje transaccional no deseado por error.

   Por ejemplo, ha publicado una plantilla de mensaje que solo utiliza para campañas de Navidad. Tal vez quiera cancelar la publicación después de que termine el período de Navidad y publicarla nuevamente el año que viene.

* Tampoco puede eliminar una plantilla de mensaje transaccional que tenga el estado **[!UICONTROL Published]**. Primero debe cancelar la publicación.

>[!NOTE]
>
>Esta funcionalidad está disponible a partir de la versión 20.2 de Campaign.

Para cancelar la publicación de una plantilla de mensaje transaccional, siga los pasos a continuación.

1. En la instancia de control, vaya a la carpeta **[!UICONTROL Message Center > Transactional message templates]** del árbol.
1. Seleccione la plantilla cuya publicación desea cancelar.
1. Haga clic **[!UICONTROL Unpublish]**.

   <!--1. Fill in the **[!UICONTROL Log of the process]** field.-->

1. Haga clic **[!UICONTROL Start]**.

![](assets/message-center-unpublish.png)

El estado de la plantilla de mensaje transaccional cambia de **[!UICONTROL Published]** a **[!UICONTROL Being edited]**.

Una vez finalizada la cancelación de la publicación:

* Ambas plantillas de mensaje (aplicadas a eventos de tipo por lotes y en tiempo real) se eliminan de cada instancia de ejecución.

   Ya no aparecen en la carpeta **[!UICONTROL Administration > Production > Message Center Execution > Default > Transactional message templates]** (consulte [esta sección](#template-publication)).

* Una vez cancelada la publicación de una plantilla, puede eliminarla de la instancia de control si es necesario.

   Para ello, selecciónela en la lista y haga clic en el botón **[!UICONTROL Delete]** situado en la parte superior derecha de la pantalla.
