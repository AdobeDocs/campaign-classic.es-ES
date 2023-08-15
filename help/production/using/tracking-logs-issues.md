---
product: campaign
title: Problemas de registros de seguimiento
description: Problemas de registros de seguimiento
feature: Monitoring
badge-v7-only: label="v7" type="Informative" tooltip="Se aplica solo a Campaign Classic v7"
audience: production
content-type: reference
topic-tags: troubleshooting
exl-id: 58656aa1-aa95-451f-80b8-9e2d28223056
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: tm+mt
source-wordcount: '76'
ht-degree: 21%

---

# Problemas de registros de seguimiento{#tracking-logs-issues}



Puede haber varias razones para que los registros de seguimiento no se reenvíen. Le recomendamos que compruebe la siguiente información:

* **¿El** Seguimiento **¿el flujo de trabajo tiene errores?**

  Consulte [Supervisión de flujos de trabajo técnicos](../../workflow/using/monitoring-technical-workflows.md).

  ![](assets/tracking_scheduled_task.png)

* **Es el módulo** trackinglogd **¿se está ejecutando en el servidor?**

  Consulte [Archivos de registro](../../production/using/log-files.md).

* **¿Se han realizado cambios?**

  Pueden almacenar en déclencheur una pérdida de conexión con los servidores mediante el alias de seguimiento.
