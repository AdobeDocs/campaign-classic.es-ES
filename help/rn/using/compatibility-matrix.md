---
product: campaign
title: Matriz de compatibilidad para Campaign Classic
description: Matriz de compatibilidades de Campaign Classic
feature: Release Notes
badge-v7-only: label="v7" type="Informative" tooltip="Se aplica solo a Campaign Classic v7"
role: User
level: Beginner
exl-id: b8c1f287-06f4-4c34-8cca-b0c7676abbc2
source-git-commit: 3db5242e2074c6d0530258073ae83c11164d7365
workflow-type: tm+mt
source-wordcount: '772'
ht-degree: 100%

---

# Matriz de compatibilidad{#compatibility-matrix}



Este documento enumera todos los sistemas y componentes compatibles con [la última versión](../../rn/using/latest-release.md) de **Adobe Campaign Classic v7**. Los productos y las versiones que no forman parte de esta lista no son compatibles con Adobe Campaign.

Si usa [!DNL Gold Standard], consulte la matriz de compatibilidad de [[!DNL Gold Standard] ](../../rn/using/gold-standard.md#compatibility-matrix-gs).

## Notas importantes{#important-notes}

A menos que se indique lo contrario, se admiten todas las versiones secundarias.

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
<p>7.x</p>
<p><strong>Importante:</strong> Si está utilizando RHEL, debe estar dispuesto a deshabilitar SELinux o a que sus arquitectos escriban reglas SELinux personalizadas para comprobar que un SELinux habilitado no está causando problemas con las operaciones de Campaign.</p>
</td>
</tr>
<tr>
<td>Debian</td>
<td>
<p>11 (a partir de la versión 7.3 de Campaign)</p>
<p>10</p>
</td>
</tr>
<tr>
<td>RHEL</td>
<td>
<p>8.x</p>
<p>7.x</p>
<p><strong>Importante:</strong> Si está utilizando RHEL, debe estar dispuesto a deshabilitar SELinux o a que sus arquitectos escriban reglas SELinux personalizadas para comprobar que un SELinux habilitado no está causando problemas con las operaciones de Campaign.</p>
</td>
</tr>
<tr>
<td>Windows Server</td>
<td>
<p>2019 (a partir de la versión 7.2 de Campaign)</p>
<p>2016</p>
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
<p>10.0 en Windows Server 2016 y 2019</p>
</td>
</tr>
<tr>
<td>Apache</td>
<td>
<p>2.4 para RHEL7: CentOS 7, Debian 8/9, Windows</p>
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
<p>Campaign es compatible con el kit de desarrollo de Java (JDK) desarrollado por Oracle y OpenJDK.</p>
</td>
</tr>
<tr>
<td>Libre Office</td>
<td>
<p>7 (y versiones anteriores si están incrustadas en el sistema)</p>
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

## Sistemas de administración de bases de datos de relación (RDBMS){#RDBMSservers}

<table>
<tbody>
<tr>
<td>Oracle</td>
<td>
<p>19c</p>
<p>18c</p>
<p>12c</p>
<p>11g  R2</p>
</td>
</tr>
<tr>
<td>PostgreSQL</td>
<td>
<p>14.x (a partir de Campaign v7.3.2)</p>
<p>13.x</p>
<p>12.x</p>
<p>11.x</p>
<p><strong>Nota:</strong> También puede utilizar Amazon RDS para PostgreSQL con las versiones especificadas anteriormente.</p>
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
<p><strong>Importante:</strong> Microsoft SQL Server no se admite como base de datos principal cuando el servidor de Campaign se ejecuta en Linux. <a href="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/install-campaign-on-prem/installing-campaign-in-linux-/prerequisites-of-campaign-installation-in-linux.html?lang=es#database-access-layers">Más información</a>.</p>
</td>
</tr>
</tbody>
</table>

>[!NOTE]
>
>* El controlador RDBMS debe coincidir con la versión del servidor RDBMS.
>
>* PostgreSQL es el RDBMS para entornos alojados.

## Conectores CRM{#CRMconnectors}

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
<td><strong>Versión de la campaña</strong></td>
<tr>
<td>Amazon Redshift</td>
<td><p> </p>
<td>V7.0 19.1.4 mínimo</td>
</td>
</tr>
<tr>
<td>Google BigQuery</td>
<td> </td>
<td>7.2 mínimo</td>
</tr>
<tr>
<td>PostgreSQL</td>
<td>
<p>14.x</p>
<p>13.x</p>
<p>12.x</p>
<p>11.x</p>
</td>
<td>V7.0 19.1.4 mínimo</td>
</tr>
<tr>
<td>Snowflake</td>
<td> </td>
<td>7.2 mínimo</td>
</tr>
<tr>
<td>Vertica Analytics</td>
<td> </td>
<td>V7.0 19.1.4 mínimo</td>
</tr>
</tbody>
</table>

Los entornos **Híbrido** y **On-Premise** pueden conectar a Campaign con los siguientes sistemas de bases de datos externos: Estos sistemas no **son compatibles** con los entornos (hospedados) de **Managed Services** de Campaign.

<table>
<tbody>
<td><strong>Sistema de bases de datos</strong></td>
<td><strong>Versión de la base de datos</strong></td>
<td><strong>Versión de la campaña</strong></td>
<tr>
<td>Microsoft Azure Synapse Analytics</td>
<td> </td>
<td>V7.0 19.1.4 mínimo</td>
</tr>
<tr><td>MySQL</td>
<td>
<p>8</p>
<p>5.7</p>
</td>
<td>
<p>Versión 7.3 como mínimo</p>
<p>V7.0 mínimo</p>
</td>
</tr>
<tr>
<td>Netezza</td>
<td>
<p>7,2</p>
</td>
<td>V7.0 mínimo</td>
</tr>
<tr>
<td>Oracle</td>
<td>
<p>19c</p>
<p>18c</p>
<p>12c</p>
<p>11g </p>
</td>
<td>
<p>V7.0 mínimo</p>
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
<td>V7.0 mínimo</td>
</tr>
<tr><td>SQL Server</td>
<td>
<p>2019</p>
<p>2017</p>
<p>2016</p>
<p>2014</p>
<p>2012 SP1 y SP2</p>
</td>
<td>V7.0 mínimo</td>
</tr>
<tr>
<td>Sybase</td>
<td>
<p>IQ 16</p>
<p>ASE 15.7</p>
</td>
<td>V7.0 mínimo</td>
</tr>
<tr>
<td>Teradata</td>
<td>
<p>17.x</p>
<p>16.x (última versión)</p>
</td>
<td>V7.0 mínimo</td>
</tr>
<tr><td>Hadoop a través de HiveSQL</td>
<td>
<p>HortonWorks HDP 2.4.X, 2.5.x, 2.6.x</p>
<p>HDInsight 3.4 (HDP 2.4), 3.5 (HDP 2.5), 3.6 (HDP 2.6)</p>
<p>Cloudera CDH6.x</p>
</td>
<td>V7.0 mínimo</td>
</tr>
</tbody>
</table>



## Consola del cliente {#ClientConsoleoperatingsystems}

Se **requieren** los siguientes sistemas operativos y exploradores para utilizar la [Consola del cliente de Campaign](../../installation/using/installing-the-client-console.md).

### Sistemas operativos

<table>
<tbody>
<td><strong>Sistema</strong></td>
<td><strong>Versión del SO</strong></td>
<td><strong>Versión de la campaña</strong></td>
<tr>
<td>Microsoft Windows</td>
<td>
<p>11</p>
<p>10</p>
</td>
<td>
<p>Versión 7.3 como mínimo</p>
<p></p>
<p></p>
</tr>
<tr>
<td>Microsoft Windows Server</td>
<td>
<p>2019</p>
<p>2016</p>
</td>
<td>
<p>V7.2.1 mínimo</p>
<p></p>
<p></p>
</tbody>
</table>

### Tiempo de ejecución de Microsoft WebView2

Tiempo de ejecución de Microsoft Edge WebView2 La última versión es obligatoria para la consola del cliente de Campaign.

Descargar Microsoft Edge WebView2 del [sitio de Microsoft Developer](http://www.adobe.com/go/acc-ms-webview2-runtime-download).


## SDK móvil{#MobileSDK}

Puede utilizar Campaign para [enviar notificaciones push](../../delivery/using/about-mobile-app-channel.md) en los sistemas operativos que se enumeran a continuación, utilizando el [SDK móvil](../../delivery/using/integrating-campaign-sdk-into-the-mobile-application.md) asociado.

También puede utilizar el SDK móvil de Adobe Experience Platform configurando la extensión de Adobe Campaign en la interfaz de usuario de recopilación de datos.

<table>
<tbody>
<tr>
<td>Google Android</td>
<td>
<p>12 (a partir de la versión 7.3 de Campaign), 9.0, 8.x, 7.x</p>
<p>con la versión 1.1.1 del SDK móvil</p>
</td>
</tr>
<tr>
<td>Apple iOS</td>
<td>
<p>iOS 9 - 15</p>
<p>con la versión 1.0.26 del SDK móvil, compatible con las versiones de 32 y 64 bits. iOS 15 es compatible a partir de la versión 7.3 de Campaign</p>
</td>
</tr>
</tbody>
</table>

## Exploradores{#Browsers}

Los siguientes exploradores, en su última versión, son compatibles con Campaign para [Acceso web](../../campaign/using/accessing-marketing-campaigns.md#using-the-web-interface-).

* Google Chrome
* Microsoft Edge
* Mozilla Firefox
* Safari



## Páginas similares{#Morelikethis}

* [Notas de la versión de Campaign Classic](../../rn/using/latest-release.md)
* [Arquitectura general de Campaign](../../installation/using/general-architecture.md)
* [Recomendaciones de tamaño de hardware](../../technotes/using/hardware-sizing.md)
* [Funcionalidades y sistemas obsoletos](../../rn/using/deprecated-features.md)
* [Procedimiento de actualización de la versión](../../production/using/build-upgrade.md)
