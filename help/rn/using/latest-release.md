---
title: Última versión
description: Última versión de Campaign Classic Notas
page-status-flag: never-activated
uuid: 269d590c-5a6d-40b9-a879-02f5033863fc
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: rns
content-type: reference
topic-tags: latest-release-notes
discoiquuid: 5df34f55-135a-4ea8-afc2-f9427ce5ae7b
translation-type: tm+mt
source-git-commit: fe7ce92bde3405fed3429475cdd5681e5837876f
workflow-type: tm+mt
source-wordcount: '1820'
ht-degree: 4%

---


# Última versión{#latest-release}

Esta página lista las nuevas funciones, mejoras y correcciones que se proporcionan con la **última versión** de Campaign Classic Release Candidate.

Para la versión de Campaign Classic Gold Standard (versión más reciente de GA build), [consulte esta página](../../rn/using/gold-standard.md).

## ![](assets/do-not-localize/blue_2.png) Versión 20.3.1: compilación 9228 {#release-20-3-1-build-9228}

_27 de octubre de 2020_

**Novedades**

<table> 
<thead>
<tr> 
<th> <strong>Mejoras en las notificaciones push de iOS</strong><br /> </th> 
</tr> 
</thead> 
<tbody> 
<tr> 
<td> <p>Al integrar su aplicación móvil con Campaña, debe asegurar su comunicación con el servicio de notificaciones push de Apple (APN). Puede utilizar la autenticación basada en certificados o en tokens.
</p>
<p>Estos dos modos de autenticación ya están disponibles para las aplicaciones móviles de iOS en Campaign Classic:
</p>
<ul> 
<li><p>Autenticación basada en tokens (recomendada): este modo de autenticación se basa en un archivo .p8. Este modo de autenticación es más rápido, ya que cada solicitud a APN contiene el token. <a href="https://developer.apple.com/documentation/usernotifications/setting_up_a_remote_notification_server/establishing_a_token-based_connection_to_apns">Más información</a></p></li>
<li><p>Autenticación basada en certificados: este modo de autenticación se basa en un archivo .p12. Se requiere un certificado independiente para cada aplicación. Apple entrega este certificado a través de su cuenta de desarrollador. <a href="https://developer.apple.com/documentation/usernotifications/setting_up_a_remote_notification_server/establishing_a_certificate-based_connection_to_apns">Más información</a></p></li> 
</ul>
<p>Obtenga información sobre cómo seleccionar el modo de autenticación en Campaña en la documentación <a href="../../delivery/using/configuring-the-mobile-application.md"></a>detallada.</p>
</td> 
</tr> 
</tbody> 
</table>

<table> 
<thead>
<tr> 
<th> <strong>Mejoras en las notificaciones push de Android</strong><br /> </th> 
</tr> 
</thead> 
<tbody> 
<tr> 
<td> <p>Se han mejorado las notificaciones push de Android para admitir la API HTTP v1 de FCM para la autenticación de canal push de Android. </p>
<p>Con la nueva versión de API admitida, ahora puede enviar mensajes de notificación FCM, que proporcionan funciones de mensajería push enriquecidas y mejoradas. <a href="https://firebase.google.com/docs/cloud-messaging/migrate-v1">Más información</a></p> 
<p>Aprenda a configurar la API HTTP v1 de FCM para Android en Adobe Campaign en <a href="../../delivery/using/configuring-the-mobile-application-android.md">esta sección</a> .</p>
</td> 
</tr> 
</tbody> 
</table>

**Mejoras de seguridad**

