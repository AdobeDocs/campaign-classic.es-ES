---
title: Tiempo de procesamiento del centro de mensajería
seo-title: Tiempo de procesamiento del centro de mensajería
description: Tiempo de procesamiento del centro de mensajería
seo-description: null
page-status-flag: never-activated
uuid: 06aca2c2-33c0-4839-bee4-fd838c49ce76
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: message-center
content-type: reference
topic-tags: reports
discoiquuid: d1f591d2-95e8-4d99-bc60-955c96b532eb
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 20f835c357d016643ea1f3209ee4dfb6d3239f90

---


# Tiempo de procesamiento del centro de mensajería{#message-center-processing-time}

Este informe muestra los indicadores principales relacionados con la cola de tiempo real. This report, aimed at technical administrators, can also be accessed via the **[!UICONTROL Monitoring]** universe in the control instance.

![](assets/mc_reports_2.png)

Just like for the **[!UICONTROL Message Center service level]** report, you can choose to display the overall statistics or those relative to a particular execution instance. También puede filtrar los datos por canal y por un período específico. The indicators displayed in the **[!UICONTROL Indicators over the period]** section are calculated over the period selected:

* **[!UICONTROL Average queuing time]** :: el tiempo promedio que los eventos procesados correctamente se emplean en el Centro de mensajes. Solo se tiene en cuenta el tiempo de procesamiento.
* **[!UICONTROL Average message sending time (s)]** :: el tiempo promedio que los eventos procesados correctamente se emplean en el Centro de mensajes. Solo se tiene en cuenta el tiempo de envío de mta.
* **[!UICONTROL Average processing time (s)]** :: el tiempo promedio que los eventos procesados correctamente se emplean en el Centro de mensajes. El cálculo toma en cuenta el tiempo de procesamiento y el tiempo de envío de mta.
* **[!UICONTROL Maximum number of queued events]** :: número máximo de eventos presentes en la cola del centro de mensajes en un momento determinado.
* **[!UICONTROL Minimum number of queued events]** :: número mínimo de eventos presentes en la cola del centro de mensajes en un momento determinado.
* **[!UICONTROL Average number of queued events]** :: número promedio de eventos presentes en la cola del centro de mensajes en un momento determinado.

>[!NOTE]
>
>Los umbrales de los indicadores de advertencia (naranja) y alerta (rojo) pueden configurarse en el Asistente para la implementación de Adobe Campaign. Consulte los umbrales [de monitoreo](../../message-center/using/monitoring-thresholds.md).

