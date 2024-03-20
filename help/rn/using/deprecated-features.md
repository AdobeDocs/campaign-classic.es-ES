---
product: campaign
title: Funciones obsoletas y eliminadas de Campaign Classic
description: Esta página lista las funciones obsoletas y eliminadas de Adobe Campaign Classic
feature: Release Notes
badge-v7-only: label="v7" type="Informative" tooltip="Se aplica solo a Campaign Classic v7"
role: User
level: Beginner
exl-id: d60d67de-6618-4f3b-be4a-ad7633ab5645
source-git-commit: f3dc9d56c693f334923d627a28a9e45b92b1c0c3
workflow-type: ht
source-wordcount: '1558'
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

Esta sección enumera las características y funcionalidades que se han marcado como obsoletas en las últimas versiones de Campaign Classic.

Por lo general, las funciones que se planea eliminar en una versión posterior se definen en primer lugar como obsoletas. Estas funciones y funcionalidades ya no están disponibles para los nuevos clientes de Campaign Classic, o no deben usarse para ninguna implementación nueva. También se eliminan de la documentación del producto.

Se aconseja a los clientes que comprueben si utilizan la función o la funcionalidad en su implementación actual y que cambien su implementación. Consulte la fecha de eliminación objetivo para planificar el entorno y las actualizaciones del proyecto según corresponda.

<table> 
 <tbody> 
   <tr>
   <td><strong>Función</strong></td>
   <td><strong>Detalles</strong></td>
  </tr>
<tr>
 <td>Marketing social con Facebook</td>
 <td>El marketing social con Facebook ya no se utiliza. Puede usar la integración de X (anteriormente conocido como Twitter) para publicar en medios sociales o trabajar con Adobe para crear un canal personalizado.
 <p></p>
  <!--p>Target removal date: End of 2023</p-->
  </td>
</tr>
<tr>
 <td>Conector ACS</td>
 <td>El conector ACS (oferta Prime) ya no se utiliza. Puede utilizar las funcionalidades de exportación e importación de Campaign para extraer e insertar datos en ambos productos.<p></p>
  <!--p>Target removal date: End of 2023</p-->
  </td>
</tr>
 </tbody> 
</table>

## Funcionalidades eliminadas {#removed-features}

Esta sección enumera las funciones y capacidades que se han eliminado de Campaign Classic.

