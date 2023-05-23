---
product: campaign
title: Directrices de monitorización
description: Descubra las directrices y las prácticas recomendadas para supervisar los procesos e instancias de Campaign
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
feature: Monitoring
exl-id: ca0c33c5-7350-462a-bc65-4cab51e529d9
source-git-commit: 4661688a22bd1a82eaf9c72a739b5a5ecee168b1
workflow-type: tm+mt
source-wordcount: '760'
ht-degree: 26%

---

# Directrices de monitorización {#monitoring-guidelines}



## Panel de monitorización de instancias {#instance-monitoring-dashboard}

El **[!UICONTROL Monitoring]** La pestaña, a la que se puede acceder desde la página de inicio del Campaign Classic, es el punto de entrada principal para ayudarle a monitorizar la instancia.

Proporciona un tablero de lo que está ocurriendo en su instancia: su estado (versión de compilación, paquetes instalados, etc.), indicadores del sistema, registros, flujos de trabajo que se están ejecutando actualmente, estado de los últimos envíos enviados, etc.

Encontrará información detallada [aquí](../../production/using/monitoring-processes.md).

![](assets/monitoring_tab.png)

## Monitorización de procesos de Campaign Classic {#monitoring-campaign-classic-processes}

<table>
<tr><td><img src="assets/do-not-localize/icon_system.svg" width="60px"><p><a href="#monitoring-instance">Monitorización de la instancia</a></p></td>
<td><img src="assets/do-not-localize/icon_workflows.svg" width="60px"><p><a href="#monitoring-workflows">Monitorización de flujos de trabajo</a></p></td>
<td><img src="assets/do-not-localize/icon_send.svg" width="60px"><p><a href="#monitoring-deliveries">Monitorización de las entregas</a></p></td>
<td><img src="assets/do-not-localize/icon_database.svg" width="60px"><p><a href="#monitoring-database">Monitorización de la base de datos</a></p></td></tr>
</table>

Hay disponibles formas adicionales de monitorizar los diferentes procesos de Campaign. Proporcionan varias formas de monitorizar las instancias para asegurarse de que el sistema esté en buen estado y, finalmente, solucionar problemas que pueden producirse al configurar flujos de trabajo, realizar envíos, etc.

### Monitorización de la instancia {#monitoring-instance}

<img src="assets/do-not-localize/icon_system.svg" width="60px">

**Herramientas de monitorización automática**

