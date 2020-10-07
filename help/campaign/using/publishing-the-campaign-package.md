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
translation-type: tm+mt
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: tm+mt
source-wordcount: '460'
ht-degree: 90%

---


# Publicación del paquete de campaña{#publishing-the-campaign-package}

Central entity operators publish campaigns they wish to offer to local entities in the **[!UICONTROL list of campaign packages]**.

Antes de poder publicar los paquetes en la lista de paquetes de campañas, la entidad central debe aprobarlos. Para ello, se puede especificar un revisor o un grupo de revisores a través del vínculo **[!UICONTROL Approval parameters]** del paquete de campañas.

## Asignación de un revisor {#assigning-a-reviewer}

Para seleccionar un revisor, haga clic en el vínculo **[!UICONTROL Approval parameters]** del paquete de campaña y elija el revisor correspondiente en la lista desplegable.

![](assets/s_advuser_mkg_dist_define_valid.png)

You may then begin the approval process by clicking **[!UICONTROL Submit for approval]**.

![](assets/s_advuser_mkg_dist_valid_process.png)

Hecho esto, se envía un mensaje de notificación al revisor para confirmar la disponibilidad de este paquete de campaña. El mensaje contiene un vínculo para aceptar o rechazar la aprobación mediante el acceso a la Web.

![](assets/s_advuser_mkg_dist_valid_process1.png)

>[!NOTE]
>
>En el nivel de la entidad organizativa, también puede especificar los revisores que deben aprobar las solicitudes. Para obtener más información, consulte [Entidades organizativas](../../campaign/using/about-distributed-marketing.md#organizational-entities).

## Añadir otros revisores {#adding-other-reviewers}

You can add other reviewers from the **[!UICONTROL Edit...]** link, found in the campaign package&#39;s **[!UICONTROL Approval parameters...]** tab.

![](assets/s_advuser_mkg_dist_select_op_valid.png)

## Periodos de aprobación {#approval-periods}

De forma predeterminada, los revisores tienen tres días a partir de la fecha de envío para procesar la aprobación.

En la ventana de edición de revisores, también puede definir recordatorios que envían uno o varios mensajes si no se ha aprobado un paquete de campañas. To do this, click the **[!UICONTROL Add reminder]** link, then the **[!UICONTROL Add]** button.

Los recordatorios pueden enviarse en una fecha determinada o **x** días después de la fecha de presentación. El tipo de recordatorio se puede configurar en la primera columna de la tabla de recordatorios. En el siguiente ejemplo, los revisores recibirán un mensaje recordatorio el 29/01/2014, es decir, dos días antes de la fecha seleccionada en la columna **[!UICONTROL Date]** y un segundo recordatorio un día antes del final del periodo de aprobación, por ejemplo, dos días después de la fecha de envío para la aprobación.

![](assets/s_advuser_mkg_dist_reminder_planning.png)

Una vez definido y enviado el paquete para su aprobación, la programación de ejecución se muestra en la pestaña **[!UICONTROL Audit]**. Muestra la fecha límite de procesamiento calculada en función de la configuración anterior, así como las fechas de todos los recordatorios configurados.

## Aprobación a través de la consola de Adobe Campaign {#approving-via-the-adobe-campaign-console}

Si no se ha especificado ningún revisor o si ninguno de los operadores de notificación ha aprobado el paquete, el botón **[!UICONTROL Approve the package]** le permite aprobarlo un paquete de campañas directamente desde el **[!UICONTROL Dashboard]** o desde la información general de los paquetes.

![](assets/s_advuser_mkg_dist_valid_button.png)

Una vez realizada la aprobación, la campaña se publica, se añade a la lista y, en cuanto se alcanza su fecha de disponibilidad, las entidades locales pueden utilizarla. Si se han especificado las entidades locales al crear la campaña, se envía un mensaje a los operadores en el grupo de notificación para que sepan que la campaña está disponible. Si no se especificó ninguna entidad con anterioridad, la campaña está disponible para todas las entidades locales de forma predeterminada. Para obtener más información, consulte [Entidades organizativas](../../campaign/using/about-distributed-marketing.md#organizational-entities).
