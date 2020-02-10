---
title: Gestión de los recursos de marketing
seo-title: Gestión de los recursos de marketing
description: Gestión de los recursos de marketing
seo-description: null
page-status-flag: never-activated
uuid: 35333bcb-0749-45b1-98ab-d5de6d91861c
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: campaign
content-type: reference
topic-tags: tasks--resources-and-budgets
discoiquuid: 069dbc6b-4019-4d66-85a8-0e4de6b66f18
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: e09692e316a92a67632201e5691e8b4df42cc341

---


# Gestión de los recursos de marketing{#managing-marketing-resources}

Adobe Campaign le permite administrar y hacer un seguimiento de los recursos de marketing implicados en el ciclo de vida de la campaña. Estos recursos de marketing pueden ser un folleto, una ayuda visual o cualquier otro medio de comunicación que implique varios operadores.

Puede rastrear el estado y el historial de cualquier recurso de marketing gestionado por Adobe Campaign en cualquier momento y consultar la versión actual.

## Adición de un recurso de marketing {#adding-a-marketing-resource}

Se accede a los recursos de marketing a través del entorno de Campaign.

To add a resource, click the **[!UICONTROL Create]** button.

![](assets/s_ncs_user_mkg_resource_add.png)

Para que un recurso esté disponible en el servidor de Adobe Campaign, debe agregar el recurso deseado arrastrándolo y soltarlo en el área central del editor. También puede hacer clic en el **[!UICONTROL Upload file to server...]** vínculo.

![](assets/s_ncs_user_mkg_resource_file.png)

Un mensaje de confirmación le permite iniciar la carga.

Una vez completada la carga, el recurso se añade a la lista de recursos disponibles. Los operadores de Adobe Campaign pueden acceder a él. They can view it (via the **[!UICONTROL Preview]** tab), make a copy to modify it, or update the file on the server (using the **[!UICONTROL Edit]** tab).

![](assets/s_ncs_user_mkg_resource_extract.png)

Click the **[!UICONTROL General]** tab to select the operators or groups of operators in charge of monitoring, tracking and approving this resource. Selecting the reviewer is done via the **[!UICONTROL Advanced parameters]** link.

* El operador al que se asigna el recurso es responsable de su seguimiento.
* El operador encargado de la aprobación es responsable de aprobar el recurso de marketing. Se le notifica cuando se inicie el proceso de validación de recursos.

   If no reviewer is selected, the resource **[!UICONTROL cannot be]** subject to approval.

* Si es necesario, también puede especificar un corrector.

Puede especificar una fecha de disponibilidad (orientativa) para el recurso. Beyond this date, it will appear with **[!UICONTROL Late]** status.

## Trabajo en colaboración sobre los recursos {#collaborative-work-on-resources}

Puede modificar y actualizar un recurso de marketing y, si fuera necesario, informar a otros operadores de Adobe Campaign al respecto. Se puede:

* Descargar el recurso de forma local para modificarlo.
* Actualizar el archivo en el servidor y facilitar el acceso a él a otros operadores.
* Bloquee un recurso para evitar que otros operadores lo modifiquen.

>[!NOTE]
>
>The **[!UICONTROL History]** tab contains the download and update log for the resource. The **[!UICONTROL Details]** button lets you view the selected version:

### Bloqueo/desbloqueo de un recurso {#locking-unlocking-a-resource}

Una vez creados, los recursos están disponibles en el panel de recursos de marketing y los operadores pueden editarlos y modificarlos.

Cuando un operador desea trabajar con un recurso, es preferible bloquearlo antes de iniciar el trabajo para evitar que otros operadores lo modifiquen al mismo tiempo. A continuación, el recurso se reserva; permanece accesible, pero el resto de operadores no lo pueden publicar ni actualizar en el servidor.

Un mensaje especial notifica a los operadores que intentan acceder a él:

![](assets/s_ncs_user_mkg_resource_locked.png)

The **[!UICONTROL Tracking]** tab indicates the name of the operator who locked the resource and the planned update date.

![](assets/s_ncs_user_mkg_resource_locked_date.png)

