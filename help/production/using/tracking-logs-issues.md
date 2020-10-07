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
translation-type: tm+mt
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: tm+mt
source-wordcount: '72'
ht-degree: 16%

---


# Problemas de registro de seguimiento{#tracking-logs-issues}

Puede haber varias razones para que no se reenvíen los registros de seguimiento. Le recomendamos que compruebe la siguiente información:

* ¿Tiene errores el flujo de trabajo **de seguimiento** ?

   Consulte flujos de trabajo técnicos [de supervisión](../../workflow/using/monitoring-technical-workflows.md).

   ![](assets/tracking_scheduled_task.png)

* ¿El módulo **trackinglogd** se está ejecutando en el servidor?

   Consulte Archivos [de registro](../../production/using/log-files.md).

* ¿Se han realizado cambios? Pueden desencadenar una pérdida de conexión con los servidores mediante el alias de seguimiento.

