---
title: Aprobación local
seo-title: Aprobación local
description: Aprobación local
seo-description: null
page-status-flag: never-activated
uuid: 4de59c8a-e229-4c8d-acab-2b116cafb70b
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: workflow
content-type: reference
topic-tags: action-activities
discoiquuid: a223641e-93e1-42ef-bb6b-8e1a0f8f6a65
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: c10a0a11c6e9952aa47da1f7a15188c79c62508d

---


# Aprobación local{#local-approval}

When integrated into a targeting workflow, the **[!UICONTROL Local approval]** activity lets you set up a recipient approval process before the delivery is sent.

![](assets/local_validation_0.png)

>[!CAUTION]
>
>Para utilizar esta actividad, debe haber adquirido el módulo de Distributed Marketing, que es una opción de la campaña. Compruebe el acuerdo de licencia.

Para ver un ejemplo de la **[!UICONTROL Local approval]** actividad con una plantilla de distribución, consulte [Uso de la actividad](../../workflow/using/using-the-local-approval-activity.md)de aprobación local.

Start by entering a label for the activity and the **[!UICONTROL Action to execute]** field:

![](assets/local_validation_1.png)

* Select the **[!UICONTROL Target approval notification]** option to send a notification email to local supervisors before the delivery, asking them to approve the recipients assigned to them.

   ![](assets/local_validation_intro_2.png)

* **Incremental query**: permite realizar una consulta y planificar su ejecución. Consulte la sección Consulta [](../../workflow/using/incremental-query.md) incremental.

   ![](assets/local_validation_intro_3.png)

## Notificación de aprobación del objetivo {#target-approval-notification}

In this case, the **[!UICONTROL Local approval]** activity is placed between upstream targeting and the delivery:

![](assets/local_validation_2.png)

Los campos que se deben ingresar en caso de una notificación para la aprobación del objetivo son los siguientes:

![](assets/local_validation_3.png)

* **[!UICONTROL Distribution context]**:: seleccione la **[!UICONTROL Specified in the transition]** opción si está utilizando una actividad de **[!UICONTROL Split]** tipo para limitar la población objetivo. En este caso, la plantilla de distribución se introduce en la actividad dividida. If you are not limiting the targeted population, select the **[!UICONTROL Explicit]** option here and enter the distribution template in the **[!UICONTROL Data distribution]** field.

   Para obtener más información sobre la creación de una plantilla de distribución de datos, consulte [Limitación del número de registros de subconjuntos por distribución](../../workflow/using/split.md#limiting-the-number-of-subset-records-per-data-distribution)de datos.

* **[!UICONTROL Approval management]**

   * Seleccione la plantilla de envío y el asunto que se utilizará para la notificación por correo electrónico. Hay disponible una plantilla predeterminada: **[!UICONTROL Local approval notification]**. También puede añadir una descripción que aparecerá sobre las listas de destinatarios en las notificaciones de aprobación y comentarios.
   * Specify the **[!UICONTROL Approval type]** that corresponds to the approval deadline (date or deadline from the start of the approval). En esta fecha, el flujo de trabajo se inicia nuevamente y los destinatarios que no se hayan aprobado no se tienen en cuenta para los objetivos. Una vez enviadas las notificaciones, la actividad se pone en cola para que los supervisores locales puedan aprobar sus contactos.

      >[!NOTE]
      >
      >De forma predeterminada, cuando se inicia el proceso de aprobación, la actividad queda pendiente durante tres días.

      También puede añadir uno o más recordatorios para informarle a los supervisores locales que la fecha límite se acerca. Para ello, haga clic en el **[!UICONTROL Add a reminder]** vínculo.

* **[!UICONTROL Complementary set]**:: la **[!UICONTROL Generate complement]** opción le permite generar un segundo conjunto que incluye todos los objetivos no aprobados.

   >[!NOTE]
   >
   >Esta opción está desactivada de forma predeterminada.

## Informe de comentarios del envío {#delivery-feedback-report}

In this case, the **[!UICONTROL Local approval]** activity is placed after the delivery:

![](assets/local_validation_4.png)

En caso de un informe de comentarios del envío, se deben ingresar los siguientes campos:

![](assets/local_validation_workflow_4.png)

* Select the **[!UICONTROL Specified in the transition]** option if the delivery was entered during a previous activity. Select **[!UICONTROL Explicit]** to specify the delivery in the local approval activity.
* Seleccione la plantilla de envío y la finalidad del correo electrónico de notificación. Hay una plantilla predeterminada: **[!UICONTROL Local approval notification]**.

## Example: Approving a workflow delivery {#example--approving-a-workflow-delivery}

Este ejemplo muestra la configuración de un proceso de aprobación para un envío de flujo de trabajo. For more information about creating delivery workflows, refer to the [Example: delivery workflow](../../workflow/using/delivery.md#example--delivery-workflow) section.

Un operador puede aprobar un envío de una de las dos maneras siguientes: con la página web enlazada en el mensaje de correo electrónico o a través de la consola.

* Aprobación en la web

   El correo electrónico enviado a los operadores del grupo Administrador permite aprobar el objetivo del envío. El mensaje utiliza el texto definido y la expresión JavaScript se sustituye por el valor calculado (en este caso, “574”).

   Para aprobar el envío, haga clic en el enlace correspondiente e inicie sesión en la consola de Adobe Campaign.

   ![](assets/new-workflow-valid-webaccess.png)

   Make a choice and click the **[!UICONTROL Submit]** button.

   ![](assets/new-workflow-valid-webaccess-confirm.png)

* Aprobación mediante la consola

   In the tree structure, the **[!UICONTROL Administration > Production > Objects created automatically > Approvals pending]** node contains the list of tasks to be approved by the operator currently connected. La lista debe mostrar una línea. Haga doble clic en esta línea para responder. Se muestra la siguiente ventana:

![](assets/new-workflow-7.png)

Seleccione **Sí** y, a continuación, haga clic en **[!UICONTROL Approve]**. Un mensaje le informará de que la respuesta se ha registrado.

Vuelva a la pantalla de flujo de trabajo: Después de unos diez segundos, el diagrama se muestra de la siguiente manera:

![](assets/new-workflow-8.png)

The workflow has executed the **[!UICONTROL Delivery control]** task, which in this case means starting the delivery previously created. El flujo de trabajo ha finalizado sin errores.
