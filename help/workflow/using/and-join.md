---
title: AND-join
seo-title: AND-join
description: AND-join
seo-description: null
page-status-flag: never-activated
uuid: 8234d6cd-0e9b-4187-9ddf-9e1f86aa1b9a
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: workflow
content-type: reference
topic-tags: flow-control-activities
discoiquuid: 075206aa-ff7b-4fa8-a05d-14a29fb119ba
index: y
internal: n
snippet: y
translation-type: ht
source-git-commit: f7ed7e59be2cfbde467b0c80d21cfbf52016a2b8
workflow-type: ht
source-wordcount: '171'
ht-degree: 100%

---


# AND-join{#and-join}

Una unión activa su transición saliente solo cuando se activan todas las transiciones entrantes, es decir, cuando terminan todas las actividades anteriores. Esto le permite asegurarse de que algunas actividades han finalizado antes de continuar ejecutándose el flujo de trabajo.

Por ejemplo, puede utilizar una actividad AND-join en el contexto de la creación de contenido y la automatización de entrega de envíos para asegurarse de que un envío se inicie solo cuando se hayan completado los pasos de consultas de destinatario y actualizaciones de contenido. Hay un caso de uso específico en [esta sección](../../delivery/using/automating-via-workflows.md#creating-the-delivery-and-its-content).

![](assets/and-join-usage.png)

La población enviada de la actividad se determina seleccionando un conjunto principal entre las transiciones entrantes de la actividad.

La transición saliente solo puede contener una de las poblaciones de transición entrantes. Si la actividad no está configurada, la transición saliente seleccionará de forma aleatoria una de las poblaciones entrantes.

>[!CAUTION]
>
>En el caso de las actividades de tipo **AND-join**, las variables de eventos se combinan, pero si se define el mismo evento variable dos veces, se genera un conflicto y el valor se mantiene indeterminado. Para obtener más información, consulte [](../../workflow/using/javascript-scripts-and-templates.md#event-variables).
