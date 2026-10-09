---
product: campaign
title: Alerta
description: Alerta
feature: Workflows
hide: true
exl-id: 21698e85-7b58-4bde-bbd2-0ee06ac90307
TQID: 'https://experienceleague.adobe.com/xYCc-adlUMfkDNIPGbbYShSmFuwqURtqtnE79MYC-Ys'
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
source-wordcount: '84'
ht-degree: 100%
---
# Alerta{#alert}



Una actividad de **Alert** envía un mensaje a un grupo de operadores. Funciona del mismo modo que una actividad de aprobación, pero no se espera ninguna respuesta en este caso.

![](assets/edit_alerte.png)

Una alerta no es persistente y, por lo tanto, no es visible desde la consola. Los operadores del grupo asignado deben tener una dirección de correo electrónico completa para recibir la notificación. La configuración de esta actividad es similar a la de una **Approval**. La plantilla de entrega predeterminada utilizada para alertar a los operadores es &#39;alertAssignee&#39;.
