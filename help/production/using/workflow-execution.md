---
title: Ejecución del flujo de trabajo
seo-title: Ejecución del flujo de trabajo
description: Ejecución del flujo de trabajo
seo-description: null
page-status-flag: never-activated
uuid: 115256f6-bdf2-4594-885c-e90d02a25b80
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: production
content-type: reference
topic-tags: troubleshooting
discoiquuid: 7d8828c5-5776-49ca-b4f7-a4a6aaaa9db1
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: b369a17fabc55607fc6751e7909e1a1cb3cd4201
workflow-type: tm+mt
source-wordcount: '637'
ht-degree: 13%

---


# Ejecución del flujo de trabajo{#workflow-execution}

La sección siguiente presenta información sobre problemas comunes relacionados con la ejecución de flujos de trabajo y cómo solucionarlos.

Para obtener más información sobre flujos de trabajo, consulte estas secciones:

* [Acerca de los flujos de trabajo](../../workflow/using/about-workflows.md)
* [Inicio de un flujo de trabajo](../../workflow/using/starting-a-workflow.md)
* [Ciclo de vida del flujo de trabajo](../../workflow/using/workflow-life-cycle.md)
* [Prácticas recomendadas al utilizar flujos de trabajo](../../workflow/using/workflow-best-practices.md)

## Inicio lo antes posible en campañas {#start-as-soon-as-possible-in-campaigns}

En algunos casos, los flujos de trabajo ejecutados desde una campaña no tienen inicios al hacer clic en el **[!UICONTROL Start]** botón. En lugar de comenzar, va a un estado de &quot;Inicio tan pronto como sea posible&quot;.

Puede haber varias causas para este problema, siga los pasos a continuación para solucionarlo:

1. Compruebe el estado [**[!UICONTROL operationMgt]**](../../workflow/using/campaign.md) del flujo de trabajo técnico. Este flujo de trabajo administra trabajos o flujos de trabajo dentro de una campaña. Si falla, esto resultará en flujos de trabajo de no inicio o parada. Reinícielo para reanudar la ejecución de flujos de trabajo de la campaña.

   Para obtener más información sobre la supervisión de flujos de trabajo técnicos, consulte [esta página](../../workflow/using/monitoring-technical-workflows.md).

   >[NOTA]
   >
   >Una vez reiniciado el flujo de trabajo, asegúrese de ejecutar las tareas pendientes (haga clic con el botón secundario en la **[!UICONTROL Scheduler]** actividad / **[!UICONTROL Execute pending task(s) now]**) para comprobar si se produce un nuevo error en cualquiera de las actividades.

   Si el flujo de trabajo sigue fallando, compruebe el registro de auditoría en busca de un error específico, solucione los problemas correspondientes y, a continuación, reinicie el flujo de trabajo de nuevo.

