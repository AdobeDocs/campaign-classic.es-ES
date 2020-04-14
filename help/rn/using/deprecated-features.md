---
title: Campaign Classic de funciones obsoletas y eliminadas
description: Esta página lista las funciones obsoletas y eliminadas de Adobe Campaign Classic
page-status-flag: never-activated
uuid: null
contentOwner: simonetn
products: SG_CAMPAIGN/CLASSIC
audience: rn
content-type: reference
topic-tags: campaign-classic-deprecated-features
discoiquuid: null
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 79f8cc179fcbf9d537a1cc889b268a43202d7369

---


# Deprecated and removed features {#deprecated-and-removed-features}

Adobe evalúa constantemente las funciones de sus productos para identificar aquellas que sean antiguas y que deban reemplazarse con alternativas más modernas para mejorar la experiencia de los clientes, intentando garantizar en todo momento la compatibilidad con versiones anteriores. Como Adobe Campaign Classic funciona con herramientas de terceros, la compatibilidad se actualiza con regularidad para poder implementar únicamente versiones compatibles. Las versiones que ya no son compatibles con Adobe Campaign Classic se enumeran a continuación.

Para comunicar la inminente eliminación/sustitución de las funciones de Campaign Classic, se aplican las siguientes reglas:

* Primero, se anuncia que la función quedará obsoleta. Aunque las funciones obsoletas todavía pueden estar disponibles para los usuarios existentes, no se mejorarán ni se documentarán.
* La eliminación completa de la función se producirá en la siguiente versión como muy pronto. En esta página se anuncia la fecha objetivo real de la eliminación.

Este proceso proporciona a los clientes al menos un ciclo de versiones para actualizar su implementación a una nueva versión o a la versión sucesora de la función obsoleta antes de su eliminación real.

>[!NOTE]
>Las versiones de Adobe Campaign y las nuevas funciones se enumeran en las [Notas](../../rn/using/latest-release.md)de la versión.


## Funciones obsoletas {#deprecated-features}

Esta sección enumera las funciones y capacidades que se han marcado como obsoletas en las últimas versiones de Campaign Classic.

Por lo general, las funciones que se planea eliminar en una versión futura se definen en primer lugar como obsoletas, y se proporciona una función alternativa a ellas. Estas funciones y funcionalidades ya no están disponibles para los nuevos clientes Campaign Standard o no deben usarse para ninguna implementación nueva. También se eliminan de la documentación del producto.

Se aconseja a los clientes que comprueben si utilizan la función o la capacidad en su implementación actual y que cambien su implementación para utilizar la alternativa proporcionada. Consulte la fecha de eliminación objetivo para planificar el entorno y las actualizaciones del proyecto según corresponda.

### Versión de Adobe Campaign 18.6 {#ac-18-6-release}

<table> 
 <tbody> 
  <tr> 
   <td><strong>Área</strong></td>
   <td><strong>Función</strong></td> 
   <td><strong>Sustitución</strong></td> 
  </tr> 
   <tr> 
   <td>Seguridad SDK de JavaScript<br> </td>
   <td>decryptString<br> </td>
   <td><p>For security reasons, <em>decryptString</em> API is no longer available by default for new installations.</p> 
   <p>In the context of a postupgrade to 18.6 (and later), this API is no longer activated, and has been replaced by the <em>decryptPassword</em> function.</p><br> </td>
  </tr> 
 </tbody> 
</table>

### Versión de Adobe Campaign 18.4 {#ac-18-4-release}

<table> 
 <tbody> 
  <tr> 
   <td><strong>Área</strong></td>
   <td><strong>Función</strong></td> 
   <td><strong>Sustitución</strong></td> 
  </tr> 
   <tr> 
   <td>Almacenamiento de correos electrónicos<br> </td>
   <td>Archivado basado en archivos<br> </td>
   <td><p>El archivado de correo electrónico ya está disponible a través de una dirección de correo electrónico específica de CCO. <a href="../../installation/using/email-archiving.md">Más información</a>.</p> 
   <p><em>Fecha de eliminación del Destinatario: Versión de Campaña 20.2: junio de 2020</em></p><br> </td>
  </tr> 
   <tr> 
   <td>Administración de posibles clientes<br> </td>
   <td>Posibles clientes<br> </td>
   <td><p>El paquete de administración de posibles clientes de Adobe Campaign Classic simplifica el proceso de creación y mantenimiento de todo el ciclo de administración de posibles clientes. Se puede implementar una funcionalidad similar mediante otras actividades nativas del flujo de trabajo y modificaciones del modelo de datos.</p> 
   <p><em>Fecha de eliminación del Destinatario: Versión de Campaña 20.2: junio de 2020</em></p><br> </td>
  </tr> 
 </tbody> 
</table>


## Compatibilidad obsoleta {#deprecated-compatibility}

### Versión de Adobe Campaign 20.1 {#compat-20-1-release}

A partir de la versión 20.1 de febrero, el siguiente sistema quedará obsoleto para Campaign Classic. La compatibilidad finalizará en la versión 20.2 (junio de 2020).

