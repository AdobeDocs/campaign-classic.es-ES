---
title: Versión 19.1
seo-title: Versión 19.1
description: Versión 19.1
seo-description: null
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
source-git-commit: c1f5217fb45d2ffcb73ad4ec7d32ba6bd7ddbc15

---


# Versión 19.1{#release-19-1}

[Build upgrade](https://helpx.adobe.com/campaign/kb/acc-build-upgrade.html) | [Control Panel releases](https://docs.adobe.com/content/help/en/control-panel/using/release-notes.html) | [Documentation updates](../../rn/using/documentation-updates.md) | [Previous releases](../../rn/using/release--19-1.md) | [Deprecated features](https://helpx.adobe.com/campaign/kb/deprecated-and-removed-features.html)

<table> 
 <tbody> 
  <tr> 
   <td><img src="assets/green3.png"/><strong>Disponibilidad general</strong></td>
   <td><img src="assets/blue3.png"/><strong>Liberar candidato</strong></td> 
   <td><img src="assets/orange3.png"/><strong>Ya no está disponible</strong></td> 
   <td><img src="assets/red3.png"/><strong>Obsoleto</strong></td> 
  </tr> 
   <tr> 
   <td>Última compilación estable disponible. Compilación validada en producción.<br></td>
   <td>Compilación validada por Adobe. Esperando pruebas de producción.<br> </td>
   <td>Nueva compilación disponible con correcciones de errores. Se requiere la actualización.<br></td>
   <td>Contiene regresiones conocidas. La actualización es obligatoria.<br></td>
  </tr> 
 </tbody> 
</table>

La **última compilación** estable es 9032 (205c981c3). Click [here](../../rn/using/release--19-1.md#release-19-1-4-build-9032)

## ![](assets/orange_2.png) Versión 19.1.6: compilación 9035 {#release-19-1-6-build-9035}

>[!CAUTION]
>
>Esta compilación es únicamente para instalaciones in situ. Para implementaciones híbridas, las instancias alojadas siguen ejecutando la compilación 9032. No actualice la instancia de marketing a la compilación 9035, ya que no es compatible con 9032.

_3 de octubre de 2019_

**Mejoras**

* Se ha corregido un problema al usar el conector CRM para Salesforce. (NEO-17712)
* Se ha corregido un problema de índice que podía provocar problemas de rendimiento al enviar mensajes transaccionales.
* Se corrigió un problema de rendimiento al enviar mensajes. (NEO-17558)
* Se ha corregido un problema que podía hacer que el servidor intermediario no procesara determinados mensajes. (NEO-12395)
* Se ha corregido un problema que impedía el uso completo de la actividad de Administración de datos SQL (faltaba la “Administración de datos SQL” denominada right).

## ![](assets/orange_2.png) Versión 19.1.5: compilación 9033{#release-19-1-5-build-9033}

_13 de agosto de 2019_

**Mejoras**

* Se ha corregido un problema con la sentencia SQL &#39;SELECT COUNT&#39; que se ejecutaba en la base de datos predeterminada en lugar de en la base de datos de FDA durante la extracción de datos en la actividad de gestión de datos.
* Ahora hay una declaración de proxy SFTP disponible en el archivo de configuración del servidor para mejorar las capacidades de la infraestructura del cliente.
* Se ha corregido un fallo en Client console al “añadir una tabla vinculada” en la actividad de flujo de trabajo de carga de datos (RDBMS) sin nombre de tabla (NEO-12213)
* Se ha corregido un problema con la instalación del paquete midEmetter a través de la línea de comandos.
* Se ha añadido una nueva opción de autenticación para admitir credenciales de OAuth dentro del conector AC con Microsoft Dynamics (NEO-11982)
* Se ha corregido un problema con UUID (Unique Universal Identifier) que causaba que la actividad de enriquecimiento fallase con FDA de Hive.

## Versión 19.1.4: compilación 9032{#release-19-1-4-build-9032}

![](assets/green_2.png) 3 **de abril de 2020**: nueva compilación (9032-...e8b36257e) que incluye la siguiente corrección:

* Estamos introduciendo un mecanismo de firma para rastrear vínculos en correos electrónicos a fin de evitar el uso malintencionado potencial (phishing). Esto protege contra la reescritura de parámetros de seguimiento que pueden incluir una dirección URL utilizada para redirigir al usuario. Este mecanismo está actualmente deshabilitado de forma predeterminada. Póngase en contacto con el Servicio de atención al cliente si necesita activarlo.

* Se ha agregado una protección de seguridad complementaria para evitar la redirección de direcciones URL mal formadas generadas desde compilaciones anteriores o cuando el mecanismo de firma está desactivado. Póngase en contacto con el Servicio de atención al cliente si necesita utilizarlo.

![](assets/orange_2.png) 5 **de marzo de 2020**: nueva compilación (9032-...205c981c3) que incluye la siguiente corrección:

* Se ha corregido un problema con cuentas externas que usaban FTP sobre SSL. (NEO-20498)

![](assets/orange_2.png) 17 **de diciembre de 2019**: nueva compilación (9032-...9d34fb17e) que incluye la siguiente corrección:

* Se ha corregido un problema de seguimiento en los siguientes canales de comunicación: móvil (SMS, MMS), push (iOS, Android) y redes sociales (Facebook, Twitter).
(NEO-19595)

![](assets/orange_2.png) 11 **de diciembre de 2019**: nueva compilación (9032-...e28b428b7) que incluye la siguiente corrección:

* Se corrigió un problema de rendimiento al enviar mensajes con una base de datos MSSQL. (NEO-17558)

![](assets/orange_2.png) 20 **de noviembre de 2019**: nueva compilación (9032-...3468c7bb5) que incluye las siguientes correcciones:

* Se ha corregido un problema de inicio de sesión mediante la autenticación IMS. (NEO-17312)
* Se corrigió un problema al mostrar informes acumulativos en varias entregas. (NEO-18165)
* Se ha corregido un problema que podía bloquear o colapsar el servidor web.

![](assets/orange_2.png) 19 **de septiembre de 2019**: nueva compilación (9032-...cee805c93) que incluye las siguientes correcciones:

* Se ha corregido un problema al usar el conector CRM para Salesforce. (NEO-17712)
* Se ha corregido un problema de índice que podía provocar problemas de rendimiento al enviar mensajes transaccionales.

![](assets/orange_2.png) **13 de agosto de 2019**: compilación inicial 19.1.4 que incluye las siguientes correcciones:

* Se ha corregido un problema con la actividad del programador que generaba mensajes de error no deseados durante la configuración del asistente. Revertir la actualización desde NEO-11662. (NEO-17097)
* Se ha corregido una regresión causada por el NEO-12727 que hacía que los flujos de trabajo se detuvieran cuando se realizaba una actividad de prueba dos veces. (NEO-16835)
* Se ha corregido un problema que provocaba la devolución de un código HTTP erróneo (HTTP 200 OK en lugar de HTTP 403 Prohibido) cuando se utilizaba un token de sesión no válido o caducado en las llamadas a la API. (NEO-16826)
* Se ha solucionado un problema con la clave DKIM que ya no se incrustaba en los mensajes de correo electrónico, lo que provocaba problemas a la hora de realizar entregas. (NEO-16804)
* Se han corregido varios problemas con la programación de los flujos de trabajo. Los flujos de trabajo se programaban para ejecutarse una vez al día sin tener en cuenta la configuración del programador. (NEO-16619, NEO-16426)

## ![](assets/orange_2.png) Versión 19.1.2: compilación 9029{#release-19-1-2-build-9029}

_21 de junio de 2019_

**Mejoras de seguridad**

* La biblioteca Java (Netty) se ha actualizado a la última versión (4.1.34) para optimizar la seguridad. (NEO-12788)

**Mejoras**

* Se ha corregido una regresión relacionada con la gestión de columnas de dominio que impedía que se enviaran correos electrónicos con ciertas configuraciones.
* Para mejorar el rendimiento, se ha añadido un atributo _operation=&quot;none&quot; a las llamadas rtEvent SOAP para evitar solicitudes &quot;SELECCIONE PARA ACTUALIZAR&quot;.
* Se ha corregido un error de muestra de flujo de trabajo con transiciones de salida tras una Actividad de prueba. (NEO-12727)
* Ahora prohibimos la eliminación de los registros de prueba creados en Microsoft Dynamics durante el flujo de trabajo de importación.
* Se han mejorado los permisos para ejecutar el paquete de zona de seguridad cuando utilice una cuenta interna.

## ![](assets/orange_2.png) Versión 19.1: compilación 9026{#release-19-1-build-9026}

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
   <td> <p>Para aumentar la eficacia en su trabajo como usuario administrador, gestione la configuración de sus servidores SFTP controlando el almacenamiento, ubicando en la lista blanca las direcciones IP e instalando claves SSH para cada instancia. Tenga en cuenta que el Panel de control solo está disponible para los clientes alojados en AWS a partir de hoy (<a href="https://experiencecloud.adobe.com/campaign/controlpanel/">Inicie sesión hoy a través de Experience Cloud)</a>.</p> <p>Para obtener más información, consulte la <a href="https://docs.adobe.com/content/help/en/control-panel/using/control-panel-home.html">documentación detallada</a> y el <a href="https://docs.adobe.com/content/help/en/campaign-learn/campaign-classic-tutorials/administrating/control-panel-acc/control-panel-overview.html">videotutorial</a>. </p><p>Nota: no es necesario actualizar a la última compilación de Campaign para acceder al Panel de control.</p> </td> 
  </tr> 
    <tr> 
   <td> Pista de auditoría<br /> </td> 
   <td> <p>Como administrador, aumente la productividad controlando y gestionando los cambios realizados en la instancia de Adobe Campaign Classic. La pista de auditoría registrará las acciones realizadas en los esquemas de fuentes, flujos de trabajo y opciones. Puede ver rápidamente si un elemento se ha creado, modificado o eliminado.</p><p>Para obtener más información, consulte la <a href="../../production/using/audit-trail.md">documentación detallada</a> y el <a href="https://docs.adobe.com/content/help/en/campaign-learn/campaign-classic-tutorials/monitoring/audit-trail.html">videotutorial</a>.</p></td> 
  </tr> 
  <tr> 
   <td> Seguridad, solidez y escalabilidad<br /> </td> 
   <td> Se ha añadido una serie de mejoras a Campaign Classic. A continuación se enumeran las mejoras de seguridad, solidez y escalabilidad.<br /> </td> 
  </tr> 
  <tr> 
   <td> Actualización de la matriz de compatibilidades<br /> </td> 
   <td> Con esta nueva versión, Adobe Campaign admite los siguientes sistemas de bases de datos. Consulte la <a href="https://helpx.adobe.com/campaign/kb/compatibility-matrix.html">Matriz de compatibilidades</a>.<br /> 
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

* For security reasons, you can no longer insert arbitrary commands when using the **[!UICONTROL Pre-process the file]** option in a **[!UICONTROL Data loading (file)]** workflow activity. A drop-down list is now available allowing you to select from 3 options: **[!UICONTROL None]**, **[!UICONTROL Decompression]** (zcat) or **[!UICONTROL Decrypt]** (gpg). Se ha añadido el indicador de seguridad XtkSecurity_Disable_Preproc. Para clientes nuevos, esta opción se establece en 0. Para los clientes existentes, esta opción se establecerá en 1 después de la actualización para mantener el comportamiento previo. Consulte esta [sección](../../workflow/using/data-loading--file-.md).
* Se corrigió un problema con la visibilidad de contraseña que se producía al probar la conexión de una cuenta externa de FDA sin un huso horario establecido.
* La biblioteca PDFBox se ha eliminado.
* Tomcat se ha actualizado a la versión 7.0.93.
* Se corrigió un problema con la visibilidad del token que se producía cuando el token de seguridad no era válido.
* Se corrigió un problema potencial de inyección de XTK en WSDL JSP (schemawsdl.jsp).
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

* Se corrigió un problema que impedía que se cargara el certificado para las notificaciones inmediatas de dispositivos móviles iOS.
* Se corrigieron bloqueos de servidor recurrentes potenciales para las notificaciones inmediatas transaccionales. Se han solucionado otros problemas de bloqueo.
* Se corrigió un problema que ocasionaba discrepancias de informes entre las actividades del usuario y los informes de seguimiento para el indicador de entrega abierto. (NEO-11742)
* Se corrigió un problema con el inicio de sesión de IMS.
* Se corrigió un problema que podría provocar la ausencia de imágenes en una entrega al añadir una imagen de la biblioteca. (NEO-11900)
* Se corrigió un problema que podría producirse al extraer detalles de oferta en una entrega de correo directo. (NEO-11700)
* Se corrigió un problema que podría afectar el rendimiento del mensaje transaccional SMS. (NEO-9812)
* Se corrigió un bloqueo de consola que podría producirse al utilizar la opción Definido en un archivo externo para el destino principal de una entrega. (NEO-12349)
* Se corrigió un problema que se producía al analizar un mensaje segmentado para destinatarios para los dominios japoneses (.JP). (NEO-12246)
* Se corrigió un problema con la visualización al utilizar una distribución de valores con un vínculo 1:N. (NEO-12212, NEO-11820)
* Se corrigió un problema que podría provocar errores NmsMxDomain en los registros de MTA tras una actualización. (NEO-12752)
* Se corrigió un problema que se producía al utilizar la opción “Conservar todos los datos adicionales del conjunto principal” en una actividad de flujo de trabajo de enriquecimiento. (NEO-13291)
* Se corrigió un problema con el bloqueo de Tomcat al enviar notificaciones inmediatas con HTTP2. (NEO-12701)
* Se corrigió un problema con la API HTTPRequest que no esperaba a que terminaran las retrollamadas. (NEO-12628)
* Se corrigió un problema con el proceso de computación de los indicadores de seguimiento para los mensajes transaccionales. (NEO-12529)
* Se corrigió un problema con el uso de temas en la administración de ofertas. (NEO-11804)
* Se corrigió un problema de rendimiento al enviar notificaciones push. (NEO-11787)
* Se corrigió un problema al previsualizar un archivo XML o CSV saliente en la administración de ofertas para una entrega de correo postal. (NEO-11290)
* Se corrigió un problema al instalar el paquete de **Managing social networks** (Marketing social). (NEO-12081)
* Se corrigió un problema que impedía eliminar una aplicación Web incluso si tenía los derechos de acceso correctos. (NEO-12072)
* Se corrigió un problema que podría provocar que algunos valores se sobrescriban al exportar y luego importar un objeto a través de XML. Se ha añadido la opción XtkExport_IncludeDefaultValues. Cuando se establece en “True” (comportamiento predeterminado), se exportan todos los valores. Cuando se establece en “False”, las modificaciones se sobrescriben con el valor predeterminado. (NEO-11979)
* Se ha corregido un problema que hacía que la actividad del flujo de trabajo **[!UICONTROL Alert]** fallara cuando se añadía una actividad de enriquecimiento después de una consulta. (NEO-12132)
* Se corrigió un problema en las configuraciones de Oracle en las que los desplazamientos de la canalización (desencadenante) no se recuperaban correctamente de la base de datos, provocando duplicados. (NEO-12121)
* Se corrigió un problema que podría provocar errores de visualización en tablas dinámicas al utilizar la integración de Analytics (NEO-12103)
* Se corrigió un problema con el informe de Análisis descriptivo. (NEO-11414)
* Se corrigió un problema con los conectores de CRM cuando la tabla remota contenía un campo con un guion bajo en su nombre.
* Se solucionó un problema que podría causar un error de visualización para los símbolos de moneda en los informes de Hipótesis. (NEO-11634)
* Se corrigió un problema con la redirección y el seguimiento al utilizar ciertos caracteres en los vínculos de seguimiento.
* Se corrigió un problema que impedía que la previsualización de la oferta funcionara correctamente.
* Se corrigió un problema en el que no se eliminaban los rebotes suaves de la tabla de direcciones.
* Se corrigió un error de JAVA al utilizar códigos de barras.
* Se corrigió un problema de traducción en aplicaciones web (NEO-12460)
* Se corrigió un problema con la actividad de flujo de trabajo de transferencia de archivos s3. (NEO-12473)
* Se corrigió un problema con los campos de fecha en las aplicaciones web. (NEO-12496)
* Se corrigió un problema de agotamiento de ID al utilizar direcciones semilla en una entrega. (NEO-11842)
* Se corrigió un problema con la compatibilidad con phantomjs y Debian 9.
* Se corrigió un error al aprobar el contenido de una prueba. (NEO-12725)
* Se corrigió un problema con la función de flujo de trabajo “Excluir este subconjunto de la población”. (NEO-12441)
* Se corrigió un problema con la API HTTPRequest-wait que no esperaba que terminaran todas las retrollamadas. (NEO-12628)
* Se corrigió un problema con la tarea “Actualizar audiencia compartida” en una actividad dividida. (NEO-11562)
* Se ha corregido un problema de bloqueo de servidor web. (NEO-12904)
* Se corrigió un problema con el parámetro Natural en las plantillas transaccionales. (NEO-12334)
* Se corrigió un problema con el bloqueo de la consola al mostrar las direcciones URL rastreadas en el editor de texto de correo electrónico. (NEO-13122)
* Se corrigió un problema con la actividad de Archivo dividido al importar audiencias desde Audience Manager. (NEO-11550)
* Se corrigió un problema que ocasionaba errores en el informe de clic activo. (NEO-11459)
* Se corrigió un problema con el renderizado de ofertas. (NEO-11565)
* Se corrigió un problema con la actividad de actualización de lista al importar audiencias desde Audience Manager. (NEO-11226)
* Se corrigió un problema con la configuración de la actividad de programación y la zona horaria. (NEO-11662)
* Se corrigió un error que hacía que el flujo de trabajo de seguimiento fallara en caso de direcciones URL mal escritas.
* Se corrigió un problema con las cuentas externas después de importar el paquete de la aplicación móvil.
* Se corrigió un problema que se producía al asignar una zona horaria a un operador. (NEO-12464)
* Se corrigió un problema que podría provocar errores en los registros de mtachild. (NEO-11539, NEO-8978)
* Se corrigió un problema que se producía al hacer clic en el icono Historial en un informe guardado. (NEO-11620)
* Se corrigió un problema que se producía al editar una tabla dinámica en un informe. (NEO-12068)
