---
title: Monitoreo de la capacidad de entrega en Adobe Campaign Classic
description: Obtenga información sobre las herramientas y las directrices sobre la supervisión de la entrega en Adobe Campaign Classic.
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
source-git-commit: a30c4a2d31c3f674ac4a7bb4827a6951b36014ab
workflow-type: tm+mt
source-wordcount: '735'
ht-degree: 33%

---


# Supervisión de la capacidad de entrega{#monitoring-deliverability}

A continuación encontrará detalles sobre las diferentes herramientas de supervisión proporcionadas por el Adobe Campaign, así como algunas directrices adicionales sobre la supervisión de la capacidad de entrega.

## Monitoring tools {#monitoring-tools}

Utilice las funciones ofrecidas por Adobe Campaign para supervisar la capacidad de entrega de la plataforma.

El paquete de entregabilidad le permite acceder a:

* Informe de seguimiento técnico para el rendimiento diario de la entrega (supervisión técnica). Este informe, disponible bajo demanda, le permite recibir un informe diario por correo electrónico en una dirección especificada. Para obtener más información, póngase en contacto con el equipo de atención al cliente de Adobe.
* El informe [de procesamiento de la](../../delivery/using/inbox-rendering.md) Bandeja de entrada, que permite realizar previsualizaciones de los mensajes en los principales clientes de correo electrónico para analizar el contenido y la reputación.
* Descripción general de la calidad del mensaje (bandeja de entrada, correo no deseado).

También puede utilizar las siguientes herramientas:

