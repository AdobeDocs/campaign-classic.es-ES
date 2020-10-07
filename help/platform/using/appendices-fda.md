---
title: Apéndices
seo-title: Apéndices de FDA
description: Apéndices de FDA
seo-description: null
page-status-flag: never-activated
uuid: 2596fabc-679a-45c8-a62a-165c221654b7
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: platform
content-type: reference
topic-tags: connectors
discoiquuid: a84a73a9-9930-449f-8b81-007a0e9d5233
translation-type: tm+mt
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: tm+mt
source-wordcount: '1416'
ht-degree: 100%

---


# Apéndices {#fda-appendices}

## Configuraciones adicionales de Teradata {#teradata-configuration}

### Compatibilidad {#teradata-compatibility}

**Basado en Unicode**

| Versión de la base de datos | Versión del controlador | Se requiere una versión de Campaign mínima | Nota |
|:-:|:-:|:-:|:-:|
| 15 | 15 | Campaign Classic 17.9 | En Linux: Es posible que las consultas con marca de tiempo no se realicen correctamente (corregido en la versión 8937 para 18.4 y 8977 para 18.10). En el modo de depuración, pueden mostrarse advertencias relativas al uso incorrecto de la memoria en el controlador. |
| 15 | 16 | Campaign Classic 17.9 | Configuración recomendada para una base de datos Teradata 15 en Linux. |
| 16 | 16 | Campaign Classic 18.10 | Los caracteres Unicode con pares sustitutos no se gestionan completamente. El uso de caracteres de sustitución en los datos debería funcionar. El uso de sustitutos en una condición de filtrado de consulta no funcionará sin este cambio. |
| 16 | 15 | no admitido |   |

**Basado en Latin1**

Las versiones anteriores a Adobe Campaign Classic 17.9 solo admitían la base de datos de Teradata en Latin-1.

A partir de Adobe Campaign Classic 17.9, ahora se admite de forma predeterminada la base de datos de Teradata en Unicode.

Los clientes que tengan una base de datos de Teradata en Latin-1 que migran a una versión reciente de Campaign Classic tendrán que agregar el parámetro APICharSize=1 en las opciones de la cuenta externa.

### Configuración de la base de datos {#database-configuration}

#### Configuración del usuario {#user-configuration}

Se requieren los siguientes derechos: procedimientos personalizados create/drop/execute y tablas create/drop/insert/select. También es posible que tenga que crear funciones de modo de usuario si desea utilizar las funciones md5 y sha2 en la instancia de Adobe Campaign.

Asegúrese de configurar la zona horaria específica. Debe coincidir con el que se establecerá en la cuenta externa creada en la instancia de Adobe Campaign.

Adobe Campaign no establecerá ningún modo de protección (reserva) en los objetos que creará en la base de datos. Es posible que tenga que establecer un valor predeterminado en el usuario que Adobe Campaign utilizará para conectarse a la base de datos de Teradata mediante la siguiente consulta:

| Disable default fallback |
| :-: |
| ```MODIFY USER $login$ AS NO FALLBACK;``` |

#### Instalación de MD5 {#md5-installation}

