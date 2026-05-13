---
product: campaign
title: Problemas de registros de seguimiento
description: Problemas de registros de seguimiento
feature: Monitoring
audience: production
content-type: reference
topic-tags: troubleshooting
exl-id: 58656aa1-aa95-451f-80b8-9e2d28223056
TQID: https://experienceleague.adobe.com/9u8xqAINLPKmeptZOZf94Ms-GiEciCL4nFBaw7SjRss
product_v2: id: dfc56824-e8b9-499e-85d4-21aedb507314
topic_v2: id: c1579802-ddd4-4214-8a91-97b2066abe11
source-git-commit: 4c295c0dabae8aba298390a3da2422a3fa1219f9
workflow-type: tm+mt
source-wordcount: 81
ht-degree: 32%

---

# Problemas de registros de seguimiento{#tracking-logs-issues}



Puede haber varias razones para que los registros de seguimiento no se reenvíen. Le recomendamos que compruebe la siguiente información:

* **¿Tiene errores el flujo de trabajo** Tracking **?**

Consulte la [documentación de Campaign v8](https://experienceleague.adobe.com/docs/campaign/automation/workflows/monitoring-workflows/monitor-technical-workflows.html?lang=es){target="_blank"}.

![](assets/tracking_scheduled_task.png)

* **¿Se está ejecutando el módulo** trackinglogd **en el servidor?**

  Consulte [Archivos de registro](../../production/using/log-files.md).

* **¿Se han realizado cambios?**

  Pueden almacenar en déclencheur una pérdida de conexión con los servidores mediante el alias de seguimiento.
