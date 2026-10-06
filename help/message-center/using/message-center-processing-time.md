---
product: campaign
title: Tiempo de procesamiento del Centro de mensajería
description: Obtenga más información sobre el informe de tiempo de procesamiento del centro de mensajes
feature: Transactional Messaging, Message Center
audience: message-center
content-type: reference
topic-tags: reports
exl-id: c797fd94-0c8d-480b-b22a-1489ac331e77
TQID: 'https://experienceleague.adobe.com/nESBoEHC7YU0SO4yJ0rscDa3E-ePk6yNbPKzusER7C4'
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
    internal-label: Campaign
  - id: fd6e6e36-54e4-4f1a-96fc-1a750e400d50
    internal-label: Campaign Classic v7
feature_v2:
  - id: 6d358f27-4f3c-5ddf-9159-05192e672ba7
    internal-label: Message Center
  - id: a4671286-a59f-47e3-b97b-90627a1977d5
    internal-label: Communication channels
subfeature_v2:
  - id: d3b34fea-a110-482f-adb2-aae8d686bac8
    internal-label: Transactional messaging
source-git-commit: a43e591a565a18d79f583d975e3e812c5435b0c0
workflow-type: tm+mt
source-wordcount: '217'
ht-degree: 100%
---
# Tiempo de procesamiento del Centro de mensajería {#message-center-processing-time}



Este informe muestra los indicadores principales relacionados con la cola de tiempo real.

También se puede acceder a este informe, dirigido a los administradores técnicos, a través de la pestaña **[!UICONTROL Monitoring]** en la instancia de control.

![](assets/mc_reports_2.png)

Al igual que para el informe **[!UICONTROL Message Center service level]**, puede elegir mostrar las estadísticas generales o las relativas a una instancia de ejecución determinada. También puede filtrar los datos por canal y por un periodo específico.

Los indicadores que se muestran en la sección **[!UICONTROL Indicators over the period]** se calculan en el periodo seleccionado:

* **[!UICONTROL Average queuing time]**: el tiempo promedio que permanecen los eventos procesados correctamente en el Centro de mensajes. Solo se tiene en cuenta el tiempo de procesamiento.
* **[!UICONTROL Average message sending time (s)]**: el tiempo promedio que permanecen los eventos procesados correctamente en el Centro de mensajes. Solo se tiene en cuenta el tiempo de envío de mta.
* **[!UICONTROL Average processing time (s)]**: el tiempo promedio que permanecen los eventos procesados correctamente en el Centro de mensajes. El cálculo toma en cuenta el tiempo de procesamiento y el tiempo de envío de mta.
* **[!UICONTROL Maximum number of queued events]**: número máximo de eventos presentes en la cola del Centro de mensajes en un momento determinado.
* **[!UICONTROL Minimum number of queued events]**: número mínimo de eventos presentes en la cola del Centro de mensajes en un momento determinado.
* **[!UICONTROL Average number of queued events]**: número promedio de eventos presentes en la cola del Centro de mensajes en un momento determinado.

>[!NOTE]
>
>Los umbrales de los indicadores de advertencia (naranja) y alerta (rojo) pueden configurarse en el Asistente para la implementación de Adobe Campaign. Consulte [Umbrales de monitorización](../../message-center/using/additional-configurations.md#monitoring-thresholds).
