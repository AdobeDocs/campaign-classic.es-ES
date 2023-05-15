---
product: campaign
title: Recomendaciones de la base de datos del Campaign Classic
description: Recomendaciones de base de datos
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
badge-v7-prem: label="on-premise & hybrid" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=en" tooltip="Applies to on-premise and hybrid deployments only"
audience: installation
content-type: reference
topic-tags: prerequisites-and-recommendations-
exl-id: 8a0426c1-9e8d-4053-bc2b-6a550e2eed2f
source-git-commit: a5762cd21a1a6d5a5f3a10f53a5d1f43542d99d4
workflow-type: tm+mt
source-wordcount: '277'
ht-degree: 2%

---

# Database{#database}



El servidor de la base de datos puede ejecutarse en cualquier sistema operativo determinado independientemente del sistema operativo que utilicen el servidor de aplicaciones o los servidores, siempre que haya conectividad de red entre ellos.

El sistema operativo del servidor de la base de datos no es importante siempre que esté disponible la conectividad con los diferentes componentes de Adobe Campaign.

Compruebe también la [Capas de acceso a bases de datos](../../installation/using/prerequisites-of-campaign-installation-in-linux.md#database-access-layers) para obtener más información.

## Microsoft SQL Server {#microsoft-sql-server}

El cliente nativo debe estar instalado en los servidores de aplicaciones de Adobe Campaign.

Puede buscar el cliente nativo en el servidor mediante el panel de configuración del controlador ODBC, en **Cliente nativo de SQL Server 11.0**.

El siguiente archivo DLL de acceso debe estar presente: **sqlncli11.dll**.

Las DLL de acceso se encuentran en el sitio web de Microsoft.

>[!NOTE]
>
>No se admite el acceso a Microsoft SQL Server desde un servidor de aplicaciones que se ejecuta en Linux.

## Oracle {#oracle}

>[!NOTE]
>
>No se admiten nombres de columna con caracteres multibyte.

La variable **NLS_NCHAR_CHARACTERSET** y **NLS_CHARACTERSET** Los parámetros de deben configurarse correctamente para que la base de datos funcione en Unicode o ANSI.

Adobe Campaign utiliza la codificación de Oracle predeterminada. El uso de otras codificaciones puede dar déclencheur a problemas de compatibilidad: en este caso, póngase en contacto con el servicio de asistencia técnica.

Para obtener más información sobre la codificación, utilice lo siguiente **sqlplus** comando:

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

* [Opción sin registrar en tablas Adobe Campaign Classic](https://helpx.adobe.com/campaign/kb/unlogged-tables-classic.html)
