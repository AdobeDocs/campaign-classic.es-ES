---
product: campaign
title: Inicio de un flujo de trabajo
description: Obtenga información sobre cómo iniciar un flujo de trabajo y descubra acciones de flujos de trabajo en la barra de herramientas y el menú que aparece al hacer clic con el botón derecho
badge-v7-only: label="v7" type="Informative" tooltip="Se aplica solo a Campaign Classic v7"
feature: Workflows
exl-id: d345ba62-c2fb-43df-a2a1-e9e4292d301a
source-git-commit: 1baf424138c95b16add37d9d556e3a2566a869c2
workflow-type: tm+mt
source-wordcount: '1116'
ht-degree: 97%

---

# Inicio de un flujo de trabajo {#starting-a-workflow}



Un flujo de trabajo siempre se inicia manualmente. Cuando se inicia, no obstante, puede permanecer inactivo según la información especificada mediante un planificador (consulte [Scheduler](scheduler.md)) o una planificación de actividad.

Acciones relacionadas con la ejecución del flujo de trabajo de objetivos (inicio, parada, pausa, etc.) son **asíncrono** processes: el pedido se registra y entra en vigor en cuanto el servidor esté disponible para aplicarlo.

La barra de herramientas permite iniciar y rastrear la ejecución del flujo de trabajo.

A continuación se detalla la lista de opciones disponibles en el menú **[!UICONTROL Actions]** y el menú contextual.

>[!IMPORTANT]
>
>Tenga en cuenta que cuando un operador realiza una acción en un flujo de trabajo (inicio, detención, pausa, etc.), la acción no se ejecuta de inmediato, sino que se coloca en una cola para que la procese el [módulo de flujo de trabajo](architecture.md).

## Barra de herramientas de acciones {#actions-toolbar}

