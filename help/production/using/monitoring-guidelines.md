---
title: Directrices de monitorización
description: Descubra las directrices y las prácticas recomendadas para supervisar los procesos e instancias de Campaña.
page-status-flag: never-activated
uuid: cf0d782d-47bf-40ae-ab6f-d1d47fa15792
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: production
content-type: reference
topic-tags: introduction
discoiquuid: 8b33e6af-15c3-4b30-8ad6-d76a1f33be21
translation-type: tm+mt
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: tm+mt
source-wordcount: '712'
ht-degree: 9%

---


# Directrices de monitorización {#monitoring-guidelines}

## Panel de monitorización de instancias {#instance-monitoring-dashboard}

La **[!UICONTROL Monitoring]** ficha, a la que se puede acceder desde la página principal del Campaign Classic, es el principal punto de entrada para ayudarle a supervisar la instancia.

Proporciona un panel de lo que sucede en la instancia: su estado (versión de compilación, paquetes instalados, etc.), indicadores del sistema, registros, flujos de trabajo que se están ejecutando actualmente, estado de los últimos envíos enviados, etc.

Encontrará información detallada [aquí](../../production/using/monitoring-processes.md).

![](assets/monitoring_tab.png)

## Monitoring Campaign Classic processes {#monitoring-campaign-classic-processes}

<table>
<tr><td><img src="assets/do-not-localize/icon_system.svg" width="60px"><p><a href="#monitoring-instance">Monitorear su instancia</a></p></td>
<td><img src="assets/do-not-localize/icon_workflows.svg" width="60px"><p><a href="#moniroting-workflows">Flujos de trabajo de monitor</a></p></td>
<td><img src="assets/do-not-localize/icon_send.svg" width="60px"><p><a href="#monitoring-deliveries">Supervise los envíos</a></p></td>
<td><img src="assets/do-not-localize/icon_database.svg" width="60px"><p><a href="#monitoring-database">Monitorear la base de datos</a></p></td></tr>
</table>

Existen otras formas de supervisar los diferentes procesos de Campaña. Proporcionan varias formas de monitorear las instancias para asegurarse de que el sistema está en buen estado y, finalmente, solucionar los problemas que pueden producirse al configurar flujos de trabajo, enviar envíos, etc.

### Monitoreo de la instancia {#monitoring-instance}

<img src="assets/do-not-localize/icon_system.svg" width="60px">

**Herramientas de supervisión automáticas**

