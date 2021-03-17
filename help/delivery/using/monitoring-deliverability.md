---
solution: Campaign Classic
product: campaign
title: Monitorización de la capacidad de envío en Adobe Campaign Classic
description: Obtenga información sobre las herramientas y las directrices sobre la monitorización de capacidad de envío en Adobe Campaign Classic.
audience: delivery
content-type: reference
topic-tags: deliverability-management
translation-type: ht
source-git-commit: fa5679d91808edb8e3916d5f0e0f54c73198e934
workflow-type: ht
source-wordcount: '479'
ht-degree: 100%

---


# Supervisión de la capacidad de entrega{#monitoring-deliverability}

A continuación encontrará detalles sobre las diferentes herramientas de monitorización que proporciona Adobe Campaign, así como algunas directrices adicionales sobre la monitorización de la capacidad de envío.

## Herramientas de monitorización {#monitoring-tools}

Utilice las funciones que ofrece Adobe Campaign para monitorizar la capacidad de envío de la plataforma.

El paquete de capacidad de envío permite acceder a:

* El [informe de procesamiento de las bandejas de entrada](../../delivery/using/inbox-rendering.md), que permite realizar previsualizaciones de los mensajes en los principales clientes de correo electrónico para analizar el contenido y la reputación.
* Descripción general de la calidad del mensaje (bandeja de entrada, correo no deseado).

También puede utilizar las siguientes herramientas:

* El informe **[!UICONTROL Delivery throughput]** proporciona una visión general del rendimiento de toda la plataforma durante un período determinado. Para obtener más información, consulte [esta sección](../../reporting/using/global-reports.md#delivery-throughput).
* Cada envío genera un informe de estadísticas de difusión para los diferentes proveedores de servicio de Internet (ISP). Muestra algunas métricas de calidad de datos y reputación que pueden afectar la capacidad de envío, incluidas las siguientes cifras:
   * **[!UICONTROL Hard bounces]** indican la calidad de los datos. Este valor debe ser inferior al 2 %.
   * **[!UICONTROL Soft bounces]** indican reputación. Este valor no debe ser superior al 10 % para un ISP determinado.

   Para obtener más información, consulte la sección [Estadísticas de envío](../../reporting/using/global-reports.md#delivery-statistics).
* De manera más general, el [panel de envío](../../delivery/using/about-delivery-monitoring.md) le permite acceder a:
   * el [resumen del envío](../../delivery/using/delivery-dashboard.md#delivery-summary), que muestra el detalle del envío y el número de mensajes que se van a enviar, procesados y enviados con éxito;
   * los [registros de envío y el historial](../../delivery/using/delivery-dashboard.md#delivery-logs-and-history), que muestran qué destinatario se ha excluido y por qué;
   * los [registros de seguimiento](../../delivery/using/delivery-dashboard.md#tracking-logs), que muestran información de seguimiento como aperturas y clics.

## Directrices de monitorización {#monitoring-guidelines}

Estas son algunas directrices adicionales sobre la monitorización de la capacidad de envío:

* Compruebe regularmente el [rendimiento del envío](../../reporting/using/global-reports.md#delivery-throughput) de toda la plataforma para comprobar si es coherente con la configuración original.
* Compruebe que [los reintentos](../../delivery/using/understanding-delivery-failures.md#retries-after-a-delivery-temporary-failure) estén correctamente configurados (30 minutos para el periodo de reintento y más de 20 reintentos) en plantillas de envíos.
* Compruebe periódicamente si puede acceder al buzón de [rechazados](../../delivery/using/understanding-delivery-failures.md#bounce-mail-management) y que la cuenta no esté a punto de caducar.
* Compruebe el rendimiento de cada envío para asegurarse de que es coherente con la validez del contenido del envío (p. ej. las “ventas flash” deben entregarse en minutos, no en días).
* Cuando utilice [olas](../../delivery/using/steps-sending-the-delivery.md#sending-using-multiple-waves), compruebe que cada ola tenga tiempo suficiente para finalizar antes de que se active la siguiente.
* Compruebe que las cantidades de errores y nuevas [cuarentenas](../../delivery/using/understanding-quarantine-management.md) sean coherentes con otros envíos.
* Consulte cuidadosamente los [registros de envío](../../delivery/using/delivery-dashboard.md#delivery-logs-and-history) en detalle para comprobar el tipo de errores resaltados (lista de bloqueados, problemas de DNS, reglas de correo no deseado, etc.).

## Signal Spam {#signal-spam}

Signal Spam es un servicio francés que ofrece el sistema de informes de bucle de retroalimentación anonimizado para los ISP franceses (Orange, SFR).

* Este servicio le permite seguir la reputación de los ISP franceses y la evolución de la actividad de los clientes.

* Signal Spam también proporciona quejas directas de que los usuarios finales registran a través de una interfaz dedicada. Esas quejas se ponen en cuarentena a partir de la base de datos de direcciones de correo electrónico.

## 250ok {#deliverability-250ok}

[250ok](https://250ok.com/) es una solución de monitorización complementaria de las herramientas internas de capacidad de envío de Adobe que proporciona IP, lista de bloqueados e indicadores de reputación.

La información se proporciona en tiempo real, lo que permite una asistencia proactiva.

<!--### Delivery Reports - Broadcast Statistics {#broadcast-statistics}

Each delivery will generate a broadcast statistics report when you open a delivery in the “Deliveries List”, which includes some reputation metrics that may impact your deliverability.-->
