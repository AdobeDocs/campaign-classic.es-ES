---
product: campaign
title: Prácticas recomendadas sobre el rendimiento de los envíos
description: Obtenga más información sobre el rendimiento de los envíos y las prácticas recomendadas
feature: Deliverability
role: User, Developer
exl-id: cc793d7b-0a26-4a75-97ed-d79c87d9b3b8
source-git-commit: eac670cd4e7371ca386cee5f1735dc201bf5410a
workflow-type: tm+mt
source-wordcount: '362'
ht-degree: 6%

---

# Prácticas recomendadas sobre el rendimiento de los envíos {#delivery-performances}

>[!NOTE]
>
>Encontrará instrucciones detalladas sobre el rendimiento de las entregas y las prácticas recomendadas en la página [Prácticas recomendadas de entrega de Campaign v8](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/start/delivery-best-practices). Este contenido se aplica tanto a los usuarios de Campaign Classic v7 como a los de Campaign v8.
>
>Esta página documenta **configuraciones de rendimiento específicas de Campaign Classic v7** para implementaciones híbridas y locales.

Para obtener prácticas recomendadas completas sobre el rendimiento de entrega, la optimización de la plataforma, la administración de cuarentena, el mantenimiento de la base de datos y las recomendaciones de programación, consulte la [documentación de prácticas recomendadas de entrega de Campaign v8](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/start/delivery-best-practices){target="_blank"}.

## Ajuste del rendimiento {#best-practices-performance}

Para **implementaciones híbridas/locales de Campaign Classic v7**, las siguientes optimizaciones de infraestructura y base de datos pueden mejorar el rendimiento de la entrega:

### Optimización de base de datos

**Direcciones de índice** para optimizar el rendimiento de las consultas SQL utilizadas en la aplicación. Se puede declarar un índice a partir del elemento principal del esquema de datos. Esta optimización requiere acceso directo a la base de datos y personalización de esquemas disponible en implementaciones locales.

### Ajuste de infraestructura

**Configuración de envíos grandes**: los envíos a más de un millón de destinatarios necesitan espacio en las colas de envío. Para instalaciones on-premise, los elementos secundarios de MTA se pueden configurar para gestionar tamaños de lote personalizados. Póngase en contacto con el administrador del sistema para ajustar esta configuración en función de la capacidad de la infraestructura.

>[!NOTE]
>
>Adobe administra la optimización de la infraestructura y la configuración de MTA para los usuarios de Cloud Services administrados de Campaign v8. Consulte las [prácticas recomendadas de entrega de Campaign v8](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/start/delivery-best-practices){target="_blank"} para obtener recomendaciones de rendimiento aplicables a su implementación.

## Mantenimiento de la base de datos {#performance-issues}

Para **implementaciones híbridas/locales de Campaign Classic v7**, el mantenimiento de la plataforma y la base de datos afecta directamente el rendimiento de entrega.

Las tareas de mantenimiento regulares incluyen:

**Limpieza de la base de datos**: utilice el flujo de trabajo de limpieza de la base de datos para quitar los registros de envío antiguos, los datos de seguimiento y las tablas temporales. Un mantenimiento deficiente de la base de datos puede ralentizar la preparación y el envío.

**Supervisión del rendimiento de la base de datos**: supervise el rendimiento de las consultas, la fragmentación de índices y las estadísticas de tablas. Para obtener instrucciones detalladas, consulte [esta página](../../production/using/database-performances.md).

**Supervisión técnica del flujo de trabajo**: Asegúrese de que todos los flujos de trabajo técnicos (especialmente los flujos de trabajo de limpieza, seguimiento y actualización de la capacidad de envío) se ejecuten correctamente sin errores.

>[!NOTE]
>
>Adobe supervisa y administra el mantenimiento de la base de datos y los flujos de trabajo técnicos de los usuarios de Cloud Services administrados de Campaign v8. Céntrese en la monitorización específica de la entrega como se describe en [Documentación de entregas del Monitor de Campaign v8](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/send/monitoring-deliverability){target="_blank"}.

## Temas relacionados

* [Prácticas recomendadas de envío](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/start/delivery-best-practices){target="_blank"} (documentación de Campaign v8)
* [Monitorice su capacidad de entrega](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/send/monitoring-deliverability){target="_blank"} (documentación de Campaign v8)
* [Solución de problemas de envío](delivery-troubleshooting.md)
* [Rendimiento de la base de datos](../../production/using/database-performances.md) (v7 híbrido/local)
