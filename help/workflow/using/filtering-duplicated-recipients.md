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
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: cf7c90f0ea9fbce3a4fd53f24189617cbd33fc40

---


# Filtrado de destinatarios duplicados {#filtering-duplicated-recipients}

En este ejemplo, deseamos filtrar los destinatarios que aparecen dos veces o más en un envío para recuperar perfiles duplicados.

Para crear este ejemplo, aplique los pasos siguientes:

1. Drag and drop a **[!UICONTROL Query]** activity in a workflow and open the activity.
1. Click **[!UICONTROL Edit query]** and set the target and filtering dimensions to **[!UICONTROL Recipients]**.

   ![](assets/query_recipients_1.png)

1. Defina la siguiente condición de filtro para segmentar al destinatario que existe en el registro de envíos. Elija **Registro de destinatarios de envío (broadlog)** en la columna **Expresión**, elija **existe como** en la columna **Operador**.

   ![](assets/query_recipients_2.png)

1. Defina la siguiente condición de filtro para dirigir su envío. Choose **[!UICONTROL Internal name]** in the Expression column and **[!UICONTROL equal to]** in the Operator column.
1. En la columna de valor, agregue el nombre interno del envío segmentado.

   ![](assets/query_recipients_3.png)

1. With an **[!UICONTROL AND]** operator, repeat the same operations to target other deliveries.

   ![](assets/query_recipients_4.png)

La transición saliente contiene los destinatarios duplicados dirigidos en los envíos.