Si desea utilizar funciones md5 en la instancia de Adobe Campaign, deberá instalar la función de modo usuario en la base de datos de Teradata desde esta [página](https://downloads.teradata.com/download/extensibility/md5-message-digest-udf) (md5_20080530.zip).

El sha1 del archivo descargado es el siguiente: 65cc0bb6935f72fcd84fef1ebcd64c00115dfd1e.

Para instalar MD5:

1. Descomprima el archivo md5_20080530.zip.

1. Vaya al directorio md5/src.

1. Conéctese a la base de datos de Teradata mediante bteq.

1. Ejecute el siguiente comando bteq:

   ```
   .run file = hash_md5.btq
   ```

#### Instalación de SHA2 {#sha2-installation}

Si desea utilizar funciones sha2 en la instancia de Adobe Campaign, deberá instalar la función de modo usuario en la base de datos de Teradata desde esta [página](https://github.com/akuroda/teradata-udf-sha2/archive/v1.0.zip) (teradata-udf-sha2-1.0.zip).

El sha1 del archivo descargado es el siguiente e87438d37424836358bd3902cf1adeb629349780.

Para instalar sha2:

1. Descomprima el archivo teradata-udf-sha2-1.0.zip.

1. Vaya al directorio teradata-udf-sha2-1.0/src.

1. Conéctese a la base de datos de Teradata mediante bteq.

1. Ejecute estos dos comandos bteq:

   ```
   .run file = hash_sha256.sql
   .run file = hash_sha512.sql
   ```

#### Instalación de UDF_UTF16TO8 {#UDF-UTF16TO8-installation}

Si desea utilizar las funciones udf_utf16to8 en la instancia de Adobe Campaign, deberá instalar la función de modo de usuario en la base de datos de Teradata desde el kit **de herramientas Unicode** de Teradata en esta [página](https://downloads.teradata.com/download/tools/unicode-tool-kit) (utk_release1.7.0.0.zip).

El sha1 del archivo descargado es el siguiente e58235f434f52c71316a577cb48e20b97d24f470.

Para instalar udf_utf16to8:

1. Descomprima el archivo utk_release1.7.0.0.zip.

1. Busque udf_utf16to8.o en los archivos extraídos y vaya al directorio que contiene el archivo. Debe solicitarse utk_release1.7.0.0/utk_release1.7.0.0/04 TranslationUDFs/01 Teradata UDFs/suselinux-x8664/udf_installation/.

1. Conéctese a la base de datos de Teradata mediante bteq.

1. Escriba el siguiente comando bteq:

   ```
   REPLACE FUNCTION udf_utf16to8 (
   inputString VARCHAR(8000) CHARACTER SET UNICODE
   ) RETURNS VARCHAR(16000) CHARACTER SET LATIN
   LANGUAGE C
   NO SQL
   EXTERNAL NAME 'CO!i18n103!udf_utf16to8.o!F!udf_utf16to8'
   PARAMETER STYLE SQL;
   
   -- Test: should return 410042
   SELECT CAST(Char2HexInt(UDF_UTF16to8(_UNICODE'004100000042'XC)) AS VARCHAR(100));
   ```

### Configuración del servidor de Campaign para Linux {#campaign-server-linux}

Se requiere lo siguiente para la instalación del controlador:

* Controlador ODBC Teradata, que se puede encontrar en esta [página](https://downloads.teradata.com/download/connectivity/odbc-driver/linux)

* Herramientas y utilidades de Teradata (utilizadas para la carga masiva), que se pueden encontrar en esta [página](https://downloads.teradata.com/download/tools/teradata-tools-and-utilities-linux-installation-package-0)

Nombres de archivos y sha1:

* tdodbc1620__linux_indep.16.20.00.00-1.tar.gz 121fdd978b56fe1304fc5cb7819741b0847f44fd

* TeradataToolsAndUtilitiesBase__linux_indep.16.20.01.00.tar.gz b 29d0af5ffd8dcf68a9dbbaa6f8639387b19c563

Si no hay ningún paquete para su distribución Linux, puede instalarlos según se explica en CentOS 7 (por ejemplo, usando docker) y luego copiar el contenido de /opt/teradata en su servidor de Adobe Campaign.

#### Instalación del controlador ODBC {#odbc-installation}

Para instalar el controlador ODBC:

1. Extraiga el archivo tdodbc1620__linux_indep.16.20.00.00-1.tar.gz.

1. Vaya al directorio tdodbc1620.

1. Es posible que tenga que corregir la secuencia de comandos de configuración:

   ```
   "sed -i s/16.10/16.20/ setup_wrapper.sh".
   ```

1. Ejecute setup_wrapper.sh.

#### Instalación de herramientas y utilidades de Teradata {#teradata-tools-installation}

Para instalar las herramientas:

1. Extraiga el archivo TeradataToolsAndUtilitiesBase__linux_indep.16.20.01.00.tar.gz.

1. Vaya al directorio TeradataToolsAndUtilitiesBase/Linux/i386-x8664/tdicu.

1. Ejecute setup_wrapper.sh.

1. Vaya al directorio TeradataToolsAndUtilitiesBase/Linux/i386-x8664/cliv2.

1. Ejecute setup_wrapper.sh.

1. Vaya al directorio TeradataToolsAndUtilitiesBase/Linux/i386-x8664/tptbase.

1. Ejecute setup_wrapper.sh.

1. Debe haber un archivo libtelapi.so disponible en /opt/teradata/client/16.20/lib64.

#### Configuración del controlador {#driver-configuration}

Para obtener más información sobre la configuración de controladores, consulte esta [sección](../../platform/using/legacy-connectors.md#configure-access-to-teradata).

#### Variables de entorno {#environment-varaiables}

Para obtener más información sobre las variables de entorno del servidor de Adobe Campaign, consulte esta [sección](../../platform/using/legacy-connectors.md#configure-access-to-teradata).

### Configuración del servidor de Campaign para Windows {#campaign-server-windows}

Primero debe descargar las herramientas y utilidades de Teradata para Windows. Puede descargarlas desde esta [página](https://downloads.teradata.com/download/tools/teradata-tools-and-utilities-windows-installation-package)

Asegúrese de instalar el controlador ODBC y la base del transportador paralelo de Teradata. Instalará telapi.dll, que se utiliza para realizar cargas masivas en la base de datos de Teradata.

Asegúrese de que la ruta del controlador y las utilidades se encuentra en la variable PATH de nlserver durante la ejecución. De forma predeterminada, la ruta es C:\Program Files (x86)\Teradata\Client\15.10\bin para Windows de 32 bits o C:\Programa Files\Teradata\Client\15.10\bin para 64 bits.

### Solución de problemas de cuentas externas {#external-account-troubleshooting}

Si aparece el siguiente error al probar la conexión **TIM-030008 Date &#39;2&#39;: missing character(s) (iRc=-53)** asegúrese de que el controlador ODBC esté correctamente instalado y de que LD_LIBRARY_PATH (Linux)/PATH (Windows) está configurado para el servidor de Campaign.

Error de ODBC **ODB-240000:[no se encontró el nombre del origen de datos de Microsoft][ODBC Driver Manager]y no se especificó ningún controlador predeterminado.** se produce con Windows si se utiliza un controlador 16.X. Adobe Campaign espera que el nombre de Teradata sea &#39;{teradata}&#39; en odbcinst.ini.
Si tiene una versión de servidor de Adobe Campaign 18.10, puede agregar ODBCDriverName=&quot;Teradata Database ODBC Driver 16.10&quot; en las opciones de la cuenta externa. El número de versión puede cambiar, y se puede encontrar el nombre exacto ejecutando odbcad32.exe y accediendo a la pestaña Controladores.
En el caso de una versión inferior a 18.10, tendrá que copiar la sección Teradata de odbcinst.ini creada por la instalación del controlador en una nueva sección llamada Teradata,regedit puede utilizarse en este caso.

Si la base está en latin1, tendrá que agregar APICharSize=1 en las opciones.

### Zona horaria {#timezone}

Teradata utiliza nombres de la zona horaria que no son estándar y puede encontrar la lista en el sitio [Teradata](https://docs.teradata.com/reader/rgAb27O_xRmMVc_aQq2VGw/oGKvgl7gCeBMTGrp59BnwA). Adobe Campaign intentará convertir la zona horaria proporcionada en la configuración externa a algo que Teradata entienda. Si no se encuentra ninguna correspondencia, se encontrará la zona horaria GMT+X (o GMT-X) más cercana para la sesión, con una advertencia en el registro.

La conversión se realiza leyendo un archivo llamado teradata_timezones.txt que debe estar en el siguiente directorio de datos: /usr/local/neolane/nl6/datakit en Linux. Si edita este archivo, asegúrese de ponerse en contacto con el equipo de Adobe Campaign para realizar el cambio en el código fuente. De lo contrario, este archivo se sobrescribirá durante la próxima actualización de Campaign.

La zona horaria usada para conectarse se indicará cuando se ejecuta nlserver con el conmutador -verbose, por ejemplo:

```
15:04:04 >   ODB-240007 Teradata: will use 'Europe Central' as session time zone.
```

Si la zona horaria utilizada no es la correcta, se puede agregar una opción denominada &quot;TimeZoneName&quot; en la cuenta externa. En ese caso, utilice el valor Teradata, por ejemplo &quot;TimeZoneName=Europe Central&quot;.

Cuando se utiliza carga masiva o &quot;carga rápida&quot; en documentos Teradata, Campaign no puede indicar la zona horaria. Por lo tanto, se recomienda establecer la zona horaria predeterminada del usuario que la Campaign utilizará para conectarse:

```
MODIFY USER $login$ AS TIME ZONE = 'Europe Central';
```

## Configuración de MySQL 5.7 {#mysql-57-configuration}

### Configuración del servidor {#server-configuration-mysql}

La configuración del servidor no requiere ningún paso de instalación específico. Adobe Campaign debe trabajar con una base de datos en latin1, predeterminada en MySQL, o una base de datos en Unicode.

### Instalación del controlador {#driver-installation-mysql}

#### Debian {#debian-mysql}

Descargue mysql-apt-config.deb desde esta [página](https://dev.mysql.com/doc/mysql-apt-repo-quick-guide/en).

Instale la biblioteca del cliente:

```
$ dpkg -i mysql-apt-config_*_all.deb # choose mysql-5.7 in the configuration menu
$ apt update
$ apt install libmysqlclient20
```

#### Windows {#windows-mysql}

Descargue el conector C desde esta [página](https://dev.mysql.com/downloads/connector/c). Se recomienda descargar la versión 5.7.

Asegúrese de que el directorio que contiene libmysqlclient.dll se agrega a la variable de entorno PATH que utilizará nlserver.

#### CentOS {#centos-mysql}

Descargue mysql57-community-release.noarch.rpm desde esta [página](https://dev.mysql.com/downloads/repo/yum).

Instale la biblioteca del cliente:

$ yum install mysql57-community-release-el7-9.noarch.rpm
$ yum install mysql-community-libs

### Configuración de cuentas externas {#external-account-mysql}

La configuración de cuentas externas no requiere ningún paso específico. Asegúrese de que la zona horaria y los datos Usar Unicode estén establecidos según la base de datos.
