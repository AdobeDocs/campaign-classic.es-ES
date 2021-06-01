---
product: campaign
title: Control de entregas
description: Descubra más información sobre la actividad del flujo de trabajo Control de entregas
audience: workflow
content-type: reference
topic-tags: action-activities
exl-id: c7cface2-0837-4e6a-91dc-b8353010a7a4
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: tm+mt
source-wordcount: '164'
ht-degree: 100%

---

# Control de entregas{#delivery-control}

Una acción del tipo **Delivery control** permite iniciar, pausar o detener una entrega.

El envío puede ser especificado en la transición, una entrega seleccionado de manera explícita o una entrega calculado por un script. Para obtener más información, consulte [Entrega](../../workflow/using/delivery.md).

![](assets/edit_diffusion_act.png)

Si selecciona **[!UICONTROL Start]**, la actividad realizará todos los pasos necesarios para iniciar la entrega (cálculo del objetivo, preparación del contenido, envío). Si ya se han realizado algunos de estos pasos por una actividad de flujo de trabajo anterior, no se volverán a realizar. Por ejemplo, si la estimación del objetivo ya fue realizada por una actividad de tipo **[!UICONTROL Delivery]** (consulte [](../../workflow/using/delivery.md)), la actividad **[!UICONTROL Act on the delivery]** iniciará los pasos restantes (preparación y envío del contenido).

Estas son las opciones disponibles:

* **[!UICONTROL Generate an outbound transition]**

   Crea una transición saliente que se activará al final de la ejecución. Puede elegir si desea o no recuperar el objetivo de la entrega saliente.

* **[!UICONTROL Processing errors]**

   Consulte [Errores de procesamiento](../../workflow/using/monitoring-workflow-execution.md#processing-errors).

## Parámetros de entrada {#input-parameters}

* deliveryId

Identificador de envío, si la acción seleccionada es **[!UICONTROL Specified in the transition]**.
