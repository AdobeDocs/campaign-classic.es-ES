---
product: campaign
title: Versiones de Campaign Classic 2021
description: Más información sobre las actualizaciones de Campaign Classic 2021
feature: Release Notes
role: User
level: Beginner
hidefromtoc: true
exl-id: 0cd6bf20-da72-4cf0-9f5d-d4e8acdd324d
source-git-commit: a1dbef3e1feca1e3347de013db8bd7809d315016
workflow-type: tm+mt
source-wordcount: '2584'
ht-degree: 100%

---

# Versiones de 2021{#release-2021}

## Versión 7.1 (21.1)

>[!CAUTION]
>Utilice el menú **[!UICONTROL Help > About...]** para comprobar su versión de Adobe Campaign [ y número de compilación](../../platform/using/launching-adobe-campaign.md#getting-your-campaign-version). Sin embargo, tenga en cuenta que para todas las compilaciones entre 9277 y 9343 enumeradas en esta página, el número de versión muestra 7.0 en lugar de 7.1.
> 

### Versión 21.1.4, compilación 9343 {#release-21-1-4-build-9343}

[!BADGE Obsoleto]{type=negative url="https://experienceleague.adobe.com/docs/campaign-classic/using/release-notes/rn-overview.html?lang=es#rn-statuses" tooltip="Obsoleto"}

_8 de octubre de 2021_

**Parches**

* Se ha mejorado la corrección del flujo de trabajo de facturación disponible en la versión 9342, que requería un reinicio manual del flujo de trabajo para que se aplicara la corrección. Ahora la posactualización reinicia automáticamente el flujo de trabajo.

* Se ha corregido un problema que podía impedir el funcionamiento de la gestión de ofertas adecuado al usar el módulo **Interacción** con la opción [Power Booster](../../installation/using/power-booster-and-power-cluster.md). (NEO-39263)

* Se ha corregido un error “La ipaffinity xxx no se encuentra en el servidor mid xxx” que podría producirse al realizar envíos si se usaba más de una afinidad IP en una instancia de intermediario múltiple. (NEO-37514)

### Versión 21.1.4, compilación 9342 {#release-21-1-4-build-9342}

[!BADGE Obsoleto]{type=negative url="https://experienceleague.adobe.com/docs/campaign-classic/using/release-notes/rn-overview.html?lang=es#rn-statuses" tooltip="Obsoleto"}

_7 de septiembre de 2021_

**Mejora de la seguridad**

* Se ha corregido un problema de seguridad para reforzar la protección contra los ataques de recorrido de directorios. (NEO-28547)

**Mejoras**

* Tras finalizar su vida útil, se ha eliminado Flash de todas las funciones y componentes de Campaign relacionados y se ha sustituido por HTML5. Se ha eliminado el tipo de gráfico **Medición**. (NEO-30330) [Más información](../../reporting/using/creating-a-chart.md)
* Al instalar la consola del cliente en Windows, el instalador ahora comprueba si hay un nodo de registro principal y crea uno si falta. Esto evita posibles problemas al iniciar la consola. (NEO-34854)
* La función de firma de seguimiento se ha mejorado para evitar errores vinculados a la forma en que las herramientas de terceros (clientes de correo electrónico, navegadores de Internet, etc.) gestionan los caracteres especiales. Los parámetros de URL ahora están codificados.

**Otros cambios**

* Se ha corregido una regresión introducida en la versión 21.1.3 con el nuevo mecanismo de protección del flujo de trabajo de facturación. El flujo de trabajo de facturación se ejecutaba en instancias incorrectas y se bloqueaba al intentar enviar el informe de facturación, que no se generaba. Debe reiniciar manualmente el flujo de trabajo para que se aplique la corrección.
* Los conectores de Microsoft CRM anteriormente obsoletos (implementaciones Office 365 y On-premise) se han eliminado de la interfaz. [Más información](../../platform/using/crm-ms-dynamics.md#configure-acc-for-microsoft)
* Después de la migración a Tomcat 8, el script de configuración de IIS se ha actualizado para solucionar los problemas de integración de IIS. (NEO-31019)
* La identificación de la fuente de datos se ha mejorado en las pestañas de datos y esquema de la ventana **Ver población** de las transiciones de flujo de trabajo.
* Los índices de base de datos que faltaban se agregaron a los siguientes esquemas para evitar problemas de actualización de la base de datos: xtk:rights, nms:dlvExclusion, nms:seedMember, nms:trackingUrl

**Parches**

* Se ha corregido un problema que impedía que el informe de clics activos funcionara cuando las ofertas estaban vinculadas al envío. (NEO-26295)
* Se ha corregido un problema con la actividad **Flujo de trabajo secundario** cuando su ejecución no generaba una tabla de salida. (NEO-36242)
* Se han corregido varios problemas al exportar el informe **Análisis descriptivo** a PDF. (NEO-25847)
* Se ha corregido un problema que podría provocar errores en los envíos al utilizar un envío de correo externo. (NEO-37435)
* Se ha corregido un error al conectarse a Microsoft CRM mediante la API web. El mensaje de error se ha eliminado porque las funcionalidades no se vieron afectadas.
* Se ha corregido un problema de deduplicación del registro de seguimiento cuando el servidor mid se establecía como reenvío entre los servidores de seguimiento y marketing. (NEO-36285)
* Se ha corregido una regresión que impedía que Vault se usara como almacén de código específico.
* Se ha corregido un problema que impedía usar variables en una actividad de flujo de trabajo **Enriquecimiento** cuando la transición entrante era de una fuente de datos FDA.
* Se ha corregido un problema que podría provocar URL rotas en los mensajes de correo electrónico.

### Versión 21.1.3, compilación 9330 {#release-21-1-3-build-9330}

[!BADGE Obsoleto]{type=negative url="https://experienceleague.adobe.com/docs/campaign-classic/using/release-notes/rn-overview.html?lang=es#rn-statuses" tooltip="Obsoleto"}

_5 de junio de 2021_

**Novedades**


<table>
<thead>
<tr>
<th><strong>Nueva actividad de flujo de trabajo: Cambiar fuente de datos</strong><br/></th>
</tr>
</thead>
<tbody>
<tr>
<td>
<p>La nueva actividad de flujo de trabajo <b>Cambiar fuente de datos</b> permite cambiar la fuente de datos de la tabla de trabajo de un flujo de trabajo. Esto proporciona una mayor flexibilidad para administrar datos en diferentes fuentes de datos (FDA y base de datos local).</p>
<p>En los flujos de trabajo de Adobe Campaign, los datos se administran mediante tablas de trabajo (o temporales). A medida que se ejecuta el flujo de trabajo, las tablas de trabajo comparten datos entre las actividades de flujo de trabajo. De forma predeterminada, las tablas de trabajo se crean en la misma base de datos que el origen de los datos que consultamos.</p>
<p>Para obtener más información, consulte la <a href="../../workflow/using/change-data-source.md">documentación detallada</a>.</p>
</td>
</tr>
</tbody>
</table>

<table>
<thead>
<tr>
<th><strong>Integración con Journey Orchestration de Adobe</strong><br/></th>
</tr>
</thead>
<tbody>
<tr>
<td>
<p>La integración entre Journey Orchestration y Adobe Campaign Classic es ahora GA. Permite a Journey Orchestration enviar correos electrónicos, notificaciones push y SMS mediante las funciones de mensajería transaccional de Adobe Campaign Classic.</p>
<p>La conexión entre las instancias de Journey Orchestration y Campaign Classic se configura por Adobe en el momento del aprovisionamiento.</p>
<p>Para obtener más información, consulte la <a href="https://experienceleague.adobe.com/docs/journeys/using/action-journeys/acc-action.html?lang=es">Documentación de Journey Orchestration</a>. En esta <a href="https://experienceleague.adobe.com/docs/journeys/using/use-cases-journeys/campaign-classic-use-case.html?lang=es">sección</a> se muestra un caso de uso paso a paso.</p>
</td>
</tr>
</tbody>
</table>

<table> 
<thead>
<tr> 
<th> <strong>Mejoras en el canal de LINE</strong><br /> </th> 
</tr> 
</thead> 
<tbody> 
<tr> 
<td> <p>Se han añadido las siguientes mejoras al canal de LINE:
</p>
<ul> 
<li><p>Compatibilidad con el tipo de mensaje de vídeo de LINE</p></li>
<li><p>Compatibilidad con la API de registro de socio de LINE</p></li>
<li><p>Soporte para reintentar el envío de mensajes en caso de error de LINE del lado del servidor o tiempo de espera de red</p></li>
</ul>
<p>Para obtener más información, consulte la <a href="../../delivery/using/line-channel.md">documentación detallada</a>.</p>
</td> 
</tr> 
</tbody> 
</table>

<table> 
<thead>
<tr> 
<th> <strong>Conector FDA de Vertica Analytics</strong><br/> </th> 
</tr> 
</thead> 
<tbody> 
<tr> 
<td> <p>Ahora puede conectar la instancia de Adobe Campaign Classic a la base de datos externa de Vertica. Esta conexión se administra mediante una nueva cuenta externa.</p>
<p>Para obtener más información, consulte la <a href="../../installation/using/configure-fda-vertica.md">documentación detallada</a>.</p>
</td> 
</tr> 
</tbody> 
</table>

<table> 
<thead>
<tr> 
<th> <strong>Conector de FDA de Google, BigQuery</strong><br /> </th> 
</tr> 
</thead> 
<tbody> 
<tr> 
<td> <p>Ahora puede conectar la instancia de Adobe Campaign Classic a la base de datos externa Google Big Query. Esta conexión se administra mediante una nueva cuenta externa.
</p>
<p>Para obtener más información, consulte la <a href="../../installation/using/configure-fda-google-big-query.md">documentación detallada</a>.</p>
</td> 
</tr> 
</tbody> 
</table>

**Mejoras de seguridad**

* El acceso al método de API **xtk:session#GetCnxInfo** que devuelve todos los detalles de conexión a la base de datos ahora está restringido únicamente a los usuarios administradores. (NEO-27779)
* La función obsoleta decryptString se ha sustituido por decryptPassword en archivos JavaScript relacionados con CRM.
* La funcionalidad de firma de seguimiento se ha mejorado para reducir el riesgo de seguimiento de errores de redirección cuando las herramientas de terceros (clientes de correo electrónico, navegadores de Internet, herramientas de seguridad de vínculos seguros) modifican el vínculo rastreado.
* Se ha corregido un problema que podía impedir que las direcciones URL rastreadas funcionaran cuando contenían caracteres en mayúsculas. El mecanismo de firma de direcciones URL rastreadas ahora distingue entre mayúsculas y minúsculas. (NEO-28414)

**Actualizaciones de compatibilidad**

Ahora se admiten los siguientes sistemas con Campaign:
* Conector de FDA de Google BigQuery
* Conector FDA de Vertica Analytics
* PostgreSQL 13

Obtenga más información en la [Matriz de compatibilidad de Campaign](../../rn/using/compatibility-matrix.md).

**Funciones obsoletas**

* A partir de la versión 21.1 de Campaign, el Conector de datos de Adobe Analytics queda obsoleto. Si utiliza este conector, debe adaptar la implementación en consecuencia con el nuevo conector de Adobe Analytics.
* La compatibilidad con Debian 8 ya está obsoleta.
* Después de la desaprobación de Oracle CRM en 20.3, la cuenta externa relacionada se ha eliminado de la interfaz.

Obtenga más información en la página [Funciones obsoletas y eliminadas](../../rn/using/deprecated-features.md).

**Mejoras**

* Se han añadido comprobaciones adicionales al guardar un flujo de trabajo para asegurarse de que los nombres de las actividades sean únicos y de que las transiciones siempre irán seguidas de una actividad.
* El flujo de trabajo técnico **Facturación (billing)** incluye ahora las tareas realizadas originalmente por el flujo de trabajo **Número de perfiles de facturación activos** (billingActiveContactCount), que se ha eliminado. El informe de correo electrónico que envía cada mes el flujo de trabajo ahora proporciona información sobre la cantidad de perfiles activos en la instancia. [Más información](../../workflow/using/about-technical-workflows.md).
* Se ha añadido un nuevo atributo **_keyOnMData** para poder utilizar una clave para operaciones en datos de memo.

**Otros cambios**

* Se ha añadido un mecanismo de protección para permitir que el [flujo de trabajo técnico de facturación](../../production/using/monitoring-processes.md#billing-report) se ejecute en la instancia de marketing.
* El tercero de openssl para Windows se ha actualizado a la versión 1.1.1h.
* En la descripción del paquete Debian, nlserver se ha cambiado a servidor de Adobe Campaign Classic.

**Parches**

* Se ha corregido un problema que se producía al editar el tiempo de espera para cerrar la sesión de los usuarios después de una cantidad específica de tiempo en el que estos permanecían conectados incluso después de la hora establecida.
* Se ha corregido un problema por el cual los envíos se mostraban como de solo lectura, pero se podían editar en las propiedades de los envíos.
* Se ha corregido un error que provocaba que la barra de herramientas de edición desapareciera al diseñar una aplicación web.
* Se ha corregido un error que mostraba la versión de texto de un correo electrónico con encabezados de Adobe Campaign Classic al añadir un vínculo a un correo electrónico. (NEO-29211
* Al utilizar FDA con conexión HTTP, el flujo de trabajo **Intermediario (logs de entrega)** (defaultMidSourcingLog) se quedaba en el periodo de tiempo establecido por la opción **NmsMidSourcing_LogsPeriodHour**. Esto evitaría que los registros se actualizaran con los datos que se produjeron después de este periodo de tiempo establecido. (NEO-30833)
* Se ha corregido un problema que se producía después de ejecutar el flujo de trabajo de sincronización del centro de mensajes. Cada vez que una carpeta de objetos de envío se movía a una carpeta personalizada el flujo de trabajo devolvía los envíos a la carpeta genérica **Historial de mensajes transaccionales**. (NEO-27445)
* Se ha corregido un problema que mostraba un mensaje de error al intentar mostrar los informes **Estadísticas de difusión**, **Indicadores de seguimiento** y **Estadísticas de las actividades de compartición**.
* La actividad del flujo de trabajo **Oracle bajo demanda** se ha eliminado de la interfaz después de que el conector CRM de Oracle quedase obsoleto.
* Se ha corregido un problema que detenía la ejecución de flujos de trabajo de procesamiento después del reinicio diario del módulo del servidor de flujo de trabajo (wfserver). (NEO-30047)
* Se ha corregido un problema que impedía actualizar el documento de administración de MX, lo que podría afectar negativamente a la reputación de la IP. (NEO-29897)
* Se han corregido problemas que ocasionaban bloqueos de procesos web al recibir una llamada SOAP. (NEO-28796) (NEO-29600)
* Se ha corregido un problema que provocaba que fallara la creación del índice FDA del SAP HANA. (NEO-29664)
* Se ha corregido un problema que podía mantener los mensajes transaccionales en el estado **Esperando** al realizar llamadas SOAP con encabezado. (NEO-28737)
* Se ha corregido un problema que se producía al utilizar el conector FDA de Teradata: todas las tablas temporales se creaban en un solo nodo del clúster, lo que podría terminar consumiendo todo el espacio de la cola y hacer que Teradata se bloqueara. Las tablas temporales ahora se generan en muchos nodos. (NEO-28230)
* Se ha corregido un problema que se producía al usar aplicaciones web, que provocaba que las etiquetas de seguimiento generaran claves principales incorrectas en el esquema **nms:trackingURL**. (NEO-27931)
* La compatibilidad con ODBC 3.x se ha mejorado para garantizar la precisión de los mensajes de error.
* Se ha corregido un problema que podía provocar bloqueos de la consola cuando se utilizaban plantillas de contenido personalizadas en los envíos de correo electrónico. (NEO-31547)
* Se ha corregido un problema que impedía que Tomcat enviara respuestas válidas debido a una conexión lenta o a un tamaño de respuesta grande. (NEO-30858)
* Se ha corregido un problema que se podía producir al leer un UUID desde una base de datos PostgreSQL.
* Se ha corregido un problema que podía provocar problemas de rendimiento al buscar datos de propuestas vinculados a ofertas. (NEO-27554)
* Se ha corregido un problema que provocaba que el proceso web no respondiera cuando el servicio IMS se activaba, pero no respondía.
* Se ha corregido un problema que impedía realizar un envío con un grupo de pruebas debido a un mecanismo de unión específico que no permitía la personalización de los envíos. (NEO-14391)
* Se ha corregido un problema que hacía que no se enviara una alerta con la actividad de alerta si una consulta y una actividad de enriquecimiento se dirigían a la tabla de entrega. (NEO-25157)

### Versión 21.1.2, compilación 9282 {#release-21-1-2-build-9282}

[!BADGE Obsoleto]{type=negative url="https://experienceleague.adobe.com/docs/campaign-classic/using/release-notes/rn-overview.html?lang=es#rn-statuses" tooltip="Obsoleto"}

_15 de abril de 2021_

* Se ha mejorado la administración de contraseñas para optimizar la seguridad.
* Se ha corregido un problema que podría provocar bloqueos de MTA.

### Versión 21.1.1, compilación 9277 {#release-21-1-1-build-9277}

[!BADGE Obsoleto]{type=negative url="https://experienceleague.adobe.com/docs/campaign-classic/using/release-notes/rn-overview.html?lang=es#rn-statuses" tooltip="Obsoleto"}

_22 de febrero de 2021_

**Mejoras de seguridad**

* Se ha mejorado el mecanismo de autenticación de la consola para optimizar la seguridad. (NEO-26944)
* Se ha corregido un problema de seguridad para reforzar la protección contra los problemas de falsificación de solicitudes del lado del servidor (SSRF). (NEO-28532)

**Actualizaciones de compatibilidad**

Ahora se admiten los siguientes sistemas con Campaign:

* La versión 49 de la API de Salesforce ahora se admite al usar la cuenta externa de CRM de Salesforce.

**Funciones obsoletas**

El informe de **monitorización de la capacidad de envío técnico** está obsoleto.

Obtenga más información en la página [Funciones obsoletas y eliminadas](../../rn/using/deprecated-features.md).

**Mejoras**

**El servicio de comentarios de correo electrónico (EFS)** es un servicio escalable que captura los comentarios del servidor de correo mejorado directamente, lo que mejora la precisión de la creación de informes. Esta capacidad se presenta como una versión beta privada y estará disponible de forma progresiva para todos los clientes en futuras versiones.

* Ahora se capturan todas las categorías de comentarios para obtener una creación de informes completa y precisa.
* El cálculo del indicador Entregado ahora se basa en los comentarios en tiempo real del servidor de correo mejorado para mejorar la precisión y la reactividad.
* EFS soluciona el problema de los retrasos con la creación de informes de devoluciones síncronas suaves.

**Otros cambios**

* La velocidad de transferencia se ha mejorado para registros de seguimiento grandes mediante compresión.
* El mapa de calor del flujo de trabajo se ha mejorado para evitar tiempos de espera al ejecutar flujos de trabajo con varias actividades. (NEO-27423).
* Se ha corregido un problema que podía permitir que se presentara una oferta aunque se pasara la fecha de finalización. Ahora, Campaign Classic tiene en cuenta la marca de tiempo completa de la fecha de finalización en lugar de solo la fecha. (NEO-27590)
* El vínculo de Google+ se ha eliminado del bloque de personalización **Vínculos compartidos de redes sociales**.
* Se ha corregido un problema tras la implementación de una corrección de errores en la última versión. Se ha añadido una comprobación en el nombre del host al conectarse mediante SSL/TLS, lo que provocó que los envíos SMS dieran error. La verificación del nombre de host se ha desactivado para la mayoría de los protocolos, como POP3, SMS y HTTP con proxy, y la comprobación del certificado de la cuenta externa SMS se ha mejorado con tres valores (NEO-29581). [Obtenga más información](../../delivery/using/sms-protocol.md#skip-tls)

**Parches**

* Se ha corregido un problema que impedía que las combinaciones de teclas Tab, Enter y Escape funcionaran en la nueva pantalla de inicio de sesión.
* Se ha corregido un problema de actualización que provocaba que el nombre de un flujo de trabajo recién creado se reemplazara por el valor predeterminado después de guardar (NEO-26106).
* Se ha corregido un problema que se producía al ejecutar flujos de trabajo en el que se agregaba un nuevo campo como parte de una actividad de **Enriquecimiento** anterior a una actividad de **Envío** mediante una asignación de destino de **archivo externo**: se han agregado campos no deseados a la asignación de destino de **archivo externo**. (NEO-27687)
* Se ha corregido un problema que provocaba que algunos caracteres del código fuente se alteraran al volver a abrir una aplicación web previamente creada y guardada. (NEO-27597)
* Se ha corregido un problema que se podía producir al actualizar a una compilación, incluido el nuevo mecanismo de firma para el seguimiento de vínculos (desde la compilación 19.1.4 y la Campaign 20.2): cuando se asocian varias plantillas a un evento, la actualización puede hacer que se seleccione una plantilla incorrecta al enviar el mensaje transaccional. (NEO-28326)
* Se ha corregido un problema que provocaba que el servidor de correo dejara de responder y no pudiera procesar envíos a menos que se reiniciara. (NEO-27455)
* Se ha corregido un problema en la base de datos MSSQL relacionado con la administración de zonas horarias durante las operaciones de carga por lotes de una columna de tipo datetime. (NEO-27375)
* Se ha corregido un problema de consulta del flujo de trabajo al usar las funciones xtk de Redshift. Los SubDays, SubSeconds, SubMinutes y SubHours ahora aceptan ambos tipos de marcas de tiempo de Redshift (NEO-24962).
* Se ha corregido un problema que mostraba un mensaje de error de secuencia de comandos al intentar la previsualización de un informe con acceso anónimo. (NEO-27081)
* Se ha corregido un problema que podía reducir el uso de memoria en el servidor al realizar el análisis del envío.
* Se ha corregido un problema que podía impedir que la instancia funcionara al intentar ejecutar consultas complejas específicas.
* Se ha corregido un problema que podía impedir que se ejecutara el flujo de trabajo técnico **Sincronización de páginas de Twitter**. (NEO-28634)
* Se ha corregido un problema por el que se podía mostrar un mensaje de error relacionado con la función decryptPassword al intentar publicar en X (anteriormente conocido como Twitter) mediante la plantilla de envíos de **tuits (Twitter)**. (NEO-28216)
* Se ha corregido un problema que se producía al utilizar una actividad **JavaScript** para realizar una solicitud HTTP en un flujo de trabajo. Después de definir el número de puerto en el nombre del host, la llamada generaría el siguiente error (NEO-29146):

```
IOB-090020 Error in SSL library: 'IOB-090013 error:14090086:SSL routines:ssl3_get_server_certificate:certificate verify failed (code 336134278)'
```

* Se ha corregido un problema que impedía que se enviaran nuevos envíos con personalización de datos de destinatario (NEO-30323).
* Se ha corregido un problema en el cual se producían varios bloqueos en la instancia de marketing que causaban archivos principales.
* Se ha corregido un problema que ocasionaba que el flujo de trabajo de **Seguimiento** diera el siguiente error (NEO-25206):

```
There is no index on the sourceId field of the 'NmsTrackingLogRcp' table required for the current Web tracking mode. Please add this index.
```

* Se ha corregido un problema que se producía al crear y guardar un envío en la pestaña **Segmentación y flujo de trabajo** de una campaña: la previsualización daría el siguiente error (NEO-29440):

```
XTK-170024 The temporary 'temp:deliveryEmail-all' schema is not defined in the current context
```

* Se ha corregido un error que se producía al configurar una cuenta externa entre una instancia de marketing y una instancia de Adobe Campaign Standard o una instancia intermediaria de Campaign Classic y al utilizar la opción &quot;DisableFOH2=1&quot;. Cuando se utilizaba la opción &quot;DisableFOH2=1&quot; en la cuenta externa, las conexiones no se cerraban correctamente y se acumulaban, lo que daba como resultado el siguiente error (NEO-26258):

```
The maximum number of connections has been reached (50) by connections pool 'nms:extAccount:acsDefaultRelayAccount XXX'. The server is overloaded. Please try again later.
```

* Se ha corregido un error con SMS cuando se producían problemas de conexión entre el servidor y el proveedor. El elemento secundario del servidor de correo desactivaría automáticamente la conexión. Adobe Campaign Classic no intentaría conectarse a esta conexión con error mientras no se hubiera iniciado un nuevo elemento secundario.
