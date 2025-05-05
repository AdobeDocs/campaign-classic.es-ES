---
product: campaign
title: El archivo de configuración del servidor
description: El archivo de configuración del servidor
feature: Installation, Instance Settings
audience: installation
content-type: reference
topic-tags: appendices
exl-id: 70cd6a4b-c839-4bd9-b9a7-5a12e59c0cbf
source-git-commit: f032ed3bdc0b402c8281bc34e6cb29f3c575aaf9
workflow-type: tm+mt
source-wordcount: '8067'
ht-degree: 5%

---

# El archivo de configuración del servidor{#the-server-configuration-file}

La configuración general de Adobe Campaign se define en el archivo **serverConf.xml**, ubicado en el directorio **conf** del directorio de instalación. Esta sección enumera todos los nodos y parámetros diferentes del archivo **serverConf.xml**.

>[!NOTE]
>
>Las configuraciones del lado del servidor solo se pueden realizar mediante el Adobe para implementaciones alojadas por el Adobe. Para obtener más información sobre las diferentes implementaciones, consulte la sección [Modelos de alojamiento](../../installation/using/hosting-models.md) o [esta página](../../installation/using/capability-matrix.md). Los pasos de instalación y configuración para los modelos hospedados e híbridos se presentan en esta [sección](../../installation/using/hosting-models.md).

Los primeros parámetros están dentro del nodo **shared**. Están relacionados con la instancia de. Son potencialmente utilizados por todos los comandos nlserver (nlserver web, nlserver wfserver, etc.). Las otras secciones están relacionadas con un subcomando nlserver específico.

**Parámetros compartidos**

