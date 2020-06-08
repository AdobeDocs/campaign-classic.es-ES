---
title: Monitorización de la capacidad de envío en Adobe Campaign Classic
description: Obtenga información sobre las herramientas y las directrices sobre la monitorización de capacidad de envío en Adobe Campaign Classic.
page-status-flag: never-activated
uuid: 0b5c5dbd-f532-4d8a-a255-9e6d88357d8d
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: delivery
content-type: reference
topic-tags: deliverability-management
discoiquuid: 0baef937-f00b-4fc4-8608-a870997be684
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: f4d82657fbeae39af173c867975455669497d8eb
workflow-type: tm+mt
source-wordcount: '787'
ht-degree: 94%

---


# Supervisión de la capacidad de entrega{#monitoring-deliverability}

A continuación encontrará detalles sobre las diferentes herramientas de monitorización que proporciona Adobe Campaign, así como algunas directrices adicionales sobre la monitorización de la capacidad de envío.

## Herramientas de monitorización {#monitoring-tools}

Utilice las funciones que ofrece Adobe Campaign para monitorizar la capacidad de envío de la plataforma.

El paquete de capacidad de envío permite acceder a:

* Informe de seguimiento técnico para el rendimiento diario de la capacidad de envío (monitorización técnica). Este informe, disponible bajo demanda, le permite recibir un informe diario por correo electrónico en una dirección especificada. Para obtener más información, póngase en contacto con el equipo de atención al cliente de Adobe.
* El [informe de procesamiento de las bandejas de entrada](../../delivery/using/inbox-rendering.md), que permite realizar previsualizaciones de los mensajes en los principales clientes de correo electrónico para analizar el contenido y la reputación.
* Descripción general de la calidad del mensaje (bandeja de entrada, correo no deseado).

También puede utilizar las siguientes herramientas:

