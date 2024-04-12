---
product: campaign
title: Introducción al acceso de datos federado
description: Obtenga información sobre cómo acceder y procesar datos en una base de datos externa
feature: Installation, Federated Data Access
exl-id: 9d8d1e9c-63e4-40c4-8338-b921d08ea405
source-git-commit: b666535f7f82d1b8c2da4fbce1bc25cf8d39d187
workflow-type: tm+mt
source-wordcount: '163'
ht-degree: 47%

---

# Introducción al acceso de datos federado {#about-federated-data-access}



Adobe Campaign proporciona la opción **Acceso de Datos Federados** (FDA) para procesar la información almacenada en una o más bases de datos externas: puede acceder a datos externos sin cambiar la estructura de los datos de Adobe Campaign.

## Requisitos previos {#operating-principle}

La opción FDA le permite ampliar el modelo de datos en una base de datos de terceros. Detecta automáticamente la estructura de las tablas de destino y utiliza datos de los orígenes SQL.

Para utilizar esta capacidad, los requisitos previos se enumeran a continuación:

* **Configuración**: la lista de bases de datos externas compatibles depende de su [modelo de alojamiento](../../installation/using/hosting-models.md).
* **Versión de base de datos externa**: necesita tener una base de datos externa compatible con el módulo FDA de Adobe Campaign.

  La lista de sistemas de base de datos y versiones compatibles por modelo de alojamiento se detalla en Campaign [Matriz de compatibilidad](../../rn/using/compatibility-matrix.md#FederatedDataAccessFDA).

* **Permisos**: los usuarios también deben tener el [permisos necesarios](../../installation/using/remote-database-access-rights.md) en Adobe Campaign y en la base de datos externa.

