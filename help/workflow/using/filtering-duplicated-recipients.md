---
title: Filtrado de destinatarios duplicados
description: Obtenga información sobre cómo filtrar destinatarios duplicados
page-status-flag: never-activated
uuid: 0556d53e-0fdf-47b3-b1e0-b52e85e0c662
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: workflow
content-type: reference
topic-tags: use-cases
discoiquuid: 7e5605c8-78f2-4011-b317-96a59c699848
translation-type: tm+mt
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: tm+mt
source-wordcount: '147'
ht-degree: 87%

---


# Filtrado de destinatarios duplicados {#filtering-duplicated-recipients}

En este ejemplo, deseamos filtrar los destinatarios que aparecen dos veces o más en una entrega para recuperar perfiles duplicados.

Para crear este ejemplo, aplique los pasos siguientes:

1. Arrastre y suelte una actividad **[!UICONTROL Query]** en un flujo de trabajo y ábrala.
1. Click **[!UICONTROL Edit query]** and set the target and filtering dimensions to **[!UICONTROL Recipients]**.

   ![](assets/query_recipients_1.png)

1. Defina la siguiente condición de filtro para segmentar al destinatario que existe en el registro de envíos. Elija **Registro de destinatarios de envío (broadlog)** en la columna **Expresión**, elija **existe como** en la columna **Operador**.

   ![](assets/query_recipients_2.png)

1. Defina la siguiente condición de filtro para dirigir su envío. Choose **[!UICONTROL Internal name]** in the Expression column and **[!UICONTROL equal to]** in the Operator column.
1. En la columna de valor, agregue el nombre interno de la entrega segmentado.

   ![](assets/query_recipients_3.png)

1. Con un operador **[!UICONTROL AND]**, repita las mismas operaciones para segmentar otros envíos.

   ![](assets/query_recipients_4.png)

La transición saliente contiene los destinatarios duplicados dirigidos en las entregas.
