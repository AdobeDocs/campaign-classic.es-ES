---
product: campaign
title: SMS entrante
description: Descubra más información sobre la actividad del flujo de trabajo SMS entrante
feature: Workflows, Channels Activity
hide: true
exl-id: 94a9d50b-4ead-4815-8d12-942fa78b4e8a
TQID: 'https://experienceleague.adobe.com/D1sDFGhO5g6QdwAPz2DHToXtI2SPAk8PQrrTY8-3gYg'
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
    internal-label: Campaign
  - id: fd6e6e36-54e4-4f1a-96fc-1a750e400d50
    internal-label: Campaign Classic v7
feature_v2:
  - id: c5474392-5419-4296-9e41-f6f4ce4f6e9b
    internal-label: Administration
  - id: a658c786-869b-4194-a780-2594d663adda
    internal-label: Data management
subfeature_v2:
  - id: ee25c34b-ea50-427b-9369-ba0a160f7d70
    internal-label: HeatMap
  - id: b5f0aaf4-1e48-400d-95ac-6eb3078cf22f
    internal-label: Execution activities
  - id: d1110311-2ca4-442b-be37-088a6db845ee
    internal-label: Data Management activities
  - id: fcb46c0f-76e1-48bc-9dd0-fcf9d97526cf
    internal-label: Workflows
  - id: bce277d1-7efa-48d8-9a1b-b588bb45ba1c
    internal-label: Channels Activity
topic_v2:
  - id: eddd9b14-83bd-4ff4-9072-54a4a484abb7
    internal-label: Administration
source-git-commit: a43e591a565a18d79f583d975e3e812c5435b0c0
workflow-type: tm+mt
source-wordcount: '106'
ht-degree: 100%
---
# SMS entrantes {#inbound-sms}



La actividad de **SMS entrantes** permite descargar y procesar mensajes de texto desde una cuenta externa.

## Propiedades {#properties}

![](assets/sms_rec_edit.png)

La primera pestaña de la actividad de **Inbound SMS** permite introducir los parámetros de enrutamiento para mensajes SMS e introducir la secuencia de comandos que se ejecutará al recibir cada mensaje. La segunda pestaña le permite asignar una programación a la actividad y la tercera pestaña define las condiciones de caducidad de la actividad.

1. **[!UICONTROL SMS routing]**: Seleccione la cuenta externa que desea utilizar para la recuperación de SMS. Las cuentas externas se configuran en el nodo **[!UICONTROL Administration > Platform > External accounts]** del árbol.
1. **[!UICONTROL Script]**
1. **[!UICONTROL Schedule]**

   ![](assets/sms_rec_edit_2.png)

1. **[!UICONTROL Expiration]**

Las pestañas **[!UICONTROL Script]**, **[!UICONTROL Schedule]** y **[!UICONTROL Expiry]** se detallan en [Correos electrónicos entrantes](inbound-emails.md).