Los botones de la barra de herramientas se encuentran en esta [sección](../../campaign/using/marketing-campaign-deliveries.md#building-the-main-target-in-a-workflow). El botón **[!UICONTROL Actions]** le permite acceder a opciones de ejecución adicionales para actuar sobre los flujos de trabajo seleccionados. También puede utilizar el menú **[!UICONTROL File > Actions]** o hacer clic con el botón derecho del ratón en un flujo de trabajo y seleccionar **[!UICONTROL Actions]**.

![](assets/purge_historique.png)

* **[!UICONTROL Start]**

  Esta acción le permite iniciar la ejecución de un flujo de trabajo: un flujo de trabajo que aparezca como **Finalizado**, **Edición en curso** o **En pausa** cambia de estado a **Iniciado**. El motor de flujo de trabajo gestiona entonces la ejecución de este flujo de trabajo. Si el flujo de trabajo estaba en pausa, se reanuda, pero de lo contrario el flujo de trabajo se inicia desde el principio y se activan las actividades iniciales.

  El inicio es un proceso asincrónico: la solicitud se guarda y se procesa lo antes posible mediante un servidor de flujo de trabajo.

* **[!UICONTROL Pause]**

  Esta acción establece el estado del flujo de trabajo como **En pausa**. No se activa ninguna actividad hasta que se reanuda el flujo de trabajo; sin embargo, las operaciones en curso no se detienen.

* **[!UICONTROL Stop]**

  Esta acción detiene un flujo de trabajo que se está ejecutando. El estado de la instancia se establece como **Finalizado**. Las operaciones en curso se detienen, si es posible. Las consultas SQL y las importaciones se cancelan inmediatamente.

  >[!IMPORTANT]
  >
  >La detención de un flujo de trabajo es un proceso asíncrono: la solicitud se registra y, después, el servidor o los servidores de flujo de trabajo cancelan las operaciones en curso. Por lo tanto, la detención de una instancia de flujo de trabajo puede llevar tiempo, especialmente si el flujo de trabajo se ejecuta en varios servidores, cada uno de los cuales debe asumir el control para cancelar las tareas en curso. Para evitar cualquier problema, espere a que se complete la operación de detención y no realice varias solicitudes en el mismo flujo de trabajo.

* **[!UICONTROL Unconditional stop]**

  Esta opción cambia el estado del flujo de trabajo a **[!UICONTROL Finished]**. Esta acción debe utilizarse únicamente como último recurso si el proceso de detención normal falla tras varios minutos. Utilice únicamente la detención incondicional si está seguro de que no hay tareas de trabajos de flujo en curso.

  >[!CAUTION]
  >
  >Esta opción se reserva para usuarios expertos.

* **[!UICONTROL Restart]**

  Esta acción detiene y reinicia el flujo de trabajo. En la mayoría de los casos, es posible reiniciarlo más rápido. También resulta útil automatizar el reinicio cuando la detención lleva una determinada cantidad de tiempo: esto sucede porque el comando “Detener” no está disponible cuando el flujo de trabajo se detiene.

  Las acciones **[!UICONTROL Start / Pause / Stop / Restart]** también están disponibles a través de los iconos de ejecución de la barra de herramientas. Para obtener más información, consulte [esta sección](../../campaign/using/marketing-campaign-deliveries.md#creating-a-targeting-workflow).

* **[!UICONTROL Purge history]**

  Esta acción permite depurar el historial del flujo de trabajo. Para obtener más información, consulte [Depuración de “logs”](monitoring-workflow-execution.md#purging-the-logs).

* **[!UICONTROL Start in simulation mode]**

  Esta opción permite iniciar el flujo de trabajo en modo de simulación, distinto del modo real. Esto significa que, cuando se activa este modo, solo se ejecutan las actividades que no afectan a la base de datos o al sistema de archivos (por ejemplo **[!UICONTROL Query]**, **[!UICONTROL Union]**, **[!UICONTROL Intersection]**, etc.). Actividades que sí tienen impacto (por ejemplo, **[!UICONTROL Export]**, **[!UICONTROL Import]**, etc.). no se ejecutan ni los que se encuentran después de ellos (en la misma rama).

* **[!UICONTROL Execute pending tasks now]**

  Esta acción le permite iniciar todas las tareas pendientes lo antes posible. Para iniciar una tarea específica, haga clic con el botón derecho en su actividad y seleccione **[!UICONTROL Execute pending task(s) now]**.

* **[!UICONTROL Save as template]**

  Esta acción crea una nueva plantilla de flujo de trabajo basada en el flujo de trabajo seleccionado. Debe especificar la carpeta donde desea que se guarde (en el campo **[!UICONTROL Folder]**).

  Las opciones **[!UICONTROL Mass update of selected lines]** y **[!UICONTROL Merge selected lines]** son opciones genéricas de plataforma disponibles en todos los menús **[!UICONTROL Actions]**. Para obtener más información, consulte [esta sección](../../platform/using/updating-data.md).


## Prácticas recomendadas para la ejecución de flujos de trabajo {#workflow-execution-best-practices}

**No programe un flujo de trabajo para que se ejecute con una frecuencia superior a 15 minutos**, ya que podría limitar el rendimiento general del sistema y crear bloques en la base de datos.

**Asimismo, evite dejar los flujos de trabajo en estado pausado**. Si crea un flujo de trabajo temporal, asegúrese de que este pueda terminar correctamente y no permanecer en estado **[!UICONTROL paused]**. Si está en pausa, eso implica que necesita mantener las tablas temporales y, por lo tanto, aumentar el tamaño de la base de datos. Asigne supervisores de flujo de trabajo en Workflow Properties para enviar una alerta cuando un flujo de trabajo falle o el sistema lo ponga en pausa.

Para evitar tener flujos de trabajo en estado pausado:

* Consulte los flujos de trabajo regularmente para garantizar que no hay errores inesperados.
* Mantenga los flujos de trabajo tan sencillos como sea posible, por ejemplo, dividiendo los flujos de trabajo grandes en distintos flujos de trabajo. Puede utilizar las actividades **[!UICONTROL External signal]** impulsando la ejecución en función de la ejecución de otros flujos de trabajo.
* Evite tener actividades desactivadas con flujos en los flujos de trabajo, dejando los subprocesos abiertos y generando que muchas tablas temporales puedan consumir mucho espacio. Evite mantener las actividades en estados **[!UICONTROL Do not enable]** o **[!UICONTROL Enable but do not execute]** en los flujos de trabajo.

**Detenga los flujos de trabajo no utilizados**. Los flujos de trabajo que siguen ejecutándose mantienen conexiones con la base de datos.

**Solo se debe utilizar la detención incondicional en los casos más inusuales**. Evite utilizar esta acción de forma regular. El no realizar un cierre limpio de las conexiones generadas por los flujos de trabajo a la base de datos afecta al rendimiento.

**No realice varias solicitudes de detención en el mismo flujo de trabajo**. La detención de un flujo de trabajo es un proceso asíncrono: la solicitud se registra y, después, el servidor o los servidores de flujo de trabajo cancelan las operaciones en curso. Por lo tanto, la detención de una instancia de flujo de trabajo puede llevar tiempo, especialmente si el flujo de trabajo se ejecuta en varios servidores, cada uno de los cuales debe asumir el control para cancelar las tareas en curso. Para evitar cualquier problema, espere a que se complete la operación de parada y evite detener un flujo de trabajo varias veces.

## Menú del botón derecho {#right-click-menu}

Cuando haya seleccionado una o más actividades de flujo de trabajo, puede hacer clic con el botón derecho para actuar sobre la selección.

![](assets/contextual_menu.png)

Las siguientes opciones están disponibles en el menú del botón derecho:

**[!UICONTROL Open]**: esta opción permite acceder a las propiedades de la actividad.

**[!UICONTROL Display logs:]** esta opción permite ver el “log” de ejecución de la tarea para la actividad seleccionada. Consulte [Visualización de “logs”](monitoring-workflow-execution.md#displaying-logs).

**[!UICONTROL Execute pending task(s) now:]** esta acción permite iniciar tareas pendientes lo antes posible.

**[!UICONTROL Workflow restart from a task:]** esta opción permite reiniciar el flujo de trabajo con los resultados almacenados anteriormente para esta actividad.

**[!UICONTROL Cut/Copy/Paste/Delete:]** estas opciones permiten cortar, copiar, pegar y eliminar actividades.

**[!UICONTROL Copy as bitmap:]** esta opción permite realizar una captura de pantalla de todas las actividades.

**[!UICONTROL Normal execution / Enable but do not execute / Do not enable:]** : estas opciones están disponibles en la pestaña **[!UICONTROL Advanced]** de las propiedades de actividad. Se encuentran detalladas en [Execution](advanced-parameters.md#execution).

**[!UICONTROL Save / Cancel:]** permite guardar o cancelar los cambios realizados en un flujo de trabajo.

>[!NOTE]
>
>Puede seleccionar un grupo de actividades y aplicar uno de estos comandos.

El menú contextual del botón derecho también se detalla en esta [sección](../../campaign/using/marketing-campaign-deliveries.md#executing-a-workflow).
