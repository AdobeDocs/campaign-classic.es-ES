---
title: Consulta incremental
seo-title: Consulta incremental
description: Consulta incremental
seo-description: null
page-status-flag: never-activated
uuid: 24d322e8-172c-4faa-8a1f-59085b390a76
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: workflow
content-type: reference
topic-tags: targeting-activities
discoiquuid: 31071cd2-7d97-4a4f-a6cc-5ac5b6178be5
index: y
internal: n
snippet: y
translation-type: ht
source-git-commit: c10a0a11c6e9952aa47da1f7a15188c79c62508d

---


# Consulta incremental{#incremental-query}

Una consulta incremental le permite seleccionar periódicamente un objetivo basado en un criterio, al mismo tiempo que excluye las personas que ya fueron destinadas por este criterio.

La población segmentada se almacena en la memoria por instancia de flujo de trabajo y por actividad, es decir, dos flujos de trabajo iniciados desde la misma plantilla no comparten el mismo registro. Por otro lado, dos tareas basadas en la misma consulta incremental para la misma instancia de flujo de trabajo utilizarán el mismo registro.

La consulta se define de la misma manera que para las consultas estándar (consulte [Creación de consultas](../../workflow/using/query.md#creating-a-query)), pero su ejecución está programada.

>[!CAUTION]
>
>Si el resultado de una consulta incremental es igual a **0** durante una de sus ejecuciones, el flujo de trabajo se detiene hasta la siguiente ejecución programada de la consulta. Por lo tanto, las transiciones y actividades que siguen a la consulta incremental no se procesan antes de la siguiente ejecución.

Para ello:

1. En la pestaña **[!UICONTROL Scheduling &amp; History]**, seleccione la opción **[!UICONTROL Schedule execution]** . La tarea permanece activa una vez que se ha creado y solo se activará en los tiempos especificados por la programación para ejecutar la consulta. Sin embargo, si la opción está desactivada, la consulta se ejecuta inmediatamente **y en una misma vez**.
1. Haga clic en el botón **[!UICONTROL Change]**.

   En la ventana **[!UICONTROL Schedule editing wizard]** puede configurar el tipo de frecuencia, la periodicidad del evento y el periodo de validez del evento.

   ![](assets/s_user_segmentation_wizard_11.png)

1. Haga clic en **[!UICONTROL Finish]** para guardar la programación.

   ![](assets/s_user_segmentation_wizard_valid.png)

1. La sección inferior de la pestaña **[!UICONTROL Scheduling &amp; History]** permite seleccionar el número de días que se deben tener en cuenta en el historial.

   ![](assets/edit_request_inc.png)

   * **[!UICONTROL History in days]**

      Los destinatarios ya seleccionados pueden registrarse un número máximo de días desde el día en que fueron seleccionados. Si este valor es cero, los destinatarios nunca se eliminan del registro.

   * **[!UICONTROL Keep history when starting]**

      Esta opción le permite no purgar el registro cuando la actividad está habilitada.

   * **[!UICONTROL SQL table name]**

      Este parámetro permite sobrecargar la tabla SQL predeterminada que contiene los datos del historial.

## Ejemplo de una consulta incremental: actualización de la lista trimestral {#example-of-an-incremental-query--quarterly-list-update}

En el siguiente ejemplo, se utiliza una consulta incremental para actualizar automáticamente una lista de destinatarios. Estos destinatarios están dirigidos como parte de campañas de marketing de temporada.

Como estas campañas se inician al comienzo de cada temporada para ofrecer actividades de deportes relevantes, estas listas se actualizan cada trimestre. Sin embargo, un destinatario solo debe ser identificado una vez cada 9 meses por esta campaña. Esto le permite espaciar la frecuencia con la que se puede seleccionar a un destinatario y ofrecerle actividades en diferentes estaciones a lo largo de los años.

![](assets/incremental_query_example.png)

1. Añade una consulta incremental así como una actividad de actualización de lista en un nuevo flujo de trabajo.
1. Configure la pestaña **[!UICONTROL Incremental query]** de la actividad según se especifica en [Creación de una consulta](../../workflow/using/query.md#creating-a-query).
1. Seleccione la pestaña **[!UICONTROL Scheduling &amp; History]** y luego especifique un historial de 270 días. Un destinatario que ya ha sido identificado ya no será objetivo durante un periodo de 270 días o aproximadamente 9 meses.

   A continuación, haga clic en el botón **[!UICONTROL Change...]**

1. Para asegurarse de que la lista se actualice antes del inicio de cada temporada, seleccione **[!UICONTROL Monthly]**.
1. En la pantalla siguiente, seleccione marzo, junio, septiembre y diciembre. Elija el día 20 del mes y elija a qué hora le gustaría iniciar el flujo de trabajo.
1. Seleccione el periodo de validez de la consulta. Por ejemplo, si desea que esta actividad esté activa de forma permanente, seleccione **[!UICONTROL Permanent validity]**.

   ![](assets/incremental_query_example_2.png)

1. Después de aprobar la consulta incremental, configure la actividad de actualización de lista como se explica en [Actualización de lista](../../workflow/using/list-update.md).

Por lo tanto, el flujo de trabajo se iniciará automáticamente justo antes del inicio de cada temporada. La lista se actualizará con nuevos destinatarios aptos para recibir las ofertas.

## Parámetros de salida {#output-parameters}

* tableName
* esquema
* recCount

Este conjunto de tres valores identifica la población objetivo de la consulta. **[!UICONTROL tableName]** es el nombre de la tabla que registra los identificadores de destinatario, **[!UICONTROL schema]** es el esquema de la población (normalmente nms:recipient) y **[!UICONTROL recCount]** es el número de elementos de la tabla.
