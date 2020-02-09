---
title: Aprobación
seo-title: Aprobación
description: Aprobación
seo-description: null
page-status-flag: never-activated
uuid: 49285790-5aa7-4e15-a657-42e4f78be518
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: workflow
content-type: reference
topic-tags: flow-control-activities
discoiquuid: a0090c78-5873-446d-8d5f-b0f94ff5d373
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 20f835c357d016643ea1f3209ee4dfb6d3239f90

---


# Aprobación{#approval}

Una tarea de **Approval** implica la participación de un operador. Al operador se le asigna una tarea y puede responder por correo electrónico, utilizando la página web vinculada en el mensaje del correo electrónico o a través de la consola.

## Asignación de tareas {#task-assignment}

De forma predeterminada, la aprobación se le asigna a un grupo de operadores. Este grupo representa una función, por ejemplo, un “grupo de contenido del boletín informativo” o “grupo de objetivos del boletín informativo”. Cada operador del grupo puede responder, pero solo se tiene en cuenta la primera respuesta (excepto en caso de varias aprobaciones).

Si es necesario, puede asignar la tarea de aprobación a un solo operador o a un conjunto de operadores definidos por un filtro.

* To select a single operator, select the **[!UICONTROL Operator]** value in the **[!UICONTROL Assignment type]** field and select the relevant operator in the drop-down list of the **[!UICONTROL Assignee]** field.

   ![](assets/s_advuser_validation_box_assign.png)

   >[!CAUTION]
   >
   >Sólo el operador elegido estará autorizado a aprobar la tarea.

* Puede definir una consulta para filtrar los operadores de aprobación. To do this, select the **[!UICONTROL Filter]** value in the **[!UICONTROL Assignment type]** field and click the **[!UICONTROL Advanced parameters...]** link to define filtering conditions, as shown in the following example:

   ![](assets/s_advuser_validation_box_filter.png)

En caso de una sola aprobación, la transición correspondiente a la opción de operador se activa y la tarea finaliza: los demás operadores no pueden responder.

En caso de varias aprobaciones, se activan las transiciones correspondientes a la opción de cada operador. La tarea finaliza cuando han respondido todos los operadores del grupo o si ha caducado la tarea.

Esta actividad no bloquea el procesamiento y el flujo de trabajo puede realizar otras tareas mientras espera una respuesta.

Un operador puede aprobar las tareas asignadas a dicho operador desde la consola. Un operador con derechos de administrador puede ver y eliminar las tareas asignadas a cualquier operador, pero no puede responder a ellas.

Modificar el título o el cuerpo del mensaje de la actividad no afecta a las tareas actuales, sino que modifica las posibles elecciones que directamente afectan a las tareas actuales, que heredan automáticamente la nueva lista de opciones.

**Se puede acceder a las tareas de tipo de aprobación** desde el **[!UICONTROL Administration > Production > Objects created automatically > Approvals pending]** nodo: los operadores pueden acceder directamente al formulario de aprobación a través de esta vista.

![](assets/s_advuser_validation_from_console.png)

## Propiedades {#properties}

Las variables personalizadas se pueden utilizar en el mensaje enviado a los revisores. Pueden insertarse en el título o en el cuerpo del mensaje.

![](assets/edit_validation.png)

Este **[!UICONTROL Title]** campo contiene el título del mensaje: Este es el asunto del mensaje de correo electrónico enviado. El título, así como el cuerpo del mensaje, son plantillas JavaScript y, por tanto, contienen valores calculados según el contexto del flujo de trabajo.

La sección inferior del editor permite definir la lista de posibles respuestas. Hay una transición correspondiente a cada respuesta. El nombre es el identificador interno y la etiqueta es el texto que se mostrará en la lista de opciones.

Click the **[!UICONTROL Advanced parameters...]** link to select the delivery template to be used to notify operators. La plantilla predeterminada (nombre interno &#39;notifyAssignee&#39;) toma el título y el mensaje y añade un enlace a la página web que se utiliza para responder.

Esta plantilla se puede modificar para personalizar el diseño del mensaje, pero es preferible realizar una copia. El mecanismo de objetivo (archivo externo, asignación de destino) no debe modificarse porque es necesario para que las notificaciones funcionen correctamente.

An approval example is shown in [Defining approvals](../../workflow/using/executing-a-workflow.md#defining-approvals).

## Parámetros de salida {#output-parameters}

* **[!UICONTROL response]**

   Comentario relacionado con la respuesta

* **[!UICONTROL responseOperator]**

   Identificador del operador que ha respondido. This field is a numerical value, but a **[!UICONTROL String]** field.

