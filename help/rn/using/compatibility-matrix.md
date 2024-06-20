---
product: campaign
title: Matriz de compatibilidad para Campaign Classic
description: Matriz de compatibilidades de Campaign Classic
feature: Release Notes
role: User
level: Beginner
exl-id: b8c1f287-06f4-4c34-8cca-b0c7676abbc2
source-git-commit: b23632d0718d62d61e94e636937b93aa39bbe43f
workflow-type: tm+mt
source-wordcount: '840'
ht-degree: 64%

---

# Matriz de compatibilidad {#compatibility-matrix}

En su [última compilación](../../rn/using/latest-release.md), Adobe Campaign Classic v7 es compatible con todos los sistemas y herramientas enumerados en esta página. Cuando las versiones específicas de estos sistemas y herramientas de terceros llegan al final de su vida útil (EOL) con sus respectivos creadores, Adobe Campaign ya no es compatible con ellas y se eliminan de nuestra matriz de compatibilidades en la versión posterior del producto. Para evitar problemas, compruebe que se encuentra en una versión compatible de cualquier sistema enumerado en esta matriz de compatibilidad. Para obtener más información sobre los elementos obsoletos, visite [esta página](../../rn/using/deprecated-features.md).

A menos que se indique lo contrario, se admiten todas las versiones secundarias.

>[!CAUTION]
>
>Esta matriz se actualiza regularmente: se añaden nuevos sistemas y herramientas compatibles y se eliminan los obsoletos.

## Sistemas operativos {#OperatingSystems}

Como cliente On-Premise/híbrido, debe instalar Adobe Campaign en uno de los sistemas operativos que se indican a continuación. Obtenga más información sobre los pasos de instalación de Campaign Classic v7 en [esta página](../../installation/using/application-server.md).

<table> 
<tbody> 
<td><strong>Sistema operativo</strong></td>
<td><strong>Versión del sistema operativo</strong></td>
<td><strong>Versión mínima de la campaña</strong></td>
<tr> 
<td>CentOs</td>
<td>
<p>7.x</p>
</td>
<td>
<p></p>
</td>
</tr>
<tr>
<td>Debian</td>
<td>
<p>11</p>
<p>10</p>
</td>
<td>
<p>Versión 7.3</p>
<p></p>
</td>
</tr>
<tr>
<td>RHEL</td>
<td>
<p>9.x</p>
<p>8.x</p>
<p>7.x</p>
</td>
<td>
<p>Versión 7.4</p>
<p></p>
<p></p>
</td>
</tr>
<tr>
<td>Windows Server</td>
<td>
<p>2022</p>
<p>2019</p>
<p>2016</p>
</td>
<td>
<p>Versión 7.4</p>
<p>Versión 7.2</p>
<p></p>
</td>
</tr>
</tbody>
</table>

