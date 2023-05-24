---
product: campaign
title: Versiones de Campaign Classic 2018
description: Más información sobre las actualizaciones de Campaign Classic 2018
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
hidefromtoc: true
exl-id: f70fceba-4bbf-4f33-8746-e4405a1cdae6
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: tm+mt
source-wordcount: '5385'
ht-degree: 97%

---

# Versiones de 2018{#release-2018}



## Versión 18.10

### Versión 18.10.6, compilación 8985{#release-18-10-6-build-8985}

12 de julio de 2019

**Mejoras**

* Ahora prohibimos la eliminación de los registros de prueba creados en Microsoft Dynamics durante el flujo de trabajo de importación.
* Se ha corregido un problema con la actividad del flujo de trabajo Recolector de fichero que creaba errores de registro repetidamente cuando se denegaba el acceso a un archivo. (NEO-12085)
* Se ha corregido un problema que ocasionaba discrepancias de informes entre las actividades del usuario y los informes de seguimiento para el indicador de entrega abierto. (NEO-11742)
* Se han mejorado los permisos para ejecutar el paquete de zona de seguridad cuando utilice una cuenta interna.
* Se ha corregido un problema que podría provocar errores en los registros de mtachild. (NEO-8978)

### Versión 18.10.5, compilación 8984{#release-18-10-5-build-8984}

23 de abril de 2019

**Mejoras**

* Se ha corregido un problema con el interbloqueo de SQL que hacía que el análisis de entrega falle en caso de análisis/entrega simultáneos (cuando se analizaron dos entregas al mismo tiempo). (NEO-13026)
* Se ha eliminado el límite de registro de 10 000 en Workflow Heatmap para solucionar un problema de ausencia de datos. (NEO-12329)
* Se ha corregido un problema que se producía al utilizar la opción “Conservar todos los datos adicionales del conjunto principal” en una actividad de flujo de trabajo de enriquecimiento. (NEO-13291)

### Versión 18.10.4, compilación 8983{#release-18-10-4-build-8983}

15 de abril de 2019

**Mejoras**

* Se ha corregido un problema con el proceso de computación de los indicadores de seguimiento para los mensajes transaccionales. (NEO-12529, NEO-12581)
* Se ha corregido un problema con la API HTTPRequest que no esperaba a que terminaran las retrollamadas. (NEO-12628)
* Los índices se agregaron en las tablas temporales del vale para optimizar las entregas. (NEO-12437)
* Se ha corregido un problema que se producía al analizar un mensaje segmentado para destinatarios para los dominios japoneses (.JP). (NEO-12246)
* En la integración de Analytics, ahora se permite la recuperación de datos del segmento AAM con caracteres %. (NEO-12025)
* Se ha corregido un problema con el bloqueo de Tomcat al enviar notificaciones inmediatas con HTTP2. (NEO-12701)

### Versión 18.10.3, compilación 8981{#release-18-10-3-build-8981}

29 de enero de 2019

