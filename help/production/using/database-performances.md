---
product: campaign
title: Rendimiento de base de datos
description: Rendimiento de base de datos
feature: Monitoring
badge-v7-prem: label="On-premise/híbrido solo" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=es" tooltip="Se aplica solo a implementaciones On-premise e híbridas"
audience: production
content-type: reference
topic-tags: troubleshooting
exl-id: 33dcfd4b-51fd-44f4-98e0-23eafb79d7da
source-git-commit: 14ba450ebff9bba6a36c0df07d715b7279604222
workflow-type: tm+mt
source-wordcount: '488'
ht-degree: 9%

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
>Puede consultar la [Guía de tamaño de hardware de Adobe Campaign](https://helpx.adobe.com/es/campaign/kb/hardware-sizing-guide.html) para obtener información.

## Configuración de plataforma {#platform-configuration}

Una configuración inadecuada puede afectar al rendimiento de la plataforma. Le recomendamos que compruebe la configuración de red, las opciones de envío de la plataforma, así como la configuración de MTA en el archivo **serverConf.xml**.

## Mantenimiento de la base de datos {#database-maintenance}

**Tarea de limpieza de la base de datos**

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

**Administrar tablas de trabajo**

Compruebe el número y tamaño de las tablas de trabajo. Cuando superan un tamaño determinado, el rendimiento de la base de datos se ve afectado. Estas tablas se crean mediante flujos de trabajo y envíos. Permanecen en la base de datos mientras los flujos de trabajo y las entregas están activos. Para limitar el tamaño de las tablas de trabajo, puede realizar las siguientes operaciones:

* Detener o eliminar los envíos con los siguientes estados: **[!UICONTROL Failed]**, **[!UICONTROL In progress]**, **[!UICONTROL Ready for delivery]** o **[!UICONTROL Paused]**.
* Detener o eliminar flujos de trabajo en pausa debido a un error.
* Detener todos los flujos de trabajo utilizados para las pruebas que no contienen una actividad **[!UICONTROL End]** y cuyo estado permanece, por lo tanto, **[!UICONTROL Paused]**.

>[!IMPORTANT]
>
>Si la operación tarda mucho tiempo y libera mucho espacio, es necesario realizar un mantenimiento exhaustivo (reconstrucción de índices, etc.). Para obtener más información, consulte [esta sección](../../production/using/recommendations.md).

**Supervisión de procesos en Adobe Campaign**

Según la configuración de instalación de Adobe Campaign, se pueden utilizar dos herramientas para la monitorización de plataformas:

* La página de producción de la instancia. Para obtener más información, consulte [Supervisión manual](../../production/using/monitoring-processes.md#manual-monitoring).
* El script *netreport*. Para obtener más información, consulte [Supervisión automática mediante scripts de Adobe Campaign](../../production/using/monitoring-processes.md#automatic-monitoring-via-adobe-campaign-scripts).

## Características {#specifics}

Puede ser necesario ejecutar un diagnóstico en tiempo real para identificar la causa del problema. Comience por comprobar los archivos de registro del proceso y la plataforma y, a continuación, monitorice la actividad de la base de datos mientras vuelve a crear el problema. Preste especial atención a lo siguiente:

* El plan de ejecución de mantenimiento
* Consultas SQL en ejecución
* Indica si los procesos externos se están ejecutando al mismo tiempo (limpieza, importaciones, cálculo agregado, etc.).
