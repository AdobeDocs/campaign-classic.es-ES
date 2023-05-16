---
product: campaign
title: Introducción al acceso de datos federado
description: Obtenga información sobre cómo acceder y procesar datos en una base de datos externa
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
feature: Federated Data Access
exl-id: 9d8d1e9c-63e4-40c4-8338-b921d08ea405
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: tm+mt
source-wordcount: '163'
ht-degree: 47%

---

# Introducción al acceso de datos federado {#about-federated-data-access}



Adobe Campaign proporciona la opción **Acceso de Datos Federados** (FDA) para procesar la información almacenada en una o más bases de datos externas: puede acceder a datos externos sin cambiar la estructura de los datos de Adobe Campaign.

## Requisitos previos {#operating-principle}

La opción FDA le permite ampliar el modelo de datos en una base de datos de terceros. Detecta automáticamente la estructura de las tablas de destino y utiliza datos de los orígenes SQL.

Para utilizar esta capacidad, los requisitos previos se enumeran a continuación:

* **Configuración**: la lista de la base de datos externa compatible depende de su [modelo hosting](../../installation/using/hosting-models.md).
* **Versión de base de datos externa**: debe tener una base de datos externa compatible con el módulo FDA de Adobe Campaign.

   La lista de sistemas de bases de datos y versiones compatibles por modelo de alojamiento se detalla en Campaign [Matriz de compatibilidad](../../rn/using/compatibility-matrix.md#FederatedDataAccessFDA).

* **Permisos**: los usuarios también deben tener la variable [permisos necesarios](../../installation/using/remote-database-access-rights.md) en Adobe Campaign y en la base de datos externa.

