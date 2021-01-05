---
solution: Campaign Classic
product: campaign
title: Versión 19.1
description: Versión 19.1
audience: rns
content-type: reference
topic-tags: latest-release-notes
translation-type: tm+mt
source-git-commit: 57093a687534ed1e7f77738ca233d4cc86cf40cf
workflow-type: tm+mt
source-wordcount: '3061'
ht-degree: 100%

---


# Versión 19.1{#release-19-1}

## ![](assets/do-not-localize/limited_2.png) Versión 19.1.8: compilación 9039 {#release-19-1-8-build-9039}

_16 de diciembre de 2020_

>[!CAUTION]
>
>Esta versión incorpora un nuevo protocolo de conexión: la actualización es obligatoria para que el servidor de Campaign y la consola del cliente puedan conectarse a Campaign después del 21 de marzo de 2021.

**Mejoras**

* El protocolo de conexión se ha actualizado para seguir el nuevo mecanismo de autenticación IMS.
* Activa la autenticación de integración basada originalmente en la configuración de autenticación oAUTH para acceder a la canalización, que se ha cambiado y se ha movido a Adobe I/O. [Más información](../../integrations/using/configuring-adobe-io.md)
* Después de finalizar la compatibilidad con el protocolo binario heredado de APN de iOS, todas las instancias que utilizan este protocolo se actualizan al protocolo HTTP/2 durante la postactualización.
* Se ha corregido un problema de seguridad para reforzar la protección contra los problemas de falsificación de solicitudes del lado del servidor (SSRF). (NEO-27777)



* Se ha corregido un problema que provocaba la desactivación del conector SMPP tras un error de conexión, lo que impedía otros envíos SMS y provocaba problemas de rendimiento.
* Se ha corregido un problema que mostraba porcentajes incorrectos al generar un informe descriptivo mediante una actividad de flujo de trabajo. (NEO-14314)
* Se ha corregido un problema con la preparación de la entrega cuando la opción **Exclude duplicate address during delivery** no está seleccionada. (NEO-13240)
* Se ha corregido un problema que podía provocar errores en los flujos de trabajo al ejecutar una actividad de **Enriquecimiento**. (NEO-17338)
* Se corrigió un problema de los flujos de trabajo al recuperar los registros de una base de datos externa e insertarlos en la base de datos de Campaign. (NEO-26359)



* Se ha corregido un problema de bloqueo del servidor al evitar la corrupción de memoria al limpiar el analizador de expresiones.
* Se ha corregido un problema que impedía que la función **NoNull** funcionara en las bases de datos de Oracle después de actualizar a la versión 9032. (NEO-26488)



* Se ha corregido un problema que, al editar una descripción de plantilla de campaña, impedía que se mostrara el botón **Guardar** al copiar y pegar símbolos como, por ejemplo, caracteres japoneses. (NEO-27071)



* Se ha corregido un problema que impedía guardar la descripción de una campaña o plantilla de campaña al hacer clic fuera de la ventana antes de hacer clic en el botón **Guardar**. (NEO-27449)



* Se ha corregido un problema al nivel de configuración proxy que impedía iniciar sesión en Adobe Campaign después de la última actualización de Windows 10. (NEO-27813)



* Se ha corregido un problema relacionado con la administración de líneas vacías en archivos de registro, que provocaba errores en el comportamiento del proceso de MTA y producía caídas de rendimiento en la realización de entregas.

**Evoluciones técnicas**

Tomcat se ha actualizado de la versión 7 (7.0.103) a la versión 8 (8.5.57). El directorio `tomcat-7` se reemplaza con un directorio `tomcat-8`. En Windows, _iis_neolane_setup.vbs_ y _apache_neolane.conf_ se instalan ahora en el directorio `conf` (en lugar de `tomcat-7/conf` anteriormente). En Linux, _apache_neolane.conf_ ahora está instalado en el directorio `conf`.

