---
title: Subflujo de trabajo
seo-title: Subflujo de trabajo
description: Subflujo de trabajo
seo-description: null
page-status-flag: never-activated
uuid: c952633f-1aca-44cf-bb50-a67e9b086030
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: workflow
content-type: reference
topic-tags: flow-control-activities
discoiquuid: a4441820-1b3d-4bac-a6e3-1c9c14466d19
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: c10a0a11c6e9952aa47da1f7a15188c79c62508d

---


# Subflujo de trabajo{#sub-workflow}

The **[!UICONTROL Sub-workflow]** activity lets you trigger the execution of another workflow and recover the result. Esta actividad permite utilizar flujos de trabajo complejos mientras se utiliza una interfaz simplificada.

Puede activar varios subflujos de trabajo en un solo flujo de trabajo. Los subflujos de trabajo se ejecutan de forma sincrónica.

>[!NOTE]
>
>Para que el subflujo de trabajo se ejecute correctamente, solo 
          debe haber un único salto de tipo “llegada” con el número más bajo y un único salto de tipo de “inicio” con 
          el número más alto. Por ejemplo, si tiene un salto de tipo “inicio” con una prioridad de 1, 2 y 
          3, solo debe haber un salto de tipo “inicio” con una prioridad de 3.

1. Cree un flujo de trabajo que utilizará como subflujo de trabajo en 
          otro flujo de trabajo.
1. Insert a **[!UICONTROL Jump (end point)]** activity with a priority of 1 at the beginning of the workflow. Si tiene varios saltos del tipo “llegada”, 
            Adobe Campaign utilizará el salto de “llegada” con el número más bajo.

   Insert a **[!UICONTROL Jump (start point)]** activity with a priority of 2 at the end of the workflow. Si tiene varios saltos del tipo “inicio”, 
            Adobe Campaign utilizará el salto “inicio” con el número más alto.

   ![](assets/subworkflow_jumps.png)

   >[!NOTE]
   >
   >If the sub-workflow activity references a workflow with several **[!UICONTROL Jump]** activities, the sub-workflow is executed between the &quot;arrival&quot; type jump with the lowest number and the &quot;start&quot; type jump with the highest number.

1. Complete y guarde este “subflujo de trabajo”.
1. Crear un flujo de trabajo “maestro”.
1. Insert a **[!UICONTROL Sub-workflow]** activity and open it.
1. Select the workflow that you want to use from the **[!UICONTROL Workflow template]** drop-down list.

   ![](assets/subworkflow_selection.png)

1. También puede agregar un script de configuración para alterar el flujo de trabajo al que se hace referencia.
1. Haga clic **[!UICONTROL Ok]**. It will automatically create an outbound transition with the label of the **[!UICONTROL Jump (start point)]** activity from the selected workflow.

   ![](assets/subworkflow_outbound.png)

1. Ejecute el flujo de trabajo.

Once run, the workflow that was called as a sub-workflow is still in **[!UICONTROL Being edited]** status, which means the following:

* No puede hacer clic con el botón derecho en las transiciones para mostrar 
            el destino.
* No se puede mostrar el recuento de 
            poblaciones intermedias.
* Los registros se agregan en el flujo de trabajo “maestro” y se 
            etiquetan como “subflujo de trabajo”.

De hecho, este flujo de trabajo solo es una plantilla. Se crea un nuevo subflujo de trabajo 
        basado en esta plantilla cuando se activa desde el flujo de trabajo “maestro”.

## Parámetros de entrada (opcional) {#input-parameters--optional-}

* tableName
* esquema

Cada evento entrante debe especificar un objetivo definido por estos parámetros.

## Parámetros de salida {#output-parameters}

* tableName
* esquema
* recCount

Este conjunto de tres valores identifica la población objetivo de la consulta. **[!UICONTROL tableName]** es el nombre de la tabla que registra los identificadores de destino, **[!UICONTROL schema]** es el esquema de la población (normalmente nms:Recipiente) y **[!UICONTROL recCount]** es el número de elementos de la tabla.

* targetSchema

Este valor es el esquema de la tabla de trabajo. This parameter is valid for all transitions with **[!UICONTROL tableName]** and **[!UICONTROL schema]**.
