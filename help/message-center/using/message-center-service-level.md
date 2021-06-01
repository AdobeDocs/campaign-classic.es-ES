---
solution: Campaign Classic
product: campaign
title: Nivel de servicio del Centro de mensajería
description: Obtenga más información sobre el informe de nivel de servicio del Centro de mensajes .
audience: message-center
content-type: reference
topic-tags: reports
exl-id: b8dc9891-84c8-445d-ad6a-d06048c8faaf
source-git-commit: d39b15b0efc6cbd6ab24e074713be6f8fc90e5fc
workflow-type: tm+mt
source-wordcount: '237'
ht-degree: 89%

---

# Nivel del servicio del centro de mensajes {#message-center-service-level}

Este informe muestra las estadísticas de envío relacionadas con los mensajes transaccionales y el desglose de errores. Puede hacer clic en un tipo de error para mostrar sus detalles.

También se puede acceder a este informe, dirigido a los administradores técnicos, a través de la pestaña **[!UICONTROL Monitoring]** de la instancia de control.

![](assets/mc_reports_1.png)

En este informe puede elegir mostrar las estadísticas generales o las relativas a una instancia de ejecución determinada. También puede filtrar los datos por canal y por un periodo específico.

Los indicadores que se muestran en la sección **[!UICONTROL Indicators over the period]** se calculan en el periodo seleccionado:

* **[!UICONTROL Incoming (throughput event/h)]** : número promedio de eventos introducidos por hora en la cola del Centro de mensajes.
* **[!UICONTROL Incoming (event vol)]** : número de eventos introducidos en la cola del Centro de mensajería.
* **[!UICONTROL Outgoing (throughput msg/h)]** : número promedio por hora de eventos del Centro de mensajería salientes correctos (por envío).
* **[!UICONTROL Outgoing (msg vol)]** : número de eventos de Centro de mensajería salientes correctos (por envío).
* **[!UICONTROL Average sending time (seconds)]** : tiempo promedio empleado en el Centro de mensajería para los eventos procesados correctamente. El cálculo toma en cuenta el tiempo de procesamiento y el tiempo de envío de mta.
* **[!UICONTROL Error rate]**: número de eventos con errores comparados con el número de eventos que se han introducido en la cola del Centro de mensajes. Los siguientes errores se tienen en cuenta: error de enrutamiento, evento caducado (evento que ha estado en la cola demasiado tiempo), error de envío, omitido por la entrega (cuarentena, etc.).

>[!NOTE]
>
>Los umbrales del indicador de advertencia (naranja) y alerta (rojo) pueden configurarse en el asistente de implementación. Consulte [Umbrales de monitorización](../../message-center/using/additional-configurations.md#monitoring-thresholds).
