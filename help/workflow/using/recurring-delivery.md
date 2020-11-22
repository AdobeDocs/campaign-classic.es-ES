---
solution: Campaign Classic
product: campaign
title: Entrega recurrente
description: Más información sobre la actividad del flujo de trabajo de envío recurrente
audience: workflow
content-type: reference
topic-tags: action-activities
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '199'
ht-degree: 95%

---


# Entrega recurrente{#recurring-delivery}

Una actividad de **[!UICONTROL Recurring delivery]** permite configurar una ocurrencia de plantilla de envío específica de una campaña.

Esta actividad solo está disponible en la pestaña **[!UICONTROL Targeting and workflows]** ubicada en una campaña.

Para ello:

1. Seleccione la plantilla de envío en la que se basa la actividad.

   ![](assets/recurring_delivery_001.png)

1. Configure la plantilla de envío.

El proceso de configuración de esta actividad es similar a la creación de una plantilla de envío en términos de las opciones disponibles. Para obtener más información, consulte [esta sección](../../delivery/using/about-templates.md).

Para ver un ejemplo de la actividad utilizada, consulte esta [sección](../../workflow/using/sending-a-birthday-email.md#creating-a-recurring-delivery-in-a-targeting-workflow).

## Configuración de envíos recurrentes

Un **envío recurrente** creará una nueva instancia de envío cada vez que se ejecute. Por ejemplo, si el flujo de trabajo está programado para ejecutarse una vez a la semana, el resultado sería de 52 envíos al cabo de un año. Esto también significa que el registro y los registros de seguimiento generales se separarán por cada instancia de envío.

![Entrega recurrente](assets/delivery_recurring.jpg)

En este vídeo se explica cómo configurar un envío recurrente y una actividad de planificador.

>[!VIDEO](https://video.tv.adobe.com/v/25040?quality=12)

>[!NOTE]
>
>No es posible enviar una prueba desde una actividad del tipo **[!UICONTROL Recurring delivery]**.\
>Para crear directamente una entrega a través de un flujo de trabajo de campaña, utilice las actividades específicas del canal que están preconfiguradas (por ejemplo **[!UICONTROL Email delivery]**).
