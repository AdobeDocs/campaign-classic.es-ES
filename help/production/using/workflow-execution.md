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
source-git-commit: 69b562979f3b32a4d30dfed0695cf3cf6c0fd26a

---


# Ejecución del flujo de trabajo{#workflow-execution}

En la sección siguiente se presenta información sobre problemas comunes relacionados con la ejecución de flujos de trabajo y cómo solucionarlos.

Para obtener más información sobre los flujos de trabajo, consulte estas secciones:

* [Acerca de los flujos de trabajo](../../workflow/using/about-workflows.md)
* [Ejecución de un flujo de trabajo](../../workflow/using/executing-a-workflow.md)
* [Prácticas recomendadas al utilizar flujos de trabajo](../../workflow/using/workflow-best-practices.md)

## Comience lo antes posible en las campañas {#start-as-soon-as-possible-in-campaigns}

En algunos casos, los flujos de trabajo ejecutados desde una campaña no se inician al hacer clic en el **[!UICONTROL Start]** botón. En lugar de comenzar, va al estado &quot;Iniciar lo antes posible&quot;.

Puede haber varias causas para este problema, siga los pasos a continuación para solucionarlo:

1. Compruebe el estado [**[!UICONTROL operationMgt]**](../../workflow/using/campaign.md) del flujo de trabajo técnico. Este flujo de trabajo administra los trabajos o flujos de trabajo dentro de una campaña. Si falla, los flujos de trabajo no se iniciarán ni se detendrán. Reiníciela para reanudar la ejecución de los flujos de trabajo de la campaña.

   Para obtener más información sobre la supervisión de flujos de trabajo técnicos, consulte [esta página](../../workflow/using/monitoring-technical-workflows.md).

   >[NOTA]
   >
   >Una vez reiniciado el flujo de trabajo, asegúrese de ejecutar las tareas pendientes (haga clic con el botón secundario en la **[!UICONTROL Scheduler]** actividad / **[!UICONTROL Execute pending task(s) now]**) para comprobar si se produce un nuevo error en alguna de las actividades.

   Si el flujo de trabajo sigue fallando, compruebe el registro de auditoría en busca de un error específico, solucione los problemas correspondientes y, a continuación, reinicie el flujo de trabajo de nuevo.

1. Compruebe el estado del **[!UICONTROL wfserver]** módulo en la **[!UICONTROL Monitoring]** ficha, a la que se puede acceder desde la página de inicio de Campaign Classic (consulte Procesos [](../../production/using/monitoring-processes.md)de supervisión). Este proceso es responsable de ejecutar todos los flujos de trabajo.

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
   >Replace **`<instancename>`** with the name of your instance (production, development, etc.). El nombre de instancia se identifica mediante los archivos de configuración:
   >`[path of application]nl6/conf/config-<instancename>.xml`

   Para obtener más información sobre cómo reiniciar los módulos, consulte [esta sección](../../production/using/usual-commands.md#module-launch-commands).

1. Compruebe si el **número de procesos de campaña que se ejecutan** en la instancia es mayor que el umbral. Existe un límite definido por la [**[!UICONTROL NmsOperation_LimitConcurrency]**](../../installation/using/configuring-campaign-options.md#campaign-e-workflow-management) opción en cuanto a cuántos procesos de campaña se pueden ejecutar en paralelo en la instancia. Cuando se alcanza este límite, el flujo de trabajo permanece en el estado &quot;Iniciar lo antes posible&quot; siempre que el número de flujos de trabajo que se ejecutan esté por encima del límite.

   Para solucionar este problema, detenga los flujos de trabajo no deseados y elimine los envíos fallidos. Si se alcanza el umbral, esto permitirá la ejecución de nuevos procesos.

   Para comprobar el número de flujos de trabajo que se ejecutan en su instancia, le recomendamos que utilice las vistas predefinidas, a las que se puede acceder de forma predeterminada en la carpeta **[!UICONTROL Administration]** / **[!UICONTROL Audit]** . Para obtener más información, consulte [esta página](../../workflow/using/monitoring-workflow-execution.md#filtering-workflows-status).

   >[PRECAUCIÓN]
   >
   >Aumentar el umbral de la **[!UICONTROL NmsOperation_LimitConcurrency]** opción puede provocar problemas de rendimiento en la instancia. En cualquier caso, no realice esto por su cuenta y póngase en contacto con su contacto de Adobe Campaign.

Para obtener más información sobre cómo supervisar los flujos de trabajo, consulte [esta sección](../../workflow/using/monitoring-workflow-execution.md).

## Comienza en curso {#start-in-progress}

Si los flujos de trabajo no se están ejecutando y su estado es **Inicio en curso**, esto puede significar que el módulo de flujo de trabajo no se ha iniciado.

Para comprobar esto e iniciar el módulo si es necesario, aplique los siguientes pasos:

1. Compruebe el estado del **[!UICONTROL wfserver]** módulo en la **[!UICONTROL Monitoring]** ficha, a la que se puede acceder desde la página de inicio de Campaign Classic (consulte Procesos [](../../production/using/monitoring-processes.md)de supervisión).

   Un usuario administrador también puede comprobar que el módulo **wfserver@`<instance>`**se inicia en el servidor de aplicaciones principal mediante el comando siguiente.

   ```
   nlserver pdump
   HH:MM:SS > Application server for Adobe Campaign Classic (7.X YY.R build XXX@SHA1) of DD/MM/YYYY
   [...]
   wfserver@<INSTANCENAME> (9340) - 11.3 Mb
   [...]
   ```

   Para obtener más información sobre cómo supervisar los módulos, consulte [esta sección](../../production/using/usual-commands.md#monitoring-commands-).

1. Si el módulo no se está ejecutando, póngase en contacto con el Servicio de atención al cliente de Adobe. Si tiene una instalación local, un administrador debe reiniciarla mediante el comando siguiente.

   ```
   nlserver start wfserver@<INSTANCENAME>
   ```

   >[!NOTE]
   >
   >Replace **`<instancename>`** with the name of your instance (production, development, etc.). El nombre de instancia se identifica mediante los archivos de configuración:
   >`[path of application]nl6/conf/config-<instancename>.xml`

   Para obtener más información sobre cómo reiniciar los módulos, consulte [esta sección](../../production/using/usual-commands.md#module-launch-commands).

## Error en el flujo de trabajo {#failed-workflow}

Si se produce un error en un flujo de trabajo, realice los siguientes pasos:

1. Compruebe el diario de flujo de trabajo. Para obtener más información sobre esto, consulte las secciones Ejecución [del flujo de trabajo de](../../workflow/using/monitoring-workflow-execution.md) supervisión y Registros [de](../../workflow/using/monitoring-workflow-execution.md#displaying-logs) visualización.
1. Monitorear los flujos de trabajo técnicos. For more on this refer to the [this section](../../workflow/using/monitoring-technical-workflows.md).
1. Busque errores en las actividades de flujo de trabajo individuales.
