---
solution: Campaign Classic
product: campaign
title: Directrices de monitorización
description: Descubra las directrices y las prácticas recomendadas para supervisar los procesos e instancias de Campaign.
audience: production
content-type: reference
topic-tags: introduction
translation-type: tm+mt
source-git-commit: 564eaedb09282c85593f638617baded0a63494a0
workflow-type: tm+mt
source-wordcount: '771'
ht-degree: 9%

---


# Directrices de monitorización {#monitoring-guidelines}

## Panel de monitorización de instancias {#instance-monitoring-dashboard}

La pestaña **[!UICONTROL Monitoring]**, a la que se puede acceder desde la página de inicio del Campaign Classic, es el principal punto de entrada para ayudarle a supervisar la instancia.

Proporciona un tablero de lo que está sucediendo en la instancia: su estado (versión de compilación, paquetes instalados, etc.), indicadores del sistema, registros, flujos de trabajo que se están ejecutando actualmente, estado de los últimos envíos enviados, etc.

Encontrará información detallada [aquí](../../production/using/monitoring-processes.md).

![](assets/monitoring_tab.png)

## Monitorización de procesos del Campaign Classic {#monitoring-campaign-classic-processes}

<table>
<tr><td><img src="assets/do-not-localize/icon_system.svg" width="60px"><p><a href="#monitoring-instance">Supervisión de la instancia</a></p></td>
<td><img src="assets/do-not-localize/icon_workflows.svg" width="60px"><p><a href="#moniroting-workflows">Monitorización de flujos de trabajo</a></p></td>
<td><img src="assets/do-not-localize/icon_send.svg" width="60px"><p><a href="#monitoring-deliveries">Supervise los envíos</a></p></td>
<td><img src="assets/do-not-localize/icon_database.svg" width="60px"><p><a href="#monitoring-database">Supervisión de la base de datos</a></p></td></tr>
</table>

Hay maneras adicionales de monitorizar los diferentes procesos de Campaign disponibles. Proporcionan varias formas de monitorizar las instancias para asegurarse de que el sistema está en buen estado y, finalmente, solucionar problemas que pueden producirse al configurar flujos de trabajo, enviar envíos, etc.

### Monitorización de la instancia {#monitoring-instance}

<img src="assets/do-not-localize/icon_system.svg" width="60px">

**Herramientas de monitorización automáticas**

