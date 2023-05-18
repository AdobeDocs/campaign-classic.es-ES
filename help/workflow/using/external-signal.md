---
product: campaign
title: Señal externa
description: Descubra más información sobre la actividad del flujo de trabajo Señal externa
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
feature: Workflows
exl-id: da84d3ff-1e64-45ef-bef0-da4a24d93461
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
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

La configuración de la caducidad se detalla en [Caducidad](defining-approvals.md).

El campo **Delay** permite especificar un retraso del vencimiento en las unidades que elija. Consulte [Espera](wait.md).

Cada línea representa un tipo de vencimiento y coincide con una transición.

![](assets/external_sign_diag.png)
