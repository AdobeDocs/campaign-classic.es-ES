---
product: campaign
title: Celdas
description: Celdas
feature: Workflows, Targeting Activity
hide: true
exl-id: 7b562dba-7e4b-40a7-91db-7b9379de44ca
TQID: 'https://experienceleague.adobe.com/hYy1-NOxnpCxVNYLV4QfiLJPec0IAQ4NlNy6RM6pYjA'
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
  - id: ff84ab2f-a7c2-4ced-a3c8-5113f4348d99
    internal-label: Targeting Activity
topic_v2:
  - id: e0eb8757-182f-49f3-94a4-1587d16f5094
    internal-label: Personalization
  - id: eddd9b14-83bd-4ff4-9072-54a4a484abb7
    internal-label: Administration
source-git-commit: a43e591a565a18d79f583d975e3e812c5435b0c0
workflow-type: tm+mt
source-wordcount: '127'
ht-degree: 100%
---
# Celdas{#cells}



La actividad **[!UICONTROL Cells]** proporciona una vista de los distintos subconjuntos en forma de columnas de datos. Facilita la manipulación de subconjuntos y está diseñado para fomentar las posibilidades de personalización.

![](assets/wf_split_cells.png)

Esta actividad se puede configurar para que introduzca parámetros específicos basados en las necesidades del usuario. De forma predeterminada, el detalle de cada subconjunto se detalla en una ventana dedicada a través de las pestañas **[!UICONTROL Selection]** y **[!UICONTROL Advanced]**. En el ejemplo que se muestra a continuación, se ha modificado el formulario: se ha añadido una pestaña **[!UICONTROL Data]** para habilitar la asociación de una oferta y un nivel de prioridad para cada subconjunto.

![](assets/wf_split_cells_with_customization.png)

Para esta configuración, se ha añadido la siguiente información al formulario de flujo de trabajo (en el nodo **[!UICONTROL Administration > Configurations > Input forms]** del árbol de Adobe Campaign):

```
<container img="nms:miniatures/mini-enrich.png" label="Data">
                <input xpath="@code"/>
                <container xpath="select/node[@alias='@numTest']">
                  <input alwaysActive="true" expr="'long'" type="expr" xpath="@type"/>
                  <input alwaysActive="true" expr="'Priority'" type="expr" xpath="@label"/>
                  <input label="Priority" maxValue="12" minValue="0" type="number"
                         xpath="@value" xpathEditFromType="@type"/>
                </container>
                <container xpath="select/node[@alias='@test']">
                  <input alwaysActive="true" expr="'string'" type="expr" xpath="@type"/>
                  <input alwaysActive="true" expr="'Identifier'" type="expr" xpath="@label"/>
                  <input label="Cell identifier" xpath="@value"/>
                </container>
                <container xpath="select/node[@alias='linkTest']">
                  <input alwaysActive="true" expr="'link'" type="expr" xpath="@type"/>
                  <input alwaysActive="true" expr="'nms:offer'" type="expr" xpath="@dataType"/>
                  <input alwaysActive="true" expr="'Offre'" type="expr" xpath="@label"/>
                  <input computeStringAlias="@valueLabel" label="Offers" notifyPathList="@_cs|@valueLabel"
                         schema="nms:offer" type="linkEdit" xpath="@value"/>
                </container>
```

La personalización del formulario de entrada en Adobe Campaign está reservada para los usuarios expertos. Para obtener más información, consulte [esta sección](../../configuration/using/identifying-a-form.md).
