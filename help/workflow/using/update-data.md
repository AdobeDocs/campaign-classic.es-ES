---
title: Actualización de datos
seo-title: Actualización de datos
description: Actualización de datos
seo-description: null
page-status-flag: never-activated
uuid: 5f3ab7c8-175a-4b06-a50c-edc97b226e3c
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: workflow
content-type: reference
topic-tags: targeting-activities
discoiquuid: c94ce5b7-aa8a-4ea2-845d-68c9c7dc2a7b
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: c10a0a11c6e9952aa47da1f7a15188c79c62508d

---


# Actualización de datos{#update-data}

Una actividad del tipo **Update data** realiza una actualización masiva de los campos de la base de datos.

## Tipo de operación {#operation-type}

The **[!UICONTROL Operation type]** field lets you choose the process to be carried out on the data in the database:

* **[!UICONTROL Insert or update]**:: agregue datos o actualícelos si ya se han agregado.
* **[!UICONTROL Insert]**:: solo agregar datos.
* **[!UICONTROL Update]**:: solo actualizar datos.
* **[!UICONTROL Update and merge collections]**:: actualice los datos y elija un registro &quot;maestro&quot; y, a continuación, vincule los elementos vinculados a los duplicados de este registro maestro. Los duplicados se pueden eliminar sin crear elementos adjuntos huérfanos.
* **[!UICONTROL Delete]**:: eliminar datos.

![](assets/s_advuser_update_data_1.png)

The **[!UICONTROL Batch size]** field lets you select the number of inbound transition elements to be updated. Por ejemplo, si establece 500, se actualizarán los 500 primeros registros analizados.

## Identificación de registro {#record-identification}

Especifique cómo identificar los registros de la base de datos:

* If data entries relate to an existing targeting dimension, select the **[!UICONTROL By directly using the targeting dimension]** option and select it in the **[!UICONTROL Updated dimension]** field.

   You can display the fields for the selected dimension using the **[!UICONTROL Edit this link]** magnifying glass button.

* De lo contrario, especifique uno o más enlaces que permitan la identificación de los datos en la base de datos o use directamente las claves de reconciliación.

![](assets/s_advuser_update_data_2.png)

## Selección de los campos que se van a actualizar {#selecting-the-fields-to-be-updated}

Use the **[!UICONTROL Automatically associate fields with the same name]** option in order for Adobe Campaign to automatically identify the fields to be updated.

![](assets/s_advuser_update_data_3b.png)

You can also use the **[!UICONTROL Insert]** icon to manually select the database fields to be updated.

![](assets/s_advuser_update_data_3.png)

Seleccione todos los campos que desea actualizar y, si es necesario, agregue las condiciones según la actualización a realizar. Para ello, utilice la **[!UICONTROL Taken into account if]** columna. Las condiciones se aplican una tras la otra y se mantienen en el orden de la lista. Utilice las flechas de la derecha para cambiar el orden de las actualizaciones.

Puede utilizar el mismo campo de destino varias veces.

Within an **[!UICONTROL Insert or update]** operation, you can select the campaign to be applied, either individually or for each field. To do this, select the desired value in the **[!UICONTROL Operation]** column.

![](assets/s_advuser_update_data_5.png)

The **[!UICONTROL modifiedDate]**, **[!UICONTROL modifiedBy]**, **[!UICONTROL createdDate]** and **[!UICONTROL createdBy]** fields are updated automatically during data updates, unless their management mode is configured specifically in the field update table.

La actualización de registros solo se realiza en registros que contengan al menos una diferencia. Si los valores son iguales, no se realiza ninguna actualización.

The **[!UICONTROL Advanced parameters]** link lets you specify additional options to deal with updating data as well as managing duplicates. También puede:

