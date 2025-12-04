---
product: campaign
title: Comprensión de la administración de cuarentenas
description: Comprensión de la administración de cuarentenas
feature: Monitoring, Deliverability
role: User
exl-id: cfd8f5c9-f368-4a31-a1e2-1d77ceae5ced
source-git-commit: eac670cd4e7371ca386cee5f1735dc201bf5410a
workflow-type: tm+mt
source-wordcount: '576'
ht-degree: 2%

---

# Comprensión de la administración de cuarentenas{#understanding-quarantine-management}

>[!NOTE]
>
>Encontrará instrucciones detalladas sobre la administración de cuarentena en la página [Administración de cuarentena de Campaign v8](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/send/monitor/quarantines). Este contenido se aplica tanto a los usuarios de Campaign Classic v7 como a los de Campaign v8 y cubre lo siguiente:
>
>* Cuarentena frente a conceptos de lista de bloqueados
>* Por qué las direcciones se envían a cuarentena (errores graves/leves)
>* Umbrales de administración de errores en software y contador de errores
>* Acceso e identificación de direcciones en cuarentena
>* Eliminación de direcciones de la cuarentena (automática, manual, masiva)
>* Informes de administración de cuarentena
>
>Esta página documenta **la configuración específica de Campaign Classic v7** para la administración de cuarentena en implementaciones híbridas y locales.

Para obtener instrucciones detalladas sobre la administración de cuarentena, consulte la [Documentación de administración de cuarentena de Campaign v8](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/send/monitor/quarantines){target="_blank"}.

## Configuración de cuarentena {#v7-quarantine-config}

Las siguientes opciones de configuración están disponibles para **implementaciones híbridas/locales de Campaign Classic v7** con el fin de personalizar el comportamiento de la cuarentena.

### Configuración del umbral de error leve {#soft-error-threshold}

Para las instalaciones on-premise que utilizan el servidor de correo de Campaign heredado, puede modificar el número de errores y el periodo entre dos errores antes de que una dirección se ponga en cuarentena.

Para establecer esta configuración:

1. Acceda al asistente de implementación desde **[!UICONTROL Tools]** > **[!UICONTROL Advanced]** > **[!UICONTROL Deployment wizard]**
2. Vaya a **[!UICONTROL Email channel]** > **[!UICONTROL Advanced parameters]**
3. Configurar:
   * **Número de errores**: El número máximo de errores leves antes de poner una dirección en cuarentena (predeterminado: 5)
   * **Período entre dos errores significativos**: Período de tiempo (en segundos) para el recuento de errores (predeterminado: 86 400 segundos = 1 día)

Cuando el contador de errores alcanza el umbral, la dirección se pone en cuarentena. Si el último error significativo se produjo hace más de 10 días, el contador de errores se reinicia.

Para obtener más información, consulte [esta página](communication-channels.md) en **Envío de entregas** > **Configurar reintentos**.

>[!NOTE]
>
>Para los usuarios de Cloud Services administrados de Campaign v8, la configuración de reintentos y los umbrales de error los administra Adobe en función del rendimiento de la IP y la reputación del dominio. No se requiere ninguna configuración.

### Flujo de trabajo para limpieza de bases de datos {#database-cleanup-workflow}

Para instalaciones on-premise, el flujo de trabajo técnico **[!UICONTROL Database cleanup]** elimina automáticamente las direcciones en cuarentena que coinciden con condiciones específicas.

Acceda a este flujo de trabajo desde **[!UICONTROL Administration]** > **[!UICONTROL Production]** > **[!UICONTROL Technical workflows]** > **[!UICONTROL Database cleanup]**.

El flujo de trabajo elimina las direcciones de la cuarentena en los siguientes casos:

* Direcciones en estado **[!UICONTROL With errors]** después de un envío correcto
* Direcciones con estado **[!UICONTROL With errors]** si el último rebote suave se produjo hace más de 10 días
* Direcciones en estado **[!UICONTROL With errors]** con error **[!UICONTROL Mailbox full]** después de 30 días

Asegúrese de que este flujo de trabajo se ejecute regularmente (recomendado: diariamente) para mantener la higiene de la lista de cuarentena.

Para obtener más información sobre limpieza de bases de datos, consulte [esta sección](../../production/using/database-cleanup-workflow.md).

>[!NOTE]
>
>Para los usuarios de Cloud Services administrados de Campaign v8, Adobe supervisa y administra el flujo de trabajo de limpieza de la base de datos.

### Detalles específicos de cuarentena de notificaciones push {#push-quarantine-specifics}

Para Campaign Classic v7, las cuarentenas de notificaciones push siguen el mecanismo de cuarentena general con algunos comportamientos específicos del canal.

Para las notificaciones push de **iOS** y **Android**, el mecanismo de cuarentena utiliza tokens de dispositivo en lugar de direcciones de correo electrónico. Cuando se desinstala o se vuelve a instalar una aplicación móvil, el token asociado se pone en cuarentena.

Para obtener información detallada sobre los escenarios de cuarentena de notificaciones push (tipos de error de iOS y Android, comportamiento de reintentos, etc.), consulte la documentación de [Explicación de los errores de entrega](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/send/monitor/delivery-failures){target="_blank"}, que incluye tablas completas de tipos de errores de notificaciones push.

### Detalles específicos de cuarentena de SMS {#sms-quarantine-specifics}

Para Campaign Classic v7, las cuarentenas de SMS siguen el mecanismo de cuarentena general con algunos comportamientos específicos del canal relacionados con los números de teléfono en lugar de las direcciones de correo electrónico.

El mecanismo de cuarentena del SMS varía según el conector utilizado:

* **Conectores SMPP estándar**: Las reglas de calificación de errores definidas en **[!UICONTROL Administration > Campaign Management > Non deliverables Management > Delivery log qualification]** se aplican a los envíos SMS.

* **Conector SMPP genérico extendido**: la administración de errores se administra de forma diferente mediante expresiones regulares (regex) para analizar los mensajes de informe de estado (SR) devueltos por el proveedor SMSC.

Para obtener información detallada sobre los escenarios de cuarentena de SMS y los tipos de error, consulte la documentación de [Explicación de los errores de entrega](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/send/monitor/delivery-failures){target="_blank"}, que incluye tablas completas de tipos de errores de SMS.

## Temas relacionados

* [Administración de cuarentena](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/send/monitor/quarantines){target="_blank"} (documentación de Campaign v8)
* [Comprender los errores de entrega](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/send/monitor/delivery-failures){target="_blank"} (Documentación de Campaign v8)
* [Prácticas recomendadas de envío](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/start/delivery-best-practices){target="_blank"} (documentación de Campaign v8)
* [Flujo de trabajo de limpieza de la base de datos](../../production/using/database-cleanup-workflow.md) (v7 híbrido/local)
* [Configurar reintentos de entrega](communication-channels.md) (v7 híbrido/local)
