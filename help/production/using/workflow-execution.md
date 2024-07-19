---
product: campaign
title: Ejecución del flujo de trabajo
description: Ejecución del flujo de trabajo
feature: Monitoring, Workflows
badge-v7-prem: label="On-premise/híbrido solo" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=es" tooltip="Se aplica solo a implementaciones On-premise e híbridas"
audience: production
content-type: reference
topic-tags: troubleshooting
exl-id: b5aa5663-1902-4f50-9202-783e73a28838
source-git-commit: 1be1528d657537786c430ea9c8bdb3aad58ba20d
workflow-type: tm+mt
source-wordcount: '644'
ht-degree: 14%

---

# Ejecución del flujo de trabajo{#workflow-execution}



La sección siguiente presenta información sobre problemas comunes relacionados con la ejecución de flujos de trabajo y cómo solucionarlos.

Para obtener más información sobre los flujos de trabajo, consulte estas secciones:

* [Acerca de los flujos de trabajo](../../workflow/using/about-workflows.md)
* [Inicio de un flujo de trabajo](../../workflow/using/starting-a-workflow.md)
* [Ciclo de vida del flujo de trabajo](../../workflow/using/workflow-life-cycle.md)
* [Prácticas recomendadas al utilizar flujos de trabajo](../../workflow/using/workflow-best-practices.md)

## Iniciar lo antes posible en las campañas {#start-as-soon-as-possible-in-campaigns}

En algunos casos, los flujos de trabajo ejecutados desde una campaña no se inician al hacer clic en el botón **[!UICONTROL Start]**. En lugar de comenzar, pasa al estado &quot;Iniciar lo antes posible&quot;.

Puede haber varias causas para este problema. Siga los pasos a continuación para resolverlo:

1. Compruebe el estado del flujo de trabajo técnico [**[!UICONTROL operationMgt]**](../../workflow/using/about-technical-workflows.md). Este flujo de trabajo administra los trabajos o flujos de trabajo dentro de una campaña. Si falla, el resultado será que los flujos de trabajo no se inicien ni se detengan. Reinícielo para reanudar la ejecución de los flujos de trabajo de campaña.

   Para obtener más información sobre la supervisión de flujos de trabajo técnicos, consulte [esta página](../../workflow/using/monitoring-technical-workflows.md).

   >[!NOTE]
   >
   >Una vez reiniciado el flujo de trabajo, asegúrese de ejecutar las tareas pendientes (haga clic con el botón derecho en la actividad **[!UICONTROL Scheduler]** / **[!UICONTROL Execute pending task(s) now]**) para comprobar si vuelve a fallar en cualquiera de las actividades.

   Si el flujo de trabajo sigue fallando, compruebe el registro de auditoría para ver si hay algún error específico, solucione los problemas correspondientes y reinicie el flujo de trabajo de nuevo.

