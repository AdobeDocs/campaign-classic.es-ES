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
translation-type: tm+mt
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: tm+mt
source-wordcount: '466'
ht-degree: 88%

---


# Parámetros avanzados{#advanced-parameters}

La pantalla de propiedades de una actividad tiene una pestaña **[!UICONTROL Advanced]** que permite definir un comportamiento en caso de errores, establecer el periodo de ejecución de la actividad e introducir una secuencia de comandos de inicialización. Existen dos versiones de esta pestaña:

* a simplified version (for **[!UICONTROL Start]** and **[!UICONTROL End]** activities for instance)

   ![](assets/wf-advanced-basic.png)

* una versión más detallada (para la actividad **[!UICONTROL Query]**, por ejemplo)

   ![](assets/wf-advanced-full.png)

Los campos que se introducen en la pestaña **[!UICONTROL Advanced]** se describen en las siguientes secciones.

## Nombre {#name}

Este campo contiene el nombre interno de la actividad.

## Imagen {#image}

Este campo permite cambiar la imagen vinculada a una actividad. Para obtener más información, consulte [Gestor imágenes de actividad](../../workflow/using/managing-activity-images.md).

## Ejecución {#execution}

Este campo permite definir la acción que se ejecuta al activarse la tarea. Hay tres opciones posibles:

Generalmente, estas opciones se seleccionan en el carro haciendo clic con el botón derecho sobre la actividad.

* **[!UICONTROL Normal]**: la actividad se ejecuta de la forma habitual.
* **[!UICONTROL Do not activate]**: esta tarea y todas las tareas siguientes (en la misma rama) no se ejecutan.
* **[!UICONTROL Activate but do not execute]**:: esta tarea y todas las siguientes tareas (en la misma rama) se detienen automáticamente. Esto puede resultar útil si desea estar presente cuando comience la tarea. Para ejecutar la tarea manualmente, haga clic con el botón derecho en la actividad y seleccione **[!UICONTROL Normal execution]**.

## Afinidad {#affinity}

Este campo le permite forzar la ejecución de una actividad en un equipo específico. Para obtener más información, consulte [Gestor de propensión](../../workflow/using/managing-propensity.md).

## Max. periodo de ejecución {#max--execution-period}

Este campo permite establecer una advertencia para los casos en los que la tarea tarde demasiado. No afecta a la operación del flujo de trabajo. If the task isn&#39;t finished by the time the **[!UICONTROL Max. execution period]** is over, the **[!UICONTROL Instance monitoring]** page will show a warning for this workflow. Se accede a esta página a través de la pestaña **[!UICONTROL Monitoring]** de la página principal.

## Comportamiento {#behavior}

Este campo permite definir el comportamiento que se debe aplicar al utilizar tareas asíncronas. Hay dos opciones posibles:

* **[!UICONTROL Several tasks authorized]**: se pueden ejecutar varias tareas a la vez, incluso si no ha finalizado la primera.
* **[!UICONTROL The current task has priority]**:: Las tareas en curso son prioritarias. Mientras una tarea esté en curso, no se ejecuta ninguna otra tarea.

## Zona horaria {#time-zone}

Este campo permite seleccionar la zona horaria de la actividad. Para más información sobre esto: [Administración de zonas horarias](../../workflow/using/managing-time-zones.md).

## En caso de errores {#in-case-of-errors}

Este campo permite definir la acción que debe llevarse a cabo cuando la actividad presenta errores. Hay dos opciones posibles:

* **[!UICONTROL Stop the process]**:: el flujo de trabajo se detiene automáticamente. Su estado cambia a **[!UICONTROL Failed]**. Una vez resuelto el problema, reinicie el flujo de trabajo.
* **[!UICONTROL Ignore]**: esta tarea y todas las tareas siguientes (en la misma rama) no se ejecutan. Esto puede resultar útil para tareas recurrentes. Si la rama tiene un planificador en una posición anterior, este se ejecuta con normalidad en la siguiente fecha de ejecución.

## Secuencia de comandos de inicialización {#initialization-script}

Este campo permite inicializar las variables o modificar las propiedades de la actividad. Para obtener más información, consulte [Scripts y plantillas de JavaScript](../../workflow/using/javascript-scripts-and-templates.md).

## Comentario {#comment}

El campo **[!UICONTROL Comment]** es un campo libre que permite añadir una descripción.
