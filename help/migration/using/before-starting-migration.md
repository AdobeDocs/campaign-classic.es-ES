---
product: campaign
title: Antes de iniciar la migración
description: Antes de iniciar la migración
audience: migration
content-type: reference
topic-tags: migration-procedure
hide: true
hidefromtoc: true
exl-id: d666bc0b-596a-4908-9364-7df5bb8d68d0
source-git-commit: 80cf56e330731237d5e7b394381b737f30f8b350
workflow-type: tm+mt
source-wordcount: '322'
ht-degree: 2%

---

# Requisitos previos{#before-starting-migration}

![](../../assets/v7-only.svg)

En esta página se detallan los pasos específicos que debe seguir antes de iniciar el proceso de migración. También debe hacer referencia a [esta página](about-migration.md) para obtener más información.

>[!NOTE]
>
>En este documento, los comandos se proporcionan como ejemplos. Pueden variar según la configuración.

1. Compruebe su versión de Adobe Campaign: antes de migrar, instale la última versión de la versión actual que está utilizando.
1. Haga una copia de seguridad de los datos.
1. Compruebe el entorno: no puede cambiar el sistema motor de base de datos (DBMS). Por ejemplo, no se puede cambiar de un motor PostgreSQL a un motor de Oracle. Sin embargo, puede cambiar a la última versión del motor de la base de datos. Tenga en cuenta que no es posible pasar de una base de datos no Unicode a una base de datos Unicode.

## Pasos de migración {#migration-steps}

El procedimiento de migración debe llevarse a cabo **all** y en un orden determinado.

* En el caso de una **plataforma independiente** (modo de máquina única), la aplicación se migra por completo.
* En el caso de una **plataforma estándar** (empresa), los pasos de migración son los siguientes:

   1. Migrar el servidor de marketing.
   1. Migrar el servidor de correo (mta).
   1. Migre los servidores de redirección y seguimiento (Apache/IIS).

* En el caso de una **Plataforma de mensajería en la nube**, los servidores de ejecución están alojados en Adobe Campaign. Póngase en contacto con Adobe Campaign para coordinar la migración entre diferentes servidores.
* En el caso de una **Power Booster o Power Cluster platform**, los pasos de migración son los siguientes:

   1. Migre los servidores de redirección y seguimiento (Apache/IIS).
   1. Migre los servidores Power Booster/Cluster.
   1. Migrar el servidor de marketing.

## Contraseñas de usuario {#user-passwords}

En la versión 7, **internal** y **admin** la conexión del operador debe estar protegida con una contraseña. Se recomienda encarecidamente asignar contraseñas a estas cuentas y a todas las cuentas de operador, **antes de la migración**. Si no ha especificado ninguna contraseña para **internal**, no podrá conectarse. Para asignar una contraseña a **internal**, introduzca el siguiente comando:

```
nlserver config -internalpassword
```

>[!CAUTION]
>
>La variable **internal** la contraseña debe ser idéntica para todos los servidores de seguimiento. Para obtener más información, consulte [Identificador interno](../../installation/using/configuring-campaign-server.md#internal-identifier) y [Permisos](../../platform/using/access-management.md) secciones.
