---
product: campaign
title: Ejecución del flujo de trabajo
description: Ejecución del flujo de trabajo
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
badge-v7-prem: label="on-premise & hybrid" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=en" tooltip="Applies to on-premise and hybrid deployments only"
audience: production
content-type: reference
topic-tags: troubleshooting
exl-id: b5aa5663-1902-4f50-9202-783e73a28838
source-git-commit: 4b13e310fcee9ba24e83b697fca57bc494505642
workflow-type: tm+mt
source-wordcount: '633'
ht-degree: 13%

---

# Ejecución del flujo de trabajo{#workflow-execution}



La sección siguiente presenta información sobre problemas comunes relacionados con la ejecución de flujos de trabajo y cómo solucionarlos.

Para obtener más información sobre los flujos de trabajo, consulte estas secciones:

* [Acerca de los flujos de trabajo](../../workflow/using/about-workflows.md)
* [Inicio de un flujo de trabajo](../../workflow/using/starting-a-workflow.md)
* [Ciclo de vida del flujo de trabajo](../../workflow/using/workflow-life-cycle.md)
* [Prácticas recomendadas al utilizar flujos de trabajo](../../workflow/using/workflow-best-practices.md)

## Comience lo antes posible en las campañas {#start-as-soon-as-possible-in-campaigns}

En algunos casos, los flujos de trabajo ejecutados desde una campaña no se inician al hacer clic en el botón **[!UICONTROL Start]** botón. En lugar de comenzar, pasa al estado &quot;Iniciar lo antes posible&quot;.

Puede haber varias causas para este problema, siga los pasos a continuación para solucionarlo:

1. Marque la [**[!UICONTROL operationMgt]**](../../workflow/using/about-technical-workflows.md) estado técnico del flujo de trabajo. Este flujo de trabajo administra los trabajos o flujos de trabajo dentro de una campaña. Si falla, esto provocará que los flujos de trabajo no se inicien ni se detengan. Reinicie para reanudar la ejecución de los flujos de trabajo de la campaña.

   Para obtener más información sobre la monitorización de flujos de trabajo técnicos, consulte [esta página](../../workflow/using/monitoring-technical-workflows.md).

   >[!NOTE]
   >
   >Una vez reiniciado el flujo de trabajo, asegúrese de ejecutar las tareas pendientes (haga clic con el botón derecho en el botón **[!UICONTROL Scheduler]** actividad / **[!UICONTROL Execute pending task(s) now]**) para comprobar si vuelve a fallar en cualquiera de las actividades.

   Si el flujo de trabajo sigue fallando, compruebe si hay algún error específico en el registro de auditoría, solucione los problemas correspondientes y, a continuación, reinicie el flujo de trabajo de nuevo.

