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
source-git-commit: 8d6e3118dc498096283d54713725071e0906aba3

---


# Última versión{#latest-release}

[Generar actualización](https://helpx.adobe.com/campaign/kb/acc-build-upgrade.html) | [Versiones](https://docs.adobe.com/content/help/en/control-panel/using/release-notes.html) del Panel de control| Actualizaciones [de documentación](../../rn/using/documentation-updates.md) | Versiones [anteriores](../../rn/using/release--19-2.md) | Funciones [obsoletas](https://helpx.adobe.com/campaign/kb/deprecated-and-removed-features.html)

<table> 
 <tbody> 
  <tr> 
   <td><img src="assets/green3.png"/><strong>Disponibilidad general</strong></td>
   <td><img src="assets/blue3.png"/><strong>Liberar candidato</strong></td> 
   <td><img src="assets/orange3.png"/><strong>Ya no está disponible</strong></td> 
   <td><img src="assets/red3.png"/><strong>Obsoleto</strong></td> 
  </tr> 
   <tr> 
   <td>Última compilación estable disponible. Compilación validada en producción.<br> </td>
   <td>Compilación validada por Adobe. Esperando pruebas de producción.<br> </td>
   <td>Nueva compilación disponible con correcciones de errores. Se requiere la actualización.<br> </td>
   <td>Contiene regresiones conocidas. La actualización es obligatoria.<br> </td>
  </tr> 
 </tbody> 
</table>

La **última compilación** estable es 9032 (205c981c3). Haga clic [aquí](../../rn/using/release--19-1.md#release-19-1-4-build-9032)

## ![](assets/blue_2.png) Versión 20.1.2: compilación 9123 {#release-20-1-2-build-9123}

_13 de marzo de 2020_

* Se ha corregido un problema que impedía la implementación de versiones en servidores de Red Hat 7. (NEO-23332)

## ![](assets/orange_2.png) Versión 20.1 - Versión 9122 {#release-20-1-build-9122}

_17 de febrero de 2020_

**Novedades**

<table> 
 <thead> 
  <tr> 
   <th> <strong>Conector FDA de copo de nieve</strong><br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> <p>Snowflake es un almacén de datos en la nube completamente gestionado, diseñado para escalar tanto en almacenamiento como en equipos. Con este nuevo conector, Adobe Campaign ahora puede aprovechar el poder de Snowflake para realizar la segmentación de datos importantes. Este conector está disponible para todos los clientes, incluido Adobe.</p>
    <p>For more information, refer to the <a href="../../platform/using/specific-configuration-database.md#configure-access-to-snowflake">detailed documentation</a> and <a href="https://docs.adobe.com/content/help/en/campaign-learn/campaign-classic-tutorials/administrating/fda/big-data-segmentation-on-snowflake.html">tutorial video</a>.</p>
   </td> 
  </tr> 
 </tbody> 
</table>

<table> 
 <thead> 
  <tr> 
   <th> <strong>Mejoras en el conector Hadoop FDA</strong><br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> <p>El conector Hadoop FDA ha sido mejorado para admitir tanto Hadoop 3.0 como Cloudera.</p>
    <p>Para obtener más información, consulte la <a href="../../platform/using/specific-configuration-database.md#configure-access-to-hadoop-3">documentación detallada</a>.</p>
   </td> 
  </tr> 
 </tbody> 
</table>

**Mejoras de seguridad**

* Se ha mejorado la seguridad en la configuración de informes para evitar el secuestro de clics. Esto se aplica a los nuevos informes. Para los informes antiguos, debe volver a publicarlos para aplicar los cambios. (NEO-13282)

* Se ha corregido un pequeño problema de memoria en cryptString. (NEO-20071)

* Se mejoró el JSP del monitor para corregir una divulgación de IP interna. (NEO-16821)

* Se corrigió un problema en el cual la información de seguimiento de pila se podía mostrar a usuarios que no fueran administradores. (NEO-12388)

* Se ha mejorado la administración de los datos almacenados en caché de sesiones anteriores. (NEO-17039)

* Se ha corregido un problema que impedía que el archivo logins.log registrara los intentos de inicio de sesión correctos a través de IMS. (NEO-11004)

**Mejoras**

* iOS 13 ahora es compatible con el conector HTTP2.

* Se ha mejorado la gestión de cuarentena y la limpieza de las tablas utilizadas por la función de notificación push (nms:address y nms:appSubscriptionRcp). Para iOS (sólo conector HTTP2), los tokens desactivados ahora se gestionan del mismo modo que para Android. El indicador disable ahora se establece en la tabla NmsAppSubscriptionRcp. [Más información](../../production/using/database-cleanup-workflow.md#subscription-cleanup--nmac-)

* Se ha agregado una nueva opción en el código **** JavaScript y en las actividades de flujo de trabajo de código **JavaScript** avanzado para definir un período de tiempo de espera. Esto evita que la fase de ejecución de javascript se ejecute durante demasiado tiempo. Si el período de tiempo de espera dura, el flujo de trabajo se detiene. El tiempo de espera predeterminado es 1 hora. [Más información](../../workflow/using/sql-code-and-javascript-code.md)

* El análisis de entrega ahora se detiene cuando no se encuentra ninguna afinidad coincidente en el servidor de abastecimiento intermedio, y se muestra el mensaje de error correspondiente.

* Ahora se admite la conmutación por error de base de datos para Postgres: cuando el servidor de la base de datos se bloquea y se reinicia, Campaign se vuelve a conectar automáticamente a él.

* La vista **Iniciar pendiente** se ha agregado al nodo Administración > Auditoría > Estado de flujos de trabajo. Esto le permite supervisar todos los flujos de trabajo de la instancia que están esperando a iniciarse en el proceso **operationMgt** . Esta vista se incluye con el paquete de campañas de marketing. [Más información](../../workflow/using/monitoring-workflow-execution.md#filtering-workflows-status)

**Otros cambios**

* En Linux, el inicio del servicio nlserver ahora utiliza una unidad sistémica en lugar de la secuencia de comandos /etc/init.d/nlserver6. La migración al nuevo esquema de inicio se realiza automáticamente al instalar el paquete 20.1. El /etc/init.d/nlserver6 aún se proporciona, pero para interactuar con el servicio nlserver (inicio, reinicio, parada, etc.), le recomendamos que utilice el comando systemctl directamente.

* Las tablas personalizadas más consumidoras se han movido de la secuencia **xtkNewId** a secuencias dedicadas. [Más información](https://helpx.adobe.com/campaign/kb/sequence_auto_generation.html#Switchtoadedicatedsequence)

* Se mejoró el rendimiento de la consulta, lo que podría verse afectado por conexiones de base de datos innecesarias.

* Se ha mejorado el rendimiento del asistente para la actualización de la base de datos.

* Se mejoró la administración de registros de la base de datos.

* Se ha mejorado la solidez del grupo de conexiones, lo que puede evitar que se produzcan fallos de conexión inesperados con demasiada frecuencia.

* Se han mejorado las reglas de validación de direcciones de correo electrónico para enviar una dirección a cuarentena en caso de error suave. [Más información](../../delivery/using/understanding-quarantine-management.md#soft-error-management)

* Para Debian, Campaign ahora utiliza bibliotecas PCRE del sistema cuando están disponibles.

* Campaign ahora permite el uso de una biblioteca ODBC del sistema más reciente.

* Se ha agregado un tiempo de espera al servlet LINE al abrir una conexión para cargar una imagen enriquecida. Si la imagen tarda demasiado en cargarse, el servlet detiene la conexión para evitar un cuello de botella.

**Parches**

* Se corrigió un problema de cifrado de clave de cuenta al usar el conector Hadoop.

* Se ha corregido un problema de regresión debido a la implementación de la certificación SSL que provocaba que la conexión del usuario fallara en el servidor de Windows. (NEO-20629)

* Se ha corregido un problema con la actividad de consulta incremental en el caso de ID de flujo de trabajo negativos. (NEO-19779)

* Se corrigió un problema de codificación al ejecutar consultas mediante el conector FDA de Netezza. (NEO-19594)

* Se ha corregido un problema que provocaba un error al usar el método POST en la actividad de evento de flujo de trabajo de descarga **** web.

* Se ha corregido un problema con la generación de propuestas de ofertas. (NEO-18176)

* Se corrigió un problema de visualización de pie de página al usar la plantilla de formulario web de adquisición.

* Se ha corregido un problema al analizar las direcciones URL en el contenido de los envíos continuos que podía provocar que se bloquearan. (NEO-16910)

* Se ha corregido un problema por el que los campos **Inicio** y **Fin** no se calculaban al crear una nueva campaña.

* Se ha corregido un problema con la actividad de flujo de trabajo de descarga **de** archivos al usar una dirección URL.

* Se corrigió un problema al obtener una vista previa de una lista importada en una actividad de consulta de un informe. (NEO-13119)

* Se ha corregido un problema que mostraba una imagen desactualizada al seleccionar el bloque de personalización **Powered by Campaign** en el editor de correo electrónico.

* Se ha mejorado la comunicación de red entre el cliente y el servidor.

* Se corrigió un problema en el cual se creaban demasiados flujos de trabajo en la misma campaña. Ahora no puede crear más de 28 flujos de trabajo. Se muestra una advertencia.

* Se ha corregido un problema al usar la opción **Una selección de reconciliación de columnas** en una actividad de flujo de trabajo de **Unión** .

* Se ha corregido un problema de bloqueo de la consola que se producía al usar una lista de enriquecimiento dañada en un flujo de trabajo. (NEO-18096)

* Se han corregido varios problemas de bloqueo de la consola que podían producirse en los flujos de trabajo (NEO-18010, NEO-18032)

* Se ha corregido un problema que permitía la ejecución de una actividad de flujo de trabajo de señal **** externa incluso cuando estaba desactivada. (NEO-17524)

* Se corrigió un problema al crear un nuevo esquema.

* Se ha corregido un problema de seguimiento al enviar mensajes SMS. (NEO-19595)

* Se ha corregido un problema que mostraba un número de audiencia objetivo incorrecto en los indicadores de entrega.

* Se ha corregido un problema que mostraba porcentajes incorrectos al generar un informe descriptivo mediante una actividad de flujo de trabajo. (NEO-14314)

* Se ha corregido un problema que hacía que el informe de rendimiento de entrega mostrara números diferentes cuando se utilizaba el parámetro de vista de tiempo. (NEO-11783)

* Se ha corregido un problema que impedía que el flujo de trabajo de seguimiento actualizara los indicadores de seguimiento de mensajes transaccionales. (NEO-17770)

* Se ha corregido un problema de regresión que provocaba que el proceso web se bloqueara y se reiniciara al solicitar una oferta a través de SOAP. (NEO-19482)

* Se ha corregido un problema que impedía cargar datos en recursos públicos si el directorio de carga era una ubicación compartida remota. (NEO-19361)

* Se ha corregido un problema que provocaba que las audiencias de **importación del flujo de trabajo técnico de Adobe Experience Cloud** fallaran constantemente. (NEO-18463)

* Se ha corregido un problema que impedía que los envíos se enviaran al utilizar plantillas importadas desde Experience Manager. (NEO-17540)

* Se ha corregido un problema que se producía tras actualizar a la compilación 9032 y evitar que la instancia se conectara al servidor FTP a través del protocolo SSL. (NEO-20498)

* Se ha corregido un problema que se producía al eliminar, insertar o actualizar una gran cantidad de datos con la actividad **Actualizar datos** en un flujo de trabajo mediante un esquema FDA como dimensión de objetivo. (NEO-13280)

* Se ha corregido un problema que impedía que se enviaran correos electrónicos al usar la instrucción &#39;if&#39; fuera de la `body` etiqueta .

* Se ha corregido un problema que se producía al intentar mostrar la página reflejada desde los registros de entrega de un mensaje enviado. (NEO-17976)

* Se ha corregido un problema que impedía que el bloque de personalización de **Vínculo a página** reflejada se mostrara en la ficha Contenido **de** texto después de hacer clic en **Importar HTML** en un envío. (NEO-17568)

* Se ha aclarado el mensaje de error que se muestra al hacer clic en un vínculo a una página reflejada que ha caducado. (NEO-17340)

* Se ha corregido un problema que impedía que se usaran algunos botones en la pantalla de creación de distribución **de** datos.

* Se ha corregido un problema que se producía al programar una actividad de entrega en una instancia con Asia y Calcuta como huso horario. (NEO-20001)

* Ahora se muestra un error cuando una entrega tiene un problema de configuración de afinidad.

* Se ha corregido un problema que mostraba un número de etiqueta de versión incorrecto en el menú **Acerca de** .

* Se ha corregido un problema que se producía al intentar actualizar la cuenta de enrutamiento desde las propiedades de una entrega recurrente en un flujo de trabajo. (NEO-18684)

* Se ha corregido un problema que se producía al conectarse a la instancia a través del módulo de redirección, lo que impedía que la conexión se limpiara correctamente una vez cerrada.
