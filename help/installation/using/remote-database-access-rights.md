---
product: campaign
title: Permisos para acceder a una base de datos externa
description: Permisos de acceso a bases de datos externas
audience: platform
content-type: reference
topic-tags: connectors
exl-id: 3d43010e-53f8-4aa2-a651-c422a02191fe
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: tm+mt
source-wordcount: '1019'
ht-degree: 99%

---

# Derechos de acceso a bases de datos remotas {#remote-database-access-rights}

En primer lugar, para que el usuario pueda llevar a cabo operaciones en una base de datos externa a través de FDA, el último debe tener un derecho específico en Adobe Campaign.

1. Seleccione el nodo **[!UICONTROL Administration > Access Management > Named Rights]** en el explorador de Adobe Campaign.
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

* **CONNECT**: conexión con la base de datos remota,
* **READ Data**: acceso de sólo lectura a tablas que contienen datos de clientes,
* **READ &#39;MetaData**: acceso a los catálogos de datos del servidor para obtener la estructura de la tabla,
* **LOAD**: carga masiva en tablas de trabajo (requerido cuando se trabaja en colecciones y uniones),
* **CREATE/DROP** para **TABLE/INDEX/PROCEDURE/FUNCTION** (solo para las tablas de trabajo generadas por Adobe Campaign),
* **EXPLAIN** (recomendado): para controlar el rendimiento en caso de problemas,
* **WRITE Data** (según el escenario de integración).

El administrador de la base de datos debe hacer coincidir estos derechos con los derechos específicos de cada motor de base de datos. Para obtener más información, consulte la siguiente sección.

## Derechos FDA {#fda-rights}

|   | Snowflake | Redshift | Oracle | SQLServer | PostgreSQL | MySQL |
|:-:|:-:|:-:|:-:|:-:|:-:|:-:|
| **Conexión a la base de datos remota** | USO EN ALMACÉN (WAREHOUSE), USO EN BASE DE DATOS (DATABASE ) y USO EN PRIVILEGIOS DE ESQUEMA (SCHEMA) | Creación de un usuario vinculado a la cuenta de AWS | Privilegio CREATE SESSION | Permiso CONNECT | Privilegio CONNECT | Creación de un usuario vinculado a un host remoto con TODOS LOS PRIVILEGIOS (ALL PRIVILEGES) |
| **Creación de tablas** | Privilegio CREATE TABLE ON SCHEMA | Privilegio CREATE | Privilegio CREATE TABLE | Permiso CREATE TABLE | Privilegio CREATE | Privilegio CREATE |
| **Creación de índices** | N/A | Privilegio CREATE | Privilegio INDEX o CREATE ANY INDEX | Permiso ALTER | Privilegio CREATE | Privilegio INDEX |
| **Creación de funciones** | Privilegio CREATE FUNCTION ON SCHEMA | El privilegio USAGE ON LANGUAGE plpythonu podrá llamar scripts de python externos | Privilegio CREATE PROCEDURE o CREATE ANY PROCEDURE | Permiso CREATE FUNCTION | Privilegio USAGE | Privilegio CREATE ROUTINE |
| **Creación de procedimientos** | N/D | El privilegio USAGE ON LANGUAGE plpythonu podrá llamar scripts de python externos | Privilegio CREATE PROCEDURE o CREATE ANY PROCEDURE | Permiso CREATE PROCEDURE | Privilegio USAGE (los procedimientos son funciones) | Privilegio CREATE ROUTINE |
| **Eliminación de objetos (tablas, índices, funciones, procedimientos)** | Propiedad del objeto | Tener el objeto o ser un superusuario | Privilegio DROP ANY &lt; object > | Permiso ALTER | Tabla: ser propietario de la tabla. Índice: ser propietario del índice. Función: ser propietario de la función | Privilegio DROP |
| **Monitoreo de las ejecuciones** | Privilegio MONITOR en el objeto requerido | No se requiere ningún privilegio para utilizar el comando EXPLAIN | Privilegio INSERT y SELECT, y privilegio necesario para ejecutar la instrucción en la que se basa el Plan de explicación | Permiso SHOWPLAN | No se requiere ningún privilegio para utilizar la instrucción EXPLAIN | Privilegio SELECT |
| **Escritura de datos** | Privilegios INSERT o UPDATE (según la operación de escritura) | Privilegios INSERT y UPDATE | Privilegios INSERT y UPDATE, o INSERT y UPDATE ANY TABLE | Permisos INSERT y UPDATE | Privilegios INSERT y UPDATE | Privilegios INSERT y UPDATE |
| **Carga de datos en tablas** | Privilegios CREATE STAGE ON SCHEMA, SELECT e INSERT en la tabla de destino | Privilegios SELECT e INSERT | Privilegios SELECT e INSERT | Permisos INSERT, ADMINISTER BULK OPERATIONS y ALTER TABLE | Privilegios SELECT e INSERT | Privilegio FILE |
| **Acceso a los datos del cliente** | Privilegios SELECT en (FUTURE) TABLE(S) o VIEW(S) | Privilegio SELECT | Privilegios SELECT o SELECT ANY TABLE | Permiso SELECT | Privilegio SELECT | Privilegio SELECT |
| **Acceso a metadatos** | Privilegio SELECT en INFORMATION_SCHEMA SCHEMA | Privilegio SELECT | No se requiere ningún privilegio para utilizar la instrucción DESCRIBE | Permiso VIEW DEFINITION | No se requiere ningún privilegio para usar el comando “\d table”. | Privilegio SELECT |

