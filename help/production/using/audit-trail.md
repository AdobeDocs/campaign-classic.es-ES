---
title: Pista de auditoría
seo-title: Pista de auditoría
description: Pista de auditoría
seo-description: null
page-status-flag: never-activated
uuid: b96b93b6-e002-4c67-b9ce-b66cdcd395d7
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: production
content-type: reference
topic-tags: production-procedures
discoiquuid: aa147a8c-9d93-45c8-bb4a-db714739f4c0
translation-type: tm+mt
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: tm+mt
source-wordcount: '455'
ht-degree: 4%

---


# Pista de auditoría{#audit-trail}

En Adobe Campaign, **[!UICONTROL Audit trail]** le permite acceder al historial completo de cambios realizados en la instancia.

**[!UICONTROL Audit trail]** captura, en tiempo real, una lista completa de acciones y eventos que se producen en la instancia de Adobe Campaign. Incluye una forma de autoservicio de acceder a un historial de datos para responder preguntas como: qué les pasó a sus flujos de trabajo y quién los actualizó por última vez o qué hicieron los usuarios en la instancia.

>[!NOTE]
>
>Adobe Campaign no audita los cambios realizados en los derechos de usuario, las plantillas, la personalización o las campañas.\
>La pista de auditoría solo puede ser administrada por los administradores de la instancia.

La pista de auditoría consta de tres componentes:

* **Pista** de auditoría de esquema: Compruebe las actividades y las últimas modificaciones realizadas a sus esquemas.

   For more information on schemas, refer to this [page](../../configuration/using/data-schemas.md).

* **Pista** de auditoría de flujo de trabajo: Compruebe las actividades y las últimas modificaciones realizadas en los flujos de trabajo, y además, el estado de sus flujos de trabajo, como:

   * Start
   * Pause
   * Stop
   * Restart
   * Cleanup que equivale al historial de purga de acciones
   * Simular qué es igual al Inicio de acción en modo de simulación
   * Despertar que es igual a la acción Ejecutar tareas pendientes ahora
   * Interrupción incondicional

   For more information on workflows, refer to this [page](../../workflow/using/about-workflows.md).

   For more on how to monitor workflows, refer to the [dedicated section](../../workflow/using/monitoring-workflow-execution.md).

* **Pista** de auditoría de opciones: Compruebe las actividades y las últimas modificaciones realizadas en las opciones.

   For more information on options, refer to this [page](../../installation/using/configuring-campaign-options.md).

## Acceso a pista de auditoría {#accessing-audit-trail}

Para acceder a la sección **[!UICONTROL Audit trail]** :

1. Acceda al **[!UICONTROL Explorer]** menú de su instancia.
1. En el **[!UICONTROL Administration]** menú, seleccione **[!UICONTROL Audit]** .

   ![](assets/audit_trail_1.png)

1. La **[!UICONTROL Audit trail]** ventana se abre con la lista de las entidades. Adobe Campaign auditará las acciones de creación, edición y eliminación de flujos de trabajo, opciones y esquemas.

   Seleccione una de las entidades para obtener más información sobre las últimas modificaciones.

   ![](assets/audit_trail_2.png)

1. La **[!UICONTROL Audit entity]** ventana proporciona información más detallada sobre la entidad elegida, como:

   * **[!UICONTROL Type]** :: Flujo de trabajo, opciones o Esquemas.
   * **[!UICONTROL Entity]** :: Nombre interno de sus actividades.
   * **[!UICONTROL Modified by]** :: Nombre de usuario de la última persona que modificó esta entidad por última vez.
   * **[!UICONTROL Action]** :: Última acción realizada en esta entidad, ya sea Creada, Editada o Eliminada.
   * **[!UICONTROL Modification date]** :: Fecha de la última acción realizada en esta entidad.

   El bloque de código le proporciona más información sobre qué se cambió exactamente en su entidad.

   ![](assets/audit_trail_3.png)

>[!NOTE]
>
>De forma predeterminada, el período de retención se establece en 180 días para **[!UICONTROL Audit logs]** . Para obtener más información sobre cómo cambiar el período de retención, consulte esta [página](../../production/using/database-cleanup-workflow.md#deployment-wizard).

## Habilitar o deshabilitar la pista de auditoría {#enable-disable-audit-trail}

La pista de auditoría se puede activar o desactivar fácilmente para una actividad específica si, por ejemplo, desea ahorrar espacio en la base de datos.

Para ello:

1. Acceda al **[!UICONTROL Explorer]** menú de su instancia.
1. En el **[!UICONTROL Administration]** menú, seleccione **[!UICONTROL Platform]** y luego **[!UICONTROL Options]** .

   ![](assets/audit_trail_4.png)

1. Seleccione una de las siguientes opciones en función de la entidad que desee activar o desactivar:

   * Para flujo de trabajo: **[!UICONTROL XtkAudit_Workflows]**
   * Para Esquemas: **[!UICONTROL XtkAudit_DataSchema]**
   * Para opciones: **[!UICONTROL XtkAudit_Option]**
   * Para cada entidad: **[!UICONTROL XtkAudit_Enable_All]**

   ![](assets/audit_trail_5.png)

1. Cambie el **[!UICONTROL Value]** a 1 si desea habilitar la entidad o a 0 si desea deshabilitarla.

   ![](assets/audit_trail_6.png)

1. Haga clic en **[!UICONTROL Save]** .

