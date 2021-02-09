---
solution: Campaign Classic
product: campaign
title: El archivo de configuración del servidor
description: El archivo de configuración del servidor
audience: installation
content-type: reference
topic-tags: appendices
translation-type: tm+mt
source-git-commit: f39a84108c1f3327a469d5a230518652647ed63e
workflow-type: tm+mt
source-wordcount: '7846'
ht-degree: 8%

---


# El archivo de configuración del servidor{#the-server-configuration-file}

La configuración general de Adobe Campaign se define en el archivo **serverConf.xml**, ubicado en el directorio **conf** del directorio de instalación. Esta sección lista todos los diferentes nodos y parámetros del archivo **serverConf.xml**.

>[!NOTE]
>
>Las configuraciones del lado del servidor sólo pueden ser realizadas por Adobe para implementaciones alojadas en Adobe. Para obtener más información sobre las diferentes implementaciones, consulte la sección [Hosting models](../../installation/using/hosting-models.md) o [esta página](../../installation/using/capability-matrix.md). Los pasos de instalación y configuración para los modelos alojados e híbridos se presentan en esta [sección](../../installation/using/hosted-model.md).

Los primeros parámetros están dentro del nodo **compartido**. Están relacionados con la instancia. Son potencialmente utilizados por todos los comandos nlserver (nlserver web, nlserver wfserver, etc.). Las demás secciones están relacionadas con un subcomando nlserver específico.

**Parámetros compartidos**

