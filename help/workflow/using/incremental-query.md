---
product: campaign
title: Consulta incremental
description: Descubra más información sobre la actividad del flujo de trabajo Consulta incremental
feature: Workflows, Targeting Activity
hide: true
exl-id: abc08232-1a92-41e8-90f1-02e0a673539b
TQID: https://experienceleague.adobe.com/RBw8ii57Yhf9IHnK9Q-v7zUqq0cJKx3JMuaS84w1Y7E
product_v2: id: dfc56824-e8b9-499e-85d4-21aedb507314
feature_v2: []
subfeature_v2: id: ee25c34b-ea50-427b-9369-ba0a160f7d70id: b5f0aaf4-1e48-400d-95ac-6eb3078cf22fid: d1110311-2ca4-442b-be37-088a6db845ee
source-git-commit: 38eab6b8da73163e4476e91c0ef73f25c3f57546
workflow-type: ht
source-wordcount: 355
ht-degree: 100%

---

# Consulta incremental{#incremental-query}



Una consulta incremental le permite seleccionar periódicamente un objetivo basado en un criterio, al mismo tiempo que excluye las personas que ya fueron destinadas por este criterio.

La población segmentada se almacena en la memoria por instancia de flujo de trabajo y por actividad, es decir, dos flujos de trabajo iniciados desde la misma plantilla no comparten el mismo registro. Por otro lado, dos tareas basadas en la misma consulta incremental para la misma instancia de flujo de trabajo utilizarán el mismo registro.

La consulta se define de la misma manera que para las consultas estándar, pero su ejecución está programada.

**Temas relacionados:**

* [Caso de uso: Actualización de lista trimestral con una consulta incremental](quarterly-list-update.md)
* [Creación de una consulta](query.md#creating-a-query)

>[!CAUTION]
>
>Si el resultado de una consulta incremental es igual a **0** durante una de sus ejecuciones, el flujo de trabajo se detiene hasta la siguiente ejecución programada de la consulta. Por lo tanto, las transiciones y actividades que siguen a la consulta incremental no se procesan antes de la siguiente ejecución.

Para ello:

1. En la pestaña **[!UICONTROL Scheduling & History]** , seleccione la opción **[!UICONTROL Schedule execution]** . La tarea permanece activa una vez que se ha creado y solo se activará en los tiempos especificados por la programación para ejecutar la consulta. Sin embargo, si la opción está desactivada, la consulta se ejecuta inmediatamente **y en una misma vez**.
1. Haga clic en el botón **[!UICONTROL Change]**.

   En la ventana **[!UICONTROL Schedule editing assistant]** puede configurar el tipo de frecuencia, la periodicidad del evento y el periodo de validez del evento.

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

Este conjunto de tres valores identifica la población objetivo de la consulta. **[!UICONTROL tableName]** es el nombre de la tabla que registra los identificadores de destinatario, **[!UICONTROL schema]** es el esquema de la población (normalmente, nms:recipient) y **[!UICONTROL recCount]** es el número de elementos de la tabla.
