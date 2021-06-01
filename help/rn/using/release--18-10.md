---
product: campaign
title: Notas de la versión de Campaign 18.10
description: Notas de la versión de Campaign 18.10
feature: Información general
role: Business Practitioner
level: Beginner
exl-id: 57996f77-4ac2-402a-95db-b75d4bea4eeb
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: tm+mt
source-wordcount: '2372'
ht-degree: 98%

---

# Versión 18.10{#release-18-10}

## Versión 18.10.6: compilación 8985{#release-18-10-6-build-8985}

12 de julio de 2019

**Mejoras**

* Ahora prohibimos la eliminación de los registros de prueba creados en Microsoft Dynamics durante el flujo de trabajo de importación.
* Se ha corregido un problema con la actividad del flujo de trabajo Recolector de fichero que creaba errores de registro repetidamente cuando se denegaba el acceso a un archivo. (NEO-12085)
* Se ha corregido un problema que ocasionaba discrepancias de informes entre las actividades del usuario y los informes de seguimiento para el indicador de entrega abierto. (NEO-11742)
* Se han mejorado los permisos para ejecutar el paquete de zona de seguridad cuando utilice una cuenta interna.
* Se ha corregido un problema que podría provocar errores en los registros de mtachild. (NEO-8978)

## Versión 18.10.5: compilación 8984{#release-18-10-5-build-8984}

23 de abril de 2019

**Mejoras**

* Se ha corregido un problema con el interbloqueo de SQL que hacía que el análisis de entrega falle en caso de análisis/entrega simultáneos (cuando se analizaron dos entregas al mismo tiempo). (NEO-13026)
* Se ha eliminado el límite de registro de 10 000 en Workflow Heatmap para solucionar un problema de ausencia de datos. (NEO-12329)
* Se ha corregido un problema que se producía al utilizar la opción “Conservar todos los datos adicionales del conjunto principal” en una actividad de flujo de trabajo de enriquecimiento. (NEO-13291)

## Versión 18.10.4: compilación 8983{#release-18-10-4-build-8983}

15 de abril de 2019

**Mejoras**

* Se ha corregido un problema con el proceso de computación de los indicadores de seguimiento para los mensajes transaccionales. (NEO-12529, NEO-12581)
* Se ha corregido un problema con la API HTTPRequest que no esperaba a que terminaran las retrollamadas. (NEO-12628)
* Los índices se agregaron en las tablas temporales del vale para optimizar las entregas. (NEO-12437)
* Se ha corregido un problema que se producía al analizar un mensaje segmentado para destinatarios para los dominios japoneses (.JP). (NEO-12246)
* En la integración de Analytics, ahora se permite la recuperación de datos del segmento AAM con caracteres %. (NEO-12025)
* Se ha corregido un problema con el bloqueo de Tomcat al enviar notificaciones inmediatas con HTTP2. (NEO-12701)

## Versión 18.10.3: compilación 8981{#release-18-10-3-build-8981}

29 de enero de 2019