* **[!UICONTROL Disable automatic key management]**.
* **[!UICONTROL Disable audit]**.
* **[!UICONTROL Empty the destination value if the source value is empty (NULL)]**. Esta opción está seleccionada de forma predeterminada.
* **[!UICONTROL Update all columns with matching names]**.
* Specify conditions that consider source elements using an expression in the **[!UICONTROL Enabled if]** field.
* Especifique condiciones que consideren duplicados mediante una expresión. If you check the **[!UICONTROL Ignore records which concern the same target]** option, only the first in the list of expressions will be considered.

**[!UICONTROL Generate an outbound transition]**

Crea una transición saliente que se activará al final de la ejecución. La actualización normalmente indica el final de un flujo de trabajo de objetivos, por lo que la opción no se activa de forma predeterminada.

**[!UICONTROL Generate an outbound transition for the rejects]**

Crea una transición saliente que contiene registros que no se han procesado correctamente después de la actualización (por ejemplo, si hay un duplicado). Por lo general, la actualización marca el final de un flujo de trabajo de objetivos y, por lo tanto, la opción no está activada de forma predeterminada.

## Actualización y combinación de colecciones {#updating-and-merging-collections}

La actualización de datos y la combinación de colecciones le permite actualizar los datos contenidos en un registro utilizando datos de uno o varios registros secundarios, con el objetivo de mantener solo uno si lo desea. Estas actualizaciones se gestionan mediante un conjunto de reglas.

>[!NOTE]
>
>Esta opción también permite procesar las referencias a registros secundarios desde las tablas de trabajo del flujo de trabajo (targetWorkflow), envíos (targetDelivery) y listas (targetList). Si es necesario, estos enlaces aparecen en la lista donde se seleccionan los campos y las colecciones.

1. Seleccione la **[!UICONTROL Update and merge collections]** operación.

   ![](assets/update_and_merge_collections1.png)

1. Seleccione el orden de prioridad de los enlaces. Esto permite identificar el registro principal. Los enlaces disponibles varían según la transición entrante.

   ![](assets/update_and_merge_collections2.png)

1. Seleccione las colecciones que se van a mover al registro principal y los campos que se van a actualizar.

   Introduzca las reglas que se aplican a estas una vez que se identifiquen uno o varios registros secundarios. Para ello, puede utilizar el generador de expresiones. Para obtener más información, consulte [esta sección](../../platform/using/defining-filter-conditions.md#building-expressions). Por ejemplo, si especifica que es el valor actualizado más recientemente de todos los registros que se deben conservar.

   A continuación introduzca las condiciones para tener en cuenta la regla.

   Finalmente, especifique el tipo de actualización que desea llevar a cabo. Por ejemplo, puede optar por eliminar los registros secundarios después de actualizar los datos.

   Por ejemplo, puede configurar la combinación de colecciones que contengan datos heterogéneos, como la lista de suscripciones de un destinatario. Con las reglas, también puede crear nuevos historiales de suscripciones a partir de suscripciones de registro secundario o incluso mover la lista de suscripciones de un registro secundario a un registro principal.

1. Specify the order in which you would like the secondary records to be processed, by selecting **[!UICONTROL Advanced parameters]** > **[!UICONTROL Duplicates]**.

   ![](assets/update_and_merge_collections3.png)

Los datos de los registros secundarios están asociados al registro principal si las reglas definidas son procedentes. Según el tipo de actualización seleccionada, los registros secundarios se pueden eliminar.

## Example: Update data following an enrichment {#example--update-data-following-an-enrichment}

El [Paso 2: La escritura de datos enriquecidos en la sección de tabla](../../workflow/using/creating-a-summary-list.md#step-2--writing-enriched-data-to-the--purchases--table) &quot;Compras&quot; del caso de uso que detalla la creación de una lista de recapitulación ofrece un ejemplo de una actualización de datos después de una actividad de enriquecimiento.

## Parámetros de entrada {#input-parameters}

* tableName
* esquema

Cada evento entrante debe especificar un objetivo definido por estos parámetros.