* Carga segura de bibliotecas: Para protegerse de los ataques de precarga de DLL, la Campaña ahora carga las DLL de Windows únicamente desde la ruta de acceso predeterminada de la DLL del sistema de Windows al cargar el cliente de Campaña (nlclient). [Más](https://support.microsoft.com/en-us/help/2389418/secure-loading-of-libraries-to-prevent-dll-preloading-attacks) información (NEO-24147)
* Se ha corregido un problema de seguridad para reforzar la protección contra los ataques de falsificación de solicitudes del lado del servidor (SSRF). (NEO-25661)



* Se ha corregido un problema que se producía al administrar solicitudes de privacidad de GDPR que impedía que se eliminaran registros de tablas personalizadas con una relación de segundo nivel con la tabla de Destinatario. (NEO-25967)



* Se ha corregido un problema de seguridad que se producía al intentar sincronizar plantillas de Adobe Experience Manager mediante llamadas de API realizadas por usuarios no administradores. (NEO-23487)




**Actualizaciones de compatibilidad**

Ahora se admiten los siguientes sistemas con Campaign:
* iOS14
* PostgreSQL 12
* CentOS / RedHat 8
* MSSQL2019

Learn more in the [Campaign Compatibility matrix](../../rn/using/compatibility-matrix.md).

**Funciones obsoletas**

Las siguientes funciones están en desuso en 20.3:

* El dominio demdex utilizado para importar y exportar audiencias al Adobe Experience Cloud está en desuso. Si utiliza el dominio demdex para sus cuentas externas de importación y exportación, deberá adaptar la implementación en consecuencia. [Más información](../../integrations/using/configuring-shared-audiences-integration-in-adobe-campaign.md)
* Activa la autenticación de integración basada originalmente en la configuración de autenticación oAUTH para acceder a la canalización y ahora se ha cambiado y se ha movido a E/S de Adobe. [Más información](../../integrations/using/about-triggers.md)

Obtenga más información en la página [](../../rn/using/deprecated-features.md)Funciones obsoletas y eliminadas.

**Mejoras**

* Se han realizado varias mejoras en la consola **Cliente**:
   * Para evitar incompatibilidades con algunas restricciones de reglas GPO de seguridad de Internet, la pantalla de inicio de sesión de la consola cliente de Campaña se ha sustituido por un formulario estándar integrado de Windows.
   * Se ha corregido un problema que se producía al copiar/pegar actividades en un flujo de trabajo con la consola cliente de 64 bits. (NEO-27635)



   * En el menú **Acerca** , se ha añadido información para distinguir las consolas de 64 y 32 bits.
* El identificador de flujo de trabajo ahora se muestra en los registros al reanudar un flujo de trabajo, lo que le permite identificar mejor qué flujo de trabajo se ha reanudado.
* Se ha introducido una nueva cookie permanente: nllastdelid. Esta cookie (que no sea UUID230) almacenará deliveryId. Cuando la cookie de sesión no está presente, la información del registro de banda ancha se tomaría de la entregaId presente en esta cookie.
Este cambio corrige un problema que se producía al finalizar la sesión del explorador: se eliminó la cookie de sesión que contenía deliveryId y BroadlogId. Sin deliveryId, no se pudo encontrar la información del registro extendido y faltaría la información de la tabla de seguimiento en caso de rastreo permanente (último envío).
Learn more about cookies in [this section](../../platform/using/privacy-and-recommendations.md#cookies).
* Se mejoró el rendimiento del rendimiento del envío de gran volumen con el servidor de entrega al reiniciar el proceso de MTA antes del envío de envíos.

**Otros cambios**

* Cuando se utiliza la ruta relativa para SFTP, ya no se agregan `~/` caracteres automáticamente. Si es necesario, puede agregar `~/` caracteres a la ruta manualmente, pero Adobe recomienda utilizar una ruta **** absoluta.
* La autenticación de Windows NT se ha eliminado de los métodos de autenticación disponibles al configurar una nueva base de datos con Microsoft SQL Server. [Más información](../../installation/using/creating-and-configuring-the-database.md#step-1---selecting-the-database-engine)
* El flujo de trabajo de limpieza de la base de datos se ha optimizado para Teradata a fin de mejorar el rendimiento. (NEO-19959)



* Se mejoró el mensaje de error que se mostraba al insertar una imagen de Adobe Target y el nombre del inquilino estaba vacío en la cuenta externa.
* En las propiedades de envío, se ha cambiado el nombre de la **[!UICONTROL Archive emails]** opción **[!UICONTROL Email BCC]**.
* Para mejorar la solidez, seleccione Todas las consultas con nodos no válidos ahora se rechazan. Si necesita deshabilitar la comprobación y volver al comportamiento anterior, puede establecer XtkSecurity_Disable_QueryCheck en 0.

**Evoluciones técnicas**

Tomcat se ha actualizado de la versión 7 (7.0.103) a la versión 8 (8.5.57).

El `tomcat-7` directorio se reemplaza por un `tomcat-8` directorio.

En Windows, _iis_neolane_setup.vbs_ y _apache_neolane.conf_ se instalan ahora en el `conf` directorio (en lugar de `tomcat-7/conf` anteriormente).

En linux, _apache_neolane.conf_ está ahora instalado en el `conf` directorio.

**Parches**

* Se ha corregido un problema que podía impedir que las estadísticas de envío se volvieran a calcular.
* Se ha corregido un problema que mostraba un mensaje de error al cargar un archivo CSV al usar la compilación Campaign Classic 9080 conectada a un servidor mediante una compilación anterior. (NEO-23218)



* Se ha corregido un problema que podía mostrar un mensaje de error al configurar el asistente de Microsoft Dynamics CRM para una cuenta externa. Esto se debió a un problema de compatibilidad con la última versión de la API de MS Dynamics CRM. (NEO-24528)
* Se ha corregido un problema que impedía exportar registros de tipo de búsqueda (es decir, datos formados por registros de claves externas conectados con otras tablas) de Campaign Classic a Microsoft Dynamics mediante el conector CRM. (NEO-23864)



* Se ha corregido un problema que podía impedir que se recuperaran datos de Microsoft Dynamics si la opción de índice **** automático estaba activada en el conector CRM. (NEO-25981)



* Se ha corregido un problema con la autenticación IMS que podía dejar las conexiones abiertas incluso si habían finalizado. Las conexiones terminadas ahora se cierran automáticamente en cuanto finalizan para evitar la acumulación de conexiones y el consumo de recursos del sistema. (NEO-25996)



* Se ha corregido un problema que no mostraba ningún mensaje de error cuando se producía un error en la sincronización del contenido de Adobe Experience Manager en un envío debido a una configuración incorrecta de la cuenta externa (cuenta o contraseña incorrectas). Ahora aparece un mensaje en caso de error, que le permite identificar el problema con mayor facilidad. (NEO-25586)



* Se ha corregido un problema que se producía al seleccionar el tipo de operación **Actualizar** en la actividad **Actualizar datos** . Si los datos que se van a actualizar son incorrectos, el flujo de trabajo se mostrará en error y fallará. En caso de datos incorrectos, el flujo de trabajo no fallará y los registros se almacenarán en una transición **Rechaza** salida. (NEO-23794)



* Se ha corregido un problema que podía impedir que los flujos de trabajo que contenían subflujos de trabajo funcionaran. (NEO-24036)



* Se ha corregido un problema que, al editar una descripción de plantilla de campaña, impedía que se mostrara el botón **Guardar** al copiar y pegar símbolos como, por ejemplo, caracteres japoneses. (NEO-27071)



* Se ha corregido un problema que podía impedir que se cambiara el servidor de seguimiento en el asistente de configuración de instancias.
* Se ha corregido un problema que impedía guardar la descripción de una campaña o plantilla de campaña al hacer clic fuera de la ventana antes de hacer clic en el botón **Guardar** . (NEO-27449)



* Se ha corregido un problema que podía impedir que funcionara el flujo de trabajo técnico **Número de perfiles** de facturación activos (facturarActiveContactCount). Esto podría suceder si se hubiera realizado un vínculo en un campo calculado en una extensión de esquema. Se creó una gran cantidad de datos, lo que podría hacer que la base de datos se quedara sin espacio temporal. (NEO-24062)



* Se ha corregido un problema con la actividad de carga de **datos (archivo)** , que podía impedir la importación de caracteres japoneses de archivos txt y csv si se colocaron al final del archivo. (NEO-24957)



* Se ha corregido un problema con envíos continuos que podía impedir que los campos **Análisis iniciada** y **Análisis finalizada** se rellenaran correctamente. (NEO-20755)



* Se ha corregido un problema que podía mostrar un mensaje de error al intentar previsualización de mensajes SMS después de una consulta en otro esquema que no fuera **Destinatario** (nms:destinatario). (NEO-27517)



* Se ha corregido un problema al usar el conector de FDA del Snowflake. Un usuario con derechos de nombre de acceso FDA Snowflake no pudo ejecutar una consulta en un esquema de Snowflake. En los registros se mostraba un error de tipo &quot;No se encontró la contraseña&quot;. (NEO-23851)



* Se ha corregido un problema que se producía al usar un conector de FDA cuando el nombre del esquema de FDA vinculado era una subcadena del nombre de un elemento del esquema actual. Esto ocurría, por ejemplo, si el esquema de FDA era &quot;cust&quot; y uno de los elementos dentro del esquema de Destinatario era &quot;customer&quot;. Al recuperar la columna dentro del elemento &quot;cliente&quot; y agregar una columna desde el esquema de FDA &quot;cust&quot;, faltaba el valor de la columna local. (NEO-20193)



* Se corrigió un problema en flujos de trabajo al recuperar registros de una base de datos externa e insertarlos en la base de datos de Campañas. (NEO-26359)



* Se ha corregido un problema en el flujo de trabajo técnico de estado **de** Actualizar evento: para que coincidiera con el tamaño de los campos correspondientes entrantes en la actividad de estadísticas **de** Envío, el tamaño de tres campos de destino en la actividad **Actualizar estadísticas** de envío cambió de 32 a 64 bits. (NEO-11557) Obtenga más información sobre el flujo de trabajo de estado **del evento de** actualización en [esta sección](../../workflow/using/message-center--execution-.md).
* Se ha corregido un problema en el informe Historial **de Eventos del centro de** mensajes que provocaba errores de secuencia de comandos al intentar aplicar filtros y hacía imposible el filtro por un intervalo de fechas. (NEO-23365)



* Se ha corregido un problema de interferencia entre los flujos de trabajo técnicos de trabajos **de** Campaña (operationMgt) y de **Previsualización** (pronóstico). Esto ocurría cuando los envíos programados permanecían en el estado &quot;Listo para Destinatario&quot; o &quot;Listo para entregar&quot;. (NEO-20819)



* Se corrigió un problema con el análisis de XML cuando el identificador XML no estaba presente en el campo de datos en xtkOperator. Estaba causando un error después de la actualización. (NEO-26113)



* Se ha corregido un problema que se producía al usar la actividad **de transferencia** de archivos vinculada a una cuenta externa de Azure cifrada en SSL, donde la conexión se realizaba con HTTP en lugar de HTTPS. (NEO-26720)



* Se corrigió un problema en la base de datos MSSQL en el cual se podía producir un error con el procedimiento up_updatestats durante el flujo de trabajo de limpieza.
* Se corrigió un bloqueo que se producía durante el cierre del proceso web si las solicitudes de interacción aún se estaban procesando. (NEO-26447)



* Se corrigió un problema en el cual la función **NoNull** en Oracle DB ya no funcionaba después de la actualización 9032. (NEO-26488)



* Se corrigió un problema en el cual el flujo de trabajo de seguimiento fallaba después de la actualización 9171 si el paquete LINEV2 se instalaba sin el paquete de Message Center.
* Se ha corregido un problema de escalabilidad que impedía que el grupo de conexiones aumentara al número deseado de conexiones porque la cadena de conexión de base de datos del atributo &quot;APP&quot; acababa obteniendo un valor no válido. (NEO-25105)



* Se ha corregido un problema en el nivel de configuración proxy que impedía iniciar sesión en Adobe Campaign después de la última actualización de Windows 10. (NEO-27813)



* Se ha corregido un problema que hacía que las direcciones URL no deseadas estuvieran visibles en los correos electrónicos enviados después de importar plantillas HTML con vínculos de seguimiento. (NEO-25909)



* Se corrigió un problema que ocasionaba que el servidor se bloqueara al mostrar los datos de destinatario del resto desde una actividad **dividida** en un flujo de trabajo.
* Se ha corregido un problema de bloqueo del servidor al evitar la corrupción de memoria al limpiar el analizador de expresiones. (NEO-26856)



* Se corrigió un problema en la actividad de enriquecimiento en el cual los usuarios no administradores definían variables de instancia. (NEO-25653)


