---
product: campaign
title: Introducción al acceso de datos federado
description: Obtenga información sobre cómo acceder y procesar datos en una base de datos externa
feature: Installation, Federated Data Access
exl-id: 9d8d1e9c-63e4-40c4-8338-b921d08ea405
TQID: 'https://experienceleague.adobe.com/X-VyiKlGatskoXtPoLYhb8HrAgCRLLHxTbwXDFmg8jI'
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
source-git-commit: a43e591a565a18d79f583d975e3e812c5435b0c0
workflow-type: tm+mt
source-wordcount: '164'
ht-degree: 47%
---
# Introducción al acceso de datos federado {#about-federated-data-access}



Adobe Campaign proporciona la opción **Acceso de Datos Federados** (FDA) para procesar la información almacenada en una o más bases de datos externas: puede acceder a datos externos sin cambiar la estructura de los datos de Adobe Campaign.

## Requisitos previos {#operating-principle}

La opción FDA le permite ampliar el modelo de datos en una base de datos de terceros. Detecta automáticamente la estructura de las tablas de destino y utiliza datos de los orígenes SQL.

Para utilizar esta capacidad, los requisitos previos se enumeran a continuación:

* **Configuración**: la lista de bases de datos externas compatibles depende de su [modelo de alojamiento](../../installation/using/hosting-models.md).
* **Versión de base de datos externa**: necesita tener una base de datos externa compatible con el módulo FDA de Adobe Campaign.

  La lista de sistemas de base de datos y versiones compatibles por modelo de alojamiento se detalla en Campaign [Compatibility matrix](../../rn/using/compatibility-matrix.md#FederatedDataAccessFDA).

* **Permisos**: los usuarios también deben tener los [permisos necesarios](../../installation/using/remote-database-access-rights.md) en Adobe Campaign y en la base de datos externa.