En Linux, el inicio del servicio nlserver ahora utiliza una unidad sistémica en lugar de la secuencia de comandos /etc/init.d/nlserver6. La migración al nuevo esquema de inicio se realiza automáticamente al instalar el paquete 19.1.8. Aún se proporciona el /etc/init.d/nlserver6; sin embargo, para interactuar con el servicio nlserver (inicio, reinicio, parada, etc.), se recomienda utilizar el comando systemctl directamente.

## ![](assets/do-not-localize/red_2.png) Versión 19.1.7: compilación 9036 {#release-19-1-7-build-9036}

_15 de septiembre de 2020_

**Mejoras**

* Se ha mejorado el uso de subprocesos de nlsrvmod para Apache 2.4 a fin de corregir los bloqueos de nlsrvmod.
* Se ha corregido un problema al usar la actividad Transferencia de archivos con una cuenta externa de Azure y un cifrado SSL. La conexión se ha realizado mediante HTTP en lugar de HTTPS. (NEO-26720)



* Se ha corregido un problema con el mecanismo de caché de la URL que no recuperaba la etiqueta o la categoría.
* Se ha corregido el problema que provocaba que las direcciones URL de página espejo se definieran incorrectamente en los envíos de correo electrónico (debido a un control incorrecto de caracteres ASCII). (NEO-26084)
* Se ha actualizado la lista jarsToSkip en catalina.properties para eliminar la referencia a un archivo jar que ya no se utilizaba (notificaciones de iOS).
* Se ha corregido un problema de regresión que impedía la publicación después de la actualización.
* Se ha corregido una regresión con los informes de envío listos para usar que aparecían truncados al exportarse a PDF. (NEO-25757)
* Se ha corregido el problema que eliminaba el valor del parámetro de codificación al redirigir desde una URL de seguimiento (impacto en los caracteres japoneses). (NEO-25637)
* Se ha corregido un problema que provocaba que los vínculos sin firmar de dominios personalizados se bloquearan cuando deberían permitirse. (NEO-25210)
* Se ha corregido la regresión que afectaba a los campos calculados de un flujo de trabajo y que provocaba un error. (NEO-25194)
* Se ha corregido un problema de compatibilidad con Microsoft Dynamics (de la versión 8.2) que podía impedir la ejecución de algunas llamadas API (RetrieveAllEntities). (NEO-24528)
* Se ha corregido un problema de regresión al utilizar la función del conector de ACS que impedía la conexión a una instancia de Campaign Standard (administración incorrecta de la conexión FOH/FOH2). (NEO-23433)
* Se ha corregido un problema de regresión en la conexión de la base de datos que provocaba que el servidor web se reiniciara constantemente debido a un problema de codificación de la base de datos. Esto podría causar un consumo excesivo. (NEO-23264)



