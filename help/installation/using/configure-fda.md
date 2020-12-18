---
solution: Campaign Classic
product: campaign
title: Configurar conectores FDA
description: Conozca los pasos de configuración para FDA
audience: platform
content-type: reference
topic-tags: connectors
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '299'
ht-degree: 70%

---


# Configuración de los conectores FDA {#specific-configurations-by-database-type}

En función de las bases de datos externas a las que desee tener acceso desde Adobe Campaign, debe realizar determinadas configuraciones específicas. Estas configuraciones implican esencialmente la instalación de controladores y la declaración de variables de entorno que pertenecen a cada RDBMS en el servidor de Adobe Campaign.

Como regla general, debe instalar la capa del cliente correspondiente en la base de datos externa en el servidor de Adobe Campaign.

>[!NOTE]
>
>Las versiones compatibles se enumeran en la [Matriz de compatibilidad de Campaign](../../rn/using/compatibility-matrix.md#FederatedDataAccessFDA).


## Pasos de configuración {#fda-configuration-steps}

Para configurar el acceso a una base de datos externa con FDA, los pasos de configuración son:

1. Instalar los controladores correspondientes a su base de datos en el servidor de Adobe Campaign. Los controladores se enumeran en las páginas específicas de la base de datos [a1/>.](#fda-specific-configuration)
1. [Crear y configurar una cuenta externa](../../installation/using/connecting-to-database.md) que permita establecer la conexión entre Adobe Campaign y la base de datos externa. Para obtener más información sobre cuentas externas en Campaña, consulte [esta página](../../installation/using/external-accounts.md).
1. [Crear el esquema](../../installation/using/creating-data-schema.md) de la base de datos externa en Adobe Campaign. Esto permite reconocer la estructura de datos de la base de datos externa.
1. Si es necesario, [cree una nueva asignación de destino](../../installation/using/defining-data-mapping.md) a partir del esquema creado anteriormente. Esto es necesario si los destinatarios de sus envíos provienen de la base de datos externa. Esta implementación incluye limitaciones relacionadas con la personalización de mensajes.

Una vez que se haya creado el esquema, los datos se pueden procesar en los flujos de trabajo de Adobe Campaign. Para obtener más información, consulte [esta sección](../../workflow/using/accessing-an-external-database--fda-.md).

## Configuración específica de la base de datos {#fda-specific-configuration}

En función de las bases de datos externas a las que desee tener acceso desde Adobe Campaign, debe realizar determinadas configuraciones específicas. Estas configuraciones implican esencialmente la instalación de controladores y la declaración de variables de entorno que pertenecen a cada RDBMS en el servidor de Adobe Campaign.

Siga los vínculos siguientes para obtener más información:

* [Azure Synapse](../../installation/using/configure-fda-synapse.md)

* [Snowflake](../../installation/using/configure-fda-snowflake.md)

* [Hadoop](../../installation/using/configure-fda-hadoop.md)

* [Oracle](../../installation/using/configure-fda-oracle.md)

* [Netezza](../../installation/using/configure-fda-netezza.md)

* [Sybase IQ](../../installation/using/configure-fda-sybase.md)

* [Teradata](../../installation/using/configure-fda-teradata.md)

* [SAP HANA](../../installation/using/configure-fda-sap-hana.md)
