---
product: campaign
title: Prácticas recomendadas y limitaciones de FDA Campaign
description: Conozca las prácticas recomendadas y las limitaciones al trabajar con una base de datos externa (FDA)
feature: Installation, Federated Data Access
audience: platform
content-type: reference
topic-tags: connectors
exl-id: f3980859-2837-416b-a0ef-2b369d2d50bd
source-git-commit: 0ed70b3c57714ad6c3926181334f57ed3b409d98
workflow-type: tm+mt
source-wordcount: '456'
ht-degree: 29%

---

# Prácticas recomendadas y limitaciones



## Optimización de la personalización de correo electrónico con datos externos {#optimizing-email-personalization-with-external-data}

Puede preprocesar la personalización de mensajes en un flujo de trabajo dedicado. Para ello, utilice la opción **[!UICONTROL Prepare the personalization data with a workflow]**, disponible en la pestaña **[!UICONTROL Analysis]** de las propiedades de entrega.

Durante el análisis de envío, esta opción crea y ejecuta automáticamente un flujo de trabajo que almacena todos los datos vinculados con el objetivo en una tabla temporal, incluidos los datos de tablas vinculadas en una base de datos externa.

Esta opción mejora significativamente el rendimiento al ejecutar el paso de personalización.

## Uso de datos de una base de datos externa en un flujo de trabajo {#using-data-from-an-external-database-in-a-workflow}

En varias actividades de flujo de trabajo de Adobe Campaign, puede utilizar los datos almacenados en una base de datos externa.

* **Filtrar datos externos**: la actividad [Consulta](../../workflow/using/targeting-data.md#selecting-data) le permite agregar datos externos y utilizarlos en las configuraciones de filtro definidas. Para obtener más información, consulte [esta página](../../workflow/using/targeting-data.md#selecting-data).

* **Crear subconjuntos**: la actividad [Split](../../workflow/using/split.md) le permite crear subconjuntos. Se pueden utilizar datos externos para definir los criterios de filtrado que se deben utilizar. Para obtener más información, consulte [esta página](../../workflow/using/split.md).

* **Cargar base de datos externa**: puede utilizar los datos externos en la actividad [Carga de datos](../../workflow/using/data-loading-rdbms.md) (RDBMS). Obtenga más información en [esta página](../../workflow/using/data-loading-rdbms.md).

* **Agregar información y vínculos** - La actividad [Enriquecimiento](../../workflow/using/enrichment.md) le permite agregar datos adicionales a la tabla de trabajo del flujo de trabajo y vínculos a una tabla externa. En este contexto, puede utilizar datos de una base de datos externa. Obtenga más información en [esta página](../../workflow/using/enrichment.md).

## Mecanismos de protección y limitaciones {#fda-limitations}

La opción FDA está diseñada para manipular los datos en bases de datos externas en modo de lote en los flujos de trabajo. Para evitar problemas de rendimiento, no se recomienda utilizar el módulo FDA en el contexto de operaciones unitarias, como: personalización, interacción, mensajería en tiempo real, etc.

No se admiten los datos de destino de una base de datos y el filtrado de los resultados mediante una dimensión de filtrado que pertenezca a otra base de datos. No se pueden combinar tablas que estén en diferentes orígenes de datos en una consulta. Puede superar esta limitación utilizando otras actividades de flujo de trabajo como Change dimension.

Evite en la medida de lo posible las operaciones que requieran utilizar tanto Adobe Campaign como la base de datos externa. La práctica recomendada es:

* Exporte la base de datos de Adobe Campaign a la base de datos externa y ejecute las operaciones solo desde la base de datos externa antes de volver a importar los resultados en Adobe Campaign.

* Recopile los datos de la base de datos externa de Adobe Campaign y ejecute las operaciones localmente.

Si desea personalizar las entregas utilizando datos de la base de datos externa, recopile los datos para utilizarlos en un flujo de trabajo para que estén disponibles en una tabla temporal. A continuación, utilice los datos de la tabla temporal para personalizar su envío.

La opción FDA está sujeta a las limitaciones del sistema de base de datos externo que utiliza.
