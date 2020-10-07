---
title: Servicios de suscripción
seo-title: Servicios de suscripción
description: Servicios de suscripción
seo-description: null
page-status-flag: never-activated
uuid: f8c05f8a-0791-4294-8aa3-69b7325e4d43
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: workflow
content-type: reference
topic-tags: targeting-activities
discoiquuid: 940bec7e-e3f0-4251-b7fe-72bf188743a7
translation-type: tm+mt
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: tm+mt
source-wordcount: '403'
ht-degree: 75%

---


# Servicios de suscripción{#subscription-services}

Una actividad del tipo de **Subscription services** permite crear o eliminar una suscripción a un servicio de información para la población especificada en la transición.

Para configurarlo, edite la actividad e introduzca la etiqueta, luego seleccione la acción que se ejecutará (suscripción o baja) y el servicio, como en el siguiente ejemplo:

![](assets/edit_service_inscription.png)

1. Introduzca la etiqueta de la actividad.
1. Select **[!UICONTROL Generate an outbound transition]** if you wish to create a transition at the end of the execution.

   Por lo general, la suscripción de un objetivo a un servicio de información marca el final del flujo de trabajo de objetivos, por lo que la opción no está activada de forma predeterminada.

1. Click **[!UICONTROL Subscription]** or **[!UICONTROL Unsubscription]** if you wish to subscribe or unsubscribe the specified population to or from the selected information service.
1. Select **[!UICONTROL Send a confirmation message]** to notify recipients that they are subscribed to or unsubscribed from a service.

   El contenido de este mensaje se especifica en la plantilla de envío asociada al servicio de información. Para obtener más información, consulte [esta sección](../../delivery/using/managing-subscriptions.md).

## Ejemplo: Suscribir una lista de destinatarios a un boletín informativo {#example--subscribe-a-list-of-recipients-to-a-newsletter}

En una única operación, el siguiente flujo de trabajo tiene como objetivo que una lista de destinatarios sea apta para un boletín informativo destinado a personas que trabajan y viven en París para hacer que se suscriban.

Para esto, también debe excluir los destinatarios que ya se hayan suscrito.

>[!CAUTION]
>
>Antes de suscribirse manualmente a un servicio, compruebe que estos destinatarios acepten recibir comunicaciones.

![](assets/subscription_services_example.png)

1. Añada las tres consultas siguientes:

   * Un primer objetivo de destinatarios de 18 a 60 años.
   * Un segundo objetivo de destinatarios que viven en París.
   * Un tercer objetivo de destinatarios que actualmente no están suscritos al boletín informativo.

1. Agregue una actividad de intersección para hacer referencia a los distintos resultados.
1. Si lo desea, inserte una actualización de la lista para mantener la lista de suscriptores actualizada.
1. Inserte una actividad de servicios de suscripción y haga doble clic en esta para configurarla.
1. Enter the activity label and select **[!UICONTROL Subscription]**.

   If you like, you can inform recipients of their newsletter subscription by checking the **[!UICONTROL Send a confirmation message]** box.

1. Seleccione la carpeta en la que se encuentra el boletín informativo y selecciónelo en la lista que aparece.
1. Leave the **[!UICONTROL Generate outbound transition]** unchecked so that this activity will mark the end of the workflow, then click **[!UICONTROL Ok]**.

Durante la ejecución del flujo de trabajo, los destinatarios que correspondan a las tres consultas se agregan a la lista y se suscriben al boletín informativo.

You can check that the subscription was successful by going to the **[!UICONTROL Subscription]** tab for your recipients.

## Parámetros de entrada {#input-parameters}

* tableName
* esquema

Cada evento entrante debe especificar un objetivo definido por estos parámetros.
