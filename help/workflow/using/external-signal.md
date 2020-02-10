---
title: Señal externa
seo-title: Señal externa
description: Señal externa
seo-description: null
page-status-flag: never-activated
uuid: dbe6624a-70cf-4ac4-adfd-bc72db9bb3f3
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: workflow
content-type: reference
topic-tags: flow-control-activities
discoiquuid: 3739593f-056c-4165-87ef-63c812bd3c43
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 20f835c357d016643ea1f3209ee4dfb6d3239f90

---


# Señal externa{#external-signal}

La actividad **External signal** permite activar la ejecución de un conjunto de tareas en un flujo de trabajo a una programación.

Cuando se activa una tarea de “Señal externa”, se pone en pausa indefinidamente o hasta el final del periodo de tiempo especificado. La transición se activa mediante la llamada de SOAP **PostEvent(sessionToken, workflowId, activity, transition, parameters, complete).** El **[!UICONTROL complete]** parámetro permite finalizar la tarea, por lo que no reaccionará a las llamadas posteriores.

Consulte la documentación en línea sobre las llamadas SOAP para obtener más información sobre la función PostEvent.

Puede configurar esta actividad para definir eventos si no se recibe ninguna 
        señal. To do this, edit the activity and click the **[!UICONTROL Expiration]** tab. Click the **[!UICONTROL Insert]** button to create and configure an event.

![](assets/edit_signal.png)

The configuration of expirations is detailed in [Expirations](../../workflow/using/executing-a-workflow.md#expirations).

El campo **Delay** permite especificar un retraso del vencimiento en las unidades que elija. Consulte [Espera](../../workflow/using/wait.md).

Cada línea representa un tipo de vencimiento y coincide con una transición.

![](assets/external_sign_diag.png)

