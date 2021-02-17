---
solution: Campaign Classic
product: campaign
title: Funciones obsoletas y eliminadas de Campaign Classic
description: Esta página lista las funciones obsoletas y eliminadas de Adobe Campaign Classic
audience: rn
content-type: reference
topic-tags: campaign-classic-deprecated-features
internal: n
snippet: y
translation-type: ht
source-git-commit: 4efe5f8a9130e7925194e56e088b3745c0cbd11a
workflow-type: ht
source-wordcount: '1632'
ht-degree: 100%

---


# Funciones obsoletas y eliminadas {#deprecated-and-removed-features}

Adobe evalúa constantemente las funciones de sus productos para identificar aquellas que sean antiguas y que deban reemplazarse con alternativas más modernas para mejorar la experiencia de los clientes, intentando garantizar en todo momento la compatibilidad con versiones anteriores. Como Adobe Campaign Classic funciona con herramientas de terceros, la compatibilidad se actualiza de forma regular para implementar únicamente versiones compatibles. Las versiones que ya no son compatibles con Adobe Campaign Classic se enumeran a continuación y en la [Matriz de compatibilidad](../../rn/using/compatibility-matrix.md).

Para comunicar la inminente eliminación/sustitución de las funciones de Campaign Classic, se aplican las siguientes reglas:

* Primero, se anuncia que la función quedará obsoleta. Aunque las funciones obsoletas todavía pueden estar disponibles y ser compatibles para los usuarios existentes, no se van a mejorar ni documentar.
* La eliminación completa de la función se producirá en la siguiente versión como muy pronto. En esta página se anuncia la fecha objetivo real de la eliminación.

Este proceso proporciona a los clientes al menos un ciclo de versiones para actualizar su implementación a una nueva versión o a la versión sucesora de la función obsoleta antes de su eliminación real.

>[!NOTE]
>Las versiones de Adobe Campaign y las nuevas funciones se enumeran en las [Notas de la versión](../../rn/using/latest-release.md).

## Funciones obsoletas {#deprecated-features}

Esta sección enumera las funciones y capacidades que se han marcado como obsoletas en las últimas versiones de Campaign Classic.

Por lo general, las funciones que se planea eliminar en una versión posterior se definen en primer lugar como obsoletas. Estas funciones y funcionalidades ya no están disponibles para los nuevos clientes de Campaign Classic, o no deben usarse para ninguna implementación nueva. También se eliminan de la documentación del producto.

Se aconseja a los clientes que comprueben si utilizan la función o la funcionalidad en su implementación actual y que cambien su implementación. Consulte la fecha de eliminación objetivo para planificar el entorno y las actualizaciones del proyecto según corresponda.

