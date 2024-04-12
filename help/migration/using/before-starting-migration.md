---
product: campaign
title: Antes de iniciar la migración
description: Antes de iniciar la migración
feature: Upgrade
audience: migration
content-type: reference
topic-tags: migration-procedure
hide: true
hidefromtoc: true
exl-id: d666bc0b-596a-4908-9364-7df5bb8d68d0
source-git-commit: b666535f7f82d1b8c2da4fbce1bc25cf8d39d187
workflow-type: tm+mt
source-wordcount: '322'
ht-degree: 2%

---

# Requisitos previos{#before-starting-migration}



En esta página se detallan los pasos específicos que deben seguirse antes de iniciar el proceso de migración. También debe consultar [esta página](about-migration.md) para obtener más información.

>[!NOTE]
>
>En este documento, los comandos se muestran como ejemplos. Pueden variar según la configuración.

1. Compruebe su versión de Adobe Campaign: antes de migrar, instale la última compilación de la versión actual que esté utilizando.
1. Haga una copia de seguridad de sus datos.
1. Compruebe su entorno: no puede cambiar el sistema de motor de base de datos (DBMS). Por ejemplo, no puede cambiar de un motor PostgreSQL a un motor de Oracle. Sin embargo, puede cambiar a la versión más reciente del motor de la base de datos. Tenga en cuenta que no es posible pasar de una base de datos no Unicode a una base de datos Unicode.

## Pasos de migración {#migration-steps}

El procedimiento de migración debe llevarse a cabo en **todo** y en un orden concreto.

* En el caso de un **plataforma independiente** (modo de máquina única), la aplicación se migra en su totalidad.
* En el caso de un **plataforma estándar** (empresa), los pasos de migración son los siguientes:

   1. Migre el servidor de marketing.
   1. Migre el servidor de correo (mta).
   1. Migre los servidores de redirección y seguimiento (Apache/IIS).

* En el caso de un **Plataforma de Cloud Messaging**, los servidores de ejecución se alojan en Adobe Campaign. Póngase en contacto con Adobe Campaign para coordinar la migración entre diferentes servidores.
* En el caso de un **Power Booster o Power Cluster Platform** Sin embargo, los pasos de migración son los siguientes:

   1. Migre los servidores de redirección y seguimiento (Apache/IIS).
   1. Migre los servidores Power Booster/Cluster.
   1. Migre el servidor de marketing.

## Contraseñas de usuario {#user-passwords}

En la versión 7, **interno** y **administrador** la conexión del operador debe estar protegida con una contraseña. Se recomienda encarecidamente asignar contraseñas a estas cuentas y a todas las cuentas de operador, **antes de la migración**. Si no ha especificado una contraseña para **interno**, no se podrá conectar. Para asignar una contraseña a **interno**, introduzca el siguiente comando:

```
nlserver config -internalpassword
```

>[!CAUTION]
>
>El **interno** la contraseña debe ser idéntica para todos los servidores de seguimiento. Para obtener más información, consulte la [Identificador interno](../../installation/using/configuring-campaign-server.md#internal-identifier) y [Permisos](../../platform/using/access-management.md) secciones.
