---
product: campaign
title: Arquitectura
description: Un módulo específico gestiona los flujos de trabajo. Este módulo se puede iniciar en varios servidores para compartir la carga de procesamiento
badge-v7-only: label="v7" type="Informative" tooltip="Se aplica solo a Campaign Classic v7"
feature: Workflows
exl-id: 46801f78-706c-4dfa-bce7-3d15f569f222
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: tm+mt
source-wordcount: '123'
ht-degree: 100%

---

# Arquitectura {#architecture}



Los flujos de trabajo se gestionan mediante un módulo específico. Este módulo se puede iniciar en varios servidores para compartir la carga de procesamiento.

![](assets/architecture.png)

* El proceso “Workflow Instance Runner” (runwf) ejecuta todas las tareas de una instancia de flujo de trabajo determinada. Cuando no hay tareas para ejecutar, se vuelve “pasivo”, es decir, guarda su estado en la base de datos y se detiene.
* El módulo “Workflow Server” (wfserver) supervisa las instancias de flujo de trabajo actuales. Cuando hay una tarea para realizar, este módulo crea un proceso para activar (o reactivar) la instancia correspondiente.