<table> 
 <tbody> 
   <tr>
   <td><strong>Función</strong></td>
   <td><strong>Sustitución</strong></td>
  </tr>
  <tr>
  <td>Conectores CRM<br></td>
   <td><p>A partir de la versión Campaign 20.3, los siguientes conectores CRM quedan obsoletos:</p>
   <ul>
   <li>API de Soap: On-Premise: 2007, 2015, 2016</li>
   <li>API de Soap: En línea: 2015, 2016</li>
   <li>API web - Microsoft Dynamics CRM On-premise: 2016, actualización 1 de 2016</li>
   <li>API web - Microsoft Dynamics CRM Online: 2016, actualización 1 de 2016</li>
   <li>API de Oracle bajo demanda</li>
   </ul>
  <p><em>Fecha de eliminación objetivo: abril de 2021</em></p>
  </td>
 </tr>
  <tr>
  <td>binario heredado de iOS<br></td>
  <td><p>A partir de la versión 20.3 de Campaign, el conector binario heredado de iOS está en desuso.<p>
  <p> Si utiliza este conector, debe adaptar la implementación en consecuencia.
  <a href="https://helpx.adobe.com/es/campaign/kb/migrate-to-apns-http2.html">Más información</a></p>
  <p><em>Fecha de eliminación objetivo: abril de 2021</em></p>
  </td>
 </tr>
   <tr>
  <td>Dominio de Demdex<br></td>
  <td><p> A partir de la versión 20.3 de Campaign, el dominio demdex utilizado para importar y exportar audiencias a Adobe Experience Cloud está en desuso.<p>
  <p>Si utiliza el dominio demdex para sus cuentas externas de importación y exportación, deberá adaptar la implementación en consecuencia. <a href="../../integrations/using/configuring-shared-audiences-integration-in-adobe-campaign.md">Más información</a></p> 
  <p><em>Fecha de eliminación objetivo: abril de 2021</em></p>
  </td>
  <tr>
  <td>Autenticación OAuth (OAuth y JWT)<br></td>
  <td><p> A partir de la versión 20.3 de Campaign, la autenticación de integración de los activadores basada originalmente en la configuración de autenticación oAUTH para acceder a la canalización se ha cambiado y se ha movido a Adobe I/O. <p>
  <p>Si utiliza la integración de los activadores, debe adaptar la implementación en consecuencia. <a href="../../integrations/using/configuring-adobe-io.md">Más información</a></p> 
  <p>Para obtener más información sobre la depreciación de la autenticación OAuth, consulte esta <a href="https://github.com/AdobeDocs/analytics-1.4-apis/blob/master/docs/APIEOL.md">página</a>.</p> 
  <p><em>Fecha de eliminación objetivo: abril de 2021</em></p>
  </td>
  </tr>
  <td>Conectores SMS<br></td>
  <td><p> A partir de la versión Campaign 20.2, los siguientes conectores SMS quedan obsoletos.<p>
   <ul>
   <li>NetSize</li>
   <li>SMPP genérico (SMPP versión 3.4 compatible con modo binario)</li>
   <li>Sybase365 (SAP SMS 365)</li>
   <li>Comunicaciones de CLX</li>
   <li>Tele2</li>
   <li>O2</li>
   <li>iOS</li>
   </ul>
  <p>Si utiliza uno de estos conectores, debe adaptar la implementación en consecuencia. <a href="../../delivery/using/sms-channel.md">Más información</a></p> 
  <p>Descubra cómo migrar los conectores heredados en <a href="https://helpx.adobe.com/es/campaign/kb/sms-connector.html">esta nota técnica</a>.</p>
  <p><em>Fecha de eliminación objetivo: abril de 2021</em></p>
  </td> 
 </tr>
  <tr>  
   <td>canal de fax<br></td>
   <td><p>A partir de la versión Campaign 20.2, el canal de fax queda obsoleto.</p> 
   <p>Si utiliza este canal, debe adaptar la implementación en consecuencia. <a href="../../delivery/using/steps-about-delivery-creation-steps.md">Obtenga más información</a> sobre los canales de Campaign.</p>
   <p><em>Fecha de eliminación objetivo: abril de 2021</em></p></td>
  </tr>
 </tbody> 
</table>

## Funciones eliminadas {#removed-features}

Esta sección enumera las funciones y capacidades que se han eliminado de Campaign Classic.

<table> 
 <tbody> 
  <tr> 
   <td><strong>Área: función</strong></td>
   <td><strong>Sustitución</strong></td> 
  </tr> 
   <tr> 
   <td>Autenticación de Windows NT<br></td>
   <td><p>A partir de la versión 20.3 de Campaign, a autenticación de Windows NT se ha eliminado de los métodos de autenticación disponibles al configurar una nueva base de datos con Microsoft SQL Server. <a href="../../installation/using/creating-and-configuring-the-database.md#step-1---selecting-the-database-engine">Más información</a></p></td>
  </tr>
   <tr> 
   <td>Archivado de correos electrónicos basado en archivos<br></td>
   <td><p>A partir de la versión 20.2 de Campaign, el archivado de correos electrónicos basado en archivos ya no está disponible. El archivado de correo electrónico ya está disponible a través de una dirección de correo electrónico específica de CCO. <a href="../../installation/using/email-archiving.md">Más información</a></p></td>
  </tr> 
   <tr> 
   <td>Administración de posibles clientes</td>
   <td><p>A partir de la versión 20.2 de Campaign, el paquete de Administración de posibles clientes ya no está disponible. Se puede implementar una funcionalidad similar mediante otras actividades nativas del flujo de trabajo y modificaciones del modelo de datos.</p></td>
   </tr>
   <tr>
   <td>Documentación de las API Campaign: archivo jsapi.chm</td>
   <td>A partir de la versión 19.1 de Campaign, las API de Campaign Classic están disponibles en una página dedicada. Si utilizó el archivo jsapi.chm heredado, debería consultar la <a href="https://docs.adobe.com/content/help/en/campaign-classic/technicalresources/api/index.html">nueva versión en línea</a>.</td>
  </tr> 
  <tr> 
   <td>Organización de campañas - Marketing predictivo</td>
   <td>A partir de la versión 18.10 de Campaign, las funcionalidades de marketing predictivas ya no están disponibles.</td>
  </tr> 
  <tr> 
   <td>Aplicaciones web: micrositios</td>
   <td>A partir de la versión 18.10 de Campaign, los micrositios ya no están disponibles. Puede mejorar la seguridad restringiendo el acceso solo a dominios dedicados en archivos de configuración de Adobe Campaign, y utilizar direcciones URL personalizadas en Campaign mediante alias DNS. <a href="https://helpx.adobe.com/es/campaign/kb/domain-name-delegation.html">Más información</a></td>
  </tr> 
  <tr> 
   <td>Notificaciones push: conector binario de iOS</td>
   <td>Por recomendación de Apple, Adobe ha eliminado el conector binario heredado de iOS a partir de la versión 18.10 de Campaign. Ya está disponible el conector basado en HTTP/2 más funcional y eficiente.</td>
  </tr> 
  <tr> 
   <td>API decryptString</td>
   <td><p>A partir de la versión 18.6 de Campaign y por motivos de seguridad, la API <em>decryptString</em> ya no está disponible de forma predeterminada en las nuevas instalaciones.</p> 
   <p>En el contexto de una actualización posterior a la versión 18.6 (y versiones posteriores), esta API ya no se activa y se ha sustituido por la función <em>decryptPassword. </em> <a href="https://docs.adobe.com/content/help/en/campaign-classic/technicalresources/api/f-decryptPassword.html?hl=decrypt">Más información</a></p></td>
  </tr> 
   <tr> 
   <td>Canal móvil: mensajes push de MMS y WAP</td>
   <td>A partir de la versión 18.4 de Campaign, los canales push MMS y Wap ya no están disponibles. Como reemplazo, puede aprovechar los envíos por <a href="../../delivery/using/sms-channel.md">SMS</a> y <a href="../../delivery/using/about-mobile-app-channel.md">Push</a>.</td>
  </tr> 
   <tr> 
   <td>Canal móvil: LINE v1</td>
   <td>A partir de la versión 18.4 de Campaign, el paquete LINE Connect ya no está disponible. Adobe recomienda utilizar el nuevo paquete LINE Channel como reemplazo. <a href="../../delivery/using/line-channel.md">Más información</a></td>
  </tr> 
 </tbody> 
