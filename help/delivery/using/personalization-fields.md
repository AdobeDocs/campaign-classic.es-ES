---
title: Campos personalizados
seo-title: Campos personalizados
description: Campos personalizados
seo-description: null
page-status-flag: never-activated
uuid: 3a94a50e-259e-40c3-ae67-8a2c42e9fad7
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: delivery
content-type: reference
topic-tags: personalizing-deliveries
discoiquuid: 27c8e443-ee6b-4d58-bc2d-81cf8391c5de
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: f5062117b5cefbdd2570018f6803f114c14a3fae

---


# Campos personalizados{#personalization-fields}

Los campos personalizados se utilizan para la personalización de primer nivel del contenido de los mensajes enviados. Los campos que se inserten en un contenido principal muestran la posición en la que se deben insertar los datos desde la fuente de datos seleccionada.

Por ejemplo, el campo personalizado con la sintaxis **&lt;%= recipient.LastName %>** indica a Adobe Campaign que inserte el nombre del destinatario en la base de datos (tabla de destinatarios).

>[!NOTE]
>
>El contenido de los campos de personalización no puede superar los 1024 caracteres.

## Fuentes de datos {#data-sources}

Los campos personalizados pueden proceder de dos tipos de fuente de datos, según el modo de envío seleccionado:

* La base de datos de Adobe Campaign es la fuente de datos. Este es el caso más común con, por ejemplo, los “campos personalizados de destinatario”. Estos son todos los campos definidos en la lista de distribución, ya sean campos estándar (generalmente: apellidos, nombre, dirección, ciudad, fecha de nacimiento, etc.) o campos definidos por el usuario.
* Un archivo externo es la fuente de datos. Estos son todos los campos definidos en las columnas del archivo presentados como entrada durante un envío con los datos que se encuentran en un archivo externo.

>[!NOTE]
>
>Una etiqueta personalizada de Adobe Campaign siempre tiene la siguiente forma **&lt;%=table.field%>**.

## Inserción de un campo personalizado {#inserting-a-personalization-field}

Para insertar campos personalizados, haga clic en el icono desplegable al que se puede acceder desde cualquier campo de edición de encabezado, asunto o cuerpo del mensaje.

![](assets/s_ncs_user_add_custom_field.png)

Después de seleccionar una fuente de datos (campos de destinatario o campo de archivo), esta inclusión aparece como un comando que Adobe Campaign interpreta y al que sustituye el valor del campo para un destinatario determinado. The physical replacement can then be viewed in the **[!UICONTROL Preview]** tab.

## Ejemplo de campos personalizados {#personalization-fields-example}

Se crea un correo electrónico en el que primero debe insertar el nombre del destinatario y, a continuación, se añade la fecha de creación del perfil en el cuerpo del mensaje. Para ello:

1. Cree un nuevo envío o abra un envío de tipo correo electrónico ya existente.
1. In the delivery wizard, click **[!UICONTROL Subject]** to edit the subject of the message and enter a subject.
1. Enter &quot; **[!UICONTROL Special offer for]** &quot; and use the button in the toolbar to insert a personalization field. Select **[!UICONTROL Recipients>Title]**.

   ![](assets/s_ncs_user_insert_custom_field.png)

1. Repita la operación para insertar el nombre del destinatario. Inserte espacios entre todos los campos personalizados.
1. Click **[!UICONTROL OK]** to validate.
1. Inserte la personalización en el cuerpo del mensaje. Para ello, haga clic en el contenido del mensaje y haga clic en el botón de inserción de campo.
1. Select **[!UICONTROL Recipient>Other...]**.

   ![](assets/s_ncs_user_insert_custom_field_b.png)

1. Select the field with the information to display and click **[!UICONTROL OK]**.

   ![](assets/s_ncs_user_insert_custom_field_c.png)

1. Click the **[!UICONTROL Preview]** tab to view the personalization result. Se debe seleccionar un destinatario para mostrar el mensaje de dicho destinatario.

   ![](assets/s_ncs_user_insert_custom_field_d.png)

   >[!NOTE]
   >
   >Cuando un envío forma parte de un flujo de trabajo, se pueden utilizar los datos de la tabla de flujo de trabajo temporal. This data is grouped in the **[!UICONTROL Target extension]** menu. Para obtener más información, consulte [esta sección](../../workflow/using/executing-a-workflow.md#target-data).

## Optimización de la personalización {#optimizing-personalization}

Puede optimizar la personalización mediante una opción dedicada: **[!UICONTROL Prepare the personalization data with a workflow]**, disponible en la **[!UICONTROL Analysis]** ficha de las propiedades de entrega.

Durante el análisis de envío, esta opción crea y ejecuta automáticamente un flujo de trabajo que almacena todos los datos vinculados con el objetivo en una tabla temporal, incluidos los datos de tablas vinculadas en FDA.

Si marca esta opción, puede mejorar de forma significativa el rendimiento de la ejecución de la personalización.

Por ejemplo, si existen problemas de rendimiento al realizar envíos a una gran cantidad de destinatarios mientras utiliza muchos campos personalizados o bloques personalizados en el contenido de sus mensajes, esta opción puede acelerar la gestión de la personalización y, por tanto, el envío de los mensajes.

Para utilizar esta opción, siga los pasos a continuación:

1. Cree una campaña. Para obtener más información, consulte [esta sección](../../campaign/using/setting-up-marketing-campaigns.md#creating-a-campaign).
1. In the **[!UICONTROL Targeting and workflows]** tab of your campaign, add a **Query** activity to your workflow. Para obtener más información sobre esta actividad, consulte [esta sección](../../workflow/using/query.md).
1. Add an **[!UICONTROL Email delivery]** activity to the workflow and open it. Para obtener más información sobre esta actividad, consulte [esta sección](../../workflow/using/delivery.md).
1. Vaya a la **[!UICONTROL Analysis]** ficha de la **[!UICONTROL Delivery properties]** y seleccione la **[!UICONTROL Prepare the personalization data with a workflow]** opción.

   ![](assets/perso_optimization.png)

1. Configure el envío e inicie el flujo de trabajo para iniciar el análisis.

Una vez finalizado el análisis, los datos de personalización se almacenan en una tabla temporal a través de un flujo de trabajo técnico temporal que se crea sobre la marcha durante el análisis.

Este flujo de trabajo no es visible desde la interfaz de Adobe Campaign. Solo pretende ser un medio técnico para almacenar y gestionar rápidamente los datos de personalización.

Once the analysis is complete, go to the workflow **[!UICONTROL Properties]** and select the **[!UICONTROL Variables]** tab. Se puede ver el nombre de la tabla temporal que se puede utilizar para realizar una llamada SQL con el fin de mostrar las ID que contiene.

![](assets/perso_optimization_temp_table.png)

## Fase de personalización de tiempo de espera agotado {#timing-out-personalization}

Para mejorar la protección de la entrega, puede establecer un período de tiempo de espera para la fase de personalización.

En la **[!UICONTROL Delivery]** ficha de la **[!UICONTROL Delivery properties]**, seleccione un valor máximo en segundos para la **[!UICONTROL Maximum personalization run time]** opción.

Durante la vista previa o el envío, si la fase de personalización supera el tiempo máximo establecido en este campo, el proceso se anulará con un mensaje de error y la entrega fallará.

![](assets/perso_time-out.png)

El valor predeterminado es 5 segundos.

Si establece esta opción en 0, no habrá límite de tiempo para la fase de personalización.