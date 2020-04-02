---
title: Acceso a una base de datos externa
seo-title: Acceso a una base de datos externa
description: Acceso a una base de datos externa
seo-description: null
page-status-flag: never-activated
uuid: b84359b9-c584-431d-80d5-71146d9b6854
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: platform
content-type: reference
topic-tags: connectors
discoiquuid: dd3d14cc-5153-428d-a98a-32b46f0fe811
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 17eed4f4ead8ce4f424d4fb2681269e888229692

---


# Derechos de acceso a bases de datos remotas {#remote-database-access-rights}

En primer lugar, para que el usuario pueda llevar a cabo operaciones en una base de datos externa a través de FDA, el último debe tener un derecho específico en Adobe Campaign.

1. Select the **[!UICONTROL Administration > Access Management > Named Rights]** node in the Adobe Campaign explorer.
1. Cree un nuevo derecho especificando la etiqueta elegida.
1. El campo **[!UICONTROL Name]** debe tener el siguiente formato **user:base@server**, donde:

   * **user** corresponde al nombre del usuario en la base de datos externa.
   * **base** corresponde al nombre de la base de datos externa.
   * **server** corresponde al nombre del servidor de base de datos externo.

      >[!NOTE]
      >
      >La parte **:base** es opcional en Oracle.

1. Guarde el derecho asignado y luego vincúlelo al usuario elegido desde el nodo **[!UICONTROL Administration > Access Management > Operators]** del explorador de Adobe Campaign.

A continuación, para procesar los datos contenidos en una base de datos externa, el usuario de Adobe Campaign debe tener al menos derechos de escritura en la base de datos para poder crear tablas de trabajo. Adobe Campaign los elimina automáticamente.

En general, son necesarios los siguientes derechos:

* **CONEXIÓN**: conexión con la base de datos remota,
* **LECTURA DE Datos**: acceso de sólo lectura a tablas que contienen datos de clientes,
* **LECTURA DE MetaDatos**: acceso a los catálogos de datos del servidor para obtener la estructura de la tabla,
* **CARGA**: carga masiva en tablas de trabajo (requerido cuando se trabaja en colecciones y uniones),
* **CREACIÓN/ELIMINACIÓN** de **TABLA/ÍNDICE/PROCEDIMIENTO/FUNCIÓN**,
* **EXPLICACIÓN** (recomendado): para controlar el rendimiento en caso de problemas,
* **ESCRITURA DE Datos** (según el escenario de integración).

El administrador de la base de datos debe hacer coincidir estos derechos con los derechos específicos de cada motor de base de datos. Para obtener más información, consulte la sección siguiente.

## Derechos FDA {#fda-rights}

|   | Snowflake | Redshift | Oracle | SQLServer | PostgreSQL | MySQL |
|:-:|:-:|:-:|:-:|:-:|:-:|:-:|
| **Conexión a la base de datos remota** | USO EN ALMACÉN Y USO EN LOS privilegios DE BASE DE DATOS | Creación de un usuario vinculado a la cuenta de AWS | CREAR privilegio DE SESIÓN | Permiso de CONNECT | Privilegio de CONNECT | Creación de un usuario vinculado a un host remoto con TODOS LOS PRIVILEGIOS |
| **Creación de tablas** | CREAR TABLA EN EL privilegio ESQUEMA | CREAR privilegio | CREAR privilegio DE TABLA | permiso CREAR TABLA | CREAR privilegio | CREAR privilegio |
| **Creación de índices** | N/D | CREAR privilegio | ÍNDICE o CREE CUALQUIER privilegio DE ÍNDICE | ALTER, permiso | CREAR privilegio | Privilegio de INDEX |
| **Creación de funciones** | CREAR FUNCIÓN EN EL privilegio ESQUEMA | USO DEL privilegio plpythonu EN IDIOMA para poder llamar a scripts de pitón externos | CREAR PROCEDIMIENTO O CREAR CUALQUIER privilegio DE PROCEDIMIENTO | permiso CREAR FUNCIÓN | Privilegio de uso | CREAR privilegio RUTINO |
| **Creación de procedimientos** | CREAR PROCEDIMIENTO SOBRE EL privilegio ESQUEMA | USO DEL privilegio plpythonu EN IDIOMA para poder llamar a scripts de pitón externos | CREAR PROCEDIMIENTO O CREAR CUALQUIER privilegio DE PROCEDIMIENTO | permiso CREAR PROCEDIMIENTO | Privilegio USAGE (los procedimientos son funciones) | CREAR privilegio RUTINO |
| **Eliminación de objetos (tablas, índices, funciones, procedimientos)** | Propiedad del objeto | Tener el objeto o ser un superusuario | ELIMINAR CUALQUIER privilegio &lt; objeto > | ALTER, permiso | Tabla: propietario del índice de tabla: propiedad de la función de índice: propiedad de la función | Privilegio de DROP |
| **Supervisión de las ejecuciones** | SUPERVISAR privilegio en el objeto requerido | No se requiere ningún privilegio para utilizar el comando EXPLAIN | Privilegio INSERTAR y SELECCIONAR y privilegio necesario para ejecutar la instrucción en la que se basa el PLAN DE EXPLICACIÓN | SHOWPLAN, permiso | No se requiere ningún privilegio para utilizar la instrucción EXPLAIN | Privilegio SELECT |
| **Escritura de datos** | Privilegios de INSERT y/o UPDATE (según la operación de escritura) | Privilegios de INSERCIÓN y ACTUALIZACIÓN | INSERTAR Y ACTUALIZAR O INSERTAR Y ACTUALIZAR CUALQUIER privilegio DE TABLA | Permisos INSERTAR y ACTUALIZAR | Privilegios de INSERCIÓN y ACTUALIZACIÓN | Privilegios de INSERCIÓN y ACTUALIZACIÓN |
| **Carga de datos en tablas** | CREAR ESCENA EN EL ESQUEMA, SELECCIONAR e INSERTAR en los privilegios de la tabla destinatario | Privilegios SELECT e INSERT | Privilegios SELECT e INSERT | INSERTAR, ADMINISTRAR OPERACIONES MASIVAS Y ALTER TABLE permissions | Privilegios SELECT e INSERT | Privilegio de ARCHIVO |
| **Acceso a los datos del cliente** | SELECCIONAR EN (FUTURO) TABLA(S) o privilegios(s) de VISTA(s) | Privilegio SELECT | SELECCIONAR O SELECCIONAR CUALQUIER privilegio DE TABLA | SELECT, permiso | Privilegio SELECT | Privilegio SELECT |
| **Acceso a los metadatos** | SELECCIONAR en el privilegio de ESQUEMA INFORMATION_ESQUEMA | Privilegio SELECT | No se requiere ningún privilegio para utilizar la instrucción DESCRIBE | Permiso de DEFINICIÓN de VISTA | No se requiere ningún privilegio para utilizar el comando &quot;\d table&quot; | Privilegio SELECT |

