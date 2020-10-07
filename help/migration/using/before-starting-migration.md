---
title: Antes de iniciar la migración
seo-title: Antes de iniciar la migración
description: Antes de iniciar la migración
seo-description: null
page-status-flag: never-activated
uuid: b9325510-2fa5-4be4-9cf0-f37232bbbd8c
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: migration
content-type: reference
topic-tags: migration-procedure
discoiquuid: d8877378-fb43-4f32-91c6-60f2f788f916
translation-type: tm+mt
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: tm+mt
source-wordcount: '410'
ht-degree: 3%

---


# Antes de iniciar la migración{#before-starting-migration}

>[!NOTE]
>
>En este documento, los comandos vinculados a la base de datos se proporcionan como ejemplo. Pueden variar según la configuración. Póngase en contacto con el administrador de la base de datos.

## Advertencias {#warnings}

### Versión instalada {#installed-version}

Antes de migrar, debe instalar la última compilación de la versión actual que está utilizando.

Compruebe la versión en el servidor accediendo al **[!UICONTROL Help> About]** menú de la consola cliente mediante el comando **nlserver pdump** .

### Backup de datos {#data-backup}

Antes de iniciar un proceso de migración, **debe** realizar una copia de seguridad de los datos.

### Entorno {#environment}

* No es posible cambiar el tipo de motor de base de datos (DBMS). Por ejemplo, no se puede cambiar de un motor PostgreSQL a un motor Oracle. Sin embargo, puede cambiar de un motor de Oracle 8 a un motor de Oracle 10.
* No es posible pasar de una base de datos no Unicode a una base de datos Unicode.

### Recomendación {#recommendation}

Dado que el procedimiento de migración es especialmente delicado, recomendamos encarecidamente que se lea este documento a fondo antes de iniciar el procedimiento.

## Pasos de migración {#migration-steps}

El procedimiento de migración debe llevarse a cabo en **todos** los servidores y en un orden determinado.

* En el caso de una plataforma **** independiente (modo de una sola máquina), la aplicación se migra por completo.
* En el caso de una plataforma **** estándar (empresa), los pasos de migración son los siguientes:

   1. Migrar el servidor de marketing.
   1. Migrar el servidor de correo (mta).
   1. Migrar los servidores de redirección y seguimiento (Apache / IIS).

* En el caso de una plataforma **de mensajería** en la nube, los servidores de ejecución están alojados en Adobe Campaign. Póngase en contacto con Adobe Campaign para coordinar la migración entre diferentes servidores.
* En el caso de una plataforma **** Power Booster o Power Cluster, los pasos de migración son los siguientes:

   1. Migrar los servidores de redirección y seguimiento (Apache / IIS).
   1. Migrar los servidores Power Booster/Cluster.
   1. Migrar el servidor de marketing.

>[!NOTE]
>
>Es posible la comunicación entre un servidor de marketing v6.02 y un servidor de mensajería en la nube v7 o Power Booster/Cluster. Sin embargo, si decide mantener su servidor de marketing v6.02, esto debe actualizarse con la versión 6.02 más reciente antes de migrar a la mensajería en la nube o a Power Booster/Cluster.

## Contraseñas de usuario {#user-passwords}

En v7, la conexión de operador **interno** y de **administrador** debe estar protegida con una contraseña. Se recomienda encarecidamente asignar contraseñas a estas cuentas y a todas las cuentas de operador **antes de la migración**. Si no ha especificado una contraseña para **interno**, no podrá conectarse. Para asignar una contraseña a **interno**, escriba el siguiente comando:

```
nlserver config -internalpassword
```

>[!IMPORTANT]
>
>La contraseña **interna** debe ser idéntica para todos los servidores de seguimiento. Para obtener más información, consulte las secciones Identificador [](../../installation/using/campaign-server-configuration.md#internal-identifier) interno y [Acerca de los permisos](../../platform/using/access-management.md#about-permissions) .

