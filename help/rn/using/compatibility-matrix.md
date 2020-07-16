---
title: Matriz de compatibilidad
description: Matriz de compatibilidad
page-status-flag: never-activated
uuid: 269d590c-5a6d-40b9-a879-02f5033863fc
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: rns
content-type: reference
topic-tags: latest-release-notes
discoiquuid: 5df34f55-135a-4ea8-afc2-f9427ce5ae7b
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 5e8598fd445f6e2ebd891af1e15c07eb836cd647
workflow-type: tm+mt
source-wordcount: '621'
ht-degree: 78%

---


# Matriz de compatibilidad{#compatibility-matrix}

This document lists all systems and components supported for the latest build of **Adobe Campaign Classic (v6.11 and v7)**. Los productos y las versiones que no forman parte de esta lista no son compatibles con Adobe Campaign.

## Notas importantes{#important-notes}

Esta matriz se actualiza regularmente: se agregan nuevos elementos admitidos y se eliminan otros obsoletos.

A menos que se indique lo contrario, se admiten todas las versiones menores.

Adobe Campaign Classic es compatible con todos los sistemas y herramientas enumerados en esta página. Cuando las versiones específicas de estos sistemas y herramientas de terceros llegan al final de su vida útil (EOL) con sus respectivos creadores, Adobe Campaign ya no es compatible con ellas y se eliminan de nuestra matriz de compatibilidades en la versión posterior del producto. Para evitar problemas, compruebe que se encuentra en una versión compatible de cualquier sistema enumerado en la matriz de compatibilidad.

Para obtener más información sobre los elementos obsoletos, consulte [esta página](../../rn/using/deprecated-features.md).

## Sistemas operativos{#OperatingSystems}

<table> 
<tbody> 
<tr> 
<td>CentOs</td>
<td>
<p>7.x (64 bits)</p>
</td>
</tr>
<tr>
<td>Debian</td>
<td>
<p>8 (64 bits)</p>
<p>9 (64 bits)</p>
<p>10 (64 bits)</p>
</td>
</tr>
<tr>
<td>RHEL</td>
<td>
<p>7.x (64 bits)</p>
<p><strong>Importante:</strong> Si está utilizando RHEL, debe estar dispuesto a deshabilitar SELinux o a que sus arquitectos escriban reglas SELinux personalizadas para verificar que un SELinux habilitado no esté causando problemas con las operaciones de Campaña.</p>
</td>
</tr>
<tr>
<td>Windows Server</td>
<td>
<p>2012</p>
<p>2012R2</p>
<p>2016</p>
</td>
</tr>
</tbody>
</table>

## Servidor web{#WebServers}

<table>
<tbody>
<tr>
<td>Microsoft IIS</td>
<td>
<p>8.0 en Windows Server 2012: Windows 8</p>
<p>8.5 en Windows Server 2012 R2</p>
<p>10.0 en Windows Server 2016</p>
</td>
</tr>
<tr>
<td>Apache</td>
<td>
<p>2.4 para RHEL7: CentOS 7, Debian 8/9, Windows (64 bits)</p>
</td>
</tr>
</tbody>
</table>

## Herramientas{#Tools}

<table>
<tbody>
<tr>
<td>Kit de desarrollo de Java (JDK)</td>
<td>
<p>8</p>
<p>9</p>
<p>La aplicación ha sido aprobada para el Kit de Desarrollo de Java (JDK) desarrollado por Oracle y para OpenJDK.</p>
</td>
</tr>
<tr>
<td>Libre Office</td>
<td>
<p>6 (y versiones anteriores si están incrustadas en el sistema)</p>
</td>
</tr>
<tr>
<td>SpamAssassin</td>
<td>
<p>3.4.x</p>
</td>
</tr>
</tbody>
</table>

## Controladores RDBMS{#RDBMSdrivers}

Se admiten los siguientes controladores RDBMS:

* Oracle SQL*Net 11

* Oracle SQL*Net 12

* PostgreSQL (libpq)

* SQLServer

* DB2 (controlador ODBC)


>[!NOTE]
>
>El controlador RDBMS debe coincidir con la versión del servidor RDBMS.

## Servidores RDBMS{#RDBMSservers}

<table>
<tbody>
<tr>
<td>Oracle</td>
<td>
<p>11g R2</p>
<p>12c</p>
<p>18c</p>
<p>19c</p>
</td>
</tr>
<tr>
<td>PostgreSQL</td>
<td>
<p>9.4.x</p>
<p>9.5.x</p>
<p>9.6.x</p>
<p>10.x</p>
<p>11.x</p>
<p>Nota: también puede utilizar Amazon RDS para PostgreSQL con las versiones especificadas arriba.</p>
</td>
</tr>
<tr>
<td>SQL Server</td>
<td>
<p>2012: SP1 y SP2</p>
<p>2014</p>
<p>2016</p>
<p>2017</p>
<p>Advertencia: Microsoft SQL Server no se admite como base de datos principal cuando el servidor de Campaña se está ejecutando en Linux. Consulte la <a href="https://docs.campaign.adobe.com/doc/AC/en/INS_Prerequisites_and_recommendations__Database.html#Microsoft_SQL_Server">Guía de instalación</a>.</p>
</td>
</tr>
</tbody>
</table>