* Se ha corregido un problema con el flujo de trabajo de limpieza de base de datos que podía fallar debido a una fuente de datos no administrada. (NEO-23160, NEO-23364)
* El flujo de trabajo de limpieza ahora purga las listas caducadas por lotes de a100 en lugar de a una por una.
* Después del cambio al [nuevo mecanismo de ID de secuencia](https://helpx.adobe.com/es/campaign/kb/sequence_auto_generation.html#Switchtoadedicatedsequence), todas las aplicaciones web que actualizan la tabla de destinatario se vuelven a publicar después de la actualización.
* Se ha corregido un problema que impedía enviar correos electrónicos cuando había código JavaScript fuera de la etiqueta de contenido HTML. (NEO-18628)
* Se ha corregido un problema que impedía que el flujo de trabajo de seguimiento actualizara los indicadores de seguimiento de mensajes transaccionales. (NEO-17770)
* Se ha mejorado el rendimiento del asistente de actualización de bases de datos a fin de hacer menos instrucciones SQL para optimizar el tiempo de respuesta.
* Se ha corregido un problema de bloqueo de la consola que se producía al desmarcar direcciones URL rastreadas en un correo electrónico, desde la ficha **Contenido de texto** debido a una variable no inicializada. (NEO-13545)
* Se ha corregido un problema que impedía cargar archivos en una actividad de Transferencia de archivos mediante una cuenta externa de almacenamiento de blob de Azure debido a una variable no inicializada (m_pCurlReader). (NEO-13717)



* Se ha corregido un problema después de la actualización que desactivaba Apache y el servidor web antes de la republicación de la aplicación web. (NEO-27155)



* Se ha corregido una regresión que provocaba la selección de una zona horaria incorrecta al establecer la hora en una actividad de flujo de trabajo de **Planificador**.

## ![](assets/do-not-localize/red_2.png) Versión 19.1.6: compilación 9035 {#release-19-1-6-build-9035}

>[!CAUTION]
>
>Esta compilación es únicamente para instalaciones in situ. Para implementaciones híbridas, las instancias alojadas siguen ejecutando la compilación 9032. No actualice la instancia de marketing a la compilación 9035, ya que no es compatible con 9032.

_3 de octubre de 2019_

**Mejoras**

* Se ha corregido un problema al usar el conector CRM para Salesforce. (NEO-17712)
* Se ha corregido un problema de índice que podía provocar problemas de rendimiento al enviar mensajes transaccionales.
* Se ha corregido un problema de rendimiento al enviar mensajes. (NEO-17558)
* Se ha corregido un problema que podía hacer que el servidor intermediario no procesara determinados mensajes. (NEO-12395)
* Se ha corregido un problema que impedía el uso completo de la actividad de Administración de datos SQL (faltaba la “Administración de datos SQL” denominada right).

## ![](assets/do-not-localize/red_2.png) Versión 19.1.5: compilación 9033{#release-19-1-5-build-9033}

_13 de agosto de 2019_

**Mejoras**

* Se ha corregido un problema con la sentencia SQL &#39;SELECT COUNT&#39; que se ejecutaba en la base de datos predeterminada en lugar de en la base de datos de FDA durante la extracción de datos en la actividad de gestión de datos.
* Ahora hay una declaración de proxy SFTP disponible en el archivo de configuración del servidor para mejorar las capacidades de la infraestructura del cliente.
* Se ha corregido un problema de bloqueo cuando el campo **Añadir tabla vinculada** está vacío en la actividad de flujo de trabajo **Carga de datos (RDBMS)**. (NEO-12213)
* Se ha corregido un problema con la instalación del paquete midEmitter a través de la línea de comandos.
* Se ha añadido una nueva opción de autenticación para admitir credenciales de OAuth dentro del conector AC con Microsoft Dynamics (NEO-11982)
* Se ha corregido un problema con la administración de UUID (identificador universal único) que provocaba que las actividades del flujo de trabajo de carga de datos y consulta fallaran con Hive FDA.
* Se ha corregido una regresión en Oracle que hacía que algunas funciones se consideraran no válidas después de la postactualización. (NEO-12759)



* Se ha corregido una regresión que provocaba la selección de una zona horaria incorrecta al establecer la hora en una actividad de flujo de trabajo de Planificador.

## ![](assets/do-not-localize/green_2.png) Versión 19.1.4: compilación 9032{#release-19-1-4-build-9032}

>[!NOTE]
>
>Las versiones de Gold Standard 19.1.4 se muestran en esta [página](../../rn/using/gold-standard.md).


## ![](assets/do-not-localize/red_2.png) Versión 19.1.2: compilación 9029{#release-19-1-2-build-9029}

_21 de junio de 2019_

**Mejoras de seguridad**

* La biblioteca Java (Netty) se ha actualizado a la última versión (4.1.34) para optimizar la seguridad. (NEO-12788)

**Mejoras**

* Se ha corregido una regresión relacionada con la gestión de columnas de dominio que impedía que se enviaran correos electrónicos con ciertas configuraciones.
* Para mejorar el rendimiento, se ha añadido un atributo _operation=&quot;none&quot; a las llamadas rtEvent SOAP para evitar solicitudes &quot;SELECCIONE PARA ACTUALIZAR&quot;.
* Se ha corregido un error de muestra de flujo de trabajo con transiciones de salida tras una Actividad de prueba. (NEO-12727)
* Ahora prohibimos la eliminación de los registros de prueba creados en Microsoft Dynamics durante el flujo de trabajo de importación.
* Se han mejorado los permisos para ejecutar el paquete de zona de seguridad cuando utilice una cuenta interna.

## ![](assets/do-not-localize/red_2.png) Versión 19.1: compilación 9026{#release-19-1-build-9026}

_30 de mayo de 2019_

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
   <td> Panel de control<br /> </td> 
   <td> <p>Para aumentar la eficacia en su trabajo como usuario administrador, gestione la configuración de sus servidores SFTP controlando el almacenamiento, añadiendo direcciones IP a listas de permitidos e instalando claves SSH para cada instancia. Tenga en cuenta que el Panel de control solo está disponible para los clientes alojados en AWS a partir de hoy (<a href="https://experiencecloud.adobe.com/campaign/controlpanel/">Inicie sesión hoy a través de Experience Cloud)</a>.</p> <p>Para obtener más información, consulte la <a href="https://docs.adobe.com/content/help/es-ES/control-panel/using/control-panel-home.html">documentación detallada</a> y el <a href="https://docs.adobe.com/content/help/es-ES/campaign-classic-learn/control-panel/control-panel-overview.html">videotutorial</a>. </p><p>Nota: no es necesario actualizar a la última compilación de Campaign para acceder al Panel de control.</p> </td> 
  </tr> 
    <tr> 
   <td> Pista de auditoría<br /> </td> 
   <td> <p>Como administrador, aumente la productividad controlando y gestionando los cambios realizados en la instancia de Adobe Campaign Classic. La pista de auditoría registrará las acciones realizadas en los esquemas de fuentes, flujos de trabajo y opciones. Puede ver rápidamente si un elemento se ha creado, modificado o eliminado.</p><p>Para obtener más información, consulte la <a href="../../production/using/audit-trail.md">documentación detallada</a> y el <a href="https://docs.adobe.com/content/help/es/campaign-classic-learn/tutorials/monitoring/audit-trail.html">videotutorial</a>.</p></td> 
  </tr> 
  <tr> 
   <td> Seguridad, solidez y escalabilidad<br /> </td> 
   <td> Se ha añadido una serie de mejoras a Campaign Classic. A continuación se enumeran las mejoras de seguridad, solidez y escalabilidad.<br /> </td> 
  </tr> 
  <tr> 
   <td> Actualización de la matriz de compatibilidades<br /> </td> 
   <td> Con esta nueva versión, Adobe Campaign admite los siguientes sistemas de bases de datos. Consulte la <a href="https://helpx.adobe.com/es/campaign/kb/compatibility-matrix.html">Matriz de compatibilidades</a>.<br /> 
    <ul> 
     <li> <p>Oracle 18c</p> </li> 
     <li> <p>MySQL 5.7 (FDA)</p> </li> 
     <li> <p>SQL Server 2017</p> </li> 
     <li> <p>Teradata 16 (FDA)</p> </li> 
     <li> <p>PostgreSQL 11</p> </li> 
    </ul> </td> 
  </tr> 
 </tbody> 
</table>

**Mejoras de seguridad**

* Por motivos de seguridad, ya no es posible insertar comandos arbitrarios al utilizar la **[!UICONTROL Pre-process the file]** opción en una **[!UICONTROL Data loading (file)]** actividad de flujo de trabajo. Ahora hay disponible una lista desplegable que le permite seleccionar entre tres opciones: **[!UICONTROL None]**, **[!UICONTROL Decompression]** (zcat) o **[!UICONTROL Decrypt]** (gpg). Se ha añadido el indicador de seguridad XtkSecurity_Disable_Preproc. Para clientes nuevos, esta opción se establece en 0. Para los clientes existentes, esta opción se establecerá en 1 después de la actualización para mantener el comportamiento previo. Consulte esta [sección](../../workflow/using/data-loading--file-.md).
* Se ha corregido un problema con la visibilidad de contraseña que se producía al probar la conexión de una cuenta externa de FDA sin un huso horario establecido.
* La biblioteca PDFBox se ha eliminado.
* Tomcat se ha actualizado a la versión 7.0.93.
* Se ha corregido un problema con la visibilidad del token que se producía cuando el token de seguridad no era válido.
* Se ha corregido un problema potencial de inyección de XTK en WSDL JSP (schemawsdl.jsp).
* Se ha optimizado el almacenamiento de credenciales y contraseñas en el código fuente y la memoria de la aplicación.
* Se ha optimizado la restricción de vista PII. (NEO-12339, NEO-12396, NEO-12398, NEO-12339, NEO-12667)
* Se corrigieron problemas de incoherencia en la administración de claves secretas.
* El mismo error genérico se muestra ahora para los intentos de inicio de sesión fallidos con un nombre de usuario válido o no válido.
* Se ha mejorado el nombre de los archivos cargados.
* Se ha añadido una nueva opción XtkSecurity_Disable_GetSetEnv para bloquear el uso de las funciones setEnv y getEnv.
* La información confidencial ahora está oculta en el seguimiento de pila de la aplicación.

**Mejoras de seguridad, solidez y escalabilidad**

* Duración: Optimización de uso de secuencia XtkNewId (las tablas más utilizadas se han movido de la secuencia de xtkNewId a secuencias dedicadas). [Más información](https://helpx.adobe.com/campaign/kb/sequence_auto_generation.html#Switchtoadedicatedsequence)
* FDA sobre HTTP v2: el protocolo FDA sobre HTTP se utiliza ampliamente en implementaciones híbridas, especialmente para la recuperación del registro general y la preparación de entregas. Se ha mejorado la solidez para evitar problemas de red y posibles errores al recuperar o extraer datos. Esto requiere que las compilaciones en ambos extremos de la conexión estén actualizadas; de lo contrario, se utilizará el protocolo antiguo.
* Flujo de trabajo de seguimiento: se ha mejorado la solidez del flujo de trabajo de seguimiento. Se han solucionado varios problemas relacionados con inserciones/actualizaciones del registro de seguimiento y la personalización del seguimiento de direcciones URL. Además, el flujo de trabajo de seguimiento ahora detecta el seguimiento de los problemas de registro que podrían provocar errores y detener el flujo de trabajo. Estos problemas ahora se descartan y no se procesan.
* Flujo de trabajo de limpieza: se ha mejorado el flujo de trabajo de limpieza para evitar posibles errores y detenciones. Esto optimiza el tamaño y el rendimiento de la base de datos.
* Imágenes incrustadas en mensajes transaccionales: hemos añadido la compatibilidad completa de las imágenes incrustadas en los mensajes transaccionales para evitar bloqueos o pérdidas de imágenes.
* Tamaño de base de datos: XtkJobLog (se ha añadido un mecanismo de depuración a esta tabla). Esto tiene un impacto positivo en el tamaño de la base de datos.
* Archivado BCC: los parámetros predeterminados para el archivado BCC se han cambiado para aumentar la velocidad de almacenamiento. [Más información](../../installation/using/email-archiving.md#parameters)
* Actualización de la estructura de la base de datos: las solicitudes de SQL generadas por el Asistente de actualización de la estructura de base de datos se han mejorado para que la ejecución sea más rápida.
* Seguridad para las acciones de operadores: se han implementado varias medidas de seguridad para evitar que los operadores realicen acciones que puedan afectar a la integridad de la plataforma. Los esquemas integrados ya no se pueden eliminar a través de la interfaz. Asimismo, los usuarios no administradores ya no pueden editar el XML de origen del flujo de trabajo.
* Existen dos nuevas opciones disponibles: **XtkSecurity_Restrict_EditXML** (permite desactivar la edición del código XML de las entregas) y **NmsOperation_OperationMgtDebug** (permite monitorizar la ejecución del flujo de trabajo técnico de operationMgt). [Más información](../../installation/using/configuring-campaign-options.md)

**Otros cambios**

* Notificaciones inmediatas: ahora se admite la opción de ID de vínculo para iOS push.
* Se ha mejorado la administración de los índices de nombres largos que podrían causar problemas después de la actualización.
* Ahora, durante el análisis de una entrega de eliminación, si el modo de publicación está configurado en **[!UICONTROL None]** en el asistente de implementación, se registra un error y se detiene el análisis: “El modo de publicación está configurado en &#39;ninguno&#39;: No se puede incrustar la imagen. Las imágenes no se mostrarán en el teléfono”. (NEO-12208)
* Se ha mejorado la administración del registro general para los mensajes transaccionales. Cuando se sincronizan los registros generales desde la instancia de ejecución a la instancia de control, el campo @lastModified se actualiza a la fecha actual del sistema. Se ha añadido la opción MC_Update_BlLastModified para instancias de control. “True” significa que la fecha actual se utilizará en la instancia de control (comportamiento predeterminado). “False” significa que usamos la fecha @lastModified de la instancia de ejecución del registro general. (NEO-12579)
* Los índices se agregaron en las tablas temporales del vale para optimizar las entregas. (NEO-12437)
* En la integración de Analytics, ahora se permite la recuperación de datos del segmento AAM con caracteres %. (NEO-12025)
* Se ha eliminado el límite de registro de 10 000 en Workflow Heatmap para solucionar un problema de ausencia de datos. (NEO-12329)
* Open Office no es compatible y ahora se ha eliminado completamente de la aplicación. Si todavía lo estaba utilizando, cambie a Libre Office ya que no funcionará a partir de la versión 19.1.
* Ahora puede limitar el acceso de escritura a la actividad de actualización de datos en el flujo de trabajo mediante atributos del filtro del sistema. [Más información](../../configuration/using/filtering-schemas.md)

**Parches**

* Se ha corregido un problema que impedía que se cargara el certificado para las notificaciones inmediatas de dispositivos móviles iOS.
* Se corrigieron bloqueos de servidor recurrentes potenciales para las notificaciones inmediatas transaccionales. Se han solucionado otros problemas de bloqueo.
* Se ha corregido un problema que ocasionaba discrepancias de informes entre las actividades del usuario y los informes de seguimiento para el indicador de entrega abierto. (NEO-11742)
* Se ha corregido un problema con el inicio de sesión de IMS.
* Se ha corregido un problema que podría provocar la ausencia de imágenes en una entrega al añadir una imagen de la biblioteca. (NEO-11900)
* Se ha corregido un problema que podría producirse al extraer detalles de oferta en una entrega de correo directo. (NEO-11700)
* Se ha corregido un problema que podría afectar el rendimiento del mensaje transaccional SMS. (NEO-9812)
* Se ha corregido un bloqueo de consola que podría producirse al utilizar la opción Definido en un archivo externo para el destino principal de una entrega. (NEO-12349)
* Se ha corregido un problema que se producía al analizar un mensaje segmentado para destinatarios para los dominios japoneses (.JP). (NEO-12246)
* Se ha corregido un problema con la visualización al utilizar una distribución de valores con un vínculo 1:N. (NEO-12212, NEO-11820)
* Se ha corregido un problema que podría provocar errores NmsMxDomain en los registros de MTA tras una actualización. (NEO-12752)
* Se ha corregido un problema que se producía al utilizar la opción “Conservar todos los datos adicionales del conjunto principal” en una actividad de flujo de trabajo de enriquecimiento. (NEO-13291)
* Se ha corregido un problema con el bloqueo de Tomcat al enviar notificaciones inmediatas con HTTP2. (NEO-12701)
* Se ha corregido un problema con la API HTTPRequest que no esperaba a que terminaran las retrollamadas. (NEO-12628)
* Se ha corregido un problema con el proceso de computación de los indicadores de seguimiento para los mensajes transaccionales. (NEO-12529)
* Se ha corregido un problema con el uso de temas en la administración de ofertas. (NEO-11804)
* Se ha corregido un problema de rendimiento al enviar notificaciones push. (NEO-11787)
* Se ha corregido un problema al previsualizar un archivo XML o CSV saliente en la administración de ofertas para una entrega de correo postal. (NEO-11290)
* Se ha corregido un problema al instalar el paquete de **Managing social networks** (Marketing social). (NEO-12081)
* Se ha corregido un problema que impedía eliminar una aplicación Web incluso si tenía los derechos de acceso correctos. (NEO-12072)
* Se ha corregido un problema que podría provocar que algunos valores se sobrescriban al exportar y luego importar un objeto a través de XML. Se ha añadido la opción XtkExport_IncludeDefaultValues. Cuando se establece en “True” (comportamiento predeterminado), se exportan todos los valores. Cuando se establece en “False”, las modificaciones se sobrescriben con el valor predeterminado. (NEO-11979)
* Se ha corregido un problema que hacía que la actividad del flujo de trabajo **[!UICONTROL Alert]** fallara cuando se añadía una actividad de enriquecimiento después de una consulta. (NEO-12132)
* Se ha corregido un problema en las configuraciones de Oracle en las que los desplazamientos de la canalización (desencadenante) no se recuperaban correctamente de la base de datos, provocando duplicados. (NEO-12121)
* Se ha corregido un problema que podría provocar errores de visualización en tablas dinámicas al utilizar la integración de Analytics (NEO-12103)
* Se ha corregido un problema con el informe de Análisis descriptivo. (NEO-11414)
* Se ha corregido un problema con los conectores de CRM cuando la tabla remota contenía un campo con un guion bajo en su nombre.
* Se solucionó un problema que podría causar un error de visualización para los símbolos de moneda en los informes de Hipótesis. (NEO-11634)
* Se ha corregido un problema con la redirección y el seguimiento al utilizar ciertos caracteres en los vínculos de seguimiento.
* Se ha corregido un problema que impedía que la previsualización de la oferta funcionara correctamente.
* Se ha corregido un problema en el que no se eliminaban los rebotes suaves de la tabla de direcciones.
* Se ha corregido un error de JAVA al utilizar códigos de barras.
* Se ha corregido un problema de traducción en aplicaciones web (NEO-12460)
* Se ha corregido un problema con la actividad de flujo de trabajo de transferencia de archivos s3. (NEO-12473)
* Se ha corregido un problema con los campos de fecha en las aplicaciones web. (NEO-12496)
* Se ha corregido un problema de agotamiento de ID al utilizar direcciones semilla en una entrega. (NEO-11842)
* Se ha corregido un problema con la compatibilidad con phantomjs y Debian 9.
* Se ha corregido un error al aprobar el contenido de una prueba. (NEO-12725)
* Se ha corregido un problema con la función de flujo de trabajo “Excluir este subconjunto de la población”. (NEO-12441)
* Se ha corregido un problema con la API HTTPRequest-wait que no esperaba que terminaran todas las retrollamadas. (NEO-12628)
* Se ha corregido un problema con la tarea “Actualizar audiencia compartida” en una actividad dividida. (NEO-11562)
* Se ha corregido un problema de bloqueo de servidor web. (NEO-12904)
* Se ha corregido un problema con el parámetro Natural en las plantillas transaccionales. (NEO-12334)
* Se ha corregido un problema con el bloqueo de la consola al mostrar las direcciones URL rastreadas en el editor de texto de correo electrónico. (NEO-13122)
* Se ha corregido un problema con la actividad de Archivo dividido al importar audiencias desde Audience Manager. (NEO-11550)
* Se ha corregido un problema que ocasionaba errores en el informe de clic activo. (NEO-11459)
* Se ha corregido un problema con el renderizado de ofertas. (NEO-11565)
* Se ha corregido un problema con la actividad de actualización de lista al importar audiencias desde Audience Manager. (NEO-11226)
* Se ha corregido un problema con la configuración de la actividad de programación y la zona horaria. (NEO-11662)
* Se ha corregido un error que hacía que el flujo de trabajo de seguimiento fallara en caso de direcciones URL mal escritas.
* Se ha corregido un problema con las cuentas externas después de importar el paquete de la aplicación móvil.
* Se ha corregido un problema que se producía al asignar una zona horaria a un operador. (NEO-12464)
* Se ha corregido un problema que podría provocar errores en los registros de mtachild. (NEO-11539, NEO-8978)
* Se ha corregido un problema que se producía al hacer clic en el icono Historial en un informe guardado. (NEO-11620)
* Se ha corregido un problema que se producía al editar una tabla dinámica en un informe. (NEO-12068)
