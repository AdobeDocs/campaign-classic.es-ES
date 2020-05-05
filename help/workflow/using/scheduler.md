---
title: Planificador
seo-title: Planificador
description: Planificador
seo-description: null
page-status-flag: never-activated
uuid: e814b978-2edd-442e-9334-9633bc9ec63a
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: workflow
content-type: reference
topic-tags: flow-control-activities
discoiquuid: 093dbe8a-494f-4fe7-8614-3bf58486e34c
index: y
internal: n
snippet: y
translation-type: ht
source-git-commit: 707352334144df86ae82aa51d595ae6bc751d1f2

---


# Planificador{#scheduler}

El **Scheduler** es una tarea persistente que activa su transición en el momento especificado por su programación.

La actividad del **[!UICONTROL Scheduler]** debe considerarse como un inicio programado. Las reglas de colocación de actividad dentro del gráfico son las mismas que para la actividad **[!UICONTROL Start]**. Esta actividad no debe tener una transición entrante.

Se recomienda no planificar un flujo de trabajo para que se ejecute durante más de 15 minutos, ya que podría limitar el rendimiento general del sistema y crear bloques en la base de datos.

Al generar el flujo de trabajo, evite utilizar más de una actividad **[!UICONTROL Scheduler]** por rama. Para obtener más información, consulte: [Uso de actividades](../../workflow/using/workflow-best-practices.md#using-activities).

El planificador define la programación de activación de la transición. Para configurarlo, haga doble clic en el objeto gráfico y, a continuación, haga clic en **[!UICONTROL Change...]**.

![](assets/s_user_segmentation_scheduler.png)

Un asistente le permite definir la frecuencia y el periodo de validez de la actividad. Los pasos de configuración son los siguientes:

1. Seleccione la frecuencia de activación y haga clic en **[!UICONTROL Next]**.

   ![](assets/s_user_segmentation_scheduler2.png)

1. Indique las horas y días de activación. Los parámetros de este paso dependen de la frecuencia seleccionada en el paso anterior. Si elige iniciar la actividad varias veces al día, las opciones de configuración serán las siguientes:

   ![](assets/s_user_segmentation_scheduler3.png)

1. Defina el periodo de validez de la programación o especifique cuántas veces se va a ejecutar.

   ![](assets/s_user_segmentation_scheduler4.png)

1. Compruebe la configuración y haga clic en **[!UICONTROL Finish]** para guardar.

   ![](assets/s_user_segmentation_scheduler5.png)

El uso de una actividad de planificador puede llevar a que se realicen varias ejecuciones de un flujo de trabajo al mismo tiempo. Por ejemplo, puede hacer que un programador active la ejecución del flujo de trabajo cada hora, pero a veces la ejecución del flujo de trabajo completo tarda más de una hora. Puede preferir omitir la ejecución si el flujo de trabajo ya se está ejecutando. Para obtener más información sobre cómo evitar ejecuciones simultáneas de un flujo de trabajo, consulte [esta página](../../workflow/using/monitoring-workflow-execution.md#preventing-simultaneous-multiple-executions).

Tenga en cuenta también que la transición puede activarse varias horas más tarde si el flujo de trabajo ejecuta una tarea a largo plazo como una importación, o si el módulo wfserver se detuvo durante un tiempo. En este caso, puede ser necesario restringir la ejecución de la tarea activada por el planificador a un determinado intervalo de tiempo.
