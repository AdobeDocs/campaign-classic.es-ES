---
solution: Campaign Classic
product: campaign
title: Señal externa
description: Descubra más información sobre la actividad del flujo de trabajo Señal externa
audience: workflow
content-type: reference
topic-tags: flow-control-activities
exl-id: da84d3ff-1e64-45ef-bef0-da4a24d93461
translation-type: ht
source-git-commit: 6854d06f8dc445b56ddfde7777f02916a60f2b63
workflow-type: ht
source-wordcount: '168'
ht-degree: 100%

---

# Señal externa{#external-signal}

La actividad **External signal** permite activar la ejecución de un conjunto de tareas en un flujo de trabajo a una programación.

Cuando se activa una tarea de “Señal externa”, se pone en pausa indefinidamente o hasta el final del periodo especificado. La transición se activa mediante la llamada de SOAP **PostEvent(sessionToken, workflowId, activity, transition, parameters, complete).** El parámetro **[!UICONTROL complete]** permite finalizar la tarea, por lo que no reaccionará a las llamadas posteriores.

Consulte la documentación en línea sobre las llamadas SOAP para obtener más información sobre la función PostEvent.

Puede configurar esta actividad para definir eventos si no se recibe ninguna señal. Para ello, edite la actividad y haga clic en la pestaña **[!UICONTROL Expiration]**. Haga clic en el botón **[!UICONTROL Insert]** para crear y configurar un evento.

![](assets/edit_signal.png)

La configuración de la caducidad se detalla en [Caducidad](../../workflow/using/defining-approvals.md).

El campo **Delay** permite especificar un retraso del vencimiento en las unidades que elija. Consulte [Espera](../../workflow/using/wait.md).

Cada línea representa un tipo de vencimiento y coincide con una transición.

![](assets/external_sign_diag.png)
