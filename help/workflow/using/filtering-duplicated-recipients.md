---
product: campaign
title: Filtro de destinatarios duplicados
description: Obtenga información sobre cómo filtrar destinatarios duplicados
feature: Workflows
hide: true
exl-id: 7cbabbae-375f-4336-9afa-6356f37a79d0
TQID: 'https://experienceleague.adobe.com/qsfiVfgYUq38VWmh5QEq87-WBwFGrc2iCSeAhjaKXbg'
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
    internal-label: Campaign
  - id: fd6e6e36-54e4-4f1a-96fc-1a750e400d50
    internal-label: Campaign Classic v7
feature_v2:
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
source-git-commit: a43e591a565a18d79f583d975e3e812c5435b0c0
workflow-type: tm+mt
source-wordcount: '147'
ht-degree: 100%
---
# Filtro de destinatarios duplicados {#filtering-duplicated-recipients}



En este ejemplo, deseamos filtrar los destinatarios que aparecen dos veces o más en una entrega para recuperar perfiles duplicados.

Para crear este ejemplo, aplique los pasos siguientes:

1. Arrastre y suelte una actividad **[!UICONTROL Query]** en un flujo de trabajo y ábrala.
1. Haga clic en **[!UICONTROL Edit query]** y configure las dimensiones de objetivo y filtrado en **[!UICONTROL Recipients]**.

   ![](assets/query_recipients_1.png)

1. Defina la siguiente condición de filtro para segmentar al destinatario que existe en el registro de envíos. Elija **Registro de destinatarios de envío (broadlog)** en la columna **Expresión**, elija **existe como** en la columna **Operador**.

   ![](assets/query_recipients_2.png)

1. Defina la siguiente condición de filtro para dirigir su envío. En la columna Expresión, elija **[!UICONTROL Internal name]** y luego, en la columna Operador, **[!UICONTROL equal to]** .
1. En la columna de valor, agregue el nombre interno de la entrega segmentado.

   ![](assets/query_recipients_3.png)

1. Con un operador **[!UICONTROL AND]**, repita las mismas operaciones para segmentar otros envíos.

   ![](assets/query_recipients_4.png)

La transición saliente contiene los destinatarios duplicados dirigidos en las entregas.