>[!CAUTION]
>
>Se ha retirado esta compilación. [actualice a la última versión](../../production/using/build-upgrade.md) o póngase en contacto con el [Servicio de atención al cliente de Adobe](https://helpx.adobe.com/es/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html).

**Mejoras**

* Se ha corregido un problema con la actividad de flujo de trabajo de transferencia de archivos s3. (NEO-12473)
* Se ha corregido un problema en el que el flujo de trabajo de seguimiento podría fallar. (NEO-12520)
* Se ha corregido un problema con el inicio de sesión de IMS.
* Se ha corregido un problema con la vista previa y la aprobación de contenido en mensajes transaccionales al utilizar un ID de oferta grande.
* Se ha corregido un problema con el flujo de trabajo intermediario (contadores de entregas).
* Se ha corregido un problema con la actualización de la estructura de la base de datos que dejaba caer nuevos índices en NmsRecipient.
* Se ha corregido un bloqueo de consola que podría producirse al utilizar la opción Definido en un archivo externo para el destino principal de una entrega. (NEO-12349)
* Se corrigieron varios bloqueos InMail.
* Se ha corregido un problema que se producía al utilizar una actividad de flujo de trabajo de actualización de datos para eliminar registros almacenados en una base de datos de Teradata de FDA.
* Se corrigieron problemas de incoherencia en la administración de claves secretas.
* Se ha corregido un problema con la actividad de enriquecimiento al escribir un campo como: xml=true y calculated=true
* Se ha corregido un problema con la pérdida de caracteres al enviar notificaciones inmediatas en una aplicación móvil.
* Se ha corregido un problema que impedía cambiar de FDA a método de sincronización SOAP en una cuenta externa intermediaria.

## Versión 18.10.2: compilación 8978{#release-18-10-2-build-8978}

6 de diciembre de 2018

>[!CAUTION]
>
>Se ha retirado esta compilación. [actualice a la última versión](../../production/using/build-upgrade.md) o póngase en contacto con el [Servicio de atención al cliente de Adobe](https://helpx.adobe.com/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html).

**Mejoras**

* Se solucionaron varios problemas al ejecutar flujos de trabajo con MySQL en FDA. (NEO-11652)
* Se ha corregido un problema de rendimiento al enviar notificaciones push. (NEO-11787)
* Se ha corregido un problema de agotamiento de ID al utilizar direcciones semilla en una entrega. (NEO-11842)
* Se ha corregido un problema con el bloqueo del cliente que podría producirse al utilizar flujos de trabajo complejos. (NEO-11847)
* Se ha corregido un problema con la visualización al utilizar una distribución de valores con un vínculo 1:N. (NEO-11820)
* Se ha corregido un error de Oracle en Workflow Heatmap.
* Se ha corregido un problema que se producía al añadir una propuesta de oferta en una actividad de enriquecimiento.
* Se ha corregido un problema de conexión de gestión de datos de SQL.
* Se ha corregido un problema con la generación de nombres de tabla de flujo de trabajo temporales en el caso de ID negativos.
* Se ha corregido un problema con el cálculo de las duraciones del flujo de trabajo en Workflow HeatMap.


## Versión 18.10: compilación 8977{#release-18-10-build-8977}

5 de noviembre de 2018

>[!CAUTION]
>
>Se ha retirado esta compilación. [actualice a la última versión](../../production/using/build-upgrade.md) o póngase en contacto con el [Servicio de atención al cliente de Adobe](https://helpx.adobe.com/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html).

**Novedades**

<table> 
 <thead> 
  <tr> 
   <th> Funcionalidad<br /> </th> 
   <th> Descripción<br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> Mejoras de notificaciones push<br /> </td> 
   <td> Se ha implementado una serie de mejoras para las notificaciones push en Adobe Campaign:<br /> 
    <ul> 
     <li> <p>Seguimiento de notificaciones silenciosas en iOS </p> </li> 
     <li> <p>Implementación de comentarios en las llamadas de registro en iOS</p> </li> 
     <li> <p>Mejorar la velocidad de preparación de la distribución de iOS</p> </li> 
    </ul> <p>Como parte de la pérdida de compatibilidad de GCM con Google, el conector Android V2 ahora solo permite conexiones al servidor FCM.</p><p>Para obtener más información, consulte la <a href="../../delivery/using/integrating-campaign-sdk-into-the-mobile-application.md">documentación detallada</a>. La actualización manual para FCM se detalla en este <a href="https://helpx.adobe.com/es/campaign/kb/migrate-to-fcm.html">artículo</a>. </p> </td> 
  </tr> 
  <tr> 
   <td> Actividad de gestión de datos SQL<br /> </td> 
   <td> <p>Se ha añadido una nueva actividad de flujo de trabajo de gestión de datos. La actividad de <strong>Gestión de datos SQL</strong> permite escribir sus propios scripts SQL para crear y rellenar tablas de trabajo (solo FDA). </p> <p>Para obtener más información, consulte la <a href="../../workflow/using/sql-data-management.md">documentación detallada</a>.</p></td> 
  </tr> 
  <tr> 
   <td> Monitorización del flujo de trabajo<br /> </td> 
   <td> <p>Con el nuevo Workflow HeatMap de Adobe Campaign, los administradores de la plataforma tienen una representación gráfica rápida de todos los flujos de trabajo simultáneos, lo que les permite hacer un seguimiento de la carga en la instancia y utilizar esta información para planificar los flujos de trabajo.</p> <p>Para obtener más información, consulte la <a href="../../workflow/using/heatmap.md">documentación detallada</a>.</p> <p>El paquete Workflow HeatMap también está disponible bajo demanda para las versiones anteriores a 8977 (inicio de compilaciones 8700). Para obtener más información sobre cómo solicitarlo e instalarlo, consulte <a href="https://helpx.adobe.com/es/campaign/kb/install-workflow-heatmap-package.html">esta página</a>.</p> </td> 
  </tr> 
 </tbody> 
</table>

**Mejoras de seguridad**

* Se ha corregido un problema de seguridad que podría provocar vulnerabilidades en los ataques de Forgery de solicitudes de servidor (SSRF) y ataques de denegación de servicio (DoS). (NEO-11453)
* Ahora, Campaign ofrecerá el contenido (seguimiento de redirecciones, páginas espejo, encuestas, etc.) con el encabezado X-Robots-Tag: nocache. Esto evita la indexación de este contenido por motores de búsqueda de Internet. (NEO-11101)
* Se solucionó un problema de inyección de XTK en API de suscripción (nms:subscription:Unsubscribe y nms:subscription:Subscribe).
* Se ha corregido un problema de inyección de XTK en la aplicación web para cancelar la suscripción.
* Se han eliminado contraseñas que se mostraban en algunos registros SMS.

**Mejoras**

* Las API de Campaign Classic están ahora disponibles en una [página dedicada](https://docs.adobe.com/content/help/en/campaign-classic/technicalresources/api/index.html). Si utilizó el archivo jsapi.chm, debería consultar la nueva versión en línea.
* Ahora admite PostgreSQL 10, Debian 9 y Teradata 16.20. Consulte la [matriz de compatibilidades](https://helpx.adobe.com/es/campaign/kb/compatibility-matrix.html).
* Al crear una conexión SFTP, ahora puede utilizar la autenticación proxy. Para obtener más información, consulte la [documentación detallada](../../installation/using/file-res-management.md) (NEO-9868).
* La opción de **fórmula de cálculo de fecha** está disponible en las propiedades de entrega al crear una única entrega con la plantilla de envíos de correo postal. (NEO-9792)
* La administración de nombres de dominio se ha mejorado para el seguimiento de cookies y las aplicaciones Web. Para obtener más información, consulte la sección “Evoluciones técnicas”.
* La importación de activos compartidos de Adobe Marketing Cloud en una página de entrega o de aterrizaje se ha mejorado en términos de seguridad y rendimiento.
* Hay una nueva casilla de verificación disponible en la cuenta externa del canal móvil para habilitar rastreos detallados de SMPP en el archivo de registro, lo cual hace que la salida sea directamente accesible desde la interfaz de Adobe Campaign.
* En los registros generales hay ahora una distinción entre el número máximo de conexiones y el número máximo de mensajes por hora. Cuando se alcanzan los límites, es posible saber por qué el rendimiento está limitado. Anteriormente, el mismo mensaje (“cuota alcanzada”) se aplica a ambos casos.
* Ahora puede especificar una secuencia de comandos SQL para ejecutarla al adquirir una conexión desde el grupo. Esta secuencia de comandos se puede utilizar para definir el esquema predeterminado. Esta secuencia de comandos se aplicará después de agrupar la consulta. (NEO-11256)
* El SDK de Campaign ya no almacena el identificador de usuario para cumplir con nuestras regulaciones PII. Ahora los datos se almacenan como un hash.
* Al importar un archivo XML de exportación de paquetes, Campaign admite la presencia de BOM en el archivo, incluso si la codificación se declara explícitamente en ella.

**Evoluciones técnicas**

Actualización de cliente y servidor

>[!CAUTION]
>
>Si tiene un servidor actualizado a 18.10, tendrá que utilizar un cliente de 18.10 para acceder al servidor. El cliente de 18.10 podrá conectarse a una versión de servidor anterior.

Administración de nombres de dominios

La administración de nombres de dominio se ha mejorado para el seguimiento de cookies y las aplicaciones Web.

Ahora, todos los nombres de dominio de segundo nivel de dos dígitos se admiten de forma predeterminada (por ejemplo, .aa.com). Para nombres de dominio más complejos (por ejemplo, dominios de segundo nivel de tres letras como .com.au), debe añadirlos en la opción **cookieDomains** del servidor de configuración (en la etiqueta de redirección). Este es un ejemplo.

```
<redirection cookiedomain="http://toureiffel.paris">
```

Mejoras en el índice

Los índices de NmsRecipient se han modificado. Esto mejora el rendimiento en las consultas que utilizan esta tabla. Si ha realizado una extensión de NmsRecipient, quizá desee verificar que no tiene índices que dupliquen los nuevos índices (para minimizar el uso del espacio en el servidor de bases de datos). (NEO-8228)

En PostgreSql al utilizar una intercalación UTF-8, ahora es posible crear índices que optimice las operaciones “LIKE &#39;string%&#39;” (o “starts with”). Si realiza otras operaciones en la misma columna (orden o unión por ejemplo), se necesitará otro índice estándar. En el lado del esquema, esto se hará añadiendo indexOption=&quot;searchFromStart&quot; en la definición del índice (creará un índice varchar_pattern_ops en lugar de un índice estándar de btree). Por ejemplo (en NmsRecipient):

```
<dbindex name="email2"> <!-- optimize order by/join (and startWith if not PostgreSql with an UTF-8 collation) operations -->
  <keyfield xpath="@email"/>
</dbindex>
<dbindex name="email3" indexOption="searchFromStart"><!-- optimize startsWith operation on PostgreSql when a UTF-8 collation is used; create no index in other cases-->
  <keyfield xpath="@email" />
</dbindex>
```

Se han agregado nuevos índices a NmsRtEvent y NmsEventHisto (en la columna “Programado”), debe mejorar el tiempo de visualización en el formulario correspondiente (NEO-11738).

Estos cambios de índice pueden producir un aumento del tiempo necesario para realizar la comparación.

**Parches**

* Se solucionó un error que impedía descargar los archivos de la actividad de flujo de trabajo de **descarga de web**. (NEO-11105)
* Se ha corregido un error que ocasionalmente dejaba el flujo de trabajo **Envío de indicadores y atributos de campaña** en un estado fallido (NEO-10820).
* Se ha corregido un problema que borraba la lista de destinatarios creada después de ejecutar la actividad de actualización de lista en un flujo de trabajo. (NEO-11696)
* Se ha corregido un error que mostraba incorrectamente las campañas un mes por delante en el calendario de Campaign (en una instancia de japonés). (NEO-11445)
* Se ha corregido un problema que impedía que la configuración de Analytics se mostrara en la ficha Análisis de Web de las propiedades de entrega. (NEO-11619)
* Se ha corregido un error que se mostraba al intentar editar y guardar el formulario de entrada de nms:delivery. (NEO-10973)
* Se solucionó un problema de configuración de cuenta externo que se producía al ejecutar un flujo de trabajo que contiene una actividad de transferencia de archivos. (NEO-11012)
* Se ha corregido un problema que devolvía líneas en blanco al utilizar la función zcat para cargar archivos en la actividad de carga de datos. (NEO-11273)
* Se ha corregido un problema que generaba registros amplios duplicados durante el análisis de la entrega. (NEO-11360)
* Se ha corregido un problema que provocaba que se enviara un error debido a la clave de vínculo externa que falta después de ejecutar la actividad de enriquecimiento en un flujo de trabajo. (NEO-11537)
* Se ha corregido un problema que impedía la desinstalación o reparación correcta de Adobe Campaign cuando la ruta de instalación incluía caracteres GB18030 chinos específicos.
* Se ha corregido un problema que mostraba algunos registros de seguimiento en la entrega incorrecta. (NEO-11412)
* Se ha corregido un problema que podría provocar que algunas partes de los registros de envío restantes en estado pendiente durante más de lo previsto. (NEO-11336)
* Se ha corregido un error que se producía al editar una consulta para agregar un cupón a una entrega. (NEO-11037)
* Se ha corregido un problema en los informes que hacía que los gráficos siempre calculan la suma de los valores sin importar el operador agregado. (NEO-10913)
* Como la función “request.scheme” ya no se utiliza, se ha eliminado de la documentación de JSAPI. (NEO-10828)
* Se ha corregido un problema que impedía a algunos usuarios con configuraciones de zona horaria específicas iniciar sesión en Adobe Campaign. (NEO-10712)
* Se ha corregido un problema que se producía al configurar una cuenta externa del canal móvil con el conector de SOAP genérico ampliado: si se ha especificado utilizando parámetros diferentes para el receptor, el transmisor utilizaría incorrectamente estos parámetros en lugar de sus propios parámetros.
* Se ha corregido un problema que ocasionaba que fallaran las entregas programadas al configurar una frecuencia para la regla de presión, puesto que las entregas se han recalculado después del primer arbitraje. (NEO-10016)
* Se ha corregido un problema que hacía que el servidor IIS se cayera durante el proceso de reciclaje de la aplicación (en la biblioteca de nlsrvmod.dll). (NEO-10862)
* Se ha corregido un problema que podría evitar la búsqueda en un destinatario en la pantalla **Perfiles y objetivos**. (NEO-8228)
* Se ha corregido un problema que podría provocar un error de tiempo de espera al acceder a la carpeta Historial de eventos en el caso de un número elevado de registros. (NEO-11738)
* Se ha corregido un problema que podría dar lugar a que los destinatarios de la entrega LINE devolviera incorrectamente como “Inaccesible”. (NEO-10833)
* Se ha corregido un problema que se producía al ejecutar una consulta de flujo de trabajo con una columna adicional en Oracle. (NEO-11615)
* Se ha realizado una mejora para asegurarse de que las conexiones cerradas no se mantengan en el grupo de conexiones durante demasiado tiempo. (NEO-11392)
* Se ha corregido un problema que se producía al utilizar una actividad de flujo de trabajo de destino (consulta, carga de datos (RDBMS), etc.) conectada a través de FDA a una tabla Oracle externa que contenía caracteres UTF8 (nombre de campo, nombre de campo, etc.) y que también contenía una restricción de clave principal con un nombre de restricción predeterminado generado por el sistema. (NEO-10714)
* Se ha corregido un problema que podría evitar eliminar el contenido HTML de una entrega. (NEO-11327)
* Se ha corregido un problema con la vista preliminar de los archivos XML y CSV en un correo directo después de que se ejecute una campaña. (NEO-11290)
* Se ha corregido un problema que se producía al ordenar datos en una actividad de flujo de trabajo de enriquecimiento. (NEO-11394)
* Se ha corregido un problema que se producía al ordenar los datos en un informe personalizado. (NEO-10896)
* Se ha corregido un problema que provocaba errores al utilizar la configuración de useVault con Teradata. (NEO-11399)
* Se ha corregido un problema que hacía que la consola del cliente de Adobe Campaign se cayera al eliminar varias líneas de consulta. (NEO-10744)
* Se ha corregido un problema que impedía que se aplicaran las reglas de presión en algunos casos al enviar un correo postal. (NEO-9004)
* Se ha corregido un problema que se producía al utilizar la actividad de carga de datos para importar una columna con el tipo de datos “hora”: el separador de tiempo se restaurará incluso después de eliminarse. (NEO-10743)
* Se ha corregido un problema que impedía que la carpeta entregas se mostrara en la lista de carpetas de ejecución en las propiedades de entrega al editar una entrega recurrente. (NEO-11094)
* Se ha corregido un problema que impedía que la ventana Ver población mostrara más de 200 registros como destino resultante de una actividad de consulta en un flujo de trabajo. (NEO-11195)
* Se ha corregido un problema en Oracle que impedía ejecutar una consulta DELETE con más de 1000 elementos seleccionados. (NEO-11171)
* Se ha corregido un problema que provocaba codificar las direcciones URL como URL rastreadas en los parámetros adicionales de una entrega de notificaciones de Android. (NEO-11468)
* Se ha corregido un error de secuencia de comandos que se producía en el informe de actividades del usuario al configurar los parámetros en “Intervalos de un día” y “Abrir”. (NEO-11655)
* Se ha corregido un problema que se producía al conectar con el servidor abastecimiento medio o al centro de mensajes a través de un proxy web autenticado. (NEO-11309)
* Se ha corregido un error de Oracle que se producía cuando se guardó una nueva composición de distribución después de seleccionar un elemento de un esquema específico **basado en una vista SQL**. (NEO-11682)
* Se ha corregido un problema que provocaba que generaba archivos rechazados que contienen los falsos positivos al procesar un archivo zip que contiene un .csv a través de una actividad de archivo de carga.
* xtkjoblog ahora se depura por la limpieza.