1. Marque la **[!UICONTROL wfserver]** estado del módulo en la variable **[!UICONTROL Monitoring]** pestaña , accesible desde la página principal del Campaign Classic (consulte [Monitorización de procesos](../../production/using/monitoring-processes.md)). Este proceso es responsable de ejecutar todos los flujos de trabajo.

   Un usuario administrador también puede comprobar que la variable **wfserver@`<instance>`** se inicia en el servidor de aplicaciones principal mediante el comando siguiente.

   ```
   nlserver pdump
   HH:MM:SS > Application server for Adobe Campaign Version X.Y (build XXXX) of DD/MM/YYYY
   [...]
   wfserver@<instance-name> (9340) - 11.3 Mb
   [...]
   ```

   Si el módulo no se está ejecutando, póngase en contacto con el servicio de atención al cliente de Adobe. Si tiene una instalación local, un usuario administrador debe reiniciar el servicio mediante el comando siguiente.

   ```
   nlserver start wfserver@<instance-name>
   ```

   >[!NOTE]
   >
   >Sustituya **`<instance-name>`** con el nombre de su instancia (producción, desarrollo, etc.). El nombre de instancia se identifica mediante los archivos de configuración:
   >`[path of application]nl6/conf/config-<instance-name>.xml`

   Para obtener más información sobre cómo reiniciar los módulos, consulte [esta sección](../../production/using/usual-commands.md#module-launch-commands).

1. Compruebe si la variable **número de procesos de campaña en ejecución** en la instancia es mayor que el umbral. Hay un límite definido por la variable [**[!UICONTROL NmsOperation_LimitConcurrency]**](../../installation/using/configuring-campaign-options.md#campaign-e-workflow-management) sobre cuántos procesos de campaña se pueden ejecutar en la instancia en paralelo. Cuando se alcanza este límite, el flujo de trabajo permanece en el estado &quot;Iniciar lo antes posible&quot;, siempre y cuando el número de flujos de trabajo que se ejecutan esté por encima del límite.

   Para resolver este problema, detenga los flujos de trabajo no deseados y elimine los envíos fallidos. Si se ha alcanzado el umbral, esto permitirá ejecutar nuevos procesos.

   Para comprobar el número de flujos de trabajo que se ejecutan en su instancia, se recomienda utilizar las vistas predefinidas, accesibles de forma predeterminada en la variable **[!UICONTROL Administration]** / **[!UICONTROL Audit]** carpeta. Para obtener más información, consulte [esta página](../../workflow/using/monitoring-workflow-execution.md#filtering-workflows-status).

   >[!IMPORTANT]
   >
   >Al aumentar el **[!UICONTROL NmsOperation_LimitConcurrency]** el umbral de opciones puede provocar problemas de rendimiento en la instancia. En cualquier caso, no lo realice por su cuenta y póngase en contacto con su contacto de Adobe Campaign.

Para obtener más información sobre cómo monitorizar los flujos de trabajo, consulte [esta sección](../../workflow/using/monitoring-workflow-execution.md).

## Inicio en curso {#start-in-progress}

Si los flujos de trabajo no se ejecutan y su estado es **Inicio en curso**, esto podría significar que el módulo de flujo de trabajo no se ha iniciado.

Para comprobar esto e iniciar el módulo si es necesario, aplique los siguientes pasos:

1. Marque la **[!UICONTROL wfserver]** estado del módulo en la variable **[!UICONTROL Monitoring]** pestaña , accesible desde la página principal del Campaign Classic (consulte [Monitorización de procesos](../../production/using/monitoring-processes.md)).

   Un usuario administrador también puede comprobar que la variable **wfserver@`<instance>`** se inicia en el servidor de aplicaciones principal mediante el comando siguiente.

   ```
   nlserver pdump
   HH:MM:SS > Application server for Adobe Campaign Classic (7.X YY.R build XXX@SHA1) of DD/MM/YYYY
   [...]
   wfserver@<instance-name> (9340) - 11.3 Mb
   [...]
   ```

   Para obtener más información sobre cómo monitorizar módulos, consulte [esta sección](../../production/using/usual-commands.md#monitoring-commands-).

1. Si el módulo no se está ejecutando, póngase en contacto con el servicio de atención al cliente de Adobe. Si tiene una instalación local, un administrador debe reiniciarla con el comando siguiente.

   ```
   nlserver start wfserver@<instance-name>
   ```

   >[!NOTE]
   >
   >Sustituya **`<instance-name>`** con el nombre de su instancia (producción, desarrollo, etc.). El nombre de instancia se identifica mediante los archivos de configuración:
   >`[path of application]nl6/conf/config-<instance-name>.xml`

   Para obtener más información sobre cómo reiniciar los módulos, consulte [esta sección](../../production/using/usual-commands.md#module-launch-commands).

## Error en el flujo de trabajo {#failed-workflow}

Si un flujo de trabajo falla, siga los siguientes pasos:

1. Compruebe el diario del flujo de trabajo. Para obtener más información, consulte [Control de la ejecución del flujo de trabajo](../../workflow/using/monitoring-workflow-execution.md) y [Registros de visualización](../../workflow/using/monitoring-workflow-execution.md#displaying-logs) secciones.
1. Monitorización de flujos de trabajo técnicos. Para obtener más información, consulte [esta sección](../../workflow/using/monitoring-technical-workflows.md).
1. Busque errores en las actividades de flujo de trabajo individuales.