* [authentication](#authentication)
* [dataStore](#datastore)
* [dnsConfig](#dnsconfig)
* [exec](#exec)
* [htmlToPdf](#htmltopdf)
* [ims](#ims)
* [javaScript](#javascript)
* [mailExchanger](#mailexchanger)
* [módulo](#module)
* [control](#monitoring)
* [ooconv](#ooconv)
* [proxyConfig](#proxyconfig)
* [threadPool](#threadpool)
* [urlPermission](#urlpermission)
* [cusHeaders](#cusheaders)
* [xtkJobs](#xtkjobs)

**Otros parámetros**

* [archivo](#archiving)
* [inMail](#inmail)
* [interactiond](#interactiond)
* [mta.](#mta)
* [nmac](#nmac)
* [canalizado](#pipelined)
* [reparar](#repair)
* [securityZone](#securityzone)
* [sms](#sms)
* [estadísticas](#stat)
* [syslogd](#syslogd)
* [seguimiento](#tracking)
* [trackinglogd](#trackinglogd)
* [web](#web)
* [wfserver](#wfserver)

## authentication {#authentication}

Estos son los diferentes parámetros del nodo **authentication**:

<table> 
 <thead> 
  <tr> 
   <th> Parámetro </th> 
   <th> Descripción </th> 
   <th> Tipo </th> 
   <th> Valor predeterminado </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> checkIPConsistent<br /> </td> 
   <td> Habilitar comprobación de direcciones IP.<br /> </td> 
   <td> Booleano<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> defaultMode<br /> </td> 
   <td> Modo de identificación predeterminado.<br /> </td> 
   <td> Cadena<br /> </td> 
   <td> 'nl'<br /> </td> 
  </tr> 
  <tr> 
   <td> longSessionTimeOutSec<br /> </td> 
   <td> Tiempo de espera de sesiones largas en segundos.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 1296000<br /> </td> 
  </tr> 
  <tr> 
   <td> securityTimeOutSec<br /> </td> 
   <td> Tiempo de espera de token de seguridad en segundos.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 86400<br /> </td> 
  </tr> 
  <tr> 
   <td> sessionCacheSec<br /> </td> 
   <td> Duración de caché: caché de información de sesión en segundos.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 600<br /> </td> 
  </tr> 
  <tr> 
   <td> sessionTimeOutSec<br /> </td> 
   <td> Tiempo de espera de sesión en segundos.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 86400<br /> </td> 
  </tr> 
 </tbody> 
</table>

### XTK {#xtk}

Estos son los diferentes parámetros del nodo **authentication > XTK**:

<table> 
 <thead> 
  <tr> 
   <th> Parámetro </th> 
   <th> Descripción </th> 
   <th> Tipo </th> 
   <th> Valor predeterminado </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> internalPassword<br /> </td> 
   <td> Contraseña de la cuenta interna.<br /> </td> 
   <td> Cadena<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> internalSecurityZone<br /> </td> 
   <td> Zona de seguridad de cuenta interna: zona autorizada para la cuenta interna.<br /> </td> 
   <td> Cadena<br /> </td> 
   <td> 'lan'<br /> </td> 
  </tr> 
 </tbody> 
</table>

## dataStore {#datastore}

Estos son los diferentes parámetros del nodo **dataStore**. Aquí es donde se definen las fuentes de datos del servidor.

<table> 
 <thead> 
  <tr> 
   <th> Parámetro </th> 
   <th> Descripción </th> 
   <th> Tipo </th> 
   <th> Valor predeterminado </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> exportDirectory<br /> </td> 
   <td> Directorio de exportación: ruta del directorio de destino para los datos exportados.<br /> </td> 
   <td> Cadena<br /> </td> 
   <td> '$(XTK_INSTALL_DIR)/var/$(INSTANCE_NAME)/export/' <br /> </td> 
  </tr> 
  <tr> 
   <td> extraSandboxedDirectories<br /> </td> 
   <td> Directorios en zona protegida adicionales: otras rutas que se agregarán en la zona protegida (separados por comas).<br /> </td> 
   <td> Cadena<br /> </td> 
   <td> '/home/customers/,/sftp/' <br /> </td> 
  </tr> 
  <tr> 
   <td> formCacheTimeToLive<br /> </td> 
   <td> Retraso de caducidad de la caché del formulario: tiempo de espera en segundos tras el cual se invalida una entrada de caché. O significa que las entradas de la caché solo se actualizan en el momento de la publicación.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 600<br /> </td> 
  </tr> 
  <tr> 
   <td> hosts<br /> </td> 
   <td> Máscaras DNS: lista de máscaras DNS a las que sirve esta instancia (separadas por comas, se pueden utilizar * y ? patrones).<br /> </td> 
   <td> Cadena<br /> </td> 
   <td> '*'<br /> </td> 
  </tr> 
  <tr> 
   <td> interactionCacheTimeToLive<br /> </td> 
   <td> Demora de caducidad de caché de JSSP de interacción: tiempo de espera en segundos tras el cual se invalida una entrada de caché. Un valor negativo significa que la caché siempre se invalida. '0', los valores vacíos o no válidos se consideran 60.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 300<br /> </td> 
  </tr> 
  <tr> 
   <td> lang<br /> </td> 
   <td> Lenguaje de instancia (enumeración). Los valores posibles son 'fr_FR' (francés), 'en_GB' (inglés (Reino Unido), 'en_US' (inglés (EE.UU.), 'de_DE' (alemán) y 'ja_JP' (japonés).<br /> </td> 
   <td> Cadena<br /> </td> 
   <td> 'en_US'<br /> </td> 
  </tr> 
  <tr> 
   <td> uploadDirectory<br /> </td> 
   <td> Cargar carpeta: ruta del directorio de destino para los datos cargados.<br /> </td> 
   <td> Cadena<br /> </td> 
   <td> '$(XTK_INSTALL_DIR)/var/$(INSTANCE_NAME)/upload/' <br /> </td> 
  </tr> 
  <tr> 
   <td> uploadAllowlist<br /> </td> 
   <td> Archivos autorizados para descargar separados por ",". La cadena debe ser una expresión Java regular válida. Ver <a href="file-res-management.md" target="_blank">Limitación de archivos cargables</a>.<br /> </td> 
   <td> Cadena<br /> </td> 
   <td> '.+' <br /> </td> 
  </tr> 
  <tr> 
   <td> useVault<br /> </td> 
   <td> Almacenar secretos en Vault: usar Hashicorp Vault.<br /> </td> 
   <td> Booleano<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> vaultSecretPath<br /> </td> 
   <td> Ruta secreta en Vault<br /> </td> 
   <td> Cadena<br /> </td> 
   <td> '/v1/secret/campaign/'<br /> </td> 
  </tr> 
  <tr> 
   <td> vaultTokenPath<br /> </td> 
   <td> Ruta de acceso local del archivo que contiene el token de Vault. $(HOME) se puede usar en esta ruta (pero no en otras variables env).<br /> </td> 
   <td> Cadena<br /> </td> 
   <td> '$(HOME)/.vaulttoken'<br /> </td> 
  </tr> 
  <tr> 
   <td> vaultUrl<br /> </td> 
   <td> URL de Hashicorp Vault <br /> </td> 
   <td> Cadena<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> viewCacheTimeToLive<br /> </td> 
   <td> Período de validez de la caché de visualización: tiempo de espera en segundos tras el cual se invalida una entrada de caché. Un valor negativo significa que la caché siempre se invalida. '0', los valores vacíos o no válidos se consideran 60.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 600<br /> </td> 
  </tr> 
  <tr> 
   <td> workingDirectory<br /> </td> 
   <td> XPath del directorio de trabajo.<br /> </td> 
   <td> Cadena<br /> </td> 
   <td> workingDirectory : XPath del directorio de trabajo. Predeterminado: '$(XTK_INSTALL_DIR)/var/$(INSTANCE_NAME)/workspace/'<br /> </td> 
  </tr> 
 </tbody> 
</table>

### proxyAdjust {#proxyadjust}

Estos son los diferentes parámetros del nodo **dataStore > proxyAdjust**. Las direcciones URL que coincidan con la expresión regular se regeneran en función de la dirección URL definida en urlBase.

<table> 
 <thead> 
  <tr> 
   <th> Parámetro </th> 
   <th> Descripción </th> 
   <th> Tipo </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> urlBase<br /> </td> 
   <td> Base para utilizar al generar URL externas. Ejemplo: https://server.domain.com<br /> </td> 
   <td> Cadena<br /> </td> 
  </tr> 
  <tr> 
   <td> urlRegEx<br /> </td> 
   <td> Expresión regular para que coincida con las direcciones URL. Ejemplo: http://server\.lan\.net.*<br /> </td> 
   <td> Cadena<br /> </td> 
  </tr> 
 </tbody> 
</table>

### dataSource {#datasource}

Estos son los diferentes parámetros del nodo **dataStore > dataSource**.

<table> 
 <thead> 
  <tr> 
   <th> Parámetro </th> 
   <th> Descripción </th> 
   <th> Tipo </th> 
   <th> Valor predeterminado </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> nombre<br /> </td> 
   <td> Nombre de Data Source<br /> </td> 
   <td> Cadena<br /> </td> 
   <td> predeterminado<br /> </td> 
  </tr> 
 </tbody> 
</table>

En el nodo **dataStore > dataSource > dbcnx**, configure la configuración de conexión:

<table> 
 <thead> 
  <tr> 
   <th> Parámetro </th> 
   <th> Descripción </th> 
   <th> Tipo </th> 
   <th> Valor predeterminado <br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> NChar<br /> </td> 
   <td> Almacenamiento Unicode<br /> </td> 
   <td> Booleano<br /> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> dbSchema<br /> </td> 
   <td> Workspace<br /> </td> 
   <td> Cadena<br /> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> cifrado<br /> </td> 
   <td> Contraseña cifrada<br /> </td> 
   <td> Booleano<br /> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> iniciar sesión<br /> </td> 
   <td> Cuenta<br /> </td> 
   <td> Cadena<br /> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> contraseña<br /> </td> 
   <td> Contraseña<br /> </td> 
   <td> Cadena<br /> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> proveedor<br /> </td> 
   <td> Tipo (enumeración). Los valores posibles son 'Oracle', 'MSSQL' (Microsoft SQL Server), 'PostgreSQL' (PostgreSQL), 'Teradata', 'MySQL', 'Netezza', 'AsterData', 'SAPHANA' (SAP HANA), 'RedShift' (Amazon Redshift), 'ODBC' (ODBC (Sybase ASE, Sybase IQ)), 'Relay' (HTTP relay to remote database).<br /> </td> 
   <td> Cadena<br /> </td> 
   <td> 'Oracle'<br /> </td> 
  </tr> 
  <tr> 
   <td> servidor<br /> </td> 
   <td> Servidor<br /> </td> 
   <td> Cadena<br /> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> zona horaria<br /> </td> 
   <td> Zona horaria: consulte <a href="../../installation/using/time-zone-management.md" target="_blank">Administración de zona horaria</a>.<br /> </td> 
   <td> Cadena<br /> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> unicodeData<br /> </td> 
   <td> Datos Unicode en la base de datos <br /> </td> 
   <td> Booleano<br /> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> useTimestampTZ<br /> </td> 
   <td> Campos de fecha con zona horaria: consulte <a href="../../installation/using/time-zone-management.md" target="_blank">Administración de zona horaria</a>.<br /> </td> 
   <td> Booleano<br /> </td> 
   <td> </td> 
  </tr> 
 </tbody> 
</table>

En el nodo **dataStore > dataSource > sqlParams**, configure los parámetros SQL:

<table> 
 <thead> 
  <tr> 
   <th> Parámetro </th> 
   <th> Descripción </th> 
   <th> Tipo </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> funcPrefix<br /> </td> 
   <td> Prefijo de función <br /> </td> 
   <td> Cadena<br /> </td> 
  </tr> 
 </tbody> 
</table>

En el nodo **dataStore > dataSource > pool**, configure los parámetros del grupo de conexiones asociado:

<table> 
 <thead> 
  <tr> 
   <th> Parámetro </th> 
   <th> Descripción </th> 
   <th> Tipo </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> liveTestDelaySec<br /> </td> 
   <td> Retraso entre las comprobaciones de validez de la conexión.<br /> </td> 
   <td> Corto<br /> </td> 
  </tr> 
  <tr> 
   <td> freeCnx<br /> </td> 
   <td> Número de conexión gratuita mantenida en el grupo.<br /> </td> 
   <td> Corto<br /> </td> 
  </tr> 
  <tr> 
   <td> maxCnx<br /> </td> 
   <td> Número máximo de conexiones permitidas antes de rechazar una nueva conexión. Ver esta <a href="https://helpx.adobe.com/es/campaign/kb/how-to-increase-the-maximum-number-of-database-connections-from-.html">nota técnica</a>.<br /> </td> 
   <td> Corto<br /> </td> 
  </tr> 
  <tr> 
   <td> maxIdleDelaySec<br /> </td> 
   <td> Tiempo máximo de inactivo de la conexión. 0 significa valor predeterminado.<br /> </td> 
   <td> Corto<br /> </td> 
  </tr> 
 </tbody> 
</table>

### virtualDir {#virtualdir}

Estos son los diferentes parámetros del nodo **dataStore > virtualDir**. Esta es la configuración del directorio virtual para la asignación de directorio real.

Para obtener más información, consulte [Administración de recursos públicos](file-res-management.md).

<table> 
 <thead> 
  <tr> 
   <th> Parámetro </th> 
   <th> Descripción </th> 
   <th> Tipo </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> nombre<br /> </td> 
   <td> Nombre del directorio virtual <br /> </td> 
   <td> Cadena<br /> </td> 
  </tr> 
  <tr> 
   <td> ruta<br /> </td> 
   <td> Ruta de acceso completa del directorio real <br /> </td> 
   <td> Cadena<br /> </td> 
  </tr> 
 </tbody> 
</table>

Esta es la configuración predeterminada:

```
<virtualDir name="images" path="$(XTK_INSTALL_DIR)/var/res/img/"/>
<virtualDir name="formCache" path="$(XTK_INSTALL_DIR)/var/$(INSTANCE_NAME)/formCache/"/>
<virtualDir name="publicFileRes" path="$(XTK_INSTALL_DIR)/var/res/$(INSTANCE_NAME)"/>
```

### preprocessCommand {#preprocesscommand}

Estos son los diferentes parámetros del nodo **dataStore > preprocessCommand**. Estos son los comandos autorizados para el preprocesamiento de la actividad de flujo de trabajo &quot;Cargar archivo&quot;.

<table> 
 <thead> 
  <tr> 
   <th> Parámetro </th> 
   <th> Descripción </th> 
   <th> Tipo </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> comando <br /> </td> 
   <td> Línea de comandos <br /> </td> 
   <td> Cadena<br /> </td> 
  </tr> 
  <tr> 
   <td> etiqueta <br /> </td> 
   <td> Etiqueta de línea de comandos <br /> </td> 
   <td> Cadena<br /> </td> 
  </tr> 
  <tr> 
   <td> nombre<br /> </td> 
   <td> Nombre de línea de comandos <br /> </td> 
   <td> Cadena<br /> </td> 
  </tr> 
 </tbody> 
</table>

Esta es la configuración predeterminada:

```
<preprocessCommand command="" label="None" name="none"/>
<preprocessCommand command="zcat &quot;$fileName&quot;" label="Decompression" name="zcat"/><preprocessCommand command="gpg --decrypt &quot;$fileName&quot;" label="Decrypt" name="gpg"/>
```

## dnsConfig {#dnsconfig}

Estos son los diferentes parámetros del nodo **dnsConfig** (configuración de DNS).

Para obtener más información, consulte esta [sección](../../installation/using/configuring-campaign-server.md).

<table> 
 <thead> 
  <tr> 
   <th> Parámetro </th> 
   <th> Descripción </th> 
   <th> Tipo </th> 
   <th> Valor predeterminado </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> localDomain<br /> </td> 
   <td> Domain name: nombre de dominio predeterminado. Utilizado por el comando SMTP HELO. De forma predeterminada, utiliza los parámetros de red de la primera interfaz de red declarada en Windows; o analiza el file/etc/resolv.conf en Linux (dominio o entrada de búsqueda). <br /> </td> 
   <td> Cadena<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> nameServers<br /> </td> 
   <td> Servidor DNS: lista separada por comas de servidores de nombres de dominio (DNS). Consulte la nota siguiente.<br /> </td> 
   <td> Cadena<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> reintentar<br /> </td> 
   <td> Número de reintentos de una consulta DNS.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 4<br /> </td> 
  </tr> 
  <tr> 
   <td> tiempo de espera <br /> </td> 
   <td> Tiempo de espera en milisegundos para una consulta DNS.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 5000<br /> </td> 
  </tr> 
 </tbody> 
</table>

>[!NOTE]
>
>Nota sobre **nameSevers**: de forma predeterminada, utiliza la red
>parámetros de la primera interfaz de red declarada en Windows
>no definido en UNIX. Define los servidores de nombres de dominio (DNS)
>utilizado por el MTA para obtener el Mail Exchanger declarado para
>un dominio.
>
>Si no se define este valor, el MTA busca esta información en la configuración de red del host. Si son posibles varios DNS, las distintas direcciones DNS deben estar separadas por una coma (por ejemplo: 212.155.207.1,212.155.207.2). Si el servidor de entrega tiene varias interfaces de red, la lista DNS utilizada por el MTA es la primera. En este caso, se recomienda especificar el parámetro **nameServer** para evitar cualquier ambigüedad.

>[!CAUTION]
>
>Si la configuración del host de red utiliza DHCP, el MTA no encontrará la lista DNS proporcionada por DHCP. En este caso, se recomienda especificar la lista DNS en los parámetros de red del panel de control de Windows.

## exec {#exec}

Estos son los diferentes parámetros del nodo **exec** (ejecución de comandos).

Para obtener más información, consulte [Restricción de comandos externos autorizados](../../installation/using/configuring-campaign-server.md#restricting-authorized-external-commands).

<table> 
 <thead> 
  <tr> 
   <th> Parámetro </th> 
   <th> Descripción </th> 
   <th> Tipo </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> blacklistFile<br /> </td> 
   <td> Ruta al archivo que contiene los comandos que se van a agregar a la lista de permitidos. <br /> </td> 
   <td> Cadena<br /> </td> 
  </tr> 
  <tr> 
   <td> usuario<br /> </td> 
   <td> Ejecutar comandos como otro usuario.<br /> </td> 
   <td> Cadena<br /> </td> 
  </tr> 
 </tbody> 
</table>

## htmlToPdf {#htmltopdf}

Estos son los diferentes parámetros del nodo **htmlToPdf**. Esta es la configuración del servicio para convertir páginas web en documentos de PDF.

<table> 
 <thead> 
  <tr> 
   <th> Parámetro </th> 
   <th> Descripción </th> 
   <th> Tipo </th> 
   <th> Valor predeterminado </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> comando <br /> </td> 
   <td> Línea de comandos para ejecutar la conversión (en modo 'otro').<br /> </td> 
   <td> Cadena<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessCount<br /> </td> 
   <td> Máx. número de procesos de conversión permitidos a la vez en un equipo.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 5<br /> </td> 
  </tr> 
  <tr> 
   <td> modo<br /> </td> 
   <td> Herramienta que se utilizará en la conversión. Los valores posibles son: phantomjs, wkhtmltopdf, other, disabled<br /> </td> 
   <td> Cadena<br /> </td> 
   <td> 'phantomjs' <br /> </td> 
  </tr> 
  <tr> 
   <td> tiempo de espera <br /> </td> 
   <td> Tiempo de espera para una conversión: tiempo máximo de conversión en segundos. Más allá de este umbral, el proceso de conversión se detiene y se genera un error.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 120<br /> </td> 
  </tr> 
  <tr> 
   <td> detallado<br /> </td> 
   <td> Modo detallado: inicie el modo detallado para diagnosticar posibles errores.<br /> </td> 
   <td> Booleano<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> waitTime<br /> </td> 
   <td> Delay when wait for a process: retraso en segundos, cuando se utilizan todos los procesos al mismo tiempo y en espera de que se libere un proceso. Si se supera este retraso, la conversión se detiene y se genera un error. <br /> </td> 
   <td> Long<br /> </td> 
   <td> 15<br /> </td> 
  </tr> 
 </tbody> 
</table>

Ejemplo de phantomjs:

```
phantomjs - -ignore-ssl-errors=true '$(XTK_INSTALL_DIR)/bin/htmlToPdf.js' '-out:{outPdf}' '-post:{postFile}' '-url:{originUrl}' -sessiontoken:{sessiontoken} -format:{format} -orientation:{orientation} -marginTop:{marginTop} -marginLeft:{marginLeft} -marginRight:{marginRight} -marginBottom:{marginBottom}
```

## ims {#ims}

Estos son los diferentes parámetros del nodo **ims**. Esta es la configuración para que Campaign se conecte a otro servicio mediante [IMS](../../integrations/using/about-adobe-id.md).

<table> 
 <thead> 
  <tr> 
   <th> Parámetro </th> 
   <th> Descripción </th> 
   <th> Tipo </th> 
   <th> Valor predeterminado </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> authIMSClientId<br /> </td> 
   <td> ID de cliente <br /> </td> 
   <td> Cadena<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> authIMSClientSecret<br /> </td> 
   <td> Clave secreta (cifrada en AES)<br /> </td> 
   <td> Cadena<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> authIMSCode<br /> </td> 
   <td> Código de autorización (cifrado en AES)<br /> </td> 
   <td> Cadena<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> authIMSEndpoint<br /> </td> 
   <td> URL del servidor IMS <br /> </td> 
   <td> Cadena<br /> </td> 
   <td> 'https://ims-na1.adobelogin.com'<br /> </td> 
  </tr> 
  <tr> 
   <td> authIMSTAClientId<br /> </td> 
   <td> Id. de cliente de cuenta técnica <br /> </td> 
   <td> Cadena<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> authIMSTAClientSecret<br /> </td> 
   <td> Clave técnica de secreto de cuenta (cifrada en AES)<br /> </td> 
   <td> Cadena<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> authIMSTAId<br /> </td> 
   <td> Id. de cuenta técnica <br /> </td> 
   <td> Cadena<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> authIMSTAPrivateKey<br /> </td> 
   <td> Clave privada de cuenta técnica (cifrada en AES)<br /> </td> 
   <td> Cadena<br /> </td> 
   <td> <br /> </td> 
  </tr> 
 </tbody> 
</table>

## JavaScript {#javascript}

Estos son los diferentes parámetros del nodo **javaScript**. Esta es la configuración del intérprete de JavaScript.

Para obtener más información, consulte [Documentación de informes](../../reporting/using/actions-on-reports.md#memory-allocation).

<table> 
 <thead> 
  <tr> 
   <th> Parámetro </th> 
   <th> Descripción </th> 
   <th> Tipo </th> 
   <th> Valor predeterminado </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> maxMB<br /> </td> 
   <td> Tamaño máximo en megabytes antes de ejecutar el recolector de elementos no utilizados.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 512 <br /> </td> 
  </tr> 
  <tr> 
   <td> stackSizeKB<br /> </td> 
   <td> Tamaño de cada fragmento de pila en kilo octetos. Este es un parámetro de ajuste de administración de memoria que la mayoría de los usuarios no deben ajustar. <br /> </td> 
   <td> Long<br /> </td> 
   <td> 8<br /> </td> 
  </tr> 
 </tbody> 
</table>

## mailExchanger {#mailexchanger}

Estos son los diferentes parámetros del nodo **mailExchanger**. Esta es la configuración del servidor SMTP.

<table> 
 <thead> 
  <tr> 
   <th> Parámetro </th> 
   <th> Descripción </th> 
   <th> Tipo </th> 
   <th> Valor predeterminado </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> mxAddress<br /> </td> 
   <td> Servidor SMTP: dirección IP del servidor SMTP para la transferencia de correos electrónicos.<br /> </td> 
   <td> Cadena<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> mxPort<br /> </td> 
   <td> Puerto TCP del servidor SMTP utilizado para la transferencia de correo electrónico.<br /> </td> 
   <td> Cadena<br /> </td> 
   <td> 25<br /> </td> 
  </tr> 
 </tbody> 
</table>

## módulo {#module}

Estos son los diferentes parámetros del nodo **module**. Esta es la configuración del módulo de restricciones de áreas de nombres xtk.

<table> 
 <thead> 
  <tr> 
   <th> Parámetro </th> 
   <th> Descripción </th> 
   <th> Tipo </th> 
   <th> Valor predeterminado </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> defaultNameSpace<br /> </td> 
   <td> Área de nombres predeterminada utilizada al crear una nueva entidad.<br /> </td> 
   <td> Cadena<br /> </td> 
   <td> 'cus'<br /> </td> 
  </tr> 
 </tbody> 
</table>

## control {#monitoring}

Estos son los diferentes parámetros del nodo **monitoring**. Esta es la configuración del servicio de monitorización.

<table> 
 <thead> 
  <tr> 
   <th> Parámetro </th> 
   <th> Descripción </th> 
   <th> Tipo </th> 
   <th> Valor predeterminado </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> maxPreparationJobsSec<br /> </td> 
   <td> Tiempo máximo de preparación: duración en segundos después de la cual una acción de envío ya no debe estar en preparación.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 3600<br /> </td> 
  </tr> 
  <tr> 
   <td> unixScript<br /> </td> 
   <td> Script Unix ejecutado por el servicio de supervisión.<br /> </td> 
   <td> Cadena<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> winScript<br /> </td> 
   <td> Script de Windows que ejecutará el servicio de supervisión.<br /> </td> 
   <td> Cadena<br /> </td> 
   <td> <br /> </td> 
  </tr> 
 </tbody> 
</table>

## ooconv {#ooconv}

Estos son los diferentes parámetros del nodo **ooconv**. Esta es la configuración del servidor de conversión de documentos.

<table> 
 <thead> 
  <tr> 
   <th> Parámetro </th> 
   <th> Descripción </th> 
   <th> Tipo </th> 
   <th> Valor predeterminado </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> maxConversions<br /> </td> 
   <td> Número máximo de conversiones permitidas por un servidor OpenOffice. Más allá de este número, se reinicia el servidor.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 1000<br /> </td> 
  </tr> 
  <tr> 
   <td> maxServerIdleSec<br /> </td> 
   <td> Tiempo máximo de inactivo del servidor OpenOffice antes del cierre forzado.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 7200<br /> </td> 
  </tr> 
  <tr> 
   <td> portRange<br /> </td> 
   <td> Intervalo de puertos en los que están escuchando los servidores OpenOffice.<br /> </td> 
   <td> Cadena<br /> </td> 
   <td> 8101-8110<br /> </td> 
  </tr> 
  <tr> 
   <td> url<br /> </td> 
   <td> URL del servidor de conversión de documentos.<br /> </td> 
   <td> Cadena<br /> </td> 
   <td> 'http://localhost:8080/nl/jsp/ooconv.jsp'<br /> </td> 
  </tr> 
 </tbody> 
</table>

## proxyConfig {#proxyconfig}

Estos son los diferentes parámetros del nodo **proxyConfig**. Esta es la configuración de los parámetros de proxy.

Para obtener más información, consulte [Configuración de conexión proxy](file-res-management.md).

<table> 
 <thead> 
  <tr> 
   <th> Parámetro </th> 
   <th> Descripción </th> 
   <th> Tipo </th> 
   <th> Valor predeterminado </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> habilitado<br /> </td> 
   <td> Usar un servidor proxy.<br /> </td> 
   <td> Booleano<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> omitir<br /> </td> 
   <td> Excepciones: lista de direcciones cuyos parámetros de proxy se omitirán.<br /> </td> 
   <td> Cadena<br /> </td> 
   <td> 'localhost*' <br /> </td> 
  </tr> 
  <tr> 
   <td> useSingleProxy<br /> </td> 
   <td> Servidor proxy único: use la misma configuración para todos los tipos de proxy.<br /> </td> 
   <td> Booleano<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
 </tbody> 
</table>

### Proxy HTTP/Proxy seguro {#http-proxy---secure-proxy-}

En el nodo **proxyConfig > Proxy HTTP / Proxy seguro**, configure los siguientes parámetros.

Para obtener más información, consulte [Configuración de conexión proxy](file-res-management.md).

<table> 
 <thead> 
  <tr> 
   <th> Parámetro </th> 
   <th> Descripción </th> 
   <th> Tipo </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> dirección<br /> </td> 
   <td> Dirección del servidor proxy <br /> </td> 
   <td> Cadena<br /> </td> 
  </tr> 
  <tr> 
   <td> iniciar sesión<br /> </td> 
   <td> Inicie sesión para la conexión con el servidor proxy <br /> </td> 
   <td> Cadena<br /> </td> 
  </tr> 
  <tr> 
   <td> contraseña<br /> </td> 
   <td> Contraseña para la conexión con el servidor proxy <br /> </td> 
   <td> Cadena<br /> </td> 
  </tr> 
  <tr> 
   <td> puerto <br /> </td> 
   <td> Puerto del servidor proxy <br /> </td> 
   <td> Corto<br /> </td> 
  </tr> 
 </tbody> 
</table>

## threadPool {#threadpool}

Estos son los diferentes parámetros del nodo **threadPool**.

<table> 
 <thead> 
  <tr> 
   <th> Parámetro </th> 
   <th> Descripción </th> 
   <th> Tipo </th> 
   <th> Valor predeterminado </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> maxThreadCount<br /> </td> 
   <td> Número máximo de hilos en el grupo. <br /> </td> 
   <td> Long<br /> </td> 
   <td> 10<br /> </td> 
  </tr> 
 </tbody> 
</table>

## urlPermission {#urlpermission}

Estos son los diferentes parámetros del nodo **urlPermission**. Esta es la lista de direcciones URL a las que puede acceder el código JavaScript.

Lista de dominios y expresiones regulares que especifican si el servidor de Adobe Campaign puede utilizar o no una URL encontrada en el código Javascript.

Si no se encuentra la dirección URL, se realiza la acción predeterminada según el modo predeterminado especificado.

Para obtener más información, consulte [Protección de conexión saliente](../../installation/using/configuring-campaign-server.md#url-permissions).

<table> 
 <thead> 
  <tr> 
   <th> Parámetro </th> 
   <th> Descripción </th> 
   <th> Tipo </th> 
   <th> Valor predeterminado </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> acción<br /> </td> 
   <td> Acción predeterminada si la dirección URL no está en la lista autorizada (enumeración). Los valores posibles son 'omitir' (autorizar sin mensaje de advertencia, esto requiere deshabilitar la protección), 'advertir' (autorizar y emitir un mensaje de advertencia) y 'denegar' (prohibir el acceso a la dirección URL).<br /> </td> 
   <td> Cadena<br /> </td> 
   <td> denegar <br /> </td> 
  </tr> 
  <tr> 
   <td> debugTrace<br /> </td> 
   <td> Seguimiento de depuración del mecanismo de selección de URL: emite mensajes adicionales durante el proceso de verificación de URL.<br /> </td> 
   <td> Booleano<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
 </tbody> 
</table>

## cusHeaders {#cusheaders}

Este nodo le permite agregar encabezados específicos en las solicitudes realizadas al cargar un archivo desde un servidor externo. Las redes de distribución de contenido (CDN) pueden solicitar un encabezado específico para confiar en el solicitante. Estos encabezados se pueden utilizar para mejorar la confianza en las solicitudes de Campaign, especialmente al descargar documentos personalizados para cada destinatario en el paso de ejecución de la entrega. Un número elevado de solicitudes de descarga de recursos se puede interpretar como un ataque DDos. dnsPattern le permite establecer nombres de encabezado y valores específicos para diferentes CDN en función de su nombre de dominio.

```
  <!-- List of custom headers added to request. 
         -->
    <cusHeaders>

    <!-- Pattern of DNS name or domain 
         value :  dnsPattern: All or part of the URL's domain to verify, * is a wild card Default:  -->
      <dnsPattern value="">

    <!-- Header Name and Value 
           headerName :  Header Name 
           headerValue :  Header Value -->
        <headerDef headerName="" headerValue=""/>

      </dnsPattern>

    </cusHeaders> 
```

### url {#url}

Para cada URL, agregue un nodo **url** con los parámetros siguientes:

Para obtener más información, consulte [Protección de conexión saliente](../../installation/using/configuring-campaign-server.md#url-permissions).

<table> 
 <thead> 
  <tr> 
   <th> Parámetro </th> 
   <th> Descripción </th> 
   <th> Tipo </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> dnsSuffix<br /> </td> 
   <td> Nombre de dominio o dominio principal al que afecta la dirección URL: todo o parte del dominio de la URL que se va a comprobar para acelerar la verificación. La dirección URL solo se verifica con respecto a la expresión regular si su dominio contiene dsnSuffix.<br /> </td> 
   <td> Cadena<br /> </td> 
  </tr> 
  <tr> 
   <td> urlRegEx<br /> </td> 
   <td> Expresión regular para perfeccionar la validación de direcciones URL que pertenecen a este dominio: expresión regular que la dirección URL debe comprobar si corresponde a dnsSuffix.<br /> </td> 
   <td> Cadena<br /> </td> 
  </tr> 
 </tbody> 
</table>

Si un registro cumple **dnsSuffix** pero no **urlRegEx**, se examina el siguiente registro.

Por ejemplo, para autorizar el acceso a todas las direcciones URL del dominio business.com, podemos definir dos registros:

dnsSuffix=&quot;business.com&quot; urlRegEx=&quot;http://.&#42;&quot;

y

dnsSuffix=&quot;business.com&quot; urlRegEx=&quot;https://.&#42;&quot;

Esta es la configuración predeterminada:

```
<url dnsSuffix="api.omniture.com" urlRegEx="https://api.omniture.com/genesis/i/3.1.*"   />
<url dnsSuffix="omniture.com" urlRegEx="https://api[1-5].omniture.com/genesis/i/3.1.*"  />
<url dnsSuffix="marketing.adobe.com"                     urlRegEx="https://.*"                                    />
<url dnsSuffix="fcm.googleapis.com"                      urlRegEx="https://fcm.googleapis.com/fcm/send.*"       />
<url dnsSuffix="graph.facebook.com"                      urlRegEx="https://.*"                                    />
<url dnsSuffix="api.line.me"                             urlRegEx="https://api.line.me/.*"                      />
<url dnsSuffix="api.twitter.com"                         urlRegEx="https://api.twitter.com/1.1.*"              />
<url dnsSuffix="adobeid-na1.services.adobe.com"          urlRegEx="https://.*"                                    />
<url dnsSuffix="adobeid-na1-stg1.services.adobe.com"     urlRegEx="https://.*"                                    />
<url dnsSuffix="localhost"                               urlRegEx="http://localhost:8080/nms/jsp/.*"              />
<url dnsSuffix="localhost"                               urlRegEx="http://localhost:8080/nl/jsp/.*"               />
<url dnsSuffix="localhost"                               urlRegEx="http://localhost:8080/xtk/jsp/.*"              />
```

## xtkJobs {#xtkjobs}

Estos son los diferentes parámetros del nodo **xtkJobs**. Esta es la configuración de los trabajos del servidor.

<table> 
 <thead> 
  <tr> 
   <th> Parámetro </th> 
   <th> Descripción </th> 
   <th> Tipo </th> 
   <th> Valor predeterminado </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> purgeLogsPeriod<br /> </td> 
   <td> Período de actualización del estado de la memoria del procesamiento del servidor (en ms).<br /> </td> 
   <td> Long<br /> </td> 
   <td> 500<br /> </td> 
  </tr> 
 </tbody> 
</table>

## archivo {#archiving}

Estos son los diferentes parámetros del nodo **archiving**. Esta es la configuración de las operaciones de archivado ejecutadas en segundo plano.

Para obtener más información, consulte [Activación del archivado de correo electrónico (local)](../../installation/using/email-archiving.md#activating-email-archiving--on-premise-).

<table> 
 <thead> 
  <tr> 
   <th> Parámetro </th> 
   <th> Descripción </th> 
   <th> Tipo </th> 
   <th> Valor predeterminado </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> acquisitionLimit<br /> </td> 
   <td> Número de EML para procesar al mismo tiempo<br /> </td> 
   <td> Long<br /> </td> 
   <td> 100<br /> </td> 
  </tr> 
  <tr> 
   <td> archivingType<br /> </td> 
   <td> Estrategia de archivado de mensajes enviados (enumeración). Los valores posibles son '0' (sin archivado) y '1' (transfiere el archivado de los mensajes enviados a un servidor SMTP).<br /> </td> 
   <td> Byte<br /> </td> 
   <td> 0<br /> </td> 
  </tr> 
  <tr> 
   <td> args<br /> </td> 
   <td> Parámetros de inicio<br /> </td> 
   <td> Cadena<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> autoStart<br /> </td> 
   <td> Inicio automático<br /> </td> 
   <td> Booleano<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> compressBatchSize<br /> </td> 
   <td> Tamaño de un archivo comprimido: número máximo de archivos en un archivo comprimido.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 10000<br /> </td> 
  </tr> 
  <tr> 
   <td> compressionFormat<br /> </td> 
   <td> Formato de compresión utilizado durante el archivado (enumeración). Los valores posibles son '0' (sin compresión) y '1' (comprimir los mensajes enviados con formato zip).<br /> </td> 
   <td> Byte<br /> </td> 
   <td> 1<br /> </td> 
  </tr> 
  <tr> 
   <td> expirationDelay<br /> </td> 
   <td> Retraso antes del archivado automático de correos electrónicos no procesados: número de días antes de que se archiven los correos electrónicos no procesados.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 2<br /> </td> 
  </tr> 
  <tr> 
   <td> initScript<br /> </td> 
   <td> Id. de JavaScript que se ejecutará al iniciar el proceso.<br /> </td> 
   <td> Cadena<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessMemoryAlertMb<br /> </td> 
   <td> Alerta de consumo de memoria: alerta relativa a la cantidad de RAM consumida (en MB) por un proceso determinado.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 1800<br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessMemoryWarningMb<br /> </td> 
   <td> Advertencia de consumo de memoria: advertencia sobre la cantidad de RAM consumida (en MB) por un proceso determinado.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 1600<br /> </td> 
  </tr> 
  <tr> 
   <td> pollDelay<br /> </td> 
   <td> Retraso (en segundos) entre cada evento de actualización.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 60<br /> </td> 
  </tr> 
  <tr> 
   <td> processRestartTime<br /> </td> 
   <td> Hora del día en que se reinicia automáticamente el proceso. Consulte <a href="../../installation/using/configuring-campaign-server.md#automatic-process-restart" target="_blank">Reinicio automático del proceso</a>.<br /> </td> 
   <td> Cadena<br /> </td> 
   <td> '06:00:00' <br /> </td> 
  </tr> 
  <tr> 
   <td> purgeArchivesDelay<br /> </td> 
   <td> Número de días antes de que se eliminen los correos electrónicos no procesados.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 7<br /> </td> 
  </tr> 
  <tr> 
   <td> runLevel<br /> </td> 
   <td> Prioridad al inicio. Los módulos de prioridad baja se inician primero y se detienen por última vez. Por lo tanto, el módulo syslogd debe tener la prioridad 0.<br /> </td> 
   <td> Corto<br /> </td> 
   <td> 10<br /> </td> 
  </tr> 
  <tr> 
   <td> smtpBccAddress<br /> </td> 
   <td> Archivando destino de destino<br /> </td> 
   <td> Cadena<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> smtpEnableTLS<br /> </td> 
   <td> Activar compatibilidad con SMTPS: activa el envío de correos electrónicos en modo seguro (STARTTLS/SMTPS) cuando el servidor remoto lo admite.<br /> </td> 
   <td> Booleano<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> smtpNbConnection<br /> </td> 
   <td> Número de conexiones al servidor SMTP de archivado.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 1<br /> </td> 
  </tr> 
  <tr> 
   <td> smtpRelayAddress<br /> </td> 
   <td> Lista separada por comas de nombres DNS o direcciones IP de retransmisiones SMTP que se van a utilizar. <br /> </td> 
   <td> Cadena<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> smtpRelayPort<br /> </td> 
   <td> Puerto IP del servidor SMTP.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 25<br /> </td> 
  </tr> 
 </tbody> 
</table>

## inMail {#inmail}

Estos son los diferentes parámetros del nodo **inMail**. Esta es la configuración del módulo de administración de correo electrónico entrante.

<table> 
 <thead> 
  <tr> 
   <th> Parámetro </th> 
   <th> Descripción </th> 
   <th> Tipo </th> 
   <th> Valor predeterminado </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> args<br /> </td> 
   <td> Parámetros de inicio<br /> </td> 
   <td> Cadena<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> autoStart<br /> </td> 
   <td> Inicio automático<br /> </td> 
   <td> Booleano<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> checkInstanceName<br /> </td> 
   <td> Verify instance name: si es true, el nombre de la instancia de Adobe Campaign contenido en los encabezados Message-ID debe ser el mismo que la instancia actual. <br /> </td> 
   <td> Booleano<br /> </td> 
   <td> true<br /> </td> 
  </tr> 
  <tr> 
   <td> defaultForwardAddress<br /> </td> 
   <td> Dirección de reenvío: dirección de transferencia de correo electrónico predeterminada no procesada por una regla. <br /> </td> 
   <td> Cadena<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> errorForwardAddress<br /> </td> 
   <td> Dirección para errores: dirección predeterminada utilizada para transferir correos electrónicos no válidos (codificación MIME incorrecta). <br /> </td> 
   <td> Cadena<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> ignoreSize<br /> </td> 
   <td> Ignore message size: se utiliza para ignorar el tamaño de un mensaje devuelto por los servidores POP3. En este caso, el módulo espera un '.' al final de los mensajes. <br /> </td> 
   <td> Booleano<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> inMailPeriodSec<br /> </td> 
   <td> Período de lectura del mensaje: frecuencia de sondeo de la cola de mensajes.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 5<br /> </td> 
  </tr> 
  <tr> 
   <td> initScript<br /> </td> 
   <td> Id. de JavaScript que se ejecutará al iniciar el proceso.<br /> </td> 
   <td> Cadena<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> maxBroadLog<br /> </td> 
   <td> Número máximo de registros que actualizar: define el número máximo de mensajes de registro que se deben mantener en memoria antes de actualizar la base de datos.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 20<br /> </td> 
  </tr> 
  <tr> 
   <td> maxMsgPerSession<br /> </td> 
   <td> Número máximo de mensajes para leer durante la sesión POP3.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 200<br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessMemoryAlertMb<br /> </td> 
   <td> Alerta de consumo de memoria: alerta relativa a la cantidad de RAM consumida (en MB) por un proceso determinado.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 1800<br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessMemoryWarningMb<br /> </td> 
   <td> Advertencia de consumo de memoria: advertencia sobre la cantidad de RAM consumida (en MB) por un proceso determinado.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 1600<br /> </td> 
  </tr> 
  <tr> 
   <td> maxSessionTTLSec<br /> </td> 
   <td> Duración de la sesión: duración máxima de la sesión de procesamiento de mensajes.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 100<br /> </td> 
  </tr> 
  <tr> 
   <td> popMailPeriodSec<br /> </td> 
   <td> Período de sondeo POP3<br /> </td> 
   <td> Long<br /> </td> 
   <td> 300<br /> </td> 
  </tr> 
  <tr> 
   <td> popQueueSize<br /> </td> 
   <td> Tamaño de cola de los mensajes leídos<br /> </td> 
   <td> Long<br /> </td> 
   <td> 100<br /> </td> 
  </tr> 
  <tr> 
   <td> popTimeoutSec<br /> </td> 
   <td> Tiempo de espera de comunicación con el servidor POP3. <br /> </td> 
   <td> Long<br /> </td> 
   <td> 300<br /> </td> 
  </tr> 
  <tr> 
   <td> processRestartTime<br /> </td> 
   <td> Hora del día en que se reinicia automáticamente el proceso. Consulte <a href="../../installation/using/configuring-campaign-server.md#automatic-process-restart" target="_blank">Reinicio automático del proceso</a>.<br /> </td> 
   <td> Cadena<br /> </td> 
   <td> '06:00:00' <br /> </td> 
  </tr> 
  <tr> 
   <td> reloadPeriodSec<br /> </td> 
   <td> Frecuencia de recarga de la base de datos de las cuentas que se van a sondear.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 600<br /> </td> 
  </tr> 
  <tr> 
   <td> runLevel<br /> </td> 
   <td> Prioridad al inicio. Los módulos de prioridad baja se inician primero y se detienen por última vez. Por lo tanto, el módulo syslogd debe tener la prioridad 0.<br /> </td> 
   <td> Corto<br /> </td> 
   <td> 10<br /> </td> 
  </tr> 
 </tbody> 
</table>

### msgDump {#msgdump}

En el nodo **inMail > msgDump**, configure los siguientes parámetros. Esta es la configuración del volcado de mensajes procesados.

<table> 
 <thead> 
  <tr> 
   <th> Parámetro </th> 
   <th> Descripción </th> 
   <th> Tipo </th> 
   <th> Valor predeterminado </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> volcar<br /> </td> 
   <td> Guardar todos los mensajes entrantes en formato de texto. <br /> </td> 
   <td> Booleano<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> msgPath<br /> </td> 
   <td> Ruta de volcado del mensaje.<br /> </td> 
   <td> Cadena<br /> </td> 
   <td> '/tmp/inMail'<br /> </td> 
  </tr> 
 </tbody> 
</table>

## interactiond {#interactiond}

Estos son los diferentes parámetros del nodo **interactiond**. Esta es la configuración del demonio de escritura para eventos de interacción entrantes.

Para obtener más información, consulte [Interacción: búfer de datos](../../installation/using/interaction-data-buffer.md).

<table> 
 <thead> 
  <tr> 
   <th> Parámetro </th> 
   <th> Descripción </th> 
   <th> Tipo </th> 
   <th> Valor predeterminado </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> args<br /> </td> 
   <td> Parámetros de inicio<br /> </td> 
   <td> Cadena<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> autoStart<br /> </td> 
   <td> Inicio automático<br /> </td> 
   <td> Booleano<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> callDataSize<br /> </td> 
   <td> Máx. número de caracteres almacenados en la memoria compartida para los datos de llamada.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 0<br /> </td> 
  </tr> 
  <tr> 
   <td> initScript<br /> </td> 
   <td> Id. de JavaScript que se ejecutará al iniciar el proceso <br /> </td> 
   <td> Cadena<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessMemoryAlertMb<br /> </td> 
   <td> Alerta de consumo de memoria: alerta relativa a la cantidad de RAM consumida (en MB) por un proceso determinado.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 1800<br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessMemoryWarningMb<br /> </td> 
   <td> Advertencia de consumo de memoria: advertencia sobre la cantidad de RAM consumida (en MB) por un proceso determinado.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 1600<br /> </td> 
  </tr> 
  <tr> 
   <td> maxSharedEntries<br /> </td> 
   <td> Máx. número de eventos almacenados en la memoria compartida.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 25000<br /> </td> 
  </tr> 
  <tr> 
   <td> nextOffersSize<br /> </td> 
   <td> Número máximo de ofertas elegibles clasificadas inmediatamente después de las propuestas, que se almacenarán para las estadísticas.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 0<br /> </td> 
  </tr> 
  <tr> 
   <td> processRestartTime<br /> </td> 
   <td> Hora del día en que se reinicia automáticamente el proceso. Consulte <a href="../../installation/using/configuring-campaign-server.md#automatic-process-restart" target="_blank">Reinicio automático del proceso</a>.<br /> </td> 
   <td> Cadena<br /> </td> 
   <td> '06:00:00' <br /> </td> 
  </tr> 
  <tr> 
   <td> runLevel<br /> </td> 
   <td> Prioridad al inicio. Los módulos de prioridad baja se inician primero y se detienen por última vez. Por lo tanto, el módulo syslogd debe tener la prioridad 0.<br /> </td> 
   <td> Corto<br /> </td> 
   <td> 10<br /> </td> 
  </tr> 
  <tr> 
   <td> statsPeriod<br /> </td> 
   <td> Duración de agregación en segundos para las estadísticas de tiempo de respuesta. 0 significa que se desactivó el almacenamiento estadístico.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 600<br /> </td> 
  </tr> 
  <tr> 
   <td> targetKeySize<br /> </td> 
   <td> Máx. número de caracteres almacenados en la memoria compartida para identificar a los individuos.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 16<br /> </td> 
  </tr> 
 </tbody> 
</table>

## mta. {#mta}

Estos son los diferentes parámetros del nodo **mta**. Esta es la configuración de los agentes de envío.

<table> 
 <thead> 
  <tr> 
   <th> Parámetro </th> 
   <th> Descripción </th> 
   <th> Tipo </th> 
   <th> Valor predeterminado </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> args<br /> </td> 
   <td> Parámetros de inicio<br /> </td> 
   <td> Cadena<br /> </td> 
   <td> '-tracefilter:nlmta' <br /> </td> 
  </tr> 
  <tr> 
   <td> autoStart<br /> </td> 
   <td> Inicio automático<br /> </td> 
   <td> Booleano<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> dataLogPath<br /> </td> 
   <td> Guardar ruta de los correos electrónicos enviados: si no está vacía, la ruta en la que se guardarán todos los archivos de origen de los correos electrónicos enviados. <br /> </td> 
   <td> Cadena<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> debugPath<br /> </td> 
   <td> Directorio de volcado: si no está vacío, copie los sobres MIME de los mensajes de correo enviados en este directorio. Se usa para solucionar problemas. <br /> </td> 
   <td> Cadena<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> dnsRequestLogDelayMs<br /> </td> 
   <td> Retraso de registros de consulta DNS: tiempo en milisegundos para mostrar los registros.<br /> </td> 
   <td> Long<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> errorPeriodSec<br /> </td> 
   <td> Error statistics frequency: tiempo entre la generación de estadísticas y el almacenamiento en la base de datos. <br /> </td> 
   <td> Long<br /> </td> 
   <td> 300<br /> </td> 
  </tr> 
  <tr> 
   <td> initScript<br /> </td> 
   <td> Id. de JavaScript que se ejecutará al iniciar el proceso.<br /> </td> 
   <td> Cadena<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> logEmailErrors<br /> </td> 
   <td> Generar estadísticas de errores y almacenarlas en la base de datos.<br /> </td> 
   <td> Booleano<br /> </td> 
   <td> true<br /> </td> 
  </tr> 
  <tr> 
   <td> logLevel<br /> </td> 
   <td> Mostrar nivel de mensajes de registro. Nivel de gravedad de los registros escritos en la base de datos. Los mensajes de registro generados por el MTA no siempre se escriben en la base de datos. Con este parámetro, puede definir el nivel desde el que considera que se debe escribir un mensaje en la base de datos. Si define el nivel 2, también se escriben los mensajes de los niveles 1 y 0, mientras que si define el nivel 1, sólo se escriben los mensajes de los niveles 1 y 0. Los valores posibles son: 0 (errores), 1 (advertencia), 2 (información)<br /> </td> 
   <td> Long<br /> </td> 
   <td> 2<br /> </td> 
  </tr> 
  <tr> 
   <td> maxMemoryMb<br /> </td> 
   <td> Tamaño máximo de memoria (en MB) que puede utilizar un proceso mta. Por encima de este límite, el proceso se reinicia para que la memoria que utiliza se libere al sistema.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 1024<br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessMemoryAlertMb<br /> </td> 
   <td> Alerta de consumo de memoria: alerta relativa a la cantidad de RAM consumida (en MB) por un proceso determinado.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 1800<br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessMemoryWarningMb<br /> </td> 
   <td> Advertencia de consumo de memoria: advertencia sobre la cantidad de RAM consumida (en MB) por un proceso determinado.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 1600<br /> </td> 
  </tr> 
  <tr> 
   <td> minConnectionsToLog<br /> </td> 
   <td> Umbral de conexión a tener en cuenta. No se generan estadísticas de error para una ruta determinada si el número total de conexiones para el período especificado por errorPeriodSec es estrictamente inferior al umbral.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 100<br /> </td> 
  </tr> 
  <tr> 
   <td> minErrorsToLog<br /> </td> 
   <td> Umbral de error a tener en cuenta: no se generan estadísticas de error para una ruta determinada si el número total de errores para el período especificado por errorPeriodSec es estrictamente inferior al umbral.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 1<br /> </td> 
  </tr> 
  <tr> 
   <td> minMessagesToLog<br /> </td> 
   <td> Umbral de mensaje a tener en cuenta. No se generan estadísticas de error para una ruta determinada si el número total de mensajes enviados para el período especificado por errorPeriodSec es estrictamente inferior al umbral.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 1000<br /> </td> 
  </tr> 
  <tr> 
   <td> notifRelay<br /> </td> 
   <td> Transmisión de notificación: HostName:Puerto utilizado para transmitir notificaciones.<br /> </td> 
   <td> Cadena<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> processRestartTime<br /> </td> 
   <td> Hora del día en que se reinicia automáticamente el proceso. Consulte <a href="../../installation/using/configuring-campaign-server.md#automatic-process-restart" target="_blank">Reinicio automático del proceso</a>.<br /> </td> 
   <td> Cadena<br /> </td> 
   <td> '06:00:00' <br /> </td> 
  </tr> 
  <tr> 
   <td> purgeDataLogDelay<br /> </td> 
   <td> Retraso antes de eliminar los correos electrónicos archivados: número de días antes de purgar los correos electrónicos archivados en el directorio especificado en dataLogPath.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 15<br /> </td> 
  </tr> 
  <tr> 
   <td> retryLostMessages<br /> </td> 
   <td> Reintentar mensajes perdidos: se volverán a intentar partes de los envíos si el proceso secundario está inactivo.<br /> </td> 
   <td> Booleano<br /> </td> 
   <td> true<br /> </td> 
  </tr> 
  <tr> 
   <td> runLevel<br /> </td> 
   <td> Prioridad al inicio. Los módulos de prioridad baja se inician primero y se detienen por última vez. Por lo tanto, el módulo syslogd debe tener la prioridad 0.<br /> </td> 
   <td> Corto<br /> </td> 
   <td> 10<br /> </td> 
  </tr> 
  <tr> 
   <td> signEmailLinks<br /> </td> 
   <td> Habilitar el mecanismo de firma. Esto mejora la seguridad en el seguimiento de vínculos en el correo electrónico.<br /> </td> 
   <td> Booleano<br /> </td> 
   <td> true<br /> </td> 
  </tr>
  <tr> 
   <td> statServerAddress<br /> </td> 
   <td> Dirección del servidor de estadísticas de envío, dada como 
    &lt;dns o ip&gt; 
      <code>&lbrack;</code>: 
     &lt;port&gt; 
       <code>&rbrack;</code>. Consulte 
      <a href="../../installation/using/email-deliverability.md#coordinates-of-the-statistics-server" target="_blank">Coordenadas del servidor de estadísticas</a>. 
      <br /> 
     </td> 
   <td> Cadena<br /> </td> 
   <td> Si no se define, el puerto predeterminado es 7777.<br /> </td> 
  </tr> 
  <tr> 
   <td> statServerTLSSupport<br /> </td> 
   <td> Habilitar TLS por dominio: habilita TLS configurable por MX (requiere un servidor de estadísticas actualizado).<br /> </td> 
   <td> Booleano<br /> </td> 
   <td> true <br /> </td> 
  </tr> 
  <!--tr> 
   <td> statServerVersion<br /> </td> 
   <td> Protocol version used: communication protocol version (1 for a v5.11 and 6.0.2 server, 2 for a v6.1 server).<br /> </td> 
   <td> String<br /> </td> 
   <td> If undefined, the latest version is used. <br /> </td> 
  </tr--> 
  <tr> 
   <td> useMomentum<br /> </td> 
   <td> Si se establece como "true", la instancia está usando el <a href="../../delivery/using/sending-with-enhanced-mta.md" target="_blank">MTA mejorado</a>.<br /> </td> 
   <td> Booleano<br /> </td> 
   <td> <br /> </td>b 
  </tr>
  <tr> 
   <td> verifyMode<br /> </td> 
   <td> Modo de comprobación: activa el modo de comprobación (sin transmisión física de mensajes; se usa para simulación y pruebas).<br /> </td> 
   <td> Booleano<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> workingPath<br /> </td> 
   <td> Directorio de trabajo: ubicación de los archivos temporales utilizados por el MTA para comunicarse con sus procesos secundarios.<br /> </td> 
   <td> Cadena<br /> </td> 
   <td> '$(XTK_INSTALL_DIR)/var/$(INSTANCE_NAME)/mta/' <br /> </td> 
  </tr> 
  <tr> 
   <td> xMailer<br /> </td> 
   <td> Campo X-Mailer: valor del campo "X-Mailer" en el encabezado de correo SMTP.<br /> </td> 
   <td> Cadena<br /> </td> 
   <td> 'nlserver, Build $(PRODUCT_VERSION)'<br /> </td> 
  </tr>  
 </tbody> 
</table>

### escondrijo {#cache}

En el nodo **cache**, configure los siguientes parámetros. Esta es la configuración de la caché del archivo local.

<table> 
 <thead> 
  <tr> 
   <th> Parámetro </th> 
   <th> Descripción </th> 
   <th> Tipo </th> 
   <th> Valor predeterminado </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> maxPeriodSec<br /> </td> 
   <td> Reciclado después de: período, expresado en segundos, tras el cual el archivo se elimina automáticamente de la caché para reclamar almacenamiento.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 244800<br /> </td> 
  </tr> 
  <tr> 
   <td> maxSizeOnDiskMb<br /> </td> 
   <td> Tamaño máximo de caché (Mb).<br /> </td> 
   <td> Long<br /> </td> 
   <td> 1024<br /> </td> 
  </tr> 
  <tr> 
   <td> purgePeriodSec<br /> </td> 
   <td> Frecuencia de purga: período en segundos entre ejecuciones del mecanismo de purga de caché.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 3600<br /> </td> 
  </tr> 
 </tbody> 
</table>

### relevo {#relay}

En el nodo **mta > relay**, configure los siguientes parámetros. Esta es la configuración del servidor de correo para la entrega de mensajes.

La lista se gestionará de la misma manera que una lista de MX devuelta por una consulta DNS MX, normalmente el primer MX se utiliza siempre que esté disponible, luego el siguiente, y así sucesivamente.

Para obtener más información, consulte [Retransmisión SMTP](../../installation/using/configuring-campaign-server.md#smtp-relay).

<table> 
 <thead> 
  <tr> 
   <th> Parámetro </th> 
   <th> Descripción </th> 
   <th> Tipo </th> 
   <th> Valor predeterminado </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> dirección<br /> </td> 
   <td> Lista separada por comas de nombres DNS o direcciones IP de retransmisiones SMTP que se van a utilizar. <br /> </td> 
   <td> Cadena<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> puerto <br /> </td> 
   <td> Puerto IP del servidor SMTP.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 25<br /> </td> 
  </tr> 
 </tbody> 
</table>

### principal {#master}

En el nodo **mta > master**, configure los siguientes parámetros. Esta es la configuración del servidor principal.

Para obtener más información, consulte esta [sección](../../installation/using/configuring-campaign-server.md#mta-child-processes).

<table> 
 <thead> 
  <tr> 
   <th> Parámetro </th> 
   <th> Descripción </th> 
   <th> Tipo </th> 
   <th> Valor predeterminado </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> dataBasePoolPeriodSec<br /> </td> 
   <td> Frecuencia de sondeo de base de datos de los trabajos que se van a enviar. Este valor indica la frecuencia de sondeo de la base de datos (en segundos). Para obtener la lista de trabajos en espera de envío, el MTA sondea la base de datos de forma regular. Cuando no hay ningún trabajo en espera, el período de sondeo se define con este valor. De lo contrario, si se ha transferido un trabajo a un servidor secundario, esta duración de sondeo se reduce automáticamente a un segundo para que se pueda volver a procesar un nuevo trabajo lo antes posible, es decir, tan pronto como un servidor secundario esté disponible de nuevo. Esto no significa que la consulta de la base de datos se realice cada segundo hasta que un servidor secundario vuelva a estar disponible. De hecho, el acceso a una base de datos sólo se realiza cuando hay al menos un servidor secundario disponible.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 30<br /> </td> 
  </tr> 
  <tr> 
   <td> dataBaseRetryDelaySec<br /> </td> 
   <td> Período de espera después de un error de conexión a base de datos. Un error de conexión a la base de datos suele deberse al propio servidor de la base de datos. El servidor también se puede detener por motivos de mantenimiento, por ejemplo. El parámetro DataBaseRetryDelay define la duración entre dos intentos de conexión en caso de un error de conexión a la base de datos.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 60<br /> </td> 
  </tr> 
  <tr> 
   <td> domainKeysReloadPeriodSec<br /> </td> 
   <td> Período de validez de la caché de claves privadas (DomainKeys). Las claves privadas utilizadas para firmar correos electrónicos siguiendo la recomendación de DomainKeys (http://antispam.yahoo.com/domainkeys) se almacenan como opciones en la base de datos. El parámetro domainKeysReloadPeriodSec define cuántos segundos puede mantener el MTA estas claves en una caché. Después de este retraso, todas las claves deben volver a cargarse desde la base de datos.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 600<br /> </td> 
  </tr> 
  <tr> 
   <td> maxSpareServers<br /> </td> 
   <td> Número máximo de servidores secundarios. Representa el número máximo de servidores en ejecución. Se recomienda limitar este número a un nivel óptimo compatible con los recursos de memoria del servidor. Esto se puede comprobar durante una entrega. La memoria utilizada no debe exceder un tercio de la memoria física disponible; de lo contrario, se utilizará el intercambio. Ver <a href="../../installation/using/configuring-campaign-server.md#mta-child-processes" target="_blank">procesos secundarios de MTA</a>.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 2<br /> </td> 
  </tr> 
  <tr> 
   <td> minSpareServers<br /> </td> 
   <td> Número mínimo de servidores secundarios. El MTA intenta mantener al menos este número de servidores en ejecución. Si hay menos, reinicia nuevos servidores cada segundo hasta que se alcance este valor.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 0<br /> </td> 
  </tr> 
  <tr> 
   <td> startSpareServers<br /> </td> 
   <td> Número de servidores secundarios en el inicio. El número de servidores secundarios se monitorea dinámicamente; cuando se inicia el MTA, crea tantos servidores secundarios como indique este valor. Normalmente, los servidores secundarios no se pueden iniciar más rápido que un servidor por segundo para ahorrar recursos de host. Sin embargo, cuando se inicia el MTA, se anula esta limitación para que los servidores secundarios estén disponibles lo antes posible.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 0<br /> </td> 
  </tr> 
 </tbody> 
</table>

### niño {#child}

En el nodo **mta > child**, configure los siguientes parámetros. Esta es la configuración de los servidores secundarios.

Para obtener más información, consulte [Optimización de envío de correo electrónico](../../installation/using/email-deliverability.md#email-sending-optimization).

<table> 
 <thead> 
  <tr> 
   <th> Parámetro </th> 
   <th> Descripción </th> 
   <th> Tipo </th> 
   <th> Valor predeterminado </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> extraArgs<br /> </td> 
   <td> Argumentos de línea de comandos opcionales <br /> </td> 
   <td> Cadena<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> inactiveChildTimeoutSec<br /> </td> 
   <td> Tiempo de espera hasta que se detengan los servidores secundarios inactivos. Si un servidor secundario tiene un tiempo de inactividad mayor que este parámetro, se eliminará automáticamente para liberar recursos del host.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 60<br /> </td> 
  </tr> 
  <tr> 
   <td> maxAgeSec<br /> </td> 
   <td> Tiempo máximo de retención de mensajes. Si no se pudo enviar un mensaje preparado debido al estrangulamiento o no se pudo conectar con el MTA de destino, el mensaje se abandona y se procesará en el siguiente reintento.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 600<br /> </td> 
  </tr> 
  <tr> 
   <td> maxGCMConnectPerChild<br /> </td> 
   <td> Máximo de solicitudes Http paralelas al FCM iniciadas por cada servidor secundario.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 8<br /> </td> 
  </tr> 
  <tr> 
   <td> maxMsgPerChild<br /> </td> 
   <td> Número máximo de mensajes por servidor secundario. Cada elemento secundario de MTA procesa este número de mensajes y muere. Es importante especificar un número tal que las pérdidas de memoria o recursos en el MTA sean inofensivas (normalmente unos pocos miles). Aunque no haya pérdidas de memoria conocidas en el código MTA, los motores JavaScript y XSL incrustados no son totalmente fiables.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 5000000<br /> </td> 
  </tr> 
  <tr> 
   <td> maxWaitingMessages<br /> </td> 
   <td> Pending messages: número máximo de mensajes que esperan en la memoria para enviarse. <br /> </td> 
   <td> Long<br /> </td> 
   <td> 2000<br /> </td> 
  </tr> 
  <tr> 
   <td> maxWorkingSetMb<br /> </td> 
   <td> Tamaño máximo de memoria (en MB) que puede utilizar un proceso secundario. Por encima de este límite, el proceso se detiene para que la memoria que utiliza se libere al sistema. <br /> </td> 
   <td> Long<br /> </td> 
   <td> 128<br /> </td> 
  </tr> 
  <tr> 
   <td> soapConnectorTimeoutSec<br /> </td> 
   <td> SOAP Tiempo de espera (en segundos) tras el cual se abandona la conexión de un conector de envío a un conector de envío.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 600<br /> </td> 
  </tr> 
  <tr> 
   <td> startWithFirstMX<br /> </td> 
   <td> Iniciar siempre con la prioridad MX más alta.<br /> </td> 
   <td> Booleano<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> timeToLive<br /> </td> 
   <td> Número máximo de intentos consecutivos cuando se reanuda.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 48<br /> </td> 
  </tr> 
 </tbody> 
</table>

En el nodo **mta > secundario > smtp**, configure los siguientes parámetros. Esta es la configuración de las sesiones SMTP.

<table> 
 <thead> 
  <tr> 
   <th> Parámetro </th> 
   <th> Descripción </th> 
   <th> Tipo </th> 
   <th> Valor predeterminado </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> enableTLS<br /> </td> 
   <td> Activa el envío de correos electrónicos en modo seguro (STARTTLS/SMTPS) cuando el servidor remoto lo admite.<br /> </td> 
   <td> Booleano<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> diskTimeoutSec<br /> </td> 
   <td> Tiempo de espera de sesión inactivo. Este parámetro solo se utiliza si la sesión se reutiliza para transmitir varios mensajes a un dominio determinado. Cuando el MTA ha completado la transmisión del mensaje, la sesión SMTP que ha utilizado no se cierra sistemáticamente. Si un mensaje está listo para enviarse para este mismo dominio, se reutilizará la misma sesión SMTP y por esta razón la sesión no se cierra automáticamente. El parámetro IdleSessionTimeout permite definir el tiempo durante el cual una sesión SMTP puede permanecer activa a la espera de otro mensaje. Una vez transcurrida la duración, la sesión se cierra automáticamente.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 5<br /> </td> 
  </tr> 
  <tr> 
   <td> initialDelaySec<br /> </td> 
   <td> Retraso inicial antes de reintentar la conexión. Este retraso se duplica cada vez que falla la conexión.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 4<br /> </td> 
  </tr> 
  <tr> 
   <td> maxSessionsPerChild<br /> </td> 
   <td> Número máximo de sesiones SMTP por servidor secundario. Para enviar un mensaje, el MTA inicializa una conexión SMTP con el MTA del destinatario. El número máximo de sesiones SMTP simultáneas y activas para un servidor secundario determinado está limitado por este valor. Si multiplica este valor por maxSpareServers, obtendrá el número máximo de mensajes que un servidor secundario determinado puede procesar simultáneamente.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 1000<br /> </td> 
  </tr> 
 </tbody> 
</table>

En el nodo **mta > secundario > smtp > IPAffinity**, configure los siguientes parámetros. Esta es la configuración de la administración de afinidades con direcciones IP para tráfico SMTP saliente optimizado.

Para obtener más información, consulte [Lista de direcciones IP que usar](../../installation/using/email-deliverability.md#list-of-ip-addresses-to-use) y [Administración del tráfico SMTP saliente con afinidades](../../installation/using/configuring-campaign-server.md#managing-outbound-smtp-traffic-with-affinities).

<table> 
 <thead> 
  <tr> 
   <th> Parámetro </th> 
   <th> Descripción </th> 
   <th> Tipo </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> localDomain<br /> </td> 
   <td> Domain name: nombre de dominio local vinculado a la dirección IP. Se usa al emitir un comando SMTP HELO.<br /> </td> 
   <td> Cadena<br /> </td> 
  </tr> 
  <tr> 
   <td> nombre<br /> </td> 
   <td> Logical name: nombres vinculados a la afinidad por los usuarios. Los nombres se separan con punto y coma;<br /> </td> 
   <td> Cadena<br /> </td> 
  </tr> 
 </tbody> 
</table>

En el nodo **mta > child > smtp > IP**, configure los siguientes parámetros.

Para obtener más información, consulte [Lista de direcciones IP que se utilizarán](../../installation/using/email-deliverability.md#list-of-ip-addresses-to-use).

<table> 
 <thead> 
  <tr> 
   <th> Parámetro </th> 
   <th> Descripción </th> 
   <th> Tipo </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> dirección<br /> </td> 
   <td> Dirección física asociada. Por ejemplo: '192.168.0.1'<br /> </td> 
   <td> Cadena<br /> </td> 
  </tr> 
  <tr> 
   <td> publicId<br /> </td> 
   <td> ID de dirección pública asociada. Se utiliza como clave para el servidor de estadísticas. Debe ser numérico. Ver esta <a href="../../installation/using/email-deliverability.md#managing-ip-addresses">sección</a>.<br /> </td> 
   <td> Long<br /> </td> 
  </tr> 
  <tr> 
   <td> peso<br /> </td> 
   <td> Especifica la frecuencia de uso de esta IP, en relación con otras IP (los pesos mayores conducen a frecuencias más altas).<br /> </td> 
   <td> Long<br /> </td> 
  </tr> 
  <tr> 
   <td> includeDomains<br /> </td> 
   <td> Lista separada por comas de las máscaras de dominio que se van a incluir.<br /> </td> 
   <td> Cadena<br /> </td> 
  </tr> 
  <tr> 
   <td> excludeDomains<br /> </td> 
   <td> Lista separada por comas de las máscaras de dominio que se van a excluir.<br /> </td> 
   <td> Cadena<br /> </td> 
  </tr> 
  <tr> 
   <td> heloHost<br /> </td> 
   <td> Nombre del equipo vinculado a la dirección IP. Se usa al emitir un comando SMTP HELO.<br /> </td> 
   <td> Cadena<br /> </td> 
  </tr> 
 </tbody> 
</table>

## nmac {#nmac}

Estos son los diferentes parámetros del nodo **nmac**. Esta es la configuración de para envíos de notificaciones push.

<table> 
 <thead> 
  <tr> 
   <th> Parámetro </th> 
   <th> Descripción </th> 
   <th> Tipo </th> 
   <th> Valor predeterminado </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> useHTTPProxy<br /> </td> 
   <td> Use el proxy HTTP definido en shared/proxyHTTP. <br /> </td> 
   <td> Booleano<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
 </tbody> 
</table>

### relevo {#relay-1}

Estos son los diferentes parámetros del nodo **nmac > relay**. Esto configura el uso de un relé para la entrega de mensajes (conector http2 de ios).

<table> 
 <thead> 
  <tr> 
   <th> Parámetro </th> 
   <th> Descripción </th> 
   <th> Tipo </th> 
   <th> Valor predeterminado </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> dirección<br /> </td> 
   <td> Dirección DNS o nombre del relé que se va a utilizar. <br /> </td> 
   <td> Cadena<br /> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> puerto <br /> </td> 
   <td> Puerto de retransmisión <br /> </td> 
   <td> Long<br /> </td> 
   <td> 443<br /> </td> 
  </tr> 
  <tr> 
   <td> trustedCertsChain<br /> </td> 
   <td> Cadena de certificados (archivo PEM). Útil cuando se usa un servidor ficticio.<br /> </td> 
   <td> Cadena<br /> </td> 
   <td> <br /> </td> 
  </tr> 
 </tbody> 
</table>

## canalizado {#pipelined}

Estos son los diferentes parámetros del nodo **pipelined**. Esta es la configuración del módulo de procesamiento de eventos para los servicios de canalización.

<table> 
 <thead> 
  <tr> 
   <th> Parámetro </th> 
   <th> Descripción </th> 
   <th> Tipo </th> 
   <th> Valor predeterminado </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> appName<br /> </td> 
   <td> Nombre de la aplicación generada en la conexión de desarrollador cuando se guarda la clave pública. <br /> </td> 
   <td> Cadena<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> args<br /> </td> 
   <td> Parámetros de inicio<br /> </td> 
   <td> Cadena<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> authGatewayEndpoint<br /> </td> 
   <td> URL para obtener un token de puerta de enlace.<br /> </td> 
   <td> Cadena<br /> </td> 
   <td> 'https://api.omniture.com' <br /> </td> 
  </tr> 
  <tr> 
   <td> authPrivateKey<br /> </td> 
   <td> Clave privada para obtener tokens (cifrados en AES con la opción XtkKey).<br /> </td> 
   <td> Cadena<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> autoStart<br /> </td> 
   <td> Inicio automático <br /> </td> 
   <td> Booleano<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> disableAuth<br /> </td> 
   <td> Deshabilitar autenticación: conéctese a los servicios de canalización sin autenticación. <br /> </td> 
   <td> Booleano<br /> </td> 
   <td> 2<br /> </td> 
  </tr> 
  <tr> 
   <td> discoverPipelineEndpoint<br /> </td> 
   <td> URL para detectar la URL de servicios de canalización.<br /> </td> 
   <td> Cadena<br /> </td> 
   <td> 'https://producer-pipeline-pnw.adobe.net'<br /> </td> 
  </tr> 
  <tr> 
   <td> dumpStatePeriodSec<br /> </td> 
   <td> Período de guardado de estado: frecuencia con la que se guarda la información interna del proceso en un archivo. Inactivo si es 0. <br /> </td> 
   <td> Long<br /> </td> 
   <td> 0<br /> </td> 
  </tr> 
  <tr> 
   <td> forcedPipelineEndpoint<br /> </td> 
   <td> URL de escucha: fuerza la URL de escucha de los servicios de canalización. <br /> </td> 
   <td> Cadena<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> initScript<br /> </td> 
   <td> Id. de JavaScript que se ejecutará al iniciar el proceso.<br /> </td> 
   <td> Cadena<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessMemoryAlertMb<br /> </td> 
   <td> Alerta de consumo de memoria: alerta relativa a la cantidad de RAM consumida (en MB) por un proceso determinado.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 1800<br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessMemoryWarningMb<br /> </td> 
   <td> Advertencia de consumo de memoria: advertencia sobre la cantidad de RAM consumida (en MB) por un proceso determinado.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 1600<br /> </td> 
  </tr> 
  <tr> 
   <td> monitorServerPort<br /> </td> 
   <td> Puerto del servidor de estado: Puerto del servidor HTTP que permite consultar el estado del proceso. Inactivo si 0.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 7781<br /> </td> 
  </tr> 
  <tr> 
   <td> pointerFlushMessageCount<br /> </td> 
   <td> El puntero se almacenará en la base de datos cada vez que se procese este número de mensajes.<br /> </td> 
   <td> <br /> </td> 
   <td> 1000<br /> </td> 
  </tr> 
  <tr> 
   <td> pointerFlushPeriodSec<br /> </td> 
   <td> Retraso antes de almacenar el puntero: el puntero se almacenará en la base de datos al menos una vez durante este período (útil en caso de baja actividad).<br /> </td> 
   <td> Long<br /> </td> 
   <td> 5<br /> </td> 
  </tr> 
  <tr> 
   <td> processRestartTime<br /> </td> 
   <td> Hora del día en que se reinicia automáticamente el proceso. Consulte <a href="../../installation/using/configuring-campaign-server.md#automatic-process-restart" target="_blank">Reinicio automático del proceso</a>.<br /> </td> 
   <td> Cadena<br /> </td> 
   <td> '06:00:00' <br /> </td> 
  </tr> 
  <tr> 
   <td> processingJSThreads<br /> </td> 
   <td> Número máximo de subprocesos para el procesamiento de eventos con un conector de JavaScript personalizado.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 4<br /> </td> 
  </tr> 
  <tr> 
   <td> processingThreads<br /> </td> 
   <td> Número máximo de subprocesos para el procesamiento de eventos.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 4<br /> </td> 
  </tr> 
  <tr> 
   <td> retryPeriodSec<br /> </td> 
   <td> Retraso entre procesamientos si se produce un error.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 30<br /> </td> 
  </tr> 
  <tr> 
   <td> retryValiditySec<br /> </td> 
   <td> Abandonar después de este período: abandone el evento si el procesamiento sigue fallando después de este período.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 300<br /> </td> 
  </tr> 
  <tr> 
   <td> runLevel<br /> </td> 
   <td> Prioridad al inicio. Los módulos de prioridad baja se inician primero y se detienen por última vez. Por lo tanto, el módulo syslogd debe tener la prioridad 0.<br /> </td> 
   <td> Corto<br /> </td> 
   <td> 10<br /> </td> 
  </tr> 
 </tbody> 
</table>

## reparar {#repair}

Estos son los diferentes parámetros del nodo **repair**. Esta es la configuración del módulo de reparación de la base de datos.

<table> 
 <thead> 
  <tr> 
   <th> Parámetro </th> 
   <th> Descripción </th> 
   <th> Tipo </th> 
   <th> Valor predeterminado </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> repairActionDelayMin<br /> </td> 
   <td> Delivery actions repair module: retraso (en minutos) tras el cual el módulo de reparación puede procesar las acciones de entrega. <br /> </td> 
   <td> Long<br /> </td> 
   <td> 60<br /> </td> 
  </tr> 
 </tbody> 
</table>

## securityZone {#securityzone}

Estos son los diferentes parámetros del nodo **securityZone**.

Para obtener más información, consulte [Definir zonas de seguridad](../../installation/using/security-zones.md).

<table> 
 <thead> 
  <tr> 
   <th> Parámetro </th> 
   <th> Descripción </th> 
   <th> Tipo </th> 
   <th> Valor predeterminado </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> allowDebug<br /> </td> 
   <td> Autorizar modo de depuración para aplicaciones web.<br /> </td> 
   <td> Booleano<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> allowEmptyPassword<br /> </td> 
   <td> Autoriza al usuario a utilizar la aplicación sin contraseña.<br /> </td> 
   <td> Booleano<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> allowHTTP<br /> </td> 
   <td> Autorizar el uso de HTTP para el inicio de sesión del operador.<br /> </td> 
   <td> Booleano<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> allowSQLInjection<br /> </td> 
   <td> Autorizar el uso de SQLDATA en expresiones.<br /> </td> 
   <td> Booleano<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> allowUserPassword<br /> </td> 
   <td> Autorizar tokens de sesión de usuario/contraseña.<br /> </td> 
   <td> Booleano<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> etiqueta <br /> </td> 
   <td> Etiqueta<br /> </td> 
   <td> Cadena<br /> </td> 
   <td> NewLabel()<br /> </td> 
  </tr> 
  <tr> 
   <td> nombre<br /> </td> 
   <td> Nombre interno<br /> </td> 
   <td> Cadena<br /> </td> 
   <td> NewName() <br /> </td> 
  </tr> 
  <tr> 
   <td> sessionTokenOnly<br /> </td> 
   <td> No use el token de seguridad.<br /> </td> 
   <td> Booleano<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> showErrors<br /> </td> 
   <td> Mostrar detalles del error<br /> </td> 
   <td> Booleano<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
 </tbody> 
</table>

Esta es la configuración predeterminada:

```
<securityZone allowDebug="false" allowHTTP="false" allowSQLInjection="false" label="Public Network" name="public">
  <subNetwork name="all" label="All addresses" mask="*" proxy="127.0.0.1, ::1"/>

  <securityZone allowDebug="true" allowHTTP="false" allowSQLInjection="false" label="Private Network (VPN)"
                name="vpn" showErrors="true">

    <securityZone allowDebug="true" allowEmptyPassword="false" allowHTTP="true" allowUserPassword="false"
                  allowSQLInjection="false" label="Private Network (LAN)" name="lan" sessionTokenOnly="true"
                  showErrors="true">
      <subNetwork name="lan1" label="Lan 1" mask="192.168.0.0/16" proxy="127.0.0.1, ::1"/>
      <subNetwork name="lan2" label="Lan 2" mask="172.16.0.0/12" proxy="127.0.0.1, ::1"/>
      <subNetwork name="lan3" label="Lan 3" mask="10.0.0.0/8" proxy="127.0.0.1, ::1"/>
      <subNetwork name="localhost" label="Localhost" mask="127.0.0.0/8" proxy="127.0.0.1, ::1"/>
      <subNetwork name="lan6"  label="Lan (IPv6)" mask="fc00::/7" proxy="127.0.0.1, ::1"/>
      <subNetwork name="lan6b" label="Lan (IPv6)" mask="fe80::/10" proxy="127.0.0.1, ::1"/>
      <subNetwork name="localhost6" label="Localhost (IPv6)" mask="::1/128" proxy="127.0.0.1, ::1"/>
    </securityZone>

  </securityZone>
</securityZone>
```

### subNetwork {#subnetwork}

Estos son los diferentes parámetros del nodo **securityZone > subNetwork**.

Para obtener más información, consulte [Definir zonas de seguridad](../../installation/using/security-zones.md).

<table> 
 <thead> 
  <tr> 
   <th> Parámetro </th> 
   <th> Descripción </th> 
   <th> Tipo </th> 
   <th> Valor predeterminado </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> etiqueta <br /> </td> 
   <td> Etiqueta<br /> </td> 
   <td> Cadena<br /> </td> 
   <td> NewLabel()<br /> </td> 
  </tr> 
  <tr> 
   <td> máscara<br /> </td> 
   <td> Máscara o dirección<br /> </td> 
   <td> Cadena<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> nombre<br /> </td> 
   <td> Nombre interno<br /> </td> 
   <td> Cadena<br /> </td> 
   <td> NewName() <br /> </td> 
  </tr> 
  <tr> 
   <td> proxy <br /> </td> 
   <td> Máscara o dirección del proxy (inverso) utilizado por esta subred para acceder a la instancia. En este caso, se probará el encabezado "X-Forwarded-For" en lugar de este proxy.<br /> </td> 
   <td> Cadena<br /> </td> 
   <td> 127.0.0.1 <br /> </td> 
  </tr> 
 </tbody> 
</table>

## sms {#sms}

Estos son los diferentes parámetros del nodo **sms**. Esta es la configuración del módulo de administración de SMS de entrada.

<table> 
 <thead> 
  <tr> 
   <th> Parámetro </th> 
   <th> Descripción </th> 
   <th> Tipo </th> 
   <th> Valor predeterminado </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> args<br /> </td> 
   <td> Parámetros de inicio<br /> </td> 
   <td> Cadena<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> autoStart<br /> </td> 
   <td> Inicio automático<br /> </td> 
   <td> Booleano<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> dataRetentionDays<br /> </td> 
   <td> Número máximo de archivos de trabajo de días conservados por el conector SMPP.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 60<br /> </td> 
  </tr> 
  <tr> 
   <td> dataSizeMo<br /> </td> 
   <td> Tamaño máximo en MB de los archivos de trabajo SMPP.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 512<br /> </td> 
  </tr> 
  <tr> 
   <td> initScript<br /> </td> 
   <td> Id. de JavaScript que se ejecutará al iniciar el proceso.<br /> </td> 
   <td> Cadena<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> keepAlivePeriod<br /> </td> 
   <td> Periodicidad del marco de continuidad de la sesión: máximo. período en segundos entre dos fotogramas para notificar que la sesión de recepción sigue habilitada.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 25<br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessMemoryAlertMb<br /> </td> 
   <td> Alerta de consumo de memoria: alerta relativa a la cantidad de RAM consumida (en MB) por un proceso determinado.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 1800<br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessMemoryWarningMb<br /> </td> 
   <td> Advertencia de consumo de memoria: advertencia sobre la cantidad de RAM consumida (en MB) por un proceso determinado.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 1600<br /> </td> 
  </tr> 
  <tr> 
   <td> pollPeriod<br /> </td> 
   <td> Frecuencia de búsqueda: período de encuesta de la cuenta SMS.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 300<br /> </td> 
  </tr> 
  <tr> 
   <td> processRestartTime<br /> </td> 
   <td> Hora del día en que se reinicia automáticamente el proceso. Consulte <a href="../../installation/using/configuring-campaign-server.md#automatic-process-restart" target="_blank">Reinicio automático del proceso</a>.<br /> </td> 
   <td> Cadena<br /> </td> 
   <td> '06:00:00' <br /> </td> 
  </tr> 
  <tr> 
   <td> reloadPeriod<br /> </td> 
   <td> Frecuencia de recarga de la cuenta: frecuencia de recarga de la base de datos de las cuentas que se van a sondear.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 600<br /> </td> 
  </tr> 
  <tr> 
   <td> runLevel<br /> </td> 
   <td> Prioridad al inicio. Los módulos de prioridad baja se inician primero y se detienen por última vez. Por lo tanto, el módulo syslogd debe tener la prioridad 0.<br /> </td> 
   <td> Corto<br /> </td> 
   <td> 10<br /> </td> 
  </tr> 
  <tr> 
   <td> srReadDelay<br /> </td> 
   <td> Número de segundos de retraso para el procesamiento de SR: solo los SR con una fecha de recuperación anterior a la hora actual menos la duración en segundos dada por srReadDelay. <br /> </td> 
   <td> Long<br /> </td> 
   <td> 600<br /> </td> 
  </tr> 
  <tr> 
   <td> tiempo de espera <br /> </td> 
   <td> Tiempo de espera de comunicación con pasarela SMS.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 300<br /> </td> 
  </tr> 
 </tbody> 
</table>

### netsize {#netsize}

Estos son los diferentes parámetros del nodo **sms > netsize**.

<table> 
 <thead> 
  <tr> 
   <th> Parámetro </th> 
   <th> Descripción </th> 
   <th> Tipo </th> 
   <th> Valor predeterminado </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> netsizeConnectionTimeout<br /> </td> 
   <td> Tiempo de espera en segundos al establecer una conexión con Netsize.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 30<br /> </td> 
  </tr> 
 </tbody> 
</table>

## estadísticas {#stat}

Estos son los diferentes parámetros del nodo **stat**. Esta es la configuración del módulo de estadísticas de MTA.

<table> 
 <thead> 
  <tr> 
   <th> Parámetro </th> 
   <th> Descripción </th> 
   <th> Tipo </th> 
   <th> Valor predeterminado </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> args<br /> </td> 
   <td> Parámetros de inicio<br /> </td> 
   <td> Cadena<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> autoStart<br /> </td> 
   <td> Inicio automático<br /> </td> 
   <td> Booleano<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> initScript<br /> </td> 
   <td> Id. de JavaScript que se ejecutará al iniciar el proceso.<br /> </td> 
   <td> Cadena<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessMemoryAlertMb<br /> </td> 
   <td> Alerta de consumo de memoria: alerta relativa a la cantidad de RAM consumida (en MB) por un proceso determinado.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 1800<br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessMemoryWarningMb<br /> </td> 
   <td> Advertencia de consumo de memoria: advertencia sobre la cantidad de RAM consumida (en MB) por un proceso determinado.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 1600<br /> </td> 
  </tr> 
  <tr> 
   <td> puerto <br /> </td> 
   <td> Puerto de escucha del servidor. Ver esta <a href="../../installation/using/email-deliverability.md#definition-of-the-server-port">sección</a>.<br /> </td> 
   <td> Corto<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> processRestartTime<br /> </td> 
   <td> Hora del día en que se reinicia automáticamente el proceso. Consulte <a href="../../installation/using/configuring-campaign-server.md#automatic-process-restart" target="_blank">Reinicio automático del proceso</a>.<br /> </td> 
   <td> Cadena<br /> </td> 
   <td> '06:00:00' <br /> </td> 
  </tr> 
  <tr> 
   <td> runLevel<br /> </td> 
   <td> Prioridad al inicio. Los módulos de prioridad baja se inician primero y se detienen por última vez. Por lo tanto, el módulo syslogd debe tener la prioridad 0.<br /> </td> 
   <td> Corto<br /> </td> 
   <td> 10<br /> </td> 
  </tr> 
 </tbody> 
</table>

## syslogd {#syslogd}

Estos son los diferentes parámetros del nodo **syslogd**. Esta es la configuración del módulo Administración de registros.

<table> 
 <thead> 
  <tr> 
   <th> Parámetro </th> 
   <th> Descripción </th> 
   <th> Tipo </th> 
   <th> Valor predeterminado </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> args<br /> </td> 
   <td> Parámetros de inicio<br /> </td> 
   <td> Cadena<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> autoStart<br /> </td> 
   <td> Inicio automático<br /> </td> 
   <td> Booleano<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> initScript<br /> </td> 
   <td> Id. de JavaScript que se ejecutará al iniciar el proceso.<br /> </td> 
   <td> Cadena<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> maxFileSizeMb<br /> </td> 
   <td> Tamaño máximo en Mb de un archivo de registro. <br /> </td> 
   <td> Long<br /> </td> 
   <td> 10<br /> </td> 
  </tr> 
  <tr> 
   <td> maxNumberOfLoginsFiles<br /> </td> 
   <td> Número máximo de archivos logins.log que mantener. <br /> </td> 
   <td> Long<br /> </td> 
   <td> 365<br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessMemoryAlertMb<br /> </td> 
   <td> Alerta de consumo de memoria: alerta relativa a la cantidad de RAM consumida (en MB) por un proceso determinado.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 1800<br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessMemoryWarningMb<br /> </td> 
   <td> Advertencia de consumo de memoria: advertencia sobre la cantidad de RAM consumida (en MB) por un proceso determinado.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 1600<br /> </td> 
  </tr> 
  <tr> 
   <td> processRestartTime<br /> </td> 
   <td> Hora del día en que se reinicia automáticamente el proceso. Consulte <a href="../../installation/using/configuring-campaign-server.md#automatic-process-restart" target="_blank">Reinicio automático del proceso</a>.<br /> </td> 
   <td> Cadena<br /> </td> 
   <td> '06:00:00' <br /> </td> 
  </tr> 
  <tr> 
   <td> runLevel<br /> </td> 
   <td> Prioridad al inicio. Los módulos de prioridad baja se inician primero y se detienen por última vez. Por lo tanto, el módulo syslogd debe tener la prioridad 0.<br /> </td> 
   <td> Corto<br /> </td> 
   <td> 10<br /> </td> 
  </tr> 
 </tbody> 
</table>

## seguimiento {#tracking}

Estos son los diferentes parámetros del nodo **tracking**. Esta es la configuración del servidor de seguimiento.

<table> 
 <thead> 
  <tr> 
   <th> Parámetro </th> 
   <th> Descripción </th> 
   <th> Tipo </th> 
   <th> Valor predeterminado </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> args<br /> </td> 
   <td> Parámetros de inicio<br /> </td> 
   <td> Cadena<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> autoStart<br /> </td> 
   <td> Inicio automático<br /> </td> 
   <td> Booleano<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> blockRedirectForUnsignedTrackingLink<br /> </td> 
   <td> Deshabilite las direcciones URL con formato incorrecto generadas a partir de compilaciones anteriores.<br /> </td> 
   <td> Booleano<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> ConsolidationPeriodSec<br /> </td> 
   <td> Período de consolidación <br /> </td> 
   <td> Long<br /> </td> 
   <td> 300<br /> </td> 
  </tr> 
  <tr> 
   <td> dedupOpenPeriodMin<br /> </td> 
   <td> Desduplicar aperturas: quite los registros de seguimiento abiertos duplicados para limitar los efectos de las vistas previas de correo en lectores de correo como Outlook.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 1<br /> </td> 
  </tr> 
  <tr> 
   <td> errorIgnorePercent<br /> </td> 
   <td> Ignorar hasta X% de los errores: no actualice los indicadores de seguimiento siempre que la proporción de asientos no tomados en cuenta no alcance este valor. <br /> </td> 
   <td> Byte<br /> </td> 
   <td> 1<br /> </td> 
  </tr> 
  <tr> 
   <td> errorIgnorePeriod<br /> </td> 
   <td> Actualizar indicadores de error: duración máxima antes de volver a calcular los indicadores de error.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 86400<br /> </td> 
  </tr> 
  <tr> 
   <td> indicatorsDuration<br /> </td> 
   <td> Calcular indicadores durante: duración posterior a la fecha de validez de un envío tras el cual ya no se calculan los indicadores consolidados.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 2592000<br /> </td> 
  </tr> 
  <tr> 
   <td> initScript<br /> </td> 
   <td> Id. de JavaScript que se ejecutará al iniciar el proceso <br /> </td> 
   <td> Cadena<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> logCountPerRequest<br /> </td> 
   <td> Número de registros solicitados por llamada al servidor de seguimiento remoto.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 1000<br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessMemoryAlertMb<br /> </td> 
   <td> Alerta de consumo de memoria: alerta relativa a la cantidad de RAM consumida (en MB) por un proceso determinado.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 1800<br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessMemoryWarningMb<br /> </td> 
   <td> Advertencia de consumo de memoria: advertencia sobre la cantidad de RAM consumida (en MB) por un proceso determinado.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 1600<br /> </td> 
  </tr> 
  <tr> 
   <td> phishbowlServiceAPIKey<br /> </td> 
   <td> Clave de API para la integración del extremo del servicio Phishbowl. Esto protege la redirección de direcciones URL con formato incorrecto generadas a partir de compilaciones anteriores. <br /> </td> 
   <td> Long<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> phishbowlServiceEndpoint<br /> </td> 
   <td> Punto final para la integración de punto final del servicio Phishbowl. Esto protege la redirección de direcciones URL mal formadas generadas a partir de compilaciones anteriores.<br /> </td> 
   <td> Long<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> processRestartTime<br /> </td> 
   <td> Hora del día en que se reinicia automáticamente el proceso. Consulte <a href="../../installation/using/configuring-campaign-server.md#automatic-process-restart" target="_blank">Reinicio automático del proceso</a>.<br /> </td> 
   <td> Cadena<br /> </td> 
   <td> '06:00:00' <br /> </td> 
  </tr> 
  <tr> 
   <td> runLevel<br /> </td> 
   <td> Prioridad al inicio. Los módulos de prioridad baja se inician primero y se detienen por última vez. Por lo tanto, el módulo syslogd debe tener la prioridad 0.<br /> </td> 
   <td> Corto<br /> </td> 
   <td> 10<br /> </td> 
  </tr> 
  <tr> 
   <td> trackingIgnorePercent<br /> </td> 
   <td> Ignorar hasta X% del seguimiento: no actualice los indicadores de seguimiento siempre que la proporción de asientos no tomados en cuenta no alcance este valor.<br /> </td> 
   <td> Byte<br /> </td> 
   <td> 1<br /> </td> 
  </tr> 
  <tr> 
   <td> trackingIgnorePeriod<br /> </td> 
   <td> Actualizar indicadores de seguimiento: duración máxima antes de volver a calcular los indicadores de seguimiento.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 86400<br /> </td> 
  </tr> 
  <tr> 
   <td> userAgentCacheSize<br /> </td> 
   <td> Tamaño de la caché del identificador del explorador.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 500<br /> </td> 
  </tr> 
 </tbody> 
</table>

## trackinglogd {#trackinglogd}

Estos son los diferentes parámetros del nodo **trackinglogd**. Esta es la configuración del daemon de escritura del registro de seguimiento.

<table> 
 <thead> 
  <tr> 
   <th> Parámetro </th> 
   <th> Descripción </th> 
   <th> Tipo </th> 
   <th> Valor predeterminado </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> args<br /> </td> 
   <td> Parámetros de inicio<br /> </td> 
   <td> Cadena<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> autoStart<br /> </td> 
   <td> Inicio automático<br /> </td> 
   <td> Booleano<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> initScript<br /> </td> 
   <td> Id. de JavaScript que se ejecutará al iniciar el proceso <br /> </td> 
   <td> Cadena<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> maxCreateFileRetry<br /> </td> 
   <td> Máximo de reintentos de escritura: número máximo de archivos que se pueden crear en caso de error de escritura en los archivos de registro.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 5<br /> </td> 
  </tr> 
  <tr> 
   <td> maxLogsSizeOnDiskMb<br /> </td> 
   <td> Tamaño máximo del registro: espacio máximo utilizado por los registros en el disco (en MB). No debe ser menor que 100 MB. <br /> </td> 
   <td> Long<br /> </td> 
   <td> 500<br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessMemoryAlertMb<br /> </td> 
   <td> Alerta de consumo de memoria: alerta relativa a la cantidad de RAM consumida (en MB) por un proceso determinado.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 1800<br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessMemoryWarningMb<br /> </td> 
   <td> Advertencia de consumo de memoria: advertencia sobre la cantidad de RAM consumida (en MB) por un proceso determinado.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 1600<br /> </td> 
  </tr> 
  <tr> 
   <td> maxSharedLogs<br /> </td> 
   <td> Maximum log count: número máximo de registros almacenados en la memoria compartida. No puede ser menor que 10000. <br /> </td> 
   <td> Long<br /> </td> 
   <td> 25000<br /> </td> 
  </tr> 
  <tr> 
   <td> processRestartTime<br /> </td> 
   <td> Hora del día en que se reinicia automáticamente el proceso. Consulte <a href="../../installation/using/configuring-campaign-server.md#automatic-process-restart" target="_blank">Reinicio automático del proceso</a>.<br /> </td> 
   <td> Cadena<br /> </td> 
   <td> '06:00:00' <br /> </td> 
  </tr> 
  <tr> 
   <td> purgeLogsPeriod<br /> </td> 
   <td> Number of logs before purge: número de registros insertados antes de iniciar la depuración de archivos de registro. No puede ser inferior a 50000.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 50000<br /> </td> 
  </tr> 
  <tr> 
   <td> runLevel<br /> </td> 
   <td> Prioridad al inicio. Los módulos de prioridad baja se inician primero y se detienen por última vez. Por lo tanto, el módulo syslogd debe tener la prioridad 0.<br /> </td> 
   <td> Corto<br /> </td> 
   <td> 10<br /> </td> 
  </tr> 
  <tr> 
   <td> webTrackingParamSize<br /> </td> 
   <td> Número máximo de caracteres guardados en la memoria compartida para parámetros de seguimiento web adicionales.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 64<br /> </td> 
  </tr> 
 </tbody> 
</table>

## web {#web}

Estos son los diferentes parámetros del nodo **web**. Esta es la configuración del módulo web.

Para obtener más información, consulte esta [sección](configuring-campaign-server.md#default-port-for-tomcat).

<table> 
 <thead> 
  <tr> 
   <th> Parámetro </th> 
   <th> Descripción </th> 
   <th> Tipo </th> 
   <th> Valor predeterminado </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> Opciones de JVM<br /> </td> 
   <td> Opciones de la JVM pasada como cadena.<br /> </td> 
   <td> Cadena<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> MaxThreads<br /> </td> 
   <td> Número máximo de subprocesos.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 75<br /> </td> 
  </tr> 
  <tr> 
   <td> MinSpareThreads<br /> </td> 
   <td> Número mínimo de subprocesos.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 5<br /> </td> 
  </tr> 
  <tr> 
   <td> args<br /> </td> 
   <td> Parámetros de inicio<br /> </td> 
   <td> Cadena<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> autoStart<br /> </td> 
   <td> Inicio automático<br /> </td> 
   <td> Booleano<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> controlPort<br /> </td> 
   <td> Puerto de control de escucha Tomcat: consulte <a href="configure-tomcat.md" target="_blank">Configurar Tomcat</a>.<br /> </td> 
   <td> Corto<br /> </td> 
   <td> 8005<br /> </td> 
  </tr> 
  <tr> 
   <td> httpPort<br /> </td> 
   <td> Puerto de escucha HTTP Tomcat: consulte <a href="configure-tomcat.md" target="_blank">Configurar Tomcat</a>.<br /> </td> 
   <td> Corto<br /> </td> 
   <td> 8080<br /> </td> 
  </tr> 
  <tr> 
   <td> initScript<br /> </td> 
   <td> Id. de JavaScript que se ejecutará al iniciar el proceso.<br /> </td> 
   <td> Cadena<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> maxDeliveryQueueSize<br /> </td> 
   <td> SOAP Tamaño de la cola para llamadas a SubmitDelivery: número máximo de llamadas a SubmitDelivery que se pueden poner en cola.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 50<br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessMemoryAlertMb<br /> </td> 
   <td> Alerta de consumo de memoria: alerta relativa a la cantidad de RAM consumida (en MB) por un proceso determinado.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 1800<br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessMemoryWarningMb<br /> </td> 
   <td> Advertencia de consumo de memoria: advertencia sobre la cantidad de RAM consumida (en MB) por un proceso determinado<br /> </td> 
   <td> Long<br /> </td> 
   <td> 1600<br /> </td> 
  </tr> 
  <tr> 
   <td> notifRelay<br /> </td> 
   <td> Transmisión de notificación: HostName:Puerto que habilita la retransmisión de notificaciones.<br /> </td> 
   <td> Cadena<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> processRestartTime<br /> </td> 
   <td> Hora del día en que se reinicia automáticamente el proceso. Consulte <a href="../../installation/using/configuring-campaign-server.md#automatic-process-restart" target="_blank">Reinicio automático del proceso</a>.<br /> </td> 
   <td> Cadena<br /> </td> 
   <td> '06:00:00' <br /> </td> 
  </tr> 
  <tr> 
   <td> runLevel<br /> </td> 
   <td> Prioridad al inicio. Los módulos de prioridad baja se inician primero y se detienen por última vez. Por lo tanto, el módulo syslogd debe tener la prioridad 0.<br /> </td> 
   <td> Corto<br /> </td> 
   <td> 10<br /> </td> 
  </tr> 
  <tr> 
   <td> startSoapRouterInModule<br /> </td> 
   <td> SOAP Iniciar el enrutador de la interfaz de usuario en modo de módulo.<br /> </td> 
   <td> Booleano<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
 </tbody> 
</table>

### jsp {#jsp}

Estos son los diferentes parámetros del nodo **web > jsp**. Esta es la configuración de los parámetros utilizados por los JSP.

<table> 
 <thead> 
  <tr> 
   <th> Parámetro </th> 
   <th> Descripción </th> 
   <th> Tipo </th> 
   <th> Valor predeterminado </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> depurar<br /> </td> 
   <td> Ejecución de JSP en modo de depuración o no.<br /> </td> 
   <td> Booleano<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> downloadPath<br /> </td> 
   <td> Carpeta de descarga: ruta de descarga de los programas de instalación para las consolas de cliente.<br /> </td> 
   <td> Cadena<br /> </td> 
   <td> '$(XTK_INSTALL_DIR)/datakit/nl/eng/jsp'<br /> </td> 
  </tr> 
  <tr> 
   <td> foFileName<br /> </td> 
   <td> Ruta de archivo .fo.<br /> </td> 
   <td> Cadena<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> soapRouter<br /> </td> 
   <td> SOAP URL del enrutador de la dirección de correo electrónico (http://myserver/xxx, http://jni o mailto:xxx).<br /> </td> 
   <td> Cadena<br /> </td> 
   <td> 'http://jni'<br /> </td> 
  </tr> 
 </tbody> 
</table>

El nodo **web > jsp > classpath** contiene la lista de todas las rutas de clase que se deben usar al iniciar JVM. Esta es la configuración predeterminada:

```
'$(XTK_INSTALL_DIR)/tomcat-X/bin/bootstrap.jar
          $(XTK_INSTALL_DIR)/tomcat-X/bin/tomcat-juli.jar
          $(XTK_INSTALL_DIR)/tomcat-X/lib/tomcat-coyote.jar
          $(XTK_INSTALL_DIR)/tomcat-X/lib/tomcat-util.jar
          $(XTK_INSTALL_DIR)/tomcat-X/lib/tomcat-api.jar
          $(XTK_INSTALL_DIR)/tomcat-X/lib/servlet-api.jar
          $(XTK_INSTALL_DIR)/tomcat-X/lib/jsp-api.jar
          $(XTK_INSTALL_DIR)/tomcat-X/lib/el-api.jar
          $(XTK_INSTALL_DIR)/tomcat-X/lib/annotations-api.jar
          $(XTK_INSTALL_DIR)/tomcat-X/lib/catalina.jar
          $(XTK_INSTALL_DIR)/tomcat-X/lib/websocket-api.jar
          $(XTK_INSTALL_DIR)/tomcat-X/lib/tomcat7-websocket.jar
          $(XTK_INSTALL_DIR)/java/lib/pdfbox-2.0.4.jar
          $(XTK_INSTALL_DIR)/java/lib/FontBox-0.1.0.jar
          $(XTK_INSTALL_DIR)/java/lib/AGJavaEndpoint.22.jar
          $(XTK_INSTALL_DIR)/java/lib/NSGConstants.jar
          $(XTK_INSTALL_DIR)/java/lib/smpp.jar
          $(XTK_INSTALL_DIR)/java/lib/nlweb.jar
          $(XTK_INSTALL_DIR)/java/lib/jcaptcha-all.jar
          $(XTK_INSTALL_DIR)/java/lib/apns-1.0.0.Beta6-jar-with-dependencies.jar
          $(XTK_INSTALL_DIR)/java/lib/commons-collections-3.2.2.jar
          $(XTK_INSTALL_DIR)/java/lib/jcommon-1.0.16.jar
          $(XTK_INSTALL_DIR)/java/lib/jfreechart-1.0.13.jar
          $(XTK_INSTALL_DIR)/java/lib/barcode4j-light.jar
          $(XTK_INSTALL_DIR)/java/lib/zxing.jar
          $(XTK_INSTALL_DIR)/java/lib/raztec.jar
          $(XTK_INSTALL_DIR)/java/lib/gson-2.7.jar
          $(XTK_INSTALL_DIR)/java/lib/alpn-api-1.1.3.v20160715.jar
          $(XTK_INSTALL_DIR)/java/lib/netty-all-4.1.6.Final.jar
          $(XTK_INSTALL_DIR)/java/lib/netty-tcnative-boringssl-static-1.1.33.Fork22.jar
          $(XTK_INSTALL_DIR)/java/lib/pushy-0.8.1.jar
          $(XTK_INSTALL_DIR)/java/lib/slf4j-api-1.7.21.jar
          $(XTK_INSTALL_DIR)/java/lib/slf4j-simple-1.7.21.jar'
```

### jssp {#jssp}

Estos son los diferentes parámetros del nodo **web > jssp**. Esta es la configuración de los parámetros que utilizan los JSSP.

<table> 
 <thead> 
  <tr> 
   <th> Parámetro </th> 
   <th> Descripción </th> 
   <th> Tipo </th> 
   <th> Valor predeterminado </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> collectGarbageAfterRequest<br /> </td> 
   <td> Activa el recolector de elementos no utilizados del contexto de JavaScript después de cada consulta.<br /> </td> 
   <td> Booleano<br /> </td> 
   <td> true<br /> </td> 
  </tr> 
  <tr> 
   <td> timeToLive<br /> </td> 
   <td> Número máximo de páginas servidas por un contexto de JavaScript. <br /> </td> 
   <td> Long<br /> </td> 
   <td> 1000<br /> </td> 
  </tr> 
 </tbody> 
</table>

El nodo **web > jsp > classpath** contiene la lista de todas las rutas de clase que se deben usar al iniciar JVM.

### relevo {#relay-2}

Estos son los diferentes parámetros del nodo **web > relay**. Esta es la configuración de la retransmisión para solicitudes HTTP entre dos zonas.

Para obtener más información, consulte esta [sección](../../installation/using/deploying-an-instance.md#synchronizing-public-resources).

<table> 
 <thead> 
  <tr> 
   <th> Parámetro </th> 
   <th> Descripción </th> 
   <th> Tipo </th> 
   <th> Valor predeterminado </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> debugRelay<br /> </td> 
   <td> Inicie el módulo de retransmisión HTTP en el servidor web en modo de depuración.<br /> </td> 
   <td> Booleano<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> forbiddenCharsInAuthority<br /> </td> 
   <td> Caracteres prohibidos (dominio): lista de caracteres prohibidos en la sección "autoridad" de un URI.<br /> </td> 
   <td> Cadena<br /> </td> 
   <td> '.?#@/:' <br /> </td> 
  </tr> 
  <tr> 
   <td> forbiddenCharsInPath<br /> </td> 
   <td> Caracteres prohibidos (ruta de acceso): lista de caracteres prohibidos en la sección "ruta de acceso" de un URI.<br /> </td> 
   <td> Cadena<br /> </td> 
   <td> '?#/'<br /> </td> 
  </tr> 
  <tr> 
   <td> modDir<br /> </td> 
   <td> Valor de la opción de módulo "mod_dir": lista de archivos que se utilizarán durante una consulta en una carpeta.<br /> </td> 
   <td> Cadena<br /> </td> 
   <td> 'index.md' <br /> </td> 
  </tr> 
  <tr> 
   <td> startRelay<br /> </td> 
   <td> Inicie el módulo de retransmisión HTTP.<br /> </td> 
   <td> Booleano<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> startRelayInModule<br /> </td> 
   <td> Inicie el módulo de retransmisión HTTP en el servidor web. <br /> </td> 
   <td> Booleano<br /> </td> 
   <td> true<br /> </td> 
  </tr> 
  <tr> 
   <td> tiempo de espera <br /> </td> 
   <td> Tiempo de espera antes de eliminar la dirección URL prohibida.<br /> </td> 
   <td> Cadena<br /> </td> 
   <td> '60'<br /> </td> 
  </tr> 
 </tbody> 
</table>

Agregue un nodo **web > relay > url** para cada URL que desee transmitir (el orden de inserción define la prioridad) con los siguientes parámetros.

Para obtener más información, consulte [Seguridad dinámica de páginas y transmisiones](../../installation/using/configuring-campaign-server.md#dynamic-page-security-and-relays) y [sección](../../installation/using/deploying-an-instance.md#synchronizing-public-resources).

<table> 
 <thead> 
  <tr> 
   <th> Parámetro </th> 
   <th> Descripción </th> 
   <th> Tipo </th> 
   <th> Valor predeterminado </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> IPMask<br /> </td> 
   <td> IP autorizadas: lista separada por comas de direcciones IP de origen permitidas para utilizar la retransmisión para esta máscara.<br /> </td> 
   <td> Cadena<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> denegar <br /> </td> 
   <td> Denegar el acceso a estas direcciones URL (devuelve el error HTTP 403)<br /> </td> 
   <td> Booleano<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> hostMask<br /> </td> 
   <td> Alias DNS para retransmitir: lista separada por comas de máscaras de alias DNS para retransmitir (por ejemplo: '*.adobe.com').<br /> </td> 
   <td> Cadena<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> httpAllowed<br /> </td> 
   <td> Acceso HTTP autorizado independientemente de la zona de seguridad (como webApps). <br /> </td> 
   <td> Booleano<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> relayHost<br /> </td> 
   <td> Agregar host original: use el encabezado "Host" HTTP de la solicitud original al retransmitir.<br /> </td> 
   <td> Booleano<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> relayPath<br /> </td> 
   <td> Añadir ruta de URL inicial: añada la ruta completa de las URL que se retransmitirán a la URL de la página de destino. <br /> </td> 
   <td> Booleano<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> estado<br /> </td> 
   <td> Estado de sincronización de un recurso público (enumeración). Los valores posibles son 'normal' (ejecución normal), 'blacklist' (dirección URL agregada a la lista de bloqueados de la en caso de error 404) y 'spare' (carga del archivo en el servidor de reserva si existe).<br /> </td> 
   <td> Cadena<br /> </td> 
   <td> normal<br /> </td> 
  </tr> 
  <tr> 
   <td> targetUrl<br /> </td> 
   <td> URL de la página de destino: consulte <a href="configure-tomcat.md" target="_blank">Configurar Tomcat</a>.<br /> </td> 
   <td> Cadena<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> tiempo de espera <br /> </td> 
   <td> Tiempo máximo de ejecución (en segundos) de la solicitud que se está retransmitiendo.<br /> </td> 
   <td> Long<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> urlPath<br /> </td> 
   <td> Máscara de direcciones URL para retransmitir (por ejemplo: "/nl*", "*.jsp").<br /> </td> 
   <td> Cadena<br /> </td> 
   <td> <br /> </td> 
  </tr> 
 </tbody> 
</table>

Esta es la configuración predeterminada:

```
<url IPMask="" deny="" hostMask="" relayHost="true" relayPath="true"
     status="normal" targetUrl="http://localhost:7781" timeout="" urlPath="/pipelined/*"/>
<url IPMask="" deny="" hostMask="" relayHost="true" relayPath="true" targetUrl="http://localhost:8080"
     timeout="" status="normal" httpAllowed="false" urlPath="/view/*"/>
<url IPMask="" deny="true" hostMask="" relayHost="true" relayPath="true" targetUrl="http://localhost:8080"
     timeout="" status="normal" httpAllowed="false" urlPath="*ooconv.jsp*"/>
<url IPMask="" deny="true" hostMask="" relayHost="true" relayPath="true" targetUrl="http://localhost:8080"
     timeout="" status="normal" httpAllowed="false" urlPath="/res/*.jsp*"/>
<url IPMask="" deny="" hostMask="" relayHost="true" relayPath="true" targetUrl="http://localhost:8080"
     timeout="" status="normal" httpAllowed="true" urlPath="*/sc.jssp"/>
<url IPMask="" deny="" hostMask="" relayHost="true" relayPath="true" targetUrl="http://localhost:8080"
     timeout="" status="normal" httpAllowed="true" urlPath="*/interactionProposal.jssp"/>
<url IPMask="" deny="" hostMask="" relayHost="true" relayPath="true" targetUrl="http://localhost:8080"
     timeout="" status="normal" httpAllowed="true" urlPath="*/zoneJson.jssp"/>
<url IPMask="" deny="" hostMask="" relayHost="true" relayPath="true" targetUrl="http://localhost:8080"
     timeout="" status="normal" httpAllowed="true" urlPath="/nms/jsp/barcode.jsp"/>
<url IPMask="" deny="" hostMask="" relayHost="true" relayPath="true" targetUrl="http://localhost:8080"
     timeout="" status="normal" httpAllowed="true" urlPath="/nms/jsp/captcha.jsp"/>
<url IPMask="" deny="" hostMask="" relayHost="true" relayPath="true" targetUrl="http://localhost:8080"
     timeout="" status="normal" httpAllowed="true" urlPath="/nms/jsp/webForm.jsp"/>
<url IPMask="" deny="" hostMask="" relayHost="true" relayPath="true" targetUrl="http://localhost:8080"
     timeout="" status="normal" httpAllowed="true" urlPath="/xtk/jsp/zoneinfo.jsp"/>
<url IPMask="" deny="" hostMask="" relayHost="true" relayPath="true" targetUrl="http://localhost:8080"
     timeout="" status="normal" httpAllowed="true" urlPath="*/facebookCallback.jssp"/>
<url IPMask="" deny="" hostMask="" relayHost="true" relayPath="true" targetUrl="http://localhost:8080"
     timeout="" status="normal" httpAllowed="true" urlPath="/nl/jsp/m.jsp"/>
<url IPMask="" deny="" hostMask="" relayHost="true" relayPath="true" targetUrl="http://localhost:8080"
     timeout="" status="normal" httpAllowed="true" urlPath="/nl/jsp/s.jsp"/>

<url IPMask="" deny="" hostMask="" relayHost="true" relayPath="true" targetUrl="http://localhost:8080"
     timeout="" status="blacklist" httpAllowed="false" urlPath="/nms/jsp/*.jsp"/>
<url IPMask="" deny="" hostMask="" relayHost="true" relayPath="true" targetUrl="http://localhost:8080"
     timeout="" status="blacklist" httpAllowed="false" urlPath="/xtk/jsp/*.jsp"/>
<url IPMask="" deny="" hostMask="" relayHost="true" relayPath="true" targetUrl="http://localhost:8080"
     timeout="" status="blacklist" httpAllowed="false" urlPath="/nl/jsp/*.jsp"/>
<url IPMask="" deny="" hostMask="" relayHost="true" relayPath="true" targetUrl="http://localhost:8080"
     timeout="" status="blacklist" httpAllowed="false" urlPath="*.jssp"/>
<url IPMask="" deny="" hostMask="" relayHost="true" relayPath="true" targetUrl="http://localhost:8080"
     timeout="" status="blacklist" httpAllowed="true" urlPath="/webApp/*"/>
<url IPMask="" deny="" hostMask="" relayHost="true" relayPath="true" targetUrl="http://localhost:8080"
     timeout="" status="blacklist" httpAllowed="false" urlPath="/report/*"/>
<url IPMask="" deny="" hostMask="" relayHost="true" relayPath="true" targetUrl="http://localhost:8080"
     timeout="" status="blacklist" httpAllowed="false" urlPath="/jssp/*"/>
<url IPMask="" deny="" hostMask="" relayHost="true" relayPath="true" targetUrl="http://localhost:8080"
     timeout="" status="normal" httpAllowed="false" urlPath="/strings/*"/>
<url IPMask="" deny="" hostMask="" relayHost="true" relayPath="true" targetUrl="http://localhost:8080"
     timeout="" status="normal" httpAllowed="true" urlPath="/interaction/*"/>
<url IPMask="" deny="" hostMask="" relayHost="true" relayPath="true" targetUrl="http://localhost:8080"
     timeout="" status="normal" httpAllowed="true" urlPath="/barcode/*"/>
<url IPMask="" deny="" hostMask="" relayHost="true" relayPath="true" targetUrl="http://localhost:8080"
     timeout="" status="normal" httpAllowed="true" urlPath="/lineImage/*"/>

<url IPMask="" deny="" hostMask="" relayHost="false" relayPath="false" targetUrl=""
     timeout="" status="spare" httpAllowed="true" urlPath="/favicon.*"/>
<url IPMask="" deny="" hostMask="" relayHost="false" relayPath="false" targetUrl=""
     timeout="" status="spare" httpAllowed="true" urlPath="/*.md"/>
<url IPMask="" deny="" hostMask="" relayHost="false" relayPath="false" targetUrl=""
     timeout="" status="spare" httpAllowed="true" urlPath="/*.png"/>
<url IPMask="" deny="" hostMask="" relayHost="false" relayPath="false" targetUrl=""
     timeout="" status="spare" httpAllowed="true" urlPath="/*.jpg"/>
```

Agregue un nodo **web > relay > responseHeader** para cada encabezado HTTP para agregarlo a las respuestas reenviadas a la retransmisión.

Para obtener más información, consulte [Administración de encabezados HTTP](../../installation/using/configuring-campaign-server.md#managing-http-headers).

<table> 
 <thead> 
  <tr> 
   <th> Parámetro </th> 
   <th> Descripción </th> 
   <th> Tipo </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> nombre<br /> </td> 
   <td> Nombre de encabezado <br /> </td> 
   <td> Cadena<br /> </td> 
  </tr> 
  <tr> 
   <td> valor<br /> </td> 
   <td> Valor de encabezado <br /> </td> 
   <td> Cadena<br /> </td> 
  </tr> 
 </tbody> 
</table>

Esta es la configuración predeterminada:

```
<responseHeader name="X-XSS-Protection" value="1; mode=block"/>
```

### redirección {#redirection}

Estos son los diferentes parámetros del nodo **web > redirection**. Esta es la configuración del módulo de redirección.

Para obtener más información, consulte esta [sección](../../installation/using/deploying-an-instance.md#synchronizing-public-resources).

<table> 
 <thead> 
  <tr> 
   <th> Parámetro </th> 
   <th> Descripción </th> 
   <th> Tipo </th> 
   <th> Valor predeterminado </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> IMSOrgId<br /> </td> 
   <td> ID de organización: identificador único de organización en Adobe Experience Cloud, utilizado en particular para el servicio VisitorID y el SSO de IMS. <br /> </td> 
   <td> Cadena<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> P3PCompactPolicy<br /> </td> 
   <td> Valor que describe la directiva utilizada para las cookies permanentes (compatible con el formato de directiva compacta P3P). <br /> </td> 
   <td> Cadena<br /> </td> 
   <td> DSP 'CAO COR CURa DEVa TAIa OUR BUS IND UNI COM NAV'<br /> </td> 
  </tr> 
  <tr> 
   <td> cookieDomain<br /> </td> 
   <td> Lista de dominios separados por comas que se deben configurar para indicar explícitamente el dominio que se va a establecer como cookie. <br /> </td> 
   <td> Cadena<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> databaseId<br /> </td> 
   <td> Identificador de base de datos asociado a la instancia de seguimiento.<br /> </td> 
   <td> Cadena<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> defLogCount<br /> </td> 
   <td> Registrar recuento por llamada: número de registros devueltos de forma predeterminada tras una llamada del método GetTrackingLogs.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 30<br /> </td> 
  </tr> 
  <tr> 
   <td> expirationURL<br /> </td> 
   <td> Página para redirecciones caducadas: dirección URL de la página web utilizada de forma predeterminada por el servidor de redirección cuando ha caducado la redirección de una acción de envío.<br /> </td> 
   <td> Cadena<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> maxJobsInCache<br /> </td> 
   <td> Maximum job count: número máximo de acciones de envío en caché. No puede ser inferior a 50. <br /> </td> 
   <td> Long<br /> </td> 
   <td> 100<br /> </td> 
  </tr> 
  <tr> 
   <td> showSourceIP<br /> </td> 
   <td> Cuando se establece en false, el valor de sourceIP en la respuesta devuelta por r/test es una cadena vacía. <br /> </td> 
   <td> Booleano<br /> </td> 
   <td> true<br /> </td> 
  </tr> 
  <tr> 
   <td> startRedirection<br /> </td> 
   <td> Iniciar el servicio de redirección.<br /> </td> 
   <td> Booleano<br /> </td> 
   <td> true<br /> </td> 
  </tr> 
  <tr> 
   <td> startRedirectionInModule<br /> </td> 
   <td> Iniciar el servicio de redirección en modo de módulo.<br /> </td> 
   <td> Booleano<br /> </td> 
   <td> true<br /> </td> 
  </tr> 
  <tr> 
   <td> trackWebVisitors<br /> </td> 
   <td> Seguimiento web: creación de registros para las páginas visitadas por usuarios desconocidos. <br /> </td> 
   <td> Booleano<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> trackingPassword<br /> </td> 
   <td> Contraseña utilizada por el servidor de redirección.<br /> </td> 
   <td> Cadena<br /> </td> 
   <td> <br /> </td> 
  </tr> 
 </tbody> 
</table>

Estos son los diferentes parámetros del nodo **web > redirection > spareServer**.

Para obtener más información, consulte [Seguimiento redundante](../../installation/using/configuring-campaign-server.md#redundant-tracking).

<table> 
 <thead> 
  <tr> 
   <th> Parámetro </th> 
   <th> Descripción </th> 
   <th> Tipo </th> 
   <th> Valor predeterminado </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> enabledIf<br /> </td> 
   <td> Taken into account if: el servidor de seguimiento se tiene en cuenta si la expresión devuelve true. <br /> </td> 
   <td> Cadena<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> id<br /> </td> 
   <td> Nombre<br /> </td> 
   <td> Cadena<br /> </td> 
   <td> 1<br /> </td> 
  </tr> 
  <tr> 
   <td> url<br /> </td> 
   <td> URL del servidor de redirección adicional <br /> </td> 
   <td> Cadena<br /> </td> 
   <td> <br /> </td> 
  </tr> 
 </tbody> 
</table>

### spamCheck {#spamcheck}

Estos son los diferentes parámetros del nodo **web > spamCheck**. Esta es la configuración de los parámetros de evaluación de puntuación antispam de correo electrónico.

Para obtener más información, consulte [Configuración de SpamAssassin](../../installation/using/configuring-spamassassin.md).

<table> 
 <thead> 
  <tr> 
   <th> Parámetro </th> 
   <th> Descripción </th> 
   <th> Tipo </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> comando <br /> </td> 
   <td> Comando a ejecutar para evaluar la puntuación antispam de un correo electrónico (p. ej. 'perl spamcheck.pl').<br /> </td> 
   <td> Cadena<br /> </td> 
  </tr> 
 </tbody> 
</table>

## wfserver {#wfserver}

Estos son los diferentes parámetros del nodo **wfserver**. Configuración del proceso de flujo de trabajo.

Para obtener información adicional, consulte [Flujos de trabajo de alta disponibilidad y afinidades](../../installation/using/configuring-campaign-server.md#high-availability-workflows-and-affinities).

<table> 
 <thead> 
  <tr> 
   <th> Parámetro </th> 
   <th> Descripción </th> 
   <th> Tipo </th> 
   <th> Valor predeterminado </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> afinidad<br /> </td> 
   <td> Afinidad<br /> </td> 
   <td> Cadena<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> args<br /> </td> 
   <td> Parámetros de inicio<br /> </td> 
   <td> Cadena<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> autoStart<br /> </td> 
   <td> Inicio automático<br /> </td> 
   <td> Booleano<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> dataBasePoolPeriodSec<br /> </td> 
   <td> Período<br /> </td> 
   <td> Long<br /> </td> 
   <td> 20<br /> </td> 
  </tr> 
  <tr> 
   <td> initScript<br /> </td> 
   <td> Id. de JavaScript que se ejecutará al iniciar el proceso.<br /> </td> 
   <td> Cadena<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessMemoryAlertMb<br /> </td> 
   <td> Alerta de consumo de memoria: alerta relativa a la cantidad de RAM consumida (en MB) por un proceso determinado.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 1800<br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessMemoryWarningMb<br /> </td> 
   <td> Advertencia de consumo de memoria: advertencia sobre la cantidad de RAM consumida (en MB) por un proceso determinado.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 1600<br /> </td> 
  </tr> 
  <tr> 
   <td> notifRelay<br /> </td> 
   <td> Transmisión de notificación: HostName:Puerto que habilita la retransmisión de notificaciones.<br /> </td> 
   <td> Cadena<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> processRestartTime<br /> </td> 
   <td> Hora del día en que se reinicia automáticamente el proceso. Consulte <a href="../../installation/using/configuring-campaign-server.md#automatic-process-restart" target="_blank">Reinicio automático del proceso</a>.<br /> </td> 
   <td> Cadena<br /> </td> 
   <td> '06:00:00' <br /> </td> 
  </tr> 
  <tr> 
   <td> runLevel<br /> </td> 
   <td> Prioridad al inicio. Los módulos de prioridad baja se inician primero y se detienen por última vez. Por lo tanto, el módulo syslogd debe tener la prioridad 0.<br /> </td> 
   <td> Corto<br /> </td> 
   <td> 10<br /> </td> 
  </tr> 
 </tbody> 
</table>