<table> 
 <tbody>
  <tr> 
   <td><strong>Función</strong></td>
   <td><strong>Detalles</strong></td>
  <tr>  
      <tr>
  <td>Conector de datos de Adobe Analytics<br></td>
   <td><p>El conector de datos de Adobe Analytics se eliminó el 17 de agosto de 2022. Ya no se utiliza en la versión 21.1.3 de Campaign.</p>
   <p>Si utiliza este conector, debe adaptar la implementación en consecuencia. <a href="../../platform/using/adobe-analytics-connector.md">Más información</a></p>
  </td>
 </tr>
    <tr>
  <td>Informe de monitorización de la capacidad de envío técnico<br></td>
   <td><p>El informe de monitorización de la capacidad de entrega técnica ya no está disponible. Ya no se utiliza en la versión 21.1.3 de Campaign.</p>
   <!--p>If needed, you can receive this report daily by email until the feature removal date. To request it, open a specific <a href="https://helpx.adobe.com/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html">Support Case</a> and specify the name of the instance and the email address(es) to send the report to.</p--> 
  </td>
 </tr>
  <tr>
  <td>Autenticación OAuth (OAuth y JWT)<br></td>
  <td><p> La autenticación de la integración de los activadores, basada originalmente en la configuración de autenticación oAUTH para acceder a la canalización, ahora se ha cambiado y se ha movido a Adobe I/O. Este modo de autenticación había quedado obsoleto con la versión 20.3 de Campaign.<p>
  <p>Si utilizaba la integración de activadores, aprenda a adaptar la implementación <a href="../../integrations/using/configuring-adobe-io.md">en esta página</a>.</p> 
  <p>Para obtener más información sobre la depreciación de la autenticación OAuth, consulte esta <a href="https://github.com/AdobeDocs/analytics-1.4-apis/blob/master/docs/APIEOL.md">página</a>.</p> 
  <!--p><em>Target removal date: October 20, 2021. Hosted environments benefit from an extension until May 25, 2022. </em></p-->
  </td>
  </tr>
   <td>Creación de informes<br></td>
   <td><p>Tras el fin de la vida útil del Flash Player de Adobe, el informe Medición y el motor de renderización Gráfico ya no están disponibles. <a href="../../reporting/using/creating-a-new-report.md">Más información</a></p>
  </tr>
  <tr>  
   <td>canal de fax<br></td>
   <td><p>A partir de la versión 21.1.3 de Campaign, el canal de fax ya no está disponible. <a href="../../delivery/using/steps-about-delivery-creation-steps.md">Más información</a></p>
  </tr>
  <tr>
  <td>Dominio de Demdex<br></td>
  <td><p> A partir de la versión 21.1.3 de Campaign, el dominio de demdex utilizado para importar y exportar audiencias a Adobe Experience Cloud ya no está disponible. <a href="../../integrations/using/configuring-shared-audiences-integration-in-adobe-campaign.md">Más información</a></p> 
  </td>
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
   <td>A partir de la versión 19.1 de Campaign, las API de Campaign Classic están disponibles en una página dedicada. Si utilizó el archivo jsapi.chm heredado, debería consultar la <a href="https://experienceleague.adobe.com/developer/campaign-api/api/index.html?lang=es">nueva versión en línea</a>.</td>
  </tr> 
  <tr> 
   <td>Orquestación de Campaign: marketing predictivo</td>
   <td>A partir de la versión 18.10 de Campaign, las funcionalidades de marketing predictivas ya no están disponibles.</td>
  </tr> 
  <tr> 
   <td>Aplicaciones web: micrositios</td>
   <td>A partir de la versión 18.10 de Campaign, los micrositios ya no están disponibles. Puede mejorar la seguridad restringiendo el acceso solo a dominios dedicados en archivos de configuración de Adobe Campaign, y utilizar direcciones URL personalizadas en Campaign mediante alias DNS.</td>
  </tr> 
  <tr> 
   <td>Notificaciones push: conector binario de iOS</td>
   <td>Por recomendación de Apple, Adobe ha eliminado el conector binario heredado de iOS a partir de la versión 18.10 de Campaign. Ya está disponible el conector basado en HTTP/2 más funcional y eficiente.</td>
  </tr> 
  <tr> 
   <td>API decryptString</td>
   <td><p>A partir de la versión 18.6 de Campaign y por motivos de seguridad, la API <em>decryptString</em> ya no está disponible de forma predeterminada en las nuevas instalaciones.</p> 
   <p>En el contexto de una actualización posterior a la versión 18.6 (y versiones posteriores), esta API ya no se activa y se ha sustituido por la función <em>decryptPassword. </em> <a href="https://experienceleague.adobe.com/developer/campaign-api/api/f-decryptPassword.html?hl=decrypt">Más información</a></p></td>
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

<!--## Deprecated compatibility {#deprecated-compatibility}

The following systems are deprecated for Campaign Classic. Please refer to the [Compatibility matrix](../../rn/using/compatibility-matrix.md) to upgrade to a newer version or move to a new system before the compatibility ends.-->

## Fin de la compatibilidad {#end-of-compatibility}

>[!CAUTION]
>
>Adobe Campaign Classic es compatible con todos los sistemas y herramientas enumerados en la [Matriz de compatibilidad](../../rn/using/compatibility-matrix.md). Cuando las versiones específicas de estos sistemas y herramientas de terceros llegan al final de su vida útil (EOL) con sus respectivos creadores, Adobe Campaign ya no es compatible con ellas: se anuncian como funciones obsoletas y, después, se eliminan de nuestra matriz de compatibilidad en la versión posterior del producto. Para evitar problemas, compruebe que se encuentra en una versión compatible de cualquier sistema enumerado en la matriz de compatibilidad.

### Consola del cliente {#client-console-eol}

La consola del cliente de Adobe Campaign Classic ya no se puede ejecutar en los siguientes sistemas, ya que su editor los ha desaprobado. Los clientes que ejecuten la consola de cliente de Campaign en una de estas versiones deben actualizar a la versión más reciente antes de la fecha de eliminación objetivo. Consulte la [matriz de compatibilidades](../../rn/using/compatibility-matrix.md).

* Windows Server 2003, 2008, 2008 R2
* Windows 7, XP, Vista

>[!NOTE]
>A partir de la versión 20.1 de Campaign, la consola de cliente de 32 bits de Campaign Classic ya no es compatible con las versiones más recientes de Campaign. Debe utilizar la consola de cliente de 64 bits.