|   | DB2 UDB | TeraData | InfiniDB | Sybase IQ/Sybase ASE | Netezza | Greenplum | AsterData |
|:-:|:-:|:-:|:-:|:-:|:-:|:-:|:-:|
| **Conexión a la base de datos remota** | Autoridad CONNECT | Privilegio CONNECT | Creación de un usuario vinculado a un host remoto con TODOS LOS PRIVILEGIOS | No se requiere permiso para utilizar la instrucción CONNECT. | No se requiere ningún privilegio. | Privilegio CONNECT | Privilegio CONNECT |
| **Creación de tablas** | Autoridad CREATETAB | Palabras clave CREATE TABLE o TABLE | Privilegio CREATE | Autoridad RESOURCE y permiso CREATE | Privilegio TABLE | Privilegio CREATE | Privilegio CREATE |
| **Creación de índices** | Privilegio INDEX | Palabras clave CREATE INDEX o INDEX | Privilegio INDEX | Autoridad RESOURCE y permiso CREATE | Privilegio INDEX | Privilegio CREATE | Privilegio CREATE |
| **Creación de funciones** | Autoridad IMPLICIT_SCHEMA o privilegio CREATEIN | Palabras clave CREATE FUNCTION o FUNCTION | Privilegio CREATE ROUTINE | Autoridad RESOURCE o autoridad de DBA para funciones de Java | Privilegio FUNCTION | Privilegio USAGE | Privilegio CREATE FUNCTION |
| **Creación de procedimientos** | Autoridad IMPLICIT_SCHEMA o privilegio CREATEIN | Palabras claves CREATE PROCEDURE o PROCEDURE | Privilegio CREATE ROUTINE | Autoridad RESOURCE | Privilegio PROCEDURE | Privilegio USAGE | Privilegio CREATE FUNCTION |
| **Eliminación de objetos (tablas, índices, funciones, procedimientos)** | Privilegio DROPIN, privilegio CONTROL o propiedad del objeto | DROP &lt; object > o palabra clave relacionada con objetos | Privilegio DROP | Propiedad del objeto o de la autoridad DBA | Privilegio DROP | Propiedad del objeto | Propiedad del objeto |
| **Monitoreo de las ejecuciones** | Autoridad EXPLAIN | No se requiere ningún privilegio para utilizar la instrucción EXPLAIN | Privilegio SELECT | Solo un administrador del sistema puede ejecutar sp_showplan. | No se requiere ningún privilegio para utilizar la instrucción EXPLAIN | No se requiere ningún privilegio para utilizar la instrucción EXPLAIN | No se requiere ningún privilegio para utilizar la instrucción EXPLAIN |
| **Escritura de datos** | privilegios INSERT y UPDATE o autoridad de DATAACCESS | Privilegios INSERT y UPDATE | Privilegios INSERT y UPDATE | Permisos INSERT y UPDATE | Privilegios INSERT y UPDATE | Privilegios INSERT y UPDATE | Privilegios INSERT y UPDATE |
| **Carga de datos en tablas** | Autoridad LOAD | Privilegios SELECT e INSERT para utilizar respectivamente las instrucciones COPY TO y COPY FROM | Privilegio FILE | Sea el propietario de la tabla o del permiso ALTER. Según la opción -gl, LOAD TABLE solo se puede realizar si el usuario tiene la autoridad de DBA. | Privilegios SELECT e INSERT | Privilegios SELECT e INSERT | Privilegios SELECT e INSERT |
| **Acceso a los datos del cliente** | Privilegios INSERT/UPDATE o autoridad de DATAACCESS | Privilegio SELECT | Privilegio SELECT | Permiso SELECT | Privilegio SELECT | Privilegio SELECT | Privilegio SELECT |
| **Acceso a metadatos** | No se requiere autorización para utilizar la instrucción DESCRIBE. | Privilegio de SHOW | Privilegio SELECT | No se requiere permiso para utilizar la instrucción DESCRIBE. | No se requiere ningún privilegio para usar el comando “\d table”. | No se requiere ningún privilegio para usar el comando “\d table”. | No se requiere ningún privilegio para utilizar el comando SHOW. |
