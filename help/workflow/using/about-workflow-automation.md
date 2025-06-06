---
product: campaign
title: Acerca de los flujos de trabajo
description: Automatice los procesos con flujos de trabajo, administre datos y audiencias, envíe mensajes, y mucho más
feature: Workflows, Data Management
exl-id: 024a7344-9376-4ff3-926a-003148229f9f
source-git-commit: b353b562bd2f0b0bd2dfde22c6477ab66d499483
workflow-type: tm+mt
source-wordcount: '232'
ht-degree: 9%

---

# Automatización con flujos de trabajo {#gs-workflows}

Los flujos de trabajo de Adobe Campaign permiten a su equipo optimizar y automatizar los procesos empresariales de extremo a extremo en toda la plataforma. Con una interfaz gráfica intuitiva, puede diseñar y administrar flujos de trabajo que coordinan tareas como la segmentación de datos, la ejecución de campañas, la administración de archivos e incluso las aprobaciones de usuarios, todo en un solo lugar.

Por ejemplo, puede automatizar un proceso para recuperar un archivo de un servidor remoto, extraer su contenido y cargar sin problemas los datos en el servidor de Adobe Campaign, lo que reduce el esfuerzo manual y aumenta la eficacia operativa. El motor de flujo de trabajo garantiza que cada paso se ejecute de forma fiable y que se rastree para obtener visibilidad y control.

>[!BEGINTABS]

>[!TAB Documentación del flujo de trabajo]

Para obtener más información sobre la administración de flujos de trabajo, consulte la [documentación de Campaign v8](https://experienceleague.adobe.com/docs/campaign/automation/workflows/introduction/about-workflows.html?lang=es){target=_blank}.


[![imagen](../../assets/do-not-localize/learn-more-button.svg)](https://experienceleague.adobe.com/docs/campaign/automation/workflows/introduction/about-workflows.html?lang=es){target=_blank}


>[!TAB Vínculos útiles]

Conozca los pasos clave relacionados con la administración de flujos de trabajo en la documentación de Campaign v8:

* [Actividades de flujo de trabajo](https://experienceleague.adobe.com/docs/campaign/automation/workflows/wf-activities/activities.html?lang=es){target=_blank}: una actividad es una plantilla de tarea. Los flujos de trabajo incluyen direccionamiento, control de flujo, acciones y actividades de evento.

* [Crear un flujo de trabajo](https://experienceleague.adobe.com/docs/campaign/automation/workflows/introduction/build-a-workflow.html?lang=es){target=_blank}: Aprenda a crear y ejecutar flujos de trabajo técnicos, de campañas y de segmentación.

* [Prácticas recomendadas](https://experienceleague.adobe.com/docs/campaign/automation/workflows/introduction/workflow-best-practices.html?lang=es){target=_blank}: Conozca las directrices para optimizar el rendimiento de los flujos de trabajo de Campaign, mejorar el diseño de los flujos de trabajo y definir la configuración correcta.

* [Supervisar flujos de trabajo](https://experienceleague.adobe.com/docs/campaign/automation/workflows/monitoring-workflows/monitor-workflow-execution.html?lang=es){target=_blank}: aprenda a monitorizar la ejecución del flujo de trabajo para asegurarse de que todo se ejecuta correctamente.

* [Casos de uso del flujo de trabajo](https://experienceleague.adobe.com/docs/campaign/automation/workflows/use-cases/workflow-use-cases.html?lang=es){target=_blank}: Conozca los contextos en los que se pueden utilizar los flujos de trabajo y cómo implementarlos a través de casos de uso de extremo a extremo.


>[!ENDTABS]





<!--

Adobe Campaign uses workflows to:

* Carry out targeting campaigns. [Learn more](building-a-workflow.md#implementation-steps-)
* Build campaigns: for each campaign, the **[!UICONTROL Workflow]** tab lets you build the target and create the deliveries. [Learn more](building-a-workflow.md#campaign-workflows)
* Perform technical processes: cleanup, collecting tracking information or provisional calculations. [Learn more](building-a-workflow.md#technical-workflows)

A workflow can mean both a process definition (the workflow model, which is a representation of what is supposed to happen) and an instance of this process (a workflow instance, which is a representation of what is actually happening).

The workflow template describes the various tasks to be performed and how they are linked together. The task templates are called activities and are represented by icons. They are linked together by transitions.

![](assets/example1.png)

Each workflow contains:

* **[!UICONTROL Activities]**

  An activity describes a task template. The various activities available are represented on the diagram by icons. Each type has common properties and specific properties. For example, while all activities have a name and label, only the **[!UICONTROL Approval]** activity has an assignment.

  In a workflow diagram, a given activity can produce multiple tasks, in particular when there is a loop or recurrent (periodic) actions.

  All workflow activities are listed in [this section](about-activities.md), including use cases and samples.

* **[!UICONTROL Transitions]**

  Transitions enable you to link activities and to define their sequence. A transition links a source activity to a destination activity. There are several sorts of transitions, which depend on the source activity. Some transitions have additional parameters such as a duration, a condition or a filter.

  A transition which is not linked to a destination activity is colored orange and the arrow head is shown as a diamond.

  >[!NOTE]
  >
  >A workflow containing unterminated transitions can still be executed: a warning message will be generated and the workflow will pause once it reaches the transition but it will not generate an error. It is thus possible to start a workflow without it being finished and to add to it as you go along.

  For more information about how to build a workflow, refer to [this section](building-a-workflow.md).

* **[!UICONTROL Worktables]**

  The worktable contains all the information carried by the transition. Each workflow uses several worktables. The data conveyed in these tables can be accelerated and used throughout the workflow's life cycle, as long as it is not purged. Indeed, unneeded tables are purged each time the workflow is passivated, and possibly during the execution of the largest workflows to avoid overloading the server.

  Learn more on workflow data and tables in [this section](how-to-use-workflow-data.md).

## Key principles and best practices{#principles-workflows}

Refer to these sections to find guidance and best practices to automate processes with workflows:

* Learn more about workflow activities in [this page](how-to-use-workflow-data.md).
* Learn how to build a workflow in [this section](building-a-workflow.md).
* Discover how to use workflows to import data in Campaign in [this section](../../platform/using/import-export-workflows.md).
* Workflow best practices are detailed in [this page](workflow-best-practices.md).
* Find guidance about workflow execution in [this section](starting-a-workflow.md).
* Learn how to monitor workflows in [this page](monitoring-workflow-execution.md).
* Learn how to grant access to users to use workflows in [this page](managing-rights.md).

-->