---
product: campaign
title: Acceso a una base de datos externa
description: Obtenga información sobre cómo acceder y procesar datos en una base de datos externa
feature: Federated Data Access
exl-id: 9d8d1e9c-63e4-40c4-8338-b921d08ea405
source-git-commit: 1e11b7419388698f5de366cbeddf2be88ef12873
workflow-type: tm+mt
source-wordcount: '161'
ht-degree: 50%

---

# Introducción al acceso de datos federado {#about-federated-data-access}

![](../../assets/v7-only.svg)

Adobe Campaign proporciona la opción **Acceso de Datos Federados** (FDA) para procesar la información almacenada en una o más bases de datos externas: puede acceder a datos externos sin cambiar la estructura de los datos de Adobe Campaign.

## Requisitos previos {#operating-principle}

La opción FDA le permite ampliar el modelo de datos en una base de datos de terceros. Detecta automáticamente la estructura de las tablas de destino y utiliza datos de los orígenes SQL.

Para utilizar esta capacidad, los requisitos previos se enumeran a continuación:

* **Configuración**: la lista de la base de datos externa compatible depende de su [modelo hosting](../../installation/using/hosting-models.md).
* **Versión de base de datos externa**: debe tener una base de datos externa compatible con el módulo FDA de Adobe Campaign.

   La lista de sistemas de bases de datos y versiones compatibles por modelo de alojamiento se detalla en Campaign [Matriz de compatibilidad](../../rn/using/compatibility-matrix.md#FederatedDataAccessFDA).

* **Permisos**: los usuarios también deben tener la variable [permisos necesarios](../../installation/using/remote-database-access-rights.md) en Adobe Campaign y en la base de datos externa.

