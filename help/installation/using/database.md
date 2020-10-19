---
title: Recomendaciones de la base de datos Campaign Classic
description: Recomendaciones de base de datos
page-status-flag: never-activated
uuid: b318365c-8846-4c1d-b5f7-ece55fb8c4af
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: installation
content-type: reference
topic-tags: prerequisites-and-recommendations-
discoiquuid: 1dcf01af-c2f3-4975-ba05-628d52952064
translation-type: tm+mt
source-git-commit: b447e316bed8e0e87d608679c147e6bd7b0815eb
workflow-type: tm+mt
source-wordcount: '277'
ht-degree: 1%

---


# Database{#database}

El servidor de base de datos puede ejecutarse en cualquier sistema operativo, independientemente del sistema operativo que utilice el servidor de aplicaciones o los servidores, siempre que haya conectividad de red entre ellos.

El sistema operativo del servidor de la base de datos no es importante mientras esté disponible la conectividad con los diferentes componentes de Adobe Campaign.

Compruebe también la sección Capas [de acceso a la](../../installation/using/prerequisites-of-campaign-installation-in-linux.md#database-access-layers) base de datos.

## Microsoft SQL Server {#microsoft-sql-server}

El cliente nativo debe estar instalado en los servidores de aplicaciones de Adobe Campaign.

Puede buscar el cliente nativo en el servidor mediante el panel de configuración del controlador ODBC, en el cliente nativo de **SQL Server 11.0**.

Debe estar presente el siguiente archivo DLL de acceso: **sqlncli11.dll**.

Las DLL de acceso se encuentran en el sitio web de Microsoft.

>[!NOTE]
>
>No se admite el acceso a Microsoft SQL Server desde un servidor de aplicaciones que se ejecuta en Linux.

## Oracle {#oracle}

>[!NOTE]
>
>No se admiten nombres de columna con caracteres multibyte.

Los parámetros **NLS_NCHAR_CHARACTERSET** y **NLS_CHARACTERSET** deben configurarse correctamente para que la base de datos funcione en Unicode o ANSI.

Adobe Campaign utiliza la codificación predeterminada de Oracle. El uso de otra codificación puede desencadenar problemas de compatibilidad: en este caso, póngase en contacto con el servicio de asistencia técnica.

Para obtener información sobre la codificación, utilice el siguiente **comando sqlplus** :

```
SELECT * FROM nls_database_parameters ;
```

* Para una instalación Unicode, las codificaciones admitidas son:

   ```
   NLS_NCHAR_CHARACTERSET         AL16UTF16
   NLS_CHARACTERSET         AL32UTF8
   ```

* Para una instalación ANSI (sin Unicode), solo se admite la siguiente codificación:

```
  NLS_CHARACTERSET WE8MSWIN1252
```

Para iniciar sesión en **sqlplus**, utilice el perfil de usuario de Oracle:

```
su - oracle 
sqlplus 
[login] [password]
```

También puede consultar [Oracle Client en Linux](../../installation/using/installing-packages-with-linux.md#oracle-client-in-linux).

## PostgresSQL {#postgressql}

Le recomendamos que instale la compatibilidad con UTF-8 al instalar el motor de procesamiento de la base de datos. De esta manera podrá crear bases de datos Unicode.

**Temas relacionados**

* [Opción sin registrar en tablas de Adobe Campaign Classic](https://helpx.adobe.com/campaign/kb/unlogged-tables-classic.html)
