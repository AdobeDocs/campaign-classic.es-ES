---
solution: Campaign Classic
product: campaign
title: Versión 19.2
description: Versión 19.2
audience: rns
content-type: reference
topic-tags: latest-release-notes
translation-type: tm+mt
source-git-commit: 57093a687534ed1e7f77738ca233d4cc86cf40cf
workflow-type: tm+mt
source-wordcount: '1376'
ht-degree: 100%

---


# Versión 19.2{#release-19-2}

## ![](assets/do-not-localize/limited_2.png) Versión 19.2.4: compilación 9082 {#release-19-2-4-build-9082}

_23 de diciembre de 2020_

>[!CAUTION]
>
>Esta versión incorpora un nuevo protocolo de conexión: la actualización es obligatoria para que el servidor de Campaign y la consola del cliente puedan conectarse a Campaign después del 21 de marzo de 2021.

* El protocolo de conexión se ha actualizado para seguir el nuevo mecanismo de autenticación IMS.
* Se ha corregido un problema de seguridad para reforzar la protección contra los problemas de falsificación de solicitudes del lado del servidor (SSRF). (NEO-27777)




## ![](assets/do-not-localize/red_2.png) Versión 19.2.3: compilación 9081 {#release-19-2-3-build-9081}

_viernes, 7 de febrero de 2020_

**Mejoras**

* Se ha corregido un problema de regresión debido a la implementación de la certificación SSL que hacía que la conexión del usuario fallara en el servidor de Windows. (NEO-20629)
* Se ha corregido un problema que mostraba un número de etiqueta de versión incorrecto en el menú **Acerca de**.

## ![](assets/do-not-localize/red_2.png) Versión 19.2: compilación 9080 {#release-19-2-build-9080}

_lunes, 2 de diciembre de 2019_

**Novedades**

<table> 
 <thead> 
  <tr> 
   <th> <strong>California Consumer Privacy Act (CCPA)</strong><br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> <p>La CCPA es la nueva normativa sobre privacidad del Estado de California que unifica y moderniza los requisitos de protección de datos y entrará en vigencia el 1 de junio de 2020. La CCPA se aplica a los clientes de Adobe Campaign que albergan datos de sujetos de datos que residen en California.</p>
    <p> Además de las funciones de privacidad ya disponibles (incluida la administración de consentimiento, la configuración de retención de datos y las funciones de usuario), Adobe Campaign le ayuda a facilitar su preparación para la CCPA:</p>
    <ul>
      <li>Derecho de acceso y derecho de eliminación: estamos aprovechando las capacidades agregadas para el RGPD. <a href="https://helpx.adobe.com/es/campaign/kb/acc-privacy.html#righttoaccess">Más información</a></li>
      <li>Puede rastrear si un consumidor ha optado por la venta de Información Personal. Para ello, debe ampliar la tabla Perfiles y agregar un campo de <strong>Opt-Out for CCPA</strong>. <a href="https://helpx.adobe.com/es/campaign/kb/acc-privacy.html#ccpa">Más información</a></li></td> 
  </tr> 
 </tbody> 
</table>

<table> 
 <thead> 
  <tr> 
   <th> <strong>Workflow live monitoring</strong><br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> <p>Ahora puede supervisar el estado de ejecución de todos los flujos de trabajo de la instancia mediante vistas predefinidas.</p>
   <p>Para obtener más información, consulte la <a href="../../workflow/using/monitoring-workflow-execution.md#filtering-workflows-status">documentación detallada</a>.</p></td> 
  </tr> 
 </tbody> 
</table>


<table> 
 <thead> 
  <tr> 
   <th> <strong>Interactive content with AMP</strong><br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
<td> <p>Adobe Campaign le permite probar el nuevo formato <a href="https://amp.dev/about/email/">AMP interactivo para correo electrónico</a>, que permite a los especialistas en marketing incluir componentes de AMP dentro de los mensajes para mejorar la experiencia de correo electrónico con contenido enriquecido, dinámico e interactivo, directamente procesable en el propio mensaje.</p>
   <p> Esta capacidad se presenta como una versión beta pública.</p>
   <p>Para obtener más información, consulte la <a href="../../delivery/using/defining-interactive-content.md">documentación detallada</a> y el <a href="https://docs.adobe.com/content/help/es/campaign-classic-learn/tutorials/sending-messages/email-channel/defining-interactive-email-content-with-amp.html">videotutorial</a>.</p><br /></td> 
  </tr> 
 </tbody> 
</table>


<table> 
 <thead> 
  <tr> 
   <th> <strong>Mensajería SMS segura (TLS)</strong><br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