</table>

## Compatibilidad obsoleta {#deprecated-compatibility}

Los siguientes sistemas son obsoletos para Campaign Classic. Consulte la [Matriz de compatibilidades](../../rn/using/compatibility-matrix.md) para actualizar a una versión más reciente o pasar a un sistema nuevo antes de que finalice el periodo de compatibilidad.

### Versión de Adobe Campaign 20.2 {#compat-20-2-release}

A partir de la versión 20.2, los conectores SMS heredados quedan obsoletos. Consulte la sección [Funciones obsoletas](#deprecated-features)

## Fin de compatibilidad {#end-of-compatibility}

>[!CAUTION]
>
>Adobe Campaign Classic es compatible con todos los sistemas y herramientas enumerados en la [Matriz de compatibilidad](../../rn/using/compatibility-matrix.md). Cuando las versiones específicas de estos sistemas y herramientas de terceros llegan al final de su vida útil (EOL) con sus respectivos creadores, Adobe Campaign ya no es compatible con ellas: se anuncian como funciones obsoletas y, después, se eliminan de nuestra matriz de compatibilidad en la versión posterior del producto. Para evitar problemas, compruebe que se encuentra en una versión compatible de cualquier sistema enumerado en la matriz de compatibilidad.

### Consola de cliente {#client-console-eol}

La consola del cliente de Adobe Campaign Classic ya no se puede ejecutar en los siguientes sistemas, ya que su editor los ha desaprobado. Los clientes que ejecuten la consola de cliente de Campaign en una de estas versiones deben actualizar a la versión más reciente antes de la fecha de eliminación objetivo. Consulte la [matriz de compatibilidades](../../rn/using/compatibility-matrix.md).

* Windows Server 2003, 2008, 2008 R2
* Windows 7, XP, Vista

>[!NOTE]
>A partir de la versión 20.1 de Campaign, la consola de cliente de 32 bits de Campaign Classic ya no es compatible con las versiones más recientes de Campaign. Debe utilizar la consola de cliente de 64 bits.


### Sistemas operativos {#o-s-eol}

A partir de la versión 19.1, Adobe Campaign deja de ser compatible con los siguientes sistemas operativos.

* CentOS 6 [Más información](https://wiki.centos.org/Download)
* Debian 7. [Más información](https://wiki.debian.org/DebianReleases)
* RHEL 6.x. [Más información](https://access.redhat.com/support/policy/updates/errata)
* Windows Server 2008. [Más información](https://support.microsoft.com/es-es/lifecycle/search/1163)
* SLES 11. [Más información](https://www.suse.com/lifecycle)

### Servidores web {#web-server-eol}

A partir de la versión de primavera (19.1), Adobe Campaign deja de ser compatible con el siguiente servidor web.

* Apache 2.2. [Más información](https://httpd.apache.org/)
* Microsoft IIS 7. [Más información](https://support.microsoft.com/es-es/lifecycle/search/810)

### Herramientas {#tools-eol}

A partir de la versión de primavera (19.1), Adobe Campaign deja de ser compatible con las siguientes herramientas.

* Java JDK 7. [Más información](http://www.oracle.com/technetwork/java/javase/eol-135779.html)
* Libre Office 3.5 / 4.3 / 5.x, excepto cuando se incorpora en otra herramienta. [Más información](https://wiki.documentfoundation.org/ReleasePlan/Archive#End-of-Life_Releases)

### Motores de bases de datos {#dbe-eol}

Adobe no admite los siguientes motores de bases de datos, ya que su editor los ha desaprobado. Los clientes que ejecutan estas versiones deben actualizar a la versión más reciente o pasar a otra.

Consulte la [Matriz de compatibilidades de Campaign](../../rn/using/compatibility-matrix.md) para acceder a la lista de versiones compatibles.

**Acceso de datos federado (FDA)**

A partir de la versión 20.2, Adobe Campaign deja de ser compatible con el siguiente servidor FDA:

* DB2 UDB 10.5

A partir de la versión de primavera (19.1), Adobe Campaign deja de ser compatible con los siguientes servidores FDA:

* PostgreSQL 9.3. [Más información](https://www.postgresql.org/support/versioning)
* MySQL 5.5. [Más información](http://www.fromdual.com/support-for-mysql-from-oracle)
* DB2 9.5. [Más información](http://www-01.ibm.com/support/docview.wss?uid=swg21168270)
* Teradata 14 versión 14.1. [Más información](https://community.teradata.com/t5/Database/Teradata-Database-Product-Life-Cycle/td-p/35068)

Campaign Classic no es compatible con los siguientes servidores de acceso de datos federado (FDA).

* DB2 UDB 9.5, 9.7. La versión más reciente de DB2 es compatible mediante el acceso de datos federado (FDA). [Más información](http://www-01.ibm.com/support/docview.wss?uid=swg21168270)
* Oracle 9i, 10G R2. Las versiones más recientes de Oracle son compatibles mediante el acceso de datos federado (FDA). [Más información](http://www.oracle.com/us/support/library/lifetime-support-technology-069183.pdf)
* PostgreSQL 8.3, 8.4, 9.0, 9.1, 9.2. Las versiones más recientes de PostgreSQL son compatibles con el acceso de datos federados (FDA). [Más información](https://www.postgresql.org/support/versioning)
* MSSQL 2000, 2005, 2008 R2. Las versiones más recientes de SQL Server son compatibles mediante el acceso de datos federado (FDA). [Más información](https://support.microsoft.com/es-es/lifecycle/search/1044)
* MySQL 5.1. Las versiones más recientes de MySQL son compatibles mediante acceso de datos federado (FDA). [Más información](https://es.wikipedia.org/wiki/InfiniDB)
* InfiniDB llegó al fin de su vida útil. [Más información](https://www.mysql.com/support)
* Teradata 13, 13.1. Las versiones más recientes de Teradata son compatibles mediante el acceso de datos federado (FDA). [Más información](https://www.info.teradata.com/download.cfm?ItemID=1007255)
* Netezza 6.02, 7.0. Netezza llegó al final de su vida. [Más información](https://en.wikipedia.org/wiki/Netezza)
* AsterData 5.0. AsterData llegó al final de su vida. [Más información](https://en.wikipedia.org/wiki/Aster_Data_Systems)
* Sybase IQ 15.2, 15.4, 15.5 y Sybase ASE 15.0. Las versiones más recientes de Sybase son compatibles con Acceso de datos federado (FDA). [Más información](https://sites.google.com/site/dbatipsandtricks/time-tracker)
* Hadoop a través de HiveSQL: Hadoop 2.7.3, HiveSQL 1.2.1. Adobe Campaign Classic seguirá siendo compatible con las versiones de Hadoop incluidas en la lista a través de HiveSQL a través del Acceso de datos federado (FDA), pero estas versiones se combinan con: HortonWorks (HDP 2.4.X, 2.5.x, 2.6.x) y HDInsight 3.4 (HDP 2.4), 3.5 (HDP 2.5), 3.6 (HDP 2.6)

**Servidor RDBMS**

Adobe Campaign no es compatible con los siguientes servidores RDBMS:
* Oracle 10GR2
* PostgreSQL 9.0 a 9.3
* SQL Server 2005
* MySQL 5.1
* DB2 UDB 9.7