>[!NOTE]
>
>PostgreSQL es el servidor de bases de datos predeterminado para entornos alojados.

## Conectores CRM{#CRMconnectors}

<table>
<tbody>
<tr>
<td>API de conector de Salesforce</td>
<td>
<p>Versión de API 37</p>
</td>
</tr>
<tr>
<td>API de SFDC</td>
<td>
<p>Versión de API 15</p>
<p>Versión de API 21</p>
</td>
</tr>
<tr><td>API de Oracle On Demand</td>
<td>
<p>API de Web Services 1.0</p>
</td>
</tr>
<tr>
<td>MS Dynamics</td>
<td>
<p>API de Soap: On-Premise: 2007, 2015, 2016</p>
<p>API de Soap: En línea: 2015, 2016</p>
<p>API web: On-Premise y en línea: 365, 2016, 2016 Actualización 1</p>
</td>
</tr>
</tbody>
</table>

## Acceso de datos federado (FDA){#FederatedDataAccessFDA}

<table>
<tbody>
<tr>
<td>Microsoft Azure Synapse Analytics</td>
<td> </td>
</tr>
<tr>
<td>Amazon Redshift</td>
<td><p> </p>
</td>
</tr>
<tr>
<td>Oracle</td>
<td>
<p>11g</p>
<p>12c</p>
<p>18c</p>
</td>
</tr>
<tr>
<td>PostgreSQL</td>
<td>
<p>9.4.x</p>
<p>9.5.x</p>
<p>9.6.x</p>
<p>10.x</p>
<p>11.x</p>
</td>
</tr>
<tr><td>SQL Server</td>
<td>
<p>2012 SP1 y SP2</p>
<p>2014</p>
<p>2016</p>
<p>2017</p>
</td>
</tr>
<tr><td>MySQL</td>
<td>
<p>5.7</p>
</td>
</tr>
<tr>
<td>Teradata</td>
<td>
<p>15.0</p>
<p>15.10</p>
<p>16</p>
<p>16.20</p>
</td>
</tr>
<tr>
<td>Netezza</td>
<td>
<p>7.2</p>
</td>
</tr>
<tr>
<td>Sybase</td>
<td>
<p>IQ 16</p>
<p>ASE 15.7</p>
</td>
</tr>
<tr>
<td>SAP HANA</td>
<td>
<p>versión 1 SP12 o superior</p>
</td>
</tr>
<tr><td>Hadoop a través de HiveSQL</td>
<td>
<p>HortonWorks HDP 2.4.X, 2.5.x, 2.6.x</p>
<p>HDInsight 3.4 (HDP 2.4), 3.5 (HDP 2.5), 3.6 (HDP 2.6)</p>
<p>Cloudera CDH6.x</p>
</td>
</tr>
<tr>
<td>Snowflake</td>
<td> </td>
</tr>
</tbody>
</table>

## Sistemas operativos de la consola del cliente{#ClientConsoleoperatingsystems}

<table>
<tbody>
<tr>
<td>Windows Server</td>
<td>
<p>2012</p>
<p>2016</p>
</td>
</tr>
<tr>
<td>Windows</td>
<td>
<p>8</p>
<p>10 (recomendado para instancias en japonés)</p>
</td>
</tr>
</tbody>
</table>

## Mobile SDK{#MobileSDK}

<table>
<tbody>
<tr>
<td>Android</td>
<td>
<p>7.x</p>
<p>8.x</p>
<p>9.0</p>
<p>con la versión 1.0.27 del SDK móvil.</p>
</td>
</tr>
<tr>
<td>iOS</td>
<td>
<p>iOS9</p>
<p>iOS10</p>
<p>iOS11</p>
<p>iOS12</p>
<p>iOS13</p>
<p>con la versión 1.0.26 del SDK móvil, compatible con las versiones de 32 y 64 bits.</p>
</td>
</tr>
</tbody>
</table>

## Navegadores{#Browsers}

Se admite la versión 11 de Internet Explorer.

Para los siguientes exploradores, se admite la versión más reciente:

* Microsoft Edge

* Firefox

* Chrome

* Safari

## Integraciones de Experience Cloud{#ExperienceCloudintegrations}

For integrations with Adobe solutions, refer to this [section](https://docs.adobe.com/content/help/es-ES/campaign-classic/using/integrating-with-adobe-experience-cloud/about-campaign-integrations.html#experience-cloud-integrations).

## Más parecido a esto{#Morelikethis}

* [Notas de la versión de Campaign Classic](https://docs.adobe.com/content/help/es-ES/campaign-classic/using/release-notes/latest-release.html)
* [Guía de instalación](https://docs.adobe.com/content/help/es-ES/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/general-architecture.html)
* [Características y sistemas obsoletos](https://helpx.adobe.com/es/campaign/kb/deprecated-and-removed-features.html)
* [Generar procedimiento de actualización](https://helpx.adobe.com/es/campaign/kb/acc-build-upgrade.html)
* [Matriz de compatibilidades de Campaign Classic para la versión 19.0](https://helpx.adobe.com/es/campaign/kb/compatibility-matrix-19-0.html)
* [Matriz de compatibilidades de Campaign Classic para la versión 19.1](https://helpx.adobe.com/es/campaign/kb/compatibility-matrix-19-1.html)