<td> <p>Ahora, se admiten mensajes SMS seguros a través del conector genérico SMPP extendido. Esto permite establecer una conexión cifrada al proveedor.</p> <p><strong>Warning</strong> Esta función requiere un certificado actualizado en todos los servidores. Los certificados no válidos, revocados o caducados generarán errores que afectarán las capacidades generales de entrega de SMS.</p><p>Para obtener más información, consulte la <a href="https://helpx.adobe.com/es/campaign/kb/sms-connector-protocol-and-settings.html">documentación detallada</a>. </p> </td> 
  </tr> 
 </tbody> 
</table>

**Mejoras de seguridad**

* Se corrigieron las vulnerabilidades de secuencias de comandos entre sitios almacenadas en la interfaz de Campaign: validación de datos de entrada y codificación de salida. (NEO-16810)
* Se ha corregido un problema de seguridad en la autorización de perfiles que podía permitir el acceso a datos no autorizados, reforzando la directiva de restricción de inicio de sesión. (NEO-14445)

**Mejoras**

* Optimización del consumo de memoria para notificaciones push.
* Para optimizar el rendimiento y el almacenamiento, se ha mejorado la administración del archivo **logins.log**. El archivo ahora se divide en varios archivos, uno cada día con un máximo de 365 archivos retenidos. [Más información](../../production/using/log-files.md)
* La cuenta externa de Microsoft Dynamics CRM ahora se puede configurar con credenciales de contraseña (contraseña + nombre de usuario) o certificado (clave privada). [Más información](../../installation/using/external-accounts.md#microsoft-dynamics-crm-external-account)
* Se han añadido algunas mejoras al conector Hadoop FDA para mejorar la fiabilidad
* Se ha agregado una protección específica para comprobar el espacio en disco antes de permitir cargar recursos públicos en el servidor.
* Se han añadido nuevas [Opciones de campaña](../../installation/using/configuring-campaign-options.md):
   * La opción de configuración **WdbcKillSessionPolicy** permite afectar al comportamiento **Unconditional Stop** en todos los flujos de trabajo y consultas de base de datos PostgreSQL.
   * La opción **NmsOperation_DeliveryPreparationWindow** permite definir el número de días por encima de los cuales los envíos con estado incoherente se excluirán del recuento de entregas en ejecución.
   * La opción **WdbcOptions_TempDbName** permite configurar una base de datos independiente para las tablas de trabajo en Microsoft SQL Server. Esto optimiza los backups y la replicación. [Más información](../../production/using/rdbms-specific-recommendations.md#microsoft-sql-server)
   * La opción **XtkCleanup_NoStats** se ha mejorado para PostgreSQL para controlar mejor el comportamiento del paso de optimización del almacenamiento del flujo de trabajo de limpieza de la base de datos. [Más información](../../production/using/database-cleanup-workflow.md#statistics-update)
* Se ha agregado un mecanismo de bloqueo de cuenta a la API **Logon()**. Evita cualquier otro intento de inicio de sesión después de un cierto número de intentos consecutivos de inicio de sesión fallidos dentro de un periodo especificado.
* Una nueva opción **Maximum personalization run time** en las propiedades de entrega permite definir un periodo de espera para el tiempo de ejecución de la personalización, para evitar que la fase de personalización se ejecute durante mucho tiempo. [Más información](../../delivery/using/personalization-fields.md#timing-out-personalization)
* Se ha agregado la opción **ftp protocol** para permitirle utilizar una configuración proxy para las conexiones SFTP. [Más información](../../installation/using/configuring-campaign-server.md#proxy-connection-configuration)
* Nueva compatibilidad de acceso proxy a un servidor externo SFTP para entornos locales.
* Se ha agregado una protección específica para evitar la instalación de paquetes que no son compatibles con la instancia de Campaign. [Más información](../../installation/using/installing-campaign-standard-packages.md)

_Deprecated systems_

Los siguientes sistemas ya están [deprecated](https://helpx.adobe.com/es/campaign/kb/deprecated-and-removed-features.html) para implementaciones de Campaign Classic:
* Apache 2.2
* Centos 6

Asegúrese de que está en las versiones compatibles de cualquier sistema que se enumera en la matriz de compatibilidad de campañas más reciente. [Más información](https://helpx.adobe.com/es/campaign/kb/compatibility-matrix.html)

_Campaign Mobile SDK_

Ya está disponible la compilación 1.0.26 del SDK para iOS. En esta nueva compilación, se ha añadido la compatibilidad con iOS 13. Esta nueva versión ahora admite la prioridad de notificación y el nuevo proceso de administración de token de registro para las notificaciones push de iOS 13. Si está ejecutando aplicaciones en una versión anterior del SDK, debe volver a compilar las aplicaciones con el nuevo SDK. Para obtener el SDK, póngase en contacto con el Servicio de atención al cliente de Adobe.

**Parches**

* Se ha corregido un problema de bloqueo cuando el campo **Añadir tabla vinculada** está vacío en la actividad de flujo de trabajo **Carga de datos (RDBMS)**. (NEO-12213)
* Se ha corregido un problema que podía hacer que el servidor intermediario no procesara determinados mensajes. (NEO-12395)
* Se ha corregido un problema en el flujo de trabajo de limpieza de la base de datos al utilizar la opción de bandas de consulta con Teradata. (NEO-12399)
* Se ha corregido un problema que afectaba al análisis de entrega con la regla de tipología, incluido el dominio ne.jp. (NEO-12609)
* Se ha corregido un problema relacionado con las actualizaciones de SMS sobre TLS que implicaban una directiva de certificado más restrictiva. Estas actualizaciones podrían provocar un error de conexión entre los servidores de marketing y de fuentes intermedias en caso de que un certificado no esté actualizado. (NEO-17698)
* Se ha corregido un problema al usar el botón **Test connection** en una cuenta externa en un entorno de abastecimiento intermedio con autenticación Vault. (NEO-12722)
* Se ha corregido un problema en las consultas que usaban funciones de fecha con una conexión Hadoop de FDA. (NEO-12847)
* Se ha corregido un problema al reemplazar una imagen en el editor de correo electrónico. (NEO-13098)
* Se ha corregido un problema que podía provocar errores posteriores a la actualización en carpetas que se habían eliminado o movido a otra ubicación. (NEO-13118)
* Se ha corregido un problema en la visualización de imágenes al utilizar la opción **Define image per device screen size** en mensajes LINE. (NEO-13228)
* Se ha corregido un problema con la preparación de la entrega cuando la opción **Exclude duplicate address during delivery** no está seleccionada. (NEO-13240)
* Se ha corregido un problema en los flujos de trabajo al utilizar la actividad **File transfer** para descargar archivos mediante la opción **Delete the source files after transfer**, con un nombre que contenía un carácter de espacio. (NEO-13411)
* Se ha corregido un problema con la limpieza de caché de Tomcat que podía provocar problemas de memoria. (NEO-13456)
* Se ha corregido un problema al instalar **Control of offer engine with execution instance** existente que se ejecuta en Microsoft SQL 2017. (NEO-13539)
* Se ha corregido un problema de bloqueo de la consola que se producía al desmarcar direcciones URL rastreadas en un correo electrónico, desde la ficha **Contenido de texto** debido a una variable no inicializada. (NEO-13545)
* Se ha corregido un problema de codificación en el nombre del remitente chino. (NEO-13837)
* Se ha corregido un error que se podía generar al mostrar los datos de respuesta del estudio desde el Explorador. (NEO-14590)
* Se ha corregido un problema que podía provocar discrepancias entre la clasificación del registro de entrega y la tabla de cuarentena. (NEO-16547)
* Se ha corregido un problema con las claves DKIM que no estaban incrustadas en los correos electrónicos. (NEO-16804)
* Se ha corregido un problema que mostraba el código de error incorrecto cuando se usaba un token de sesión no válido en el contexto de llamadas de API para desencadenar eventos. El código de error era &#39;HTTP 200 OK&#39; en lugar de &#39;HTTP 403 Prohibido&#39;. (NEO-16826)
* Se ha corregido un problema que se producía al mostrar informes de entrega mediante acceso web. (NEO-17015)
* Se ha corregido un problema de autenticación IMS al iniciar sesión en Adobe Campaign. (NEO-17312)
* Se ha corregido un problema que impedía que el proceso de Administración de privacidad eliminara los correos electrónicos en cuarentena. (NEO-17314)
* Se corrigieron problemas de rendimiento después de actualizar a 9031 con la base de datos SQL. (NEO-17558)
* Se ha corregido un problema que afectaba al conector CRM con Salesforce. (NEO-17712)
* Se ha corregido un problema de tiempo de espera al importar datos desde un SFTP externo. (NEO-19723)
* Se ha corregido un problema al acceder a modelos predictivos. (NEO-19713)
* Se ha corregido un problema que afectaba al muestreo aleatorio en la actividad de flujo de trabajo de **Split** con la base de datos FDA de Hadoop. (NEO-16636)
* Se ha corregido una regresión en Oracle que hacía que algunas funciones se consideraran no válidas después de la postactualización. (NEO-12759)