* [autenticación](#authentication)
* [dataStore](#datastore)
* [dnsConfig](#dnsconfig)
* [exec](#exec)
* [htmlToPdf](#htmltopdf)
* [javaScript](#javascript)
* [mailExchange](#mailexchanger)
* [módulo](#module)
* [monitoreo](#monitoring)
* [ooconv](#ooconv)
* [proxyConfig](#proxyconfig)
* [threadPool](#threadpool)
* [urlPermission](#urlpermission)
* [xtkJobs](#xtkjobs)

**Otros parámetros**

* [archivar](#archiving)
* [inMail](#inmail)
* [interactiond](#interactiond)
* [mta](#mta)
* [nmac](#nmac)
* [canalizado](#pipelined)
* [reparación](#repair)
* [securityZone](#securityzone)
* [sms](#sms)
* [stat](#stat)
* [syslogd](#syslogd)
* [tracking](#tracking)
* [trackinglogd](#trackinglogd)
* [web](#web)
* [wfserver](#wfserver)

## autenticación {#authentication}

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
   <td> Habilitar la comprobación de direcciones IP.<br /> </td> 
   <td> Boolean<br /> </td> 
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
   <td> Largo<br /> </td> 
   <td> 1296000<br /> </td> 
  </tr> 
  <tr> 
   <td> securityTimeOutSec<br /> </td> 
   <td> Tiempo de espera del token de seguridad en segundos.<br /> </td> 
   <td> Largo<br /> </td> 
   <td> 86400<br /> </td> 
  </tr> 
  <tr> 
   <td> sessionCacheSec<br /> </td> 
   <td> Duración de caché: caché de la información de la sesión en segundos.<br /> </td> 
   <td> Largo<br /> </td> 
   <td> 600<br /> </td> 
  </tr> 
  <tr> 
   <td> sessionTimeOutSec<br /> </td> 
   <td> Tiempo de espera de sesión en segundos.<br /> </td> 
   <td> Largo<br /> </td> 
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
   <td> Exportar directorio: ruta del directorio de destino para los datos exportados.<br /> </td> 
   <td> Cadena<br /> </td> 
   <td> '$(XTK_INSTALL_DIR)/var/$(INSTANCE_NAME)/export/' <br /> </td> 
  </tr> 
  <tr> 
   <td> extraSandboxedDirectories<br /> </td> 
   <td> Directorios adicionales con zonas protegidas: otras rutas que se añadirán al entorno limitado de pruebas (separadas por coma).<br /> </td> 
   <td> Cadena<br /> </td> 
   <td> '/home/customers/,/sftp/' <br /> </td> 
  </tr> 
  <tr> 
   <td> formCacheTimeToLive<br /> </td> 
   <td> Retraso de caducidad de la caché del formulario: tiempo de espera en segundos tras el cual se invalida una entrada de caché. O significa que las entradas de caché solo se actualizan en el momento de la publicación.<br /> </td> 
   <td> Largo<br /> </td> 
   <td> 600<br /> </td> 
  </tr> 
  <tr> 
   <td> hosts<br /> </td> 
   <td> Máscaras DNS: lista de máscaras DNS que esta instancia proporciona (separadas por coma, puede utilizar * y ? patrones).<br /> </td> 
   <td> Cadena<br /> </td> 
   <td> '*'<br /> </td> 
  </tr> 
  <tr> 
   <td> interactiveCacheTimeToLive<br /> </td> 
   <td> Retraso de caducidad de caché JSSP de interacción: tiempo de espera en segundos tras el cual se invalida una entrada de caché. Un valor negativo significa que la caché siempre se invalida. Los valores '0', vacíos o no válidos se consideran 60.<br /> </td> 
   <td> Largo<br /> </td> 
   <td> 300<br /> </td> 
  </tr> 
  <tr> 
   <td> lang<br /> </td> 
   <td> Idioma de instancia (lista desglosada). Los valores posibles son 'fr_FR' (Français), 'en_GB' (Inglés (Reino Unido), 'en_US' (Inglés (Estados Unidos)), 'de_DE' (Deutsch) y 'ja_JP' (Japonés).<br /> </td> 
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
   <td> Los archivos autorizados se descargarán separados por ','. La cadena debe ser una expresión java normal y válida. Consulte <a href="../../installation/using/configuring-campaign-server.md#limiting-uploadable-files" target="_blank">Limitación de archivos cargables</a>.<br /> </td> 
   <td> Cadena<br /> </td> 
   <td> '.+' <br /> </td> 
  </tr> 
  <tr> 
   <td> useVault<br /> </td> 
   <td> Almacenar secretos en Vault: use Hashicorp Vault.<br /> </td> 
   <td> Boolean<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> vaultSecretPath<br /> </td> 
   <td> Ruta secreta en Vault<br /> </td> 
   <td> Cadena<br /> </td> 
   <td> '/v1/secret/campaña/'<br /> </td> 
  </tr> 
  <tr> 
   <td> vaultTokenPath<br /> </td> 
   <td> Ruta de acceso local del archivo que contiene el token de almacén. $(HOME) se puede utilizar en esta ruta (pero no en otras variables env).<br /> </td> 
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
   <td> Período de validez de la caché de vista: tiempo de espera en segundos tras el cual se invalida una entrada de caché. Un valor negativo significa que la caché siempre se invalida. Los valores '0', vacíos o no válidos se consideran 60.<br /> </td> 
   <td> Largo<br /> </td> 
   <td> 600<br /> </td> 
  </tr> 
  <tr> 
   <td> workingDirectory<br /> </td> 
   <td> XPath del directorio de trabajo.<br /> </td> 
   <td> Cadena<br /> </td> 
   <td> workingDirectory : XPath del directorio de trabajo. Predeterminado: '$(XTK_INSTALL_DIR)/var/$(INSTANCE_NAME)/Workspace/'<br /> </td> 
  </tr> 
 </tbody> 
</table>

### proxyFit {#proxyadjust}

Estos son los diferentes parámetros del nodo **dataStore > proxyAdjustment**. Las direcciones URL que coinciden con la expresión normal se regeneran según la dirección URL definida en urlBase.

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
   <td> Base para usar al generar direcciones URL externas. Por ejemplo: https://server.domain.com<br /> </td> 
   <td> Cadena<br /> </td> 
  </tr> 
  <tr> 
   <td> urlRegEx<br /> </td> 
   <td> Expresión regular para que coincidan con las direcciones URL. Por ejemplo: http://server\.lan\.net.*<br /> </td> 
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
   <td> name<br /> </td> 
   <td> Nombre de la fuente de datos<br /> </td> 
   <td> Cadena<br /> </td> 
   <td> por defecto<br /> </td> 
  </tr> 
 </tbody> 
</table>

En el nodo **dataStore > dataSource > dbcnx**, configure la conexión:

<table> 
 <thead> 
  <tr> 
   <th> Parámetro </th> 
   <th> Descripción </th> 
   <th> Tipo </th> 
   <th> Valor predeterminado<br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> NChar<br /> </td> 
   <td> Almacenamiento Unicode<br /> </td> 
   <td> Boolean<br /> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> dbSchema<br /> </td> 
   <td> Espacio de trabajo<br /> </td> 
   <td> Cadena<br /> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> encrypated<br /> </td> 
   <td> Contraseña cifrada<br /> </td> 
   <td> Boolean<br /> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> login<br /> </td> 
   <td> Cuenta<br /> </td> 
   <td> Cadena<br /> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> password<br /> </td> 
   <td> Contraseña<br /> </td> 
   <td> Cadena<br /> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> provider<br /> </td> 
   <td> Tipo (lista desglosada). Los valores posibles son 'Oracle', 'MSSQL' (Microsoft SQL Server), 'PostgreSQL' (PostgreSQL, Greenplum), 'Teradata', 'DB2', 'MySQL', 'Netezza', 'AsterData', 'SAPHANA' (SAP HANA), 'RedShift' (Amazon Redshift), 'ODBC' (ODBC (Sybase ASE, Sybase IQ), 'Relay' (HTTP) a la base de datos remota).<br /> </td> 
   <td> Cadena<br /> </td> 
   <td> 'Oracle'<br /> </td> 
  </tr> 
  <tr> 
   <td> server<br /> </td> 
   <td> Servidor<br /> </td> 
   <td> Cadena<br /> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> timezone<br /> </td> 
   <td> Zona horaria: consulte <a href="../../installation/using/time-zone-management.md" target="_blank">Administración de husos horarios</a>.<br /> </td> 
   <td> Cadena<br /> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> unicodeData<br /> </td> 
   <td> Datos Unicode en la base de datos<br /> </td> 
   <td> Boolean<br /> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> useTimestampTZ<br /> </td> 
   <td> Campos de fecha con zona horaria: consulte <a href="../../installation/using/time-zone-management.md" target="_blank">Administración de husos horarios</a>.<br /> </td> 
   <td> Boolean<br /> </td> 
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
   <td> Prefijo de función<br /> </td> 
   <td> Cadena<br /> </td> 
  </tr> 
 </tbody> 
</table>

En el nodo **dataStore > dataSource > pool**, configure los parámetros del grupo de conexiones asociadas:

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
   <td> aliveTestDelaySec<br /> </td> 
   <td> Retraso entre las comprobaciones de validez de la conexión.<br /> </td> 
   <td> Corto<br /> </td> 
  </tr> 
  <tr> 
   <td> freeCnx<br /> </td> 
   <td> Número de conexiones gratuitas que se mantienen en el grupo.<br /> </td> 
   <td> Corto<br /> </td> 
  </tr> 
  <tr> 
   <td> maxCnx<br /> </td> 
   <td> Número máximo de conexiones permitidas antes de rechazar una nueva conexión. Consulte esta <a href="https://helpx.adobe.com/campaign/kb/how-to-increase-the-maximum-number-of-database-connections-from-.html">nota técnica</a>.<br /> </td> 
   <td> Corto<br /> </td> 
  </tr> 
  <tr> 
   <td> maxIdleDelaySec<br /> </td> 
   <td> Tiempo máximo de inactividad de la conexión. 0 significa valor predeterminado.<br /> </td> 
   <td> Corto<br /> </td> 
  </tr> 
 </tbody> 
</table>

### virtualDir {#virtualdir}

Estos son los diferentes parámetros del nodo **dataStore > virtualDir**. Esta es la configuración del directorio virtual a la asignación de directorios real.

Para obtener más información, consulte [Administración de recursos públicos](../../installation/using/configuring-campaign-server.md#managing-public-resources).

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
   <td> name<br /> </td> 
   <td> Nombre del directorio virtual <br /> </td> 
   <td> Cadena<br /> </td> 
  </tr> 
  <tr> 
   <td> path<br /> </td> 
   <td> Ruta completa del directorio real<br /> </td> 
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

Estos son los diferentes parámetros del nodo **dataStore > preprocessCommand**. Estos son los comandos autorizados para el preprocesamiento de la actividad de flujo de trabajo &#39;Cargar archivo&#39;.

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
   <td> comando<br /> </td> 
   <td> Línea de comandos <br /> </td> 
   <td> Cadena<br /> </td> 
  </tr> 
  <tr> 
   <td> label<br /> </td> 
   <td> Etiqueta de línea de comandos<br /> </td> 
   <td> Cadena<br /> </td> 
  </tr> 
  <tr> 
   <td> name<br /> </td> 
   <td> Nombre de la línea de comandos<br /> </td> 
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

Estos son los diferentes parámetros del nodo **dnsConfig** (configuración DNS).

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
   <td> Nombre de dominio: nombre de dominio predeterminado. Utilizado por el comando SMTP HELO. De forma predeterminada, utiliza los parámetros de red de la primera interfaz de red declarada en Windows; o analiza el file/etc/resolv.conf en Linux (dominio o entrada de búsqueda). <br /> </td> 
   <td> Cadena<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> nameServers<br /> </td> 
   <td> Servidor DNS: lista separada por comas de servidores de nombres de dominio (DNS). Véase la nota siguiente.<br /> </td> 
   <td> Cadena<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> reintentar<br /> </td> 
   <td> Número de reintentos para una consulta DNS.<br /> </td> 
   <td> Largo<br /> </td> 
   <td> 4<br /> </td> 
  </tr> 
  <tr> 
   <td> timeout<br /> </td> 
   <td> Tiempo de espera en milisegundos para una consulta DNS.<br /> </td> 
   <td> Largo<br /> </td> 
   <td> 5000<br /> </td> 
  </tr> 
 </tbody> 
</table>

>[!NOTE]
>
>Nota en **nameSevers**: de forma predeterminada, utiliza la red
>parámetros de la primera interfaz de red declarada en Windows
>no definida en UNIX. Define los servidores de nombres de dominio (DNS)
>utilizado por el MTA para obtener el Intercambio de correo declarado para
>un dominio.
>
>Si no se define este valor, el MTA busca esta información en la configuración de red del host. Si son posibles varios DNS, las distintas direcciones DNS deben separarse con una coma (ejemplo: 212.155.207.1.212.155.207.2). Si el servidor envío tiene varias interfaces de red, la lista DNS utilizada por el MTA es la primera. En este caso, se recomienda especificar el parámetro **nameServer** para evitar cualquier ambigüedad.

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
   <td> Ruta al archivo que contiene los comandos para agregar a la lista de permitidos. <br /> </td> 
   <td> Cadena<br /> </td> 
  </tr> 
  <tr> 
   <td> user<br /> </td> 
   <td> Ejecutar comandos como un usuario diferente.<br /> </td> 
   <td> Cadena<br /> </td> 
  </tr> 
 </tbody> 
</table>

## htmlToPdf {#htmltopdf}

Estos son los diferentes parámetros del nodo **htmlToPdf**. Esta es la configuración del servicio para convertir páginas Web en documentos PDF.

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
   <td> comando<br /> </td> 
   <td> Línea de comandos para ejecutar la conversión (en modo 'otro').<br /> </td> 
   <td> Cadena<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessCount<br /> </td> 
   <td> Max. número de procesos de conversión permitidos a la vez en un equipo.<br /> </td> 
   <td> Largo<br /> </td> 
   <td> 5<br /> </td> 
  </tr> 
  <tr> 
   <td> mode<br /> </td> 
   <td> Herramienta que se utilizará para la conversión. Los valores posibles son: phantomjs, wkhtmltopdf, otros, deshabilitados<br /> </td> 
   <td> Cadena<br /> </td> 
   <td> 'phantomjs' <br /> </td> 
  </tr> 
  <tr> 
   <td> timeout<br /> </td> 
   <td> Tiempo de espera para una conversión: tiempo máximo de conversión en segundos. Más allá de este umbral, el proceso de conversión se detiene y se genera un error.<br /> </td> 
   <td> Largo<br /> </td> 
   <td> 120<br /> </td> 
  </tr> 
  <tr> 
   <td> verbose<br /> </td> 
   <td> Modo detallado: inicio en modo detallado para diagnosticar posibles errores.<br /> </td> 
   <td> Boolean<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> waitTime<br /> </td> 
   <td> Retraso al esperar un proceso: retraso en segundos, cuando se utilizan todos los procesos al mismo tiempo y cuando se espera a que se libere un proceso. Si se supera este retraso, la conversión se detiene y se genera un error. <br /> </td> 
   <td> Largo<br /> </td> 
   <td> 15<br /> </td> 
  </tr> 
 </tbody> 
</table>

Ejemplo para phantomjs:

```
phantomjs - -ignore-ssl-errors=true '$(XTK_INSTALL_DIR)/bin/htmlToPdf.js' '-out:{outPdf}' '-post:{postFile}' '-url:{originUrl}' -sessiontoken:{sessiontoken} -format:{format} -orientation:{orientation} -marginTop:{marginTop} -marginLeft:{marginLeft} -marginRight:{marginRight} -marginBottom:{marginBottom}
```

## javaScript {#javascript}

Estos son los diferentes parámetros del nodo **javaScript**. Ésta es la configuración del intérprete de JavaScript.

Para obtener más información, consulte la [documentación de Sistema de informes](../../reporting/using/actions-on-reports.md#memory-allocation) y esta [nota técnica](https://helpx.adobe.com/campaign/kb/out-of-memory-error-in-js-code-activity-in-workflows.html).

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
   <td> Largo<br /> </td> 
   <td> 512 <br /> </td> 
  </tr> 
  <tr> 
   <td> stackSizeKB<br /> </td> 
   <td> Tamaño de cada fragmento de pila en octetos de kilo. Es un parámetro de ajuste de administración de memoria que la mayoría de los usuarios no deben ajustar. <br /> </td> 
   <td> Largo<br /> </td> 
   <td> 8<br /> </td> 
  </tr> 
 </tbody> 
</table>

## mailExchange {#mailexchanger}

Estos son los diferentes parámetros del nodo **mailExchange**. Esta es la configuración del servidor SMTP.

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
   <td> Servidor SMTP: Dirección IP del servidor SMTP para la transferencia de correos electrónicos.<br /> </td> 
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

Estos son los diferentes parámetros del nodo **module**. Esta es la configuración del módulo de restricciones de Áreas de nombres xtk.

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
   <td> Área de nombres predeterminada que se usa al crear una nueva entidad.<br /> </td> 
   <td> Cadena<br /> </td> 
   <td> 'cus'<br /> </td> 
  </tr> 
 </tbody> 
</table>

## monitoreo {#monitoring}

Estos son los diferentes parámetros del nodo **monitoreo**. Esta es la configuración del servicio de monitoreo.

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
   <td> Largo<br /> </td> 
   <td> 3600<br /> </td> 
  </tr> 
  <tr> 
   <td> unixScript<br /> </td> 
   <td> La secuencia de comandos Unix ejecutada por el servicio de supervisión.<br /> </td> 
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

Estos son los diferentes parámetros del nodo **ooconv**. Ésta es la configuración del servidor de conversión de documento.

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
   <td> Número máximo de conversiones que un servidor OpenOffice puede realizar. Más allá de este número, se reinicia el servidor.<br /> </td> 
   <td> Largo<br /> </td> 
   <td> 1000<br /> </td> 
  </tr> 
  <tr> 
   <td> maxServerIdleSec<br /> </td> 
   <td> Tiempo máximo de inactividad del servidor OpenOffice antes de forzar el cierre.<br /> </td> 
   <td> Largo<br /> </td> 
   <td> 7200<br /> </td> 
  </tr> 
  <tr> 
   <td> portRange<br /> </td> 
   <td> Intervalo de puertos en los que los servidores OpenOffice están escuchando.<br /> </td> 
   <td> Cadena<br /> </td> 
   <td> 8101-8110<br /> </td> 
  </tr> 
  <tr> 
   <td> url<br /> </td> 
   <td> Dirección URL del servidor de conversión de documento.<br /> </td> 
   <td> Cadena<br /> </td> 
   <td> 'http://localhost:8080/nl/jsp/ooconv.jsp'<br /> </td> 
  </tr> 
 </tbody> 
</table>

## proxyConfig {#proxyconfig}

Estos son los diferentes parámetros del nodo **proxyConfig**. Esta es la configuración de los parámetros proxy.

Para obtener más información, consulte [Configuración de conexión proxy](../../installation/using/configuring-campaign-server.md#proxy-connection-configuration).

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
   <td> enabled<br /> </td> 
   <td> Usar un servidor proxy.<br /> </td> 
   <td> Boolean<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> override<br /> </td> 
   <td> Excepciones: lista de direcciones para las que se deben ignorar los parámetros proxy.<br /> </td> 
   <td> Cadena<br /> </td> 
   <td> 'localhost*' <br /> </td> 
  </tr> 
  <tr> 
   <td> useSingleProxy<br /> </td> 
   <td> Servidor proxy único: use la misma configuración para todos los tipos de proxy.<br /> </td> 
   <td> Boolean<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
 </tbody> 
</table>

### Proxy HTTP / Proxy seguro {#http-proxy---secure-proxy-}

En el nodo **proxyConfig > proxy HTTP / proxy seguro**, configure los parámetros siguientes.

Para obtener más información, consulte [Configuración de conexión proxy](../../installation/using/configuring-campaign-server.md#proxy-connection-configuration).

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
   <td> address<br /> </td> 
   <td> Dirección del servidor proxy<br /> </td> 
   <td> Cadena<br /> </td> 
  </tr> 
  <tr> 
   <td> login<br /> </td> 
   <td> Inicie sesión para la conexión con el servidor proxy<br /> </td> 
   <td> Cadena<br /> </td> 
  </tr> 
  <tr> 
   <td> password<br /> </td> 
   <td> Contraseña para la conexión con el servidor proxy<br /> </td> 
   <td> Cadena<br /> </td> 
  </tr> 
  <tr> 
   <td> puerto<br /> </td> 
   <td> Puerto del servidor proxy<br /> </td> 
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
   <td> Número máximo de subprocesos en el grupo. <br /> </td> 
   <td> Largo<br /> </td> 
   <td> 10<br /> </td> 
  </tr> 
 </tbody> 
</table>

## urlPermission {#urlpermission}

Estos son los diferentes parámetros del nodo **urlPermission**. Esta es la lista de direcciones URL a las que puede acceder el código Javascript.

Lista de dominios y expresiones regulares que especifican si el servidor de Adobe Campaign puede o no utilizar una URL encontrada en el código Javascript.

Si no se encuentra la dirección URL, la acción predeterminada se realiza de acuerdo con el modo predeterminado especificado.

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
   <td> action<br /> </td> 
   <td> Acción predeterminada si la dirección URL no está en la lista autorizada (lista desglosada). Los valores posibles son 'ignore' (autorizar sin mensaje de advertencia, esto requiere deshabilitar la protección), 'warning' (autorizar y emitir un mensaje de advertencia) y 'bold' (prohibir el acceso a la dirección URL).<br /> </td> 
   <td> Cadena<br /> </td> 
   <td> negar<br /> </td> 
  </tr> 
  <tr> 
   <td> debugTrace<br /> </td> 
   <td> Seguimiento de depuración del mecanismo de selección de URL: emite mensajes adicionales durante el proceso de verificación de la dirección URL.<br /> </td> 
   <td> Boolean<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
 </tbody> 
</table>

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
   <td> Nombre de dominio, o dominio principal, al que afecta la dirección URL: todo o parte del dominio de la dirección URL para verificar, para acelerar la verificación. La dirección URL solo se comprueba con respecto a la expresión regular si su dominio contiene dsnSuffix.<br /> </td> 
   <td> Cadena<br /> </td> 
  </tr> 
  <tr> 
   <td> urlRegEx<br /> </td> 
   <td> Expresión regular para refinar las URL de validación que pertenecen a este dominio: expresión regular que debe comprobar la dirección URL, en caso de que corresponda a dnsSuffix.<br /> </td> 
   <td> Cadena<br /> </td> 
  </tr> 
 </tbody> 
</table>

Si un registro satisface **dnsSuffix** pero no **urlRegEx**, se examina el siguiente registro.

Por ejemplo, para autorizar el acceso a todas las direcciones URL del dominio business.com, podemos definir dos registros:

dnsSuffix=&quot;business.com&quot; urlRegEx=&quot;http://.*&quot;

y

dnsSuffix=&quot;business.com&quot; urlRegEx=&quot;https://.*&quot;

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
<url dnsSuffix="deliverability.neolane.net"              urlRegEx="https://deliverability.neolane.net/jssp/dm/renderingSeed.jssp" />
<url dnsSuffix="deliverability.neolane.net"              urlRegEx="https://deliverability.neolane.net/nl/jsp/soaprouter.jsp" />
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
   <td> Período de actualización del estado de memoria del procesamiento del servidor (en ms).<br /> </td> 
   <td> Largo<br /> </td> 
   <td> 500<br /> </td> 
  </tr> 
 </tbody> 
</table>

## archivando {#archiving}

Estos son los diferentes parámetros del nodo **archiving**. Ésta es la configuración de las operaciones de archivado ejecutadas en segundo plano.

Para obtener más información, consulte [Activación del archivado de correo electrónico (in situ)](../../installation/using/email-archiving.md#activating-email-archiving--on-premise-).

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
   <td> Número de direcciones URL que se procesarán al mismo tiempo<br /> </td> 
   <td> Largo<br /> </td> 
   <td> 100<br /> </td> 
  </tr> 
  <tr> 
   <td> archiveType<br /> </td> 
   <td> Estrategia de archivado de mensajes enviados (lista desglosada). Los valores posibles son '0' (sin archivar) y '1' (transfiere el archivado de mensajes enviados a un servidor SMTP).<br /> </td> 
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
   <td> Boolean<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> compressBatchSize<br /> </td> 
   <td> Tamaño de un archivo comprimido: número máximo de archivos en un archivo comprimido.<br /> </td> 
   <td> Largo<br /> </td> 
   <td> 10000<br /> </td> 
  </tr> 
  <tr> 
   <td> compressionFormat<br /> </td> 
   <td> Formato de compresión utilizado durante el archivado (lista desglosada). Los valores posibles son '0' (sin compresión) y '1' (comprimir los mensajes enviados con formato zip).<br /> </td> 
   <td> Byte<br /> </td> 
   <td> 1<br /> </td> 
  </tr> 
  <tr> 
   <td> expirationDelay<br /> </td> 
   <td> Retraso antes del archivado automático de correos electrónicos no procesados: cantidad de días antes de que se archiven los correos electrónicos sin procesar.<br /> </td> 
   <td> Largo<br /> </td> 
   <td> 2<br /> </td> 
  </tr> 
  <tr> 
   <td> initScript<br /> </td> 
   <td> ID de JavaScript que se ejecutará al iniciar el proceso.<br /> </td> 
   <td> Cadena<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessMemoryAlertMb<br /> </td> 
   <td> Alerta de consumo de memoria: alerta relativa a la cantidad de RAM consumida (en Mb) por un proceso determinado.<br /> </td> 
   <td> Largo<br /> </td> 
   <td> 1800<br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessMemoryWarningMb<br /> </td> 
   <td> Advertencia de consumo de memoria: advertencia sobre la cantidad de RAM consumida (en Mb) por un proceso determinado.<br /> </td> 
   <td> Largo<br /> </td> 
   <td> 1600<br /> </td> 
  </tr> 
  <tr> 
   <td> pollDelay<br /> </td> 
   <td> Retraso (en segundos) entre cada evento de actualización.<br /> </td> 
   <td> Largo<br /> </td> 
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
   <td> Número de días antes de que se eliminen los correos electrónicos sin procesar.<br /> </td> 
   <td> Largo<br /> </td> 
   <td> 7<br /> </td> 
  </tr> 
  <tr> 
   <td> runLevel<br /> </td> 
   <td> Prioridad en el inicio. Los módulos de baja prioridad se inician y se detienen por primera vez. Por lo tanto, el módulo syslogd debe tener la prioridad 0.<br /> </td> 
   <td> Corto<br /> </td> 
   <td> 10<br /> </td> 
  </tr> 
  <tr> 
   <td> smtpBccAddress<br /> </td> 
   <td> Archivando destino de destinatario<br /> </td> 
   <td> Cadena<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> smtpEnableTLS<br /> </td> 
   <td> Activar compatibilidad con SMTPS: activa el envío de correos electrónicos en modo seguro (STARTTLS/SMTPS) cuando se admite en el servidor remoto.<br /> </td> 
   <td> Boolean<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> smtpNbConnection<br /> </td> 
   <td> Número de conexiones al servidor SMTP de archivado.<br /> </td> 
   <td> Largo<br /> </td> 
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
   <td> Largo<br /> </td> 
   <td> 25<br /> </td> 
  </tr> 
 </tbody> 
</table>

## inMail {#inmail}

Estos son los diferentes parámetros del nodo **inMail**. Ésta es la configuración del módulo de administración de correo electrónico entrante.

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
   <td> Boolean<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> checkInstanceName<br /> </td> 
   <td> Verificar nombre de instancia: si el valor es true, el nombre de la instancia de Adobe Campaign contenida en los encabezados de ID de mensaje debe ser el mismo que la instancia actual. <br /> </td> 
   <td> Boolean<br /> </td> 
   <td> true<br /> </td> 
  </tr> 
  <tr> 
   <td> defaultForwardAddress<br /> </td> 
   <td> Dirección de reenvío: una regla no procesó la dirección de transferencia de correo electrónico predeterminada. <br /> </td> 
   <td> Cadena<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> errorForwardAddress<br /> </td> 
   <td> Dirección de errores: dirección predeterminada utilizada para transferir correos electrónicos no válidos (codificación MIME incorrecta). <br /> </td> 
   <td> Cadena<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> ignoreSize<br /> </td> 
   <td> Ignorar tamaño del mensaje: se utiliza para ignorar el tamaño de un mensaje devuelto por los servidores POP3. En este caso, el módulo espera un '.' al final de los mensajes. <br /> </td> 
   <td> Boolean<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> inMailPeriodSec<br /> </td> 
   <td> Período de lectura del mensaje: frecuencia de sondeo de la cola de mensajes.<br /> </td> 
   <td> Largo<br /> </td> 
   <td> 5<br /> </td> 
  </tr> 
  <tr> 
   <td> initScript<br /> </td> 
   <td> ID de JavaScript que se ejecutará al iniciar el proceso.<br /> </td> 
   <td> Cadena<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> maxBroadLog<br /> </td> 
   <td> Número máximo de registros para actualizar: define el número máximo de mensajes de registro que se guardarán en la memoria antes de actualizar la base de datos.<br /> </td> 
   <td> Largo<br /> </td> 
   <td> 20<br /> </td> 
  </tr> 
  <tr> 
   <td> maxMsgPerSession<br /> </td> 
   <td> Número máximo de mensajes para leer durante la sesión POP3.<br /> </td> 
   <td> Largo<br /> </td> 
   <td> 200<br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessMemoryAlertMb<br /> </td> 
   <td> Alerta de consumo de memoria: alerta relativa a la cantidad de RAM consumida (en Mb) por un proceso determinado.<br /> </td> 
   <td> Largo<br /> </td> 
   <td> 1800<br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessMemoryWarningMb<br /> </td> 
   <td> Advertencia de consumo de memoria: advertencia sobre la cantidad de RAM consumida (en Mb) por un proceso determinado.<br /> </td> 
   <td> Largo<br /> </td> 
   <td> 1600<br /> </td> 
  </tr> 
  <tr> 
   <td> maxSessionTTLSec<br /> </td> 
   <td> Duración de la sesión: duración máxima de la sesión de procesamiento de mensajes.<br /> </td> 
   <td> Largo<br /> </td> 
   <td> 100<br /> </td> 
  </tr> 
  <tr> 
   <td> popMailPeriodSec<br /> </td> 
   <td> Período de sondeo POP3<br /> </td> 
   <td> Largo<br /> </td> 
   <td> 300<br /> </td> 
  </tr> 
  <tr> 
   <td> popQueueSize<br /> </td> 
   <td> Tamaño de cola de mensajes leídos<br /> </td> 
   <td> Largo<br /> </td> 
   <td> 100<br /> </td> 
  </tr> 
  <tr> 
   <td> popTimeoutSec<br /> </td> 
   <td> Tiempo de espera de comunicación con el servidor POP3. <br /> </td> 
   <td> Largo<br /> </td> 
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
   <td> Frecuencia de recarga de base de datos de las cuentas que se van a sondear.<br /> </td> 
   <td> Largo<br /> </td> 
   <td> 600<br /> </td> 
  </tr> 
  <tr> 
   <td> runLevel<br /> </td> 
   <td> Prioridad en el inicio. Los módulos de baja prioridad se inician y se detienen por primera vez. Por lo tanto, el módulo syslogd debe tener la prioridad 0.<br /> </td> 
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
   <td> dump<br /> </td> 
   <td> Guarde todos los mensajes entrantes en formato de texto. <br /> </td> 
   <td> Boolean<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> msgPath<br /> </td> 
   <td> Ruta de volcado de mensajes.<br /> </td> 
   <td> Cadena<br /> </td> 
   <td> '/tmp/inMail'<br /> </td> 
  </tr> 
 </tbody> 
</table>

## interactiond {#interactiond}

Estos son los diferentes parámetros del nodo **interactiond**. Esta es la configuración del demonio de escritura para eventos de interacción entrantes.

Para obtener más información, consulte [Interacción - Búfer de datos](../../installation/using/interaction---data-buffer.md).

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
   <td> Boolean<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> callDataSize<br /> </td> 
   <td> Máx. número de caracteres almacenados en la memoria compartida para los datos de llamada.<br /> </td> 
   <td> Largo<br /> </td> 
   <td> 0<br /> </td> 
  </tr> 
  <tr> 
   <td> initScript<br /> </td> 
   <td> ID de JavaScript que se ejecutará al iniciar el proceso<br /> </td> 
   <td> Cadena<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessMemoryAlertMb<br /> </td> 
   <td> Alerta de consumo de memoria: alerta relativa a la cantidad de RAM consumida (en Mb) por un proceso determinado.<br /> </td> 
   <td> Largo<br /> </td> 
   <td> 1800<br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessMemoryWarningMb<br /> </td> 
   <td> Advertencia de consumo de memoria: advertencia sobre la cantidad de RAM consumida (en Mb) por un proceso determinado.<br /> </td> 
   <td> Largo<br /> </td> 
   <td> 1600<br /> </td> 
  </tr> 
  <tr> 
   <td> maxSharedEntries<br /> </td> 
   <td> Máx. número de eventos almacenados en la memoria compartida.<br /> </td> 
   <td> Largo<br /> </td> 
   <td> 25000<br /> </td> 
  </tr> 
  <tr> 
   <td> nextOffersSize<br /> </td> 
   <td> Número máximo de ofertas elegibles ordenadas justo después de las proposiciones, que se almacenarán para las estadísticas.<br /> </td> 
   <td> Largo<br /> </td> 
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
   <td> Prioridad en el inicio. Los módulos de baja prioridad se inician y se detienen por primera vez. Por lo tanto, el módulo syslogd debe tener la prioridad 0.<br /> </td> 
   <td> Corto<br /> </td> 
   <td> 10<br /> </td> 
  </tr> 
  <tr> 
   <td> statsPeriod<br /> </td> 
   <td> Duración de agregación en segundos para las estadísticas de tiempo de respuesta. 0 significa que el almacenamiento estadístico se desactivó.<br /> </td> 
   <td> Largo<br /> </td> 
   <td> 600<br /> </td> 
  </tr> 
  <tr> 
   <td> targetKeySize<br /> </td> 
   <td> Máx. número de caracteres almacenados en la memoria compartida para identificar individuos.<br /> </td> 
   <td> Largo<br /> </td> 
   <td> 16<br /> </td> 
  </tr> 
 </tbody> 
</table>

## mta {#mta}

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
   <td> Boolean<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> dataLogPath<br /> </td> 
   <td> Guardar ruta de correo electrónico enviado: si no está vacío, se guardará la ruta donde se guardarán todos los archivos de origen de los mensajes de correo electrónico enviados. <br /> </td> 
   <td> Cadena<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> debugPath<br /> </td> 
   <td> Directorio de volcado:iSi no está vacío, copie los sobres MIME de los mensajes de correo enviados en este directorio. Se usa para la resolución de problemas. <br /> </td> 
   <td> Cadena<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> dnsRequestLogDelayMs<br /> </td> 
   <td> Retraso de registros de consulta DNS: tiempo en milisegundos para mostrar los registros.<br /> </td> 
   <td> Largo<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> errorPeriodSec<br /> </td> 
   <td> Frecuencia de las estadísticas de errores: tiempo entre la generación de estadísticas y el almacenamiento en la base de datos. <br /> </td> 
   <td> Largo<br /> </td> 
   <td> 300<br /> </td> 
  </tr> 
  <tr> 
   <td> initScript<br /> </td> 
   <td> ID de JavaScript que se ejecutará al iniciar el proceso.<br /> </td> 
   <td> Cadena<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> logEmailErrors<br /> </td> 
   <td> Genere estadísticas de errores y guárdelas en la base de datos.<br /> </td> 
   <td> Boolean<br /> </td> 
   <td> true<br /> </td> 
  </tr> 
  <tr> 
   <td> logLevel<br /> </td> 
   <td> Mostrar nivel de mensajes de registro. Nivel de gravedad de los registros escritos en la base de datos. Los mensajes de registro generados por MTA no siempre se escriben en la base de datos. Con este parámetro, puede definir el nivel desde el que considera que un mensaje debe escribirse en la base de datos. Si define el nivel 2, también se escribirán los mensajes de los niveles 1 y 0, mientras que si define el nivel 1, solo se escribirán los mensajes de los niveles 1 y 0. Los valores posibles son: 0 (errores), 1 (advertencia), 2 (información)<br /> </td> 
   <td> Largo<br /> </td> 
   <td> 2<br /> </td> 
  </tr> 
  <tr> 
   <td> maxMemoryMb<br /> </td> 
   <td> Tamaño máximo de memoria (en MB) que puede utilizar un proceso de metadatos. Por encima de este límite, el proceso se reinicia para que la memoria que utiliza se libere al sistema.<br /> </td> 
   <td> Largo<br /> </td> 
   <td> 1024<br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessMemoryAlertMb<br /> </td> 
   <td> Alerta de consumo de memoria: alerta relativa a la cantidad de RAM consumida (en Mb) por un proceso determinado.<br /> </td> 
   <td> Largo<br /> </td> 
   <td> 1800<br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessMemoryWarningMb<br /> </td> 
   <td> Advertencia de consumo de memoria: advertencia sobre la cantidad de RAM consumida (en Mb) por un proceso determinado.<br /> </td> 
   <td> Largo<br /> </td> 
   <td> 1600<br /> </td> 
  </tr> 
  <tr> 
   <td> minConnectionsToLog<br /> </td> 
   <td> Umbral de conexión que se debe tener en cuenta. No se generan estadísticas de errores para una ruta determinada si el número total de conexiones para el período especificado por errorPeriodSec es estrictamente menor que el umbral.<br /> </td> 
   <td> Largo<br /> </td> 
   <td> 100<br /> </td> 
  </tr> 
  <tr> 
   <td> minErrorsToLog<br /> </td> 
   <td> Umbral de error que se debe tener en cuenta: no se generan estadísticas de errores para una ruta determinada si el número total de errores para el período especificado por errorPeriodSec es estrictamente menor que el umbral.<br /> </td> 
   <td> Largo<br /> </td> 
   <td> 1<br /> </td> 
  </tr> 
  <tr> 
   <td> minMessagesToLog<br /> </td> 
   <td> Umbral de mensaje que se debe tener en cuenta. No se generan estadísticas de errores para una ruta determinada si el número total de mensajes enviados para el período especificado por errorPeriodSec es estrictamente inferior al umbral.<br /> </td> 
   <td> Largo<br /> </td> 
   <td> 1000<br /> </td> 
  </tr> 
  <tr> 
   <td> notifRelay<br /> </td> 
   <td> Relé de notificaciones: HostName:puerto utilizado para retransmitir notificaciones.<br /> </td> 
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
   <td> Retraso antes de que se eliminen los correos electrónicos archivados: número de días antes de que se purguen los correos electrónicos archivados en el directorio especificado en dataLogPath.<br /> </td> 
   <td> Largo<br /> </td> 
   <td> 15<br /> </td> 
  </tr> 
  <tr> 
   <td> reintentarLostMessages<br /> </td> 
   <td> Reintentar mensajes perdidos: partes de envíos se reintentarán si el proceso secundario está muerto.<br /> </td> 
   <td> Boolean<br /> </td> 
   <td> true<br /> </td> 
  </tr> 
  <tr> 
   <td> runLevel<br /> </td> 
   <td> Prioridad en el inicio. Los módulos de baja prioridad se inician y se detienen por primera vez. Por lo tanto, el módulo syslogd debe tener la prioridad 0.<br /> </td> 
   <td> Corto<br /> </td> 
   <td> 10<br /> </td> 
  </tr> 
  <tr> 
   <td> signEmailLinks<br /> </td> 
   <td> Habilite el mecanismo de firma. Esto mejora la seguridad de los vínculos de seguimiento en el correo electrónico.<br /> </td> 
   <td> Boolean<br /> </td> 
   <td> true<br /> </td> 
  </tr>
  <tr> 
   <td> statServerAddress<br /> </td> 
   <td> Dirección del servidor de estadísticas de envío, dada como 
    &lt;dns o ip&gt; 
      <code>[</code>: 
     &lt;puerto&gt; 
       <code>]</code>. Consulte 
      <a href="../../installation/using/email-deliverability.md#coordinates-of-the-statistics-server" target="_blank">Coordenadas del servidor de estadísticas</a>. 
      <br /> 
     </td> 
   <td> Cadena<br /> </td> 
   <td> Si no se define, el puerto predeterminado es 7777.<br /> </td> 
  </tr> 
  <tr> 
   <td> statServerTLSSupport<br /> </td> 
   <td> Habilitar TLS por dominio: habilita el TLS configurable por MX (requiere un servidor de estadísticas actualizado).<br /> </td> 
   <td> Boolean<br /> </td> 
   <td> true <br /> </td> 
  </tr> 
  <tr> 
   <td> statServerVersion<br /> </td> 
   <td> Versión de protocolo utilizada: versión del protocolo de comunicación (1 para un servidor v5.11 y 6.0.2, 2 para un servidor v6.1).<br /> </td> 
   <td> Cadena<br /> </td> 
   <td> Si no está definida, se utiliza la versión más reciente. <br /> </td> 
  </tr> 
  <tr> 
   <td> useMomentum<br /> </td> 
   <td> Si se establece en "true", la instancia utiliza el <a href="../../delivery/using/sending-with-enhanced-mta.md" target="_blank">MTA mejorado</a>.<br /> </td> 
   <td> Boolean<br /> </td> 
   <td> <br /> </td>b 
  </tr>
  <tr> 
   <td> verifyMode<br /> </td> 
   <td> Modo de verificación: activa el modo de verificación (sin transmisión física de mensajes; se usa para simulación y pruebas).<br /> </td> 
   <td> Boolean<br /> </td> 
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
   <td> Campo X-Mailer: valor del campo 'X-Mailer' en el encabezado de correo SMTP.<br /> </td> 
   <td> Cadena<br /> </td> 
   <td> 'nlserver, Build $(PRODUCT_VERSION)'<br /> </td> 
  </tr>  
 </tbody> 
</table>

### cache {#cache}

En el nodo **cache**, configure los siguientes parámetros. Ésta es la configuración de la caché de archivos local.

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
   <td> Reciclado después de: punto, expresado en segundos, después del cual el archivo se elimina automáticamente de la caché para recuperar el almacenamiento.<br /> </td> 
   <td> Largo<br /> </td> 
   <td> 244800<br /> </td> 
  </tr> 
  <tr> 
   <td> maxSizeOnDiskMb<br /> </td> 
   <td> Tamaño máximo de caché (Mb).<br /> </td> 
   <td> Largo<br /> </td> 
   <td> 1024<br /> </td> 
  </tr> 
  <tr> 
   <td> purgePeriodSec<br /> </td> 
   <td> Frecuencia de purga: período en segundos entre ejecuciones del mecanismo de depuración de caché.<br /> </td> 
   <td> Largo<br /> </td> 
   <td> 3600<br /> </td> 
  </tr> 
 </tbody> 
</table>

### relé {#relay}

En el nodo **mta > relay**, configure los siguientes parámetros. Ésta es la configuración del servidor de correo para el envío de mensajes.

Para obtener más información, consulte [retransmisión SMTP](../../installation/using/configuring-campaign-server.md#smtp-relay).

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
   <td> address<br /> </td> 
   <td> Lista separada por comas de nombres DNS o direcciones IP de retransmisiones SMTP que se van a utilizar. <br /> </td> 
   <td> Cadena<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> puerto<br /> </td> 
   <td> Puerto IP del servidor SMTP.<br /> </td> 
   <td> Largo<br /> </td> 
   <td> 25<br /> </td> 
  </tr> 
 </tbody> 
</table>

### master {#master}

En el nodo **mta > master**, configure los parámetros siguientes. Ésta es la configuración del servidor principal.

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
   <td> Frecuencia de sondeo de la base de datos de los trabajos que se van a entregar. Este valor indica la frecuencia de sondeo de la base de datos (en segundos). Para obtener la lista de trabajos en espera de envío, el MTA sondea la base de datos de manera regular. Cuando no hay trabajo en espera, el período de sondeo se define por este valor. De lo contrario, si se ha transferido un trabajo a un servidor secundario, la duración de la encuesta se reduce automáticamente a un segundo para que se pueda volver a procesar un nuevo trabajo lo antes posible, es decir, tan pronto como vuelva a estar disponible un servidor secundario. Esto no significa que la consulta de la base de datos se realizará cada segundo hasta que se vuelva a disponer de un servidor secundario. De hecho, el acceso a la base de datos solo se realiza cuando al menos un servidor secundario está disponible.<br /> </td> 
   <td> Largo<br /> </td> 
   <td> 30<br /> </td> 
  </tr> 
  <tr> 
   <td> dataBaseRetryDelaySec<br /> </td> 
   <td> Período de espera tras un error de conexión a la base de datos. El propio servidor de base de datos suele provocar un error de conexión a la base de datos. El servidor también se puede detener por motivos de mantenimiento, por ejemplo. El parámetro DataBaseRetryDelay define la duración entre dos intentos de conexión en caso de error de conexión a la base de datos.<br /> </td> 
   <td> Largo<br /> </td> 
   <td> 60<br /> </td> 
  </tr> 
  <tr> 
   <td> domainKeysReloadPeriodSec<br /> </td> 
   <td> Período de validez para la caché de claves privadas (DomainKeys). Las claves privadas utilizadas para firmar correos electrónicos siguiendo la recomendación DomainKeys (http://antispam.yahoo.com/domainkeys) se almacenan como opciones en la base de datos. El parámetro domainKeysReloadPeriodSec define cuántos segundos el MTA puede mantener estas claves en una caché. Después de este retraso, todas las claves deben volver a cargarse desde la base de datos.<br /> </td> 
   <td> Largo<br /> </td> 
   <td> 600<br /> </td> 
  </tr> 
  <tr> 
   <td> maxSpareServers<br /> </td> 
   <td> Número máximo de servidores secundarios. Representa el número máximo de servidores en ejecución. Se recomienda limitar este número a un nivel óptimo compatible con los recursos de memoria del servidor. Esto se puede comprobar durante un envío. La memoria usada no debe superar un tercio de la memoria física disponible de lo contrario se utilizará el intercambio. Consulte <a href="../../installation/using/configuring-campaign-server.md#mta-child-processes" target="_blank">Procesos secundarios de MTA</a>.<br /> </td> 
   <td> Largo<br /> </td> 
   <td> 2<br /> </td> 
  </tr> 
  <tr> 
   <td> minSpareServers<br /> </td> 
   <td> Número mínimo de servidores secundarios. El MTA intenta mantener al menos este número de servidores en ejecución. Si hay menos, reinicia los nuevos servidores cada segundo hasta que se alcance este valor.<br /> </td> 
   <td> Largo<br /> </td> 
   <td> 0<br /> </td> 
  </tr> 
  <tr> 
   <td> startSpareServers<br /> </td> 
   <td> Número de servidores secundarios en el inicio. Se supervisa dinámicamente el número de servidores secundarios; cuando el MTA inicio, crea tantos servidores secundarios como se indica en este valor. Normalmente, los servidores secundarios no se pueden iniciar más rápido que un servidor por segundo para guardar los recursos del host. Sin embargo, cuando se usan los inicios MTA, esta limitación se invalida para que los servidores secundarios estén disponibles lo antes posible.<br /> </td> 
   <td> Largo<br /> </td> 
   <td> 0<br /> </td> 
  </tr> 
 </tbody> 
</table>

### child {#child}

En el nodo **mta > child**, configure los parámetros siguientes. Esta es la configuración de los servidores secundarios.

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
   <td> Argumentos opcionales de la línea de comandos <br /> </td> 
   <td> Cadena<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> inactiveChildTimeoutSec<br /> </td> 
   <td> Tiempo de espera hasta que se detengan los servidores secundarios inactivos. Si un servidor secundario tiene un tiempo de inactividad bueno que este parámetro, se matará automáticamente para liberar recursos de host.<br /> </td> 
   <td> Largo<br /> </td> 
   <td> 60<br /> </td> 
  </tr> 
  <tr> 
   <td> maxAgeSec<br /> </td> 
   <td> Tiempo máximo de retención de mensajes. Si no se pudo enviar un mensaje preparado debido a la limitación o no se pudo conectar con el MTA de destinatario, el mensaje se abandona y se procesará en el siguiente reintento.<br /> </td> 
   <td> Largo<br /> </td> 
   <td> 600<br /> </td> 
  </tr> 
  <tr> 
   <td> maxGCMConnectPerChild<br /> </td> 
   <td> Número máximo de solicitudes Http paralelas al FCM iniciadas por cada servidor secundario.<br /> </td> 
   <td> Largo<br /> </td> 
   <td> 8<br /> </td> 
  </tr> 
  <tr> 
   <td> maxMsgPerChild<br /> </td> 
   <td> Número máximo de mensajes por servidor secundario. Cada elemento secundario de MTA procesa este número de mensajes y muere. Es importante especificar un número tal que las fugas de memoria o de recursos en el MTA sean inofensivas (por lo general, unos pocos miles). Incluso si no hay fugas de memoria conocidas en el código MTA, los motores JavaScript y XSL incrustados no son totalmente fiables.<br /> </td> 
   <td> Largo<br /> </td> 
   <td> 5000000<br /> </td> 
  </tr> 
  <tr> 
   <td> maxWaitingMessages<br /> </td> 
   <td> Mensajes pendientes: número máximo de mensajes en espera de entrega en memoria. <br /> </td> 
   <td> Largo<br /> </td> 
   <td> 2000<br /> </td> 
  </tr> 
  <tr> 
   <td> maxWorkingSetMb<br /> </td> 
   <td> Tamaño máximo de memoria (en MB) que puede utilizar un proceso secundario. Por encima de este límite, el proceso se detiene para que la memoria que utiliza se libere al sistema. <br /> </td> 
   <td> Largo<br /> </td> 
   <td> 128<br /> </td> 
  </tr> 
  <tr> 
   <td> soapConnectorTimeoutSec<br /> </td> 
   <td> Tiempo de espera (en segundos) después del cual se abandona una conexión SOAP para un conector de envío.<br /> </td> 
   <td> Largo<br /> </td> 
   <td> 600<br /> </td> 
  </tr> 
  <tr> 
   <td> startWithFirstMX<br /> </td> 
   <td> Inicio siempre con la prioridad MX más alta.<br /> </td> 
   <td> Boolean<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> timeToLive<br /> </td> 
   <td> Número máximo de intentos consecutivos al reanudarse.<br /> </td> 
   <td> Largo<br /> </td> 
   <td> 48<br /> </td> 
  </tr> 
 </tbody> 
</table>

En el nodo **mta > child > smtp**, configure los siguientes parámetros. Esta es la configuración de las sesiones SMTP.

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
   <td> Activa el envío de correos electrónicos en modo seguro (STARTTLS/SMTPS) cuando se admite en el servidor remoto.<br /> </td> 
   <td> Boolean<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> inactiveSessionTimeoutSec<br /> </td> 
   <td> Tiempo de espera de sesión inactiva. Este parámetro solo se utiliza si la sesión se reutiliza para transmitir varios mensajes a un dominio determinado. Cuando el MTA ha completado la transmisión del mensaje, la sesión SMTP que ha utilizado no se cierra sistemáticamente. Si un mensaje está listo para enviarse para este mismo dominio, se reutilizará la misma sesión SMTP y por este motivo la sesión no se cerrará automáticamente. El parámetro IdleSessionTimeout permite definir el tiempo durante el cual una sesión SMTP puede permanecer activa esperando otro mensaje. Una vez transcurrida la duración, la sesión se cierra automáticamente.<br /> </td> 
   <td> Largo<br /> </td> 
   <td> 5<br /> </td> 
  </tr> 
  <tr> 
   <td> initialDelaySec<br /> </td> 
   <td> Retraso inicial antes de volver a intentar la conexión. Este retraso se duplica cada vez que falla la conexión.<br /> </td> 
   <td> Largo<br /> </td> 
   <td> 4<br /> </td> 
  </tr> 
  <tr> 
   <td> maxSessionsPerChild<br /> </td> 
   <td> Número máximo de sesiones SMTP por servidor secundario. Para enviar un mensaje, el MTA inicializa una conexión SMTP con el MTA de destinatario. El número máximo de sesiones SMTP simultáneas y activas para un servidor secundario determinado está limitado por este valor. Si multiplica este valor por maxSpareServers, obtendrá el número máximo de mensajes que un servidor secundario determinado puede procesar simultáneamente.<br /> </td> 
   <td> Largo<br /> </td> 
   <td> 1000<br /> </td> 
  </tr> 
 </tbody> 
</table>

En el nodo **mta > child > smtp > IPAffinity**, configure los siguientes parámetros. Esta es la configuración de la administración de afinidades con direcciones IP para el tráfico SMTP saliente optimizado.

Para obtener más información, consulte [Lista de direcciones IP para utilizar](../../installation/using/email-deliverability.md#list-of-ip-addresses-to-use) y [Administración del tráfico SMTP saliente con afinidades](../../installation/using/configuring-campaign-server.md#managing-outbound-smtp-traffic-with-affinities).

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
   <td> Nombre de dominio: nombre de dominio local vinculado a la dirección IP. Se utiliza al emitir un comando SMTP HELO.<br /> </td> 
   <td> Cadena<br /> </td> 
  </tr> 
  <tr> 
   <td> name<br /> </td> 
   <td> Nombre lógico: nombres vinculados a la afinidad por los usuarios. Los nombres se separan con punto y coma;<br /> </td> 
   <td> Cadena<br /> </td> 
  </tr> 
 </tbody> 
</table>

En el nodo **mta > child > smtp > IP**, configure los siguientes parámetros.

Para obtener más información, consulte [Lista de direcciones IP para usar](../../installation/using/email-deliverability.md#list-of-ip-addresses-to-use).

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
   <td> address<br /> </td> 
   <td> Dirección física asociada. Por ejemplo: '192.168.0.1'<br /> </td> 
   <td> Cadena<br /> </td> 
  </tr> 
  <tr> 
   <td> publicId<br /> </td> 
   <td> ID de dirección pública asociada. Se utiliza como clave para el servidor de estadísticas. Debe ser numérico. Consulte esta <a href="../../installation/using/email-deliverability.md#managing-ip-addresses">sección</a>.<br /> </td> 
   <td> Largo<br /> </td> 
  </tr> 
  <tr> 
   <td> ponderación<br /> </td> 
   <td> Especifica la frecuencia de uso para esta IP, en relación con otras IP (los pesos mayores producen frecuencias más altas).<br /> </td> 
   <td> Largo<br /> </td> 
  </tr> 
  <tr> 
   <td> includeDomains<br /> </td> 
   <td> Lista separada por comas de las máscaras de dominio para incluir.<br /> </td> 
   <td> Cadena<br /> </td> 
  </tr> 
  <tr> 
   <td> excludeDomains<br /> </td> 
   <td> Lista separada por comas de las máscaras de dominio para excluir.<br /> </td> 
   <td> Cadena<br /> </td> 
  </tr> 
  <tr> 
   <td> heloHost<br /> </td> 
   <td> Nombre del equipo vinculado a la dirección IP. Se utiliza al emitir un comando SMTP HELO.<br /> </td> 
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
   <td> Utilice el proxy HTTP definido en shared/proxyHTTP. <br /> </td> 
   <td> Boolean<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
 </tbody> 
</table>

### relé {#relay-1}

Estos son los diferentes parámetros del nodo **nmac > relay**. Esto configura el uso de un relé para el envío de mensajes (conector ios http2).

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
   <td> address<br /> </td> 
   <td> Dirección DNS o nombre del reenvío que se va a usar. <br /> </td> 
   <td> Cadena<br /> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> puerto<br /> </td> 
   <td> Puerto de retransmisión<br /> </td> 
   <td> Largo<br /> </td> 
   <td> 443<br /> </td> 
  </tr> 
  <tr> 
   <td> TrustedCertsChain<br /> </td> 
   <td> Cadena de certificados (archivo PEM). Útil cuando se utiliza un servidor ficticio.<br /> </td> 
   <td> Cadena<br /> </td> 
   <td> <br /> </td> 
  </tr> 
 </tbody> 
</table>

## canalizado {#pipelined}

Estos son los diferentes parámetros del nodo **canalizado**. Esta es la configuración del módulo de procesamiento de evento para los servicios de tubería.

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
   <td> Nombre de la aplicación generada en la conexión del desarrollador cuando se guarda la clave pública. <br /> </td> 
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
   <td> Clave privada para obtener tokens (cifrada en AES con la opción XtkKey).<br /> </td> 
   <td> Cadena<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> autoStart<br /> </td> 
   <td> Inicio automático <br /> </td> 
   <td> Boolean<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> disableAuth<br /> </td> 
   <td> Deshabilitar autenticación: conectarse a los servicios de canalización sin autenticación. <br /> </td> 
   <td> Boolean<br /> </td> 
   <td> 2<br /> </td> 
  </tr> 
  <tr> 
   <td> discoverPipelineEndpoint<br /> </td> 
   <td> URL para descubrir la dirección URL de los servicios de tubería.<br /> </td> 
   <td> Cadena<br /> </td> 
   <td> 'https://producer-pipeline-pnw.adobe.net'<br /> </td> 
  </tr> 
  <tr> 
   <td> dumpStatePeriodSec<br /> </td> 
   <td> Período de guardado del estado: frecuencia con la que la información interna del proceso se guarda en un archivo. Inactivo si 0. <br /> </td> 
   <td> Largo<br /> </td> 
   <td> 0<br /> </td> 
  </tr> 
  <tr> 
   <td> forcedPipelineEndpoint<br /> </td> 
   <td> URL de escucha: forzar la URL de escucha de los servicios de tubería. <br /> </td> 
   <td> Cadena<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> initScript<br /> </td> 
   <td> ID de JavaScript que se ejecutará al iniciar el proceso.<br /> </td> 
   <td> Cadena<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessMemoryAlertMb<br /> </td> 
   <td> Alerta de consumo de memoria: alerta relativa a la cantidad de RAM consumida (en Mb) por un proceso determinado.<br /> </td> 
   <td> Largo<br /> </td> 
   <td> 1800<br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessMemoryWarningMb<br /> </td> 
   <td> Advertencia de consumo de memoria: advertencia sobre la cantidad de RAM consumida (en Mb) por un proceso determinado.<br /> </td> 
   <td> Largo<br /> </td> 
   <td> 1600<br /> </td> 
  </tr> 
  <tr> 
   <td> monitorServerPort<br /> </td> 
   <td> Puerto del servidor de estado: Puerto del servidor HTTP que permite la consulta del estado del proceso. Inactivo si 0.<br /> </td> 
   <td> Largo<br /> </td> 
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
   <td> Retraso antes de que se almacene el puntero: el puntero se almacenará en la base de datos al menos una vez durante este período (útil en caso de actividad baja).<br /> </td> 
   <td> Largo<br /> </td> 
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
   <td> Número de subprocesos para el procesamiento de eventos con un conector de JavaScript personalizado.<br /> </td> 
   <td> Largo<br /> </td> 
   <td> 4<br /> </td> 
  </tr> 
  <tr> 
   <td> processingThreads<br /> </td> 
   <td> Número de subprocesos para procesamiento de evento.<br /> </td> 
   <td> Largo<br /> </td> 
   <td> 4<br /> </td> 
  </tr> 
  <tr> 
   <td> retryPeriodSec<br /> </td> 
   <td> Retraso entre el procesamiento si hay un error.<br /> </td> 
   <td> Largo<br /> </td> 
   <td> 30<br /> </td> 
  </tr> 
  <tr> 
   <td> retryValiditySec<br /> </td> 
   <td> Abandono después de este período: abandone el evento si el procesamiento sigue fallando después de este período.<br /> </td> 
   <td> Largo<br /> </td> 
   <td> 300<br /> </td> 
  </tr> 
  <tr> 
   <td> runLevel<br /> </td> 
   <td> Prioridad en el inicio. Los módulos de baja prioridad se inician y se detienen por primera vez. Por lo tanto, el módulo syslogd debe tener la prioridad 0.<br /> </td> 
   <td> Corto<br /> </td> 
   <td> 10<br /> </td> 
  </tr> 
 </tbody> 
</table>

## reparar {#repair}

Estos son los diferentes parámetros del nodo **Repair**. Esta es la configuración del módulo de reparación de la base de datos.

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
   <td> RepairActionDelayMin<br /> </td> 
   <td> Módulo de reparación de acciones de envío: retraso (en minutos) tras el cual el módulo de reparación puede procesar las acciones de envío. <br /> </td> 
   <td> Largo<br /> </td> 
   <td> 60<br /> </td> 
  </tr> 
 </tbody> 
</table>

## securityZone {#securityzone}

Estos son los diferentes parámetros del nodo **securityZone**.

Para obtener más información, consulte [Definición de zonas de seguridad](../../installation/using/configuring-campaign-server.md#defining-security-zones).

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
   <td> Autorice el modo de depuración para Aplicaciones web.<br /> </td> 
   <td> Boolean<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> allowEmptyPassword<br /> </td> 
   <td> Autorice al usuario a utilizar la aplicación sin contraseña.<br /> </td> 
   <td> Boolean<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> allowHTTP<br /> </td> 
   <td> Autorice el uso de HTTP para el inicio de sesión del operador.<br /> </td> 
   <td> Boolean<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> allowSQLInjection<br /> </td> 
   <td> Autorice el uso de SQLDATA en expresiones.<br /> </td> 
   <td> Boolean<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> allowUserPassword<br /> </td> 
   <td> Autorice tokens de sesión de usuario/contraseña.<br /> </td> 
   <td> Boolean<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> label<br /> </td> 
   <td> Etiqueta<br /> </td> 
   <td> Cadena<br /> </td> 
   <td> NewLabel()<br /> </td> 
  </tr> 
  <tr> 
   <td> name<br /> </td> 
   <td> Nombre interno<br /> </td> 
   <td> Cadena<br /> </td> 
   <td> NewName() <br /> </td> 
  </tr> 
  <tr> 
   <td> sessionTokenOnly<br /> </td> 
   <td> No utilice el token de seguridad.<br /> </td> 
   <td> Boolean<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> showErrors<br /> </td> 
   <td> Mostrar detalles de error<br /> </td> 
   <td> Boolean<br /> </td> 
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

Para obtener más información, consulte [Definición de zonas de seguridad](../../installation/using/configuring-campaign-server.md#defining-security-zones).

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
   <td> label<br /> </td> 
   <td> Etiqueta<br /> </td> 
   <td> Cadena<br /> </td> 
   <td> NewLabel()<br /> </td> 
  </tr> 
  <tr> 
   <td> mask<br /> </td> 
   <td> Máscara o dirección<br /> </td> 
   <td> Cadena<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> name<br /> </td> 
   <td> Nombre interno<br /> </td> 
   <td> Cadena<br /> </td> 
   <td> NewName() <br /> </td> 
  </tr> 
  <tr> 
   <td> proxy<br /> </td> 
   <td> Máscara o dirección del proxy (inverso) utilizado por esta subred para acceder a la instancia. En este caso, se probará el encabezado 'X-Forwarded-For' en lugar de este proxy.<br /> </td> 
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
   <td> Boolean<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> dataRetentionDays<br /> </td> 
   <td> Número máximo de días que los archivos de trabajo conservan el conector SMPP.<br /> </td> 
   <td> Largo<br /> </td> 
   <td> 60<br /> </td> 
  </tr> 
  <tr> 
   <td> dataSizeMo<br /> </td> 
   <td> Tamaño máximo en MB de los archivos de trabajo de SMPP.<br /> </td> 
   <td> Largo<br /> </td> 
   <td> 512<br /> </td> 
  </tr> 
  <tr> 
   <td> initScript<br /> </td> 
   <td> ID de JavaScript que se ejecutará al iniciar el proceso.<br /> </td> 
   <td> Cadena<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> keepAlivePeriod<br /> </td> 
   <td> Periodicidad del marco de continuidad de la sesión: máx. período en segundos entre dos fotogramas para notificar que la sesión de recepción sigue habilitada.<br /> </td> 
   <td> Largo<br /> </td> 
   <td> 25<br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessMemoryAlertMb<br /> </td> 
   <td> Alerta de consumo de memoria: alerta relativa a la cantidad de RAM consumida (en Mb) por un proceso determinado.<br /> </td> 
   <td> Largo<br /> </td> 
   <td> 1800<br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessMemoryWarningMb<br /> </td> 
   <td> Advertencia de consumo de memoria: advertencia sobre la cantidad de RAM consumida (en Mb) por un proceso determinado.<br /> </td> 
   <td> Largo<br /> </td> 
   <td> 1600<br /> </td> 
  </tr> 
  <tr> 
   <td> pollPeriod<br /> </td> 
   <td> Frecuencia de búsqueda: Período de encuesta de la cuenta SMS.<br /> </td> 
   <td> Largo<br /> </td> 
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
   <td> Frecuencia de recarga de cuenta: frecuencia de recarga de base de datos de las cuentas que se van a sondear.<br /> </td> 
   <td> Largo<br /> </td> 
   <td> 600<br /> </td> 
  </tr> 
  <tr> 
   <td> runLevel<br /> </td> 
   <td> Prioridad en el inicio. Los módulos de baja prioridad se inician y se detienen por primera vez. Por lo tanto, el módulo syslogd debe tener la prioridad 0.<br /> </td> 
   <td> Corto<br /> </td> 
   <td> 10<br /> </td> 
  </tr> 
  <tr> 
   <td> srReadDelay<br /> </td> 
   <td> Número de segundos de retraso en el procesamiento de SR: sólo los SR con una fecha de recuperación anterior a la hora actual menos la duración en segundos proporcionada por srReadDelay. <br /> </td> 
   <td> Largo<br /> </td> 
   <td> 600<br /> </td> 
  </tr> 
  <tr> 
   <td> timeout<br /> </td> 
   <td> Tiempo de espera de comunicación con la puerta de enlace SMS.<br /> </td> 
   <td> Largo<br /> </td> 
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
   <td> Largo<br /> </td> 
   <td> 30<br /> </td> 
  </tr> 
 </tbody> 
</table>

## stat {#stat}

Estos son los diferentes parámetros del nodo **stat**. Ésta es la configuración del módulo de estadísticas de MTA.

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
   <td> Boolean<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> initScript<br /> </td> 
   <td> ID de JavaScript que se ejecutará al iniciar el proceso.<br /> </td> 
   <td> Cadena<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessMemoryAlertMb<br /> </td> 
   <td> Alerta de consumo de memoria: alerta relativa a la cantidad de RAM consumida (en Mb) por un proceso determinado.<br /> </td> 
   <td> Largo<br /> </td> 
   <td> 1800<br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessMemoryWarningMb<br /> </td> 
   <td> Advertencia de consumo de memoria: advertencia sobre la cantidad de RAM consumida (en Mb) por un proceso determinado.<br /> </td> 
   <td> Largo<br /> </td> 
   <td> 1600<br /> </td> 
  </tr> 
  <tr> 
   <td> puerto<br /> </td> 
   <td> Puerto de escucha del servidor. Consulte esta <a href="../../installation/using/email-deliverability.md#definition-of-the-server-port">sección</a>.<br /> </td> 
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
   <td> Prioridad en el inicio. Los módulos de baja prioridad se inician y se detienen por primera vez. Por lo tanto, el módulo syslogd debe tener la prioridad 0.<br /> </td> 
   <td> Corto<br /> </td> 
   <td> 10<br /> </td> 
  </tr> 
 </tbody> 
</table>

## syslogd {#syslogd}

Estos son los diferentes parámetros del nodo **syslogd**. Ésta es la configuración del módulo de administración de registros.

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
   <td> Boolean<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> initScript<br /> </td> 
   <td> ID de JavaScript que se ejecutará al iniciar el proceso.<br /> </td> 
   <td> Cadena<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> maxFileSizeMb<br /> </td> 
   <td> Tamaño máximo en Mb para un archivo de registro. <br /> </td> 
   <td> Largo<br /> </td> 
   <td> 10<br /> </td> 
  </tr> 
  <tr> 
   <td> maxNumberOfLoginsFiles<br /> </td> 
   <td> Número máximo de archivos logins.log que se deben conservar. <br /> </td> 
   <td> Largo<br /> </td> 
   <td> 365<br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessMemoryAlertMb<br /> </td> 
   <td> Alerta de consumo de memoria: alerta relativa a la cantidad de RAM consumida (en Mb) por un proceso determinado.<br /> </td> 
   <td> Largo<br /> </td> 
   <td> 1800<br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessMemoryWarningMb<br /> </td> 
   <td> Advertencia de consumo de memoria: advertencia sobre la cantidad de RAM consumida (en Mb) por un proceso determinado.<br /> </td> 
   <td> Largo<br /> </td> 
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
   <td> Prioridad en el inicio. Los módulos de baja prioridad se inician y se detienen por primera vez. Por lo tanto, el módulo syslogd debe tener la prioridad 0.<br /> </td> 
   <td> Corto<br /> </td> 
   <td> 10<br /> </td> 
  </tr> 
 </tbody> 
</table>

## tracking {#tracking}

Estos son los diferentes parámetros del nodo **tracking**. Ésta es la configuración del servidor de seguimiento.

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
   <td> Boolean<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> blockRedirectForUnsignedTrackingLink<br /> </td> 
   <td> Deshabilite las direcciones URL con formato incorrecto generadas a partir de compilaciones anteriores.<br /> </td> 
   <td> Boolean<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> integrationPeriodSec<br /> </td> 
   <td> Período de consolidación<br /> </td> 
   <td> Largo<br /> </td> 
   <td> 300<br /> </td> 
  </tr> 
  <tr> 
   <td> dedupOpenPeriodMin<br /> </td> 
   <td> Anular la duplicación de aperturas: quitar registros de seguimiento abiertos de duplicado para limitar los efectos de las previsualizaciones de correo en lectores de correo como Outlook.<br /> </td> 
   <td> Largo<br /> </td> 
   <td> 1<br /> </td> 
  </tr> 
  <tr> 
   <td> errorIgnorePercent<br /> </td> 
   <td> Omitir hasta X % de errores: no actualice los indicadores de seguimiento siempre que la proporción de historiales que no se haya tenido en cuenta no alcance este valor. <br /> </td> 
   <td> Byte<br /> </td> 
   <td> 1<br /> </td> 
  </tr> 
  <tr> 
   <td> errorIgnorePeriod<br /> </td> 
   <td> Actualizar indicadores de error: duración máxima antes de que se recompongan los indicadores de error.<br /> </td> 
   <td> Largo<br /> </td> 
   <td> 86400<br /> </td> 
  </tr> 
  <tr> 
   <td> IndicadoresDuración<br /> </td> 
   <td> Calcular indicadores durante: duración posterior a la fecha de validez de un envío tras el cual ya no se calculan los indicadores consolidados.<br /> </td> 
   <td> Largo<br /> </td> 
   <td> 2592000<br /> </td> 
  </tr> 
  <tr> 
   <td> initScript<br /> </td> 
   <td> ID de JavaScript que se ejecutará al iniciar el proceso <br /> </td> 
   <td> Cadena<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> logCountPerRequest<br /> </td> 
   <td> Número de registros solicitados por llamada al servidor de seguimiento remoto.<br /> </td> 
   <td> Largo<br /> </td> 
   <td> 1000<br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessMemoryAlertMb<br /> </td> 
   <td> Alerta de consumo de memoria: alerta relativa a la cantidad de RAM consumida (en Mb) por un proceso determinado.<br /> </td> 
   <td> Largo<br /> </td> 
   <td> 1800<br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessMemoryWarningMb<br /> </td> 
   <td> Advertencia de consumo de memoria: advertencia sobre la cantidad de RAM consumida (en Mb) por un proceso determinado.<br /> </td> 
   <td> Largo<br /> </td> 
   <td> 1600<br /> </td> 
  </tr> 
  <tr> 
   <td> phishbowlServiceAPIKey<br /> </td> 
   <td> Clave de API para la integración del extremo del servicio Phishbowl. Esto protege la redirección de direcciones URL mal formadas generadas a partir de compilaciones anteriores. <br /> </td> 
   <td> Largo<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> phishbowlServiceEndpoint<br /> </td> 
   <td> Extremo para la integración del extremo del servicio Phishbowl. Esto protege la redirección de direcciones URL mal formadas generadas a partir de compilaciones anteriores.<br /> </td> 
   <td> Largo<br /> </td> 
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
   <td> Prioridad en el inicio. Los módulos de baja prioridad se inician y se detienen por primera vez. Por lo tanto, el módulo syslogd debe tener la prioridad 0.<br /> </td> 
   <td> Corto<br /> </td> 
   <td> 10<br /> </td> 
  </tr> 
  <tr> 
   <td> trackingIgnorePercent<br /> </td> 
   <td> Omitir hasta el X % del seguimiento: no actualice los indicadores de seguimiento siempre que la proporción de historiales que no se haya tenido en cuenta no alcance este valor.<br /> </td> 
   <td> Byte<br /> </td> 
   <td> 1<br /> </td> 
  </tr> 
  <tr> 
   <td> trackingIgnorePeriod<br /> </td> 
   <td> Actualizar indicadores de seguimiento: duración máxima antes de que se recompongan los indicadores de seguimiento.<br /> </td> 
   <td> Largo<br /> </td> 
   <td> 86400<br /> </td> 
  </tr> 
  <tr> 
   <td> userAgentCacheSize<br /> </td> 
   <td> Tamaño de la caché del identificador del explorador.<br /> </td> 
   <td> Largo<br /> </td> 
   <td> 500<br /> </td> 
  </tr> 
 </tbody> 
</table>

## trackinglogd {#trackinglogd}

Estos son los diferentes parámetros del nodo **trackinglogd**. Ésta es la configuración del daemon de escritura del registro de seguimiento.

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
   <td> Boolean<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> initScript<br /> </td> 
   <td> ID de JavaScript que se ejecutará al iniciar el proceso <br /> </td> 
   <td> Cadena<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> maxCreateFileRetry<br /> </td> 
   <td> Reintentos máximos de escritura: número máximo de archivos que se pueden crear en caso de error al escribir en los archivos de registro.<br /> </td> 
   <td> Largo<br /> </td> 
   <td> 5<br /> </td> 
  </tr> 
  <tr> 
   <td> maxLogsSizeOnDiskMb<br /> </td> 
   <td> Tamaño máximo de registro: espacio máximo utilizado por los registros en disco (en MB). No puede ser inferior a 100 MB. <br /> </td> 
   <td> Largo<br /> </td> 
   <td> 500<br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessMemoryAlertMb<br /> </td> 
   <td> Alerta de consumo de memoria: alerta relativa a la cantidad de RAM consumida (en Mb) por un proceso determinado.<br /> </td> 
   <td> Largo<br /> </td> 
   <td> 1800<br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessMemoryWarningMb<br /> </td> 
   <td> Advertencia de consumo de memoria: advertencia sobre la cantidad de RAM consumida (en Mb) por un proceso determinado.<br /> </td> 
   <td> Largo<br /> </td> 
   <td> 1600<br /> </td> 
  </tr> 
  <tr> 
   <td> maxSharedLogs<br /> </td> 
   <td> Número máximo de registros: número máximo de registros almacenados en la memoria compartida. No puede ser menor que 10000. <br /> </td> 
   <td> Largo<br /> </td> 
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
   <td> Número de registros antes de la depuración: número de registros insertados antes de iniciar la purga de archivos de registro. No puede ser inferior a 50000.<br /> </td> 
   <td> Largo<br /> </td> 
   <td> 50000<br /> </td> 
  </tr> 
  <tr> 
   <td> runLevel<br /> </td> 
   <td> Prioridad en el inicio. Los módulos de baja prioridad se inician y se detienen por primera vez. Por lo tanto, el módulo syslogd debe tener la prioridad 0.<br /> </td> 
   <td> Corto<br /> </td> 
   <td> 10<br /> </td> 
  </tr> 
  <tr> 
   <td> webTrackingParamSize<br /> </td> 
   <td> Número máximo de caracteres guardados en la memoria compartida para parámetros de seguimiento web adicionales.<br /> </td> 
   <td> Largo<br /> </td> 
   <td> 64<br /> </td> 
  </tr> 
 </tbody> 
</table>

## web {#web}

Estos son los diferentes parámetros del nodo **web**. Ésta es la configuración del módulo Web.

Para obtener más información, consulte esta [sección](../../installation/using/configuring-campaign-server.md#default-port-for-tomcat).

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
   <td> JVMOoptions<br /> </td> 
   <td> Las opciones de JVM se pasan como una cadena.<br /> </td> 
   <td> Cadena<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> MaxThwords<br /> </td> 
   <td> Número máximo de subprocesos.<br /> </td> 
   <td> Largo<br /> </td> 
   <td> 75<br /> </td> 
  </tr> 
  <tr> 
   <td> MinSpareThwords<br /> </td> 
   <td> Número mínimo de subprocesos.<br /> </td> 
   <td> Largo<br /> </td> 
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
   <td> Boolean<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> controlPort<br /> </td> 
   <td> Puerto de control de escucha Tomcat: consulte <a href="../../installation/using/configuring-campaign-server.md#configuring-tomcat" target="_blank">Configuración de Tomcat</a>.<br /> </td> 
   <td> Corto<br /> </td> 
   <td> 8005<br /> </td> 
  </tr> 
  <tr> 
   <td> httpPort<br /> </td> 
   <td> Puerto de escucha HTTP Tomcat: consulte <a href="../../installation/using/configuring-campaign-server.md#configuring-tomcat" target="_blank">Configuración de Tomcat</a>.<br /> </td> 
   <td> Corto<br /> </td> 
   <td> 8080<br /> </td> 
  </tr> 
  <tr> 
   <td> initScript<br /> </td> 
   <td> ID de JavaScript que se ejecutará al iniciar el proceso.<br /> </td> 
   <td> Cadena<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> maxDeliveryQueueSize<br /> </td> 
   <td> Tamaño de la cola para llamadas SubmitDelivery: número máximo de llamadas SubmitDelivery SOAP que se pueden poner en cola.<br /> </td> 
   <td> Largo<br /> </td> 
   <td> 50<br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessMemoryAlertMb<br /> </td> 
   <td> Alerta de consumo de memoria: alerta relativa a la cantidad de RAM consumida (en Mb) por un proceso determinado.<br /> </td> 
   <td> Largo<br /> </td> 
   <td> 1800<br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessMemoryWarningMb<br /> </td> 
   <td> Advertencia de consumo de memoria: advertencia sobre la cantidad de RAM consumida (en Mb) por un proceso determinado<br /> </td> 
   <td> Largo<br /> </td> 
   <td> 1600<br /> </td> 
  </tr> 
  <tr> 
   <td> notifRelay<br /> </td> 
   <td> Relé de notificaciones: HostName:Puerto que habilita el reenvío de notificaciones.<br /> </td> 
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
   <td> Prioridad en el inicio. Los módulos de baja prioridad se inician y se detienen por primera vez. Por lo tanto, el módulo syslogd debe tener la prioridad 0.<br /> </td> 
   <td> Corto<br /> </td> 
   <td> 10<br /> </td> 
  </tr> 
  <tr> 
   <td> startSoapRouterInModule<br /> </td> 
   <td> Inicio del enrutador SOAP en modo módulo.<br /> </td> 
   <td> Boolean<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
 </tbody> 
</table>

### jsp {#jsp}

Estos son los diferentes parámetros del nodo **web > jsp**. Esta es la configuración de los parámetros que utilizan los JSP.

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
   <td> debug<br /> </td> 
   <td> Ejecución de JSP en modo de depuración o no.<br /> </td> 
   <td> Boolean<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> downloadPath<br /> </td> 
   <td> Descargar carpeta: ruta de descarga de programas de instalación para las consolas de cliente.<br /> </td> 
   <td> Cadena<br /> </td> 
   <td> '$(XTK_INSTALL_DIR)/datakit/nl/eng/jsp'<br /> </td> 
  </tr> 
  <tr> 
   <td> forFileName<br /> </td> 
   <td> Ruta del archivo .fo.<br /> </td> 
   <td> Cadena<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> soapRouter<br /> </td> 
   <td> Dirección URL del enrutador SOAP (http://myserver/xxx, http://jni o mailto:xxx).<br /> </td> 
   <td> Cadena<br /> </td> 
   <td> 'http://jni'<br /> </td> 
  </tr> 
 </tbody> 
</table>

El nodo **web > jsp > class path** contiene la lista de todas las rutas de clase que se utilizarán al iniciar JVM. Esta es la configuración predeterminada:

```
'$(XTK_INSTALL_DIR)/tomcat-8/bin/bootstrap.jar
          $(XTK_INSTALL_DIR)/tomcat-8/bin/tomcat-juli.jar
          $(XTK_INSTALL_DIR)/tomcat-8/lib/tomcat-coyote.jar
          $(XTK_INSTALL_DIR)/tomcat-8/lib/tomcat-util.jar
          $(XTK_INSTALL_DIR)/tomcat-8/lib/tomcat-api.jar
          $(XTK_INSTALL_DIR)/tomcat-8/lib/servlet-api.jar
          $(XTK_INSTALL_DIR)/tomcat-8/lib/jsp-api.jar
          $(XTK_INSTALL_DIR)/tomcat-8/lib/el-api.jar
          $(XTK_INSTALL_DIR)/java/lib/log4j-1.2.11.jar
          $(XTK_INSTALL_DIR)/tomcat-8/lib/annotations-api.jar
          $(XTK_INSTALL_DIR)/tomcat-8/lib/catalina.jar
          $(XTK_INSTALL_DIR)/tomcat-8/lib/websocket-api.jar
          $(XTK_INSTALL_DIR)/tomcat-8/lib/tomcat7-websocket.jar
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
   <td> Habilita el recolector de elementos no utilizados del contexto JavaScript después de cada consulta.<br /> </td> 
   <td> Boolean<br /> </td> 
   <td> true<br /> </td> 
  </tr> 
  <tr> 
   <td> timeToLive<br /> </td> 
   <td> Número máximo de páginas servidas por un contexto de JavaScript. <br /> </td> 
   <td> Largo<br /> </td> 
   <td> 1000<br /> </td> 
  </tr> 
 </tbody> 
</table>

El nodo **web > jsp > class path** contiene la lista de todas las rutas de clase que se utilizarán al iniciar JVM.

### relé {#relay-2}

Estos son los diferentes parámetros del nodo **web > relay**. Esta es la configuración del relé para solicitudes HTTP entre dos zonas.

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
   <td> Inicio del módulo de retransmisión HTTP dentro del servidor Web en modo de depuración.<br /> </td> 
   <td> Boolean<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> banCharsInAuthority<br /> </td> 
   <td> Caracteres prohibidos (dominio): lista de caracteres prohibidos en la sección 'autoridad' de un URI.<br /> </td> 
   <td> Cadena<br /> </td> 
   <td> '.?#@/:' <br /> </td> 
  </tr> 
  <tr> 
   <td> banCharsInPath<br /> </td> 
   <td> Caracteres prohibidos (ruta): lista de caracteres prohibidos en la sección 'path' de un URI.<br /> </td> 
   <td> Cadena<br /> </td> 
   <td> '?#/'<br /> </td> 
  </tr> 
  <tr> 
   <td> modDir<br /> </td> 
   <td> Valor de la opción del módulo 'mod_dir': lista de los archivos que se utilizarán durante una consulta en una carpeta.<br /> </td> 
   <td> Cadena<br /> </td> 
   <td> 'index.md' <br /> </td> 
  </tr> 
  <tr> 
   <td> startRelay<br /> </td> 
   <td> Inicio del módulo de retransmisión HTTP.<br /> </td> 
   <td> Boolean<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> startRelayInModule<br /> </td> 
   <td> Inicio el módulo de retransmisión HTTP dentro del servidor Web. <br /> </td> 
   <td> Boolean<br /> </td> 
   <td> true<br /> </td> 
  </tr> 
  <tr> 
   <td> timeout<br /> </td> 
   <td> Espere un tiempo antes de eliminar la dirección URL prohibida.<br /> </td> 
   <td> Cadena<br /> </td> 
   <td> '60'<br /> </td> 
  </tr> 
 </tbody> 
</table>

Añada un nodo **web > relay > url** para cada URL que se va a retransmitir (el orden de inserción define la prioridad) con los parámetros siguientes.

Para obtener más información, consulte [Seguridad dinámica de la página y relevos](../../installation/using/configuring-campaign-server.md#dynamic-page-security-and-relays) y [sección](../../installation/using/deploying-an-instance.md#synchronizing-public-resources).

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
   <td> IP autorizadas: lista separada por comas de las direcciones IP de origen permitidas para usar el relé de esta máscara.<br /> </td> 
   <td> Cadena<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> negar<br /> </td> 
   <td> Denegar acceso a estas direcciones URL (devolver un error HTTP 403)<br /> </td> 
   <td> Boolean<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> hostMask<br /> </td> 
   <td> Alias DNS que se va a retransmitir: lista separada por comas de las máscaras de alias DNS que se van a retransmitir (por ejemplo: '*.adobe.com').<br /> </td> 
   <td> Cadena<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> httpAllowed<br /> </td> 
   <td> Acceso HTTP autorizado independientemente de la zona de seguridad (como webApps). <br /> </td> 
   <td> Boolean<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> relayHost<br /> </td> 
   <td> Añadir host original: utilice el encabezado HTTP 'Host' de la solicitud original al reproducirla.<br /> </td> 
   <td> Boolean<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> relayPath<br /> </td> 
   <td> Añadir ruta de URL inicial: anexe la ruta completa de las direcciones URL para que se retransmitan a la dirección URL de la página de destinatario. <br /> </td> 
   <td> Boolean<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> status<br /> </td> 
   <td> Estado de sincronización de un recurso público (lista desglosada). Los valores posibles son 'normal' (ejecución normal), 'blacklist' (dirección URL agregada a lista de bloqueados en caso de error 404) y 'spare' (carga de archivos en el servidor de reserva si existe).<br /> </td> 
   <td> Cadena<br /> </td> 
   <td> normal<br /> </td> 
  </tr> 
  <tr> 
   <td> targetUrl<br /> </td> 
   <td> Dirección URL de la página de destinatario: consulte <a href="../../installation/using/configuring-campaign-server.md#configuring-tomcat" target="_blank">Configuración de Tomcat</a>.<br /> </td> 
   <td> Cadena<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> timeout<br /> </td> 
   <td> Tiempo máximo de ejecución (en segundos) de la solicitud que se está retransmitiendo.<br /> </td> 
   <td> Largo<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> urlPath<br /> </td> 
   <td> Máscara de direcciones URL para retransmitir (por ejemplo: '/nl*', '*.jsp').<br /> </td> 
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

Añada un nodo **web > relay > responseHeader** para cada encabezado HTTP para agregarlo a las respuestas reenviadas al relé.

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
   <td> name<br /> </td> 
   <td> Nombre de encabezado<br /> </td> 
   <td> Cadena<br /> </td> 
  </tr> 
  <tr> 
   <td> value<br /> </td> 
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

Estos son los diferentes parámetros del nodo **web > redirección**. Ésta es la configuración del módulo de redirección.

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
   <td> Identificador de organización de Identity Management System (IMS): identificador de organización único dentro del Adobe Experience Cloud, utilizado en particular para el servicio VisitorID y el SSO de IMS. <br /> </td> 
   <td> Cadena<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> P3PCompactPolicy<br /> </td> 
   <td> Valor que describe la directiva utilizada para las cookies permanentes (compatible con el formato de directiva compacta P3P). <br /> </td> 
   <td> Cadena<br /> </td> 
   <td> 'CAO DSP COR CURa DEVa TAIa NUESTRO BUS IND UNI COM NAV'<br /> </td> 
  </tr> 
  <tr> 
   <td> cookieDomain<br /> </td> 
   <td> Lista separada por comas de los dominios que se van a configurar para indicar explícitamente el dominio en el que se va a establecer la cookie. <br /> </td> 
   <td> Cadena<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> databaseId<br /> </td> 
   <td> Identificador de base de datos asociado con la instancia de seguimiento.<br /> </td> 
   <td> Cadena<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> defLogCount<br /> </td> 
   <td> Recuento de registros por llamada: número de registros devueltos de forma predeterminada al llamar al método GetTrackingLogs.<br /> </td> 
   <td> Largo<br /> </td> 
   <td> 30<br /> </td> 
  </tr> 
  <tr> 
   <td> expirationURL<br /> </td> 
   <td> Página para redirecciones caducadas: La dirección URL de la página Web que utiliza de forma predeterminada el servidor de redirección cuando caduca la redirección de una acción de envío.<br /> </td> 
   <td> Cadena<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> maxJobsInCache<br /> </td> 
   <td> Número máximo de trabajos: número máximo de acciones de envío en la caché. Puede no ser inferior a 50. <br /> </td> 
   <td> Largo<br /> </td> 
   <td> 100<br /> </td> 
  </tr> 
  <tr> 
   <td> startRedirect<br /> </td> 
   <td> Inicio del servicio de redirección.<br /> </td> 
   <td> Boolean<br /> </td> 
   <td> true<br /> </td> 
  </tr> 
  <tr> 
   <td> startRedirectInModule<br /> </td> 
   <td> Inicio del servicio de redirección en modo módulo.<br /> </td> 
   <td> Boolean<br /> </td> 
   <td> true<br /> </td> 
  </tr> 
  <tr> 
   <td> trackWebVisitors<br /> </td> 
   <td> Seguimiento web: creación de registros para las páginas visitadas por usuarios desconocidos. <br /> </td> 
   <td> Boolean<br /> </td> 
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

Estos son los diferentes parámetros del nodo **web > redirección > spareServer**.

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
   <td> Se tendrá en cuenta si: el servidor de seguimiento se tiene en cuenta si la expresión devuelve true. <br /> </td> 
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
   <td> URL del servidor de redirección adicional<br /> </td> 
   <td> Cadena<br /> </td> 
   <td> <br /> </td> 
  </tr> 
 </tbody> 
</table>

### spamCheck {#spamcheck}

Estos son los diferentes parámetros del nodo **web > spamCheck**. Ésta es la configuración de los parámetros de evaluación de la puntuación de correo electrónico no deseado.

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
   <td> comando<br /> </td> 
   <td> Comando que se debe ejecutar para evaluar la puntuación antispam de un correo electrónico (p. ej. 'perl spamcheck.pl').<br /> </td> 
   <td> Cadena<br /> </td> 
  </tr> 
 </tbody> 
</table>

## wfserver {#wfserver}

Estos son los diferentes parámetros del nodo **wfserver**. Ésta es la configuración del proceso de flujo de trabajo.

Para obtener más información, consulte [flujos de trabajo y afinidades de alta disponibilidad](../../installation/using/configuring-campaign-server.md#high-availability-workflows-and-affinities).

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
   <td> Boolean<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> dataBasePoolPeriodSec<br /> </td> 
   <td> Periodo<br /> </td> 
   <td> Largo<br /> </td> 
   <td> 20<br /> </td> 
  </tr> 
  <tr> 
   <td> initScript<br /> </td> 
   <td> ID de JavaScript que se ejecutará al iniciar el proceso.<br /> </td> 
   <td> Cadena<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessMemoryAlertMb<br /> </td> 
   <td> Alerta de consumo de memoria: alerta relativa a la cantidad de RAM consumida (en Mb) por un proceso determinado.<br /> </td> 
   <td> Largo<br /> </td> 
   <td> 1800<br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessMemoryWarningMb<br /> </td> 
   <td> Advertencia de consumo de memoria: advertencia sobre la cantidad de RAM consumida (en Mb) por un proceso determinado.<br /> </td> 
   <td> Largo<br /> </td> 
   <td> 1600<br /> </td> 
  </tr> 
  <tr> 
   <td> notifRelay<br /> </td> 
   <td> Relé de notificaciones: HostName:Puerto que habilita el reenvío de notificaciones.<br /> </td> 
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
   <td> Prioridad en el inicio. Los módulos de baja prioridad se inician y se detienen por primera vez. Por lo tanto, el módulo syslogd debe tener la prioridad 0.<br /> </td> 
   <td> Corto<br /> </td> 
   <td> 10<br /> </td> 
  </tr> 
 </tbody> 
</table>

