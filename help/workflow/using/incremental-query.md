---
solution: Campaign Classic
product: campaign
title: Consulta incremental
description: Descubra más información sobre la actividad del flujo de trabajo Consulta incremental
audience: workflow
content-type: reference
topic-tags: targeting-activities
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '355'
ht-degree: 100%

---


# Consulta incremental{#incremental-query}

Una consulta incremental le permite seleccionar periódicamente un objetivo basado en un criterio, al mismo tiempo que excluye las personas que ya fueron destinadas por este criterio.

La población segmentada se almacena en la memoria por instancia de flujo de trabajo y por actividad, es decir, dos flujos de trabajo iniciados desde la misma plantilla no comparten el mismo registro. Por otro lado, dos tareas basadas en la misma consulta incremental para la misma instancia de flujo de trabajo utilizarán el mismo registro.

La consulta se define de la misma manera que para las consultas estándar, pero su ejecución está programada.

**Temas relacionados:**

* [Caso de uso: actualización de lista trimestral con una consulta incremental](../../workflow/using/quarterly-list-update.md)
* [Creación de consultas](../../workflow/using/query.md#creating-a-query)

>[!CAUTION]
>
>Si el resultado de una consulta incremental es igual a **0** durante una de sus ejecuciones, el flujo de trabajo se detiene hasta la siguiente ejecución programada de la consulta. Por lo tanto, las transiciones y actividades que siguen a la consulta incremental no se procesan antes de la siguiente ejecución.

Para ello:

1. En la pestaña **[!UICONTROL Scheduling & History]** , seleccione la opción **[!UICONTROL Schedule execution]** . La tarea permanece activa una vez que se ha creado y solo se activará en los tiempos especificados por la programación para ejecutar la consulta. Sin embargo, si la opción está desactivada, la consulta se ejecuta inmediatamente **y en una misma vez**.
1. Haga clic en el botón **[!UICONTROL Change]**.

   En la ventana **[!UICONTROL Schedule editing wizard]** puede configurar el tipo de frecuencia, la periodicidad del evento y el periodo de validez del evento.

   ![](assets/s_user_segmentation_wizard_11.png)

1. Haga clic en **[!UICONTROL Finish]** para guardar la programación.

   ![](assets/s_user_segmentation_wizard_valid.png)

1. La sección inferior de la pestaña **[!UICONTROL Scheduling & History]** permite seleccionar el número de días que se deben tener en cuenta en el historial.

   ![](assets/edit_request_inc.png)

   * **[!UICONTROL History in days]**

      Los destinatarios ya seleccionados pueden registrarse un número máximo de días desde el día en que fueron seleccionados. Si este valor es cero, los destinatarios nunca se eliminan del registro.

   * **[!UICONTROL Keep history when starting]**

      Esta opción le permite no purgar el registro cuando la actividad está habilitada.

   * **[!UICONTROL SQL table name]**

      Este parámetro permite sobrecargar la tabla SQL predeterminada que contiene los datos del historial.

## Parámetros de salida {#output-parameters}

* tableName
* esquema
* recCount

Este conjunto de tres valores identifica la población objetivo de la consulta. **[!UICONTROL tableName]** es el nombre de la tabla que registra los identificadores de destinatario, **[!UICONTROL schema]** es el esquema de la población (normalmente nms:recipient) y **[!UICONTROL recCount]** es el número de elementos de la tabla.