<table> 
 <tbody> 
  <tr> 
   <td><strong>Área</strong></td>
   <td><strong>Sustitución</strong></td> 
  </tr> 
   <tr> 
   <td>Consola de cliente de Campaign Classic de 32 bits<br> </td>
   <td><p>Consola de cliente de Campaign Classic de 64 bits</p><br> </td>
  </tr> 
 </tbody> 
</table>

### Versión de Adobe Campaign 19.2  {#compat-19-2-release}

A partir de la versión de otoño (19.2), los siguientes sistemas operativos quedan obsoletos para Campaign Classic. La compatibilidad finalizará a finales del año 2020.

* Servidor web: Apache 2.2. [Más información](https://wiki.centos.org/About/Product)
* Sistema operativo: CentOS 6. [Más información](https://wiki.centos.org/About/Product)

Consulte la [Matriz de compatibilidades](https://helpx.adobe.com/es/campaign/kb/compatibility-matrix.html) para actualizar a una versión más reciente o pasar a un sistema nuevo.

## Funciones eliminadas {#removed-features}

Esta sección lista las funciones y funciones que se han eliminado del Campaign Standard.

<table> 
 <tbody> 
  <tr> 
   <td><strong>Área: Función</strong></td>
   <td><strong>Sustitución</strong></td> 
   <td><strong>Versión</strong></td> 
  </tr> 
   <tr> 
   <td>Documentación de las API de Campaign - archivo<br>jsapi.chm</td>
   <td>Las API de Campaign Classic están ahora disponibles en una página dedicada. If you were using the jsapi.chm file, you should now refer to <a href="https://docs.adobe.com/content/help/en/campaign-classic/technicalresources/api/index.html">the new online version</a>.</td>
   <td>19.1</td>
  </tr> 
  <tr> 
   <td>Organización de campañas - Marketing predictivo</td>
   <td>Una gran parte de las funciones de marketing predictivo de Adobe Campaign Classic es el consumo de modelos predictivos. Aunque la actividad de flujo de trabajo de marketing predictivo se eliminará en las próximas versiones, Adobe Campaign seguirá admitiendo el consumo y el uso de modelos predictivos de fuentes externas a través de otras actividades de flujo de trabajo.</td>
   <td>18.10</td>
  </tr> 
  <tr> 
   <td>Aplicaciones web - Micrositios</td>
   <td>Mejore la seguridad restringiendo el acceso solo a los dominios dedicados en los archivos de configuración de Adobe Campaign. Puede seguir utilizando direcciones URL personalizadas en la Campaña mediante alias DNS. <a href="https://helpx.adobe.com/es/campaign/kb/domain-name-delegation.html">Más información</a>.</td>
   <td>18.10</td>
  </tr> 
  <tr> 
   <td>Notificaciones push: Conector<br>binario de iOS</td>
   <td>Por recomendación de Apple, Adobe eliminará el conector binario heredado de iOS. Ya está disponible el conector basado en HTTP/2 más funcional y eficiente.</td>
   <td>18.10</td>
  </tr> 
   <tr> 
   <td>canal móvil: mensajes push de MMS y WAP</td>
   <td>Los canales push de MMS y Wap ya no están disponibles. Como reemplazo, puedes aprovechar los envíos <a href="../../delivery/using/sms-channel.md">SMS</a> y <a href="../../delivery/using/about-mobile-app-channel.md">Push</a> .</td>
   <td>18.4</td>
  </tr> 
   <tr> 
   <td>canal móvil: LÍNEA v1</td>
   <td>El paquete de LINE Connect ya no se puede instalar en Adobe Campaign Classic. Adobe recomienda utilizar el nuevo paquete de Canal LINE para enviar mensajes LINE. <a href="../../delivery/using/line-channel.md">Más información</a>.</td>
   <td>18.4</td>
  </tr> 
 </tbody> 
</table>

## Fin de compatibilidad {#end-of-compatibility}

>[!CAUTION]
>
>Adobe Campaign Classic es compatible con todos los sistemas y herramientas enumerados en la [Matriz de compatibilidad](https://helpx.adobe.com/es/campaign/kb/compatibility-matrix.html). Cuando las versiones específicas de estos sistemas y herramientas de terceros llegan al final de su vida útil (EOL) con sus respectivos creadores, Adobe Campaign ya no es compatible con ellas: se anuncian como funciones obsoletas y, después, se eliminan de nuestra matriz de compatibilidad en la versión posterior del producto. Para evitar problemas, compruebe que se encuentra en una versión compatible de cualquier sistema enumerado en la matriz de compatibilidad.

### Client console {#client-console-eol}

La consola del cliente de Adobe Campaign Classic ya no se puede ejecutar en los siguientes sistemas, ya que su editor los ha desaprobado. Los clientes que ejecuten la consola de cliente de Campaign en una de estas versiones deben actualizar a la versión más reciente antes de la fecha de eliminación objetivo. Consulte la [matriz de compatibilidades](https://helpx.adobe.com/es/campaign/kb/compatibility-matrix.html).

* Windows Server 2003, 2008, 2008 R2
* Windows XP, Vista

### Sistemas operativos {#o-s-eol}

A partir de la versión 19.1, Adobe Campaign ya no es compatible con los siguientes sistemas operativos.

* Debian 7. [Más información](https://wiki.debian.org/DebianReleases).
* RHEL 6.x. [Más](https://access.redhat.com/support/policy/updates/errata)información.
* Windows Server 2008. [Más información](https://support.microsoft.com/es-es/lifecycle/search/1163).
* SLES 11. [Más información](https://www.suse.com/lifecycle).

### Web servers {#web-server-eol}

A partir de la versión de primavera (19.1), Adobe Campaign deja de ser compatible con el siguiente servidor web.

* Microsoft IIS 7. [Más información](https://support.microsoft.com/es-es/lifecycle/search/810).

### Herramientas {#tools-eol}

A partir de la versión de primavera (19.1), Adobe Campaign deja de ser compatible con las siguientes herramientas.

* Java JDK 7. [Más información](http://www.oracle.com/technetwork/java/javase/eol-135779.html).
* Libre Office 3.5 / 4.3 / 5.x, excepto cuando se incorpora en otra herramienta. [Más información](https://wiki.documentfoundation.org/ReleasePlan/Archive#End-of-Life_Releases).

### Motores de bases de datos {#dbe-eol}

Adobe no admite los siguientes motores de bases de datos, ya que su editor los ha desaprobado. Los clientes que ejecutan estas versiones deben actualizar a la versión más reciente o pasar a otra.

Refer to [Campaign Classic Compatibility matrix](https://helpx.adobe.com/es/campaign/kb/compatibility-matrix.html) to access the list of compatible versions.

**ACCESO DE DATOS FEDERADO (FDA)**

A partir de la versión de primavera (19.1), Adobe Campaign deja de ser compatible con los siguientes servidores FDA.

* Oracle 11G. [Más información](http://www.oracle.com/us/support/library/lifetime-support-technology-069183.pdf).
* PostgreSQL 9.3. [Más](https://www.postgresql.org/support/versioning)información.
* MySQL 5.5. &lt;[Más información](http://www.fromdual.com/support-for-mysql-from-oracle).
* DB2 9.5. [Más](http://www-01.ibm.com/support/docview.wss?uid=swg21168270)información.
* Teradata 14 - 14.1. [Más](https://community.teradata.com/t5/Database/Teradata-Database-Product-Life-Cycle/td-p/35068)información.

Campaign Classic no es compatible con los siguientes servidores de acceso de datos federado (FDA).

* DB2 UDB 9.5, 9.7. La versión más reciente de DB2 se admite mediante Acceso de datos federado (FDA). [Más información](http://www-01.ibm.com/support/docview.wss?uid=swg21168270).
* Oracle 9i, 10G R2. Las versiones más recientes de Oracle son compatibles mediante el acceso de datos federado (FDA). [Más información](http://www.oracle.com/us/support/library/lifetime-support-technology-069183.pdf).
* PostgreSQL 8.3, 8.4, 9.0, 9.1, 9.2. Las versiones más recientes de PostgreSQL son compatibles con Acceso de datos federado (FDA). [Más información](https://www.postgresql.org/support/versioning).
* MSSQL 2000, 2005, 2008 R2. Las versiones más recientes de SQL Server son compatibles mediante el acceso de datos federado (FDA). [Más información](https://support.microsoft.com/es-es/lifecycle/search/1044).
* MySQL 5.1. Las versiones más recientes de MySQL son compatibles con Acceso de datos federado (FDA). [Más información](https://es.wikipedia.org/wiki/InfiniDB).
* InfiniDB llegó al final de su vida útil. [Más información](https://www.mysql.com/support).
* Teradata 13, 13.1. Las versiones más recientes de Teradata son compatibles con Acceso de datos federado (FDA). [Más información](https://www.info.teradata.com/download.cfm?ItemID=1007255).
* Netezza 6.02, 7.0. Netezza llegó a su fin. [Más información](https://en.wikipedia.org/wiki/Netezza).
* AsterData 5.0. AsterData llegó al final de su vida útil. [Más información](https://en.wikipedia.org/wiki/Aster_Data_Systems).
* Sybase IQ 15.2, 15.4, 15.5 y Sybase ASE 15.0. Las versiones más recientes de Sybase son compatibles con Acceso de datos federado (FDA). [Más información](https://sites.google.com/site/dbatipsandtricks/time-tracker).
* Hadoop a través de HiveSQL: Hadoop 2.7.3, HiveSQL 1.2.1. Adobe Campaign Classic seguirá siendo compatible con las versiones de Hadoop incluidas en la lista a través de HiveSQL a través de Acceso de datos federado (FDA), pero estas versiones se combinan con: HortonWorks (HDP 2.4.X, 2.5.x, 2.6.x) y HDInsight 3.4 (HDP 2.4), 3.5 (HDP 2.5), 3.6 (HDP 2.6)

**SERVIDOR RDBMS**

Adobe Campaign no es compatible con los siguientes servidores RDBMS:
* Oracle 10GR2, 11G
* PostgreSQL 9.0 a 9.3
* SQL Server 2005
* MySQL 5.1
* DB2 UDB 9.7
