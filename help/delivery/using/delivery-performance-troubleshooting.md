---
product: campaign
title: Rendimiento de entrega y solución de problemas
description: Obtenga información sobre cómo optimizar el rendimiento de la entrega y solucionar problemas en Campaign Classic v7
feature: Monitoring, Deliverability, Troubleshooting
role: User, Developer
exl-id: cc793d7b-0a26-4a75-97ed-d79c87d9b3b8
source-git-commit: 2ebae2b84741bf26dd44c872702dbf3b0ebfc453
workflow-type: tm+mt
source-wordcount: '665'
ht-degree: 5%

---

# Rendimiento de entrega y solución de problemas {#delivery-performance-troubleshooting}

>[!NOTE]
>
>Encontrará instrucciones detalladas sobre el rendimiento de las entregas y las prácticas recomendadas en la página [Prácticas recomendadas de entrega de Campaign v8](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/start/delivery-best-practices). Este contenido se aplica tanto a los usuarios de Campaign Classic v7 como a los de Campaign v8.
>
>Esta página documenta **configuraciones específicas de Campaign Classic v7** para la optimización del rendimiento y la solución de problemas en implementaciones híbridas y locales.

Para obtener prácticas recomendadas completas sobre el rendimiento de entrega, la optimización de la plataforma, la administración de cuarentena, el mantenimiento de la base de datos y las recomendaciones de programación, consulte la [documentación de prácticas recomendadas de entrega de Campaign v8](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/start/delivery-best-practices){target="_blank"}.

## Optimización del rendimiento {#performance-optimization}

Para **implementaciones híbridas/locales de Campaign Classic v7**, las siguientes optimizaciones de infraestructura y base de datos pueden mejorar el rendimiento de la entrega.

### Optimización de base de datos

**Direcciones de índice** para optimizar el rendimiento de las consultas SQL utilizadas en la aplicación. Se puede declarar un índice a partir del elemento principal del esquema de datos. Esta optimización requiere acceso directo a la base de datos y personalización de esquemas disponible en implementaciones locales.

### Ajuste de infraestructura

**Configuración de envíos grandes**: los envíos a más de un millón de destinatarios necesitan espacio en las colas de envío. Para instalaciones on-premise, los elementos secundarios de MTA se pueden configurar para gestionar tamaños de lote personalizados. Póngase en contacto con el administrador del sistema para ajustar esta configuración en función de la capacidad de la infraestructura.

>[!NOTE]
>
>Adobe administra la optimización de la infraestructura y la configuración de MTA para los usuarios de Cloud Services administrados de Campaign v8. Consulte las [prácticas recomendadas de entrega de Campaign v8](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/start/delivery-best-practices){target="_blank"} para obtener recomendaciones de rendimiento aplicables a su implementación.

### Mantenimiento de la base de datos {#database-maintenance}

Para **implementaciones híbridas/locales de Campaign Classic v7**, el mantenimiento de la plataforma y la base de datos afecta directamente el rendimiento de entrega.

Las tareas de mantenimiento regulares incluyen:

**Limpieza de la base de datos**: utilice el flujo de trabajo de limpieza de la base de datos para quitar los registros de envío antiguos, los datos de seguimiento y las tablas temporales. Un mantenimiento deficiente de la base de datos puede ralentizar la preparación y el envío.

**Supervisión del rendimiento de la base de datos**: supervise el rendimiento de las consultas, la fragmentación de índices y las estadísticas de tablas. Para obtener instrucciones detalladas, consulte [esta página](../../production/using/database-performances.md).

**Supervisión técnica del flujo de trabajo**: Asegúrese de que todos los flujos de trabajo técnicos (especialmente los flujos de trabajo de limpieza, seguimiento y actualización de la capacidad de envío) se ejecuten correctamente sin errores.

>[!NOTE]
>
>Adobe supervisa y administra el mantenimiento de la base de datos y los flujos de trabajo técnicos de los usuarios de Cloud Services administrados de Campaign v8. Céntrese en la monitorización específica de la entrega como se describe en [Documentación de entregas del Monitor de Campaign v8](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/send/monitoring-deliverability){target="_blank"}.

## Solución de problemas de entrega {#troubleshooting}

>[!NOTE]
>
>En la documentación de Campaign v8 se documenta una guía completa sobre la resolución de problemas de la entrega, aplicable tanto a los usuarios de Campaign Classic v7 como a los de Campaign v8:
>
>* Errores y soluciones de entrega comunes: [Comprender los errores de entrega](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/send/monitor/delivery-failures){target="_blank"}
>* Diagnóstico de envío lento: [Supervisar los envíos en la interfaz de usuario de Campaign](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/send/monitor/delivery-dashboard){target="_blank"}
>* Prácticas recomendadas de entrega: [Prácticas recomendadas de entrega](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/start/delivery-best-practices){target="_blank"}
>
>Esta sección describe la solución de problemas **específica de Campaign Classic v7** para implementaciones híbridas y locales.

Para **implementaciones híbridas/locales de Campaign Classic v7**, los siguientes pasos para solucionar problemas son específicos de la infraestructura que administra.

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
* [Rendimiento de la base de datos](../../production/using/database-performances.md) (v7 híbrido/local)