|   | DB2 UDB | TeraData | InfiniDB | Sybase IQ / Sybase ASE | Netezza | Greenplum | AsterData |
|:-:|:-:|:-:|:-:|:-:|:-:|:-:|:-:|
| **Conexión a la base de datos remota** | Autoridad de CONNECT | Privilegio de CONNECT | Creación de un usuario vinculado a un host remoto con TODOS LOS PRIVILEGIOS | No se requiere permiso para utilizar la instrucción CONNECT | No se requiere ningún privilegio | Privilegio de CONNECT | Privilegio de CONNECT |
| **Creación de tablas** | Autoridad CREATETAB | CREAR TABLA o palabra clave TABLE | CREAR privilegio | Autoridad de RECURSOS y permiso CREAR | Privilegio de TABLE | CREAR privilegio | CREAR privilegio |
| **Creación de índices** | Privilegio de INDEX | CREAR INDEX o palabra clave INDEX | Privilegio de INDEX | Autoridad de RECURSOS y permiso CREAR | Privilegio de INDEX | CREAR privilegio | CREAR privilegio |
| **Creación de funciones** | autoridad IMPLICIT_ESQUEMA o privilegio CREATEIN | CREAR FUNCIÓN o palabra clave FUNCTION | CREAR privilegio RUTINO | Autoridad de RECURSOS o autoridad de DBA para funciones de Java | Privilegio de función | Privilegio de uso | CREAR privilegio DE FUNCIÓN |
| **Creación de procedimientos** | autoridad IMPLICIT_ESQUEMA o privilegio CREATEIN | CREAR PROCEDIMIENTO O palabra clave PROCEDURE | CREAR privilegio RUTINO | Autoridad de recursos | Privilegio del procedimiento | Privilegio de uso | CREAR privilegio DE FUNCIÓN |
| **Eliminación de objetos (tablas, índices, funciones, procedimientos)** | DROPIN, privilegio CONTROL o propiedad del objeto | DROP &lt; objeto > o palabra clave relacionada con objetos | Privilegio de DROP | Propiedad del objeto o de la autoridad DBA | Privilegio de DROP | Propiedad del objeto | Propiedad del objeto |
| **Supervisión de las ejecuciones** | EXPLICAR autoridad | No se requiere ningún privilegio para utilizar la instrucción EXPLAIN | Privilegio SELECT | Sólo un administrador del sistema puede ejecutar sp_showplan | No se requiere ningún privilegio para utilizar la instrucción EXPLAIN | No se requiere ningún privilegio para utilizar la instrucción EXPLAIN | No se requiere ningún privilegio para utilizar la instrucción EXPLAIN |
| **Escritura de datos** | INSERTAR y ACTUALIZAR privilegios o autoridad de DATAACCESS | Privilegios de INSERCIÓN y ACTUALIZACIÓN | Privilegios de INSERCIÓN y ACTUALIZACIÓN | Permisos INSERTAR y ACTUALIZAR | Privilegios de INSERCIÓN y ACTUALIZACIÓN | Privilegios de INSERCIÓN y ACTUALIZACIÓN | Privilegios de INSERCIÓN y ACTUALIZACIÓN |
| **Carga de datos en tablas** | Autoridad de CARGA | Privilegios SELECT e INSERT para utilizar respectivamente las instrucciones COPY TO y COPY FROM | Privilegio de ARCHIVO | Sea el propietario de la tabla o del permiso ALTER. Según la opción -gl, la TABLA DE CARGA solo se puede realizar si el usuario tiene la autoridad de DBA | Privilegios SELECT e INSERT | Privilegios SELECT e INSERT | Privilegios SELECT e INSERT |
| **Acceso a los datos del cliente** | INSERTAR/ACTUALIZAR privilegios o autoridad de DATAACCESS | Privilegio SELECT | Privilegio SELECT | SELECT, permiso | Privilegio SELECT | Privilegio SELECT | Privilegio SELECT |
| **Acceso a los metadatos** | No se requiere autorización para utilizar la instrucción DESCRIBE | Mostrar privilegios | Privilegio SELECT | No se requiere permiso para utilizar la instrucción DESCRIBE | No se requiere ningún privilegio para utilizar el comando &quot;\d table&quot; | No se requiere ningún privilegio para utilizar el comando &quot;\d table&quot; | No se requiere ningún privilegio para utilizar el comando SHOW |