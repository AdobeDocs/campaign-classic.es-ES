---
title: Nivel del servicio del centro de mensajes
seo-title: Nivel del servicio del centro de mensajes
description: Nivel del servicio del centro de mensajes
seo-description: null
page-status-flag: never-activated
uuid: 8e363706-292b-40db-97bc-d41b41910556
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: message-center
content-type: reference
topic-tags: reports
discoiquuid: e46a4e87-6c02-4b9c-bf6d-bb4e785e78fa
index: y
internal: n
snippet: y
translation-type: ht
source-git-commit: 20f835c357d016643ea1f3209ee4dfb6d3239f90

---


# Nivel del servicio del centro de mensajes{#message-center-service-level}

Este informe muestra las estadísticas de envío relacionadas con los mensajes transaccionales y el desglose de errores. Puede hacer clic en un tipo de error para mostrar sus detalles. También se puede acceder a este informe, dirigido a los administradores técnicos, a través del entorno **[!UICONTROL Monitoring]** en la instancia de control.

![](assets/mc_reports_1.png)

En este informe puede elegir mostrar las estadísticas generales o las relativas a una instancia de ejecución determinada. También puede filtrar los datos por canal y por un periodo específico. Los indicadores que se muestran en la sección **[!UICONTROL Indicators over the period]** se calculan en el periodo seleccionado:

* **[!UICONTROL Incoming (throughput event/h)]**: número promedio de eventos introducidos por hora en la cola del Centro de mensajes.
* **[!UICONTROL Incoming (event vol)]**: número de eventos introducidos en la cola del Centro de mensajes.
* **[!UICONTROL Outgoing (throughput msg/h)]**: número promedio por hora de eventos del Centro de mensajes salientes correctos (por envío).
* **[!UICONTROL Outgoing (msg vol)]**: número de eventos de Centro de mensajes salientes correctos (por envío).
* **[!UICONTROL Average sending time (seconds)]**: tiempo promedio empleado en el Centro de mensajes para los eventos procesados correctamente. El cálculo toma en cuenta el tiempo de procesamiento y el tiempo de envío de mta.
* **[!UICONTROL Error rate]**: número de eventos con errores comparados con el número de eventos que se han introducido en la cola del Centro de mensajes. Los siguientes errores se tienen en cuenta: error de enrutamiento, evento caducado (evento que ha estado en la cola demasiado tiempo), error de envío, omitido por la entrega (cuarentena, etc.).

>[!NOTE]
>
>Los umbrales del indicador de advertencia (naranja) y alerta (rojo) pueden configurarse en el asistente de implementación. Consulte [Umbrales de monitorización](../../message-center/using/monitoring-thresholds.md).