>[!IMPORTANT]
>
>Si utiliza RHEL, debe estar dispuesto a deshabilitar [SELinux](../../installation/using/prerequisites-of-campaign-installation-in-linux.md#selinux) o que sus arquitectos escriban reglas SELinux personalizadas para comprobar que un SELinux habilitado no esté causando problemas con las operaciones de Campaign.

## Servidores web {#WebServers}

Como cliente On-Premise/híbrido, según su sistema operativo, deberá integrar Campaign en uno de los servidores web que se indican a continuación. Obtenga más información acerca de los pasos de configuración de los servidores web en [esta página](../../installation/using/integration-into-a-web-server-for-windows.md) (para Windows) y [esta página](../../installation/using/integration-into-a-web-server-for-linux.md) (para Linux).

<table>
<tbody>
<tr>
<td>Microsoft IIS</td>
<td>
<p>10.0 en Windows Server</p>
</td>
</tr>
<tr>
<td>Apache</td>
<td>
<p>2,4</p>
</td>
</tr>
</tbody>
</table>

## Herramientas {#Tools}

Como cliente On-Premise/híbrido, debe instalar y configurar las herramientas que se indican a continuación. [Más información](../../installation/using/application-server.md).

<table>
<tbody>
<td><strong>Herramienta</strong></td>
<td><strong>Versión</strong></td>
<td><strong>Versión mínima de Campaign</strong></td>
<tr>
<td><p>Kit de desarrollo de Java (JDK)</p>
<p>Obtenga más información en <a href="../../installation/using/application-server.md#jdk" target="_blank">esta página</a>.</p>
</td>
<td>
<p>11</p>
<p>9</p>
<p>8</p>
<p></p>
</td>
<td>
<p>necesario a partir de la versión 7.4.1</p>
<p>hasta la versión 7.4.1</p>
<p>hasta la versión 7.4.1</p>
</tr>
<tr>
<td><p>Libre Office</p></td>
<td>
<p>7 (y versiones anteriores si están incrustadas en el sistema)</p>
</td>
<td>
<p></p>
</td>
</tr>
<tr>
<td><p>SpamAssassin</p></td>
<td>
<p>3.4.x</p>
</td>
<td>
<p></p>
</td>
</tbody>
</table>

## Sistemas de administración de bases de datos de relación (RDBMS) {#RDBMSservers}

Como cliente On-Premise/híbrido, debe instalar y configurar una de las bases de datos que se indican a continuación. [Más información](../../installation/using/creating-and-configuring-the-database.md).


<table>
<tbody>
<td><strong>Sistema de bases de datos</strong></td>
<td><strong>Versión de la base de datos</strong></td>
<td><strong>Versión mínima de la campaña</strong></td>
<tr>
<td>Oracle</td>
<td>
<p>23c</p>
<p>19c</p>
<p>18c</p>
<p>12c</p>
<p>11g R2</p>
</td>
<td>
<p>Versión 7.4</p>
<p></p>
<p></p>
<p></p>
<p></p>
</td>
</tr>
<tr>
<td>PostgreSQL</td>
<td>
<p>14.x</p>
<p>13.x</p>
<p>12.x</p>
<p>11.x</p>
</td>
<td>
<p>Versión 7.3.2</p>
<p></p>
<p></p>
<p></p>
</td>
</tr>
<tr>
<td>Microsoft SQL Server</td>
<td>
<p>2022</p>
<p>2019</p>
<p>2017</p>
<p>2016</p>
<p>2014</p>
</td>
<td>
<p>Versión 7.4</p>
<p></p>
<p></p>
<p></p>
<p></p>
</td>
</tr>
</tbody>
</table>

>[!NOTE]
>
>* El controlador RDBMS debe coincidir con la versión del servidor RDBMS.
>
>* Microsoft SQL Server no se admite como base de datos principal cuando el servidor de Campaign se ejecuta en Linux. [Más información](../../installation/using/prerequisites-of-campaign-installation-in-linux.md#database-access-layers).
>
>* También puede utilizar Amazon RDS para PostgreSQL con las versiones especificadas anteriormente.
>
>* PostgreSQL es el RDBMS para entornos alojados o de Managed Cloud Services.


## Conectores CRM {#CRMconnectors}

A continuación se enumeran los sistemas de gestión de relaciones con el cliente (CRM) compatibles con Adobe Campaign. [Más información](../../platform/using/crm-connectors.md) acerca de los conectores CRM de Campaign.

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
<p>API web</p>
</td>
</tr>
</tbody>
</table>

## Acceso de datos federado (FDA){#FederatedDataAccessFDA}

A continuación se enumeran las bases de datos externas compatibles con el [módulo de acceso de datos federado](../../installation/using/about-fda.md) de Adobe Campaign. La compatibilidad depende de su [modelo hosting](../../installation/using/hosting-models.md).

Los entornos **Managed Services** (alojados), **Híbrido** y **On-Premise** pueden conectar Campaign con los siguientes sistemas de bases de datos externas:

<table>
<tbody>
<td><strong>Sistema de bases de datos</strong></td>
<td><strong>Versión de la base de datos</strong></td>
<td><strong>Versión mínima de la campaña</strong></td>
<tr>
<td>Amazon Redshift</td>
<td><p> </p>
<td>Versión 7.0 19.1.4</td>
</td>
</tr>
<tr>
<td>Google BigQuery</td>
<td> </td>
<td>Versión 7.2</td>
</tr>
<tr>
<td>PostgreSQL</td>
<td>
<p>14.x</p>
<p>13.x</p>
<p>12.x</p>
<p>11.x</p>
</td>
<td>Versión 7.0 19.1.4</td>
</tr>
<tr>
<td>Snowflake</td>
<td> </td>
<td>Versión 7.2</td>
</tr>
<tr>
<td>Vertica Analytics</td>
<td> </td>
<td>Versión 7.0 19.1.4 </td>
</tr>
</tbody>
</table>

Los entornos **Híbrido** y **On-Premise** pueden conectar a Campaign con los siguientes sistemas de bases de datos externos: Estos sistemas no **son compatibles** con los entornos (hospedados) de **Managed Services** de Campaign.

<table>
<tbody>
<td><strong>Sistema de bases de datos</strong></td>
<td><strong>Versión de la base de datos</strong></td>
<td><strong>Versión mínima de la campaña</strong></td>
<tr>
<td>Microsoft Azure Synapse Analytics</td>
<td> </td>
<td></td>
</tr>
<tr><td>MySQL</td>
<td>
<p>8</p>
<p>5.7</p>
</td>
<td>
<p>Versión 7.3</p>
<p></p>
</td>
</tr>
<tr>
<td>Netezza</td>
<td>
<p>Versión 7.2</p>
</td>
<td></td>
</tr>
<tr>
<td>Oracle</td>
<td>
<p>23c</p>
<p>19c</p>
<p>18c</p>
<p>12c</p>
<p>11g </p>
</td>
<td>
<p>Versión 7.4</p>
<p></p>
<p></p>
<p></p>
<p></p>
</td>
</tr>
<tr>
<td>SAP HANA</td>
<td>
<p>versión 1 SPS 12</p>
</td>
<td></td>
</tr>
<tr><td>SQL Server</td>
<td>
<p>2022 (a partir de la versión 7.4 de Campaign)</p>
<p>2019</p>
<p>2017</p>
<p>2016</p>
<p>2014</p>
<p>2012 SP1 y SP2</p>
</td>
<td></td>
</tr>
<tr>
<td>Sybase</td>
<td>
<p>IQ 16</p>
<p>ASE 15.7</p>
</td>
<td></td>
</tr>
<tr>
<td>Teradata</td>
<td>
<p>17.x</p>
<p>16.x (última versión)</p>
</td>
<td></td>
</tr>
<tr><td>Hadoop a través de HiveSQL</td>
<td>
<p>HortonWorks HDP 2.4.X, 2.5.x, 2.6.x</p>
<p>HDInsight 3.4 (HDP 2.4), 3.5 (HDP 2.5), 3.6 (HDP 2.6)</p>
<p>Cloudera CDH6.x</p>
</td>
<td></td>
</tr>
</tbody>
</table>


## Consola del cliente {#ClientOS}

Se **requieren** los siguientes sistemas operativos y exploradores para utilizar la [Consola del cliente de Campaign](../../installation/using/installing-the-client-console.md).

### Sistemas operativos

<table>
<tbody>
<td><strong>Sistema</strong></td>
<td><strong>Versión del SO</strong></td>
<td><strong>Versión mínima de Campaign</strong></td>
<tr>
<td>Microsoft Windows</td>
<td>
<p>11</p>
<p>10</p>
</td>
<td>
<p>Versión 7.3</p>
<p></p>
<p></p>
</tr>
<tr>
<td>Microsoft Windows Server</td>
<td>
<p>2022</p>
<p>2019</p>
<p>2016</p>
</td>
<td>
<p>Versión 7.4.1</p>
<p>Versión 7.2.1</p>
<p></p>
</tbody>
</table>

### Tiempo de ejecución de Microsoft WebView2 {#webview}

La última versión en tiempo de ejecución de Microsoft Edge WebView2 es obligatoria en la consola del cliente de Campaign.

Descargar Microsoft Edge WebView2 del [sitio de Microsoft Developer](http://www.adobe.com/go/acc-ms-webview2-runtime-download).


## SDK móvil {#MobileSDK}

Puede utilizar Campaign para lo siguiente [enviar notificaciones push](../../delivery/using/about-mobile-app-channel.md)mediante el SDK de Adobe Experience Platform Mobile, configurando la extensión de Adobe Campaign en la interfaz de usuario de la recopilación de datos.

El SDK de Campaign es [obsoleto](deprecated-features.md) a partir de Campaign v7.4. Para garantizar una transición sin problemas de la implementación existente al SDK de AEP Mobile, aún puede utilizarlo en los sistemas operativos que se enumeran a continuación<!--, using the associated [mobile SDK](../../delivery/using/integrating-campaign-sdk-into-the-mobile-application.md)-->.


<table>
<tbody>
<tr>
<td>Google Android</td>
<td>
<p>7 - 14</p>
<p>con la versión 1.1.1 del SDK móvil.</p>
<p>Android 13 y 14 son compatibles a partir de la versión 7.4 de Campaign.</p>
<p>Android 12 es compatible a partir de la versión 7.3 de Campaign.</p>
</td>
</tr>
<tr>
<td>Apple iOS</td>
<td>
<p>iOS 9 - 17</p>
<p>con la versión 1.0.26 del SDK móvil.</p>
<p>Apple iOS 15 es compatible a partir de la versión 7.3 de Campaign. </p>
<p>Apple iOS 16 y 17 son compatibles a partir de la versión 7.4 de Campaign.</p>
</td>
</tr>
</tbody>
</table>

## Exploradores {#Browsers}

Los siguientes exploradores, en su última versión, son compatibles con Campaign para [Acceso web](../../campaign/using/accessing-marketing-campaigns.md#using-the-web-interface-).

* Google Chrome
* Microsoft Edge
* Mozilla Firefox
* Safari



>[!MORELIKETHIS]
>
>* [Notas de la versión de Campaign Classic](../../rn/using/latest-release.md)
>* [Arquitectura general de Campaign](../../installation/using/general-architecture.md)
>* [Recomendaciones de tamaño de hardware](../../technotes/using/hardware-sizing.md)
>* [Funcionalidades y sistemas obsoletos](../../rn/using/deprecated-features.md)
>* [Generar procedimiento de actualización](../../production/using/build-upgrade.md)
