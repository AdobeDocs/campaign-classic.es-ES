---
product: campaign
title: Configuración de conectores FDA
description: Conozca los pasos de configuración para FDA
feature: Installation, Federated Data Access
audience: platform
content-type: reference
topic-tags: connectors
exl-id: 0b53b165-a6d8-4604-b3f0-3fa6fce35146
TQID: 'https://experienceleague.adobe.com/F1-F9k9cn7jFb-xmYCQUq5h1-3A6-bajr1cfxeHNPf0'
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
    internal-label: Campaign
  - id: fd6e6e36-54e4-4f1a-96fc-1a750e400d50
    internal-label: Campaign Classic v7
feature_v2:
  - id: c5474392-5419-4296-9e41-f6f4ce4f6e9b
    internal-label: Administration
  - id: a658c786-869b-4194-a780-2594d663adda
    internal-label: Data management
subfeature_v2:
  - id: e656c701-3899-4db3-989c-de0980ddfffa
    internal-label: Installation
  - id: ee3dfd63-9a21-4961-9f24-ea3385284a21
    internal-label: Federated Data Access
topic_v2:
  - id: b5ce8718-c3af-4fdb-a1a9-fca32f83a87c
    internal-label: Implementation
  - id: cdd65e7e-8839-44a2-bc21-0e03623b5dd1
    internal-label: Optimization
  - id: e0eb8757-182f-49f3-94a4-1587d16f5094
    internal-label: Personalization
source-git-commit: a43e591a565a18d79f583d975e3e812c5435b0c0
workflow-type: tm+mt
source-wordcount: '355'
ht-degree: 38%
---
# Configuración de conectores FDA {#specific-configurations-by-database-type}



En función de las bases de datos externas a las que desee tener acceso desde Adobe Campaign, debe realizar determinadas configuraciones específicas. Estas configuraciones implican esencialmente la instalación de controladores y la declaración de variables de entorno que pertenecen a cada RDBMS en el servidor de Adobe Campaign.

Como regla general, debe instalar la capa del cliente correspondiente en la base de datos externa en el servidor de Adobe Campaign.

>[!NOTE]
>
>Las versiones compatibles se enumeran en la [Matriz de compatibilidad de Campaign](../../rn/using/compatibility-matrix.md#FederatedDataAccessFDA).
>

## Pasos de configuración {#fda-configuration-steps}

Para configurar el acceso a una base de datos externa con FDA, los pasos de configuración son:

1. Instale los controladores y configure la cuenta externa correspondiente a la base de datos en el servidor de Adobe Campaign. Consulte las páginas específicas de la base de datos [enumeradas más abajo](#fda-specific-configuration)
1. Pruebe la cuenta externa o cree una conexión temporal entre Adobe Campaign y la base de datos externa. [Más información](../../installation/using/connecting-to-database.md)
1. Cree el esquema de la base de datos externa en Adobe Campaign. Esto permite identificar la estructura de datos de la base de datos externa. [Más información](../../installation/using/creating-data-schema.md)
1. Si es necesario, cree una nueva asignación de destino a partir del esquema creado anteriormente. Esto es necesario si los destinatarios de los envíos proceden de la base de datos externa. Esta implementación viene con limitaciones relacionadas con la personalización de mensajes. [Más información](../../installation/using/defining-data-mapping.md)

Una vez que se haya creado el esquema, los datos se pueden procesar en los flujos de trabajo de Adobe Campaign. Consulte la [documentación de Campaign v8](https://experienceleague.adobe.com/docs/campaign/automation/campaign-optimization/campaign-typologies.html?lang=es){target="_blank"}.

## Configuración específica de base de datos {#fda-specific-configuration}

En función de las bases de datos externas a las que desee tener acceso desde Adobe Campaign, debe realizar determinadas configuraciones específicas. Estas configuraciones implican esencialmente la instalación de controladores y la declaración de variables de entorno que pertenecen a cada RDBMS en el servidor de Adobe Campaign, así como la configuración de la cuenta externa.

Siga los vínculos a continuación para obtener más información:

* Conectar Campaign y [Amazon Redshift](../../installation/using/configure-fda-redshift.md)
* Conectar Campaign y [Azure Synapse](../../installation/using/configure-fda-synapse.md)
* Conectar Campaign y [Google BigQuery](../../installation/using/configure-fda-google-big-query.md)
* Conectar Campaign y [Hadoop](../../installation/using/configure-fda-hadoop.md)
* Conectar Campaign y [Microsoft SQL Server](../../installation/using/configure-fda-sql.md)
* Conectar Campaign y [Netezza](../../installation/using/configure-fda-netezza.md)
* Conectar Campaign y [Oracle](../../installation/using/configure-fda-oracle.md)
* Conectar Campaign y [PostgreSQL](../../installation/using/configure-fda-postgresql.md)
* Conectar Campaign y [SAP HANA](../../installation/using/configure-fda-sap-hana.md)
* Conectar Campaign y [Snowflake](../../installation/using/configure-fda-snowflake.md)
* Conectar Campaign y [Sybase IQ](../../installation/using/configure-fda-sybase.md)
* Conectar Campaign y [Teradata](../../installation/using/configure-fda-teradata.md)
* Conectar Campaign y [Vertica Analytics](../../installation/using/configure-fda-vertica.md)
