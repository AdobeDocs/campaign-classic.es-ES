---
solution: Campaign Classic
product: campaign
title: Acceso a una base de datos externa
description: Obtenga información sobre cómo acceder y procesar datos en una base de datos externa
audience: platform
content-type: reference
topic-tags: connectors
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '590'
ht-degree: 41%

---


# Introducción a Acceso de datos federado {#about-federated-data-access}

Adobe Campaign proporciona la opción **Acceso de Datos Federados** (FDA) para procesar la información almacenada en una o más bases de datos externas: puede acceder a datos externos sin cambiar la estructura de los datos de Adobe Campaign.

## Requisitos previos {#operating-principle}

La opción FDA le permite ampliar el modelo de datos en una base de datos de terceros. Detecta automáticamente la estructura de las tablas de destino y utiliza datos de los orígenes SQL.

Para utilizar esta capacidad, los requisitos previos se enumeran a continuación:

* **Configuración**: excepto para el Snowflake, necesita un modelo  **de alojamiento** local o  **** híbrido para configurar el Acceso de datos federado. [Obtenga más información](../../installation/using/hosting-models.md)
* **Versión** de base de datos externa: necesita tener una base de datos externa que sea compatible con el módulo de Adobe Campaign FDA. La lista de los sistemas de bases de datos y las versiones compatibles se detalla en la Campaña [Tabla de compatibilidad](../../rn/using/compatibility-matrix.md#FederatedDataAccessFDA).
* **Permisos**: los usuarios también deben tener los  [permisos ](../../installation/using/remote-database-access-rights.md) necesarios en Adobe Campaign y en la base de datos externa.

## Limitaciones {#limitations}

La opción FDA se realiza para manipular los datos en bases de datos externas en modo de lote en los flujos de trabajo. Para evitar problemas de rendimiento, no se recomienda utilizar el módulo FDA en el contexto de operaciones unitarias, como: personalización, interacción, mensajes en tiempo real, etc.

Evite en la medida de lo posible las operaciones que requieran utilizar tanto Adobe Campaign como la base de datos externa. Para ello, puede hacer lo siguiente:

* Exporte la base de datos de Adobe Campaign a la base de datos externa y ejecute las operaciones solo desde la base de datos externa antes de volver a importar los resultados en Adobe Campaign.

* Recopile los datos de la base de datos externa de Adobe Campaign y ejecute las operaciones localmente.

Si desea personalizar las entregas utilizando datos de la base de datos externa, recopile los datos para utilizarlos en un flujo de trabajo para que estén disponibles en una tabla temporal. A continuación, utilice los datos de la tabla temporal para personalizar su envío.

La opción FDA está sujeta a las limitaciones del sistema de bases de datos externas que utilice.

## Recomendaciones {#recommendations}

### Crear esquemas temporales {#create-temporary-schemas}

Puede administrar varios accesos a la base de datos externa de Greenplum mediante FDA. Una opción dedicada permite crear un esquema de trabajo directamente al configurar la cuenta externa.

![](assets/fda_work_table.png)

>[!NOTE]
>
>Esta opción solo está disponible con Greenplum PostgreSQL.

### Optimizar la personalización del correo electrónico con datos externos {#optimizing-email-personalization-with-external-data}

Puede preprocesar la personalización de mensajes en un flujo de trabajo dedicado. Para realizar esto, utilice la opción **[!UICONTROL Prepare the personalization data with a workflow]**, disponible en la ficha **[!UICONTROL Analysis]** de las propiedades de envío.

Durante la análisis de envío, esta opción crea y ejecuta automáticamente un flujo de trabajo que almacena todos los datos vinculados al destinatario en una tabla temporal, incluidos los datos de tablas vinculadas en una base de datos externa.

Esta opción mejora significativamente el rendimiento al ejecutar el paso de personalización.

### Utilizar datos de una base de datos externa en un flujo de trabajo {#using-data-from-an-external-database-in-a-workflow}

En varias actividades de flujo de trabajo de Adobe Campaign, puede utilizar los datos almacenados en una base de datos externa.

* **Filtrar datos**  externos: La actividad de  [](../../workflow/using/targeting-data.md#selecting-data) consulta le permite agregar datos externos y usarlos en las configuraciones de filtro definidas. Para obtener más información, consulte [esta página](../../workflow/using/targeting-data.md#selecting-data).

* **Crear subconjuntos** : la  [](../../workflow/using/split.md) actividad de la división permite crear subconjuntos. Puede utilizar datos externos para definir los criterios de filtrado que deben utilizarse. Para obtener más información, consulte [esta página](../../workflow/using/split.md).

* **Cargar base de datos**  externa: puede utilizar los datos externos en la actividad de carga [ de ](../../workflow/using/data-loading--rdbms-.md) datos (RDBMS). Obtenga más información en [esta página](../../workflow/using/data-loading--rdbms-.md).

* **Añadir información y vínculos** : la actividad  [](../../workflow/using/enrichment.md) Enriquecimiento permite agregar datos adicionales a la tabla de trabajo del flujo de trabajo y vínculos a una tabla externa. En este contexto, puede utilizar datos de una base de datos externa. Obtenga más información en [esta página](../../workflow/using/enrichment.md).
