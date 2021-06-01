---
product: campaign
title: Recomendaciones de la base de datos del Campaign Classic
description: Recomendaciones de base de datos
audience: installation
content-type: reference
topic-tags: prerequisites-and-recommendations-
exl-id: 8a0426c1-9e8d-4053-bc2b-6a550e2eed2f
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: tm+mt
source-wordcount: '277'
ht-degree: 1%

---

# Database{#database}

El servidor de la base de datos puede ejecutarse en cualquier sistema operativo determinado independientemente del sistema operativo que utilicen el servidor de aplicaciones o los servidores, siempre que haya conectividad de red entre ellos.

El sistema operativo del servidor de la base de datos no es importante siempre que esté disponible la conectividad con los diferentes componentes de Adobe Campaign.

Compruebe también la sección [Database access ayers](../../installation/using/prerequisites-of-campaign-installation-in-linux.md#database-access-layers).

## Microsoft SQL Server {#microsoft-sql-server}

El cliente nativo debe estar instalado en los servidores de aplicaciones de Adobe Campaign.

Puede buscar el cliente nativo en el servidor a través del panel de configuración del controlador ODBC, en **Cliente nativo de SQL Server 11.0**.

El siguiente archivo DLL de acceso debe estar presente: **sqlncli11.dll**.

Las DLL de acceso se encuentran en el sitio web de Microsoft.

>[!NOTE]
>
>No se admite el acceso a Microsoft SQL Server desde un servidor de aplicaciones que se ejecuta en Linux.

## Oracle {#oracle}

>[!NOTE]
>
>No se admiten nombres de columna con caracteres multibyte.

Los parámetros **NLS_NCHAR_CHARACTERSET** y **NLS_CHARACTERSET** deben configurarse correctamente para que la base de datos funcione en Unicode o ANSI.

Adobe Campaign utiliza la codificación de Oracle predeterminada. El uso de otras codificaciones puede dar déclencheur a problemas de compatibilidad: en este caso, póngase en contacto con el servicio de asistencia técnica.

Para obtener información sobre la codificación, utilice el siguiente comando **sqlplus**:

```
SELECT * FROM nls_database_parameters ;
```

* Para una instalación de Unicode, las codificaciones admitidas son:

   ```
   NLS_NCHAR_CHARACTERSET         AL16UTF16
   NLS_CHARACTERSET         AL32UTF8
   ```

* Para una instalación ANSI (que no sea Unicode), solo se admite la siguiente codificación:

```
  NLS_CHARACTERSET WE8MSWIN1252
```

Para iniciar sesión en **sqlplus**, utilice el perfil de usuario del Oracle:

```
su - oracle 
sqlplus 
[login] [password]
```

También puede consultar [Cliente de Oracle en Linux](../../installation/using/installing-packages-with-linux.md#oracle-client-in-linux).

## PostgresSQL {#postgressql}

Le recomendamos que instale la compatibilidad con UTF-8 al instalar el motor de base de datos. De este modo, podrá crear bases de datos Unicode.

**Tema relacionado**

* [Opción sin registrar en tablas Adobe Campaign Classic](https://helpx.adobe.com/campaign/kb/unlogged-tables-classic.html)