* El informe **[!UICONTROL Delivery throughput]** proporciona una visión general del rendimiento de toda la plataforma durante un período determinado. Para obtener más información, consulte [esta sección](../../reporting/using/global-reports.md#delivery-throughput).
* El informe **[!UICONTROL Technical deliverability monitoring]** incluye una serie de indicadores de calidad de capacidad de envío para su plataforma. Para obtener más información, consulte [esta sección](#technical-deliverability-monitoring).
* Cada envío genera un informe de estadísticas de difusión para los diferentes proveedores de servicio de Internet (ISP). Muestra algunas métricas de calidad de datos y reputación que pueden afectar la capacidad de envío, incluidas las siguientes cifras:
   * **[!UICONTROL Hard bounces]** indican la calidad de los datos. Este valor debe ser inferior al 2 %.
   * **[!UICONTROL Soft bounces]** indican reputación. Este valor no debe ser superior al 10 % para un ISP determinado.
   Para obtener más información, consulte la sección [Estadísticas de envío](../../reporting/using/global-reports.md#delivery-statistics).
* De manera más general, el [panel de envío](../../delivery/using/monitoring-a-delivery.md#delivery-dashboard) le permite acceder a:
   * el [resumen del envío](../../delivery/using/monitoring-a-delivery.md#delivery-summary), que muestra el detalle del envío y el [número de mensajes](../../delivery/using/monitoring-a-delivery.md#number-of-messages-sent) que se van a enviar, procesados y enviados con éxito;
   * los [registros de envío y el historial](../../delivery/using/monitoring-a-delivery.md#delivery-logs-and-history), que muestran qué destinatario se ha excluido y por qué;
   * los [registros de seguimiento](../../delivery/using/monitoring-a-delivery.md#tracking-logs), que muestran información de seguimiento como aperturas y clics.

## Directrices de monitorización {#monitoring-guidelines}

Estas son algunas directrices adicionales sobre la monitorización de la capacidad de envío:

* Compruebe regularmente el [rendimiento del envío](../../reporting/using/global-reports.md#delivery-throughput) de toda la plataforma para comprobar si es coherente con la configuración original.
* Compruebe que [los reintentos](../../delivery/using/understanding-delivery-failures.md#retries-after-a-delivery-temporary-failure) estén correctamente configurados (30 minutos para el periodo de reintento y más de 20 reintentos) en plantillas de envíos.
* Compruebe periódicamente si puede acceder al buzón de [rechazados](../../delivery/using/understanding-delivery-failures.md#bounce-mail-management) y que la cuenta no esté a punto de caducar.
* Compruebe el rendimiento de cada envío para asegurarse de que es coherente con la validez del contenido del envío (p. ej. las “ventas flash” deben entregarse en minutos, no en días).
* Cuando utilice [olas](../../delivery/using/steps-sending-the-delivery.md#sending-using-multiple-waves), compruebe que cada ola tenga tiempo suficiente para finalizar antes de que se active la siguiente.
* Compruebe que las cantidades de errores y nuevas [cuarentenas](../../delivery/using/understanding-quarantine-management.md) sean coherentes con otros envíos.
* Carefully consult the [delivery logs](../../delivery/using/monitoring-a-delivery.md#delivery-logs-and-history) in detail to check the kind of errors that are highlighted (grey or black-listing, DNS issues, anti-spam rules, etc.).

## Signal Spam {#signal-spam}

Signal Spam es un servicio francés que ofrece el sistema de informes de bucle de retroalimentación anonimizado para los ISP franceses (Orange, SFR).

* Este servicio le permite seguir la reputación de los ISP franceses y la evolución de la actividad de los clientes.

* Signal Spam también proporciona quejas directas de que los usuarios finales registran a través de una interfaz dedicada. Esas quejas se ponen en cuarentena a partir de la base de datos de direcciones de correo electrónico.

## 250ok {#deliverability-250ok}

[250ok](https://250ok.com/) es una solución de supervisión complementaria de las herramientas internas de entrega de Adobe que proporciona IP, listas negras de dominios e indicadores de reputación.

La información se proporciona en tiempo real, lo que permite una asistencia proactiva.

## Informe de monitorización de la capacidad de envío técnica {#technical-deliverability-monitoring}

El informe de monitorización de capacidad de envío técnica se actualiza diariamente y está disponible. Para ello, vaya a **[!UICONTROL Monitoring]** > **[!UICONTROL Overview]** y, en la pestaña **[!UICONTROL Home]** de Adobe Campaign, haga clic en el enlace **[!UICONTROL Technical monitoring]**. Incluye una serie de indicadores de calidad de envío para su plataforma.

Estos indicadores se actualizan diariamente a las 9 a. m.

>[!NOTE]
>
>Además, puede recibir un informe diario por correo electrónico en una dirección específica. Infórmenos de la dirección de correo electrónico solicitada por correo electrónico o a través de la Extranet de Adobe Campaign.

![](assets/s_tn_del_monitoring.png)

En el informe se usan los siguientes indicadores:

* **[!UICONTROL Reverse DNS]** : Adobe Campaign comprueba si se ha proporcionado un DNS inverso para una dirección IP y que este señala correctamente a la dirección IP.

* **[!UICONTROL SPF]** (Marco de Política del Remitente): Mecanismo de autenticación que permite a los ISP y proveedores de buzones de correo comprobar si el remitente del correo electrónico está autorizado en el dominio de envío.

* **[!UICONTROL DomainKeys]**: Servicio desarrollado por Yahoo! y pensado para certificar la identidad de un remitente de correo electrónico.

* **[!UICONTROL IP and RBL domain]** (lista negra en tiempo real): Una lista de direcciones IP y dominios que han sido marcados por organizaciones de listas de bloqueo por mala reputación de envío. Organizaciones dedicadas como Spamhaus, Spamcop, SURBL/URIBL, etc. mantienen estas listas. Adobe Campaign procesa actualmente comprobaciones con RBL que tienen un impacto significativo en la capacidad de entrega. Estos RBL reflejan su reputación y los ISP pueden consultarlos antes de aceptar recibir sus correos electrónicos.

* **[!UICONTROL SNDS]** (Servicios de datos de red inteligente): [Servicio antispam de Windows Live Hotmail](https://sendersupport.olc.protection.outlook.com/snds/FAQ.aspx). Hotmail es el único ISP que proporciona este tipo de información. Las puntuaciones de referencia son un resultado de filtro verde, una tasa de quejas de menos del 0,1 % y cero trampas no deseadas.

<!--### Delivery Reports - Broadcast Statistics {#broadcast-statistics}

Each delivery will generate a broadcast statistics report when you open a delivery in the “Deliveries List”, which includes some reputation metrics that may impact your deliverability.-->
