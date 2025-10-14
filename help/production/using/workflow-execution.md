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
source-git-commit: ad6f3f2cf242d28de9e6da5cec100e096c5cbec2
workflow-type: tm+mt
source-wordcount: '652'
ht-degree: 12%

---

# Ejecución del flujo de trabajo{#workflow-execution}



La sección siguiente presenta información sobre problemas comunes relacionados con la ejecución de flujos de trabajo y cómo solucionarlos.

Para obtener más información sobre los flujos de trabajo, consulte estas secciones:

* [Acerca de los flujos de trabajo](../../workflow/using/about-workflows.md)
* [Iniciando un flujo de trabajo](https://experienceleague.adobe.com/docs/campaign/automation/workflows/executing-a-workflow/start-a-workflow.html?lang=es){target="_blank"}.
* [Ciclo de vida del flujo de trabajo](https://experienceleague.adobe.com/docs/campaign/automation/workflows/introduction/about-workflows.html?lang=es){target="_blank"}.
* [Prácticas recomendadas al utilizar flujos de trabajo](https://experienceleague.adobe.com/docs/campaign/automation/workflows/introduction/workflow-best-practices.html?lang=es){target="_blank"}.

## Iniciar lo antes posible en las campañas {#start-as-soon-as-possible-in-campaigns}

En algunos casos, los flujos de trabajo ejecutados desde una campaña no se inician al hacer clic en el botón **[!UICONTROL Start]**. En lugar de comenzar, pasa al estado &quot;Iniciar lo antes posible&quot;.

Puede haber varias causas para este problema. Siga los pasos a continuación para resolverlo:

1. Comprobar el estado del flujo de trabajo técnico [**[!UICONTROL operationMgt]**](https://experienceleague.adobe.com/docs/campaign/automation/workflows/introduction/wf-type/technical-workflows.html?lang=es){target="_blank"}. Este flujo de trabajo administra los trabajos o flujos de trabajo dentro de una campaña. Si falla, el resultado será que los flujos de trabajo no se inicien ni se detengan. Reinícielo para reanudar la ejecución de los flujos de trabajo de campaña.

   Para obtener más información sobre la monitorización de flujos de trabajo técnicos, consulte la [Documentación de Campaign v8](https://experienceleague.adobe.com/docs/campaign/automation/workflows/monitoring-workflows/monitor-technical-workflows.html?lang=es){target="_blank"}.

   >[!NOTE]
   >
   >Una vez reiniciado el flujo de trabajo, asegúrese de ejecutar las tareas pendientes (haga clic con el botón derecho en la actividad **[!UICONTROL Scheduler]** / **[!UICONTROL Execute pending task(s) now]**) para comprobar si vuelve a fallar en cualquiera de las actividades.

   Si el flujo de trabajo sigue fallando, compruebe el registro de auditoría para ver si hay algún error específico, solucione los problemas correspondientes y reinicie el flujo de trabajo de nuevo.

1. Compruebe el estado del módulo **[!UICONTROL wfserver]** en la ficha **[!UICONTROL Monitoring]**, a la que se puede acceder desde la página principal de Campaign Classic (consulte [Monitorización de procesos](../../production/using/monitoring-processes.md)). Este proceso es responsable de ejecutar todos los flujos de trabajo.

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

   Para comprobar el número de flujos de trabajo que se están ejecutando en su instancia, se recomienda utilizar las vistas predefinidas, a las que se puede acceder de forma predeterminada en la carpeta **[!UICONTROL Administration]** / **[!UICONTROL Audit]**. Para obtener más información, consulte la [Documentación de Campaign v8](https://experienceleague.adobe.com/docs/campaign/automation/workflows/monitoring-workflows/monitor-workflow-execution.html?lang=es){target="_blank"}.

   >[!IMPORTANT]
   >
   >Si se aumenta el umbral de opción **[!UICONTROL NmsOperation_LimitConcurrency]** se pueden producir problemas de rendimiento en la instancia. En cualquier caso, no lo haga por su cuenta y póngase en contacto con su contacto de Adobe Campaign.

Para obtener más información sobre cómo monitorizar sus flujos de trabajo, consulte la [documentación de Campaign v8](https://experienceleague.adobe.com/docs/campaign/automation/workflows/monitoring-workflows/monitor-workflow-execution.html?lang=es){target="_blank"}.

## Inicio en curso {#start-in-progress}

Si los flujos de trabajo no se están ejecutando y su estado es **Iniciar en curso**, puede que el módulo de flujo de trabajo no se inicie.

Para comprobar esto e iniciar el módulo si es necesario, aplique los siguientes pasos:

1. Compruebe el estado del módulo **[!UICONTROL wfserver]** en la ficha **[!UICONTROL Monitoring]**, a la que se puede acceder desde la página principal de Campaign Classic (consulte [Monitorización de procesos](../../production/using/monitoring-processes.md)).

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

1. Compruebe el historial de flujo de trabajo. Para obtener más información, consulte la [Documentación de Campaign v8](https://experienceleague.adobe.com/docs/campaign/automation/workflows/monitoring-workflows/monitor-workflow-execution.html?lang=es){target="_blank"}.
1. Monitorización de flujos de trabajo técnicos. Consulte la [documentación de Campaign v8](https://experienceleague.adobe.com/docs/campaign/automation/workflows/monitoring-workflows/monitor-technical-workflows.html?lang=es){target="_blank"}.
1. Busque errores en las actividades de flujo de trabajo individuales.