To lock a resource, you must click the resource followed by the **[!UICONTROL Lock]** button in the resource dashboard.

![](assets/s_ncs_user_mkg_resource_lock.png)

You can indicate the planned return date in the **[!UICONTROL Tracking]** tab of the resource.

![](assets/s_ncs_user_mkg_resource_lock_date.png)

Esta información le permite informar a otros operadores de Adobe Campaign de la fecha en que pretende desbloquear el recurso.

Cuando el recurso se ha actualizado, se desbloquea automáticamente y se pone a disposición de todos los operadores.

Si es necesario, también puede desbloquearlo manualmente desde el panel.

>[!NOTE]
>
>Solo el operador que ha bloqueado el recurso y los operadores con derechos de administrador están autorizados a desbloquear un recurso.

### Foros de debate {#discussion-forums}

For each resource, the **[!UICONTROL Forum]** tab lets participants exchange information.

[Los foros](../../campaign/using/discussion-forums.md) de discusión explican cómo funcionan los foros de discusión en Adobe Campaign.

## Ciclo de vida de un recurso de marketing {#life-cycle-of-a-marketing-resource}

Cuando se crea el recurso, los operadores de Adobe Campaign tienen la función de diseñar, corregir, aprobar y publicar el recurso. Se puede determinar una duración para estas campañas.

The **[!UICONTROL Tracking]** tab lets you monitor any actions carried out on the resource: approvals, approval refusals, related comments, or publications.

The **[!UICONTROL History]** tab displays file transfers carried out for this resource.

### Proceso de aprobación {#approval-process}

The expected availability date is displayed in the resource details, if it was specified in the **[!UICONTROL Tracking]** tab. Once this date is reached, you can execute the approval process using the **[!UICONTROL Submit for approval]** button in the resource dashboard. A continuación, el estado del recurso cambia a **[!UICONTROL Approval in progress]**.

A resource can be approved via the **[!UICONTROL Approve resource]** button on its dashboard.

![](assets/s_ncs_user_task_valid_date.png)

Los operadores autorizados pueden aceptar o rechazar la aprobación. This action is possible either: via the email message sent (by clicking the link in the notification message) or via the console (by clicking the **[!UICONTROL Approve]** ) button.

La ventana de aprobación permite introducir un comentario.

![](assets/s_ncs_user_mkg_resource_valid_ok.png)

The **[!UICONTROL Tracking]** tab enables all operators to track the various stages of the approval process.

![](assets/s_ncs_user_mkg_resource_log.png)

>[!NOTE]
>
>Además del revisor designado para cada recurso de marketing, los operadores con derechos de administrador y el gestor de recursos tienen autorización para aprobar un recurso de marketing.

### Publicación de un recurso {#publishing-a-resource}

Cuando se aprueba, el recurso de marketing debe publicarse. El proceso de publicación debe estar sujeto a una implementación específica según los requisitos de la empresa. Esto significa que los recursos se pueden publicar en una extranet o en cualquier otro servidor, se puede enviar información específica a un proveedor de servicios externos, etc.

To publish a resource, click the **[!UICONTROL Publish]** button in the editing zone of the marketing resource dashboard.

![](assets/s_ncs_user_mkg_resource_available.png)

También puede automatizar la publicación de un recurso mediante un flujo de trabajo.

La publicación de un recurso implica que está disponible para su uso (por ejemplo, por otra tarea). La publicación como tal varía según la naturaleza del recurso: para un folleto, la publicación puede significar el envío del archivo a una imprenta; para una agencia web, puede significar publicarlo en un sitio web, etc.

Para que Adobe Campaign publique, se debe crear un flujo de trabajo adecuado y vincularlo al recurso. To do this, open the **[!UICONTROL Advanced settings]** box of the resource, then select the desired workflow in the **[!UICONTROL Post-processing]** field.

![](assets/mrm_asset_postprocessing_workflow.png)

Esto hace que se ejecute el flujo de trabajo:

