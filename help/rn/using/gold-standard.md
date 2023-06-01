---
product: campaign
title: “Versiones de [!DNL Gold Standard]”
description: Notas de la versión y matriz de compatibilidad para Campaign Classic [!DNL Gold Standard]
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
feature: Overview
role: User
level: Beginner
exl-id: 9e3a11b1-3070-4d90-91d5-7c559bdd500e
source-git-commit: 4661688a22bd1a82eaf9c72a739b5a5ecee168b1
workflow-type: ht
source-wordcount: '1670'
ht-degree: 100%

---

# Versiones de [!DNL Gold Standard]{#gold-standard}



Puede encontrar en esta página las notas de la versión y la matriz de compatibilidad para versiones de [!DNL Gold Standard].

## Notas de la versión de [!DNL Gold Standard]


### ![](assets/do-not-localize/limited_2.png) [!DNL Gold Standard] versión 12{#gs-12}

_7 de septiembre de 2021_

La compilación 9032@554dbcd incluye la siguiente corrección:

* Se ha corregido un problema que provocaba un error 500 al abrir el vínculo a una aplicación web en un envío de línea con seguimiento habilitado.

_27 de agosto de 2021_

La versión 9032@99a3894 incluye las siguientes correcciones:

* La función de firma de seguimiento se ha mejorado para evitar errores vinculados a la forma en que las herramientas de terceros (clientes de correo electrónico, navegadores de Internet, etc.) gestionan los caracteres especiales. Los parámetros de URL ahora están codificados.
* Se ha corregido un problema con los selectores de fechas que podría provocar que una consola muestre un mensaje de error de bloqueador. (NEO-36345)

### ![](assets/do-not-localize/limited_2.png) [!DNL Gold Standard] versión 11{#gs-11}

_14 de abril de 2021_

La compilación 9032@d030c36 incluye la siguiente corrección:

* Se ha corregido una regresión de la consola del cliente que provocaba mensajes de error persistentes en la pantalla de conexión IMS. (NEO-34821)
* Esta compilación de la consola es necesaria para mantener el [acceso IMS](../../technotes/using/ims-updates.md).

**Solo es obligatorio actualizar la consola. No se requiere ninguna actualización del servidor.**

