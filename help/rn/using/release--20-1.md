---
product: campaign
title: Versión 20.1
description: Versión 20.1
feature: Información general
role: Business Practitioner
level: Beginner
exl-id: 7e4234c9-3d8f-4014-a870-75e91cfad725
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: tm+mt
source-wordcount: '1560'
ht-degree: 100%

---

# Versión 20.1{#release-20-1}

## ![](assets/do-not-localize/limited_2.png) Versión 20.1.4: compilación 9126 {#release-20-1-4-build-9126}

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
> * Esta versión incorpora un nuevo protocolo de conexión: si se está conectando a Campaign a través del Servicio de identidad de Adobe (IMS), la actualización es obligatoria tanto para el servidor de Campaign como para la consola cliente para poder conectarse a Campaign después del **30 de junio de 2021**.
   >
   > 
* Esta versión incluye una [corrección de seguridad](https://helpx.adobe.com/security/products/campaign/apsb21-04.html): la actualización es obligatoria para reforzar la seguridad de su entorno.


* El protocolo de conexión se ha actualizado para seguir el nuevo mecanismo de autenticación IMS.
* Se ha corregido un problema de seguridad para reforzar la protección contra los problemas de falsificación de solicitudes del lado del servidor (SSRF). (NEO-27777)




## ![](assets/do-not-localize/red_2.png) Versión 20.1.3 - Compilación 9124{#release-20-1-3-build-9124}

_miércoles, 6 de mayo de 2020_

* Se ha corregido un problema con la actividad **File Transfer** que impedía que la autenticación basada en claves SFTP funcionara en Debian 9. (NEO-23183)

## ![](assets/do-not-localize/red_2.png) Versión 20.1.2: compilación 9123{#release-20-1-2-build-9123}

_viernes, 13 de marzo de 2020_

* Se ha corregido un problema que impedía la implementación de versiones en servidores de Red Hat 7. (NEO-23332)

## ![](assets/do-not-localize/red_2.png) Versión 20.1: compilación 9122{#release-20-1-build-9122}

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
    <p>Para obtener más información, consulte la <a href="../../installation/using/configure-fda-snowflake.md">documentación detallada</a> y el <a href="https://docs.adobe.com/content/help/es/campaign-classic-learn/tutorials/administrating/fda/big-data-segmentation-on-snowflake.html">videotutorial</a>.</p>
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

* Se ha añadido una nueva opción en las actividades de flujo de trabajo de **código JavaScript** y de **código JavaScript avanzado** para definir un período de tiempo de espera. Esto evita que la fase de ejecución de javascript se realice durante demasiado tiempo. Si transcurre el tiempo de espera, el flujo de trabajo se detiene. El tiempo de espera predeterminado es 1 hora. [Más información](../../workflow/using/sql-code-and-javascript-code.md)

* El análisis de envío ahora se detiene cuando no se encuentra ninguna afinidad coincidente en el servidor intermediario y se muestra el mensaje de error correspondiente.

* Ahora se admite la conmutación por error de base de datos para Postgres: cuando el servidor de la base de datos se bloquea y se reinicia, Campaign ahora se vuelve a conectar automáticamente.

* La vista **Start Pending** se ha añadido al nodo Administration > Audit > Workflows Status. Esto permite supervisar todos los flujos de trabajo de la instancia que están a la espera de ser iniciados por el proceso **operationMgt**. Esta vista viene con el paquete de campañas de marketing. [Más información](../../workflow/using/monitoring-workflow-execution.md#filtering-workflows-status)

**Otros cambios**

* En Linux, el inicio del servicio nlserver ahora utiliza una unidad sistémica en lugar de la secuencia de comandos /etc/init.d/nlserver6. La migración al nuevo esquema de inicio se realiza automáticamente al instalar el paquete 20.1. Aún se proporciona el /etc/init.d/nlserver6; sin embargo, para interactuar con el servicio nlserver (inicio, reinicio, parada, etc.), se recomienda utilizar el comando systemctl directamente.

* Las tablas personalizadas más consumidoras se han movido de la secuencia **xtkNewId** a secuencias dedicadas. [Más información](https://helpx.adobe.com/es/campaign/kb/sequence_auto_generation.html#Switchtoadedicatedsequence)

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
