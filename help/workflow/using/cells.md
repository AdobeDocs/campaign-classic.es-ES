---
solution: Campaign Classic
product: campaign
title: Celdas
description: Celdas
audience: workflow
content-type: reference
topic-tags: targeting-activities
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
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