* El **[!UICONTROL Delivery throughput]** informe proporciona una visión general del rendimiento de toda la plataforma durante un período determinado. Para obtener más información, consulte [esta sección](../../reporting/using/global-reports.md#delivery-throughput).
* The **[!UICONTROL Technical deliverability monitoring]** report includes a number of deliverability quality indicators for your platform. Para obtener más información, consulte [esta sección](#technical-deliverability-monitoring).
* El panel [del](../../delivery/using/monitoring-a-delivery.md#delivery-dashboard) envío le permite acceder al resumen [del](../../delivery/using/monitoring-a-delivery.md#delivery-summary)Envío, a los [Registros de envío, a la historia](../../delivery/using/monitoring-a-delivery.md#delivery-logs-and-history) y a los [Registros de seguimiento](../../delivery/using/monitoring-a-delivery.md#tracking-logs). Muestran los detalles del envío, qué destinatario se ha excluido y por qué, así como la información de seguimiento como aperturas y clics. <!--For more on this, see [Monitoring a delivery](../../delivery/using/monitoring-a-delivery.md).-->
* También puede comprobar el número de mensajes que enviar, procesar y enviar con éxito. Para obtener más información, consulte [esta sección](../../delivery/using/monitoring-a-delivery.md#number-of-messages-sent)
   <!--[SpamAssassin](../../installation/using/configuring-spamassassin.md)?-->

## Directrices de supervisión {#monitoring-guidelines}

Estas son algunas directrices adicionales sobre la supervisión de la capacidad de entrega:

* Compruebe regularmente el rendimiento [del](../../reporting/using/global-reports.md#delivery-throughput) envío de toda la plataforma para comprobar si es coherente con la configuración original.
* Compruebe que [los reintentos](../../delivery/using/understanding-delivery-failures.md#retries-after-a-delivery-temporary-failure) están correctamente configurados (30 minutos para el período de reintento y más de 20 reintentos) en Plantillas de envíos.
* Compruebe periódicamente que el buzón de [devoluciones](../../delivery/using/understanding-delivery-failures.md#bounce-mail-management) esté accesible y que la cuenta no esté a punto de caducar.
* Compruebe el rendimiento de cada envío para asegurarse de que es coherente con la validez del contenido del envío (p. ej. &#39;ventas flash&#39; deben entregarse en minutos, no en días).
* Cuando utilice [olas](../../delivery/using/steps-sending-the-delivery.md#sending-using-multiple-waves), compruebe que cada onda tiene tiempo suficiente para finalizar antes de que se active la siguiente.
* Compruebe que el número de errores y nuevas [cuarentenas](../../delivery/using/understanding-quarantine-management.md) sean coherentes con otros envíos.
* Consulte cuidadosamente los [registros de envío](../../delivery/using/monitoring-a-delivery.md#delivery-logs-and-history) en detalle para comprobar el tipo de errores resaltados (listas grises o negras, problemas de DNS, reglas antispam, etc.).

## Correo no deseado de señal {#signal-spam}

Signal Spam es un servicio francés que oferta el sistema de informes de bucle de retroalimentación anonimizado para los ISP franceses (Orange, SFR).

* Este servicio le permite seguir la reputación de los ISP franceses y la evolución de la actividad de los clientes.

* El correo no deseado de señal también proporciona quejas directas de que los usuarios finales inician sesión a través de una interfaz dedicada. Esas quejas se ponen en cuarentena a partir de la base de datos de direcciones de correo electrónico.

## 250ok {#deliverability-250ok}

[250ok](https://250ok.com/) es una solución de supervisión complementaria de las herramientas internas de entrega de Adobe que proporciona IP, listas negras de dominios e indicadores de reputación.

La información proporcionada es en tiempo real, lo que permite una asistencia proactiva.

## Informe de monitorización de la capacidad de envío técnica {#technical-deliverability-monitoring}

The technical deliverability monitoring report is updated daily and available by navigating to **[!UICONTROL Monitoring]** > **[!UICONTROL Overview]** and clicking the **[!UICONTROL Technical monitoring]** link from the Adobe Campaign **[!UICONTROL Home]** tab. Incluye una serie de indicadores de calidad de envío para su plataforma.

Estos indicadores se actualizan diariamente a las 9 a. m.

>[!NOTE]
>
>Además, puede recibir un informe diario por correo electrónico en una dirección específica. Háganos saber la dirección de correo electrónico solicitada por correo electrónico o a través de la Extranet de Adobe Campaign.

![](assets/s_tn_del_monitoring.png)

En el informe se usan los siguientes indicadores:

* **[!UICONTROL Reverse DNS]** : Adobe Campaign comprueba si se ha proporcionado un DNS inverso para una dirección IP y que este señala correctamente a la dirección IP.

* **[!UICONTROL SPF]** (Marco de Política del Remitente): Mecanismo de autenticación que permite a los ISP y proveedores de buzones de correo comprobar si el remitente del correo electrónico está autorizado en el dominio de envío.

* **[!UICONTROL DomainKeys]**: Servicio desarrollado por Yahoo! y pensado para certificar la identidad de un remitente de correo electrónico.

* **[!UICONTROL IP and RBL domain]** (lista negra en tiempo real): Una lista de direcciones IP y dominios que han sido marcados por organizaciones de listas de bloqueo por mala reputación de envío. Organizaciones dedicadas como Spamhaus, Spamcop, SURBL/URIBL, etc. mantienen estas listas. Adobe Campaign procesa actualmente comprobaciones con RBL que tienen un impacto significativo en la capacidad de entrega. Estos RBL reflejan su reputación y los ISP pueden consultarlos antes de aceptar recibir sus correos electrónicos.

* **[!UICONTROL SNDS]** (Servicios de datos de red inteligente): [Servicio antispam de Windows Live Hotmail](https://sendersupport.olc.protection.outlook.com/snds/FAQ.aspx). Hotmail es el único ISP que proporciona este tipo de información. Las puntuaciones de referencia son un resultado de filtro verde, una tasa de quejas de menos del 0,1 % y cero trampas no deseadas.

<!--### Delivery Reports - Broadcast Statistics {#broadcast-statistics}

Each delivery will generate a broadcast statistics report when you open a delivery in the “Deliveries List”, which includes some reputation metrics that may impact your deliverability.-->
