---
solution: Campaign Classic
product: campaign
title: Matriz de compatibilidad para Campaign Classic
description: Matriz de compatibilidades de Campaign Classic
feature: Información general
role: Business Practitioner
level: Beginner
exl-id: b8c1f287-06f4-4c34-8cca-b0c7676abbc2
translation-type: ht
source-git-commit: 6854d06f8dc445b56ddfde7777f02916a60f2b63
workflow-type: ht
source-wordcount: '524'
ht-degree: 100%

---

# Matriz de compatibilidad{#compatibility-matrix}

Este documento enumera todos los sistemas y componentes compatibles con [la última versión](../../rn/using/latest-release.md) de **Adobe Campaign Classic**. Los productos y las versiones que no forman parte de esta lista no son compatibles con Adobe Campaign.

Si usa [!DNL Gold Standard], consulte la matriz de compatibilidad de [[!DNL Gold Standard] ](../../rn/using/compatibility-matrix-gs.md).

## Notas importantes{#important-notes}

A menos que se indique lo contrario, se admiten todas las versiones menores.

En su [última versión](../../rn/using/latest-release.md), Adobe Campaign Classic es compatible con todos los sistemas y herramientas enumerados en esta página. Cuando las versiones específicas de estos sistemas y herramientas de terceros llegan al final de su vida útil (EOL) con sus respectivos creadores, Adobe Campaign ya no es compatible con ellas y se eliminan de nuestra matriz de compatibilidades en la versión posterior del producto. Para evitar problemas, compruebe que se encuentra en una versión compatible de cualquier sistema enumerado en la matriz de compatibilidad.

Para obtener más información sobre los elementos obsoletos, visite [esta página](../../rn/using/deprecated-features.md).

>[!CAUTION]
>
>Esta matriz se actualiza regularmente: se agregan nuevos elementos admitidos y se eliminan otros obsoletos.

## Sistemas operativos{#OperatingSystems}

<table> 
<tbody> 
<tr> 
<td>CentOs</td>
<td>
<p>8.x (64 bits)</p>
<p>7.x (64 bits)</p>
</td>
</tr>
<tr>
<td>Debian</td>
<td>
<p>10 (64 bits)</p>
<p>9 (64 bits)</p>
<p>8 (64 bits)</p>
</td>
</tr>
<tr>
<td>RHEL</td>
<td>
<p>8.x (64 bits)</p>
<p>7.x (64 bits)</p>
<p><strong>Importante:</strong> Si está utilizando RHEL, debe estar dispuesto a deshabilitar SELinux o a que sus arquitectos escriban reglas SELinux personalizadas para comprobar que un SELinux habilitado no está causando problemas con las operaciones de Campaign.</p>
</td>
</tr>
<tr>
<td>Windows Server</td>
<td>
<p>2016</p>
<p>2012R2</p>
<p>2012</p>
</td>
</tr>
</tbody>
</table>

## Servidores web{#WebServers}

<table>
<tbody>
<tr>
<td>Microsoft IIS</td>
<td>
<p>10.0 en Windows Server 2016</p>
<p>8.5 en Windows Server 2012 R2</p>
<p>8.0 en Windows Server 2012: Windows 8</p>
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
<p>11</p>
<p>9</p>
<p>8</p>
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

## Servidores RDBMS{#RDBMSservers}

>[!NOTE]
>
>El controlador RDBMS debe coincidir con la versión del servidor RDBMS.

<table>
<tbody>
<tr>
<td>Oracle</td>
<td>
<p>19c</p>
<p>18c</p>
<p>12c</p>
<p>11g R2</p>
</td>
</tr>
<tr>
<td>PostgreSQL</td>
<td>
<p>12.x</p>
<p>11.x</p>
<p>10.x</p>
<p>9.6.x</p>
<p>9.5.x</p>
<p>9.4.x</p>
<p>Nota: También puede utilizar Amazon RDS para PostgreSQL con las versiones especificadas anteriormente.</p>
</td>
</tr>
<tr>
<td>SQL Server</td>
<td>
<p>2019</p>
<p>2017</p>
<p>2016</p>
<p>2014</p>
<p>2012: SP1 y SP2</p>
<p>Advertencia: Microsoft SQL Server no se admite como base de datos principal cuando el servidor de Campaign se está ejecutando en Linux. <a href="https://docs.adobe.com/content/help/en/campaign-classic/using/installing-campaign-classic/prerequisites-and-recommendations-/database.html#Microsoft_SQL_Server">Más información</a>.</p>
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
<p>Versión de API 49</p>
</td>
</tr>
<tr>
<td>Conector de Microsoft Dynamics</td>
<td>
<p>API web: Dynamics 365 On-premise y en línea</p>
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
<p>19c</p>
<p>18c</p>
<p>12c</p>
<p>11g</p>
</td>
</tr>
<tr>
<td>PostgreSQL</td>
<td>
<p>12.x</p>
<p>11.x</p>
<p>10.x</p>
<p>9.6.x</p>
<p>9.5.x</p>
<p>9.4.x</p>
</td>
</tr>
<tr><td>SQL Server</td>
<td>
<p>2019</p>
<p>2017</p>
<p>2016</p>
<p>2014</p>
<p>2012 SP1 y SP2</p>
</td>
</tr>
<tr><td>MySQL</td>
<td>
<p>5,7</p>
</td>
</tr>
<tr>
<td>Teradata</td>
<td>
<p>16,20</p>
<p>16</p>
<p>15,10</p>
<p>15,0</p>
</td>
</tr>
<tr>
<td>Netezza</td>
<td>
<p>7,2</p>
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
<p>versión 1 SPS 12</p>
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
<p>2016</p>
<p>2012</p>
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
<p>7.x, 8.x, 9.0</p>
<p>con la versión 1.0.27 del SDK móvil.</p>
</td>
</tr>
<tr>
<td>iOS</td>
<td>
<p>iOS 9 - 14</p>
<p>con la versión 1.0.26 del SDK móvil, compatible con las versiones de 32 y 64 bits.</p>
</td>
</tr>
</tbody>
</table>

## Navegadores{#Browsers}

En el caso de los siguientes exploradores, se admite la versión más reciente: Microsoft Edge, Mozilla Firefox, Google Chrome y Safari.

Internet Explorer 11 es compatible.

## Más parecido a esto{#Morelikethis}

* [Notas de la versión de Campaign Classic](../../rn/using/latest-release.md)
* [Guía de instalación](../../installation/using/general-architecture.md)
* [Funcionalidades y sistemas obsoletos](../../rn/using/deprecated-features.md)
* [Generar procedimiento de actualización](../../production/using/build-upgrade.md)
