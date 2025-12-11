---
product: campaign
title: Introducción a la monitorización de entregas
description: Obtenga más información acerca de las funciones de monitorización de entregas de Campaign Classic
feature: Monitoring, Deliverability
role: User
exl-id: 9ce11da0-e37b-459e-8ec7-d2bddf59bdf7
source-git-commit: 62ab16b206563aa25b8943e606d03a3184eb00db
workflow-type: ht
source-wordcount: '814'
ht-degree: 100%

---

# Introducción a la monitorización de entregas {#about-delivery-monitoring}

>[!IMPORTANT]
>
>Esta página documenta **funciones de supervisión específicas de Campaign Classic v7** para implementaciones híbridas y locales.

## Funciones de monitorización

### Monitorización de entrega {#monitoring-deliveries}

**Para las implementaciones híbridas/locales de la versión 7 de Campaign Classic**, se requiere supervisión adicional para los recursos del servidor y la configuración de MTA (Agente de transferencia de correo).

#### Solución de problemas de entregas pendientes {#pending-deliveries}

¿Qué sucede si no se entregan los envíos y su estado sigue siendo **Pendiente**?

* El proceso de ejecución está esperando a que estén disponibles algunos recursos. Es posible que el MTA no se haya iniciado.
Compruebe que los módulos mta@instance se inicien en los servidores MTA y, si es necesario, inicie el módulo MTA. [Más información](../../production/using/administration.md).

* El envío puede estar utilizando una afinidad que no se ha configurado en la instancia remitente.
Sugerencia: Compruebe la configuración de la administración del tráfico (afinidad IP). Para obtener más información sobre esto, consulte Control del tráfico SMTP saliente.

>[!NOTE]
>
>Estos pasos solo los puede realizar un usuario experto en instalaciones locales.

### Seguimiento de la capacidad de entrega {#deliverability-monitoring}

#### Instalación del paquete de entregabilidad {#deliverability-package}

Esta función está disponible a través de un paquete dedicado en Adobe Campaign. Para utilizarlo, este paquete debe estar instalado. Una vez finalizado, reinicie el servidor para que el paquete se tenga en cuenta.

* Para los clientes alojados e híbridos, el servicio de asistencia técnica y los consultores de Adobe configuran la **supervisión de la entrega** en su instancia. Para obtener más información, póngase en contacto con su administrador de cuentas de Adobe.

* Para las instalaciones on-premise, debe instalar el **[!UICONTROL Deliverability monitoring (Email Deliverability)]** paquete a través del **[!UICONTROL Tools]** > **[!UICONTROL Advanced]** > **[!UICONTROL Import package]** menú. Para obtener más información sobre esto, consulte [Instalación de paquetes estándar de Campaign Classic](../../installation/using/installing-campaign-standard-packages.md).

#### Flujo de trabajo de entregabilidad {#deliverability-workflow}

En Adobe Campaign Classic, la **supervisión de la entrega** se administra mediante el flujo de trabajo de **[!UICONTROL Refresh for deliverability]**. El flujo de trabajo se instala de manera predeterminada en todas las instancias y le permite inicializar la lista de reglas de calificación de correos rechazados, la lista de dominios y la lista de MX. Una vez que se ha instalado el paquete **[!UICONTROL Deliverability monitoring (Email Deliverability)]**, este flujo de trabajo se ejecuta todas las noches para actualizar regularmente la lista de reglas y permite administrar de forma activa la capacidad de envío de la plataforma.

**El paquete de entregabilidad permite acceder a lo siguiente:**

* El [informe de procesamiento de las bandejas de entrada](inbox-rendering.md), que permite realizar previsualizaciones de los mensajes en los principales clientes de correo electrónico para analizar el contenido y la reputación.
* Descripción general de la calidad del mensaje (bandeja de entrada, correo no deseado).

#### Herramientas de monitorización {#monitoring-tools}

**Para instalaciones locales**, puede utilizar las siguientes herramientas de monitorización:

