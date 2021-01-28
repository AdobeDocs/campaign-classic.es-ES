---
solution: Campaign Classic
product: campaign
title: AND-join
description: AND-join
audience: workflow
content-type: reference
topic-tags: flow-control-activities
translation-type: ht
source-git-commit: 3eecc16442a11849c12819cf83392f60c5b82a13
workflow-type: ht
source-wordcount: '190'
ht-degree: 100%

---


# AND-join{#and-join}

Una unión activa su transición saliente solo cuando se activan todas las transiciones entrantes, es decir, cuando terminan todas las actividades anteriores. Esto le permite asegurarse de que algunas actividades han finalizado antes de continuar ejecutándose el flujo de trabajo.

Por ejemplo, puede utilizar una actividad AND-join en el contexto de la creación de contenido y la automatización de entrega de envíos para asegurarse de que un envío se inicie solo cuando se hayan completado los pasos de consultas de destinatario y actualizaciones de contenido. Hay un caso de uso específico en [esta sección](../../delivery/using/automating-via-workflows.md#creating-the-delivery-and-its-content).

![](assets/and-join-usage.png)

>[!NOTE]
>
>Tenga en cuenta que las transiciones entrantes configuradas con diferentes dimensiones de segmentación no se pueden unir mediante una actividad **[!UICONTROL AND-join]**.

La población enviada de la actividad se determina seleccionando un conjunto principal entre las transiciones entrantes de la actividad.

La transición saliente solo puede contener una de las poblaciones de transición entrantes. Si la actividad no está configurada, la transición saliente seleccionará de forma aleatoria una de las poblaciones entrantes.

>[!CAUTION]
>
>En el caso de las actividades de tipo **AND-join**, las variables de eventos se combinan, pero si se define el mismo evento variable dos veces, se genera un conflicto y el valor se mantiene indeterminado. Para obtener más información, consulte [esta sección](../../workflow/using/javascript-scripts-and-templates.md#event-variables).
