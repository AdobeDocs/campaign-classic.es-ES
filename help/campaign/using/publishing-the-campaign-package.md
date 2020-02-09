---
title: Publicación del paquete de campaña
seo-title: Publicación del paquete de campaña
description: Publicación del paquete de campaña
seo-description: null
page-status-flag: never-activated
uuid: f2d35a8d-191f-4c53-8682-7ccce2a94257
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: campaign
content-type: reference
topic-tags: distributed-marketing
discoiquuid: 8653d4fc-e47f-451a-95f2-c9209a252664
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: d30de91002862b664249c5a704b7c0f521dd30f2

---


# Publicación del paquete de campaña{#publishing-the-campaign-package}

Central entity operators publish campaigns they wish to offer to local entities in the **[!UICONTROL list of campaign packages]**.

Antes de poder publicar los paquetes en la lista de paquetes de campañas, la entidad central debe aprobarlos. To do this, you can specify a reviewer or group of reviewers via the **[!UICONTROL Approval parameters]** link in the campaign package.

## Asignación de un revisor {#assigning-a-reviewer}

To select the reviewer, click the **[!UICONTROL Approval parameters]** link from the campaign package and choose the relevant reviewer from the drop-down list.

![](assets/s_advuser_mkg_dist_define_valid.png)

You may then begin the approval process by clicking **[!UICONTROL Submit for approval]**.

![](assets/s_advuser_mkg_dist_valid_process.png)

Hecho esto, se envía un mensaje de notificación al revisor para confirmar la disponibilidad de este paquete de campaña. El mensaje contiene un enlace para aceptar o rechazar la aprobación mediante el acceso a la Web.

![](assets/s_advuser_mkg_dist_valid_process1.png)

>[!NOTE]
>
>En el nivel de la entidad organizativa, también puede especificar los revisores que deben aprobar las solicitudes. For more on this, refer to [Organizational entities](../../campaign/using/about-distributed-marketing.md#organizational-entities).

## Añadir otros revisores {#adding-other-reviewers}

You can add other reviewers from the **[!UICONTROL Edit...]** link, found in the campaign package&#39;s **[!UICONTROL Approval parameters...]** tab.

![](assets/s_advuser_mkg_dist_select_op_valid.png)

## Periodos de aprobación {#approval-periods}

De forma predeterminada, los revisores tienen tres días a partir de la fecha de envío para procesar la aprobación.

En la ventana de edición de revisores, también puede definir recordatorios que envían uno o varios mensajes si no se ha aprobado un paquete de campañas. Para ello, haga clic en el **[!UICONTROL Add reminder]** vínculo y, a continuación, en el **[!UICONTROL Add]** botón .

Los recordatorios pueden enviarse en una fecha determinada o **x** días después de la fecha de presentación. El tipo de recordatorio se puede configurar en la primera columna de la tabla de recordatorios. In the example below, the reviewers will receive a reminder message on the on the 29/01/2014, i.e. two days before the date selected in the **[!UICONTROL Date]** column, and a second reminder one day before the end of the approval period, i.e. two days after the submission for approval date.

![](assets/s_advuser_mkg_dist_reminder_planning.png)

Once it is defined and the package has been submitted for approval, the execution schedule is displayed in the **[!UICONTROL Audit]** tab. Muestra la fecha límite de procesamiento calculada en función de la configuración anterior, así como las fechas de todos los recordatorios configurados.

## Aprobación a través de la consola de Adobe Campaign {#approving-via-the-adobe-campaign-console}

If no reviewer has been specified or if none of the notified operators have approved the package, the **[!UICONTROL Approve the package]** button lets you proceed directly to the approval from the campaign package **[!UICONTROL Dashboard]** or from the packages overview.

![](assets/s_advuser_mkg_dist_valid_button.png)

Una vez realizada la aprobación, la campaña se publica, se añade a la lista y, en cuanto se alcanza su fecha de disponibilidad, las entidades locales pueden utilizarla. Si se han especificado las entidades locales al crear la campaña, se envía un mensaje a los operadores en el grupo de notificación para que sepan que la campaña está disponible. Si no se especificó ninguna entidad con anterioridad, la campaña está disponible para todas las entidades locales de forma predeterminada. For more on this, refer to [Organizational entities](../../campaign/using/about-distributed-marketing.md#organizational-entities).