* El informe **[!UICONTROL Delivery throughput]** proporciona una visión general del rendimiento de toda la plataforma durante un período determinado. Para obtener más información, consulte [esta sección](../../reporting/using/global-reports.md#delivery-throughput).
* Cada envío genera un informe de estadísticas de difusión para los diferentes proveedores de servicio de Internet (ISP). Muestra algunas métricas de calidad de datos y reputación que pueden afectar la capacidad de envío, incluidas las siguientes cifras:
   * **[!UICONTROL Hard bounces]** indican la calidad de los datos. Este valor debe ser inferior al 2 %.
   * **[!UICONTROL Soft bounces]** indican reputación. Este valor no debe ser superior al 10 % para un ISP determinado.

  Para obtener más información, consulte la sección [Estadísticas de envío](../../reporting/using/global-reports.md#delivery-statistics).

#### Directrices de monitorización {#monitoring-guidelines}

**Para instalaciones locales**, estas son algunas directrices adicionales sobre la monitorización de la entregabilidad:

* Compruebe regularmente el [rendimiento del envío](../../reporting/using/global-reports.md#delivery-throughput) de toda la plataforma para comprobar si es coherente con la configuración original.
* Compruebe que [los reintentos](delivery-failures-quarantine.md#retries-after-a-delivery-temporary-failure) estén correctamente configurados (30 minutos para el periodo de reintento y más de 20 reintentos) en plantillas de envíos.
* Compruebe periódicamente si puede acceder al buzón de [rechazados](delivery-failures-quarantine.md#bounce-mail-management) y que la cuenta no esté a punto de caducar.
* Compruebe el rendimiento de cada entrega, accesible desde el [panel de control de entrega](https://experienceleague.adobe.com/es/docs/campaign/campaign-v8/send/monitor/delivery-dashboard){target="_blank"}, para asegurarse de que es coherente con la validez de su contenido (por ejemplo, las “ventas flash” deben entregarse en minutos, no en días).
* Cuando utilice olas, compruebe que cada una tenga tiempo suficiente para finalizar antes de que se active la siguiente.
* Compruebe que las cantidades de errores y nuevas [cuarentenas](delivery-failures-quarantine.md) sean coherentes con otros envíos.
* Consulte cuidadosamente los [registros de envío](https://experienceleague.adobe.com/es/docs/campaign/campaign-v8/send/monitor/delivery-dashboard#delivery-logs-and-history){target="_blank"} en detalle para comprobar el tipo de errores resaltados (lista de bloqueados, problemas de DNS, reglas de correo no deseado, etc.).

### Solución de problemas {#delivery-troubleshooting}

Se pueden realizar acciones específicas al encontrar problemas con los envíos en **implementaciones híbridas/locales**:

* [Problemas de entregas](../../production/using/performance-and-throughput-issues.md#deliverability_issues)
* [Problemas de visualización de imágenes](../../production/using/image-display-issues.md)
* [Problemas de rendimiento de envíos](delivery-performance-troubleshooting.md)
* [Problemas de archivos temporales](../../production/using/temporary-files.md): *solo clientes in situ*

## Monitorización de entregas

Los siguientes recursos le ayudarán a monitorizar y rastrear el rendimiento de su envío en Campaign Classic v7:

### Acceso al panel de entrega

Obtenga información sobre cómo acceder a las listas de entregas y utilizar el panel de entregas para monitorizar la actividad de envíos:

* [Monitorización de las entrgas en la interfaz de usuario de Campaign](https://experienceleague.adobe.com/es/docs/campaign/campaign-v8/send/monitor/delivery-dashboard){target="_blank"} (documentación de la versión 8 de Campaign: se aplica tanto a la versión 7 como a la 8)
* [Estados de entrega](https://experienceleague.adobe.com/es/docs/campaign/campaign-v8/send/monitor/delivery-statuses){target="_blank"} (documentación de Campaign v8)
* [Avanzado: personalizar registros de entrega](customize-delivery-logs.md) (v7 híbrido/solo local: extensión de esquema)

### Seguimiento de interacciones de mensajes

Rastree las aperturas, los clics y las interacciones de los destinatarios con las entregas:

* [Documentación de seguimiento de mensajes](https://experienceleague.adobe.com/es/docs/campaign/campaign-v8/analytics/tracking/tracking){target="_blank"} (documentación de Campaign v8: se aplica tanto a v7 como a v8)
* [Configurar vínculos de seguimiento](https://experienceleague.adobe.com/es/docs/campaign/campaign-v8/analytics/tracking/tracked-links){target="_blank"} (documentación de Campaign v8)
* [Registros de seguimiento de acceso](https://experienceleague.adobe.com/es/docs/campaign/campaign-v8/analytics/tracking/tracking-logs){target="_blank"} (documentación de Campaign v8)

### Optimizar el rendimiento de la entrega

Prácticas recomendadas y solución de problemas de rendimiento de entregas:

* [Prácticas recomendadas de envío](https://experienceleague.adobe.com/es/docs/campaign/campaign-v8/start/delivery-best-practices){target="_blank"} (documentación de Campaign v8: se aplica tanto a v7 como a v8)
* [Rendimiento de envío y solución de problemas](delivery-performance-troubleshooting.md) (configuraciones específicas híbridas/locales de v7)

### Comprensión de errores y cuarentenas

Administrar errores de entrega, correos rechazados y direcciones en cuarentena:

* [Explicación de los errores de envío](https://experienceleague.adobe.com/es/docs/campaign/campaign-v8/send/monitor/delivery-failures){target="_blank"} (documentación de Campaign v8: guía completa para v7 y v8)
* [Administración de cuarentena](https://experienceleague.adobe.com/es/docs/campaign/campaign-v8/send/monitor/quarantines){target="_blank"} (documentación de Campaign v8: guía completa para v7 y v8)
* [Errores de envío y configuración de cuarentena](delivery-failures-quarantine.md) (configuraciones específicas híbridas/locales de v7)
