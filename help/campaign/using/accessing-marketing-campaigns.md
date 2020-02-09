---
title: Acceso a campañas de marketing
seo-title: Acceso a campañas de marketing
description: Acceso a campañas de marketing
seo-description: null
page-status-flag: never-activated
uuid: a482be37-61bb-4588-9dfb-f9c3ee5a1930
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: campaign
content-type: reference
topic-tags: about-marketing-campaigns
discoiquuid: 8e7eb53c-bbe2-4bd4-8581-c2a63a3dc84e
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: b47dcfa0e4ee2e5e43e7aa14b94e12fd70ff9c2d

---


# Acceso a campañas de marketing{#accessing-marketing-campaigns}

Adobe Campaign le permite crear, configurar, ejecutar y analizar las campañas de marketing. Todas las campañas de marketing se pueden administrar desde un centro de control unificado.

## Conceptos básicos del espacio de trabajo (Workspace){#workspace-basics}

### Página principal {#home-page}

Una vez que se conecte a Adobe Campaign, verá la página principal.

![](assets/campaign_global_view.png)

Haga clic en los enlaces de la barra de navegación para acceder a los distintos universos.

Campaign elements are found in the **[!UICONTROL Campaigns]** universe: here you can see an overview of the marketing programs and campaigns as well as their sub-sets. Un programa de marketing consta de campañas, que están formadas por envíos, tareas, recursos vinculados, etc. En el contexto de la administración de campañas de marketing mediante Campaign, la información sobre los envíos, los presupuestos, los revisores y los documentos vinculados se encuentran en las campañas.

The navigation block of the **[!UICONTROL Campaigns]** universe offers various entries, depending on modules installed on the instance. Por ejemplo, puede acceder a:

