---
solution: Campaign Classic
product: campaign
title: Bifurcación (Fork)
description: Descubra más información sobre la actividad del flujo de trabajo Bifurcación (fork)
audience: workflow
content-type: reference
topic-tags: flow-control-activities
translation-type: tm+mt
source-git-commit: 3eecc16442a11849c12819cf83392f60c5b82a13
workflow-type: tm+mt
source-wordcount: '207'
ht-degree: 16%

---


# Bifurcación (Fork){#fork}

La actividad **[!UICONTROL Fork]** le permite crear varias transiciones salientes para llevar a cabo varias actividades de forma independiente dentro del mismo flujo de trabajo.

Por ejemplo, puede utilizar la actividad después de una consulta para realizar dos acciones en paralelo:

* Guarde el resultado de la consulta en una audiencia,
* Ejecute una segmentación en el resultado para enviar varios envíos.

También puede utilizar la actividad en el contexto de la creación de contenido y la automatización del envío de envíos, para iniciar el cálculo de destinatarios y la creación de contenido en paralelo. Hay un caso de uso específico en [esta sección](../../delivery/using/automating-via-workflows.md#creating-the-delivery-and-its-content).

>[!WARNING]
>
>Tenga en cuenta que las transiciones de salida agregadas después de una actividad de horquilla no se ejecutarán simultáneamente.
>
>Por lo tanto, la actividad no debe utilizarse para mejorar el rendimiento del flujo de trabajo, sino para ejecutar varias actividades de forma independiente y, finalmente, unirlas antes de ejecutar el resto del flujo de trabajo.

Para configurar la actividad, ábrala y defina el número y la etiqueta de las transiciones de salida que desee.

![](assets/s_user_segmentation_fork.png)

A continuación, puede configurar cada transición de salida y luego unirlas mediante una actividad [AND-join](../../workflow/using/and-join.md), si es necesario. De este modo, el resto del flujo de trabajo se ejecutará sólo una vez finalizadas las transiciones salientes de la actividad **[!UICONTROL Fork]**.
