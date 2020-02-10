---
title: Problemas de registro de seguimiento
seo-title: Problemas de registro de seguimiento
description: Problemas de registro de seguimiento
seo-description: null
page-status-flag: never-activated
uuid: 996869c4-7ffe-4fcc-9555-1d8b65e93e87
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: production
content-type: reference
topic-tags: troubleshooting
discoiquuid: 1b9ff479-4847-408d-a5c2-9a164805081f
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: e1937c1ddcbde092a22f4fe8c50d3d72b02cfeed

---


# Problemas de registro de seguimiento{#tracking-logs-issues}

Puede haber varias razones para que no se reenvíen los registros de seguimiento. Le recomendamos que compruebe la siguiente información:

* ¿Tiene errores el flujo de trabajo **de seguimiento** ?

   Consulte [Monitoreo de flujos de trabajo](../../workflow/using/monitoring-technical-workflows.md)técnicos.

   ![](assets/tracking_scheduled_task.png)

* ¿El módulo **trackinglogd** se está ejecutando en el servidor?

   Consulte Archivos [de registro](../../production/using/log-files.md).

* ¿Se han realizado cambios? Pueden desencadenar una pérdida de conexión con los servidores mediante el alias de seguimiento.