* **Campaign calendar** (calendario de campañas): calendario de planes, programas de marketing, envíos y campañas. Consulte el calendario [de](#campaign-calendar)campaña.
* **Campaigns** (campañas): acceso a las campañas contenidas en todos los programas de marketing.
* **Deliveries** (envíos): acceso a los envíos vinculados a las campañas.
* **Web Applications** (aplicaciones web): acceso a aplicaciones web (formularios, encuestas, etc.).

>[!NOTE]
>
>Para obtener más información sobre el funcionamiento general de Adobe Campaign, los permisos y las funcionalidades de administración de perfiles, consulte [esta sección](../../platform/using/adobe-campaign-workspace.md).
>
>En [esta sección](../../delivery/using/communication-channels.md) se describen todas las funcionalidades relacionadas con canales y envíos.

### Calendario de campañas {#campaign-calendar}

Cada campaña pertenece a un programa que, a su vez, pertenece a un plan. Plans, programs and campaigns are accessed via the **[!UICONTROL Campaign calendar]** menu in the **Campaigns** universe.

To edit a plan, program, campaign or delivery, click its name in the calendar and then click **[!UICONTROL Open...]**. A continuación se muestra en una nueva pestaña, como se muestra a continuación:

![](assets/d_ncs_user_interface_hierar.png)

Puede filtrar la información que se muestra en el calendario de campañas. To do this, click the **[!UICONTROL Filter]** link and select the filtering criteria.

![](assets/campaign_planning_filter.png)

>[!NOTE]
>
>Cuando filtra una fecha, se muestran todas las campañas con una fecha de inicio posterior a la fecha especificada o con una fecha de finalización anterior a la fecha especificada. Es necesario seleccionar las fechas utilizando los calendarios a la derecha de cada campo.

You can also use the **[!UICONTROL Search]** field to filter the displayed items.

Los iconos vinculados a cada elemento permiten ver su estado: terminado, en curso, en edición, etc.

### Exploración en un programa de marketing {#browsing-in-a-marketing-program}

Campaign le permite administrar un conjunto de programas creados a partir de diferentes campañas de marketing. Cada campaña contiene envíos y los procesos y recursos asociados.

#### Exploración de un programa {#browsing-a-program}

Al editar un programa, utilice las pestañas que se describen a continuación para explorarlo y configurarlo.

* La pestaña **Programación** muestra el calendario de programas de un mes, una semana o un día según la pestaña en la que haga clic en el encabezado del calendario.

   Si es necesario, puede crear una campaña, un programa o una tarea a través de esta página.

   ![](assets/s_ncs_user_interface_campaign02.png)

* La pestaña **Editar** permite personalizar el programa: nombre, fechas de inicio y finalización, presupuesto, documentos vinculados, etc.

   ![](assets/s_ncs_user_interface_campaign05.png)

#### Exploración de campañas {#browsing-campaigns}

Campaigns can be accessed via the campaign calendar, the **[!UICONTROL Schedule]** tab of the program, or the list of campaigns.

1. Via the campaign calendar, select the campaign you want to display, then click the **[!UICONTROL Open]** link.

   ![](assets/campaign_planning_edit_op.png)

   La campaña se abre en una nueva pestaña, como se muestra a continuación:

   ![](assets/campaign_op_edit.png)

1. Via the **[!UICONTROL Schedule]** tab of the program, the edit mode is the same as via the campaign calendar.
1. Via the **[!UICONTROL Campaigns]** link of the **[!UICONTROL Campaigns]** universe, click the name of the campaign you want to edit.

   ![](assets/campaign_edit_from_list.png)

### Control de una campaña {#controlling-a-campaign}

#### Panel {#dashboard}

Para cada campaña, los trabajos, recursos y envíos están centralizados en una sola pantalla, el panel, que permite administrar las acciones de marketing en colaboración con otros usuarios.

El panel de una campaña se utiliza como interfaz de control. Accede a las principales fases de creación y gestión de campañas directamente: envíos, extracción de archivos, notificaciones, presupuestos, etc.

![](assets/s_ncs_user_op_board_start_del.png)

Con Adobe Campaign, se pueden configurar procesos de colaboración para la creación y aprobación de las distintas etapas de marketing y de comunicación de las campañas: la aprobación del presupuesto, el objetivo, el contenido, etc.

![](assets/s_ncs_user_op_board_validate.png)

>[!NOTE]
>
>The configuration of campaign templates is presented in [Campaign templates](../../campaign/using/marketing-campaign-templates.md#campaign-templates).

#### Programación {#schedule}

Una campaña unifica un conjunto de envíos. Para cada campaña, la programación ofrece una vista global de todos los componentes: esto permite mostrar las tareas y los envíos y acceder a ellos fácilmente.

![](assets/campaign_planning_tab.png)

#### Foro {#forum}

Para cada campaña, los operadores pueden intercambiar mensajes a través de un foro dedicado.

For more on this, refer to [Discussion forums](../../campaign/using/discussion-forums.md).

#### Informes {#reports}

The **[!UICONTROL Reports]** link lets you access the campaign reports.

![](assets/campaign_reporting_tab.png)

>[!NOTE]
>
>Los informes se describen en [esta sección](../../reporting/using/about-adobe-campaign-reporting-tools.md).

#### Configuración {#configuration}

Las campañas se crean mediante plantillas de campaña. Puede configurar plantillas reutilizables para las que algunas opciones están seleccionadas y otras configuraciones ya están guardadas. Para cada campaña, se ofrece la siguiente funcionalidad:

* Referencia a documentos y recursos: puede asociar documentos con la campaña (resumen, informes, imágenes, etc.). Se admiten todos los formatos de documento. Consulte [Administración de documentos](../../campaign/using/marketing-campaign-deliveries.md#managing-associated-documents)asociados.
* Definición de costes: para cada campaña, Adobe Campaign permite definir las entradas de coste y las estructuras de cálculo de costes que se pueden utilizar al crear la campaña de marketing. Por ejemplo: gastos de impresión, utilización de una agencia externa, alquiler de habitaciones, etc. Consulte [Definición de categorías](../../campaign/using/providers--stocks-and-budgets.md#defining-cost-categories)de costes.
* Definición de objetivos: puede definir objetivos cuantificables para una campaña, por ejemplo: número de suscriptores, volumen comercial, etc. Esta información se utiliza más tarde en los informes de campaña.
* Managing seed addresses (for more on this, refer to [this section](../../delivery/using/about-seed-addresses.md)) and control groups (refer to [Defining a control group](../../campaign/using/marketing-campaign-deliveries.md#defining-a-control-group)).
* Administrar aprobaciones: puede seleccionar los tratamientos que desea aprobar y, si es necesario, seleccionar los operadores o grupos de operadores revisores. See [Checking and approving deliveries](../../campaign/using/marketing-campaign-approval.md#checking-and-approving-deliveries).

>[!NOTE]
>
>To access the campaign configurations and make changes to them, click the **[!UICONTROL Advanced campaign parameters...]** link in the **[!UICONTROL Edit]** tab. Para obtener más información sobre la configuración de parámetros en el nivel de campaña para que los envíos hereden valores automáticamente, consulte [nuestra nota técnica](https://helpx.adobe.com/campaign/kb/simplifying-campaign-management-acc.html#Setparametersatthecampaignlevelsodeliveriesinheritvaluesautomatically).

## Uso de la interfaz web {#using-the-web-interface-}

Puede acceder a las pantallas de la consola de Adobe Campaign a través de un explorador de internet para ver todas las campañas y envíos, así como informes e información sobre los perfiles de la base de datos. Este acceso no permite la creación de registros. Según los derechos de los operadores, puede ver o actuar en los datos de la base de datos. Por ejemplo: puede aprobar el contenido de las campañas y su segmentación, reiniciar o detener un envío, etc.

1. Log on as usual via https://`<your instance>:<port>/view/home`.
1. Utilice los menús para acceder a las descripciones generales.

   ![](assets/s_ncs_user_interface_web_campaign_01.png)

Las aprobaciones (de un destino o contenido de envío, por ejemplo) se pueden llevar a cabo mediante el acceso a la Web.

![](assets/campaign_web_interface_validation.png)

También puede utilizar el enlace incluido en los mensajes de notificación. Para obtener más información sobre esto, consulte [Comprobación y aprobación de envíos](../../campaign/using/marketing-campaign-approval.md#checking-and-approving-deliveries).
