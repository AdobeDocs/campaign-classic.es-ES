---
product: campaign
title: Arquitectura
description: Un módulo específico gestiona los flujos de trabajo. Este módulo se puede iniciar en varios servidores para compartir la carga de procesamiento
feature: Workflows
hide: true
exl-id: 46801f78-706c-4dfa-bce7-3d15f569f222
TQID: 'https://experienceleague.adobe.com/lQLXeSTFhKRCNhA9SdShd9Nyd1mbNt-KPa-XJw-6wAs'
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
    internal-label: Campaign
  - id: fd6e6e36-54e4-4f1a-96fc-1a750e400d50
    internal-label: Campaign Classic v7
feature_v2:
  - id: a658c786-869b-4194-a780-2594d663adda
    internal-label: Data management
  - id: c5474392-5419-4296-9e41-f6f4ce4f6e9b
    internal-label: Administration
subfeature_v2:
  - id: ee25c34b-ea50-427b-9369-ba0a160f7d70
    internal-label: HeatMap
  - id: b5f0aaf4-1e48-400d-95ac-6eb3078cf22f
    internal-label: Execution activities
  - id: d1110311-2ca4-442b-be37-088a6db845ee
    internal-label: Data Management activities
  - id: fcb46c0f-76e1-48bc-9dd0-fcf9d97526cf
    internal-label: Workflows
source-git-commit: 3e213ecc670d5a3cb8299c092ccbb5303858327d
workflow-type: tm+mt
source-wordcount: '116'
ht-degree: 100%
---
# Arquitectura {#architecture}



Los flujos de trabajo se gestionan mediante un módulo específico. Este módulo se puede iniciar en varios servidores para compartir la carga de procesamiento.

![](assets/architecture.png)

* El proceso “Workflow Instance Runner” (runwf) ejecuta todas las tareas de una instancia de flujo de trabajo determinada. Cuando no hay tareas para ejecutar, se vuelve “pasivo”, es decir, guarda su estado en la base de datos y se detiene.
* El módulo “Workflow Server” (wfserver) supervisa las instancias de flujo de trabajo actuales. Cuando hay una tarea para realizar, este módulo crea un proceso para activar (o reactivar) la instancia correspondiente.