>[!CAUTION]
>
>Se ha retirado esta compilación. Por favor [actualice a la última versión](../../production/using/build-upgrade.md)  o contacto [Adobe del Servicio de atención al cliente](https://helpx.adobe.com/es/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html).

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

### Versión 18.10.2, compilación 8978{#release-18-10-2-build-8978}

6 de diciembre de 2018

>[!CAUTION]
>
>Se ha retirado esta compilación. Por favor [actualice a la última versión](../../production/using/build-upgrade.md) o contacto [Adobe del Servicio de atención al cliente](https://helpx.adobe.com/es/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html).

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


### Versión 18.10.1, compilación 8977{#release-18-10-build-8977}

5 de noviembre de 2018

>[!CAUTION]
>
>Se ha retirado esta compilación. Por favor [actualice a la última versión](../../production/using/build-upgrade.md) o contacto [Adobe del Servicio de atención al cliente](https://helpx.adobe.com/es/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html).

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
    </ul> <p>Como parte de la pérdida de compatibilidad de GCM con Google, el conector Android V2 ahora solo permite conexiones al servidor FCM.</p><p>Para obtener más información, consulte la <a href="../../delivery/using/integrating-campaign-sdk-into-the-mobile-application.md">documentación detallada</a>.</p> </td> 
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
* Se ha corregido un problema de inyección de XTK en API de suscripción (nms):subscription:Cancelar suscripción y nms:subscription:Suscribirse).
* Se ha corregido un problema de inyección de XTK en la aplicación web para cancelar la suscripción.
* Se han eliminado contraseñas que se mostraban en algunos registros SMS.

**Mejoras**

* Las API de Campaign Classic están ahora disponibles en una [página dedicada](https://experienceleague.adobe.com/developer/campaign-api/api/index.html?lang=es). Si utilizó el archivo jsapi.chm, debería consultar la nueva versión en línea.
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

## Versión 18.6

### Versión 18.6.2, compilación 8949{#release-18-6-3-build-8949}

22 de agosto de 2018

>[!CAUTION]
>
>Se ha retirado esta compilación. Por favor [actualice a la última versión](../../production/using/build-upgrade.md) o contacto [Adobe del Servicio de atención al cliente](https://helpx.adobe.com/es/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html).

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
   <td> Banda de consultas<br /> </td> 
   <td> <p>Cuando varios usuarios de Campaign se conectan con la misma cuenta externa de Teradata de FDA, ahora puede pasar una banda de consulta (pares clave/valor) específica a cada usuario. Cada vez que un usuario de Campaign realiza una consulta en la base de datos de Teradata, Adobe Campaign ahora puede enviar metadatos asociados al usuario. Estos datos, que se componen de una lista de claves y valores, pueden ser utilizados por administradores de Teradata para fines de auditoría o para administrar derechos de acceso, por ejemplo.</p><p>Para obtener más información, consulte la <a href="../../installation/using/external-accounts.md">documentación detallada</a>.</p> </td>
  </tr> 
 </tbody> 
</table>

**Mejoras**

* Se han mejorado los registros de archivos de correo electrónico, lo que facilita la comprobación de los mensajes de correo electrónico que se han entregado o no se han enviado correctamente a través del archivo BCC. (NEO-10675)
* Se ha corregido un problema que provocaba la visualización de las direcciones IP del equilibrador de carga en lugar de las direcciones IP del cliente en los registros de seguimiento. (NEO-11295)
* Se ha corregido un problema aleatorio que ocasionaba que las propiedades de una entrega se sobrescriban erróneamente. (NEO-11015)
* Se ha corregido un error de sintaxis al ordenar los resultados de las actividades de enriquecimiento. (NEO-11394)
* Se ha corregido un problema que se producía al utilizar campos calculados en una actividad de flujo de trabajo **[!UICONTROL Survey answers]**. (NEO-11382)
* Se ha actualizado Tomcat para evitar la explotación de vulnerabilidades. (NEO-11503)
* Se ha corregido un error con la codificación LATIN1 al utilizar una conexión de FDA con una base de datos PostgreSQL. (NEO-11299)
* Se ha corregido un problema que se producía al usar el **[!UICONTROL Prepare the personalization data with a workflow]** opción de envío. (NEO-11047)
* Se ha corregido un problema posterior a la actualización que impedía la entrega de SMS al utilizar un conector extendido.
* Se mejoró la importación/exportación de paquetes (se han añadido registros y regiones en la interfaz).
* Se ha corregido un problema que mostraba errores no viables en el registro posterior de actualización cuando una actividad de flujo de trabajo **[!UICONTROL Survey answers]** no estaba completamente configurada.

**Evoluciones técnicas**

Banda de consultas

Se utiliza una clave específica (PROXYUSER o PROXYROLE) para asociar un usuario o función de Teradata a un usuario de Campaign. Se ha añadido un nuevo permiso para utilizar este usuario/función de proxy. Debe añadir el derecho al acceso de GRANT CONNECT THROUGH a la cuenta de la base de datos (la definida en la cuenta externa de Teradata).

Se ha añadido una nueva pestaña en las cuentas externas de Teradata. La pestaña **[!UICONTROL Query banding]** incluye las siguientes opciones:

* **[!UICONTROL Active]**: Marque esta casilla para activar la función.
* **[!UICONTROL Default]**: introduzca una banda de consulta predeterminada que se debe utilizar si un usuario no tiene una banda de consulta asociada. Si no se ha definido una banda de consulta predeterminada, los usuarios que no tengan bandas de consulta asociadas no podrán utilizar Teradata.
* **[!UICONTROL Users]**: para cada usuario, especifique una banda de consultas. Puede añadir todos los pares de clave/valor que necesite. Por ejemplo: ‘priority=1;carga de trabajo=high;’

Para obtener más información sobre la banda de consultas, vea esta sección.

* [https://docs.teradata.com/reader/cY5B~oeEUFWjgN2kBnH3Vw/a5G1iz~ve68yTMa24kVjVw](https://docs.teradata.com/reader/cY5B%7EoeEUFWjgN2kBnH3Vw/a5G1iz%7Eve68yTMa24kVjVw)
* [https://docs.teradata.com/reader/rgAb27O_xRmMVc_aQq2VGw/qVNfdszBssrZ7ttrE7AtmQ](https://docs.teradata.com/reader/rgAb27O_xRmMVc_aQq2VGw/qVNfdszBssrZ7ttrE7AtmQ)

### Versión 18.6.1, compilación 8947{#release-18-6-build-8947}

25 de junio de 2018

>[!CAUTION]
>
>Se ha retirado esta compilación. [Actualice a la última versión](../../production/using/build-upgrade.md) o contacte con el [soporte técnico](https://helpx.adobe.com/es/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html).

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
   <td> Mejoras de seguridad<br /> </td> 
   <td> Se ha añadido una serie de mejoras de seguridad a Campaign Classic. A continuación se enumeran las mejoras y correcciones.<br /> </td> 
  </tr> 
  <tr> 
   <td> Compatibilidad con Windows Server 2016<br /> </td> 
   <td> Adobe Campaign ahora es compatible con Windows Server 2016. Consulte la <a href="https://helpx.adobe.com/es/campaign/kb/compatibility-matrix.html">Matriz de compatibilidades de Campaign Classic</a>.<br /> </td> 
  </tr> 
 </tbody> 
</table>

**Mejoras de seguridad**

decryptString

La función **decryptString** ya no se utiliza. Consulte el artículo [Funciones obsoletas y eliminadas](deprecated-features.md).

Para nuevos clientes, esta función se utiliza ahora solamente para descifrar el ID cifrado del destinatario en las páginas de aterrizaje. Para descifrar contraseñas almacenadas en una cuenta externa, utilice la nueva función **decryptPassword**.

Para los clientes existentes, el comportamiento de esta función no cambia pero recomendamos que utilice **decryptPassword** en lugar de **decryptString**. La opción de compatibilidad con **XtkSecurity_Unsafe_DecryptString** se añade en la mejora y se activa de forma predeterminada, lo que le permite continuar usando la función. Si desea desactivar **decryptString**, desactive la opción.

decryptPassword

Se ha añadido la función **decryptPassword.** Permite descifrar una contraseña almacenada en una cuenta externa. Consulte la documentación de [JSAPI](https://helpx.adobe.com/es/campaign/kb/compatibility-matrix.html) para obtener más información.

API de archivo

Para las nuevas instalaciones, el acceso a carpetas mediante las API de archivo está limitado a las carpetas **var**, **sftp** y temporales de Adobe Campaign.

Para los clientes existentes, las API de archivo ya no pueden acceder a la carpeta **conf** de Adobe Campaign. La opción de compatibilidad con **XtkSecurity_Disable_JSFileSandboxing** se añade en la actualización y se activa de forma predeterminada, lo que le permite mantener el acceso a las otras carpetas. Si desea limitar el acceso a las carpetas temporales **var**, **sftp** y de Adobe Campaign, desactive la opción.

**Parche**

* Se ha corregido un problema que podría afectar el rendimiento del mensaje transaccional SMS. (NEO-9812)

## Versión 18.4

### Versión 18.4.5, compilación 8937{#release-18-4-5-build-8937}

21 de noviembre de 2018

**Mejoras**

* Se solucionaron varios problemas al ejecutar flujos de trabajo con MySQL en FDA. (NEO-11652)
* Se ha corregido un problema por el que una parte de la población de entrega permanecía en estado pendiente en casos específicos. (NEO-11336)
* Se ha corregido un problema intermitente con la respuesta automática de SMS. (NEO-11811)
* Se ha corregido un problema de agotamiento de ID al utilizar direcciones semilla en una entrega. (NEO-11842)
* Se ha corregido un error de sintaxis al realizar una ordenación en una actividad de flujo de trabajo de enriquecimiento. (NEO-11394)
* Se ha corregido un problema que podría provocar el bloqueo de un servidor web al reiniciar IIS. (NEO-10862)
* Se ha corregido un problema que podría provocar que el flujo de trabajo de seguimiento falle tras una actualización de compilación (FDA - SQL). (NEO-11635)
* Se ha corregido un problema que podría provocar que se pierdan los datos de la lista de flujos de trabajo. (NEO-11696)
* Se ha corregido un problema de rendimiento al enviar notificaciones push. (NEO-11787)
* Se ha corregido un problema que impedía que el seguimiento web funcionara para los dominios “com.au” (NEO-4385).
* Se ha corregido un problema con el bloqueo del cliente que podría producirse al utilizar flujos de trabajo complejos. (NEO-11847)
* Se ha corregido un error de Oracle al guardar una nueva entrega después de seleccionar un elemento de un esquema específico (NEO-11682).
* Se ha corregido un problema que se producía al consultar un campo que contiene caracteres con acentos (FDA/Teradata). La cuenta externa ahora permite cambiar la codificación utilizada para comunicarse con el controlador de Teradata. (NEO-11818).
* Se ha corregido un problema con el seguimiento al pasar direcciones URL en variables adicionales en una notificación inmediata que podría provocar datos incorrectos o sin formato recibidos por la aplicación móvil. (NEO-11468, NEO-11960)
* Se ha corregido un problema que ocasionaba un problema de visualización al utilizar una distribución de valores con un vínculo 1:N. (NEO-11820)
* Se ha corregido un problema que impedía que la carga masiva funcionara en Teradata 16.
* Se ha aumentado el tamaño del búfer para la marca de tiempo en Teradata para evitar problemas de vínculo con el controlador 15.10.
* Se ha mejorado la administración de los índices de nombres largos que podrían causar problemas después de la actualización.
* Se ha mejorado el tiempo disponible de memoria compartida durante el procesamiento secundario (MTA).
* Se ha corregido un posible bloqueo en Apache (seguimiento).


### Versión 18.4.4, compilación 8936{#release-18-4-4-build-8936}

1 de agosto de 2018

**Mejoras**

* Se han mejorado los registros de archivos de correo electrónico, lo que facilita la comprobación de los mensajes de correo electrónico que se han entregado o no se han enviado correctamente a través del archivo BCC. (NEO-10675)
* Se ha corregido un problema que provocaba la visualización de las direcciones IP del equilibrador de carga en lugar de las direcciones IP del cliente en los registros de seguimiento. (NEO-11295)
* Se ha corregido un error con la codificación LATIN1 al utilizar una conexión de FDA con una base de datos PostgreSQL. (NEO-11299)
* Se ha corregido un problema que se producía al usar el **[!UICONTROL Prepare the personalization data with a workflow]** opción de envío. (NEO-11047, NEO-11301)
* Se ha corregido un problema aleatorio que ocasionaba que las propiedades de una entrega se sobrescriban erróneamente. (NEO-11015)
* Se ha corregido un problema que se producía al utilizar campos calculados en una actividad de flujo de trabajo **[!UICONTROL Survey answers]**. (NEO-11382)
* Se ha corregido un problema que se producía al utilizar datos almacenados en XML en una actividad de flujo de trabajo **[!UICONTROL Survey answers]**. (NEO-10816)
* Se ha corregido un problema que se producía al realizar la actualización del servidor con la compilación 8935.
* Se ha corregido un problema que mostraba errores no viables en el registro posterior de actualización cuando una actividad de flujo de trabajo **[!UICONTROL Survey answers]** no estaba completamente configurada.
* Teradata FDA: Se ha corregido un problema con campos autoincrementados e índices en tablas SQL.

### Versión 18.4.3, compilación 8935{#release-18-4-3-build-8935}

22 de junio de 2018

**Mejoras**

* Se ha corregido un problema en la codificación de seguimiento con Microsoft Edge e Internet Explorer. (NEO-11257)
* Se ha corregido un problema con la personalización de vínculos de imágenes en las entregas LINE. (NEO-11077)
* Se ha corregido un problema que impedía que el mecanismo de generación de secuencia de ID funcionara correctamente. (NEO-11115)
* Se ha corregido un problema que impedía que las solicitudes de privacidad (RGPD) funcionen al utilizar un área de nombres personalizada con una clave de reconciliación de tipo entero. (NEO-11123)
* Se ha corregido un error que se producía al utilizar la opción **[!UICONTROL Distribution of values]** en las actividades de flujo de trabajo **[!UICONTROL Query]**. (NEO-10958)
* Se ha corregido un problema que se producía al sincronizar los espacios de oferta de la instancia de marketing a la instancia de interacción. (NEO-11162)
* Se ha mejorado la administración de los índices de nombres largos posterior a la actualización

### Versión 18.4.2, compilación 8932{#release-18-4-2-build-8932}

22 de mayo de 2018

**Mejoras**

* Se ha corregido un problema que impedía que la actualización de Windows Server funcionara correctamente.
* Se ha corregido un problema en la actividad **[!UICONTROL Survey Result]** al utilizar datos almacenados en XML. El informe se mostraba incorrectamente. (NEO-10816)
* Se ha corregido un problema de rendimiento que podría ocurrir con el proceso de inMail al utilizar un servidor de correo de rebote. (NEO-10641)
* Se ha corregido un problema con la actualización de base de datos que se podría producir al actualizar más de 1000 esquemas.

### Versión 18.4.1, compilación 8931{#release-18-4-build-8931}

24 de abril de 2018

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
   <td> Reglamento General de Protección de Datos.<br /> </td> 
   <td> <p>El Reglamento General de Protección de Datos (RGPD) es la nueva normativa sobre privacidad de la Unión Europea que unifica y moderniza los requisitos de protección de datos y entrará en vigencia el 25 de mayo de 2018. El RGPD se aplica a los clientes de Adobe Campaign que albergan datos de sujetos de datos que residan en la UE.</p> <p>Además de las funcionalidades de privacidad disponibles en Adobe Campaign (incluida la administración de consentimiento, configuración de retención de datos y funciones de usuario), estamos tomando esta oportunidad en nuestro rol como procesador de datos para incluir funcionalidades adicionales, para ayudar a facilitar su preparación como controlador de datos para ciertas solicitudes de RGPD:</p> 
    <ul> 
     <li> <p>Derecho de acceso: permite que el sujeto de datos reciba una copia de sus datos personales capturados por los controladores de datos, incluso los datos almacenados en Adobe Campaign.</p> </li> 
     <li> <p>Derecho a eliminación: autoriza al sujeto de datos a que sus datos personales recopilados por los controladores de datos se borren, lo que incluye datos almacenados en Adobe Campaign.</p> </li> 
    </ul> Para obtener más información, consulte la <a href="https://helpx.adobe.com/es/campaign/kb/acc-privacy.html">documentación detallada</a>.<br /> </td> 
  </tr> 
  <tr> 
   <td> Perfiles activos<br /> </td> 
   <td> <p>Adobe Campaign ahora proporciona la lista de perfiles activos, actualizados mensualmente a través de un flujo de trabajo dedicado.</p> <p>Para obtener más información, consulte la <a href="../../platform/using/about-profiles.md#active-profiles">documentación detallada</a>.</p> </td> 
  </tr> 
  <tr> 
   <td> Mejora del conector de Android<br /> </td> 
   <td> <p>El conector Android se ha mejorado para ofrecer un mayor rendimiento. </p> <p>Para obtener más información, consulte la <a href="../../delivery/using/configuring-the-mobile-application.md">documentación detallada</a>.</p> </td> 
  </tr> 
 </tbody> 
</table>

**Mejoras de seguridad**

* La expansión de entidades externas está desactivada para evitar ataques potenciales de usuarios no autenticados. (NEO-10173)
* Se han endurecido los permisos para impedir que los usuarios estándar cambien los parámetros de configuración de la instancia, como URL de acceso a la aplicación, configuración de LDAP, etc. (NEO-10171)
* Se ha corregido un problema que pudiera revelar la información confidencial mediante los seguimientos de segmentación. Los detalles de error ahora se registran en el proceso de finalización a una ubicación inaccesible desde la red externa. (NEO-10176)
* Se han endurecido los permisos para impedir que los usuarios estándar vean los documentos cargados o paquetes exportados de un administrador. (NEO-10170)

**Mejoras**

* **Canal LINE: mejoras en la arquitectura**: Al igual que sucede con los demás canales de Adobe Campaign, el canal LINE ahora se admite en todos los tipos de implementación: alojada, híbrido y locales.
* **Generación automática de secuencias**: El mecanismo de generación de ID se ha mejorado para aumentar la duración de las instancias de Campaign con grandes cantidades de objetos.

**Otros cambios**

* Hay disponible un nuevo modo para la importación de paquetes mediante la línea de comandos, lo que permite dependencias circulares (no recomendado para paquetes grandes). Consulte la sección “Evoluciones técnicas” para obtener más información. (NEO-8979)
* Se mejoró el rendimiento para una gran cantidad de datos en Teradata y Se ha corregido un problema que impedía mostrar el valor correcto de datos procesados en el registro. (NEO-10429)
* La importación de audiencias desde el Gestor de colaboradores ahora funciona con archivos divididos. Anteriormente, el último archivo del segmento se importó mediante el flujo de trabajo técnico Importar audiencia compartida. (NEO-10156)
* En Windows, la ruta de instalación predeterminada del servidor Campaign ha cambiado. Al iniciar la configuración de la versión de 64 bits, la ruta de instalación predeterminada ahora es: **C:\Archivos de programa\Adobe\Adobe Campaign Classic v7** en lugar de **C:\Archivos de programa (x86)\Adobe\Adobe Campaign Classic v7**.
* Las reglas MX predeterminadas se han mejorado para incluir más dominios y optimizar el rendimiento.
* Restricciones de acceso mejoradas en la llamada SOAP del asistente de implementación (xtk:serverOptions#SaveOptions).
* La biblioteca obsoleta weka.jar se ha eliminado y la biblioteca OpenSSL se ha actualizado para la mejorar la seguridad.
* Se mejoró el flujo de trabajo técnico de facturación para asegurar la eficacia de las instancias.
* Se ha restaurado la capacidad para que los administradores definan o restablezcan la contraseña de cualquier operador. Para ello, haga clic con el botón derecho del ratón en un operador, seleccione **[!UICONTROL Actions]** >**[!UICONTROL Reset password]** y establezca la nueva contraseña del operador. Recomendamos que los operadores cambien su contraseña cuando vuelvan a conectarse por primera vez. Para obtener más información, consulte la [documentación detallada](../../production/using/lost-password.md).
* Para admitir la nueva función de inquilinos múltiples en Adobe Target, ahora se puede añadir un nuevo parámetro “at_property” a las URL al configurar opciones y cuentas externas para la integración con Target. El valor que se utiliza para este parámetro se puede encontrar en Adobe Target y se utilizará Campaign al realizar llamadas a Target. Para obtener más información, consulte la [documentación detallada](../../integrations/using/inserting-a-dynamic-image.md).
* Ahora puede especificar una página de aterrizaje predeterminada para abrirla al hacer clic en una imagen ofrecida por Adobe Target. Anteriormente, al hacer clic en la imagen principal el conjunto de imágenes predeterminado al crear el correo electrónico. Para obtener más información, consulte la [documentación detallada](../../integrations/using/inserting-a-dynamic-image.md).
* Se agregó la casilla de verificación **Habilitar los trazos** de niebla en la cuenta externa para forzar el seguimiento de la salida. Para obtener más información, consulte la [documentación detallada](../../delivery/using/sms-set-up.md#creating-an-smpp-external-account).

**Evoluciones técnicas**

queryDef

queryDef se ha modificado acerca de la cláusula “orderBy”. Antes del cambio, la clave principal de la tabla de consulta se agregaría implícitamente a las cláusulas “orderBy”. En algunos motores de base de datos (postgresql al menos), impide el uso de índices (todos los campos de la cláusula orderBy deben estar cubiertos por el mismo índice). Si queda pendiente de este comportamiento, tendrá que añadir explícitamente la clave principal en la cláusula “orderBy”.

Por ejemplo, si tiene la siguiente consulta:

```
<queryDef operation="select" schema="xtk:job" startPath="/" xtkschema="xtk:queryDef">
  <select>
     <node expr="@id"/>
   </select>
   <orderBy>
     <node expr="@logDate"/>
   </orderBy>
</queryDef>`
```

Se entregaría implícitamente como (antes de que 18.4 cambie):

```
<queryDef operation="select" schema="xtk:job" startPath="/" xtkschema="xtk:queryDef">
  <select>
     <node expr="@id"/>
   </select>
   <orderBy>
      <node expr="@logDate"/>
      <node expr="@id"/> <!-- implicitly added before 18.4, you can add it manually on your query, if you relied on this implicit order clauses --!>
   </orderBy>
</queryDef>
```

una función urlEncode

La función de JavaScript “urlEncode” no funcionaba correctamente para caracteres no ASCII. Se ha corregido y ahora debería funcionar con todos los caracteres Unicode (incluidos los caracteres japoneses). Si confía en el comportamiento “urlEncode” para el carácter no ASCII, tendrá que adaptar el código.

Empaquetar el nuevo modo de importación

Hay disponible un nuevo modo para la importación de paquetes mediante la línea de comandos, lo que permite dependencias circulares (no recomendado para paquetes grandes). Se mantiene la funcionalidad existente. Para estos paquetes con dependencias circulares, se ha añadido un nuevo indicador **-usejs** a la importación del paquete de la línea de comandos. Cuando se ejecuta, utilizará JSEngine como cuando se realiza la importación del paquete desde la interfaz.

```
nlserver package -instance:fresh -import:sup-packInstallTest.xml -verbose -usejs
```

**Parches**

* Se ha corregido un problema con la sincronización al replicar los registros de entrega y seguimiento de Adobe Campaign Standard a Adobe Campaign Classic. (NEO-10023)
* Se ha corregido un problema con el control de las tablas Error y Registro en Teradata cuando un flujo de trabajo de ETL se reanuda tras producirse un error en una operación de carga rápida. Las tablas de error y registro se han eliminado correctamente cada vez que se reanuda el flujo de trabajo. (NEO-10672)
* Se ha corregido un problema posterior a la actualización para instalar automáticamente el paquete Hive (necesario para Hadoop) si está instalado el paquete FDA. (NEO-10592)
* Se ha corregido un error que trataba los dominios no válidos como un error **no definido**. (NEO-10248)
* Se ha corregido un problema que duplicaba registros en la tabla deliveryLogStats al realizar entregas push de Android. (NEO-10234)
* Se ha corregido un problema que podría provocar que algunos formatos de código de barra no se puedan leer con escáneres de códigos de barra. (NEO-10125)
* Se ha corregido un problema con la función JavaScript “urlEncode” al utilizar caracteres no ASCII. Consulte la sección “Evoluciones técnicas” para obtener más información. (NEO-10123)
* Se ha corregido un problema que se producía al ejecutar una consulta que incluye funciones sha256 en bases de datos Teradata. (NEO-10119)
* Se corrigieron errores de memoria de flujo de trabajo que podrían producirse en la actividad de SalesForce al utilizar tablas SalesForce muy grandes. (NEO-9900)
* Se ha corregido un problema con la opción **Generar complemento** en las actividades de flujo de trabajo de destino al utilizar FDA. (NEO-9878)
* Se ha corregido un problema que podría provocar que las métricas **Procesado** y de **Éxito** no se actualicen en la instancia de marketing al utilizar intermediarios. (NEO-9454)
* Se corrigieron reglas de no reproposición de interacción cuando se acumulan más de 10 000 ofertas en total en la plataforma (NEO-9352)
* Se ha corregido un problema que podría evitar especificar el destino de una entrega al utilizar un archivo externo XML. (NEO-9312)
* Se ha corregido un problema que podría provocar errores de flujo de trabajo al ejecutar una hipótesis en una oferta y actualizar el estado de la propuesta. (NEO-9304)
* Se corrigieron errores que se producen durante el análisis de la entrega al utilizar reglas de presión basadas en un atributo de la asignación de entrega de Android. (NEO-9202)
* Se ha corregido un problema que se producía al ordenar columnas en la lista de destinatarios que podría provocar problemas de rendimiento. Para obtener más información sobre las modificaciones de queryDef, consulte la sección “Evoluciones técnicas” más abajo. (NEO-9042)
* Se ha corregido un problema en el cual los vínculos de un correo electrónico de aprobación podrían señalar a una URL de inicio de sesión incorrecta, especialmente cuando se utiliza un tipo de inicio de sesión de Federated ID. (NEO-9011)
* Se ha corregido un problema que podría provocar la visualización de fechas incorrectas en los selectores de fecha de los informes para ciertas zonas horarias. (NEO-9007)
* Se ha corregido un problema que impedía ver el destino de una salida cuando se utiliza una base de datos de SQL FDA. (NEO-8924)
* Se ha corregido un problema que provocaba que el conector de MS Dynamics CRM no logre extraer los datos durante los primeros 7 días del mes. (NEO-8803)
* Se ha corregido un error en la integración de Analytics que impedía a los usuarios incluir caracteres internacionales. (NEO-8719)
* Se ha corregido un problema que podría permitir la edición del flujo de trabajo sin los derechos adecuados. (NEO-8708)
* Se ha corregido un problema con FDA sobre direcciones HTTP cuando se utiliza el Centro de mensajes en una arquitectura híbrida, con el fin de establecer la conexión o pérdida de conexión (tiempo de espera). (NEO-8438)
* Se corrigieron los errores de flujo de trabajo que se producen en la actividad de consulta incremental para los ID negativos. (NEO-8229)
* Se ha corregido un problema que podría provocar la visualización de barras de desplazamiento doble en determinadas pantallas. (NEO-8208)
* Se ha corregido un problema que provocaba que se mostrara un mensaje de error al ejecutar el asistente de estructura de la base de datos de actualización. El componente PostUpgrade ejecutará un nombre de índices con nombres de más de 30. Tenga en cuenta que para tablas grandes, la sustitución de índices tardará un tiempo. (NEO-7983)
* Se ha corregido un problema que se producía cuando los registros de seguimiento no se sincronizaban correctamente a partir de la instancia de ejecución del Centro de mensajes para controlar la instancia. (NEO-7286)
* Se ha corregido un problema de rendimiento con la actividad de enriquecimiento de la oferta. (NEO-7263)
* Se ha corregido un problema que impedía utilizar la función DaysAgo al consultar la base de datos Redshift a través de FDA. (NEO-7099)
* Se ha corregido una regresión en la gestión de datos que impedía la creación de índices en actividades de flujo de trabajo de enriquecimiento.
* Se ha solucionado un problema que podría ocurrir al crear recursos externos con el título @id.
* Se ha corregido un problema que se podía producir al cargar archivos comprimidos a través de un servidor FTP o al cargar archivos con caracteres comodín en el nombre del archivo.
* Se ha corregido un problema con las enumeraciones de tipos base largas en los recursos personalizados externos creados en Campaign Standard.
* Se ha corregido un problema que podría provocar la entrega de SMS incluso cuando la conexión con el proveedor falla en las pérdidas de SMS.
* Se ha corregido un error que permite que la conexión SMTP se bloquee indefinidamente.
* Se ha corregido un problema con las reglas de tipología de presión durante la preparación del mensaje al utilizar una asignación LINE o cuando los esquemas de filtrado y segmentación son diferentes.
