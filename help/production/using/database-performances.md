---
product: campaign
title: Rendimientos de la base de datos
description: Rendimientos de la base de datos
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
badge-v7-prem: label="on-premise & hybrid" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html" tooltip="Applies to on-premise and hybrid deployments only"
audience: production
content-type: reference
topic-tags: troubleshooting
exl-id: 33dcfd4b-51fd-44f4-98e0-23eafb79d7da
source-git-commit: 4661688a22bd1a82eaf9c72a739b5a5ecee168b1
workflow-type: tm+mt
source-wordcount: '481'
ht-degree: 8%

---

# Rendimiento de la base de datos{#database-performances}



La mayoría de los problemas de rendimiento están vinculados al mantenimiento de la base de datos. Estos son cuatro posibles clientes principales que le ayudarán a encontrar la causa del rendimiento lento:

* Configuración
* Instalación y configuración de la plataforma de Adobe Campaign
* Mantenimiento de la base de datos
* Diagnóstico en tiempo real

## Configuración {#configuration}

Compruebe que la configuración inicial de la plataforma de Adobe Campaign sigue siendo válida y, si es necesario, vuelva a evaluar las necesidades del cliente en términos de capacidad de envío o tamaño de la base de datos. También recomendamos realizar una comprobación completa del hardware (CPU, RAM, sistema de E/S).

>[!NOTE]
>
>Puede hacer referencia a [Guía de tamaño de hardware de Adobe Campaign](https://helpx.adobe.com/es/campaign/kb/hardware-sizing-guide.html) para obtener información.

## Configuración de plataforma {#platform-configuration}

Una configuración inadecuada puede afectar al rendimiento de la plataforma. Le recomendamos que compruebe la configuración de red, las opciones de envío de la plataforma, así como la configuración de MTA en la **serverConf.xml** archivo.

## Mantenimiento de la base de datos {#database-maintenance}

**Tarea de limpieza de base de datos**

Asegúrese de que la tarea de limpieza de la base de datos esté operativa. Para ello, vea los archivos de registro para ver si contienen algún error. Para obtener más información, consulte [esta sección](../../production/using/database-cleanup-workflow.md).

**Planes de mantenimiento**

Asegúrese de que el mantenimiento de la base de datos esté correctamente programado y ejecutado. Para ello, póngase en contacto con el administrador de la base de datos para obtener más información sobre lo siguiente:

* Su horario de mantenimiento
* Planes de mantenimiento ejecutados anteriormente
* Visualización de los registros de script

Para obtener más información, consulte [esta sección](../../production/using/recommendations.md).

>[!IMPORTANT]
>
>Si utiliza una configuración intermediaria, es esencial que las bases de datos se mantengan de forma regular. Al analizar un envío en la plataforma de marketing, la instancia de marketing envía información a la instancia de intermediario. Si el proceso se ralentiza, la instancia de marketing se verá afectada.

**Administración de tablas de trabajo**

Compruebe el número y tamaño de las tablas de trabajo. Cuando superan un tamaño determinado, el rendimiento de la base de datos se ve afectado. Estas tablas se crean mediante flujos de trabajo y envíos. Permanecen en la base de datos mientras los flujos de trabajo y las entregas están activos. Para limitar el tamaño de las tablas de trabajo, puede realizar las siguientes operaciones:

* Detenga o elimine los envíos con los siguientes estados: **[!UICONTROL Failed]**, **[!UICONTROL In progress]**, **[!UICONTROL Ready for delivery]**, o **[!UICONTROL Paused]**.
* Detener o eliminar flujos de trabajo en pausa debido a un error.
* Detener todos los flujos de trabajo utilizados para pruebas que no contienen un **[!UICONTROL End]** actividad y cuyo estado sigue siendo, por lo tanto, **[!UICONTROL Paused]**.

>[!IMPORTANT]
>
>Si la operación tarda mucho tiempo y libera mucho espacio, es necesario realizar un mantenimiento exhaustivo (reconstrucción de índices, etc.). Para obtener más información, consulte [esta sección](../../production/using/recommendations.md).

**Monitorización de procesos de Adobe Campaign**

Según la configuración de instalación de Adobe Campaign, se pueden utilizar dos herramientas para la monitorización de plataformas:

* La página de producción de la instancia. Para obtener más información, consulte [Monitorización manual](../../production/using/monitoring-processes.md#manual-monitoring).
* El *netreport* script. Para obtener más información, consulte [Supervisión automática mediante scripts de Adobe Campaign](../../production/using/monitoring-processes.md#automatic-monitoring-via-adobe-campaign-scripts).

## Características {#specifics}

Puede ser necesario ejecutar un diagnóstico en tiempo real para identificar la causa del problema. Comience por comprobar los archivos de registro del proceso y la plataforma y, a continuación, monitorice la actividad de la base de datos mientras vuelve a crear el problema. Preste especial atención a lo siguiente:

* El plan de ejecución de mantenimiento
* Consultas SQL en ejecución
* Indica si los procesos externos se están ejecutando al mismo tiempo (limpieza, importaciones, cálculo agregado, etc.).
