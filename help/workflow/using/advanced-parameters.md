---
title: Parámetros avanzados
seo-title: Parámetros avanzados
description: Parámetros avanzados
seo-description: null
page-status-flag: never-activated
uuid: 9453d291-921b-4a03-80d1-2c8295f9a986
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: workflow
content-type: reference
topic-tags: advanced-management
discoiquuid: f66f1ff5-3601-4eb8-b05d-6f99164890ae
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: c10a0a11c6e9952aa47da1f7a15188c79c62508d

---


# Parámetros avanzados{#advanced-parameters}

The properties screen of an activity has an **[!UICONTROL Advanced]** tab that lets you define a behavior in case of errors, the execution period for the activity; and lets you enter an initialization script. Existen dos versiones de esta pestaña:

* una versión simplificada (por ejemplo, para **[!UICONTROL Start]** actividades y **[!UICONTROL End]** actividades)

   ![](assets/wf-advanced-basic.png)

* a more detailed version (for the **[!UICONTROL Query]** activity, for instance)

   ![](assets/wf-advanced-full.png)

The fields to be entered in the **[!UICONTROL Advanced]** tab are detailed in the following sections.

## Nombre {#name}

Este campo contiene el nombre interno de la actividad.

## Imagen {#image}

Este campo permite cambiar la imagen vinculada a una actividad. For more on this, refer to: [Managing activity images](../../workflow/using/managing-activity-images.md).

## Ejecución {#execution}

Este campo permite definir la acción que se ejecuta al activarse la tarea. Hay tres opciones posibles:

Generalmente, estas opciones se seleccionan en el carro haciendo clic con el botón derecho sobre la actividad.

* **[!UICONTROL Normal]**:: la actividad se ejecuta de la forma habitual.
* **[!UICONTROL Do not activate]**:: esta tarea y todas las siguientes tareas (en la misma rama) no se ejecutan.
* **[!UICONTROL Activate but do not execute]**:: esta tarea y todas las siguientes tareas (en la misma rama) se detienen automáticamente. Esto puede resultar útil si desea estar presente cuando comience la tarea. To execute the task manually, right-click the activity and select **[!UICONTROL Normal execution]**.

## Afinidad {#affinity}

Este campo le permite forzar la ejecución de una actividad en un equipo específico. For more on this, refer to: [Managing propensity](../../workflow/using/managing-propensity.md).

## Max. período de ejecución {#max--execution-period}

Este campo permite establecer una advertencia para los casos en los que la tarea tarde demasiado. No afecta a la operación del flujo de trabajo. If the task isn&#39;t finished by the time the **[!UICONTROL Max. execution period]** is over, the **[!UICONTROL Instance monitoring]** page will show a warning for this workflow. This page is accessed via the **[!UICONTROL Monitoring]** tab of the home page.

## Comportamiento {#behavior}

Este campo permite definir el comportamiento que se debe aplicar al utilizar tareas asíncronas. Hay dos opciones posibles:

* **[!UICONTROL Several tasks authorized]**:: se pueden ejecutar varias tareas a la vez, incluso si la primera no ha finalizado.
* **[!UICONTROL The current task has priority]**:: las tareas en curso tienen prioridad. Mientras una tarea esté en curso, no se ejecuta ninguna otra tarea.

## Zona horaria {#time-zone}

Este campo permite seleccionar la zona horaria de la actividad. Para más información sobre esto: [Administración de husos](../../workflow/using/managing-time-zones.md)horarios.

## En caso de errores {#in-case-of-errors}

Este campo permite definir la acción que debe llevarse a cabo cuando la actividad presenta errores. Hay dos opciones posibles:

* **[!UICONTROL Stop the process]**:: el flujo de trabajo se detiene automáticamente. Su estado cambia a **[!UICONTROL Failed]**. Una vez resuelto el problema, reinicie el flujo de trabajo.
* **[!UICONTROL Ignore]**:: esta tarea y todas las siguientes tareas (en la misma rama) no se ejecutan. Esto puede resultar útil para tareas recurrentes. Si la rama tiene un planificador en una posición anterior, este se ejecuta con normalidad en la siguiente fecha de ejecución.

## Secuencia de comandos de inicialización {#initialization-script}

Este campo permite inicializar las variables o modificar las propiedades de la actividad. Para obtener más información sobre esto, consulte: Plantillas y secuencias de comandos [JavaScript](../../workflow/using/javascript-scripts-and-templates.md).

## Comentario {#comment}

The **[!UICONTROL Comment]** field is a free field that lets you add a description.
