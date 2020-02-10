---
title: Creación de un flujo de trabajo
seo-title: Creación de un flujo de trabajo
description: Creación de un flujo de trabajo
seo-description: null
page-status-flag: never-activated
uuid: 55743545-dd4b-4a0a-aeff-8fd638812b9d
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: workflow
content-type: reference
topic-tags: -general-operation
discoiquuid: 2d4ccf81-cd85-4f4c-8ba8-5b5612af1e16
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 1c86322fa95aee024f6c691b61a10c21a9a22eb7

---


# Creación de un flujo de trabajo {#building-a-workflow}

Esta sección detalla los principios fundamentales y las prácticas recomendadas para crear un flujo de trabajo en Campaign.

* Creación de un flujo de trabajo, consulte [Creación de un nuevo flujo de trabajo](#creating-a-new-workflow)
* Diseño del diagrama de flujo de trabajo, consulte [Adición y vinculación de actividades](#adding-and-linking-activities)
* Acceso a parámetros y propiedades de actividades, consulte [Configuración de actividades](#configuring-activities)
* Diseño de flujos de trabajo de objetivos, consulte [Flujos de trabajo de objetivo](#targeting-workflows)
* Uso del flujo de trabajo para ejecutar una campaña, consulte [Flujos de trabajo de campaña](#campaign-workflows)
* Acceso y creación de flujos de trabajo técnicos, consulte [Flujos de trabajo técnicos](#technical-workflows)
* Uso de plantillas para crear flujos de trabajo, consulte [Plantillas de flujo de trabajo](#workflow-templates)

## Creación de un flujo de trabajo nuevo {#creating-a-new-workflow}

From the **[!UICONTROL Explorer]**, access a workflow folder. De forma predeterminada, puede utilizar **[!UICONTROL Profiles and Targets]** > **[!UICONTROL Jobs]** > **[!UICONTROL Targeting workflows]**.

Click the **[!UICONTROL New]** button located above the list of workflows.

![](assets/create_a_wf_icon.png)

O bien, también puede utilizar el **[!UICONTROL Create]** botón en la descripción general del flujo de trabajo (**[!UICONTROL Monitoring]** > **[!UICONTROL Workflow]** vínculo).

![](assets/create_a_wf.png)

Enter a label and click **[!UICONTROL Save]**.

>[!NOTE]
>
>Cuando modifique el nombre interno de una actividad de flujo de trabajo o el propio flujo de trabajo, asegúrese de guardar el flujo de trabajo antes de cerrarlo para que el nuevo nombre interno se aplique correctamente.

## Adición y vinculación de actividades {#adding-and-linking-activities}

A continuación debe definir las distintas actividades y vincularlas todas en el diagrama. En esta fase de la configuración, podemos ver la etiqueta del diagrama y el estado del flujo de trabajo (edición en curso). La sección inferior de la ventana se utiliza para editar solo el diagrama. Contiene una barra de herramientas, una paleta de actividades (a la izquierda) y el diagrama (a la derecha).

![](assets/new-workflow-2.png)

>[!NOTE]
>
>Si no se muestra la paleta, haga clic en el primer botón de la barra de herramientas para mostrarla.

Las actividades se agrupan por categorías dentro de las diferentes pestañas de la paleta. Las pestañas y actividades disponibles pueden variar según el tipo de flujo de trabajo (técnico, de objetivos o flujo de trabajo de la campaña).

* La primera pestaña contiene actividades de establecimiento de objetivos y de manipulación de datos. Estas actividades se detallan en las actividades de [establecimiento de objetivos](../../workflow/using/about-targeting-activities.md).
* La segunda pestaña contiene las actividades de planificación, que se utilizan principalmente para coordinar otras actividades. Estas actividades se detallan en las actividades [de control de](../../workflow/using/about-flow-control-activities.md)flujo.
* La tercera pestaña contiene herramientas y acciones que se pueden utilizar en el flujo de trabajo. Estas actividades se detallan en las actividades [de acción](../../workflow/using/about-action-activities.md).
* La cuarta pestaña contiene actividades que dependen de un evento determinado, como la recepción de un correo electrónico o la llegada de un archivo en un servidor. Estas actividades se detallan en las actividades [del](../../workflow/using/about-event-activities.md)evento.

Creación del diagrama

1. Añada una actividad seleccionándola en la paleta y moviéndola al diagrama mediante una operación de arrastrar y soltar.

   En el diagrama, añada una actividad **Start** y luego una actividad **Delivery**.

   ![](assets/new-workflow-3.png)

1. Para vincular las actividades, arrastre la transición de la actividad **Start** y suéltela sobre la actividad **Delivery**.

   ![](assets/new-workflow-4.png)

   Puede enlazar automáticamente una actividad a la anterior colocando la nueva actividad al final de la transición.

1. Añada las actividades que necesita y vincúlelas como se muestra en el diagrama siguiente.

   ![](assets/new-workflow-5.png)

>[!CAUTION]
>
>Puede copiar y pegar actividades en un mismo flujo de trabajo. Sin embargo, no se recomienda copiar actividades de pegado en diferentes flujos de trabajo. Algunas opciones de configuración asociadas a actividades como Entregas y Programador podrían provocar conflictos y errores al ejecutar el flujo de trabajo de destino. En su lugar, le recomendamos que **duplique** los flujos de trabajo. Para obtener más información, consulte [Duplicar flujos de trabajo](#duplicating-workflows).

### Opciones de diseño adicionales {#additional-layout-options}

Puede cambiar la visualización y el diseño del gráfico mediante los siguientes elementos:

* **Uso de la barra de herramientas**

   La barra de herramientas de edición del diagrama le permite acceder a las funciones de diseño y ejecución del flujo de trabajo.

   ![](assets/s_user_segmentation_wizard_10.png)

   Esto le permite adaptar el diseño de la herramienta de edición: visualización de la paleta y descripción general, tamaño y alineación de los objetos gráficos.

   ![](assets/s_user_segmentation_toolbar.png)

   En esta [sección](../../campaign/using/marketing-campaign-deliveries.md#creating-a-targeting-workflow) se describen los iconos relacionados con el seguimiento y el inicio de un flujo de trabajo de objetivos avanzado.

* **Alineación de objetos**

   Para alinear iconos, selecciónelos y haga clic en el **[!UICONTROL Align vertically]** icono o **[!UICONTROL Align horizontally]** .

   Utilice la tecla **Ctrl** para seleccionar varias actividades separadas o para anular la selección de una o varias actividades. Haga clic en el fondo del diagrama para anular la selección de todo.

* **Gestión de imágenes**

   Puede personalizar la imagen de fondo del diagrama, así como las relacionadas con las distintas actividades. Consulte [Administración de imágenes](../../workflow/using/managing-activity-images.md)de actividad.

## Configuración de actividades {#configuring-activities}

Double-click an activity to configure it or right-click and select **[!UICONTROL Open...]**.

>[!NOTE]
>
>Las actividades de flujo de trabajo de Campaign se detallan en [esta sección](../../workflow/using/about-activities.md).

La primera pestaña contiene la configuración básica. The **[!UICONTROL Advanced]** tab contains the additional parameters, which are used particularly for defining behavior when an error is encountered, specifying the execution duration for an activity, and for entering an initialization script.

Para comprender mejor las actividades y mejorar la legibilidad del flujo de trabajo, se pueden introducir comentarios en las actividades, que se muestran automáticamente cuando los operadores se desplazan por la actividad.

![](assets/example1-comment.png)

## Flujos de trabajo de objetivos {#targeting-workflows}

Los flujos de trabajo de objetivos permiten crear varios objetivos de envío. Gracias a las actividades de flujo de trabajo, se pueden crear consultas, definir enlaces o exclusiones basadas en criterios específicos y añadir planificaciones. El resultado de esta dirección se puede transferir automáticamente a una lista que pueda servir como objetivo de las acciones de envío.

Además de estas actividades, la gestión de datos permite manipular dichos datos y acceder a funciones avanzadas para satisfacer problemas complejos relacionados con los objetivos. For more on this, refer to [Data Management](../../workflow/using/targeting-data.md#data-management).

Todas estas actividades se encuentran en la primera pestaña del flujo de trabajo.

>[!NOTE]
>
>Las actividades de segmentación se describen en esta [página](../../workflow/using/about-activities.md).

Targeting workflows can be created and edited via the **[!UICONTROL Profiles and Targets > Jobs > Targeting workflows]** node of the Adobe Campaign tree or via the **[!UICONTROL Profiles and Targets > Targeting workflows]** menu of the home page.

![](assets/target_wf.png)

Dentro del marco de una campaña, los flujos de trabajo de objetivos se almacenan con todos los flujos de trabajo de la campaña.

### Pasos de implementación {#implementation-steps-}

Las fases de creación de datos de destino son las siguientes:

1. For identifying data in the database, refer to [Creating queries](../../workflow/using/targeting-data.md#creating-queries).
1. Para preparar los datos para satisfacer las necesidades de entrega, consulte [Enriquecimiento y modificación de datos](../../workflow/using/targeting-data.md#enriching-and-modifying-data).
1. For using data to perform updates or within a delivery, refer to [Updating the database](../../workflow/using/how-to-use-workflow-data.md#updating-the-database).

Los resultados de todos los enriquecimientos y todas las gestiones realizadas durante el establecimiento de objetivos se almacenan y están accesibles en los campos personalizados, en particular para utilizarlos al crear mensajes personalizados. For more on this, refer to [Target data](../../workflow/using/executing-a-workflow.md#target-data)

### Establecimiento de objetivos y filtrado de dimensiones {#targeting-and-filtering-dimensions}

Durante las operaciones de segmentación de datos, la clave de establecimiento de objetivos se asigna a una dimensión de filtrado. La dimensión objetivo permite definir la población objetivo de la operación: destinatarios, beneficiarios de contratos, operadores, suscriptores, etc. La dimensión de filtrado permite seleccionar la población en función de determinados criterios: titulares de contrato, suscriptores a boletines, etc.

Por ejemplo, para seleccionar clientes que han tenido una póliza de seguro de vida durante más de 5 años, seleccione la siguiente dimensión de objetivo: **Clientes** y la siguiente dimensión de filtrado: **Titular** del contrato. Después, puede definir las condiciones de filtrado dentro de la actividad de consulta.

Durante la fase de selección de la dimensión objetivo, solo se ofrecen en la interfaz las dimensiones de filtrado compatibles.

Estas dos dimensiones deben estar vinculadas. Thus, the content of the **[!UICONTROL Filtering dimension]** list depends on the targeting dimension specified in the first field.

Por ejemplo, para los destinatarios (**recipient**), están disponibles las siguientes dimensiones de filtrado:

![](assets/query_filter_target_dimensions_1.png)

No obstante, para las **aplicaciones web**, la lista contiene las siguientes dimensiones de filtrado:

![](assets/query_filter_target_dimensions_2.png)

## Flujos de trabajo de la campaña {#campaign-workflows}

For each campaign, you can create workflows to be executed from the **[!UICONTROL Targeting and workflows]** tab. Estos flujos de trabajo son específicos de la campaña.

![](assets/wf-in-op-edit-delivery-tab.png)

Esta pestaña contiene las mismas actividades para todos los flujos de trabajo. They are presented in the [Implementation steps](#implementation-steps-) section.

Además de las campañas de destino, los flujos de trabajo de la campaña permiten crear y configurar envíos de principio a fin para todos los canales disponibles. Una vez creados en el flujo de trabajo, estos envíos están disponibles en el panel de la campaña.

Todos los flujos de trabajo de campaña están centralizados bajo el **[!UICONTROL Administration > Production > Objects created automatically > Campaign workflows]** nodo.

![](assets/campaigns_wf.png)

En esta [página](../../campaign/using/marketing-campaign-deliveries.md#building-the-main-target-in-a-workflow) se describen los flujos de trabajo de campaña y algunos ejemplos de implementación.

## Flujos de trabajo técnicos {#technical-workflows}

Los flujos de trabajo técnicos se incluyen ya preparados con Adobe Campaign. Son operaciones o trabajos planificados para su ejecución periódica en el servidor. Permiten realizar el mantenimiento de la base de datos, enviar información de seguimiento sobre los envíos y configurar procesos provisionales relacionados con los envíos. Los flujos de trabajo técnicos se configuran mediante el **[!UICONTROL Administration > Production > Technical workflows]** nodo.

![](assets/navtree.png)

Hay plantillas nativas disponibles para crear flujos de trabajo técnicos. Se pueden configurar para adaptarlas a sus necesidades.

The **[!UICONTROL Campaign process]** subfolder centralizes the workflows required for executing processes within the campaigns: task notification, stock management, cost calculation, etc.

>[!NOTE]
>
>La lista de flujos de trabajo técnicos instalados con cada módulo está disponible en una [sección específica](../../workflow/using/about-technical-workflows.md).

You can create other technical workflows in the **[!UICONTROL Administration > Production > Technical workflows]** node of the tree structure. Sin embargo, este proceso está reservado para usuarios expertos.

Las actividades ofrecidas son las mismas que para los flujos de trabajo de objetivos. For more on this, refer to [Implementation steps](#implementation-steps-).

## Plantillas de flujo de trabajo {#workflow-templates}

Las plantillas de flujo de trabajo contienen la configuración general de las propiedades y posiblemente diversas actividades concatenadas dentro de un diagrama. Esta configuración se puede reutilizar para crear nuevos flujos de trabajo que contengan un determinado número de elementos preconfigurados

Puede crear nuevas plantillas de flujo de trabajo basadas en plantillas existentes o cambiar un flujo de trabajo en una plantilla directamente.

Workflow templates are stored in the **[!UICONTROL Resources > Templates > Workflow templates]** node of the Adobe Campaign tree.

![](assets/s_advuser_wf_template_tree.png)

Además de las propiedades habituales del flujo de trabajo, las propiedades de la plantilla permiten especificar el archivo de ejecución para los flujos de trabajo creados en función de esta plantilla.

![](assets/s_advuser_wf_template_properties.png)

## Duplicar flujos de trabajo {#duplicating-workflows}

Puede duplicar diferentes tipos de flujos de trabajo. Una vez duplicadas, las modificaciones del flujo de trabajo no se transfieren a la copia del flujo de trabajo.

>[!CAUTION]
>
>La función de copiar y pegar está disponible en los flujos de trabajo, pero le recomendamos que utilice **Duplicar**. Una vez copiada una actividad, se conserva toda su configuración. Para las actividades de entrega (correo electrónico, SMS, notificaciones push...), el objeto de entrega adjunto a la actividad también se copia, lo que puede provocar un bloqueo.

1. Haga clic con el botón secundario en un flujo de trabajo.
1. Haga clic en **Duplicar**.

   ![](assets/duplicate-workflows.png)

1. En la ventana de flujo de trabajo, cambie la etiqueta de flujo de trabajo.
1. Haga clic en **Save**.

La función duplicada no está directamente disponible en la vista de una campaña.

Sin embargo, puede crear una vista para mostrar todos los flujos de trabajo de la instancia. En esta vista, puede duplicar flujos de trabajo mediante **Duplicar para**.

**Primero, creemos una vista:**

1. En el **Explorador**, vaya a la carpeta en la que debe crear la vista.
1. Haga clic con el botón derecho y vaya a **Agregar una nueva carpeta** > **Proceso**, seleccione **Flujos de trabajo**.

   ![](assets/add-new-folder-workflows.png)

Se crea la nueva carpeta **Flujos** de trabajo.

1. Right-click and select **Properties**.
1. En **Restricción**, marque **Carpeta en una vista** y haga clic en **Guardar**.

   ![](assets/folder-is-a-view.png)

La carpeta ahora se rellena con todos los flujos de trabajo de la instancia.

**Duplicar un flujo de trabajo de campaña**

1. Seleccione un flujo de trabajo de campaña en la vista Flujo de trabajo.
1. Haga clic con el botón secundario en **Duplicar para**.
   ![](assets/duplicate-to-right-click.png)
1. Cambie su etiqueta.
1. Haga clic en **Save**.

Puede ver el flujo de trabajo duplicado en la vista de flujo de trabajo.
