---
solution: Campaign Classic
product: campaign
title: Arquitectura
description: Un módulo específico gestiona los flujos de trabajo. Este módulo se puede iniciar en varios servidores para compartir la carga de procesamiento.
audience: workflow
content-type: reference
topic-tags: -general-operation
translation-type: ht
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: ht
source-wordcount: '116'
ht-degree: 100%

---


# Arquitectura {#architecture}

Los flujos de trabajo se gestionan mediante un módulo específico. Este módulo se puede iniciar en varios servidores para compartir la carga de procesamiento.

![](assets/architecture.png)

* El proceso “Workflow Instance Runner” (runwf) ejecuta todas las tareas de una instancia de flujo de trabajo determinada. Cuando no hay tareas para ejecutar, se vuelve “pasivo”, es decir, guarda su estado en la base de datos y se detiene.
* El módulo “Workflow Server” (wfserver) supervisa las instancias de flujo de trabajo actuales. Cuando hay una tarea para realizar, este módulo crea un proceso para activar (o reactivar) la instancia correspondiente.

