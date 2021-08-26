---
product: campaign
title: Bifurcación (Fork)
description: Descubra más información sobre la actividad del flujo de trabajo Bifurcación (fork)
audience: workflow
content-type: reference
topic-tags: flow-control-activities
exl-id: 7a38653b-c15d-4ed8-85dc-f7214409f42b
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '196'
ht-degree: 100%

---

# Bifurcación{#fork}

![](../../assets/common.svg)

La actividad **[!UICONTROL Fork]** le permite crear varias transiciones salientes para llevar a cabo varias actividades de forma independiente dentro del mismo flujo de trabajo.

Por ejemplo, puede utilizar la actividad después de una consulta para realizar dos acciones en paralelo:

* Guarde el resultado de la consulta en una audiencia,
* Ejecute una segmentación en el resultado para entregar varios envíos.

También puede utilizar la actividad en el contexto de la creación de contenido y la automatización de entregas de envíos para iniciar el cálculo de destinatarios y la creación de contenido al mismo tiempo. Hay un caso de uso específico en [esta sección](../../delivery/using/automating-via-workflows.md#creating-the-delivery-and-its-content).

>[!IMPORTANT]
>
>Las transiciones salientes agregadas después de una actividad **[!UICONTROL Fork]** **no se ejecutarán** simultáneamente. Este comportamiento puede afectar al rendimiento del flujo de trabajo. Utilice esta actividad si necesita ejecutar varias actividades de forma independiente y, finalmente, únalas antes de ejecutar el resto del flujo de trabajo.

Para configurar la actividad **[!UICONTROL Fork]**, ábrala y defina el número y la etiqueta de las transiciones de salida que desee.

![](assets/s_user_segmentation_fork.png)

A continuación, puede configurar cada transición de salida y, luego, unirlas mediante una actividad [AND-join](and-join.md) si es necesario. De este modo, el resto del flujo de trabajo se ejecutará solo cuando finalicen las transacciones salientes de la actividad **[!UICONTROL Fork]**.