* When the reviewer clicks the **[!UICONTROL Publish resource]** link (or, if no reviewer was defined, the person in charge of the resource).
* If the resource is managed via a marketing resource creation task, it will be executed when the task is set to **[!UICONTROL Finished]**, as long as the **[!UICONTROL Publish the marketing resource]** box is checked in the task (Refer to [Marketing resource creation task](../../campaign/using/creating-and-managing-tasks.md#marketing-resource-creation-task))

If a workflow isn&#39;t started immediately (if the workflow is stopped for instance), the status of the resource changes to **[!UICONTROL Pending publication]**. Once the workflow is started, the status of the resource changes to **[!UICONTROL Published]**. Este estado no tiene en cuenta los posibles errores en el proceso de publicación. Compruebe el estado del flujo de trabajo para asegurarse de que se ha ejecutado correctamente.

## Vinculación de recursos a una campaña {#linking-a-resource-to-a-campaign}

### Referencia a un recurso de marketing {#referencing-a-marketing-resource}

Los recursos de marketing se pueden asociar a las campañas, siempre y cuando esta característica se haya seleccionado en la plantilla de campaña.

>[!NOTE]
>
>For details on how to create and configure campaign templates, refer to [Campaign templates](../../campaign/using/marketing-campaign-templates.md#campaign-templates).

Click the **[!UICONTROL Documents > Resources]** tab in the campaign dashboard, then click **[!UICONTROL Add]** to select the resource concerned.

![](assets/s_ncs_user_mkg_resource_ref.png)

Puede filtrar los recursos por estado, naturaleza o tipo, o aplicar un filtro personalizado.

![](assets/s_ncs_user_mkg_resource_ref_filter.png)

Click **[!UICONTROL OK]** to add the resource to the list of marketing resources referenced for this campaign.

The **[!UICONTROL Details]** button lets you edit and view it.

Los recursos añadidos se muestran en el panel. También pueden editarse desde allí.

### Agregar un recurso de marketing a una descripción de envío {#adding-a-marketing-resource-to-a-delivery-outline}

Los recursos de marketing se pueden asociar a los envíos a través de las descripciones de envío.

![](assets/s_ncs_user_mkg_resource_in_compo.png)

>[!NOTE]
>
>Para obtener más información sobre los esquemas de entrega, consulte [Asociación y estructuración de recursos vinculados a través de un esquema](../../campaign/using/marketing-campaign-deliveries.md#associating-and-structuring-resources-linked-via-a-delivery-outline)de entrega.

## Gestión de existencias {#stock-management}

Puede asociar un recurso de marketing con uno o más inventarios de existencias para administrar los suministros y mostrar una advertencia en el panel de control en caso de que no haya existencias suficientes.

>[!NOTE]
>
>For more information on stock management in Adobe Campaign, refer to [Stock management](../../campaign/using/providers--stocks-and-budgets.md#stock-management).

Para asociar un recurso de marketing a un inventario de existencias, edite la asignación de existencias y edite o cree un inventario. Añada una línea de acción y seleccione el recurso de marketing correspondiente.

![](assets/s_ncs_user_task_in_a_stock.png)

If necessary, you can edit the selected resource via the **[!UICONTROL Edit the link]** icon (magnifying glass) located to the right of the resource once it has been selected.

Especifique las existencias iniciales y las existencias de advertencia y, a continuación, guárdelo.

Las existencias se indican en los detalles del recurso.

![](assets/s_ncs_user_task_with_a_stock.png)

Si no es suficiente, se envía una advertencia a los operadores correspondientes.

## Funciones avanzadas {#advanced-functions}

El panel de control de marketing permite realizar operaciones de los tipos habituales: agregar, editar, bloquear/desbloquear, aprobar, publicar. Puede crear otros tipos de recursos de marketing y acceder a funciones avanzadas a través del árbol de Adobe Campaign. To do this, click **[!UICONTROL Explorer]** in the Adobe Campaign home page.

By default, marketing resources are stored in the **[!UICONTROL MRM > Marketing resources]** node of the tree.

![](assets/s_ncs_user_mkg_resource_create_from_list.png)

Puede añadir los siguientes recursos desde esta vista:

* Archivo
* HTML
* Texto
* URL

