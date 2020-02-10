---
title: Creación de una campaña de colaboración
seo-title: Creación de una campaña de colaboración
description: Creación de una campaña de colaboración
seo-description: null
page-status-flag: never-activated
uuid: 13d8ff65-1480-422a-85b6-40b553a3c151
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: campaign
content-type: reference
topic-tags: distributed-marketing
discoiquuid: 01d8be92-7312-4386-b5f5-651af31308f7
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: d30de91002862b664249c5a704b7c0f521dd30f2

---


# Creación de una campaña de colaboración{#creating-a-collaborative-campaign-intro}

La entidad central crea campañas de colaboración a partir de plantillas de campañas de **Distributed Marketing.** Consulte [esta página](../../campaign/using/about-distributed-marketing.md#collaborative-campaign).

## Creación de una campaña de colaboración {#creating-a-collaborative-campaign}

Para configurar una campaña de colaboración, haga clic en el **[!UICONTROL Campaign management > Campaigns]** nodo y, a continuación, en el **[!UICONTROL New]** icono.

>[!NOTE]
>
>Apart from **[!UICONTROL collaborative campaigns (by campaign)]**, these campaigns can be configured and executed via a web interface.

El proceso de configuración de una base de datos de campaña de colaboración es similar al de una plantilla de campaña local. A continuación se describen las especificaciones de los diferentes tipos de campañas colaborativas.

### Por formulario {#by-form}

To create a collaborative campaign (by form), the **[!UICONTROL Collaborative campaign (by form)]** template must be selected.

![](assets/mkg_dist_mutual_op_form2.png)

In the **[!UICONTROL Edit]** tab, click the **[!UICONTROL Advanced campaign settings...]** link to access the **Distributed Marketing** tab.

Seleccione la interfaz web **By form.** Este tipo de interfaz le permite crear campos de personalización que se utilizarán en entidades locales cuando se solicite una campaña. Consulte [Creación de una campaña local (por formulario)](../../campaign/using/examples.md#creating-a-local-campaign--by-form-).

Guarde la campaña. You can now use it from the **Campaign packages** view in the **Campaign** universe, by clicking the **[!UICONTROL Create]** button.

The **[!UICONTROL Campaign Package]** view allows you to use local campaign templates (out-of-the-box or duplicated), as well as reference campaigns for collaborative campaigns, with the aim of creating campaigns for your different organizational entities.

![](assets/mkg_dist_mutual_op_form1b.png)

### Por campaña {#by-campaign}

To create a collaborative campaign (by campaign), the **[!UICONTROL Collaborative campaign (by campaign) (opCollaborativeByCampaign)]** template must be selected.

![](assets/mkg_dist_mutual_op_by_op2.png)

Al realizar la solicitud de la campaña, la entidad local puede completar los criterios predefinidos por la entidad central y evaluar la campaña antes de realizar la solicitud.

Una vez aprobada la solicitud de una campaña **Collaborative campaign (by campaign)** en la entidad central, se crea una campaña secundaria para la entidad local. Una vez disponibles, la entidad local puede modificar:

* el flujo de trabajo de la campaña,
* reglas de tipología,
* y campos de personalización.

La entidad local ejecuta la campaña secundaria. La entidad central ejecuta la campaña principal.

The central entity can view all child campaigns linked with a **Collaborative campaign (by campaign)** from this dashboard (via the **[!UICONTROL List of associated campaigns]** link).

![](assets/mkg_dist_mutual_op_by_op.png)

### Por aprobación de destino {#by-target-approval}

To create a collaborative campaign (by target approval), the **[!UICONTROL Collaborative campaign (by target approval)]** template must be selected.

![](assets/mkg_dist_mutual_op_by_valid.png)

>[!NOTE]
>
>En este modo, la entidad central no necesita especificar las entidades locales.

El flujo de trabajo de campaña debe integrar la actividad de tipo de **Local approval** . Los parámetros de actividad son los siguientes:

* **[!UICONTROL Action to perform]** : Notificación de aprobación del objetivo.
* **[!UICONTROL Distribution context]** : Explícito.
* **[!UICONTROL Data distribution]** : Distribución de entidad local.

Se debe crear la distribución de datos del tipo de **Local entity distribution** . La plantilla de distribución de datos permite limitar el número de registros de una lista de valores de agrupación. En **[!UICONTROL Resources > Campaign management > Data distribution]**, haga clic en el **[!UICONTROL New]** icono para crear un nuevo **[!UICONTROL Data distribution]**. Para obtener más información sobre la distribución de los datos, consulte la Guía de [Flujos de trabajo](../../workflow/using/using-the-local-approval-activity.md#step-1--creating-the-data-distribution-template-) .

![](assets/mkg_dist_data_distribution.png)

Select the **Targeting dimension** and the **[!UICONTROL Distribution field]**. Para el **[!UICONTROL Assignment type]**, seleccione Entidad **** local.

In the **[!UICONTROL Distribution]** tab, add a field for each local entity and specify the value.

![](assets/mkg_dist_data_distribution2.png)

Puede añadir una segunda **aprobación de destino** después de la actividad de **envío** para configurar un informe.

En el mensaje de notificación de creación de la campaña, la entidad local recibe una lista de contactos predefinida por los parámetros de la entidad central.

![](assets/mkg_dist_mutual_op_by_valid1.png)

La entidad local puede eliminar ciertos contactos según el contenido de la campaña.

![](assets/mkg_dist_mutual_op_by_valid2.png)

### Sencilla {#simple}

To create a simple collaborative campaign, the **[!UICONTROL Collaborative campaign (simple)]** template must be selected.

## Creación de un paquete de campaña de colaboración {#creating-a-collaborative-campaign-package}

Para que una campaña esté disponible para las entidades locales, la entidad central debe crear un paquete de campañas.

Siga estos pasos:

1. En la **[!UICONTROL Navigation]** sección de la página **Campañas** , haga clic en el **[!UICONTROL Campaign packages]** vínculo.
1. Haga clic en el botón **[!UICONTROL Create]**.
1. The section at the top of the window lets you select the **[!UICONTROL New collaborative package (mutualizedEmpty)]** template.
1. Seleccione la campaña de referencia.
1. Especifique la etiqueta, la carpeta y el programa de ejecución para el paquete de campaña.

### Fechas {#dates}

Las fechas de inicio y finalización definen el periodo de visibilidad de la campaña en la lista de paquetes de campañas.

Para las **campañas de colaboración**, la entidad central debe especificar el plazo de registro y personalización.

>[!NOTE]
>
>The **[!UICONTROL Personalization deadline]** allows the central entity to choose a deadline by which the local entities must have delivered the documents (spreadsheets, images) to be used to configure the campaign. Esta no es una opción obligatoria. Omitir esta fecha no afecta la implementación de la campaña.

![](assets/s_advuser_mkg_dist_create_mutual_entry.png)

### Audiencia {#audience}

La entidad central debe especificar las entidades locales involucradas en cada campaña en cuanto se crea la campaña de colaboración.

![](assets/s_advuser_mkg_dist_create_mutual_entry2.png)

>[!CAUTION]
>
>**[!UICONTROL Simple, by form and by campaign collaborative campaign kits]** no se puede aprobar a menos que se hayan especificado las entidades locales pertinentes.

### Modos de aprobación {#approval-modes}

Para las **campañas de colaboración**, se puede especificar el modo de aprobación de la solicitud.

![](assets/mkg_dist_edit_kit1.png)

En modo manual, la entidad local necesita suscribirse para poder participar en la campaña.

En modo automático, la entidad local se presuscribe automáticamente a la campaña. Puede cancelar la suscripción de la campaña o modificar sus parámetros sin necesidad de que la entidad central lo apruebe.

![](assets/mkg_dist_edit_kit2.png)

### Notificaciones {#notifications}

La configuración de las notificaciones es idéntica a las notificaciones de una entidad local. Consulte [esta sección](../../campaign/using/creating-a-local-campaign.md#notifications).

## Solicitud de una campaña {#ordering-a-campaign}

Cuando se añade una campaña colaborativa a la lista de paquetes de campaña, se notifica a las entidades locales pertenecientes a la audiencia definida por la entidad central (**Collaborative campaigns (by target approval)** no tienen un público predefinido). El mensaje enviado contiene un enlace que le permite registrarse en la campaña, como se muestra a continuación:

![](assets/mkg_dist_mutual_op_notification.png)

Este mensaje también permite que las entidades locales vean la descripción introducida por el operador central que creó el paquete, así como los documentos vinculados a la campaña. No pertenecen a la misma campaña, aunque proporcionan información adicional sobre ella.

Una vez que los operadores locales se han registrado a través de una interfaz web, pueden añadir información personalizada a la campaña de colaboración que deseen solicitar:

![](assets/mkg_dist_mutual_op_command.png)

Una vez que una entidad local ha finalizado su registro, se notifica a las entidades centrales por correo electrónico para que aprueben la solicitud.

![](assets/mkg_dist_mutual_op_valid_command.png)

For more on this, refer to the [Approval process](../../campaign/using/creating-a-local-campaign.md#approval-process) section.

## Aprobación de una solicitud {#approving-an-order}

El proceso de aprobación de una solicitud de paquete de campaña de colaboración es el mismo que al hacerlo para una campaña local. Consulte [esta sección](../../campaign/using/creating-a-local-campaign.md#approving-an-order).
