---
solution: Campaign Classic
product: campaign
title: Problemas de registro de seguimiento
description: Problemas de registro de seguimiento
audience: production
content-type: reference
topic-tags: troubleshooting
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '69'
ht-degree: 13%

---


# Problemas de registro de seguimiento{#tracking-logs-issues}

Puede haber varias razones para que no se reenvíen los registros de seguimiento. Le recomendamos que compruebe la siguiente información:

* ¿Tiene errores el flujo de trabajo **Tracking**?

   Consulte [flujos de trabajo técnicos de monitoreo](../../workflow/using/monitoring-technical-workflows.md).

   ![](assets/tracking_scheduled_task.png)

* ¿Se está ejecutando el módulo **trackinglogd** en el servidor?

   Consulte [Archivos de registro](../../production/using/log-files.md).

* ¿Se han realizado cambios? Pueden desencadenar una pérdida de conexión con los servidores mediante el alias de seguimiento.

