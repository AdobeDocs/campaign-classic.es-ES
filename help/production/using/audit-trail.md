---
product: campaign
title: Pista de auditoría
description: Obtenga información sobre cómo monitorizar la instancia con la pista de auditoría de Campaign
feature: Audit Trail, Monitoring, Workflows
badge-v7-only: label="v7" type="Informative" tooltip="Se aplica solo a Campaign Classic v7"
exl-id: 8508d879-fb38-4b1f-9f55-0341bb8d0c67
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: tm+mt
source-wordcount: '468'
ht-degree: 12%

---

# Pista de auditoría{#audit-trail}



En Adobe Campaign, la variable **[!UICONTROL Audit trail]** le permite acceder al historial completo de cambios realizados en su instancia.

**[!UICONTROL Audit trail]** captura, en tiempo real, una lista completa de las acciones y eventos que se producen dentro de la instancia de Adobe Campaign. Incluye una forma de autoservicio de acceder a un historial de datos para responder preguntas como: qué ha pasado con sus flujos de trabajo y quién los actualizó por última vez o qué han hecho los usuarios en la instancia.

>[!NOTE]
>
>Adobe Campaign no audita los cambios realizados en los derechos de usuario, las plantillas, la personalización o las campañas.\
>Solo los administradores de la instancia pueden administrar la pista de auditoría.

La pista de auditoría consta de tres componentes:

* **Pista de auditoría de esquema**: Compruebe las actividades y las últimas modificaciones realizadas en los esquemas.

  Para obtener más información sobre esquemas, consulte [página](../../configuration/using/data-schemas.md).

* **Pista de auditoría de flujo de trabajo**: Compruebe las actividades y las últimas modificaciones realizadas en los flujos de trabajo y, además, el estado de los mismos, como:

   * Start
   * Pause
   * Stop
   * Restart
   * Cleanup que es igual a la acción Purgar historial
   * Simular, que es igual a la acción Iniciar en modo de simulación
   * Activación igual a la acción Ejecutar tareas pendientes ahora
   * Interrupción incondicional

  Para obtener más información sobre los flujos de trabajo, consulte [página](../../workflow/using/about-workflows.md).

  Para obtener más información sobre la monitorización de flujos de trabajo, consulte la [sección dedicada](../../workflow/using/monitoring-workflow-execution.md).

* **Pista de auditoría de opción**: Compruebe las actividades y las últimas modificaciones realizadas en las opciones.

  Para obtener más información, consulte [página](../../installation/using/configuring-campaign-options.md).

## Acceso a Pista de auditoría {#accessing-audit-trail}

Para acceder a la de **[!UICONTROL Audit trail]** :

1. Acceda a la **[!UICONTROL Explorer]** de la instancia.
1. En el **[!UICONTROL Administration]** menú, seleccione **[!UICONTROL Audit]** .

   ![](assets/audit_trail_1.png)

1. El **[!UICONTROL Audit trail]** se abre con la lista de las entidades. Adobe Campaign auditará las acciones de creación, edición y eliminación para flujos de trabajo, opciones y esquemas.

   Seleccione una de las entidades para obtener más información sobre las últimas modificaciones.

   ![](assets/audit_trail_2.png)

1. El **[!UICONTROL Audit entity]** Esta ventana proporciona información más detallada sobre la entidad elegida, como:

   * **[!UICONTROL Type]** : flujo de trabajo, opciones o esquemas.
   * **[!UICONTROL Entity]** : Nombre interno de las actividades.
   * **[!UICONTROL Modified by]** : Nombre de usuario de la última persona que modificó esta entidad por última vez.
   * **[!UICONTROL Action]** : última acción realizada en esta entidad, ya sea Creada, Editada o Eliminada.
   * **[!UICONTROL Modification date]** : Fecha de la última acción realizada en esta entidad.

   El bloque de código proporciona más información sobre lo que se ha cambiado exactamente en la entidad.

   ![](assets/audit_trail_3.png)

>[!NOTE]
>
>De forma predeterminada, el período de retención se establece en 180 días para **[!UICONTROL Audit logs]** . Para obtener más información sobre cómo cambiar el período de retención, consulte esta sección [página](../../production/using/database-cleanup-workflow.md#deployment-wizard).

## Habilitar/deshabilitar pista de auditoría {#enable-disable-audit-trail}

La pista de auditoría se puede activar o desactivar fácilmente para una actividad específica si, por ejemplo, desea ahorrar espacio en la base de datos.

Para ello:

1. Acceda a la **[!UICONTROL Explorer]** de la instancia.
1. En el **[!UICONTROL Administration]** menú, seleccione **[!UICONTROL Platform]** entonces **[!UICONTROL Options]** .

   ![](assets/audit_trail_4.png)

1. Seleccione una de las siguientes opciones en función de la entidad que desee activar/desactivar:

   * Para Flujo De Trabajo: **[!UICONTROL XtkAudit_Workflows]**
   * Para Esquemas: **[!UICONTROL XtkAudit_DataSchema]**
   * Para Opciones: **[!UICONTROL XtkAudit_Option]**
   * Para cada entidad: **[!UICONTROL XtkAudit_Enable_All]**

   ![](assets/audit_trail_5.png)

1. Cambie el **[!UICONTROL Value]** a 1 si desea activar la entidad o a 0 si desea desactivarla.

   ![](assets/audit_trail_6.png)

1. Haga clic en **[!UICONTROL Save]** .
