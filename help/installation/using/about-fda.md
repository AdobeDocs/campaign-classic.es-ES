---
product: campaign
title: Acceso a una base de datos externa
description: Obtenga información sobre cómo acceder y procesar datos en una base de datos externa
audience: platform
content-type: reference
topic-tags: connectors
exl-id: 9d8d1e9c-63e4-40c4-8338-b921d08ea405
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: tm+mt
source-wordcount: '166'
ht-degree: 50%

---

# Introducción al acceso de datos federado {#about-federated-data-access}

Adobe Campaign proporciona la opción **Acceso de Datos Federados** (FDA) para procesar la información almacenada en una o más bases de datos externas: puede acceder a datos externos sin cambiar la estructura de los datos de Adobe Campaign.

## Requisitos previos {#operating-principle}

La opción FDA le permite ampliar el modelo de datos en una base de datos de terceros. Detecta automáticamente la estructura de las tablas de destino y utiliza datos de los orígenes SQL.

Para utilizar esta capacidad, los requisitos previos se enumeran a continuación:

* **Configuración**: excepto para Snowflake, necesita un modelo de alojamiento  **en** locales o  **** híbrido para configurar el acceso de datos federado. [Obtenga más información](../../installation/using/hosting-models.md)
* **Versión** de la base de datos externa: debe tener una base de datos externa compatible con el módulo FDA de Adobe Campaign. La lista de sistemas de bases de datos y versiones compatibles se detalla en la matriz de compatibilidad [Campaign](../../rn/using/compatibility-matrix.md#FederatedDataAccessFDA).
* **Permisos**: los usuarios también deben tener los  [permisos necesarios ](../../installation/using/remote-database-access-rights.md) en Adobe Campaign y en la base de datos externa.

