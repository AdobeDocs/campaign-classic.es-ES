---
solution: Campaign Classic
product: campaign
title: Notas de la versión de Campaign 20.3
description: Notas de la versión de Campaign 20.3
feature: Overview
role: Business Practitioner
level: Beginner
translation-type: tm+mt
source-git-commit: 1f718e26aeaa5ed5a58dfd0e3bc29d2dd9e995ee
workflow-type: tm+mt
source-wordcount: '1952'
ht-degree: 95%

---


# Versión 20.3{#release-20-3}

## ![](assets/do-not-localize/red_2.png) Versión 20.3.3: compilación 9234 {#release-20-3-3-build-9234}

_11 de enero de 2021_

* Se ha corregido un problema de seguridad para reforzar la protección contra los problemas de falsificación de solicitudes del lado del servidor (SSRF). (NEO-27777)



* Se ha corregido un problema de regresión relacionado con el proceso de generación de registros de banda ancha que podía provocar el bloqueo del proceso de MTA.

## ![](assets/do-not-localize/red_2.png) Versión 20.3.1 - Compilación 9228 {#release-20-3-1-build-9228}

_27 de octubre de 2020_

>[!CAUTION]
>
> * Esta versión incorpora un nuevo protocolo de conexión: si se conecta a Campaign a través del servicio de identidad de Adobe (IMS), la actualización es obligatoria para que el servidor de Campaign y la consola del cliente puedan conectarse a Campaign después del **30 de junio de 2021**.
> * Esta versión incluye una [corrección de seguridad](https://helpx.adobe.com/security/products/campaign/apsb21-04.html): la actualización es obligatoria para reforzar la seguridad de su entorno.
> * Si está utilizando la integración de Déclencheur de Experience Cloud mediante autenticación oAuth, debe pasar a Adobe I/O como se describe [en esta página](../../integrations/using/configuring-adobe-io.md). El modo de autenticación oAuth heredado con Campaign se eliminará el **30 de noviembre de 2021**.


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



