---
solution: Campaign Classic
product: campaign
title: Rendimientos de la base de datos
description: Rendimientos de la base de datos
audience: production
content-type: reference
topic-tags: troubleshooting
translation-type: tm+mt
source-git-commit: 50f95d7156e7104d90fa7a31eea30711b9c11bbf
workflow-type: tm+mt
source-wordcount: '481'
ht-degree: 8%

---


# Rendimiento de la base de datos{#database-performances}

La mayoría de los problemas de rendimiento están vinculados al mantenimiento de la base de datos. Estos son cuatro leads principales que le ayudarán a encontrar la causa del rendimiento lento:

* Configuración
* Instalación y configuración de la plataforma Adobe Campaign
* Mantenimiento de la base de datos
* Diagnóstico en tiempo real

## Configuración {#configuration}

Compruebe que la configuración inicial de la plataforma Adobe Campaign sigue siendo válida y, si es necesario, vuelva a evaluar las necesidades de los clientes en cuanto a la capacidad de entrega o al tamaño de la base de datos. También recomendamos ejecutar una comprobación completa de hardware (CPU, RAM, sistema de E/S).

>[!NOTE]
>
>Puede consultar [Guía de tamaño de hardware de Adobe Campaign](https://helpx.adobe.com/es/campaign/kb/hardware-sizing-guide.html) para obtener más información.

## Configuración de plataforma {#platform-configuration}

Una configuración inadecuada puede afectar al rendimiento de la plataforma. Le recomendamos que compruebe la configuración de red, las opciones de entrega de plataforma y la configuración de MTA en el archivo **serverConf.xml**.

## Mantenimiento de la base de datos {#database-maintenance}

**Tarea de limpieza de base de datos**

Asegúrese de que la tarea de limpieza de la base de datos esté operativa. Para ello, vista los archivos de registro para ver si contienen algún error. Para obtener más información, consulte [esta sección](../../production/using/database-cleanup-workflow.md).

**Planes de mantenimiento**

Asegúrese de que el mantenimiento de la base de datos se programe y ejecute correctamente. Para ello, póngase en contacto con el administrador de la base de datos para obtener más información sobre:

* su calendario de mantenimiento,
* planes de mantenimiento ejecutados anteriormente,
* vista de los registros de secuencias de comandos.

Para obtener más información, consulte [esta sección](../../production/using/recommendations.md).

>[!IMPORTANT]
>
>Si utiliza una configuración intermediaria, es esencial que las bases de datos se mantengan de forma regular. Al analizar un envío en la plataforma de marketing, la instancia de marketing envía información a la instancia de intermediaria. Si el proceso se ralentiza, la instancia de marketing se verá afectada.

**Administración de tablas de trabajo**

Verifique el número y el tamaño de las tablas de trabajo. Cuando superan un tamaño determinado, el rendimiento de la base de datos se ve afectado. Estas tablas se crean mediante flujos de trabajo y envíos. Permanecen en la base de datos mientras los flujos de trabajo y envíos están activos. Para limitar el tamaño de las tablas de trabajo, puede realizar las siguientes operaciones:

* detenga o elimine envíos con los siguientes estados: **[!UICONTROL Failed]** , **[!UICONTROL In progress]** , **[!UICONTROL Ready for delivery]** o **[!UICONTROL Paused]** .
* detener o eliminar flujos de trabajo en pausa debido a un error,
* detenga todos los flujos de trabajo utilizados para pruebas que no contengan una actividad **[!UICONTROL End]** y cuyo estado permanezca por tanto **[!UICONTROL Paused]**.

>[!IMPORTANT]
>
>Si la operación tarda mucho tiempo y libera mucho espacio, significa que es necesario realizar un mantenimiento profundo (reconstrucción de índices, etc.). Para obtener más información, consulte [esta sección](../../production/using/recommendations.md).

**Supervisión de procesos de Adobe Campaign**

Según la configuración de la instalación de Adobe Campaign, se pueden utilizar dos herramientas para la supervisión de plataformas:

* la página de producción de la instancia. Para obtener más información sobre esto, consulte [Monitoreo manual](../../production/using/monitoring-processes.md#manual-monitoring).
* la secuencia de comandos netreport. Para obtener más información sobre esto, consulte [Monitoreo automático mediante scripts de Adobe Campaign](../../production/using/monitoring-processes.md#automatic-monitoring-via-adobe-campaign-scripts).

## Especifica {#specifics}

Puede que sea necesario realizar un diagnóstico en tiempo real para identificar la causa del problema. Inicio comprobando el proceso y los archivos de registro de la plataforma, luego monitoree la actividad de la base de datos mientras vuelve a crear el problema. Preste especial atención a lo siguiente:

* el plan de ejecución del mantenimiento,
* CONSULTAS SQL que se están ejecutando,
* si los procesos externos se ejecutan o no al mismo tiempo (limpieza, importaciones, cálculo acumulado, etc.).