### Sistemas operativos {#o-s-eol}


* A partir de la versión 22.1, Adobe Campaign deja de ser compatible con CentOs 8 (64 bits). CentOS Linux 8 llegó al fin de su vida útil el 31 de diciembre de 2021. [Más información](https://www.centos.org/centos-linux-eol/).

  Si utilizaba este sistema operativo, adapte la implementación en consecuencia. CentOS 7 (64 bits) y RHEL 8 y 7 (64 bits) siguen siendo compatibles.

* A partir de la versión 21.1.3, Adobe Campaign deja de ser compatible con Debian 8.

* A partir de la versión 19.1, Adobe Campaign deja de ser compatible con los siguientes sistemas operativos.

   * CentOS 6. [Más información](https://wiki.centos.org/Download)
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

* Java JDK 7. [Más información](https://www.oracle.com/technetwork/java/javase/eol-135779.html)
* Libre Office 3.5 / 4.3 / 5.x, excepto cuando se incorpora en otra herramienta. [Más información](https://wiki.documentfoundation.org/ReleasePlan/Archive#End-of-Life_Releases)

### Motores de las bases de datos {#dbe-eol}

Adobe no admite los siguientes motores de bases de datos, ya que su editor los ha desaprobado. Los clientes que ejecutan estas versiones deben actualizar a la versión más reciente o pasar a otra.

Consulte la [Matriz de compatibilidades de Campaign](../../rn/using/compatibility-matrix.md) para acceder a la lista de versiones compatibles.

**Acceso de datos federado (FDA)**

A partir de la versión 20.2, Adobe Campaign deja de ser compatible con el siguiente servidor FDA:

* DB2 UDB 10.5

A partir de la versión de primavera (19.1), Adobe Campaign deja de ser compatible con los siguientes servidores FDA:

* PostgreSQL 9.3.
* MySQL 5.5.
* DB2 9.5.
* Teradata 14 – 14.1.

Campaign Classic no es compatible con los siguientes servidores de acceso de datos federado (FDA). Utilice versiones o sistemas más recientes.

* DB2 UDB 9.5, 9.7.
* Oracle 9i, 10G R2.
* Las versiones de PostgreSQL hasta 9.6 llegaron al final de su vida útil.
* MSSQL 2000, 2005, 2008 R2.
* MySQL 5.1.
* InfiniDB llegó al fin de su vida útil.
* Teradata 13, 13.1.
* Netezza 6.02, 7.0. Netezza llegó al final de su vida.
* AsterData 5.0. AsterData llegó al final de su vida.
* Sybase IQ 15.2, 15.4, 15.5 y Sybase ASE 15.0.
* Hadoop a través de HiveSQL: Hadoop 2.7.3, HiveSQL 1.2.1. Adobe Campaign Classic sigue siendo compatible con las versiones de Hadoop incluidas en la lista a través de HiveSQL a través del Acceso de datos federado (FDA), pero estas versiones se combinan con: HortonWorks (HDP 2.4.X, 2.5.x, 2.6.x) y HDInsight 3.4 (HDP 2.4), 3.5 (HDP 2.5), 3.6 (HDP 2.6)

**SERVIDOR RDBMS**

A partir de la versión de primavera (19.1), Adobe Campaign deja de ser compatible con los siguientes servidores RDBMS:

* Oracle 10GR2
* PostgreSQL 9.0 a 9.3
* SQL Server 2005
* MySQL 5.1
* DB2 UDB 9.7

Las versiones de PostgreSQL hasta 9.6 llegaron al final de su vida útil. Por lo tanto, Adobe Campaign no los admite.

### Conectores SMS {#sms-eol}

A partir de la versión 20.2, los conectores SMS heredados quedan obsoletos. Adobe Campaign no es compatible con lo siguiente:

* SMPP genérico (SMPP versión 3.4 compatible con modo binario)
* Sybase365 (SAP SMS 365)
* Comunicaciones de CLX
* Tele2
* O2
* iOS

### Conectores CRM {#crm-connectors}

A partir de la versión Campaign 21.1, los siguientes conectores CRM quedan obsoletos:

* API de Soap: On-Premise: 2007, 2015, 2016
* API de Soap: En línea: 2015, 2016
* API web - Microsoft Dynamics CRM, 2016
* API web - Microsoft Dynamics CRM, actualización 1 de 2016
* API de Oracle bajo demanda
