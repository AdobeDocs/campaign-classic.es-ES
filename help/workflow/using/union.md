---
product: campaign
title: Unión
description: Descubra más información sobre la actividad del flujo de trabajo Unión
feature: Workflows, Targeting Activity
hide: true
exl-id: 1cda3146-c333-4743-a871-c44583b6e5b2
TQID: 'https://experienceleague.adobe.com/qgrHaoMQwEN1YVWXuRHPiCchaQSaiwW5HgVLWgpUymg'
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
  - id: ff84ab2f-a7c2-4ced-a3c8-5113f4348d99
    internal-label: Targeting Activity
source-git-commit: 3e213ecc670d5a3cb8299c092ccbb5303858327d
workflow-type: tm+mt
source-wordcount: '305'
ht-degree: 100%
---
# Unión{#union}



Una unión agrupa el resultado de varias actividades entrantes en un solo destino. El objetivo se crea con todos los resultados recibidos: por lo tanto, todas las actividades anteriores deben terminar para que se ejecute la unión.

![](assets/s_user_segmentation_union.png)

>[!NOTE]
>
>Para obtener más información sobre la configuración y el uso de la actividad de unión, consulte [Combinación de varios objetivos (Unión)](targeting-data.md#combining-several-targets--union-).

## Ejemplo de unión {#union-example}

En el ejemplo siguiente, los resultados de dos consultas se han combinado para actualizar la lista. Las dos consultas se dirigen a los destinatarios. Por lo tanto, los resultados se basan en la misma tabla.

1. Inserte una actividad de tipo **[!UICONTROL Union]** inmediatamente después de las dos consultas y antes de una actividad de tipo actualización de la lista y ábrala.
1. Puede introducir una etiqueta.
1. Seleccione el método de reconciliación **[!UICONTROL Keys only]** ya que, en este ejemplo, la población resultante de las consultas contiene datos coherentes.
1. Si agregó datos adicionales para las consultas, puede optar por mantener solamente los datos compartidos.
1. Si desea limitar el tamaño de la población final, marque la casilla **[!UICONTROL Limit size of generated population]**.

   Especifique este número final introduciendo el número máximo de destinatarios y seleccionando la consulta cuya población tendrá prioridad.

1. Apruebe la actividad de unión y configure la actividad de actualización de lista (consulte [Actualización de listas](list-update.md)).
1. Inicie el flujo de trabajo. El número de resultados se muestra y la lista definida en la actividad de actualización de lista se crea o actualiza. Esta lista contiene el conjunto de destinatarios para ambas consultas o, si corresponde, el número definido en el paso anterior.

   ![](assets/union_example.png)

## Parámetros de entrada {#input-parameters}

* tableName
* esquema

Cada evento entrante debe especificar un objetivo definido por estos parámetros.

## Parámetros de salida {#output-parameters}

* tableName
* esquema
* recCount

Este conjunto de tres valores identifica el destino resultante de la unión. **[!UICONTROL tableName]** es el nombre de la tabla que registra los identificadores de destinatario, **[!UICONTROL schema]** es el esquema de la población (normalmente, nms:recipient) y **[!UICONTROL recCount]** es el número de elementos de la tabla.

