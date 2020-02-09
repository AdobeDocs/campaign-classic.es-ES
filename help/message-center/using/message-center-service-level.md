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
translation-type: tm+mt
source-git-commit: 20f835c357d016643ea1f3209ee4dfb6d3239f90

---


# Nivel del servicio del centro de mensajes{#message-center-service-level}

Este informe muestra las estadísticas de envío relacionadas con los mensajes transaccionales y el desglose de errores. Puede hacer clic en un tipo de error para mostrar sus detalles. This report, aimed at technical administrators, can also be accessed via the **[!UICONTROL Monitoring]** universe in the control instance.

![](assets/mc_reports_1.png)

En este informe puede elegir mostrar las estadísticas generales o las relativas a una instancia de ejecución determinada. También puede filtrar los datos por canal y por un período específico. The indicators displayed in the **[!UICONTROL Indicators over the period]** section are calculated over the period selected:

* **[!UICONTROL Incoming (throughput event/h)]** :: número promedio por hora de eventos ingresados en la cola del Centro de mensajes.
* **[!UICONTROL Incoming (event vol)]** :: número de eventos ingresados en la cola de Message Center.
* **[!UICONTROL Outgoing (throughput msg/h)]** :: número promedio por hora de los eventos de centro de mensajes salientes (enviados por una entrega).
* **[!UICONTROL Outgoing (msg vol)]** :: número de eventos de centro de mensajes salientes correctos (enviados por un envío).
* **[!UICONTROL Average sending time (seconds)]** :: promedio de tiempo empleado en el centro de mensajes para eventos procesados correctamente. El cálculo toma en cuenta el tiempo de procesamiento y el tiempo de envío de mta.
* **[!UICONTROL Error rate]** :: número de eventos con errores en comparación con el número de eventos que han entrado en la cola de Message Center. Los siguientes errores se tienen en cuenta: error de enrutamiento, evento caducado (evento que ha estado en la cola demasiado tiempo), error de envío, omitido por el envío (cuarentena, etc.).

>[!NOTE]
>
>Los umbrales del indicador de advertencia (naranja) y alerta (rojo) pueden configurarse en el asistente de implementación. Consulte los umbrales [de monitoreo](../../message-center/using/monitoring-thresholds.md).

