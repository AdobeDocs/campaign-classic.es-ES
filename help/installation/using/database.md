---
product: campaign
title: Recommendations de Campaign Classic Database
description: Recomendaciones de base de datos
feature: Installation, Instance Settings
badge-v7-prem: label="On-Premise e híbrido" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=es" tooltip="Se aplica solo a implementaciones On-premise e híbridas"
audience: installation
content-type: reference
topic-tags: prerequisites-and-recommendations-
exl-id: 8a0426c1-9e8d-4053-bc2b-6a550e2eed2f
source-git-commit: b666535f7f82d1b8c2da4fbce1bc25cf8d39d187
workflow-type: tm+mt
source-wordcount: '281'
ht-degree: 6%

---

# Base de datos{#database}



El servidor de base de datos puede ejecutarse en cualquier sistema operativo dado independientemente del sistema operativo utilizado por el servidor o los servidores de aplicaciones, siempre y cuando haya conectividad de red entre ellos.

El sistema operativo del servidor de la base de datos no es importante siempre que la conectividad con los diferentes componentes de Adobe Campaign esté disponible.

Compruebe también la [Capas de acceso a base de datos](../../installation/using/prerequisites-of-campaign-installation-in-linux.md#database-access-layers) sección.

## Microsoft SQL Server {#microsoft-sql-server}

El cliente nativo debe estar instalado en los servidores de aplicaciones de Adobe Campaign.

Puede buscar el cliente nativo en el servidor a través del panel de configuración del controlador ODBC, en **SQL Server Native Client 11.0**.

La siguiente DLL de acceso debe estar presente: **sqlncli11.dll**.

Las DLL de acceso se encuentran en el sitio web de Microsoft.

>[!NOTE]
>
>No se admite el acceso a Microsoft SQL Server desde un servidor de aplicaciones que se ejecute en Linux.

## Oracle {#oracle}

>[!NOTE]
>
>No se admiten nombres de columna con caracteres de bytes múltiples.

El **NLS_NCHAR_CHARACTERSET** y **NLS_CHARACTERSET** Los parámetros deben configurarse correctamente para que la base de datos funcione en Unicode o ANSI.

Adobe Campaign utiliza la codificación de Oracle predeterminada. El uso de otra codificación puede provocar problemas de compatibilidad con el déclencheur: en este caso, póngase en contacto con el servicio de asistencia técnica.

Para obtener más información sobre la codificación, utilice el siguiente **sqlplus** comando:

```
SELECT * FROM nls_database_parameters ;
```

* En una instalación Unicode, las codificaciones admitidas son:

  ```
  NLS_NCHAR_CHARACTERSET         AL16UTF16
  NLS_CHARACTERSET         AL32UTF8
  ```

* Para una instalación ANSI (no Unicode), sólo se admite la siguiente codificación:

```
  NLS_CHARACTERSET WE8MSWIN1252
```

Para iniciar sesión en **sqlplus**, utilice el perfil de usuario de Oracle:

```
su - oracle 
sqlplus 
[login] [password]
```

También puede consultar [Cliente de oracle en Linux](../../installation/using/installing-packages-with-linux.md#oracle-client-in-linux).

## PostgresSQL {#postgressql}

Le recomendamos que instale la compatibilidad con UTF-8 al instalar el motor de base de datos. De este modo, podrá crear bases de datos Unicode.

**Tema relacionado**

* [Opción sin registrar en tablas de Adobe Campaign Classic](https://helpx.adobe.com/campaign/kb/unlogged-tables-classic.html)
