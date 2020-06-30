---
title: Última versión
description: Última versión
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
source-git-commit: b2cc71f8f9b7df80b1601a9fa55bfd77f9a82433
workflow-type: tm+mt
source-wordcount: '1765'
ht-degree: 99%

---


# Última versión{#latest-release}

[Build upgrade](https://helpx.adobe.com/es/campaign/kb/acc-build-upgrade.html) | [Control Panel releases](https://docs.adobe.com/content/help/es-ES/control-panel/using/release-notes.html) | [Documentation updates](../../rn/using/documentation-updates.md) | [Previous releases](../../rn/using/release--20-1.md) | [Deprecated features](../../rn/using/deprecated-features.md)

<table> 
 <tbody> 
  <tr> 
   <td><img src="assets/do-not-localize/green3.png"/><strong>Disponibilidad general</strong></td>
   <td><img src="assets/do-not-localize/blue3.png"/><strong>Liberar candidato</strong></td> 
   <td><img src="assets/do-not-localize/orange3.png"/><strong>Ya no está disponible</strong></td> 
   <td><img src="assets/do-not-localize/red3.png"/><strong>Obsoleto</strong></td> 
  </tr> 
   <tr> 
   <td>Última compilación estable disponible. Compilación validada en producción.<br></td>
   <td>Compilación validada por Adobe. Esperando pruebas de producción.<br> </td>
   <td>Nueva compilación disponible con correcciones de errores. Se requiere la actualización.<br></td>
   <td>Contiene regresiones conocidas. La actualización es obligatoria.<br></td>
  </tr> 
 </tbody> 
</table>

La **última compilación estable** es 9032 (3a9dc9c). Haga clic [aquí](../../rn/using/release--19-1.md#release-19-1-4-build-9032)

![](assets/do-not-localize/cp-icon.png) **Nueva versión** de junio del Panel de control con supervisión de perfiles activos, auditoría de entregas de subdominios y administración de claves GPG. [Más información](https://docs.adobe.com/content/help/es-ES/control-panel/using/release-notes.html).

## ![](assets/do-not-localize/blue_2.png) Versión 20.2.1: compilación 9178 {#release-20-2-1-build-9178}

_lunes, 8 de junio de 2020_

**Novedades**

<table> 
 <thead> 
  <tr> 
   <th> <strong>Compatibilidad de emoticonos</strong><br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> <p>Ahora, al diseñar un mensaje en Campaign, puede insertar fácilmente emoticonos en el cuerpo del mensaje con un botón específico. También se pueden añadir en la línea de asunto del correo electrónico. Puede personalizar la lista de los emoticonos disponibles en la interfaz.</p>
    <p>Para obtener más información sobre cómo añadir emoticonos, consulte la <a href="../../delivery/using/defining-the-email-content.md#inserting-emoticons">documentación detallada</a>. Entérese de cómo personalizar la lista de emoticonos <a href="../../delivery/using/customizing-emoticon-list.md">en esta sección</a>.</p>
   </td> 
  </tr> 
 </tbody> 
</table>

<table> 
 <thead> 
  <tr> 
   <th> <strong>Conector de FDA de Azure Synapse</strong><br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> <p>Ahora puede conectar la instancia de Campaign a la base de datos externa de Azure Synapse. Esta conexión se administra mediante una nueva cuenta externa.</p>
    <p>Azure Synapse solo está disponible para entornos híbridos y locales. Para obtener más información, consulte la <a href="../../platform/using/specific-configuration-database.md#configure-access-to-azure-synapse">documentación detallada</a>.</p>
   </td> 
  </tr> 
 </tbody> 
</table>

<table> 
 <thead> 
  <tr> 
   <th> <strong>Leyes de privacidad de Tailandia y Brasil</strong><br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> <p>La Ley de Protección de Datos Personales de Tailandia (PDPA, por sus siglas en inglés) es la nueva ley de privacidad que armoniza y moderniza los requerimientos de protección de datos para Tailandia. </p>
   <p>La Lei Geral de Proteção de Dados (LGPD) de Brasil va a entrar en vigencia a partir del 16 de agosto para todas las compañías que recopilen o procesen datos personales en Brasil.</p>
   <p>Estos reglamentos se aplican a los clientes de Adobe Campaign que albergan datos de sujetos de datos que residan en estos países. Además de las funcionalidades de privacidad disponibles en Campaign (incluida la administración de consentimientos, configuración de retención de datos y funciones de usuario), estamos tomando esta oportunidad para incluir funcionalidades adicionales, para ayudar a facilitar su preparación para la PDPA y la LGPD.</p>
   <ul> 
     <li><p>Derecho de acceso y derecho de eliminación: estamos aprovechando las capacidades añadidas para el RGPD y la CCPA. <a href="https://helpx.adobe.com/es/campaign/kb/acc-privacy.html">Más información</a></p></li> 
     <li> <p>Al crear una solicitud de privacidad mediante la interfaz de Campaign o API, ahora puede seleccionar el tipo de <strong>reglamento</strong>: PDPA, LGPD, RGPD, CCPA. <a href="https://helpx.adobe.com/es/campaign/kb/acc-privacy.html#ManagingPrivacyRequests">Más información</a>.</p></li>
    </ul>
   </td> 
  </tr> 
 </tbody> 
</table>

**Mejoras de seguridad**

* La seguridad mejorada en el seguimiento de enlaces en el correo electrónico está habilitada de forma predeterminada para todos los clientes. Hay disponible una función de seguridad adicional y mejorada que se puede habilitar si se pone en contacto con el Servicio de atención al cliente. Encuentre más detalles sobre la función y los pasos para que los clientes que no están alojados puedan habilitarla en la [Lista de comprobación de seguridad y privacidad](https://helpx.adobe.com/es/campaign/kb/acc-security.html). (NEO-24232)

* Para optimizar la seguridad, el algoritmo hash MD5 utilizado para generar nombres de archivo se ha reforzado con sha256 para la carga pública de archivos. (NEO-17044)

* Para reforzar la seguridad contra los ataques XSS, los scripts del lado del cliente se desactivan al ejecutar una página espejo. (NEO-17987)

* Se ha corregido un problema que impedía que el flujo de trabajo técnico de **Limpieza de solicitudes de privacidad** eliminara datos de reconciliación. (NEO-25168, NEO-21004)

* Se ha corregido un problema con la actividad **File Transfer** que impedía que la autenticación basada en claves SFTP funcionara en Debian 9. (NEO-23183)

**Mejoras de compatibilidad**

Ahora se admiten los siguientes sistemas con Campaign:
* Sistema operativo: Debian 10.
* RDBMS: Oracle 18c y Oracle 19c
* FDA: Azure Synapse Analytics

Obtenga más información en la [Matriz de compatibilidad de Campaign](https://helpx.adobe.com/es/campaign/kb/compatibility-matrix.html).

**Mejoras**

* La mensajería transaccional se ha mejorado para mejorar la experiencia del usuario. Ahora puede cancelar la publicación de una plantilla de mensaje transaccional, que la elimina de las instancias de ejecución. [Más información](../../message-center/using/template-unpublication.md).

* Hay nuevas opciones disponibles para establecer limitaciones al enviar correos electrónicos que incluyen imágenes o archivos adjuntos. Estas protecciones pueden evitar problemas de rendimiento, lo que resulta especialmente útil con la mensajería transaccional. [Más información](../../installation/using/configuring-campaign-options.md#delivery)

* La nueva opción **Preparar las piezas de envío en la base de datos** permite realizar la preparación de envíos directamente en la base de datos, lo que puede acelerar el análisis en gran medida. Esta opción solo está disponible para configuraciones específicas. [Más información](../../delivery/using/steps-validating-the-delivery.md#improving-delivery-analysis). (NEO-23886)

* Se ha mejorado el rendimiento de la [actividad del conector CRM](../../workflow/using/crm-connector.md) para Microsoft Dynamics. (NEO-13303, NEO-12710)

* Se ha aumentado la versión de memoria compartida.

   >[!WARNING]
   >
   >Esta mejora requiere un paso adicional después de realizar la actualización. Consulte la sección de **Evoluciones técnicas** que aparece a continuación.

* Se ha mejorado el flujo de trabajo de limpieza. Las tablas de trabajo huérfanas de todos los flujos de trabajo eliminados ahora también se eliminan automáticamente mediante el flujo de trabajo de limpieza. [Más información](../../production/using/database-cleanup-workflow.md#cleanup-of-workflow-instances).

* Los certificados para aplicaciones móviles iOS con el conector HTTP2 de iOS ahora se validan antes de enviar las notificaciones push, lo que evita que los envíos produzcan errores debido a certificados caducados.

* Se ha mejorado la administración de las conexiones proxy HTTP. [Más información](../../installation/using/configuring-campaign-server.md#proxy-connection-configuration).

**Otros cambios**

* Los conectores SMS heredados quedan obsoletos. Consulte la [Página de funciones obsoletas](../../rn/using/deprecated-features.md).

* Ya no puede utilizar su propia cuenta de Litmus para aprovisionar y utilizar la renderización de la Bandeja de entrada en Adobe Campaign. [Más información](../../delivery/using/inbox-rendering.md).

* Para distinguir mejor las vistas de las carpetas, se ha cambiado el color de los nombres de vistas de azul oscuro a cian oscuro. [Más información](../../platform/using/access-management.md#about-views)

* Ahora, Campaign Classic puede conectarse a cuentas de Microsoft Dynamics CRM alojadas en las regiones de Reino Unido, India y Canadá. Esto se aplica a los tipos de implementación de Office 365 y Locales (Dynamics 2015).

* Campaign ahora realiza una verificación TLS para comprobar que el nombre de host del servidor coincide con el nombre de host del certificado proporcionado.

* La tabla de estadísticas de envío y seguimiento ahora muestra una entrada por envío para el canal SMS, en lugar de una entrada por destinatario de envío.

* Se añadió un mensaje de error en el archivo de registro para advertir a los usuarios cuando el archivo descargado es mayor que el espacio en disco.

* Ahora están disponibles las siguientes funciones para el conector Snowflake: Meses anteriores, Días anteriores, Hasta la fecha, Hora, Años anteriores.

**Evoluciones técnicas**

Esta nueva compilación actualiza la memoria compartida y requiere pasos adicionales para realizar la actualización. Como administrador de Campaign, debe eliminar los segmentos de memoria. Estos pasos son obligatorios, ya que los segmentos antiguos evitan que nlserver/nlsrvmod se inicie.

En Windows, es necesario reiniciar el sistema.

En Debian/CentOs, es necesario eliminar la memoria compartida. Estos son los pasos:

Antes de la actualización, debe seguir estos pasos:

1. Detenga el servicio apache2 (http2 en CentOS) si se está ejecutando.
1. Detenga el servicio nlserver (nlserver6 para compilaciones anteriores) si se está ejecutando.

Después de la actualización:

1. Elimine la memoria compartida mediante el comando **ipcrm** , si la versión es anterior a la versión actual.
1. Inicio el servicio nlserver si se estaba ejecutando.
1. Inicie el servicio apache2 si se estaba ejecutando.

Estas son las líneas de comandos para Debian:

```
/etc/init.d/nlserver* stop
/etc/init.d/apache2 stop

for i in `ipcs -s | awk '/www-data/
{print $2}'`; do (ipcrm -s $i); done

for i in `ipcs -m | awk '/www-data/ {print $2}
'`; do (ipcrm shm $i); done

for i in `ipcs -m | awk '/neolane/
{print $2}'`; do (ipcrm shm $i); done

for i in `ipcs -s | awk '/neolane/ {print $2}
'`; do (ipcrm -s $i); done

/etc/init.d/apache2 restart
/etc/init.d/nlserver* start
```

Hay un ejemplo para Linux disponible en esta [página](../../configuration/using/additional-parameters.md#redirection-server-configuration).

**Parches**

* Se corrigió una regresión menor en los registros del flujo de trabajo de limpieza.
* Se ha corregido un problema en la actividad **Carga (SOAP)** de flujo de trabajo al analizar archivos WSDL.
* Se ha corregido un problema que provocaba un error al actualizar varios flujos de trabajo mediante una actividad de **Encuesta** para procesar de forma eficaz un número elevado de flujos de trabajo.
* Se ha corregido un problema de conectividad intermitente durante el procesamiento de mensajes inMail desde el MTA mejorado. (NEO-20380)
* Se ha corregido un problema que impedía que los porcentajes de clics interactivos se mostraran correctamente cuando las imágenes se mostraban con una anchura del 100 % en el HTML. (NEO-23203)
* Se ha corregido un problema que impedía que el contenido condicional del envío se mostrara completamente en el informe de clics activos. (NEO-18729)
* Se ha corregido un problema que omitía el paso de aprobación de destinatario al reanudar un flujo de trabajo para realizar un envío recurrente. (NEO-18166)
* Se ha corregido un problema que impedía que el botón **Reiniciar preparación de mensajes** reanudara el envío después de corregir un error en el flujo de trabajo. (NEO-13488)
* Se ha corregido un problema que podía hacer que los envíos fallaran en el modo de intermediario durante la fase de ampliación, en la que el objetivo incluía destinatarios con formatos de correo electrónico en japonés. (NEO-23846)
* Se ha corregido un problema de conversión de huso horario con el conector de Snowflake (NEO-20105).
* Se ha corregido un problema con cuentas externas que usaban FTP sobre SSL. (NEO-20498)
* Se ha corregido un problema que podía impedir que las imágenes se mostraran en envíos de línea. (NEO-23207)
* Se ha corregido un problema que provocaba un error al publicar una oferta. (NEO-23312)
* Se ha corregido un problema con las notificaciones push que permitía que las conexiones de prueba funcionaran en aplicaciones móviles, incluso cuando el certificado había caducado. (NEO-22991)
* Se ha corregido un problema que podía afectar a la notificación push cuando se enviaba con una frecuencia alta. (NEO-20516)
* Se corrigió un problema que ocasionaba que los datos de seguimiento incluyeran duplicados aunque los registros de seguimiento no lo hicieran. (NEO-20040)
* Se ha corregido un problema que hacía que se enviaran correos electrónicos transaccionales en duplicado después de que se corrigiera un error de comunicación del servidor de seguimiento. (NEO-23640)
* Se ha corregido un problema que eliminaba el valor del parámetro de codificación al redirigir desde una URL de seguimiento. (NEO-25637)
* Se ha corregido un problema que podía impedir que una consulta funcionara al comparar números flotantes. (NEO-23243)
* Se ha corregido un problema que podía impedir que se mostrara el contenido de la columna **Modificado por** después de reiniciar un flujo de trabajo. (NEO-23035)
* Se corrigió un problema que ocasionaba que fallara el flujo de trabajo técnico de seguimiento al descargar registros de un segundo contenedor. (NEO-23159)
* Se ha corregido un problema que podía provocar errores en los flujos de trabajo al ejecutar una actividad de **Enriquecimiento**. (NEO-17338)
* Se ha añadido una comprobación al campo **Dobles para mantener** en la actividad del flujo de trabajo de **Anulación de duplicación** para evitar que se introduzca valores nulos o negativos.
* Se ha eliminado el **Asistente del planificador** de las campañas recurrentes para evitar la mención de horas y minutos. Solo se tienen en cuenta las fechas.
* Se ha corregido un problema con campos de almacenamiento adicionales al crear envíos a través de la opción **Calculado por un script** en la actividad de flujo de trabajo **Script**. (NEO-20609)
* Se ha corregido un problema que impedía que se eliminaran flujos de trabajo fantasma en las tareas de limpieza de la base de datos.
* Se ha corregido un problema que provocaba que fallara el flujo de trabajo técnico de **Facturación (perfiles activos)**. (NEO-19777)
* Se corrigió un problema al probar la conexión de la cuenta externa acsDefaultAccount. (NEO-23433)
* Se ha corregido un problema que impedía crear una extensión de esquema en una clave principal con varias columnas con una tabla Hadoop. (NEO-17390)
* Se ha corregido un problema en la actividad **Cargar (SOAP)** que podía impedir que los archivos WSDL se cargaran desde una dirección URL. (NEO-16924)
* Se ha corregido un problema que impedía realizar una **Parada incondicional** a través de la consola cuando se equilibraba la carga de varios servidores de flujo de trabajo activos. (NEO-19556)
* Se corrigió una regresión que ocasionaba que el flujo de trabajo de limpieza se bloqueara.
* Se ha corregido un problema que se podía producir al publicar una plantilla en una instancia de ejecución.
* Se ha corregido un problema que podía impedir que se ejecutara el flujo de trabajo técnico collectPrivacyRequests. (NEO-20513, NEO-25169)
* Se han corregido problemas que podían producirse al intentar conectarse a Audience Manager después de la actualización para la compilación 9080. (NEO-20511, NEO-25167)
* Se han corregido problemas que podían producirse al exportar informes en formato PDF o XLS. (NEO-20982, NEO-23493, NEO-23348)
* Se ha corregido un problema que podía mostrar un envío dos veces en la lista de envíos después de enviarlo.
* Se ha corregido un problema con la preparación de envíos que se podía producir cuando la configuración de enrutamiento estaba configurada para realizar el envío mediante intermediario.
* Se ha corregido un problema que podía mostrar un mensaje de error al hacer clic en un enlace de aplicación web dentro de un mensaje de línea.
* Se ha corregido un problema que podía impedir que Microsoft Dynamics CRM recuperara todas las entidades. (NEO-24528)
* Se ha corregido un problema que eliminaba el historial de actividades de **Consulta incremental** después de ejecutar el flujo de trabajo de limpieza.
* Se corrigió un problema al crear una cuenta externa intermediaria en el cual faltaba la opción NmsMidSourcing_LastBroadLog_&lt;InternalName>.