>[!CAUTION]
>
> * Si se está conectando a Campaign con su Adobe ID, a través del servicio de Identity Management de Adobe (IMS), la actualización es obligatoria tanto para el servidor de Campaign como para la consola del cliente para poder conectarse a Campaign después del **30 de junio de 2021**. [Más información](../../technotes/using/ims-updates.md)
> * Esta versión incluye una [corrección de seguridad](https://helpx.adobe.com/es/security/products/campaign/apsb21-04.html): la actualización es obligatoria para reforzar la seguridad de su entorno.
> * Si está utilizando la integración de Experience Cloud Triggers mediante autenticación oAuth, debe ir a Adobe I/O como se detalla [en esta página](../../integrations/using/configuring-adobe-io.md). El modo de autenticación de oAuth heredado con Campaign [se ha eliminado](https://experienceleaguecommunities.adobe.com/t5/adobe-analytics-discussions/adobe-analytics-legacy-api-end-of-life-notice/td-p/385411?profile.language=es) en **septiembre de 2021**. Los entornos alojados se benefician de una extensión hasta el **23 de febrero de 2022**. Como cliente local o híbrido, póngase en contacto con el servicio de atención al cliente de Adobe para ampliar la asistencia hasta febrero de 2022. Debe proporcionar [el AppID de la aplicación OAuth](../../integrations/using/configuring-pipeline.md#step-optional) a Adobe.
>
>Obtenga más información en esta [[!DNL Gold Standard] sección](../../rn/using/gold-standard.md)

_2 de marzo de 2021_

La compilación 9032@10c2709 incluye la siguiente corrección:

* Se ha corregido una regresión que impedía el uso de algunos componentes de la consola, como el selector de fechas y la administración de imágenes en los envíos. (NEO-31453, NEO-31454)

**Solo es obligatorio actualizar la consola. No se requiere ninguna actualización del servidor.**

>[!NOTE]
>
> Conéctese a [Adobe Software Distribution](https://experience.adobe.com/#/downloads/content/software-distribution/es/campaign.html) para descargar la nueva versión. Aprenda a proponer la actualización de la consola a todos los usuarios finales [en esta página](../../installation/using/client-console-availability-for-windows.md).

_22 de diciembre de 2020_

La versión 9032@d3b452f incluye las siguientes mejoras y correcciones:

* El protocolo de conexión se ha actualizado para seguir el nuevo mecanismo de autenticación IMS.

* Activa la autenticación de integración, basada originalmente en la configuración de autenticación oAUTH, para acceder al canal que ahora se ha cambiado y se ha movido a Adobe I/O. [Más información](../../integrations/using/configuring-adobe-io.md)

* Después de finalizar [la compatibilidad con el protocolo binario heredado de APN de iOS](https://developer.apple.com/news/?id=c88acm2b), todas las instancias que utilizan este protocolo se actualizan al protocolo HTTP/2 durante la postactualización.

* Se ha corregido un problema de seguridad para reforzar la protección contra los problemas de falsificación de solicitudes del lado del servidor (SSRF). (NEO-27777)




* Se ha corregido un problema que podía provocar errores en los flujos de trabajo al ejecutar una actividad de **Enriquecimiento**. (NEO-17338)

### ![](assets/do-not-localize/red_2.png) [!DNL Gold Standard] Versión 10{#gs-10}

_7 de julio de 2020_

La compilación 9032@efd8a94 incluye la siguiente corrección:

Se ha corregido un problema que impedía que el seguimiento funcionara cuando la función de firma estaba deshabilitada. (NEO-26411)

>[!CAUTION]
>
>Le recomendamos que actualice la consola de cliente con la que está disponible en esta versión. Consulte [esta página](../../installation/using/installing-the-client-console.md)

### ![](assets/do-not-localize/red_2.png) [!DNL Gold Standard] Versión 9{#gs-9}

_22 de junio de 2020_

La versión 9032@800be2e incluye las siguientes correcciones:

* Se ha mejorado el conector HTTP2 de iOS (actualizaciones de terceros y administración de errores). (NEO-25904, NEO-25903, NEO-25799)

Las siguientes correcciones están relacionadas con el mecanismo de seguridad del vínculo de seguimiento (consulte la [lista de comprobación Seguridad y privacidad](https://helpx.adobe.com/es/campaign/kb/acc-security.html#signature-mechanism)):

* Se ha corregido un problema que impedía el funcionamiento del seguimiento de &quot;clics de notificación&quot; (notificaciones push de iOS y Android). (NEO-25965)
* Se ha corregido un problema que podía impedir que se abrieran las direcciones URL de seguimiento al usar ciertas versiones heredadas de Outlook o se hiciera clic en ellas.  (NEO-25688)
* Se ha corregido un problema que impedía que el funcionamiento del seguimiento de direcciones URL mediante fragmentos en parámetros de personalización (etiquetas de anclaje con signo de almohadilla). (NEO-25774)
* Se ha corregido un problema con el servicio de antiphishing. (NEO-25283)
* Se ha corregido un problema de seguimiento al usar fórmulas de seguimiento personalizadas específicas. (NEO-25277)





### ![](assets/do-not-localize/red_2.png) [!DNL Gold Standard] Versión 8{#gs-8}

_29 de abril de 2020_

La versión 9032@3a9dc9c incluye las siguientes correcciones:

* Se ha mejorado la seguridad en el seguimiento de enlaces en el correo electrónico. Esta opción está habilitada de forma predeterminada para todos los clientes. Hay disponible una función de seguridad adicional y mejorada que se puede habilitar si se pone en contacto con el Servicio de atención al cliente. Encuentre más detalles sobre la función y los pasos para que los clientes que no están alojados puedan habilitarla en la [Lista de comprobación de seguridad y privacidad](https://helpx.adobe.com/es/campaign/kb/acc-security.html#signature-mechanism).

>[!CAUTION]
>
>Si tiene problemas con las notificaciones push mediante vínculos de seguimiento o con envíos que utilizan etiquetas de anclaje, le recomendamos que desactive el nuevo mecanismo de firma para el seguimiento de vínculos. El procedimiento se detalla [en esta página](https://helpx.adobe.com/es/campaign/kb/acc-security.html#signature-mechanism).

* Se ha corregido un problema que podía impedir que las imágenes se mostraran en envíos de línea. (NEO-23207)
* Se ha corregido un problema con la actividad **File Transfer** que impedía que la autenticación basada en claves SFTP funcionara en Debian 9. (NEO-23183)
* Se ha corregido un problema que podía afectar a la notificación push cuando se enviaba con una frecuencia alta. (NEO-20516)
* Se ha corregido un problema en la administración de respuestas de oferta que podía provocar bloqueos en el servidor web. (NEO-19482)
* Se ha corregido un error en la administración de LibreOffice que impedía exportar informes. (NEO-20982)
* Se ha corregido un problema que provocaba un error al actualizar numerosos flujos de trabajo mediante una actividad de encuesta.
* Se mejoró la administración de LibreOffice para evitar fallos en la previsualización de correos electrónicos con archivos .odt.
* Se ha mejorado la administración de la conexión de Apache para evitar la latencia en el servicio web.
* Se ha mejorado la visualización de la etiqueta de versión (7 dígitos) en el menú **Acerca de**.
* Se ha corregido una regresión en la administración de listas que impedía que se publicaran ofertas.
* Se ha corregido una regresión que ocasionaba que el flujo de trabajo de limpieza se bloqueara.
* Se ha corregido una regresión menor en los registros del flujo de trabajo de limpieza.

### ![](assets/do-not-localize/red_2.png) [!DNL Gold Standard] Versión 6{#gs-6}

_9 de marzo de 2020_

La versión 9032@19f73c5 incluye la siguiente corrección:

* Se ha corregido un problema con cuentas externas que usaban FTP sobre SSL. (NEO-20498)

### ![](assets/do-not-localize/red_2.png) [!DNL Gold Standard] Versión 5{#gs-5}

_17 de diciembre de 2019_

La versión 9032@d6b8062 incluye la siguiente corrección:

* Se ha corregido un problema de seguimiento en los siguientes canales de comunicación: móvil (SMS, MMS), push (iOS, Android) y redes sociales (Facebook, Twitter). (NEO-19595)

### ![](assets/do-not-localize/red_2.png) [!DNL Gold Standard] Versión 4{#gs-4}

_11 de diciembre de 2019_

La versión 9032@bc4a935 incluye la siguiente corrección:

* Se ha corregido un problema de rendimiento al enviar mensajes con una base de datos MSSQL. (NEO-17558)

### ![](assets/do-not-localize/red_2.png) [!DNL Gold Standard] Versión 3{#gs-3}

_20 de noviembre de 2019_

La versión 9032@3468c7b incluye las siguientes correcciones:

* Se ha corregido un problema de inicio de sesión mediante la autenticación IMS. (NEO-17312)
* Se ha corregido un problema al mostrar informes acumulativos en varias entregas. (NEO-18165)
* Se ha corregido un problema que podía bloquear o colapsar el servidor web.

### ![](assets/do-not-localize/red_2.png) [!DNL Gold Standard] Versión 2{#gs-2}

_19 de septiembre de 2019_

La versión 9032@cee805c incluye las siguientes correcciones:

* Se ha corregido un problema al usar el conector CRM para Salesforce. (NEO-17712)
* Se ha corregido un problema de índice que podía provocar problemas de rendimiento al enviar mensajes transaccionales.

### ![](assets/do-not-localize/red_2.png) Versión 19.1.4, compilación 9032{#release-19-1-4-build-9032}

_13 de agosto de 2019_

La versión inicial 19.1.4 incluye las siguientes correcciones:

* Se ha corregido un problema con la actividad del programador que generaba mensajes de error no deseados durante la configuración del asistente. Revertir la actualización desde NEO-11662. (NEO-17097)
* Se ha corregido una regresión causada por el NEO-12727 que hacía que los flujos de trabajo se detuvieran cuando se realizaba una actividad de prueba dos veces. (NEO-16835)
* Se ha corregido un problema que provocaba la devolución de un código HTTP erróneo (HTTP 200 OK en lugar de HTTP 403 Prohibido) cuando se utilizaba un token de sesión no válido o caducado en las llamadas a la API. (NEO-16826)
* Se ha solucionado un problema con la clave DKIM que ya no se incrustaba en los mensajes de correo electrónico, lo que provocaba problemas a la hora de realizar entregas. (NEO-16804)
* Se han corregido varios problemas con la programación de los flujos de trabajo. Los flujos de trabajo se programaban para ejecutarse una vez al día sin tener en cuenta la configuración del programador. (NEO-16619, NEO-16426)


## Matriz de compatibilidad de [!DNL Gold Standard]{#compatibility-matrix-gs}

Este documento enumera todos los sistemas y componentes compatibles con las versiones 19.1 de **Adobe Campaign Classic[!DNL Gold Standard]**. Los productos y las versiones que no forman parte de esta lista no son compatibles con esta versión de Adobe Campaign.

>[!CAUTION]
>A menos que se indique lo contrario, se admiten todas las versiones secundarias.
>
>Adobe Campaign Classic es compatible con todos los sistemas y herramientas enumerados en esta página. Cuando las versiones específicas de estos sistemas y herramientas de terceros llegan al final de su vida útil (EOL) con sus respectivos creadores, Adobe Campaign ya no es compatible con ellas y se eliminan de nuestra matriz de compatibilidades en la versión posterior del producto. Para evitar problemas, compruebe que se encuentra en una versión compatible de cualquier sistema enumerado en la matriz de compatibilidad.

### Sistemas operativos{#OperatingSystems-gs}

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
<p>9 (64 bits)</p>
<p>8 (64 bits)</p>
</td>
</tr>
<tr>
<td>RHEL</td>
<td>
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

### Servidores web{#WebServers-gs}

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
<p>2.2 solo para RHEL6: CentOS 6 (64 bits)</p>
</td>
</tr>
</tbody>
</table>

### Herramientas{#Tools-gs}

<table>
<tbody>
<tr>
<td>Kit de desarrollo de Java (JDK)</td>
<td>
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

### Servidores RDBMS{#RDBMSservers-gs}

>[!NOTE]
>
>El controlador RDBMS debe coincidir con la versión del servidor RDBMS.

<table>
<tbody>
<tr>
<td>Oracle</td>
<td>
<p>18c</p>
<p>12c</p>
<p>11g  R2</p>
</td>
</tr>
<tr>
<td>PostgreSQL</td>
<td>
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
<p>Advertencia: Microsoft SQL Server no se admite como base de datos principal cuando el servidor de Campaign se está ejecutando en Linux.</p>
</td>
</tr>
<tr>
<td>DB2 UDB</td>
<td>
<p>9,7</p>
<p>Advertencia: No se permite DB2 UDB para nuevas instalaciones.</p>
</td>
</tr>
</tbody>
</table>

>[!NOTE]
>
>PostgreSQL es el servidor de bases de datos predeterminado para entornos hospedados.

### Conectores CRM{#CRMconnectors-gs}

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
<p>Versión de API 21</p>
<p>Versión de API 15</p>
</td>
</tr>
<tr>
<td>Microsoft Dynamics</td>
<td>
<p>API de Soap: On-Premise: 2007, 2015, 2016</p>
<p>API de Soap: En línea: 2015, 2016</p>
<p>API web: On-Premise y en línea: 365, 2016, 2016 Actualización 1</p>
</td>
</tr>
</tbody>
</table>

### Acceso de datos federado (FDA){#FederatedDataAccessFDA-gs}

<table>
<tbody>
<tr>
<td>Amazon Redshift</td>
<td><p> </p>
</td>
</tr>
<tr>
<td>Oracle</td>
<td>
<p>12c</p>
<p>11g</p>
</td>
</tr>
<tr>
<td>PostgreSQL</td>
<td>
<p>11.x</p>
<p>10.x</p>
<p>9.6.x</p>
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
<p>5.7</p>
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
</td>
</tr>
</tbody>
</table>

### Consola del cliente {#ClientConsoleoperatingsystems}

:warning: Se requieren los siguientes sistemas operativos y exploradores para utilizar la consola del cliente de Campaign.

#### Sistemas operativos

<table>
<tbody>
<tr>
<td>Microsoft Windows Server</td>
<td>
<p>2016</p>
<p>2012</p>
</td>
</tr>
<tr>
<td>Microsoft Windows</td>
<td>
<p>8</p>
<p>10 (recomendado para instancias en japonés)</p>
</td>
</tr>
</tbody>
</table>

#### Navegador

<table>
<tbody>
<tr>
<td>
<p>Microsoft Internet Explorer</p>
</td>
<td>
<p>11</p>
</td>
</tr>
</tbody>
</table>

### SDK móvil{#MobileSDK}

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

### Exploradores{#Browsers}

Los siguientes exploradores son compatibles con Campaign for Web Access.

<table>
<tbody>
<tr>
<td>
<p>Microsoft Edge</p>
</td>
<td>
<p>Última versión</p>
</td>
</tr>
<tr>
<td>
<p>Mozilla Firefox</p>
</td>
<td>
<p>Última versión</p>
</td>
</tr>
<tr>
<td>
<p>Google Chrome</p>
</td>
<td>
<p>Última versión</p>
</td>
</tr>
<tr>
<td>
<p>Safari</p>
</td>
<td>
<p>Última versión</p>
</td>
</tr>
<tr>
<td>
<p>Microsoft Internet Explorer</p>
</td>
<td>
<p>11</p>
</td>
</tr>
</tbody>
</table>