1. Compruebe el estado del **[!UICONTROL wfserver]** módulo en la **[!UICONTROL Monitoring]** ficha, accesible desde la página principal del Campaign Classic (consulte [Monitoreo de procesos](../../production/using/monitoring-processes.md)). Este proceso es responsable de ejecutar todos los flujos de trabajo.

   Un usuario administrador también puede comprobar que el módulo **wfserver@`<instance>`**se inicia en el servidor de aplicaciones principal mediante el comando siguiente.

   ```
   nlserver pdump
   HH:MM:SS > Application server for Adobe Campaign Version X.Y (build XXXX) of DD/MM/YYYY
   [...]
   wfserver@<INSTANCENAME> (9340) - 11.3 Mb
   [...]
   ```

   Si el módulo no se está ejecutando, póngase en contacto con el Servicio de atención al cliente de Adobe. Si tiene una instalación local, un usuario administrador debe reiniciar el servicio mediante el comando siguiente.

   ```
   nlserver start wfserver@<INSTANCENAME>
   ```

   >[!NOTE]
   >
   >Sustituya **`<instancename>`** con el nombre de su instancia (producción, desarrollo, etc.). El nombre de instancia se identifica mediante los archivos de configuración:
   >`[path of application]nl6/conf/config-<instancename>.xml`

   For more on how to restart modules, refer to [this section](../../production/using/usual-commands.md#module-launch-commands).

1. Compruebe si el **número de procesos de campaña que se ejecutan** en la instancia es superior al umbral. Existe un límite definido por la [**[!UICONTROL NmsOperation_LimitConcurrency]**](../../installation/using/configuring-campaign-options.md#campaign-e-workflow-management) opción en cuanto a cuántos procesos de campaña se pueden ejecutar en paralelo en la instancia. Cuando se alcanza este límite, el flujo de trabajo permanece en el estado &quot;Inicio lo antes posible&quot; siempre que el número de flujos de trabajo que se ejecutan esté por encima del límite.

   Para solucionar este problema, detenga los flujos de trabajo no deseados y elimine los envíos fallidos. Si se alcanza el umbral, esto permitirá la ejecución de nuevos procesos.

   Para comprobar el número de flujos de trabajo que se están ejecutando en su instancia, le recomendamos que utilice las vistas predefinidas, a las que se puede acceder de forma predeterminada en la carpeta **[!UICONTROL Administration]** / **[!UICONTROL Audit]** . Para obtener más información, consulte [esta página](../../workflow/using/monitoring-workflow-execution.md#filtering-workflows-status).

   >[PRECAUCIÓN]
   >
   >Aumentar el umbral de la **[!UICONTROL NmsOperation_LimitConcurrency]** opción puede provocar problemas de rendimiento en la instancia. En cualquier caso, no lo haga por su cuenta y póngase en contacto con su Adobe Campaign.

Para obtener más información sobre cómo monitorizar los flujos de trabajo, consulte [esta sección](../../workflow/using/monitoring-workflow-execution.md).

## Inicio en curso {#start-in-progress}

Si los flujos de trabajo no se están ejecutando y su estado es **Inicio en curso**, esto puede significar que el módulo de flujo de trabajo no se ha iniciado.

Para comprobar esto e iniciar el módulo si es necesario, aplique los siguientes pasos:

1. Compruebe el estado del **[!UICONTROL wfserver]** módulo en la **[!UICONTROL Monitoring]** ficha, accesible desde la página principal del Campaign Classic (consulte [Monitoreo de procesos](../../production/using/monitoring-processes.md)).

   Un usuario administrador también puede comprobar que el módulo **wfserver@`<instance>`**se inicia en el servidor de aplicaciones principal mediante el comando siguiente.

   ```
   nlserver pdump
   HH:MM:SS > Application server for Adobe Campaign Classic (7.X YY.R build XXX@SHA1) of DD/MM/YYYY
   [...]
   wfserver@<INSTANCENAME> (9340) - 11.3 Mb
   [...]
   ```

   For more on how to monitor modules, refer to [this section](../../production/using/usual-commands.md#monitoring-commands-).

1. Si el módulo no se está ejecutando, póngase en contacto con el Servicio de atención al cliente de Adobe. Si tiene una instalación local, un administrador debe reiniciarla mediante el comando siguiente.

   ```
   nlserver start wfserver@<INSTANCENAME>
   ```

   >[!NOTE]
   >
   >Sustituya **`<instancename>`** con el nombre de su instancia (producción, desarrollo, etc.). El nombre de instancia se identifica mediante los archivos de configuración:
   >`[path of application]nl6/conf/config-<instancename>.xml`

   For more on how to restart modules, refer to [this section](../../production/using/usual-commands.md#module-launch-commands).

## Error en el flujo de trabajo {#failed-workflow}

Si se produce un error en un flujo de trabajo, realice los siguientes pasos:

1. Compruebe el historial del flujo de trabajo. Para obtener más información sobre esto, consulte las secciones Ejecución [del flujo de trabajo de](../../workflow/using/monitoring-workflow-execution.md) supervisión y Registros [de](../../workflow/using/monitoring-workflow-execution.md#displaying-logs) visualización.
1. Monitorear flujos de trabajo técnicos. For more on this refer to the [this section](../../workflow/using/monitoring-technical-workflows.md).
1. Busque errores en las actividades de flujo de trabajo individuales.
