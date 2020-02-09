---
title: Control de envíos
seo-title: Control de envíos
description: Control de envíos
seo-description: null
page-status-flag: never-activated
uuid: f9cef2d9-a6a5-45bd-8c7a-fabc11879628
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: workflow
content-type: reference
topic-tags: action-activities
discoiquuid: 0b5ee05c-4b96-425a-ab0f-60b930de21bd
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: cfb1b02a6261c001392b5cc6430f00206e802bb8

---


# Control de envíos{#delivery-control}

Una acción del tipo **Delivery control** permite iniciar, pausar o detener un envío.

El envío puede ser especificado en la transición, un envío seleccionado de manera explícita o un envío calculado por un script. For more on this, refer to [Delivery](../../workflow/using/delivery.md).

![](assets/edit_diffusion_act.png)

If you select **[!UICONTROL Start]**, the activity will perform all the steps required to start the delivery (target calculation, content preparation, delivery). Si ya se han realizado algunos de estos pasos por una actividad de flujo de trabajo anterior, no se volverán a realizar. For instance, if the target estimation was already performed by a **[!UICONTROL Delivery]** type activity (refer to [Delivery](../../workflow/using/delivery.md)), the **[!UICONTROL Act on the delivery]** activity will launch the remaining steps (content preparation and delivery).

Estas son las opciones disponibles:

* **[!UICONTROL Generate an outbound transition]**

   Crea una transición saliente que se activará al final de la ejecución. Puede elegir si desea o no recuperar el objetivo del envío saliente.

* **[!UICONTROL Processing errors]**

   Consulte Errores [de procesamiento](../../workflow/using/monitoring-workflow-execution.md#processing-errors).

## Parámetros de entrada {#input-parameters}

* deliveryId

Identificador de entrega, si la acción seleccionada es **[!UICONTROL Specified in the transition]**.
