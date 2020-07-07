---
title: Acceso a una base de datos externa
seo-title: Acceso a una base de datos externa
description: Acceso a una base de datos externa
seo-description: null
page-status-flag: never-activated
uuid: b84359b9-c584-431d-80d5-71146d9b6854
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: platform
content-type: reference
topic-tags: connectors
discoiquuid: dd3d14cc-5153-428d-a98a-32b46f0fe811
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: c86af066045c1c35b51624de8565af21746354c1
workflow-type: tm+mt
source-wordcount: '580'
ht-degree: 96%

---


# Acerca del Acceso a Datos Federados {#about-federated-data-access}

Adobe Campaign proporciona la opción **Acceso de Datos Federados** (FDA) para procesar la información almacenada en una o más bases de datos externas: puede acceder a datos externos sin cambiar la estructura de los datos de Adobe Campaign.

>[!CAUTION]
>
>El acceso a una base de datos externa mediante FDA solo es posible para instalaciones in situ o híbridas, excepto con los conectores Snowflake. Para obtener más información, consulte [esta página](https://helpx.adobe.com/es/campaign/kb/acc-on-prem-vs-hosted.html).

## Principio de funcionamiento {#operating-principle}

La opción FDA le permite ampliar el modelo de datos en una base de datos de terceros. Detecta automáticamente la estructura de las tablas de destino y utiliza datos de los orígenes SQL.

Para utilizar esta función, tiene que:

1. Poseer una base de datos externa compatible con el módulo FDA de Adobe Campaign. La lista de sistemas de bases de datos y versiones compatibles se detalla en la [matriz de compatibilidad](https://helpx.adobe.com/es/campaign/kb/compatibility-matrix.html). Los usuarios también deben tener los [permisos necesarios](../../platform/using/remote-database-access-rights.md) en Adobe Campaign y en la base de datos externa.
1. [Instalar los controladores](../../platform/using/specific-configuration-database.md) correspondientes a su base de datos en el servidor de Adobe Campaign.
1. [Crear y configurar una cuenta externa](../../platform/using/connecting-to-database.md) que permita establecer la conexión entre Adobe Campaign y la base de datos externa. Para obtener más información sobre cuentas externas disponibles, consulte [esta página](../../platform/using/external-accounts.md). 
1. [Crear el esquema](../../platform/using/creating-data-schema.md) de la base de datos externa en Adobe Campaign. Esto permite reconocer la estructura de datos de la base de datos externa.
1. Finalmente, [crear una nueva asignación de objetivo](../../platform/using/defining-data-mapping.md) desde el esquema creado anteriormente, en caso de que los destinatarios de las entregas provengan de la base de datos externa. Esto presenta ciertas limitaciones, especialmente en relación con la personalización de las entregas.

Una vez que se haya creado el esquema, los datos se pueden procesar en los flujos de trabajo de Adobe Campaign. Para obtener más información, consulte [esta sección](../../workflow/using/accessing-an-external-database--fda-.md).

## Bases de datos externas disponibles {#external-database}

A continuación se encuentra la lista de cada base de datos externa compatible con el módulo de FDA Adobe Campaign:

* Microsoft Azure Synapse Analytics. Para obtener más información, consulte [esta sección](../../platform/using/specific-configuration-database.md#azure-external).
* Snowflake. Para obtener más información, consulte [esta sección](../../platform/using/specific-configuration-database.md#configure-access-to-snowflake).
* Hadoop. Para obtener más información, consulte [esta sección](../../platform/using/specific-configuration-database.md#configure-access-to-hadoop-3).
* Oracle. Para obtener más información, consulte [esta sección](../../platform/using/specific-configuration-database.md#configure-access-to-oracle).
* Netezza. Para obtener más información, consulte [esta sección](../../platform/using/specific-configuration-database.md#configure-access-to-netezza).
* Sybase IQ. Para obtener más información, consulte [esta sección](../../platform/using/specific-configuration-database.md#configure-access-to-sybase-iq).
* Teradata. Para obtener más información, consulte [esta sección](../../platform/using/specific-configuration-database.md#configure-access-to-teradata).
* SAP HANA. Para obtener más información, consulte [esta sección](../../platform/using/specific-configuration-database.md).

## Buenas prácticas y recomendaciones {#best-practices-and-recommendations}

La opción FDA se realiza para manipular los datos en bases de datos externas en modo de lote en los flujos de trabajo. El uso de FDA en otro contexto, por ejemplo para las operaciones unitarias, se debe llevar a cabo con precaución (personalización, interacción, entregas en tiempo real, etc.).

Evite en la medida de lo posible las operaciones que requieran utilizar tanto Adobe Campaign como la base de datos externa. Para ello, puede hacer lo siguiente:

* Exporte la base de datos de Adobe Campaign a la base de datos externa y ejecute las operaciones solo desde la base de datos externa antes de volver a importar los resultados en Adobe Campaign.
* Recopile los datos de la base de datos externa de Adobe Campaign y ejecute las operaciones localmente.

Si desea personalizar las entregas utilizando datos de la base de datos externa, recopile los datos para utilizarlos en un flujo de trabajo para que estén disponibles en una tabla temporal. A continuación, utilice los datos de la tabla temporal para personalizar su envío.

## Limitaciones {#limitations}

La opción FDA está sujeta a la limitación del sistema externo de base de datos que utiliza.

Por motivos de rendimiento, no se recomienda utilizar esta funcionalidad para llevar a cabo operaciones unitarias (personalización de entrega, módulo de interacción, tiempo real).
