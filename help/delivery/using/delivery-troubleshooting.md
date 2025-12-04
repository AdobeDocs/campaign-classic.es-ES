---
product: campaign
title: Solución de problemas de envíos de entregas
description: Obtenga más información sobre el rendimiento de las entregas y cómo solucionar problemas relacionados con la monitorización de entregas
feature: Monitoring, Deliverability, Troubleshooting
role: User
exl-id: 37b1d7fb-7ceb-4647-9aac-c8a80495c5bf
source-git-commit: eac670cd4e7371ca386cee5f1735dc201bf5410a
workflow-type: tm+mt
source-wordcount: '330'
ht-degree: 16%

---

# Solución de problemas de envíos de entregas {#delivery-troubleshooting}

>[!NOTE]
>
>En la documentación de Campaign v8 se documenta una guía completa sobre la resolución de problemas de la entrega, aplicable tanto a los usuarios de Campaign Classic v7 como a los de Campaign v8:
>
>* Errores y soluciones de entrega comunes: [Comprender los errores de entrega](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/send/monitor/delivery-failures){target="_blank"}
>* Diagnóstico de envío lento: [Supervisar los envíos en la interfaz de usuario de Campaign](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/send/monitor/delivery-dashboard){target="_blank"}
>* Prácticas recomendadas de entrega: [Prácticas recomendadas de entrega](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/start/delivery-best-practices){target="_blank"}
>
>Esta página documenta **solución de problemas específica de Campaign Classic v7** para implementaciones híbridas y locales.

## Solución de problemas {#v7-specific}

Para **implementaciones híbridas/locales de Campaign Classic v7**, los siguientes pasos para solucionar problemas son específicos de la infraestructura que administra:

### Configuración de reglas MX

Si tiene problemas de regulación con ISP específicos, es posible que tenga que revisar y ajustar la configuración de las reglas MX. Para obtener más información acerca de las reglas y cuotas MX, consulte [esta sección](../../installation/using/email-deliverability.md#about-mx-rules).

### Mantenimiento de base de datos para rendimiento de envío

Si encuentra el siguiente error en las implementaciones intermediarias:

```
Error during the call of method 'AppendDeliveryPart' on the mid sourcing server: 'Communication error with the server: please check this one is correctly configured. Code HTTP 408 'Service temporarily unavailable'.
```

La causa está relacionada con problemas de rendimiento en los que la instancia de marketing invierte demasiado tiempo creando datos antes de enviarlos al servidor de mid-sourcing.

**Para instalaciones locales**, realice una limpieza y vuelva a indexar la base de datos. Para obtener más información sobre el mantenimiento de la base de datos, consulte [esta sección](../../production/using/recommendations.md).

También debe reiniciar todos los flujos de trabajo con una actividad programada y todos los flujos de trabajo en estado fallido. Consulte [esta sección](../../workflow/using/scheduler.md).

### Monitorización técnica del flujo de trabajo

Para las instalaciones on-premise, asegúrese de que todos los flujos de trabajo técnicos relacionados con la capacidad de entrega se ejecuten sin errores:

**Flujo de trabajo de actualización de la capacidad de envío**: actualiza las reglas de calificación de correo rechazado y los indicadores de capacidad de envío.

**Flujo de trabajo de seguimiento**: Procesa los datos de seguimiento de los envíos enviados.

**Flujo de trabajo de limpieza de la base de datos**: purga con regularidad los registros de envío antiguos y las tablas temporales para mantener el rendimiento.

Comprobar el estado del flujo de trabajo en **[!UICONTROL Administration]** > **[!UICONTROL Production]** > **[!UICONTROL Technical workflows]**.

>[!NOTE]
>
>Adobe administra los flujos de trabajo técnicos y la monitorización de la infraestructura de los usuarios de Cloud Services administrados de Campaign v8. Céntrese en el contenido de envío y el direccionamiento tal como se describe en la [Documentación de Campaign v8](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/send/monitor/delivery-failures){target="_blank"}.

## Temas relacionados

* [Comprender los errores de entrega](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/send/monitor/delivery-failures){target="_blank"} (Documentación de Campaign v8)
* [Prácticas recomendadas de envío](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/start/delivery-best-practices){target="_blank"} (documentación de Campaign v8)
* [Supervisar los envíos en la interfaz de usuario de Campaign](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/send/monitor/delivery-dashboard){target="_blank"} (documentación de Campaign v8)
* [Mantenimiento de la base de datos](../../production/using/recommendations.md) (v7 híbrido/local)
* [Capacidad de entrega de correo electrónico](../../installation/using/email-deliverability.md) (v7 híbrido/local)
