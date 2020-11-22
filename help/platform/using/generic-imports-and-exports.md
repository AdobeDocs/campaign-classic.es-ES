---
solution: Campaign Classic
product: campaign
title: Importación y exportación genéricas
description: Importación y exportación genéricas
audience: platform
content-type: reference
topic-tags: importing-and-exporting-data
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---


# Importación y exportación genéricas{#generic-imports-and-exports}

Adobe Campaign ofrece un módulo de exportación de datos que facilita la extracción de una lista de clientes o clientes potenciales (por ejemplo, una operación de segmentación) que luego forme parte de una población objetivo.

Adobe Campaign también ofrece un módulo de importación que le permite suministrar datos de archivos externos a su base de datos.

>[!NOTE]
>
>Las exportaciones e importaciones se configuran en plantillas dedicadas ejecutadas a través de flujos de trabajo mediante las actividades **[!UICONTROL Import]** y **[!UICONTROL Export]**. Se pueden repetir automáticamente según un programa, por ejemplo, para automatizar el intercambio de datos entre varios sistemas de información. Si es necesario, puede crear una importación o exportación puntual a través del nodo **[!UICONTROL Profiles and Targets > Jobs > Generic imports and exports]** del árbol de Adobe Campaign.

Se puede:

* Crear una plantilla de importación o exportación y configurarla (consulte a continuación).
* Crear una importación o exportación: consulte [Exportación de datos](../../platform/using/exporting-data.md) o [Importación de datos](../../platform/using/importing-data.md).
* Inicie la importación o exportación y monitorice su ejecución. consulte [Seguimiento de ejecución](#execution-tracking).

>[!CAUTION]
>
>La importación de datos en Campaign debe realizarse mediante flujos de trabajo para proteger la coherencia de los datos y mejorar la eficacia. Para obtener más información, consulte las secciones recomendadas [Importación de datos](../../workflow/using/importing-data.md), [Importación de recomendaciones](../../workflow/using/importing-data.md#best-practices-when-importing-data) y [Ejemplo de plantilla para importar](../../workflow/using/importing-data.md#setting-up-a-recurring-import).

![](assets/do-not-localize/how-to-video.png) [Descubra esta función en vídeo](../../platform/using/exporting-and-importing-profiles.md#import-profiles-video)

## Creación de una plantilla de trabajo {#creating-a-job-template}

Las plantillas de importación y exportación se almacenan en el directorio **[!UICONTROL Resources > Templates > Job templates]** del árbol de Adobe Campaign.

De forma predeterminada, hay tres plantillas de importación y una plantilla de exportación en este directorio. No deben modificarse. Puede duplicarlas para crear sus propias plantillas o crear una nueva plantilla a través del menú **[!UICONTROL New > Import template]** / **[!UICONTROL Export template]**.

![](assets/s_ncs_user_export_wizard_template_create.png)

El procedimiento para crear una plantilla de proceso se presenta en [Asistente de exportación](../../platform/using/exporting-data.md#export-wizard) y en [Asistente de importación](../../platform/using/importing-data.md#import-wizard).

>[!NOTE]
>
>La plantilla nativa **[!UICONTROL Import denylist]** ya está configurada para importar una lista de direcciones de correo electrónico que se incluyeron a la de lista de bloqueados.
> 
>Las plantillas **[!UICONTROL New text import]** y **[!UICONTROL New text export]** permiten configurar una importación o exportación desde cero.

## Creación de una nueva importación/exportación {#creating-a-new-import-export}

Una vez configurada la plantilla, se pueden iniciar operaciones de importación y exportación en varios contextos en Adobe Campaign.

Todos ellos abren el asistente de [importación](../../platform/using/importing-data.md) o [exportación](../../platform/using/exporting-data.md#export-wizard) .

* En la sección **[!UICONTROL Profiles and targets]** del espacio de trabajo de Adobe Campaign, haga clic en el vínculo **[!UICONTROL Jobs]**: esto le lleva a la lista de importaciones y exportaciones existentes.

   Haga clic en el botón **[!UICONTROL Create]** y seleccione el tipo de trabajo que desea realizar.

   ![](assets/s_ncs_user_import_from_home.png)

* También puede iniciar importaciones y exportaciones desde la sección Supervisión del espacio de trabajo: dos vínculos dedicados le permiten iniciar la importación o exportación directamente.

   ![](assets/s_ncs_user_import_from_production.png)

* Las importaciones y exportaciones también se pueden iniciar desde el explorador de Adobe Campaign.

   Para exportar o importar datos, haga clic en el nodo **[!UICONTROL Profiles and Targets > Jobs > Generic imports and exports]**, luego en el icono **[!UICONTROL New]** y seleccione **[!UICONTROL Export]** o **[!UICONTROL Import]**. Esto hace que se abra el asistente correspondiente.

   ![](assets/s_ncs_user_export_wizard_launch_from_menu.png)

## Seguimiento de ejecución {#execution-tracking}

Puede ver el seguimiento de la ejecución en la sección superior de este editor. Puede cerrar el asistente de exportación y ver la ejecución del trabajo mediante la lista de trabajos de importación/exportación.

![](assets/s_ncs_user_export_list_and_details.png)

* La pestaña **[!UICONTROL Log]** permite ver los mensajes de registro relacionados con la ejecución.
* La pestaña **[!UICONTROL Rejects]** contiene los registros rechazados. Consulte [Comportamiento en caso de error](../../platform/using/importing-data.md#behavior-in-the-event-of-an-error).

>[!NOTE]
>
>El estado de los trabajos de importación o exportación se presenta en [Estados de trabajo](../../platform/using/importing-data.md#job-statuses).

