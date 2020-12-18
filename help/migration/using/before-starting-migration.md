---
solution: Campaign Classic
product: campaign
title: Antes de iniciar la migración
description: Antes de iniciar la migración
audience: migration
content-type: reference
topic-tags: migration-procedure
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '524'
ht-degree: 2%

---


# Antes de iniciar la migración{#before-starting-migration}

>[!NOTE]
>
>En este documento, los comandos vinculados a la base de datos se proporcionan como ejemplo. Pueden variar según la configuración. Póngase en contacto con el administrador de la base de datos.

## Advertencias {#warnings}

* El proceso de migración solo debe realizarlo un usuario experto. Debe contar con la asistencia de al menos un experto en bases de datos, un administrador del sistema y un desarrollador de aplicaciones de Adobe Campaign.
* Antes de iniciar la migración, compruebe que los sistemas y los componentes del sistema que utiliza son compatibles con la versión 7. Consulte la [matriz de compatibilidad](../../rn/using/compatibility-matrix.md).
* Si utiliza Adobe Campaign Cloud Messaging (intermediaria), póngase en contacto con Adobe antes de iniciar el procedimiento de migración completo.
* Antes de iniciar un proceso de migración, **debe** realizar una copia de seguridad de los datos.
* El proceso de migración puede tardar varios días en completarse.
* Adobe Campaign v7 es más estricto que las versiones 5.11 y 6.02 en términos de configuración. Esto sirve principalmente para evitar problemas como la corrupción de datos y para preservar la integridad de los datos en la base de datos. Por consiguiente, es posible que determinadas funciones ofrecidas en las versiones 5.11 y v6.02 ya no funcionen en la versión v7 y que, por lo tanto, deban adaptarse después de la migración. Antes de poner en producción cualquier cosa, le sugerimos que pruebe sistemáticamente todas las configuraciones, especialmente los flujos de trabajo necesarios para utilizar Adobe Campaign.

### Versión instalada {#installed-version}

Antes de migrar, debe instalar la última compilación de la versión actual que está utilizando.

Compruebe la versión del servidor en el menú **[!UICONTROL Help> About]** de la consola del cliente mediante el comando **nlserver pdump**.

### Backup de datos {#data-backup}

Antes de iniciar un proceso de migración, **debe** realizar una copia de seguridad de los datos.

### Entorno {#environment}

* No es posible cambiar el tipo de motor de base de datos (DBMS). Por ejemplo, no se puede cambiar de un motor PostgreSQL a un motor Oracle. Sin embargo, puede cambiar de un motor Oracle 8 a un motor Oracle 10.
* No es posible pasar de una base de datos no Unicode a una base de datos Unicode.

### Recomendación {#recommendation}

Dado que el procedimiento de migración es delicado, recomendamos encarecidamente que se lea a fondo este documento antes de iniciar el procedimiento.

## Pasos de migración {#migration-steps}

El procedimiento de migración debe realizarse en **todos** servidores y en un orden determinado.

* En el caso de una **plataforma independiente** (modo de una sola máquina), la aplicación se migra en su totalidad.
* En el caso de una **plataforma estándar** (empresa), los pasos de migración son los siguientes:

   1. Migrar el servidor de marketing.
   1. Migrar el servidor de correo (mta).
   1. Migrar los servidores de redirección y seguimiento (Apache / IIS).

* En el caso de una **plataforma de mensajería en la nube**, los servidores de ejecución se alojan en Adobe Campaign. Póngase en contacto con Adobe Campaign para coordinar la migración entre diferentes servidores.
* En el caso de una **plataforma de Power Booster o Power Cluster**, los pasos de migración son los siguientes:

   1. Migrar los servidores de redirección y seguimiento (Apache / IIS).
   1. Migrar los servidores Power Booster/Cluster.
   1. Migrar el servidor de marketing.

## Contraseñas de usuario {#user-passwords}

En v7, la conexión del operador **internal** y **admin** debe estar asegurada mediante una contraseña. Se recomienda encarecidamente asignar contraseñas a estas cuentas y a todas las cuentas de operador, **antes de la migración**. Si no ha especificado una contraseña para **internal**, no podrá conectarse. Para asignar una contraseña a **internal**, introduzca el siguiente comando:

```
nlserver config -internalpassword
```

>[!IMPORTANT]
>
>La contraseña **interna** debe ser idéntica para todos los servidores de seguimiento. Para obtener más información, consulte las secciones [Identificador interno](../../installation/using/campaign-server-configuration.md#internal-identifier) y [Acerca de los permisos](../../platform/using/access-management.md#about-permissions).

