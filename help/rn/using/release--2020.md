---
product: campaign
title: Versiones de 2020
description: Más información sobre las actualizaciones de Campaign Classic 2020
feature: Overview
role: User
level: Beginner
exl-id: e2eb7e04-faaa-4df0-913d-471c291eeb03
source-git-commit: 0f31ee570ba6e763f48902e91c5d823ac297fc24
workflow-type: tm+mt
source-wordcount: '6569'
ht-degree: 94%

---

# Versiones de 2020{#release-2020}

![](../../assets/v7-only.svg)


## Versión 20.3{#release-20-3}

### ![](assets/do-not-localize/red_2.png) Versión 20.3.3, compilación 9234 {#release-20-3-3-build-9234}

_11 de enero de 2021_

* Se ha corregido un problema de seguridad para reforzar la protección contra los problemas de falsificación de solicitudes del lado del servidor (SSRF). (NEO-27777)



* Se ha corregido un problema de regresión relacionado con el proceso de generación de registros de banda ancha que podía provocar el bloqueo del proceso de MTA.

### ![](assets/do-not-localize/red_2.png) Versión 20.3.1, compilación 9228 {#release-20-3-1-build-9228}

_27 de octubre de 2020_

>[!CAUTION]
>
> * Esta versión incorpora un nuevo protocolo de conexión: si se conecta a Campaign a través del Servicio de identidad de Adobe (IMS), la actualización es obligatoria tanto para el servidor de Campaign como para la consola cliente para poder conectarse a Campaign después del **30 de junio de 2021**. [Más información](../../technotes/using/ims-updates.md)
> * Esta versión incluye una [corrección de seguridad](https://helpx.adobe.com/es/security/products/campaign/apsb21-04.html): la actualización es obligatoria para reforzar la seguridad de su entorno.
> * Si está utilizando la integración de Experience Cloud Triggers mediante autenticación oAuth, debe ir a Adobe I/O como se detalla [en esta página](../../integrations/using/configuring-adobe-io.md). El modo de autenticación de oAuth heredado con Campaign [se ha eliminado](https://experienceleaguecommunities.adobe.com/t5/adobe-analytics-discussions/adobe-analytics-legacy-api-end-of-life-notice/td-p/385411?profile.language=es) en **septiembre de 2021**. Los entornos alojados se benefician de una extensión hasta  **23 de febrero de 2022**. Como cliente local o híbrido, póngase en contacto con el servicio de atención al cliente de Adobe para ampliar la asistencia hasta febrero de 2022. Debe proporcionar [el AppID de la aplicación OAuth](../../integrations/using/configuring-pipeline.md?lang=en#step-optional) a Adobe.


**Novedades**

<table> 
<thead>
<tr> 
<th> <strong>Mejoras de notificaciones push en iOS</strong><br /> </th> 
</tr> 
</thead> 
<tbody> 
<tr> 
<td> <p>Al integrar su aplicación móvil con Campaign, debe asegurar su comunicación con el servicio de notificaciones push de Apple (APNS). Puede utilizar la autenticación basada en certificados o en token.
</p>
<p>Estos dos modos de autenticación ya están disponibles para las aplicaciones móviles de iOS en Campaign Classic:
</p>
<ul> 
<li><p>Autenticación basada en token (recomendada): este modo de autenticación se basa en un archivo .p8. Este modo de autenticación es más rápido, ya que cada solicitud a APN contiene el token. <a href="https://developer.apple.com/documentation/usernotifications/setting_up_a_remote_notification_server/establishing_a_token-based_connection_to_apns">Más información</a></p></li>
<li><p>Autenticación basada en certificado: este modo de autenticación se basa en un archivo .p12. Se requiere un certificado independiente para cada aplicación. Apple entrega este certificado con su cuenta de desarrollador. <a href="https://developer.apple.com/documentation/usernotifications/setting_up_a_remote_notification_server/establishing_a_certificate-based_connection_to_apns">Más información</a></p></li> 
</ul>
<p>Obtenga información sobre cómo seleccionar el modo de autenticación en Campaign en la <a href="../../delivery/using/configuring-the-mobile-application.md">documentación detallada</a>.</p>
</td> 
</tr> 
</tbody> 
</table>

<table> 
<thead>
<tr> 
<th> <strong>Mejoras de notificaciones push de Android</strong><br /> </th> 
</tr> 
</thead> 
<tbody> 
<tr> 
<td> <p><a href="../../delivery/using/configuring-the-mobile-application-android.md#creating-notification-message">Se han mejorado las notificaciones push de Android para admitir la API HTTP v1 de FCM para la autenticación del canal push de Android.</a> </p>
<p>Con la nueva versión de API admitida, ahora puede enviar mensajes de notificación de FCM, que proporcionan funcionalidades de mensajería push enriquecidas y mejoradas. <a href="https://firebase.google.com/docs/cloud-messaging/migrate-v1">Más información</a></p> 
<p>Aprenda a configurar la API HTTP v1 de FCM para Android en Adobe Campaign en <a href="../../delivery/using/configuring-the-mobile-application-android.md">esta sección</a>.</p>
</td> 
</tr> 
</tbody> 
</table>

**Mejoras de seguridad**

* Carga segura de bibliotecas: para protegerse de los ataques de precarga de DLL, Campaign ahora carga las DLL de Windows únicamente desde la ruta de acceso predeterminada de la DLL del sistema de Windows al cargar el cliente de Campaign (nlclient). [Más información](https://support.microsoft.com/en-us/help/2389418/secure-loading-of-libraries-to-prevent-dll-preloading-attacks) (NEO-24147)
* Se ha corregido un problema de seguridad para reforzar la protección contra los ataques de falsificación de solicitudes del lado del servidor (SSRF). (NEO-25661)



* Se ha corregido un problema que se producía al administrar las solicitudes de privacidad de RGPD que impedía que se eliminaran registros de tablas personalizadas con una relación de segundo nivel con la tabla de Destinatario. (NEO-25967)



* Se ha corregido un problema de seguridad que se producía al intentar sincronizar plantillas de Adobe Experience Manager mediante llamadas API realizadas por usuarios no administradores. (NEO-23487)




**Actualizaciones de compatibilidad**

Ahora se admiten los siguientes sistemas con Campaign:
* iOS14
* PostgreSQL 12
* CentOS/RedHat 8
* MSSQL2019

Obtenga más información en la [Matriz de compatibilidad de Campaign](../../rn/using/compatibility-matrix.md).

**Funciones obsoletas**

Las siguientes funciones están en desuso en 20.3:

* El dominio demdex utilizado para importar y exportar audiencias a Adobe Experience Cloud está en desuso. Si utiliza el dominio demdex para sus cuentas externas de importación y exportación, deberá adaptar la implementación en consecuencia. [Más información](../../integrations/using/configuring-shared-audiences-integration-in-adobe-campaign.md)
* Activa la autenticación de integración basada originalmente en la configuración de autenticación oAUTH para acceder a la canalización y ahora se ha cambiado y se ha movido a Adobe I/O. [Más información](../../integrations/using/configuring-adobe-io.md)

Obtenga más información en la página [Funciones obsoletas y eliminadas](../../rn/using/deprecated-features.md).

**Mejoras**

* Se han realizado varias mejoras en la **consola de Cliente**:
   * El protocolo de conexión se ha actualizado para seguir el nuevo mecanismo de autenticación IMS. La actualización de la consola del servidor y del cliente es obligatoria para poder conectarse después del 30 de junio de 2021.
   * Para evitar incompatibilidades con algunas restricciones de las reglas GPO de seguridad de internet, la pantalla de inicio de sesión de la consola de cliente de Campaign se ha sustituido por un formulario estándar integrado de Windows.
   * Se ha corregido un problema que se producía al copiar/pegar actividades en un flujo de trabajo con la consola de cliente de 64 bits. (NEO-27635)



   * En el menú **Acerca**, se ha añadido información para distinguir las consolas de 64 y 32 bits.
* El identificador de flujo de trabajo ahora se muestra en los registros al reanudar un flujo de trabajo, lo que le permite identificar mejor qué flujo de trabajo se ha reanudado.
* Se ha introducido una nueva cookie permanente: nllastdelid. Esta cookie (que no sea UUID230) almacenará deliveryId. Cuando la cookie de sesión no está presente, la información del broadlog se tomaría de deliveryId presente en esta cookie.
Este cambio corrige un problema que se producía al finalizar la sesión del explorador: se eliminó la cookie de sesión que contenía deliveryId y broadlogId. Sin deliveryId, no se pudo encontrar la información de broadlog y faltaría la información de la tabla de seguimiento en caso de un seguimiento permanente (último envío).
Obtenga más información sobre las cookies en [esta sección](../../platform/using/privacy-and-recommendations.md#cookies).
* Se mejoró el rendimiento de la producción del envío de gran volumen con el servidor de entrega al reiniciar el proceso de MTA antes de los envíos.

**Otros cambios**

* Cuando se utiliza la ruta relativa para SFTP, ya no se agregan los caracteres `~/` automáticamente. Si es necesario, puede agregar los caracteres `~/` a la ruta manualmente, pero Adobe recomienda utilizar una **ruta absoluta**.
* La autenticación de Windows NT se ha eliminado de los métodos de autenticación disponibles al configurar una nueva base de datos con Microsoft SQL Server. [Más información](../../installation/using/creating-and-configuring-the-database.md#step-1---selecting-the-database-engine)
* El flujo de trabajo para limpieza de la base de datos se ha optimizado para Teradata a fin de mejorar el rendimiento. (NEO-19959)



* Se mejoró el mensaje de error que se mostraba al insertar una imagen de Adobe Target y el nombre del inquilino estaba vacío en la cuenta externa.
* En las propiedades de envío, se ha cambiado el nombre de la opción **[!UICONTROL Archive emails]** a **[!UICONTROL Email BCC]**.
* Para mejorar la solidez, las consultas selectAll con nodos no válidos ahora se rechazan. Si necesita deshabilitar la comprobación y volver al comportamiento anterior, puede establecer XtkSecurity_Disable_QueryCheck en 0.

**Evoluciones técnicas**

Tomcat se ha actualizado de la versión 7 (7.0.103) a la versión 8 (8.5.57).

El directorio `tomcat-7` se reemplaza con un directorio `tomcat-8`.

En Windows, _iis_neolane_setup.vbs_ y _apache_neolane.conf_ se instalan ahora en el directorio `conf` (en lugar de `tomcat-7/conf` anteriormente).

En Linux, _apache_neolane.conf_ ahora está instalado en el directorio `conf`.

**Parches**

* Se ha corregido un problema que podía impedir que las estadísticas de envío se volvieran a calcular.
* Se ha corregido un problema que mostraba un mensaje de error al cargar un archivo CSV con la versión 9080 de Campaign Classic conectada a un servidor con una versión anterior. (NEO-23218)



* Se ha corregido un problema que podía mostrar un mensaje de error al configurar el asistente de Microsoft Dynamics CRM para una cuenta externa. Esto se debió a un problema de compatibilidad con la última versión de la API de MS Dynamics CRM. (NEO-24528)
* Se ha corregido un problema que impedía exportar los registros de tipo de búsqueda (es decir, datos de registros de claves externas conectados con otras tablas) de Campaign Classic a Microsoft Dynamics mediante el conector CRM. (NEO-23864)



* Se ha corregido un problema que podía impedir que se recuperaran datos de Microsoft Dynamics si la opción de **índice automático** estaba activada en el conector CRM. (NEO-25981)



* Se ha corregido un problema con la autenticación IMS que podía dejar las conexiones abiertas incluso si habían finalizado. Las conexiones terminadas ahora se cierran automáticamente en cuanto finalizan para evitar la acumulación de conexiones y el consumo de recursos del sistema. (NEO-25996)



* Se ha corregido un problema que no mostraba ningún mensaje de error cuando se producía un error en un envío en la sincronización del contenido de Adobe Experience Manager debido a una configuración incorrecta de la cuenta externa (cuenta o contraseña incorrectas). Ahora aparece un mensaje en caso de error, que le permite identificar el problema con mayor facilidad. (NEO-25586)



* Se ha corregido un problema que se producía al seleccionar el tipo de operación **Actualizar** en la actividad **Actualizar datos**. Si los datos que se van a actualizar son incorrectos, el flujo de trabajo da error. En caso de datos incorrectos, el flujo de trabajo no da error y los registros se almacenan en la transición de salida **Rechazados**. (NEO-23794)



* Se ha corregido un problema que podía impedir que funcionaran los flujos de trabajo que contenían subflujos de trabajo. (NEO-24036)



* Se ha corregido un problema que, al editar una descripción de plantilla de campaña, impedía que se mostrara el botón **Guardar** al copiar y pegar símbolos como, por ejemplo, caracteres japoneses. (NEO-27071)



* Se ha corregido un problema que podía impedir que se cambiara el servidor de seguimiento en el asistente de configuración de instancias.
* Se ha corregido un problema que impedía guardar la descripción de una campaña o plantilla de campaña al hacer clic fuera de la ventana antes de hacer clic en el botón **Guardar**. (NEO-27449)



* Se ha corregido un problema que podía impedir que funcionara el flujo de trabajo técnico **Número de perfiles de facturación activos** (billingActiveContactCount). Esto podría suceder si se hubiera realizado un vínculo en un campo calculado en una extensión de esquema. Se creó una gran cantidad de datos, lo que podría hacer que la base de datos se quedara sin espacio temporal. (NEO-24062)



* Se ha corregido un problema con la actividad de **carga de datos (archivo)** que podía impedir la importación de caracteres japoneses de archivos .txt y .csv si se colocaban al final del archivo. (NEO-24957)



* Se ha corregido un problema de los envíos continuos que podía impedir que los campos **Análisis iniciada** y **Análisis finalizada** se rellenaran correctamente. (NEO-20755)



* Se ha corregido un problema que podía mostrar un mensaje de error al intentar previsualizar los mensajes SMS después de una consulta en otro esquema que no fuera **Destinatario** (nms:destinatario). (NEO-27517)



* Se ha corregido un problema al usar el conector de FDA de Snowflake. Un usuario con derechos asignados de acceso a FDA Snowflake no pudo ejecutar una consulta en un esquema de Snowflake. En los registros se mostraba un error de tipo “No se encontró la contraseña”. (NEO-23851)



* Se ha corregido un problema que se producía al usar un conector de FDA cuando el nombre del esquema de FDA vinculado era una subcadena del nombre de un elemento del esquema actual. Esto ocurría, por ejemplo, si el esquema de FDA era “cust” y uno de los elementos dentro del esquema de Destinatario era “customer”. Al recuperar la columna dentro del elemento “cliente” y agregar una columna desde el esquema de FDA “cust”, faltaba el valor de la columna local. (NEO-20193)



* Se corrigió un problema de los flujos de trabajo al recuperar los registros de una base de datos externa e insertarlos en la base de datos de Campaign. (NEO-26359)



* Se ha corregido un problema en el flujo de trabajo técnico de **Actualización de estado del evento**: para que coincidiera con el tamaño de los campos correspondientes entrantes en la actividad de **estadísticas de Envío**, el tamaño de los tres campos de destino en la actividad **Actualización de estadísticas de envío** cambió de 32 a 64 bits. (NEO-11557) Obtenga más información sobre el flujo de trabajo de **Actualización de estado del evento** en [esta sección](../../workflow/using/about-technical-workflows.md).
* Se ha corregido un problema en el informe **Historial de Eventos del centro de mensajes** que provocaba errores de secuencia de comandos al intentar aplicar filtros y hacía imposible el filtro por un intervalo de fechas. (NEO-23365)



* Se ha corregido un problema de interferencia entre los flujos de trabajo técnicos **de Campaign** (operationMgt) y de **Previsualización** (pronóstico). Esto ocurría cuando los envíos programados permanecían en el estado “Listo para Destinatario” o “Listo para entregar”. (NEO-20819)



* Se corrigió un problema con el análisis de XML cuando el identificador XML no estaba presente en el campo mdata en xtkOperator. Causaba un error después de la actualización. (NEO-26113)



* Se ha corregido un problema que se producía al usar la actividad de **transferencia de archivos** vinculada a una cuenta externa de Azure cifrada en SSL, donde la conexión se realizaba con HTTP en lugar de HTTPS. (NEO-26720)



* Se corrigió un problema en la base de datos MSSQL en el cual se podía producir un error con el procedimiento up_updatestats durante el flujo de trabajo de limpieza.
* Se corrigió un bloqueo que se producía durante el cierre del proceso web si las solicitudes de interacción aún se estaban procesando. (NEO-26447)



* Se corrigió un problema en el cual la función **NoNull** en Oracle DB ya no funcionaba después de la actualización 9032. (NEO-26488)



* Se corrigió un problema en el cual el flujo de trabajo de seguimiento fallaba después de la actualización 9171 si el paquete LINEV2 se instalaba sin el paquete de Message Center.
* Se ha corregido un problema de escalabilidad que impedía que el grupo de conexiones aumentara al número deseado de conexiones porque la cadena de conexión de base de datos del atributo “APP” acababa obteniendo un valor no válido. (NEO-25105)



* Se ha corregido un problema al nivel de configuración proxy que impedía iniciar sesión en Adobe Campaign después de la última actualización de Windows 10. (NEO-27813)



* Se ha corregido un problema que hacía que las direcciones URL no deseadas estuvieran visibles en los correos electrónicos enviados después de importar las plantillas HTML con vínculos de seguimiento. (NEO-25909)



* Se corrigió un problema que ocasionaba que el servidor se bloqueara al mostrar los datos de destinatario del resto desde una actividad **dividida** en un flujo de trabajo.
* Se ha corregido un problema de bloqueo del servidor al evitar la corrupción de memoria al limpiar el analizador de expresiones. (NEO-26856)



* Se corrigió un problema en la actividad de enriquecimiento en el cual los usuarios no administradores definían variables de instancia. (NEO-25653)



* Se ha corregido una regresión que podía bloquear la exportación de datos de flujo de trabajo a una base de datos FDA (Teradata, Snowflake).

## Versión 20.2{#release-20-2}

### ![](assets/do-not-localize/limited_2.png) Versión 20.2.5, compilación 9188 {#release-20-2-5-build-9188}

_15 de abril de 2021_

* Se ha corregido una regresión de la consola del cliente que provocaba mensajes de error persistentes en la pantalla de conexión IMS. (NEO-34821)

**Solo es obligatorio actualizar la consola. No se requiere ninguna actualización del servidor.**

>[!NOTE]
>
> Conéctese a [Adobe Software Distribution](https://experience.adobe.com/#/downloads/content/software-distribution/es/campaign.html) para descargar la nueva versión. Aprenda a proponer la actualización de la consola a todos los usuarios finales [en esta página](../../installation/using/client-console-availability-for-windows.md).

_31 de marzo de 2021_

**Mejoras**

* Se ha realizado una mejora para evitar bloqueos en llamadas de jabón no válidas. Esto podría hacer que la instancia deje de funcionar al intentar ejecutar consultas complejas específicas. (NEO-28796, NEO-30553)
* Se ha corregido una regresión que impedía que se enviaran envíos SMS con TLS debido a la verificación del nombre de host. (NEO-29581)
* Se ha corregido un problema que impedía que los vínculos de seguimiento firmados funcionaran en algunos clientes de correo electrónico. (NEO-28414, NEO-29615)
* Se ha corregido una secuencia de id de seguimiento al usar etiquetas de seguimiento de webApp que podía provocar conflictos con ID duplicados. (NEO-27931)
* Se ha corregido un problema que provocaba que el reinicio diario del servidor wfserver detuviera los flujos de trabajo en ejecución. (NEO-30047)
* Se ha corregido un problema de seguridad que se producía al intentar sincronizar plantillas de Adobe Experience Manager mediante llamadas API realizadas por usuarios no administradores. (NEO-32389, NEO-23487)
* Se ha corregido un problema que hacía que la consola se bloqueara al cerrar un cuadro de diálogo de envío en una entrega creada con a partir de una plantilla. (NEO-31547)
* Se ha corregido un problema que se producía al crear y guardar una entrega dentro de la función **Segmentación y flujo de trabajo** de una campaña: la vista previa fallaría con el siguiente error. (NEO-29440)
* Se ha corregido un problema por el que Tomcat 8.5 enviaba respuestas no válidas que causaban errores en los registros de mensajería transaccional. (NEO-30858)
* Se ha corregido un problema de regresión que provocaba daños en la memoria en la administración de subprocesos externos e impactaba en el rendimiento.
* Se ha corregido un problema que podría provocar que el flujo de trabajo de facturación falle al usar una asignación de destino personalizada. La clave principal del esquema personalizado se almacena en la columna &quot;sourceId&quot;, que solo permitía valores enteros. Ahora permite valores enteros y de cadena. (NEO-25914, NEO-28146)
* Se ha corregido una regresión que impedía el uso de algunos componentes de la consola, como el selector de fechas y la administración de imágenes en los envíos. (NEO-31453)

### ![](assets/do-not-localize/red_2.png) Versión 20.2.4, compilación 9187 {#release-20-2-4-build-9187}

_15 de abril de 2021_

* Se ha corregido una regresión de la consola del cliente que provocaba mensajes de error persistentes en la pantalla de conexión IMS. (NEO-34821)
* Se ha corregido una regresión que impedía el uso de algunos componentes de la consola, como el selector de fechas y la administración de imágenes en los envíos. (NEO-31453, NEO-31454)

**Solo es obligatorio actualizar la consola. No se requiere ninguna actualización del servidor.**

>[!NOTE]
>
> Conéctese a [Adobe Software Distribution](https://experience.adobe.com/#/downloads/content/software-distribution/en/campaign.html) para descargar la nueva versión. Aprenda a proponer la actualización de la consola a todos los usuarios finales [en esta página](../../installation/using/client-console-availability-for-windows.md).

_22 de diciembre de 2020_

>[!CAUTION]
>
> * Esta versión incorpora un nuevo protocolo de conexión: si se conecta a Campaign a través del Servicio de identidad de Adobe (IMS), la actualización es obligatoria tanto para el servidor de Campaign como para la consola cliente para poder conectarse a Campaign después del **30 de junio de 2021**.  [Más información](../../technotes/using/ims-updates.md)
> * Esta versión incluye una [corrección de seguridad](https://helpx.adobe.com/security/products/campaign/apsb21-04.html): la actualización es obligatoria para reforzar la seguridad de su entorno.
> * Si está utilizando la integración de Experience Cloud Triggers mediante autenticación oAuth, debe ir a Adobe I/O como se detalla [en esta página](../../integrations/using/configuring-adobe-io.md). El modo de autenticación de oAuth heredado con Campaign [se ha eliminado](https://experienceleaguecommunities.adobe.com/t5/adobe-analytics-discussions/adobe-analytics-legacy-api-end-of-life-notice/td-p/385411) en **septiembre de 2021**. Los entornos alojados se benefician de una extensión hasta  **23 de febrero de 2022**. Como cliente local o híbrido, póngase en contacto con el servicio de atención al cliente de Adobe para ampliar la asistencia hasta febrero de 2022. Debe proporcionar [el AppID de la aplicación OAuth](../../integrations/using/configuring-pipeline.md?lang=en#step-optional) a Adobe.


**Mejoras**

* El protocolo de conexión se ha actualizado para seguir el nuevo mecanismo de autenticación IMS.
* Activa la autenticación de integración basada originalmente en la configuración de autenticación oAUTH para acceder a la canalización, que se ha cambiado y se ha movido a Adobe I/O. [Más información](../../integrations/using/configuring-adobe-io.md)
* Después de [finalizar la compatibilidad con el protocolo binario heredado de APN de iOS](https://developer.apple.com/news/?id=c88acm2b), todas las instancias que utilizan este protocolo se actualizan al protocolo HTTP/2 durante la postactualización.
* Se ha corregido un problema de seguridad para reforzar la protección contra los problemas de falsificación de solicitudes del lado del servidor (SSRF). (NEO-27777)



* Se ha corregido un problema que provocaba la desactivación del conector SMPP tras un error de conexión, lo que impedía otros envíos SMS y provocaba problemas de rendimiento. (NEO-28609)



* Se ha corregido un problema de bloqueo del servidor al evitar la corrupción de memoria al limpiar el analizador de expresiones. (NEO-26856)



* Se corrigió un problema que ocasionaba que el servidor se bloqueara al mostrar los datos de destinatario del resto desde una actividad **dividida** en un flujo de trabajo.
* Se ha corregido un problema que podía mostrar un mensaje de error al intentar previsualizar los mensajes SMS después de una consulta en otro esquema que no fuera **Destinatario** (nms:destinatario). (NEO-27517)



* Se ha corregido un problema que se producía al realizar una solicitud de conexión HTTPS con el número de puerto definido explícitamente en el nombre de host y que provocaba un error de certificado. (NEO-29146)



* Se ha corregido un problema en la administración de subprocesos POSIX que generaba archivos de volcado de núcleo grandes en la instancia de marketing. (NEO-28117, NEO-29281)
* Se han corregido problemas que podían provocar que el proceso web se bloqueara al preparar entregas o con previsualización recurrente de entregas. (NEO-27790, NEO-27517)
* Se ha corregido un problema que ocasionaba que fallaran los envíos de entregas o pruebas cuando se activaba mediante un operador que no era administrador. (NEO-28597)




![](assets/do-not-localize/cp-icon.png) **la nueva versión de Panel de control de Campaign de octubre** con configuración de dominio mediante CNAME y nuevas funciones de supervisión de bases de datos. [Más información](https://experienceleague.adobe.com/docs/control-panel/using/release-notes.html?lang=es).

### ![](assets/do-not-localize/red_2.png) Versión 20.2.3, compilación 9182 {#release-20-2-3-build-9182}

_11 de septiembre de 2020_

* Se ha corregido una regresión que ocasionaba que la preparación de la entrega se bloqueara debido a una única función errónea en la parte de la entrega que provocó una sobrecarga de memoria. (NEO-27346)



* Se ha corregido un problema después de la actualización que desactivaba Apache y el servidor web antes de la republicación de la aplicación web. (NEO-27155)



* Se ha corregido una regresión en la administración de plantillas de HTML que provocaba que las direcciones URL de seguimiento se volvieran visibles debido a una interpretación errónea de las pestañas. (NEO-25909)



* Se ha corregido un problema con el flujo de trabajo de limpieza de base de datos que podía fallar debido a una fuente de datos no administrada. (NEO-23160, NEO-23364)
* El flujo de trabajo de limpieza ahora purga las listas caducadas por lotes de a100 en lugar de a una por una.
* Se ha corregido una regresión que impedía modificar el nombre interno de una cuenta externa. (NEO-27323)



* La corrección de una regresión después de la actualización provoca un inicio incorrecto de nlserver (registros de errores).
* Se ha mejorado la administración de actualizaciones para la memoria compartida. Los pasos adicionales requeridos en 20.2 ya no son necesarios.

### ![](assets/do-not-localize/red_2.png) Versión 20.2.2, compilación 9180 {#release-20-2-2-build-9180}

_22 de julio de 2020_

* Se ha corregido un problema que impedía que el seguimiento funcionara cuando la función de firma estaba deshabilitada. (NEO-26411)
* Se ha corregido un problema que provocaba que los vínculos sin firmar de dominios personalizados se bloquearan cuando deberían permitirse. (NEO-25210)
* Se ha corregido un problema que podía impedir que se abrieran las direcciones URL de seguimiento al usar ciertas versiones heredadas de Outlook o se hiciera clic en ellas. (NEO-25688)
* Se ha corregido el problema que provocaba que las direcciones URL de página espejo se definieran incorrectamente en los envíos de correo electrónico (debido a un control incorrecto de caracteres ASCII). (NEO-26084)
* Se ha corregido un problema de codificación con la administración de direcciones URL en el servicio antiphishing. (NEO-25283)
* Se ha corregido un problema que impedía que el funcionamiento del seguimiento de direcciones URL mediante fragmentos en parámetros de personalización (etiquetas de anclaje con signo de almohadilla). (NEO-25774)
* Se ha corregido un problema de seguimiento al usar fórmulas de seguimiento personalizadas específicas. (NEO-25277)




* Se ha corregido un problema que impedía el funcionamiento del seguimiento de &quot;clics de notificación&quot; (notificaciones push de iOS y Android). (NEO-25965)
* Se ha corregido la regresión que afectaba a los campos calculados de un flujo de trabajo y que provocaba un error. (NEO-25194)
* Se ha corregido una regresión que impedía que funcionara la creación rápida de direcciones URL de seguimiento web. (NEO-20999)
* Se ha corregido un problema de una regresión con los informes de envío listos para usar que aparecían truncados al exportarse a PDF. (NEO-25757)
* Se ha corregido un problema de bloqueo en el asistente de implementación.
* Se ha corregido un problema que podía impedir que el flujo de trabajo de la notificación de oferta funcionara correctamente después de una actualización posterior.
* Se ha mejorado el conector HTTP2 de iOS (actualizaciones de terceros y administración de errores). (NEO-25904, NEO-25903)
* Se ha actualizado la lista jarsToSkip en catalina.properties para eliminar la referencia a un archivo jar que ya no se utilizaba (notificaciones de iOS).
* Se ha corregido un problema que bloqueaba la preparación del envío después de la actualización.
* Después del cambio al [nuevo mecanismo de ID de secuencia](https://helpx.adobe.com/campaign/kb/sequence_auto_generation.html#Switchtoadedicatedsequence), todas las aplicaciones web que actualizan la tabla de destinatario se vuelven a publicar después de la actualización.
* Se ha corregido una potencial vulnerabilidad XSS en el contenido de envío. (NEO-17987, NEO-26073)

![](assets/do-not-localize/cp-icon.png) **Nuevo lanzamiento del Panel de control de Campaign en junio** con monitorización de perfiles activos, auditoría de entregas de subdominios y administración de claves GPG. [Más información](https://experienceleague.adobe.com/docs/control-panel/using/release-notes.html).

### ![](assets/do-not-localize/red_2.png) Versión 20.2.1, compilación 9178 {#release-20-2-1-build-9178}

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
    <p>Azure Synapse solo está disponible para entornos híbridos y locales. Para obtener más información, consulte la <a href="../../installation/using/configure-fda-synapse.md">documentación detallada</a>.</p>
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
   <p>La Ley General de Protección de Datos (Lei Geral de Proteção de Dados, LGPD) de Brasil entrará en vigencia a principios de 2021 para todas las compañías que recopilen o procesen datos personales en Brasil.</p>
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

* La mensajería transaccional se ha mejorado para mejorar la experiencia del usuario. Ahora puede cancelar la publicación de una plantilla de mensaje transaccional, que la elimina de las instancias de ejecución. [Más información](../../message-center/using/publishing-message-templates.md#template-unpublication).

* Hay nuevas opciones disponibles para establecer limitaciones al enviar correos electrónicos que incluyen imágenes o archivos adjuntos. Estas protecciones pueden evitar problemas de rendimiento, lo que resulta especialmente útil con la mensajería transaccional. [Más información](../../installation/using/configuring-campaign-options.md#delivery)

* La nueva opción **Preparar las piezas de envío en la base de datos** permite realizar la preparación de envíos directamente en la base de datos, lo que puede acelerar el análisis en gran medida. Esta opción solo está disponible para configuraciones específicas. [Más información](../../delivery/using/steps-validating-the-delivery.md#improving-delivery-analysis). (NEO-23886)

* Se ha mejorado el rendimiento de la [actividad del conector CRM](../../workflow/using/crm-connector.md) para Microsoft Dynamics. (NEO-13303, NEO-12710)

* Se ha aumentado la versión de memoria compartida.

   >[!WARNING]
   >
   >Esta mejora requiere un paso adicional después de realizar la actualización. Consulte la sección de **Evoluciones técnicas** que aparece a continuación.

* Se ha mejorado el flujo de trabajo de limpieza. Las tablas de trabajo huérfanas de todos los flujos de trabajo eliminados ahora también se eliminan automáticamente mediante el flujo de trabajo de limpieza. [Más información](../../production/using/database-cleanup-workflow.md#cleanup-of-workflow-instances).

* Los certificados para aplicaciones móviles iOS con el conector HTTP2 de iOS ahora se validan antes de enviar las notificaciones push, lo que evita que los envíos produzcan errores debido a certificados caducados.

* Se ha mejorado la administración de las conexiones proxy HTTP. [Más información](../../installation/using/file-res-management.md).

* Nueva opción en las actividades de flujo de trabajo **[!UICONTROL Javascript Code]** y **[!UICONTROL Advanced Javascript Code]** para detener la ejecución después de cierto límite. El valor predeterminado es de 1 hora. [Más información](../../workflow/using/sql-code-and-javascript-code.md#javascript-code).

**Otros cambios**

* Los conectores SMS heredados quedan obsoletos. Consulte la [Página de funciones obsoletas](../../rn/using/deprecated-features.md).

* Ya no puede utilizar su propia cuenta de Litmus para aprovisionar y utilizar la renderización de la Bandeja de entrada en Adobe Campaign. [Más información](../../delivery/using/inbox-rendering.md).

* Para distinguir mejor las vistas de las carpetas, se ha cambiado el color de los nombres de vistas de azul oscuro a cian oscuro. [Más información](../../platform/using/access-management-folders.md)

* Ahora, Campaign Classic puede conectarse a cuentas de Microsoft Dynamics CRM alojadas en las regiones de Reino Unido, India y Canadá. Esto se aplica a los tipos de implementación de Office 365 y Locales (Dynamics 2015).

* Campaign ahora realiza una verificación TLS para comprobar que el nombre de host del servidor coincide con el nombre de host del certificado proporcionado.

* La tabla de estadísticas de envío y seguimiento ahora muestra una entrada por envío para el canal SMS, en lugar de una entrada por destinatario de envío.

* Se añadió un mensaje de error en el archivo de registro para advertir a los usuarios cuando el archivo descargado es mayor que el espacio en disco.

* Ahora están disponibles las siguientes funciones para el conector Snowflake: MonthsAgo, DaysAgoInt, ToDateTime, YearsAgo.

**Evoluciones técnicas**

Esta nueva compilación actualiza la memoria compartida y requiere pasos adicionales para realizar la actualización. Como administrador de Campaign, debe eliminar los segmentos de memoria. Estos pasos son obligatorios, ya que los segmentos antiguos evitan que nlserver/nlsrvmod se inicie.

En Windows, es necesario reiniciar el sistema.

En Debian/CentOs, es necesario eliminar la memoria compartida. Estos son los pasos:

Antes de la actualización, debe seguir estos pasos:

1. Detenga el servicio apache2 (http2 en CentOS) si se está ejecutando.
1. Detenga el servicio nlserver (nlserver6 para compilaciones anteriores) si se está ejecutando.

Después de la actualización:

1. Elimine la memoria compartida mediante el comando **ipcrm** si la versión es anterior a la versión actual.
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

* Se ha corregido una regresión menor en los registros del flujo de trabajo de limpieza.
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
* Se ha corregido un problema que ocasionaba que los datos de seguimiento incluyeran duplicados aunque los registros de seguimiento no lo hicieran. (NEO-20040)
* Se ha corregido un problema que hacía que se enviaran correos electrónicos transaccionales en duplicado después de que se corrigiera un error de comunicación del servidor de seguimiento. (NEO-23640)
* Se ha corregido el problema que eliminaba el valor del parámetro de codificación al redirigir desde una URL de seguimiento (impacto en los caracteres japoneses). (NEO-25637)
* Se ha corregido un problema que podía impedir que una consulta funcionara al comparar números flotantes. (NEO-23243)
* Se ha corregido un problema que podía impedir que se mostrara el contenido de la columna **Modificado por** después de reiniciar un flujo de trabajo. (NEO-23035)
* Se ha corregido un problema que ocasionaba que fallara el flujo de trabajo técnico de seguimiento al descargar registros de un segundo contenedor. (NEO-23159)
* Se ha corregido un problema que podía provocar errores en los flujos de trabajo al ejecutar una actividad de **Enriquecimiento**. (NEO-17338)
* Se ha añadido una comprobación al campo **Dobles para mantener** en la actividad del flujo de trabajo de **Anulación de duplicación** para evitar que se introduzca valores nulos o negativos.
* Se ha eliminado el **Asistente del planificador** de las campañas recurrentes para evitar la mención de horas y minutos. Solo se tienen en cuenta las fechas.
* Se ha corregido un problema con campos de almacenamiento adicionales al crear envíos a través de la opción **Calculado por un script** en la actividad de flujo de trabajo **Script**. (NEO-20609)
* Se ha corregido un problema que impedía que se eliminaran flujos de trabajo fantasma en las tareas de limpieza de la base de datos.
* Se ha corregido un problema que provocaba que fallara el flujo de trabajo técnico de **Facturación (perfiles activos)**. (NEO-19777)
* Se ha corregido un problema de regresión al utilizar la función del conector de ACS que impedía la conexión a una instancia de Campaign Standard (administración incorrecta de la conexión FOH/FOH2). (NEO-23433)
* Se ha corregido un problema que impedía crear una extensión de esquema en una clave principal con varias columnas con una tabla Hadoop. (NEO-17390)
* Se ha corregido un problema en la actividad **Cargar (SOAP)** que podía impedir que los archivos WSDL se cargaran desde una dirección URL. (NEO-16924)
* Se ha corregido un problema que impedía realizar una **Parada incondicional** a través de la consola cuando se equilibraba la carga de varios servidores de flujo de trabajo activos. (NEO-19556)
* Se ha corregido una regresión que ocasionaba que el flujo de trabajo de limpieza se bloqueara.
* Se ha corregido un problema que se podía producir al publicar una plantilla en una instancia de ejecución.
* Se ha corregido un problema que podía impedir que se ejecutara el flujo de trabajo técnico collectPrivacyRequests. (NEO-20513, NEO-25169)
* Se han corregido problemas que podían producirse al intentar conectarse al Audience Manager después de actualizar a la versión 9080. (NEO-20511, NEO-25167)
* Se han corregido problemas que podían producirse al exportar informes en formato PDF o XLS. (NEO-20982, NEO-23493, NEO-23348)
* Se ha corregido un problema que podía mostrar un envío dos veces en la lista de envíos después de enviarlo.
* Se ha corregido un problema con la preparación de envíos que se podía producir cuando la configuración de enrutamiento estaba configurada para realizar el envío mediante intermediario.
* Se ha corregido un problema que podía mostrar un mensaje de error al hacer clic en un enlace de aplicación web dentro de un mensaje de línea.
* Se ha corregido un problema que eliminaba el historial de actividades de **Consulta incremental** después de ejecutar el flujo de trabajo de limpieza.
* Se ha corregido un problema al crear una cuenta externa intermediaria en el cual faltaba la opción NmsMidSourcing_LastBroadLog_&lt;InternalName>..
* Se ha corregido un problema de regresión en la conexión de la base de datos que provocaba que el servidor web se reiniciara constantemente debido a un problema de codificación de la base de datos. Esto podría causar un consumo excesivo. (NEO-23264)





## Versión 20.1{#release-20-1}

### ![](assets/do-not-localize/limited_2.png) Versión 20.1.4, compilación 9126 {#release-20-1-4-build-9126}

_15 de abril de 2021_

* Se ha corregido una regresión de la consola del cliente que provocaba mensajes de error persistentes en la pantalla de conexión IMS. (NEO-34821)

**Solo es obligatorio actualizar la consola. No se requiere ninguna actualización del servidor.**

>[!NOTE]
>
> Conéctese a [Adobe Software Distribution](https://experience.adobe.com/#/downloads/content/software-distribution/en/campaign.html) para descargar la nueva versión. Aprenda a proponer la actualización de la consola a todos los usuarios finales [en esta página](../../installation/using/client-console-availability-for-windows.md).

_22 de marzo de 2021_

* Se ha corregido una regresión que impedía el uso de algunos componentes de la consola, como el selector de fechas y la administración de imágenes en los envíos. (NEO-31453, NEO-31454)

**Solo es obligatorio actualizar la consola. No se requiere ninguna actualización del servidor.**

>[!NOTE]
>
> Conéctese a [Adobe Software Distribution](https://experience.adobe.com/#/downloads/content/software-distribution/en/campaign.html) para descargar la nueva versión. Aprenda a proponer la actualización de la consola a todos los usuarios finales [en esta página](../../installation/using/client-console-availability-for-windows.md).

_23 de diciembre de 2020_

>[!CAUTION]
>
> * Esta versión incorpora un nuevo protocolo de conexión: si se conecta a Campaign a través del Servicio de identidad de Adobe (IMS), la actualización es obligatoria tanto para el servidor de Campaign como para la consola cliente para poder conectarse a Campaign después del **30 de junio de 2021**. [Más información](../../technotes/using/ims-updates.md)
>
> * Esta versión incluye una [corrección de seguridad](https://helpx.adobe.com/security/products/campaign/apsb21-04.html): la actualización es obligatoria para reforzar la seguridad de su entorno.


* El protocolo de conexión se ha actualizado para seguir el nuevo mecanismo de autenticación IMS.
* Se ha corregido un problema de seguridad para reforzar la protección contra los problemas de falsificación de solicitudes del lado del servidor (SSRF). (NEO-27777)




### ![](assets/do-not-localize/red_2.png) Versión 20.1.3, compilación 9124{#release-20-1-3-build-9124}

_miércoles, 6 de mayo de 2020_

* Se ha corregido un problema con la actividad **File Transfer** que impedía que la autenticación basada en claves SFTP funcionara en Debian 9. (NEO-23183)

### ![](assets/do-not-localize/red_2.png) Versión 20.1.2, compilación 9123{#release-20-1-2-build-9123}

_viernes, 13 de marzo de 2020_

* Se ha corregido un problema que impedía la implementación de versiones en servidores de Red Hat 7. (NEO-23332)

### ![](assets/do-not-localize/red_2.png) Versión 20.1, compilación 9122{#release-20-1-build-9122}

_lunes, 17 de febrero de 2020_

**Novedades**

<table> 
 <thead> 
  <tr> 
   <th> <strong>Conector de FDA de Snowflake</strong><br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> <p>Snowflake es un almacén de datos en la nube completamente gestionado, diseñado para escalar tanto en almacenamiento como en computación. Con este nuevo conector, Adobe Campaign ahora puede aprovechar el poder de Snowflake para realizar la segmentación de Big Data. Este conector está disponible para todos los clientes, incluido Adobe.</p>
    <p>Para obtener más información, consulte la <a href="../../installation/using/configure-fda-snowflake.md">documentación detallada</a> y el <a href="https://experienceleague.adobe.com/docs/campaign-classic-learn/tutorials/administrating/fda/big-data-segmentation-on-snowflake.html">videotutorial</a>.</p>
   </td> 
  </tr> 
 </tbody> 
</table>

<table> 
 <thead> 
  <tr> 
   <th> <strong>Mejoras en el conector FDA Hadoop</strong><br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> <p>Se ha mejorado el conector de FDA Hadoop para admitir tanto Hadoop 3.0 como Cloudera.</p>
    <p>Para obtener más información, consulte la <a href="../../installation/using/configure-fda-hadoop.md">documentación detallada</a>.</p>
   </td> 
  </tr> 
 </tbody> 
</table>

**Mejoras de seguridad**

* Se ha mejorado la seguridad en la configuración de informes para evitar el secuestro de clics. Esto se aplica a los nuevos informes. Para los informes antiguos, debe volver a publicarlos para aplicar los cambios. (NEO-13282)

* Se ha corregido un pequeño problema de memoria en cryptString. (NEO-20071)

* Se mejoró el JSP del monitor para corregir una divulgación de IP interna. (NEO-16821)

* Se ha corregido un problema en el cual la información de seguimiento de pila se podía mostrar a usuarios que no fueran administradores. (NEO-12388)

* Se ha mejorado la administración de los datos almacenados en caché de sesiones anteriores. (NEO-17039)

* Se ha corregido un problema que impedía que el archivo logins.log registrara los intentos de inicio de sesión correctos a través de IMS. (NEO-11004)

**Mejoras**

* iOS 13 ahora es compatible con el conector HTTP2.

* Se ha mejorado la gestión y limpieza de cuarentenas de las tablas utilizadas por la función de notificaciones push (nms:address y nms:appSubscriptionRcp). Para iOS (solo conector HTTP2), los tokens desactivados ahora se gestionan del mismo modo que para Android. El indicador disable ahora se establece en la tabla NmsAppSubscriptionRcp. [Más información](../../production/using/database-cleanup-workflow.md#subscription-cleanup--nmac-)

* Se ha añadido una nueva opción en las actividades de flujo de trabajo de **código JavaScript** y de **código JavaScript avanzado** para definir un período de tiempo de espera. Esto evita que la fase de ejecución de JavaScript se ejecute durante demasiado tiempo. Si transcurre el tiempo de espera, el flujo de trabajo se detiene. El tiempo de espera predeterminado es 1 hora. [Más información](../../workflow/using/sql-code-and-javascript-code.md)

* El análisis de envío ahora se detiene cuando no se encuentra ninguna afinidad coincidente en el servidor intermediario y se muestra el mensaje de error correspondiente.

* Ahora se admite la conmutación por error de base de datos para Postgres: cuando el servidor de la base de datos se bloquea y se reinicia, Campaign ahora se vuelve a conectar automáticamente.

* La vista **Start Pending** se ha añadido al nodo Administration > Audit > Workflows Status. Esto permite supervisar todos los flujos de trabajo de la instancia que están a la espera de ser iniciados por el proceso **operationMgt**. Esta vista viene con el paquete de campañas de marketing. [Más información](../../workflow/using/monitoring-workflow-execution.md#filtering-workflows-status)

**Otros cambios**

* En Linux, el inicio del servicio nlserver ahora utiliza una unidad sistémica en lugar de la secuencia de comandos /etc/init.d/nlserver6. La migración al nuevo esquema de inicio se realiza automáticamente al instalar el paquete 20.1. Aún se proporciona el /etc/init.d/nlserver6; sin embargo, para interactuar con el servicio nlserver (inicio, reinicio, parada, etc.), se recomienda utilizar el comando systemctl directamente.

* Las tablas personalizadas más consumidoras se han movido de la secuencia **xtkNewId** a secuencias dedicadas. [Más información](https://helpx.adobe.com/campaign/kb/sequence_auto_generation.html#Switchtoadedicatedsequence)

* Se ha mejorado el rendimiento de la consulta, lo que podría verse afectado por conexiones de base de datos innecesarias.

* Se ha mejorado el rendimiento del asistente de actualización de bases de datos a fin de hacer menos instrucciones SQL para optimizar el tiempo de respuesta.

* Se mejoró la administración de registros de la base de datos.

* Se ha mejorado la solidez del grupo de conexiones, lo que puede evitar que se produzcan fallos de conexión inesperados con demasiada frecuencia.

* Se han mejorado las reglas de validación de direcciones de correo electrónico para enviar una dirección a la cuarentena en caso de que se produzca un error de software. [Más información](../../delivery/using/understanding-quarantine-management.md#soft-error-management)

* Para Debian, Campaign ahora utiliza bibliotecas PCRE del sistema cuando están disponibles.

* Campaign ahora permite el uso de una biblioteca ODBC del sistema más reciente.

* Se ha añadido un tiempo de espera al servlet LINE al abrir una conexión para cargar una imagen enriquecida. Si la imagen tarda demasiado en cargarse, el servlet detiene la conexión para evitar un cuello de botella.

**Parches**

* Se ha corregido un problema de cifrado de clave de cuenta al usar el conector Hadoop.

* Se ha corregido un problema de regresión debido a la implementación de la certificación SSL que hacía que la conexión del usuario fallara en el servidor de Windows. (NEO-20629)

* Se ha corregido un problema con la actividad de consulta incremental en el caso de ID de flujo de trabajo negativos. (NEO-19779)

* Se ha corregido un problema de codificación al ejecutar consultas mediante el conector de FDA de Netezza. (NEO-19594)

* Se ha corregido un problema que provocaba un error al usar el método POST en la actividad de evento del flujo de trabajo de **descarga web**.

* Se ha corregido un problema con la generación de propuestas de ofertas. (NEO-18176)

* Se ha corregido un problema de visualización de pie de página al usar la plantilla de formulario web de adquisición.

* Se ha corregido un problema que se producía al analizar las direcciones URL en el contenido de envíos continuos y que podía provocar que se bloquearan. (NEO-16910)

* Se ha corregido un problema por el que los campos **Start** y **End** no se calculaban al crear una nueva campaña.

* Se ha corregido un problema con la actividad del flujo de trabajo de **File Download** al usar una dirección URL.

* Se ha corregido un problema al obtener una vista previa de una lista importada en una actividad de consulta de un informe. (NEO-13119)

* Se ha corregido un problema que mostraba una imagen desactualizada al seleccionar el bloque de personalización **Powered by Campaign** en el editor de correo electrónico.

* Se ha mejorado la comunicación de red entre el cliente y el servidor.

* Se ha corregido un problema en el cual se creaban demasiados flujos de trabajo en la misma campaña. Ahora no se pueden crear más de 28 flujos de trabajo. Se muestra una advertencia.

* Se ha corregido un problema al usar la opción de reconciliación **A selection of columns** en una actividad de flujo de trabajo de **Union**.

* Se ha corregido un problema de bloqueo de la consola que se podía producir al usar una lista de enriquecimiento dañada en un flujo de trabajo. (NEO-18096)

* Se han corregido varios problemas de bloqueo de la consola que podían producirse en flujos de trabajo (NEO-18010, NEO-18032).

* Se ha corregido un problema que permitía la ejecución de una actividad de flujo de trabajo de **señal externa** incluso cuando estaba desactivada. (NEO-17524)

* Se ha corregido un problema al crear un nuevo esquema.

* Se ha corregido un problema de seguimiento al enviar mensajes SMS. (NEO-19595)

* Se ha corregido un problema que mostraba un número de audiencia objetivo incorrecto en los indicadores de envío.

* Se ha corregido un problema que mostraba porcentajes incorrectos al generar un informe descriptivo mediante una actividad de flujo de trabajo. (NEO-14314)

* Se ha corregido un problema que hacía que el informe de rendimiento de envíos mostrara números diferentes cuando se utilizaba el parámetro de vista horaria. (NEO-11783)

* Se ha corregido un problema que impedía que el flujo de trabajo de seguimiento actualizara los indicadores de seguimiento de mensajes transaccionales. (NEO-17770)

* Se ha corregido un problema de regresión que provocaba que el proceso web se bloqueara y se reiniciara al solicitar una oferta a través de SOAP. (NEO-19482)

* Se ha corregido un problema que impedía cargar datos en recursos públicos si el directorio de carga era una ubicación compartida remota. (NEO-19361)

* Se ha corregido un problema que provocaba que el flujo de trabajo técnico de **Import audiences from the Adobe Experience Cloud** fallara constantemente. (NEO-18463)

* Se ha corregido un problema que impedía que se mandaran envíos al usar plantillas importadas desde Experience Manager. (NEO-17540)

* Se ha corregido un problema que se producía tras actualizar a la compilación 9032 y evitar que la instancia se conectara al servidor FTP a través del protocolo SSL. (NEO-20498)

* Se ha corregido un problema que se producía al eliminar, insertar o actualizar una gran cantidad de datos con la actividad **Actualizar datos** en un flujo de trabajo mediante un esquema FDA como dimensión de segmentación. (NEO-13280)

* Se ha corregido un problema que impedía enviar correos electrónicos cuando había código JavaScript fuera de la etiqueta de contenido HTML. (NEO-18628)

* Se ha corregido un problema que se producía al intentar mostrar la página espejo de los registros de envío de un mensaje enviado. (NEO-17976)

* Se ha corregido un problema que impedía que el bloque de personalización **Enlace a página espejo** se mostrara en la ficha **Contenido de texto** después de hacer clic en **Importar HTML** en un envío. (NEO-17568)

* Se ha aclarado el mensaje de error que se muestra al hacer clic en un enlace a una página espejo que ha caducado. (NEO-17340)

* Se ha corregido un problema que impedía que se usaran algunos botones en la pantalla de creación de la **Distribución de datos**.

* Se ha corregido un problema que se producía al programar una actividad de envío en una instancia con Asia y Calcuta como huso horario. (NEO-20001)

* Ahora se muestra un error cuando un envío tiene un problema de configuración de afinidad.

* Se ha corregido un problema que mostraba un número de etiqueta de versión incorrecto en el menú **Acerca de**.

* Se ha corregido un problema que se producía al intentar actualizar la cuenta de enrutamiento desde las propiedades de un envío recurrente en un flujo de trabajo. (NEO-18684)

* Se ha corregido un problema que se producía al conectarse a la instancia a través del módulo de redirección, lo que impedía que la conexión se limpiara correctamente una vez cerrada.
