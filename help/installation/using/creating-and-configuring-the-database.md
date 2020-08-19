---
title: Creación y configuración de la base de datos
seo-title: Creación y configuración de la base de datos
description: Creación y configuración de la base de datos
seo-description: null
page-status-flag: never-activated
uuid: e5143d55-61fa-416a-80db-c29a0caf9a3e
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: installation
content-type: reference
topic-tags: initial-configuration
discoiquuid: 7dd8a6a5-7cca-4e92-8226-1b9e450dfaf9
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 890950463146fe0863d2809759eb142cb4bb1fff
workflow-type: tm+mt
source-wordcount: '1296'
ht-degree: 2%

---


# Creación y configuración de la base de datos{#creating-and-configuring-the-database}

Al crear una base de datos, Adobe Campaign ofrece dos opciones diferentes:

1. Creación o reciclaje de una base de datos: elija estas opciones si desea crear una nueva base de datos o reutilizar una existente. Véase el [caso 1: Creación/reciclaje de una base de datos](#case-1--creating-recycling-a-database).
1. Uso de una base de datos existente: seleccione esta opción si el administrador ya ha creado una base de datos vacía y desea utilizarla; o ampliar la estructura de una base de datos existente. Véase el [caso 2: Uso de una base de datos](#case-2--using-an-existing-database)existente.

Los pasos de configuración se detallan a continuación.

>[!CAUTION]
>
>Los nombres de bases de datos, usuarios y esquemas no deben tener inicio con un número ni incluir caracteres especiales.
>
>Only the **internal** identifier can carry out these operations. For more on this, refer to [Internal identifier](../../installation/using/campaign-server-configuration.md#internal-identifier).

## Caso 1: Creación/reciclaje de una base de datos {#case-1--creating-recycling-a-database}

The steps for creating a database or recycling an existing base are presented below. Algunas configuraciones dependen del motor de base de datos utilizado:

Se trata de los siguientes pasos:

* [Paso 1: Selección del motor](#step-1---selecting-the-database-engine)de la base de datos,
* [Paso 2: Conexión al servidor](#step-2---connecting-to-the-server),
* [Paso 3 - Conexión y características de la base de datos](#step-3---connection-and-characteristics-of-the-database),
* [Paso 4 - Paquetes para instalar](#step-4---packages-to-install),
* [Paso 5: pasos](#step-5---creation-steps)de creación,
* [Paso 6: Creación de la base de datos](#step-6---creating-the-database).

### Paso 1: Selección del motor de procesamiento de la base de datos {#step-1---selecting-the-database-engine}

Seleccione el motor de base de datos entre los de la lista desplegable.

![](assets/s_ncs_install_db_select_engine.png)

Las bases de datos admitidas se presentan en la sección Matriz [de](https://helpx.adobe.com/es/campaign/kb/compatibility-matrix.html)compatibilidad.

Identifique el servidor y elija el tipo de operación que desea realizar. En este caso, **[!UICONTROL Create or recycle a database]**.

![](assets/s_ncs_install_db_oracle_creation01.png)

Según el motor de base de datos seleccionado, la información de identificación del servidor puede variar.

* Para un motor **Oracle** , rellene el nombre **** TNS definido para el servidor de aplicaciones.
* Para un motor **PostgreSQL** o **DB2** , debe especificar el nombre DNS (o dirección IP) definido en el servidor de aplicaciones para acceder al servidor de bases de datos.
* For a **Microsoft SQL Server** engine, you must define:

   1. the DNS name (or IP address) defined on the application server to access the database server: **DNS** or **DNS\ `<instance>`** (instance mode),
   1. the authentication method used to access Microsoft SQL Server: **[!UICONTROL SQL Server authentication]** or **[!UICONTROL Windows NT authentication]**.

      ![](assets/s_ncs_install_db_mssql_creation01.png)

### Step 2 - Connecting to the server {#step-2---connecting-to-the-server}

In the **[!UICONTROL Server access]** window, define the database server access.

![](assets/s_ncs_install_db_oracle_creation02.png)

To do this, enter the name and password of an **Administration system account** which has permission to access the databases, i.e.:

* **system** for an Oracle database,
* **sa** for a Microsoft SQL Server database,
* **postgres** for a PostgreSQL database,
* **db2inst1** for a DB2 database.

### Step 3 - Connection and characteristics of the database {#step-3---connection-and-characteristics-of-the-database}

The following step lets you configure the settings for logging on to the database.

![](assets/s_ncs_install_db_oracle_creation03.png)

You need to define the following settings:

* Specify the name of the database to be created.

   >[!NOTE]
   >
   >For a DB2 database, the name of the database must not exceed 8 characters.

* Enter the password of the account linked to this database.
* Indicate whether or not the database must be in Unicode.

   The **[!UICONTROL Unicode database]** option lets you store all character types in Unicode regardless of language.

   >[!NOTE]
   >
   >Con una base de datos Oracle, la **[!UICONTROL Unicode storage]** opción le permite utilizar campos de tipo **NCLOB** y **NVARCHAR** .
   > 
   >If you do not select this option, the character set (charset) of the Oracle database must enable data storage in all languages (AL32UTF8 is recommended).

* Choose a time zone for the database and specify whether you want it to be in UTC (if available).

   For more on this, refer to [Time zone management](../../installation/using/time-zone-management.md).

### Paso 4: Paquetes para instalar {#step-4---packages-to-install}

Select the packages you wish to install.

Refer to your license agreement to check which solutions and options you are entitled to install, such as &quot;Interaction&quot; or &quot;Social Marketing&quot;.

![](assets/s_ncs_install_modules.png)

### Step 5 - Creation steps {#step-5---creation-steps}

The **[!UICONTROL Creation steps]** window enables you to display and edit the SQL script used to create the tables.

![](assets/s_ncs_install_db_oracle_creation04.png)

* For an Oracle, Microsoft SQL Server or PostgreSQL database, the administrator may also define the **storage parameters** to be used when creating database objects.

   These parameters receive the exact tablespace names (warning: case sensitive). Se almacenan respectivamente en el **[!UICONTROL Administration > Platform > Options]** nodo en las siguientes opciones (consulte [](../../installation/using/configuring-campaign-options.md#database)):

   * **WdbcOptions_TableSpaceUser**: user tables based on a schema
   * **WdbcOptions_TableSpaceIndex**: index of user tables based on a schema
   * **WdbcOptions_TableSpaceWork**: tablas de trabajo sin esquema
   * **WdbcOptions_TableSpaceWorkIndex**: índice de tablas de trabajo sin esquema

* Para una base de datos Oracle, el usuario de Adobe Campaign debe tener acceso a las bibliotecas de Oracle, normalmente como miembro del grupo **oinstall** .
* La **[!UICONTROL Set or change the administrator password]** opción le permite introducir la contraseña vinculada al operador de Adobe Campaign con derechos de administrador.

   Se recomienda definir una contraseña de administrador de cuentas de Adobe Campaign por motivos de seguridad.

### Paso 6: Creación de la base de datos {#step-6---creating-the-database}

La etapa final del asistente le permite crear la base de datos. Haga clic en **[!UICONTROL Start]** para confirmar.

![](assets/s_ncs_install_db_oracle_creation06.png)

Una vez creada la base de datos, puede volver a conectarse para finalizar la configuración de instancias.

Ahora debe poner en inicio el asistente de implementación para finalizar la configuración de la instancia. Refer to [Deployment wizard](../../installation/using/deploying-an-instance.md#deployment-wizard).

La configuración de conexión de la base de datos vinculada a la instancia se almacena en el archivo **`/conf/config-<instance>.xml`** que se encuentra en el directorio de instalación de Adobe Campaign.

Example of a Microsoft SQL Server configuration on the base61 database linked to the &#39;campaign&#39; account with its encrypted password:

```
<dbcnx encrypted="1" login="campaign:myBase" password="myPassword" provider="DB" server="dbServer"/>
```

## Caso 2: Uso de una base de datos existente {#case-2--using-an-existing-database}

The database, as well as the user, must have been created by the database administrator and the access rights correctly configured.

Por ejemplo, para una base de datos Oracle, los derechos mínimos requeridos son: OTORGAR CONNECT, RECURSOS Y ESPACIO DE TABLAS ILIMITADO.

Para utilizar una base de datos existente, los pasos de configuración son los siguientes:

* [Step 1 - Choosing the database engine](#step-1---choosing-the-database-engine),
* [Step 2 - Database connection settings](#step-2---database-connection-settings),
* [Paso 3 - Paquetes para instalar](#step-3---packages-to-install),
* [Paso 4: pasos](#step-4---creation-steps)de creación,
* [Paso 5: Creación de la base de datos](#step-5---creating-the-database).

### Paso 1: Selección del motor de procesamiento de la base de datos {#step-1---choosing-the-database-engine}

Elija el motor de base de datos en la lista desplegable.

![](assets/s_ncs_install_db_select_engine.png)

Identifique el servidor y elija el tipo de operación que desee realizar. En este caso, **[!UICONTROL Use an existing database]**.

![](assets/s_ncs_install_db_oracle_exists_01.png)

Según el motor de base de datos seleccionado, la información de identificación del servidor puede variar.

* Para un motor **Oracle** , rellene el nombre **** TNS definido para el servidor de aplicaciones.
* Para un motor **PostgreSQL** o **DB2** , debe especificar el nombre DNS (o dirección IP) definido en el servidor de aplicaciones para acceder al servidor de bases de datos.
* Para un motor de **Microsoft SQL Server** , debe definir:

   1. nombre DNS (o dirección IP) definido en el servidor de aplicaciones para acceder al servidor de bases de datos,
   1. el método de seguridad utilizado para obtener acceso a Microsoft SQL Server: **[!UICONTROL SQL Server authentication]** o **[!UICONTROL Windows NT authentication]**.

      ![](assets/s_ncs_install_db_mssql_exists_01.png)

### Paso 2: Ajustes de conexión a la base de datos {#step-2---database-connection-settings}

En la **[!UICONTROL Database]** ventana, defina la configuración de conexión de la base de datos.

![](assets/s_ncs_install_db_oracle_exists_02.png)

Debe definir la siguiente configuración:

* Introduzca el nombre de la base de datos que se va a utilizar.
* Introduzca el nombre y la contraseña de la cuenta asociada a esta base de datos.

   >[!NOTE]
   >
   >Make sure that both the schema name and user name match. Recommended way of creating database is through campaign console client.
   >For an Oracle database, you do not need to enter the account name.

* Indique si la base de datos debe ser Unicode o no.

### Paso 3: Paquetes para instalar {#step-3---packages-to-install}

Select the packages you wish to install.

Refer to your license agreement to check which solutions and options you are entitled to install, such as &quot;Interaction&quot; or &quot;Leads&quot;.

![](assets/s_ncs_install_modules.png)

### Paso 4: pasos de creación {#step-4---creation-steps}

The **[!UICONTROL Creation steps]** window enables you to display and edit the SQL script used to create the tables.

![](assets/s_ncs_install_db_oracle_creation04.png)

* Para las bases de datos Oracle, Microsoft SQL Server o PostgreSQL, el administrador puede definir los parámetros **de** almacenamiento que se utilizarán al crear objetos de base de datos.
* For an Oracle database, the Adobe Campaign user must have access to the Oracle libraries, typically as a member of the **oinstall** group.
* The **[!UICONTROL Set or change the administrator password]** option lets you enter the password linked to the Adobe Campaign operator with administrator rights.

   We recommend defining an Adobe Campaign account administrator password for security purposes.

### Step 5 - Creating the database {#step-5---creating-the-database}

The final stage of the wizard enables you to create the database. Haga clic en **[!UICONTROL Start]** para confirmar.

![](assets/s_ncs_install_db_oracle_creation06.png)

Once database creation is complete, you can reconnect to finalize instance configuration.

You must now start the deployment wizard to finish configuring the instance. Refer to [Deployment wizard](../../installation/using/deploying-an-instance.md#deployment-wizard).

La configuración de conexión de la base de datos vinculada a la instancia se almacena en el archivo **`/conf/config-<instance>.xml`** que se encuentra en el directorio de instalación de Adobe Campaign.

Example of a Microsoft SQL Server configuration on the base61 database linked to the &#39;campaign&#39; account with its encrypted password:

```
<dbcnx encrypted="1" login="campaign:myBase" password="myPassword" provider="DB" server="dbServer"/>
```

