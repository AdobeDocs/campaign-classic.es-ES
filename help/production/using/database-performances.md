---
product: campaign
title: Rendimientos de la base de datos
description: Rendimientos de la base de datos
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
badge-v7-prem: label="on-premise & hybrid" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=en" tooltip="Applies to on-premise and hybrid deployments only"
audience: production
content-type: reference
topic-tags: troubleshooting
exl-id: 33dcfd4b-51fd-44f4-98e0-23eafb79d7da
source-git-commit: a5762cd21a1a6d5a5f3a10f53a5d1f43542d99d4
workflow-type: tm+mt
source-wordcount: '481'
ht-degree: 8%

---

# Rendimiento de la base de datos{#database-performances}



La mayoría de los problemas de rendimiento están vinculados al mantenimiento de la base de datos. Estos son cuatro posibles clientes principales que le ayudarán a encontrar la causa del rendimiento lento:

* Configuración
* Instalación y configuración de la plataforma Adobe Campaign
* Mantenimiento de la base de datos
* Diagnóstico en tiempo real

## Configuración {#configuration}

Compruebe que la configuración inicial de la plataforma de Adobe Campaign siga siendo válida y, si es necesario, vuelva a evaluar las necesidades del cliente en términos de capacidad de envío o tamaño de la base de datos. También recomendamos ejecutar una comprobación de hardware completa (CPU, RAM, sistema IO).

>[!NOTE]
>
>Puede consultar [Guía de tamaño de hardware de Adobe Campaign](https://helpx.adobe.com/es/campaign/kb/hardware-sizing-guide.html) para obtener información.

## Configuración de plataforma {#platform-configuration}

La configuración inadecuada puede afectar al rendimiento de la plataforma. Le recomendamos que compruebe la configuración de red, las opciones de capacidad de envío de la plataforma y la configuración de MTA en la **serverConf.xml** archivo.

## Mantenimiento de la base de datos {#database-maintenance}

**Tarea de limpieza de base de datos**

Asegúrese de que la tarea de limpieza de la base de datos esté operativa. Para ello, consulte los archivos de registro para ver si contienen algún error. Para obtener más información, consulte [esta sección](../../production/using/database-cleanup-workflow.md).

**Planes de mantenimiento**

Asegúrese de que el mantenimiento de la base de datos esté correctamente programado y se ejecute. Para ello, póngase en contacto con el administrador de la base de datos para obtener más información sobre:

* Su calendario de mantenimiento
* Planes de mantenimiento ejecutados anteriormente
* Visualización de los registros de secuencias de comandos

Para obtener más información, consulte [esta sección](../../production/using/recommendations.md).

>[!IMPORTANT]
>
>Si utiliza una configuración intermediaria, es esencial que las bases de datos se mantengan de forma regular. Al analizar una entrega en la plataforma de marketing, la instancia de marketing envía información a la instancia de intermediario. Si el proceso se ralentiza, la instancia de marketing se verá afectada.

**Administración de tablas de trabajo**

Compruebe el número y el tamaño de las tablas de trabajo. Cuando superan un tamaño determinado, el rendimiento de la base de datos se ve afectado. Estas tablas se crean mediante flujos de trabajo y envíos. Permanecen en la base de datos mientras los flujos de trabajo y los envíos están activos. Para limitar el tamaño de las tablas de trabajo, puede realizar las siguientes operaciones:

* Detenga o elimine entregas con los siguientes estados: **[!UICONTROL Failed]**, **[!UICONTROL In progress]**, **[!UICONTROL Ready for delivery]** o **[!UICONTROL Paused]**.
* Detenga o elimine flujos de trabajo que estén en pausa debido a un error.
* Detenga todos los flujos de trabajo utilizados para pruebas que no contienen un **[!UICONTROL End]** actividad y cuyo estado, por lo tanto, permanece **[!UICONTROL Paused]**.

>[!IMPORTANT]
>
>Si la operación tarda mucho tiempo y libera mucho espacio, significa que es necesario realizar un mantenimiento en profundidad (reconstrucción de índices, etc.). Para obtener más información, consulte [esta sección](../../production/using/recommendations.md).

**Supervisión del proceso de Adobe Campaign**

Según la configuración de instalación de Adobe Campaign, se pueden utilizar dos herramientas para la supervisión de la plataforma:

* La página de producción de la instancia. Para obtener más información, consulte [Monitorización manual](../../production/using/monitoring-processes.md#manual-monitoring).
* La variable *netreport* secuencia de comandos. Para obtener más información, consulte [Monitorización automática mediante scripts de Adobe Campaign](../../production/using/monitoring-processes.md#automatic-monitoring-via-adobe-campaign-scripts).

## Especificaciones {#specifics}

Puede ser necesario ejecutar un diagnóstico en tiempo real para identificar la causa del problema. Comience comprobando los archivos de registro de proceso y plataforma y, a continuación, supervise la actividad de la base de datos mientras vuelve a crear el problema. Preste especial atención a lo siguiente:

* El plan de ejecución de mantenimiento
* Consultas SQL en ejecución
* Indica si los procesos externos se ejecutan al mismo tiempo (limpieza, importaciones, cálculo de agregados, etc.).