1. Compruebe el estado del módulo **[!UICONTROL wfserver]** en la ficha **[!UICONTROL Monitoring]**, a la que se puede acceder desde la página principal del Campaign Classic (consulte [Monitorización de procesos](../../production/using/monitoring-processes.md)). Este proceso es responsable de ejecutar todos los flujos de trabajo.

   Un usuario administrador también puede comprobar que el módulo **wfserver@`<instance>`** se inicie en el servidor de aplicaciones principal mediante el comando siguiente.

   ```
   nlserver pdump
   HH:MM:SS > Application server for Adobe Campaign Version X.Y (build XXXX) of DD/MM/YYYY
   [...]
   wfserver@<instance-name> (9340) - 11.3 Mb
   [...]
   ```

   Si el módulo no se está ejecutando, póngase en contacto con el Servicio de atención al cliente de Adobe. Si tiene una instalación on-premise, un usuario administrador debe reiniciar el servicio con el comando siguiente.

   ```
   nlserver start wfserver@<instance-name>
   ```

   >[!NOTE]
   >
   >Sustituya **`<instance-name>`** con el nombre de su instancia (producción, desarrollo, etc.). El nombre de instancia se identifica mediante los archivos de configuración:
   >`[path of application]nl6/conf/config-<instance-name>.xml`

   Para obtener más información sobre cómo reiniciar módulos, consulte [esta sección](../../production/using/usual-commands.md#module-launch-commands).

1. Compruebe si el **número de procesos de campaña que se ejecutan** en la instancia supera el umbral. Hay un límite definido por la opción [**[!UICONTROL NmsOperation_LimitConcurrency]**](../../installation/using/configuring-campaign-options.md#campaign-e-workflow-management) en cuanto a la cantidad de procesos de campaña que se pueden ejecutar en la instancia en paralelo. Cuando se alcanza este límite, el flujo de trabajo permanece en el estado &quot;Iniciar lo antes posible&quot; siempre y cuando el número de flujos de trabajo en ejecución supere el límite.

   Para resolver este problema, detenga los flujos de trabajo no deseados y elimine los envíos fallidos. Si se ha alcanzado el umbral, esto permite la ejecución de nuevos procesos.

   Para comprobar el número de flujos de trabajo que se están ejecutando en su instancia, se recomienda utilizar las vistas predefinidas, a las que se puede acceder de forma predeterminada en la carpeta **[!UICONTROL Administration]** / **[!UICONTROL Audit]**. Para obtener más información, consulte [esta página](../../workflow/using/monitoring-workflow-execution.md#filtering-workflows-status).

   >[!IMPORTANT]
   >
   >Si se aumenta el umbral de opción **[!UICONTROL NmsOperation_LimitConcurrency]** se pueden producir problemas de rendimiento en la instancia. En cualquier caso, no lo haga por su cuenta y póngase en contacto con su contacto de Adobe Campaign.

Para obtener más información sobre cómo monitorizar los flujos de trabajo, consulte [esta sección](../../workflow/using/monitoring-workflow-execution.md).

## Inicio en curso {#start-in-progress}

Si los flujos de trabajo no se están ejecutando y su estado es **Iniciar en curso**, puede que el módulo de flujo de trabajo no se inicie.

Para comprobar esto e iniciar el módulo si es necesario, aplique los siguientes pasos:

1. Compruebe el estado del módulo **[!UICONTROL wfserver]** en la ficha **[!UICONTROL Monitoring]**, a la que se puede acceder desde la página principal del Campaign Classic (consulte [Monitorización de procesos](../../production/using/monitoring-processes.md)).

   Un usuario administrador también puede comprobar que el módulo **wfserver@`<instance>`** se inicie en el servidor de aplicaciones principal mediante el comando siguiente.

   ```sql
   nlserver pdump
   HH:MM:SS > Application server for Adobe Campaign Classic (7.X YY.R build XXX@SHA1) of DD/MM/YYYY
   [...]
   wfserver@<instance-name> (9340) - 11.3 Mb
   [...]
   ```

   Para obtener más información sobre cómo supervisar módulos, consulte [esta sección](../../production/using/usual-commands.md#monitoring-commands-).

1. Si el módulo no se está ejecutando, póngase en contacto con el Servicio de atención al cliente de Adobe. Si tiene una instalación On-Premise, un administrador debe reiniciarla con el comando siguiente.

   ```
   nlserver start wfserver@<instance-name>
   ```

   >[!NOTE]
   >
   >Sustituya **`<instance-name>`** con el nombre de su instancia (producción, desarrollo, etc.). El nombre de instancia se identifica mediante los archivos de configuración:
   >`[path of application]nl6/conf/config-<instance-name>.xml`

   Para obtener más información sobre cómo reiniciar módulos, consulte [esta sección](../../production/using/usual-commands.md#module-launch-commands).

## Flujo de trabajo fallido {#failed-workflow}

Si un flujo de trabajo falla, realice los siguientes pasos:

1. Compruebe el historial de flujo de trabajo. Para obtener más información, consulte las secciones [Supervisión de la ejecución del flujo de trabajo](../../workflow/using/monitoring-workflow-execution.md) y [Visualización de registros](../../workflow/using/monitoring-workflow-execution.md#displaying-logs).
1. Monitorización de flujos de trabajo técnicos. Para obtener más información, consulte [esta sección](../../workflow/using/monitoring-technical-workflows.md).
1. Busque errores en las actividades de flujo de trabajo individuales.
