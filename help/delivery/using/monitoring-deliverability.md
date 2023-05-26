---
product: campaign
title: Monitorización de la entregabilidad en Adobe Campaign
description: Obtenga información acerca de las herramientas y las directrices sobre la monitorización de la entregabilidad en Adobe Campaign
badge-v7: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7"
badge-v8: label="v8" type="Positive" tooltip="Also applies to Campaign v8"
feature: Deliverability
exl-id: e4caa316-242f-46cd-a20b-a5eee5a0c456
source-git-commit: 6dc6aeb5adeb82d527b39a05ee70a9926205ea0b
workflow-type: tm+mt
source-wordcount: '531'
ht-degree: 100%

---

# Monitorización de la capacidad de entrega{#monitoring-deliverability}



A continuación, encontrará detalles sobre las herramientas de monitorización que proporciona Adobe Campaign, así como algunas directrices adicionales para aprovechar las funciones que ofrece para monitorizar la capacidad de entrega de su plataforma.

## Acerca de la monitorización de la capacidad de entrega {#about-deliverability-monitoring}

Esta función está disponible a través de un paquete dedicado en Adobe Campaign. Para utilizarlo, este paquete debe estar instalado. Una vez finalizado, reinicie el servidor para que el paquete se tenga en cuenta.
* Para los clientes alojados e híbridos, el servicio de asistencia técnica y los consultores de Adobe configuran la **supervisión de la entrega** en su instancia. Para obtener más información, póngase en contacto con su administrador de cuentas de Adobe.

* Para las instalaciones on-premise, debe instalar el **[!UICONTROL Deliverability monitoring (Email Deliverability)]** paquete a través del **[!UICONTROL Tools]** > **[!UICONTROL Advanced]** > **[!UICONTROL Import package]** menú. Para obtener más información sobre esto, consulte [Instalación de paquetes estándar de Campaign Classic](../../installation/using/installing-campaign-standard-packages.md).

En Adobe Campaign Classic, la **supervisión de la entrega** se administra mediante el flujo de trabajo de **[!UICONTROL Refresh for deliverability]**. El flujo de trabajo se instala de manera predeterminada en todas las instancias y le permite inicializar la lista de reglas de cualificación de correos rechazados, la lista de dominios y la lista de MX. Una vez que se ha instalado el paquete **[!UICONTROL Deliverability monitoring (Email Deliverability)]**, este flujo de trabajo se ejecuta todas las noches para actualizar regularmente la lista de reglas y permite administrar de forma activa la capacidad de envío de la plataforma.

El paquete de capacidad de entrega permite acceder a lo siguiente:

* El [informe de procesamiento de las bandejas de entrada](inbox-rendering.md), que permite realizar previsualizaciones de los mensajes en los principales clientes de correo electrónico para analizar el contenido y la reputación.
* Descripción general de la calidad del mensaje (bandeja de entrada, correo no deseado).

## Herramientas de monitorización {#monitoring-tools}

También puede utilizar las siguientes herramientas:

* El informe **[!UICONTROL Delivery throughput]** proporciona una visión general del rendimiento de toda la plataforma durante un período determinado. Para obtener más información, consulte [esta sección](../../reporting/using/global-reports.md#delivery-throughput).
* Cada envío genera un informe de estadísticas de difusión para los diferentes proveedores de servicio de Internet (ISP). Muestra algunas métricas de calidad de datos y reputación que pueden afectar la capacidad de envío, incluidas las siguientes cifras:
   * **[!UICONTROL Hard bounces]** indican la calidad de los datos. Este valor debe ser inferior al 2 %.
   * **[!UICONTROL Soft bounces]** indican reputación. Este valor no debe ser superior al 10 % para un ISP determinado.

   Para obtener más información, consulte la sección [Estadísticas de envío](../../reporting/using/global-reports.md#delivery-statistics).
* De manera más general, el [panel de envío](about-delivery-monitoring.md) le permite acceder a:
   * el [resumen del envío](delivery-dashboard.md#delivery-summary), que muestra el detalle del envío y el número de mensajes que se van a enviar, procesados y enviados con éxito;
   * los [registros de envío y el historial](delivery-dashboard.md#delivery-logs-and-history), que muestran qué destinatario se ha excluido y por qué;
   * los [registros de seguimiento](delivery-dashboard.md#tracking-logs), que muestran información de seguimiento como aperturas y clics.

## Directrices de monitorización {#monitoring-guidelines}

Estas son algunas directrices adicionales sobre la monitorización de la capacidad de envío:

* Compruebe regularmente el [rendimiento del envío](../../reporting/using/global-reports.md#delivery-throughput) de toda la plataforma para comprobar si es coherente con la configuración original.
* Compruebe que [los reintentos](understanding-delivery-failures.md#retries-after-a-delivery-temporary-failure) estén correctamente configurados (30 minutos para el periodo de reintento y más de 20 reintentos) en plantillas de envíos.
* Compruebe periódicamente si puede acceder al buzón de [rechazados](understanding-delivery-failures.md#bounce-mail-management) y que la cuenta no esté a punto de caducar.
* Compruebe el rendimiento de cada entrega, accesible desde el [panel de entrega](delivery-dashboard.md), para asegurarse de que es coherente con la validez de su contenido (por ejemplo, las “ventas flash” deben entregarse en minutos, no en días).
* Cuando utilice [olas](steps-sending-the-delivery.md#sending-using-multiple-waves), compruebe que cada ola tenga tiempo suficiente para finalizar antes de que se active la siguiente.
* Compruebe que las cantidades de errores y nuevas [cuarentenas](understanding-quarantine-management.md) sean coherentes con otros envíos.
* Consulte cuidadosamente los [registros de envío](delivery-dashboard.md#delivery-logs-and-history) en detalle para comprobar el tipo de errores resaltados (lista de bloqueados, problemas de DNS, reglas de correo no deseado, etc.).