Hay varios métodos automáticos disponibles. para ayudarle a supervisar su instancia. Por ejemplo, puede configurar informes de correo electrónico con anomalías detectadas, recuperar una lista de indicadores en formato XML, etc. [Haga clic aquí](../../production/using/monitoring-processes.md#automatic-monitoring) para obtener más información.

**Pista de auditoría**

La pista de auditoría permite visualizar el historial completo de cambios relacionados con opciones, flujos de trabajo y esquemas dentro de la instancia. [Haga clic aquí](../../production/using/audit-trail.md) para obtener más información.

**Panel de control**

El Panel de control de Campaign le permite administrar varias configuraciones de la instancia: administrar permisos de URL, comprobar los detalles de la instancia como las versiones de compilación de los servidores, etc. También permite supervisar el espacio disponible en los servidores SFTP conectados a la instancia. [Haga clic aquí](https://docs.adobe.com/content/help/es-ES/control-panel/using/control-panel-home.html) para obtener más información.

>[!NOTE]
>
>Tenga en cuenta que el Panel de control de Campaign solo está disponible para los usuarios administradores y para todos los clientes que utilicen los servicios gestionados de Adobe.

### Monitorización de flujos de trabajo {#monitoring-workflows}

<img src="assets/do-not-localize/icon_workflows.svg" width="60px">

**Mapa de calor del flujo de trabajo**

El mapa de calor del flujo de trabajo proporciona una representación visual de todos los flujos de trabajo que se ejecutan en la instancia. Permite monitorear fácilmente la carga en la instancia y planificar flujos de trabajo en consecuencia. [Haga clic aquí](../../workflow/using/heatmap.md) para obtener más información.

**Pista de auditoría**

La pista de auditoría permite visualizar todas las modificaciones realizadas en flujos de trabajo, así como sus estados actuales. [Haga clic aquí](../../production/using/audit-trail.md).

**Solución de problemas de flujos de trabajo**

Se pueden realizar acciones específicas al encontrar problemas con la ejecución de un flujo de trabajo. [Haga clic aquí](../../production/using/workflow-execution.md) para obtener más información

**Monitoreo del estado del flujo de trabajo**

Además del mapa de calor, puede crear un flujo de trabajo que le permitirá supervisar el estado de un conjunto de flujos de trabajo y enviar mensajes recurrentes a los supervisores. [Haga clic aquí](../../workflow/using/supervising-workflows.md) para obtener más información.

**Directrices generales**

Las siguientes directrices y prácticas recomendadas al usar flujos de trabajo pueden ayudar a mejorar el rendimiento. Para obtener más información, consulte estas secciones:
* [Prácticas recomendadas al utilizar flujos de trabajo](../../workflow/using/workflow-best-practices.md)
* [Control de la ejecución del flujo de trabajo](../../workflow/using/monitoring-workflow-execution.md)

### Seguimiento de envíos {#monitoring-deliveries}

<img src="assets/do-not-localize/icon_send.svg" width="60px">

**Informes SMTP**

Los informes SMTP muestran estadísticas de envío y errores SMTP por dominio. [Más información](../../production/using/monitoring-processes.md)

**Prácticas recomendadas**

[Las prácticas recomendadas para enviar y diseñar](../../delivery/using/delivery-best-practices.md) envíos pueden ayudarle a mejorar su rendimiento.

**Solución de problemas** de envío Se pueden realizar acciones específicas al encontrar problemas con envíos:
* [Problemas con entregas](../../production/using/performance-and-throughput-issues.md#deliverability_issues)
* [Problemas de visualización de imágenes](../../production/using/image-display-issues.md)
* [Problemas de rendimiento de envíos](../../delivery/using/monitoring-a-delivery.md#performance_issues)
* [Problemas](../../production/using/temporary-files.md) de archivos temporales: solo modelos de alojamiento *in situ*

### Supervisión de la base de datos {#monitoring-database}

<img src="assets/do-not-localize/icon_database.svg" width="60px">

**Flujo de trabajo para limpieza de bases de datos**

El flujo de trabajo de limpieza de la base de datos le permite eliminar datos obsoletos de la base de datos. Se recomienda evitar el crecimiento exponencial de la base de datos. [Haga clic aquí](../../production/using/database-cleanup-workflow.md) para obtener más información.

**Solución de problemas de rendimiento de la base de datos**

Se pueden realizar acciones específicas al encontrar problemas con el rendimiento de la base de datos. [Haga clic aquí](../../production/using/database-performances.md) para obtener más información.

**Mantenimiento de la base de datos**

*solo modelos de alojamiento in situ e híbridos*

Le recomendamos que realice el mantenimiento regular de la base de datos para evitar un consumo excesivo de espacio en disco, afectando así el acceso a la base de datos. [Haga clic aquí](../../production/using/recommendations.md) para obtener más información.

**Backup y restauración**

*solo modelos de alojamiento in situ e híbridos*

La copia de seguridad es esencial para evitar la pérdida de datos en el evento de un problema (físico o relacionado con el sistema) en una máquina. [Haga clic aquí](../../production/using/backup.md) para obtener más información. El procedimiento de restauración se describe en [esta sección](../../production/using/restoration.md).

## Principios técnicos del Campaign Classic {#campaign-classic-technical-principles}

Los recursos técnicos están disponibles en la documentación del Campaign Classic. Le recomendamos que se familiarice con estos temas antes de realizar cualquier operación técnica en su instancia.

**Modelos y capacidades de alojamiento**

* [Modelos de alojamiento de Campaign Classic](../../installation/using/hosting-models.md)
* [Capacidades del modelo de alojamiento](https://helpx.adobe.com/es/campaign/kb/acc-on-prem-vs-hosted.html)

**Configuración del servidor**

*Modelos de alojamiento in situ e híbridos únicamente*

* [Configuraciones de servidor obligatorias](../../installation/using/campaign-server-configuration.md)
* [Configuración del archivo Serverconf.xml](../../installation/using/the-server-configuration-file.md)
* [Configuración del servidor para la capacidad de entrega](../../installation/using/email-deliverability.md)
* [Líneas de comandos para crear una instancia y declarar una base de datos](../../installation/using/command-lines.md)

**Principios generales**

* [Arquitectura Campaign Classic](../../production/using/general-architecture.md)
* [Módulos Campaign Classic](../../production/using/operating-principle.md)
* [Opciones de Campaign Classic](../../installation/using/configuring-campaign-options.md)
* [Cómo configurar el inicio automático de los módulos](../../production/using/administration.md)
* [Principio de configuración de campaña](../../production/using/configuration-principle.md)
* [Procedimientos de resolución de problemas](../../production/using/performance-and-throughput-issues.md)
