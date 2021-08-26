---
product: campaign
title: Problemas de registros de seguimiento
description: Problemas de registros de seguimiento
audience: production
content-type: reference
topic-tags: troubleshooting
exl-id: 58656aa1-aa95-451f-80b8-9e2d28223056
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '69'
ht-degree: 13%

---

# Problemas de registros de seguimiento{#tracking-logs-issues}

![](../../assets/v7-only.svg)

Puede haber varias razones para que los registros de seguimiento no se reenvíen. Le recomendamos que compruebe la siguiente información:

* **¿Tiene errores el flujo de****trabajo de seguimiento?**

   Consulte [Monitorización de flujos de trabajo técnicos](../../workflow/using/monitoring-technical-workflows.md).

   ![](assets/tracking_scheduled_task.png)

* **¿El módulo****trackinglogdrunning está en el servidor?**

   Consulte [Archivos de registro](../../production/using/log-files.md).

* **¿Se han realizado cambios?**

   Pueden causar la pérdida de conexión con los servidores mediante el alias de seguimiento.
