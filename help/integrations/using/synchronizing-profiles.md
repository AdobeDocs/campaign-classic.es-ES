---
title: Sincronización de perfiles
seo-title: Sincronización de perfiles
description: Sincronización de perfiles
seo-description: null
page-status-flag: never-activated
uuid: 3d5f0fd4-dfe7-4b34-a75f-8cf36fb7c91d
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: integrations
content-type: reference
topic-tags: acs-connector
discoiquuid: 91115d4f-0cb6-4bce-b28d-17f15e9f9a0a
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 209ac4d81d2d27c264ee6b288bcb7fcb1900ffc5

---


# Sincronización de perfiles{#synchronizing-profiles}

El conector ACS duplica los datos de Campaign v7 a Campaign Standard. Los datos recibidos de Campaign v7 se pueden utilizar en Campaign Standard para crear envíos. Puede ver cómo se sincronizan los perfiles realizando las operaciones enumeradas a continuación.

* **Agregar nuevos destinatarios**: Cree un nuevo destinatario en Campaign v7 y confirme que se haya replicado un perfil correspondiente en Campaign Standard. See [Creating a new recipient](#creating-a-new-recipient).
* **Actualizar destinatarios**: Edite un nuevo destinatario en Campaign v7 y vea el perfil correspondiente en Campaign Standard para confirmar que la actualización se ha replicado. Consulte [Edición de un destinatario](#editing-a-recipient).
* **Genere un flujo de trabajo en Campaign Standard**: Cree un flujo de trabajo en Campaign Standard que incluya una consulta con una audiencia o perfiles replicados desde Campaign v7. Consulte [Creación de un flujo de trabajo](#creating-a-workflow).
* **Crear una entrega en Campaign Standard**: Siga el flujo de trabajo hasta la finalización para enviar una entrega. Consulte [Creación de una entrega](#creating-a-delivery).
* **Verifique el vínculo** de cancelación de suscripción: Utilice una aplicación web de Campaign v7 para asegurarse de que la opción del destinatario de cancelar la suscripción a un servicio se envía a la base de datos de Campaign v7. La opción de dejar de recibir el servicio se duplica en Campaign Standard. See [Changing the unsubscription link](#changing-the-unsubscription-link).

## Requisitos previos {#prerequisites}

Las secciones siguientes describen cómo el conector ACS ayuda a añadir y editar destinatarios en Campaign v7 y a utilizarlos después en un envío de Campaign Standard. El conector ACS requiere lo siguiente:

* duplicación de destinatarios de Campaign v7 en Campaign Standard.
* Derechos de usuario para ejecutar flujos de trabajo en Campaign v7 y en Campaign Standard.
* Derechos de usuario para crear y ejecutar un envío en Campaign Standard.

## Modificación del enlace de baja de suscripción {#changing-the-unsubscription-link}

Cuando un destinatario hace clic en el enlace de baja de suscripción en un mensaje de correo electrónico enviado por Campaign Standard, se actualiza el perfil correspondiente en Campaign Standard. Para asegurarse de que un perfil duplicado incluya la opción para el usuario de darse baja de un servicio, la información debe enviarse a Campaign v7 en lugar de a Campaign Standard. Para ejecutar el cambio, el servicio de baja está vinculado con una aplicación web de Campaign v7 en lugar de Campaign Standard.

>[!NOTE]
>
>Solicite al consultor que configure la aplicación web para el servicio de baja antes de iniciar los pasos siguientes.

## Creación de un destinatario nuevo {#creating-a-new-recipient}

1. Cree un destinatario nuevo en Campaign v7 para la duplicación en Campaign Standard. Introduzca la mayor cantidad de información posible, incluidos el apellido, el nombre, la dirección de correo electrónico y la dirección postal del destinatario. However, do not choose a **[!UICONTROL Salutation]** since it will be added in the next section, [Editing a recipient](#editing-a-recipient). Para obtener más información, consulte [Adición de destinatarios](../../platform/using/adding-profiles.md).

   ![](assets/acs_connect_profile_sync_01.png)

1. Confirme que el nuevo destinatario se ha añadido a Campaign Standard. Al revisar el perfil, asegúrese de que los datos introducidos en Campaign v7 también estén disponibles en Campaign Standard. Para saber dónde encontrar los perfiles en Campaign Standard, consulte [Conceptos básicos de navegación](https://docs.adobe.com/content/help/en/campaign-standard/using/getting-started/discovering-the-interface/interface-description.html).

   ![](assets/acs_connect_profile_sync_02.png)

   De forma predeterminada, la duplicación periódica del conector ACS se produce una vez cada 15 minutos. Para obtener más información, consulte Replicación [de datos](../../integrations/using/acs-connector-principles-and-data-cycle.md#data-replication).

## Edición de un destinatario {#editing-a-recipient}

Los pasos siguientes para cambiar un único punto de datos proporcionan un ejemplo sencillo de cómo Campaign v7 se convierte en la base de datos maestra para Campaign Standard cuando se utiliza la duplicación de datos. Modificar o eliminar los datos duplicados en Campaign v7 tiene el mismo efecto en los datos correspondientes de Campaign Standard.

1. Elija el destinatario recién creado en [Creación de un nuevo destinatario](#creating-a-new-recipient) y edite el nombre del destinatario. For example, choose a **[!UICONTROL Salutation]** for the recipient (e.g. Mr. or Mrs.). Para obtener más información, consulte [Edición de un perfil](../../platform/using/editing-a-profile.md).

   ![](assets/acs_connect_profile_sync_03.png)

1. Confirme que el nombre del destinatario se ha actualizado en Campaign Standard. Para saber dónde encontrar los perfiles en Campaign Standard, consulte [Conceptos básicos de navegación](https://docs.adobe.com/content/help/en/campaign-standard/using/getting-started/discovering-the-interface/interface-description.html).

   ![](assets/acs_connect_profile_sync_04.png)

   De forma predeterminada, la duplicación periódica del conector ACS se produce una vez cada 15 minutos. Para obtener más información, consulte Replicación [de datos](../../integrations/using/acs-connector-principles-and-data-cycle.md#data-replication).

## Creación de un flujo de trabajo {#creating-a-workflow}

Los perfiles y servicios duplicados de Campaign v7 están disponibles para los profesionales de marketing digital a fin de aprovechar los datos enriquecidos en Campaign Standard. Las instrucciones siguientes muestran cómo añadir una consulta a un flujo de trabajo de Campaign Standard y cómo utilizarla con la base de datos duplicada.

Para obtener más información e instrucciones completas sobre los flujos de trabajo de Campaign Standard, consulte [Flujos de trabajo](https://docs.adobe.com/content/help/en/campaign-standard/using/managing-processes-and-data/about-workflows-and-data-management/workflow-data-and-processes.html).

1. Go to Campaign Standard and click **[!UICONTROL Marketing Activities]**.
1. Click **[!UICONTROL Create]** on the upper right.
1. Haga clic **[!UICONTROL Workflow]**.
1. Haga clic en **[!UICONTROL New workflow]** y **[!UICONTROL Next]**.
1. Enter a name for the workflow in the **[!UICONTROL Label]** field and additional information if needed. Haga clic **[!UICONTROL Next]**.
1. From **[!UICONTROL Targeting]** on the left, drag a **[!UICONTROL Query]** target to the workspace.

   ![](assets/acs_connect_profile_sync_05.png)

1. Double click the **[!UICONTROL Query]** activity and choose a parameter that can be used with the replicated database. Por ejemplo, puede:

   * Drag **[!UICONTROL Profiles]** to the workspace. Use the field pull-down menu to choose **[!UICONTROL Is external resource]** to find profiles that were replicated from Campaign v7.
   * Arrastre otros parámetros de consulta para segmentar más los perfiles duplicados.

## Creación de envíos {#creating-a-delivery}

>[!NOTE]
>
>The instructions for creating the delivery continue the workflow started with [Creating a workflow](#creating-a-workflow).

Los profesionales del marketing digital pueden aprovechar la aplicación web de Campaign v7 para asegurarse de que la decisión de un destinatario de darse de baja de la suscripción a un servicio se envía a la base de datos Campaign v7. Después de que el destinatario haga clic en el enlace de baja de suscripción, la opción para detener la recepción del servicio se duplica de Campaign v7 a Campaign Standard. Para obtener más información, consulte [Cambio del vínculo](#changing-the-unsubscription-link)de cancelación de suscripción.

Siga los pasos a continuación para añadir un envío de correo electrónico a un flujo de trabajo existente con el servicio de baja de suscripción creado en Campaign v7. Para obtener más información e instrucciones completas sobre los flujos de trabajo de Campaign Standard, consulte este [documento](https://docs.adobe.com/content/help/en/campaign-standard/using/managing-processes-and-data/about-workflows-and-data-management/workflow-data-and-processes.html).

>[!NOTE]
>
>Solicite al consultor que configure la aplicación web para el servicio de baja antes de iniciar los pasos siguientes.

1. Click **[!UICONTROL Channels]** on the left.
1. Drag **[!UICONTROL Email delivery]** to the existing workflow in the workspace.

   ![](assets/acs_connect_profile_sync_07.png)

1. Haga doble clic en la **[!UICONTROL Email delivery]** actividad y elija **[!UICONTROL Single send email]** o **[!UICONTROL Recurring email]**. Select your options and click **[!UICONTROL Next]**.
1. Haga clic en **[!UICONTROL Send via email]** y en **[!UICONTROL Next]**.

   ![](assets/acs_connect_profile_sync_08.png)

1. Enter a name for the delivery in the **[!UICONTROL Label]** field and additional information if needed. Haga clic **[!UICONTROL Next]**.

   ![](assets/acs_connect_profile_sync_09.png)

1. In the **[!UICONTROL Subject]** field, enter the subject that will appear in the recipient&#39;s email inbox.
1. Click **[!UICONTROL Change content]** to add an HTML template.

   ![](assets/acs_connect_profile_sync_10.png)

1. Seleccione el contenido que incluye el enlace de baja de suscripción al servicio. Haga clic **[!UICONTROL Confirm]**.

   ![](assets/acs_connect_profile_sync_11.png)

1. El enlace de baja actual debe reemplazarse por uno nuevo que utilice la aplicación web creada por el consultor. Busque el enlace de baja en la parte inferior del contenido del correo electrónico y haga clic en él una vez. Haga clic en el icono de la papelera para eliminar el enlace.

   ![](assets/acs_connect_profile_sync_12.png)

1. Haga clic dentro de la misma área de contenido y escriba **Enlace de baja**.

   ![](assets/acs_connect_profile_sync_13.png)

1. Resalte el texto con el cursor y haga clic en el icono de cadena.
1. Haga clic **[!UICONTROL Link to a landing page]**.

   ![](assets/acs_connect_profile_sync_14.png)

1. Haga clic en el icono de la carpeta para seleccionar la página de destino.

   ![](assets/acs_connect_profile_sync_15.png)

1. Choose the web application created by the consultant and click **[!UICONTROL Confirm]**.

   ![](assets/acs_connect_profile_sync_16.png)

1. Haga clic **[!UICONTROL Create]**.
1. Vuelva al flujo de trabajo haciendo clic en el nombre del envío.

   ![](assets/acs_connect_profile_sync_17.png)

1. Click **[!UICONTROL Start]** to send the delivery. El icono de envío de correo electrónico parpadea para indicar que se está preparando la realización del envío.

   ![](assets/acs_connect_profile_sync_18.png)

1. Double click the **[!UICONTROL Email delivery]** channel and choose **[!UICONTROL Confirm]** to send the email. Click **[!UICONTROL OK]** to send the messages.

   ![](assets/acs_connect_profile_sync_19.png)

## Verificación del servicio de baja de suscripción {#verifying-the-unsubscription-service}

Siga las instrucciones de [Creación de un flujo de trabajo](#creating-a-workflow) y [Creación de un envío](#creating-a-delivery) antes de pasar a los pasos que se describen a continuación.

1. El destinatario hace clic en el enlace de baja en el correo electrónico enviado.

   ![](assets/acs_connect_profile_sync_20.png)

1. El destinatario confirma la baja.

   ![](assets/acs_connect_profile_sync_21.png)

1. Los datos del destinatario en Campaign v7 se actualizan para reflejar que el usuario se ha dado de baja de la suscripción. Confirm that the box **[!UICONTROL No longer contact (by any channel)]** is checked for the recipient. Para obtener información sobre cómo ver un destinatario en Campaign v7, consulte [Edición de un perfil](../../platform/using/editing-a-profile.md).

   ![](assets/acs_connect_profile_sync_22.png)

1. Vaya a Campaign Standard y abra los detalles del perfil del destinatario. Confirme que aparece una casilla de verificación junto a **[!UICONTROL No longer contact (by any channel)]**. Para saber dónde encontrar los perfiles en Campaign Standard, consulte [Conceptos básicos de navegación](https://docs.adobe.com/content/help/en/campaign-standard/using/getting-started/discovering-the-interface/interface-description.html).

   ![](assets/acs_connect_profile_sync_23.png)