Hay varios métodos automáticos disponibles. para ayudarle a supervisar su instancia. Por ejemplo, puede configurar informes de correo electrónico con anomalías detectadas, recuperar una lista de indicadores en formato XML, etc. [Haga clic aquí](../../production/using/monitoring-processes.md#automatic-monitoring) para obtener más información.

**Pista de auditoría**

La pista de auditoría permite visualizar el historial completo de cambios relacionados con las opciones, flujos de trabajo y esquemas dentro de la instancia. [Haga clic ](../../production/using/audit-trail.md) aquí para obtener más información.

**Panel de control de Campaign**

El Panel de control de Campaign le permite administrar varias configuraciones de su instancia: administre permisos de URL, compruebe los detalles de su instancia como las versiones de compilación de sus servidores, etc. También le permite supervisar el espacio disponible en los servidores SFTP conectados a su instancia. [Haga clic ](https://docs.adobe.com/content/help/es-ES/control-panel/using/control-panel-home.html) aquí para obtener más información.

>[!NOTE]
>
>Todos los usuarios administradores pueden acceder a Panel de control de Campaign. Los pasos para otorgar acceso de administrador a un usuario se detallan en [esta página](https://experienceleague.adobe.com/docs/control-panel/using/discover-control-panel/managing-permissions.html?lang=en#discover-control-panel).
>
>Tenga en cuenta que la instancia debe alojarse en AWS y actualizarse con la última versión de [Gold Standard](../../rn/using/gs-overview.md) o la [última versión de GA (21.1)](../../rn/using/latest-release.md). Aprenda a comprobar su versión en [esta sección](../../platform/using/launching-adobe-campaign.md#getting-your-campaign-version). Para comprobar si la instancia está alojada en AWS, siga los pasos detallados en [esta página](https://experienceleague.adobe.com/docs/control-panel/using/faq.html).

### Monitorización de flujos de trabajo {#monitoring-workflows}

<img src="assets/do-not-localize/icon_workflows.svg" width="60px">

**Mapa de calor del flujo de trabajo**

El mapa de calor del flujo de trabajo proporciona una representación visual de todos los flujos de trabajo que se ejecutan en la instancia. Permite monitorizar fácilmente la carga en la instancia y planificar los flujos de trabajo en consecuencia. [Haga clic ](../../workflow/using/heatmap.md) aquí para obtener más información.

**Pista de auditoría**

La pista de auditoría permite visualizar todas las modificaciones realizadas en los flujos de trabajo, así como sus estados actuales. [Haga clic aquí](../../production/using/audit-trail.md).

**Solución de problemas de flujos de trabajo**

Se pueden realizar acciones específicas al encontrar problemas con una ejecución de flujo de trabajo. [Haga clic aquí](../../production/using/workflow-execution.md) para obtener más información

**Monitorización del estado del flujo de trabajo**

Además del mapa de calor, puede crear un flujo de trabajo que le permita supervisar el estado de un conjunto de flujos de trabajo y enviar mensajes recurrentes a los supervisores. [Haga clic ](../../workflow/using/supervising-workflows.md) aquí para obtener más información.

**Directrices generales**

Las siguientes directrices y prácticas recomendadas al utilizar flujos de trabajo pueden ayudar a mejorar el rendimiento. Para obtener más información, consulte estas secciones:
* [Prácticas recomendadas al utilizar flujos de trabajo](../../workflow/using/workflow-best-practices.md)
* [Control de la ejecución del flujo de trabajo](../../workflow/using/monitoring-workflow-execution.md)

### Seguimiento de entregas {#monitoring-deliveries}

<img src="assets/do-not-localize/icon_send.svg" width="60px">

**Informes SMTP**

Los informes SMTP muestran las estadísticas de entrega y los errores SMTP por dominio. [Obtenga más información](../../production/using/monitoring-processes.md)

**Prácticas recomendadas**

[Las prácticas recomendadas para el envío y el ](../../delivery/using/delivery-best-practices.md) diseño de entregas pueden ayudarle a mejorar su rendimiento.

**Solución de problemas de**
entregaSe pueden realizar acciones específicas al encontrar problemas con los envíos:
* [Problemas con entregas](../../production/using/performance-and-throughput-issues.md#deliverability_issues)
* [Problemas de visualización de imágenes](../../production/using/image-display-issues.md)
* [Problemas de rendimiento de envíos](../../delivery/using/delivery-performances.md)
* [Problemas con archivos temporales](../../production/using/temporary-files.md) : solo modelos  *de alojamiento locales*

### Monitorización de la base de datos {#monitoring-database}

<img src="assets/do-not-localize/icon_database.svg" width="60px">

**Flujo de trabajo para limpieza de bases de datos**

El flujo de trabajo Database cleanup permite eliminar datos obsoletos de la base de datos. Se recomienda evitar el crecimiento exponencial de la base de datos. [Haga clic ](../../production/using/database-cleanup-workflow.md) aquí para obtener más información.

**Solución de problemas de rendimiento de la base de datos**

Se pueden realizar acciones específicas al encontrar problemas con el rendimiento de la base de datos. [Haga clic ](../../production/using/database-performances.md) aquí para obtener más información.

**Mantenimiento de la base de datos**

*solo modelos de alojamiento locales e híbridos*

Se recomienda realizar el mantenimiento de la base de datos de forma regular para evitar el consumo excesivo de espacio en disco, lo que afecta al acceso a la base de datos. [Haga clic ](../../production/using/recommendations.md) aquí para obtener más información.

**Copia de seguridad y restauración**

*solo modelos de alojamiento locales e híbridos*

La copia de seguridad es esencial para evitar la pérdida de datos en caso de problemas (físicos o relacionados con el sistema) en una máquina. [Haga clic aquí](../../production/using/backup.md) para obtener más información. El procedimiento de restauración se describe en [esta sección](../../production/using/restoration.md).

## Principios técnicos del Campaign Classic {#campaign-classic-technical-principles}

Los recursos técnicos están disponibles en la documentación de Campaign Classic. Le recomendamos que se familiarice con estos temas antes de realizar cualquier operación técnica en su instancia.

**Modelos y capacidades de alojamiento**

* [modelos de alojamiento de Campaign Classic](../../installation/using/hosting-models.md)
* [Capacidades del modelo de alojamiento](../../installation/using/capability-matrix.md)

**Configuración del servidor**

*Modelos de alojamiento locales e híbridos únicamente*

* [Configuraciones de servidor obligatorias](../../installation/using/campaign-server-configuration.md)
* [Configuración del archivo Serverconf.xml](../../installation/using/the-server-configuration-file.md)
* [Configuración del servidor para la entrega](../../installation/using/email-deliverability.md)
* [Líneas de comandos para crear una instancia y declarar una base de datos](../../installation/using/command-lines.md)

**Principios generales**

* [arquitectura Campaign Classic](../../production/using/general-architecture.md)
* [módulos Campaign Classic](../../production/using/operating-principle.md)
* [opciones del Campaign Classic](../../installation/using/configuring-campaign-options.md)
* [Configuración del inicio automático de los módulos](../../production/using/administration.md)
* [Principio de configuración de Campaign](../../production/using/configuration-principle.md)
* [Procedimientos de resolución de problemas](../../production/using/performance-and-throughput-issues.md)
