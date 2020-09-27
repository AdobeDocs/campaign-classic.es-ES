---
title: Acerca de los flujos de trabajo
description: Automatice los procesos con flujos de trabajo, administre datos y audiencias, envíe mensajes y mucho más.
page-status-flag: never-activated
uuid: 19adb0e5-042d-47a0-9f92-24e4b3045dbe
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: workflow
content-type: reference
topic-tags: introduction
discoiquuid: 868940d1-f19d-4e9a-bffa-8654abb4441c
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 700cd82d87eccf6579afab5c9e8f7945807817da
workflow-type: tm+mt
source-wordcount: '668'
ht-degree: 84%

---


# Get started with workflows{#about-workflows}

## Acerca de los flujos de trabajo

Adobe Campaign incluye un módulo de flujos de trabajo que permite organizar la gama completa de procesos y tareas en los distintos módulos del servidor de aplicaciones. Este entorno gráfico completo permite diseñar procesos, incluso la segmentación, la ejecución de campañas, el procesamiento de archivos, la participación humana, etc. El motor de flujo de trabajo se ejecuta y rastrea estos procesos.

Se puede utilizar un flujo de trabajo, por ejemplo, para descargar un archivo de un servidor, descomprimirlo y, a continuación, importar registros de la base de datos de Adobe Campaign.

Un flujo de trabajo también puede incluir uno o varios operadores por notificar o que pueden realizar acciones y aprobar procesos. De este modo, es posible crear una acción de envío, asignar una tarea a uno o varios operadores para trabajar en el contenido, especificar objetivos y verificar pruebas antes de iniciar la entrega.

Los flujos de trabajo se producen en varios contextos y etapas del proceso de administración de campañas.

Adobe Campaign utiliza flujos de trabajo para:

* Llevar a cabo las campañas de objetivos. Para obtener más información, consulte [Pasos de implementación](../../workflow/using/building-a-workflow.md#implementation-steps-).
* Generar campañas: para cada campaña, la pestaña **[!UICONTROL Workflow]** permite crear el objetivo y las entregas. Para obtener más información, consulte [Flujos de trabajo de campaña](../../workflow/using/building-a-workflow.md#campaign-workflows).
* Realizar procesos técnicos: limpieza, recopilación de información de seguimiento o cálculos provisionales. Para obtener más información, consulte [Flujos de trabajo técnicos](../../workflow/using/building-a-workflow.md#technical-workflows).

Un flujo de trabajo puede significar una definición de proceso (el modelo de flujo de trabajo, que es una representación de lo que se supone que debe ocurrir) y una instancia de este proceso (una instancia de flujo de trabajo, que es una representación de lo que realmente sucede).

La plantilla de flujo de trabajo describe las diversas tareas que se realizan y cómo se relacionan entre sí. Las plantillas de tareas se denominan actividades y se representan mediante iconos. Se vinculan entre sí mediante transiciones.

![](assets/example1.png)

Cada flujo de trabajo contiene:

* **[!UICONTROL Activities]**

   Una actividad describe una plantilla de tarea. Las distintas actividades disponibles se representan en el diagrama mediante iconos. Cada tipo tiene propiedades comunes y propiedades específicas. Por ejemplo, mientras que todas las actividades tienen un nombre y una etiqueta, solo la actividad **[!UICONTROL Approval]** tiene una asignación.

   En un diagrama de flujo de trabajo, una actividad determinada puede producir varias tareas, en particular cuando hay un bucle o una acción recurrente (periódica).

   Todas las actividades de flujo de trabajo se enumeran en [esta sección](../../workflow/using/about-activities.md), incluidos los ejemplos de uso y las muestras.

* **[!UICONTROL Transitions]**

   Las transiciones permiten vincular actividades y definir su secuencia. Una transición vincula una actividad de origen a una actividad de destino. Existen varios tipos de transiciones que dependen de la actividad de origen. Algunas transiciones tienen parámetros adicionales, como una duración, una condición o un filtro.

   Una transición que no está vinculada a una actividad de destino aparece en color naranja, y la cabeza de la flecha se muestra como un diamante.

   >[!NOTE]
   >
   >Se puede ejecutar igualmente un flujo de trabajo que contenga transiciones no finalizadas: se genera un mensaje de advertencia y el flujo de trabajo se pausa una vez que llega a la transición, pero no genera un error. Por lo tanto, es posible iniciar un flujo de trabajo sin que haya terminado y añadirlo a medida que avanza

   Para obtener más información sobre la creación de flujos de trabajo, consulte [esta sección](../../workflow/using/building-a-workflow.md).

* **[!UICONTROL Worktables]**

   La tabla de trabajo contiene toda la información que transmite la transición. Cada flujo de trabajo utiliza varias tablas de trabajo. Los datos transmitidos en estas tablas pueden acelerarse y utilizarse en todo el ciclo de vida del flujo de trabajo, siempre y cuando no se depure. De hecho, las tablas innecesarias se depuran cada vez que se desactiva el flujo de trabajo y posiblemente durante la ejecución de los flujos de trabajo más grandes para evitar sobrecargar el servidor.

   Para obtener más información sobre los datos y las tablas de flujos de trabajo, consulte [esta sección](../../workflow/using/how-to-use-workflow-data.md).

## Principios fundamentales y prácticas recomendadas

Consulte estas secciones para obtener instrucciones y optimizaciones para automatizar procesos con flujos de trabajo:

* Obtenga más información sobre las actividades de flujo de trabajo en [esta página](../../workflow/using/how-to-use-workflow-data.md).
* Obtenga información sobre cómo crear un flujo de trabajo en [esta sección](../../workflow/using/building-a-workflow.md).
* Descubra cómo utilizar flujos de trabajo para importar datos en Campaña en [esta sección](../../workflow/using/importing-data.md).
* Las optimizaciones del flujo de trabajo se detallan en [esta página](../../workflow/using/workflow-best-practices.md).
* Encontrará instrucciones sobre la ejecución del flujo de trabajo en [esta sección](../../workflow/using/starting-a-workflow.md).
* Obtenga información sobre cómo supervisar flujos de trabajo en [esta página](../../workflow/using/monitoring-workflow-execution.md).
* Obtenga información sobre cómo conceder acceso a los usuarios para que utilicen flujos de trabajo en [esta página](../../workflow/using/managing-rights.md).