Hay varios métodos automáticos disponibles. para ayudarle a monitorizar su instancia. Por ejemplo, puede configurar informes de correo electrónico con anomalías detectadas, recuperar una lista de indicadores en formato XML, etc. [Haga clic aquí](../../production/using/monitoring-processes.md#automatic-monitoring) para obtener más información.

**Pista de auditoría**

La pista de auditoría permite visualizar el historial completo de cambios relacionados con las opciones, los flujos de trabajo y los esquemas dentro de la instancia. [Haga clic aquí](../../production/using/audit-trail.md) para obtener más información.

**Panel de control**

El Panel de control de Campaign le permite administrar varias configuraciones de la instancia: administrar permisos de URL, comprobar los detalles de la instancia, como las versiones de compilación de los servidores, etc. También le permite monitorizar el espacio disponible en los servidores SFTP conectados a su instancia. [Haga clic aquí](https://experienceleague.adobe.com/docs/control-panel/using/control-panel-home.html?lang=es) para obtener más información.

>[!NOTE]
>
>Todos los usuarios administradores pueden acceder al Panel de control. Los pasos para otorgar acceso de administrador a un usuario se detallan en [esta página](https://experienceleague.adobe.com/docs/control-panel/using/discover-control-panel/managing-permissions.html?lang=es#discover-control-panel).
>
>Tenga en cuenta que la instancia debe alojarse en AWS y actualizarse con la [última versión de GA](../../rn/using/rn-overview.md). Aprenda a comprobar su versión en [esta sección](../../platform/using/launching-adobe-campaign.md#getting-your-campaign-version). Para comprobar si la instancia está alojada en AWS, siga los pasos detallados en [esta página](https://experienceleague.adobe.com/docs/control-panel/using/faq.html?lang=es).

### Monitorización de flujos de trabajo {#monitoring-workflows}

<img src="assets/do-not-localize/icon_workflows.svg" width="60px">

**Mapa de calor del flujo de trabajo**

El mapa de calor del flujo de trabajo proporciona una representación visual de todos los flujos de trabajo que se ejecutan en la instancia. Permite monitorizar fácilmente la carga de la instancia y planificar los flujos de trabajo en consecuencia. [Haga clic aquí](../../workflow/using/heatmap.md) para obtener más información.

**Pista de auditoría**

La pista de auditoría permite visualizar todas las modificaciones realizadas en los flujos de trabajo, así como sus estados actuales. [Haga clic aquí](../../production/using/audit-trail.md).

**Solución de problemas de flujos**

Se pueden realizar acciones específicas al encontrar problemas con la ejecución de un flujo de trabajo. [Haga clic aquí](../../production/using/workflow-execution.md) para obtener más información

**Monitorización del estado de flujo de trabajo**

Además del mapa de calor, puede crear un flujo de trabajo que le permitirá monitorizar el estado de un conjunto de flujos de trabajo y enviar mensajes recurrentes a los supervisores. [Haga clic aquí](../../workflow/using/supervising-workflows.md) para obtener más información.

**Directrices generales**

Las siguientes directrices y prácticas recomendadas al utilizar flujos de trabajo pueden ayudar a mejorar el rendimiento. Para obtener más información, consulte estas secciones:
* [Prácticas recomendadas al utilizar flujos de trabajo](../../workflow/using/workflow-best-practices.md)
* [Control de la ejecución del flujo de trabajo](../../workflow/using/monitoring-workflow-execution.md)

### Seguimiento de entregas {#monitoring-deliveries}

<img src="assets/do-not-localize/icon_send.svg" width="60px">

**Informes SMTP**

Los informes SMTP muestran las estadísticas de envío y los errores SMTP por dominio. [Más información](../../production/using/monitoring-processes.md)

**Prácticas recomendadas**

[Prácticas recomendadas para la entrega y el diseño de envíos](../../delivery/using/delivery-best-practices.md) puede ayudarle a mejorar su rendimiento.

**Solución de problemas del envío**
Se pueden realizar acciones específicas al encontrar problemas con las entregas:
* [Problemas de entregas](../../production/using/performance-and-throughput-issues.md#deliverability_issues)
* [Problemas de visualización de imágenes](../../production/using/image-display-issues.md)
* [Problemas de rendimiento de envíos](../../delivery/using/delivery-performances.md)
* [Problemas de archivos temporales](../../production/using/temporary-files.md) - *solo modelos de alojamiento on-premise*

### Monitorización de la base de datos {#monitoring-database}

<img src="assets/do-not-localize/icon_database.svg" width="60px">

**Flujo de trabajo de limpieza de la base de datos**

El flujo de trabajo Database cleanup permite eliminar datos obsoletos de la base de datos. Se recomienda evitar el crecimiento exponencial de la base de datos. [Haga clic aquí](../../production/using/database-cleanup-workflow.md) para obtener más información.

**Solución de problemas de rendimiento de base**

Se pueden realizar acciones específicas al encontrar problemas con el rendimiento de la base de datos. [Haga clic aquí](../../production/using/database-performances.md) para obtener más información.

**Mantenimiento de la base de datos**

*solo modelos de alojamiento on-premise e híbrido*

Se recomienda realizar el mantenimiento de la base de datos de forma regular para evitar un consumo excesivo de espacio en disco, lo que afecta al acceso a la base de datos. [Haga clic aquí](../../production/using/recommendations.md) para obtener más información.

**Copia de seguridad y restauración**

*solo modelos de alojamiento on-premise e híbrido*

El backup es esencial para evitar la pérdida de datos en caso de problemas (ya sean físicos o relacionados con el sistema) en una máquina. [Haga clic aquí](../../production/using/backup.md) para obtener más información. El procedimiento de restauración se describe en [esta sección](../../production/using/restoration.md).

## Principios técnicos del Campaign Classic {#campaign-classic-technical-principles}

Los recursos técnicos están disponibles en la documentación del Campaign Classic. Le recomendamos que se familiarice con estos temas antes de realizar cualquier operación técnica en su instancia.

**Modelos y capacidades de alojamiento**

* [modelos de alojamiento de Campaign Classic](../../installation/using/hosting-models.md)
* [Funcionalidades del modelo de alojamiento](../../installation/using/capability-matrix.md)

**Configuración del servidor**

*Solo modelos de alojamiento on-premise e híbridos*

* [Configuraciones del servidor](../../installation/using/configuring-campaign-server.md)
* [Configuración del archivo Serverconf.xml](../../installation/using/the-server-configuration-file.md)
* [Configuración del servidor para envío](../../installation/using/email-deliverability.md)
* [Líneas de comandos para crear una instancia y declarar una base de datos](../../installation/using/command-lines.md)

**Principios generales**

* [arquitectura de Campaign Classic](../../production/using/general-architecture.md)
* [Módulos de Campaign Classic](../../production/using/operating-principle.md)
* [Opciones del Campaign Classic](../../installation/using/configuring-campaign-options.md)
* [Cómo configurar el inicio automático de los módulos](../../production/using/administration.md)
* [Principio de configuración de Campaign](../../production/using/configuration-principle.md)
* [Procedimientos de resolución de problemas](../../production/using/performance-and-throughput-issues.md)
