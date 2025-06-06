---
product: campaign
title: Entrega recurrente
description: Descubra más información sobre la actividad del flujo de trabajo Entrega recurrente
feature: Workflows
hide: true
hidefromtoc: true
exl-id: efd2cdfb-2e5f-4672-8be8-a424481b11ed
source-git-commit: 776c664a99721063dce5fa003cf40c81d94f8c78
workflow-type: ht
source-wordcount: '281'
ht-degree: 100%

---

# Entrega recurrente{#recurring-delivery}

Una actividad de **[!UICONTROL Recurring delivery]** permite configurar una ocurrencia de plantilla de envío específica de una campaña.

![](assets/do-not-localize/how-to-video.png) [Descubra esta función en vídeo](#recurring-delivery-video)

Esta actividad solo está disponible en la pestaña **[!UICONTROL Targeting and workflows]** ubicada en una campaña.

Para ello:

1. Seleccione la plantilla de envío en la que se basa la actividad.

   ![](assets/recurring_delivery_001.png)

1. Configure la plantilla de envío.

El proceso de configuración de esta actividad es similar a la creación de una plantilla de envío en términos de las opciones disponibles. Para obtener más información, consulte [esta sección](../../delivery/using/about-templates.md).

>[!CAUTION]
>
>Las entregas recurrentes no admiten la vista previa del contenido ni el envío de pruebas que incluyan elementos de personalización de [datos de destino](../../workflow/using/data-life-cycle.md#target-data).

Para ver un ejemplo de la actividad utilizada, consulte esta [sección](sending-a-birthday-email.md#creating-a-recurring-delivery-in-a-targeting-workflow).

## Configuración de envíos recurrentes {#set-up-recurring-delivery}

Un **envío recurrente** creará una nueva instancia de envío cada vez que se ejecute. Por ejemplo, si el flujo de trabajo está programado para ejecutarse una vez a la semana, el resultado serían 52 envíos al cabo de un año.  Esto también significa que el registro y los registros de seguimiento generales se separarán por cada instancia de envío.

![Entrega recurrente](assets/delivery_recurring.jpg)

Si desea detener la ejecución de una entrega recurrente, debe cancelar completamente la campaña o detener el flujo de trabajo que la ejecuta. Al detener la entrega desde el panel de Campaign, solo se detendrá la ocurrencia de la entrega: las siguientes instancias de la entrega recurrente se seguirán creando en cada ejecución del flujo de trabajo.

>[!NOTE]
>
>No es posible enviar una prueba desde una actividad del tipo **[!UICONTROL Recurring delivery]**.
> 
>Para crear directamente una entrega a través de un flujo de trabajo de campaña, utilice las actividades específicas del canal que están preconfiguradas (por ejemplo **[!UICONTROL Recurring delivery]**).

## Tutorial en vídeo {#recurring-delivery-video}

En este vídeo se explica cómo configurar un envío recurrente y una actividad de planificador.

>[!VIDEO](https://video.tv.adobe.com/v/27509?quality=12&captions=spa)

Hay disponibles más vídeos de procedimientos para Campaign Classic [aquí](https://experienceleague.adobe.com/docs/campaign-classic-learn/tutorials/overview.html?lang=es).
