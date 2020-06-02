---
title: Seguimiento de una entrega
seo-title: Seguimiento de una entrega
description: Seguimiento de una entrega
seo-description: null
page-status-flag: never-activated
uuid: 7cb409eb-a01c-4b4d-bb62-760e0bafdc8a
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: delivery
content-type: reference
topic-tags: monitoring-deliveries
discoiquuid: 3aab3d47-76fd-4c68-add4-9c14240c936e
index: y
internal: n
snippet: y
translation-type: ht
source-git-commit: fcedad248169f53e716f2bd8b1b141fbf1f4d189
workflow-type: ht
source-wordcount: '2602'
ht-degree: 100%

---


# Seguimiento de una entrega{#monitoring-a-delivery}

El **panel de entrega** es fundamental para controlar las entregas y los problemas que puedan ser detectados durante la entrega de mensajes.

**Temas relacionados:**

* [Comprensión de los errores de entrega](../../delivery/using/understanding-delivery-failures.md)
* [Compresión de la gestión de la cuarentena](../../delivery/using/understanding-quarantine-management.md)
* [Prácticas recomendadas relacionadas con las entregas](https://helpx.adobe.com/es/campaign/kb/delivery-best-practices.html)
* [Administración de envíos](../../delivery/using/about-deliverability.md)

## Panel de entregas {#delivery-dashboard}

Para ver la información de una entrega, editarlo, ver el panel y hacer clic en las pestañas disponibles.

El contenido de las pestañas no se puede cambiar una vez realizado la entrega.

![](assets/s_ncs_user_del_details.png)

### Resumen de entregas {#delivery-summary}

La pestaña **[!UICONTROL Summary]** contiene las características de la entrega: estado de entrega, canal utilizado, información sobre el remitente, asunto, información sobre la ejecución. Para obtener más información, consulte [Número de mensajes enviados](#number-of-messages-sent).

El vínculo **[!UICONTROL reports]** le permite ver un conjunto de informes relativos a la acción de entrega: informe de entrega general, informe detallado, informe de entrega, distribución de mensajes fallidos, tasa de apertura, clics y transacciones, etc. El contenido de esta pestaña se puede configurar según sus necesidades. Para obtener más información, consulte [esta sección](../../reporting/using/delivery-reports.md).

### “Logs” de entrega e historial{#delivery-logs-and-history}

La pestaña **[!UICONTROL Delivery]** ofrece un historial de los sucesos en esta entrega. Contiene los “logs” de entrega, es decir. la lista de mensajes enviados y su estado y los mensajes asociados.

Para una entrega, puede mostrar, por ejemplo, solo los destinatarios con una entrega fallido o una dirección en cuarentena. Para ello, haga clic en el botón **[!UICONTROL Filters]** y seleccione **[!UICONTROL By state]**. Seleccione el estado en la lista desplegable.

![](assets/s_ncs_user_delivery_delivery_tab.png)

En [esta página](#delivery-statuses) se enumeran varios estados.

>[!NOTE]
>
>El enlace **[!UICONTROL Display the mirror page for this message...]** permite ver la página espejo del contenido del envío seleccionado en la lista en una nueva ventana. La página espejo solo está disponible para las entregas para los que se ha definido contenido HTML. Para obtener más información, consulte [Generación de la página espejo](../../delivery/using/sending-messages.md#generating-the-mirror-page).

### “Logs” de seguimiento{#tracking-logs}

La pestaña **[!UICONTROL Tracking]** enumera el historial de seguimiento de esta entrega. Esta pestaña muestra los datos de seguimiento de los mensajes enviados, es decir, todas las direcciones URL sobre las que Adobe Campaign realiza un seguimiento. Los datos de seguimiento se actualizan cada hora.

>[!NOTE]
>
>Si el seguimiento no está habilitado para una entrega, esta pestaña no se muestra.

La configuración de seguimiento se realiza en el escenario adecuado del asistente de envíos. Consulte [Configuración de los vínculos rastreados](../../delivery/using/how-to-configure-tracked-links.md).

Los datos de **[!UICONTROL Tracking]** se interpretan en los informes de envío. Consulte [esta sección](../../reporting/using/delivery-reports.md).

![](assets/s_ncs_user_delivery_tracking_tab.png)

### Auditoría de entrega {#delivery-audit-}

La pestaña **[!UICONTROL Audit]** contiene el registro de entrega y todos los mensajes correspondientes a las pruebas. El botón **[!UICONTROL Refresh]** permite actualizar los datos. Utilice el botón **[!UICONTROL Filters]** para definir un filtro en los datos.

Los iconos especiales permiten identificar errores o advertencias. Consulte [Análisis de la entrega](../../delivery/using/steps-validating-the-delivery.md#analyzing-the-delivery).

La subpestaña **[!UICONTROL Proofs]** permite ver la lista de pruebas que se han enviado.

![](assets/s_ncs_user_delivery_log_tab.png)

Puede modificar la información mostrada en esta ventana (y la de las pestañas **[!UICONTROL Delivery]** y **[!UICONTROL Tracking]**) seleccionando las columnas que desea mostrar. Para ello, haga clic en el icono **[!UICONTROL Configure list]** situado en la esquina inferior derecha. Para obtener más información sobre la configuración de listas, consulte [esta sección](../../platform/using/adobe-campaign-workspace.md#configuring-lists).

### Sincronización del panel de entregas {#delivery-dashboard-synchronization}

En el panel de entregas, se recomienda comprobar los mensajes procesados y los “logs” de entrega para asegurarse de que su entrega se haya realizado correctamente.

Algunos indicadores o estados pueden ser incorrectos o no estar actualizados; esto puede resolverse con las soluciones siguientes:

* Si su estado de entrega es incorrecto, compruebe que se hayan realizado todas las aprobaciones necesarias para esta entrega o que los flujos de trabajo de **[!UICONTROL operationMgt]** y **[!UICONTROL deliveryMgt]** se estén ejecutando sin errores. Esto también se puede deber a que la entrega mediante una afinidad no está configurado en la instancia del emisor.
* Si los indicadores de envío aún se encuentran en 0 y si se encuentra en una configuración intermediaria, consulte el flujo de trabajo técnico **[!UICONTROL Mid-sourcing (delivery counters)]**. Inícielo si su estado no es **[!UICONTROL Started]**. A continuación, puede intentar volver a calcular los indicadores haciendo clic con el botón derecho en la entrega correspondiente en el explorador de Adobe Campaign y seleccionando **[!UICONTROL Actions]** > **[!UICONTROL Recompute delivery and tracking indicators]**. Para obtener más información sobre los indicadores de seguimiento, consulte [esta sección](../../reporting/using/delivery-reports.md#tracking-indicators).
* Si el contador de envío no coincide con su envío, intente volver a calcular los indicadores haciendo clic con el botón derecho en el envío correspondiente del explorador de Adobe Campaign y seleccionando **[!UICONTROL Actions]** > **[!UICONTROL Recompute delivery and tracking indicators]** para volver a sincronizar. Para obtener más información sobre los indicadores de seguimiento, consulte [esta sección](../../reporting/using/delivery-reports.md#tracking-indicators).
* Si el contador de envío no está actualizado para las implementaciones intermediarias, compruebe que se esté ejecutando el flujo de trabajo técnico **[!UICONTROL Mid-Sourcing (Delivery counters)]**. Para obtener más información, consulte [esta página](../../installation/using/mid-sourcing-deployment.md).

También puede rastrear las entregas con diferentes informes a través del panel de entrega. Para obtener más información, consulte [esta sección](../../reporting/using/delivery-reports.md).

## Problemas de rendimiento {#performance-issues}

### Lista de comprobación {#checklist-}

Si los resultados de la entrega son malos, puede comprobar:

* **El tamaño de la entrega**: Las entregas grandes pueden tardar más en completarse. Los elementos MTA secundarios se configuran para gestionar un tamaño predeterminado que funciona con la mayoría de las instancias, pero es necesario comprobar si las entregas son constantemente lentos.
* **El destinatario de la entrega**: El rendimiento de las entregas se puede ver afectado por errores de rechazos leves que se gestionan según la configuración de reintento. Cuanto mayor sea el número de errores, más necesarios son los reintentos de entrega.
* **La carga de la plataforma general**: Cuando se envían varias entregas de gran tamaño, la plataforma general se puede ver afectada. También puede comprobar los problemas de reputación de la IP y de capacidad de entrega. Para obtener más información, consulte la [Guía de prácticas recomendadas de entrega](https://docs.adobe.com/content/help/es-ES/campaign-classic/using/sending-messages/deliverability-management/about-deliverability.html) de Adobe Campaign y [esta página](../../delivery/using/about-deliverability.md).

El mantenimiento de la plataforma y de la base de datos también puede afectar el rendimiento de las entregas. Para obtener más información, consulte [esta página](../../production/using/database-performances.md).

### Entregas lentas {#slow-deliveries}

Tras hacer clic en el botón **[!UICONTROL Send]**, la entrega parece tardar más de lo normal. Esto puede deberse a diferentes elementos:

* Algunos proveedores de correo electrónico pueden incluido sus direcciones IP en una lista negra. En este caso, compruebe sus broadlogs y consulte [esta introducción](https://docs.adobe.com/content/help/es-ES/campaign-classic/using/sending-messages/deliverability-management/about-deliverability.html).
* Su entrega puede ser demasiado grande como para procesarlo rápidamente, como puede ser el caso de una alta personalización de JavaScript o si su entrega pesa más de 60 kB. Consulte las [prácticas recomendadas relacionadas con las entregas](https://helpx.adobe.com/es/campaign/kb/delivery-best-practices.html) de Adobe Campaign para obtener más información sobre las directrices de contenido.
* Es posible que se haya activado una restricción dentro del MTA de Adobe Campaign. Esto se debe a:

   * Mensajes pendientes (mensaje **[!UICONTROL quotas met]**): se han cumplido las cuotas declaradas por las reglas de MX definidas en Campaign. Para obtener más información sobre este mensaje, consulte [esta página](https://helpx.adobe.com/es/campaign/kb/acc-deliverability-faq.html#FAQ). Para obtener más información sobre las reglas MX, consulte [esta página](../../delivery/using/technical-recommendations.md#mx-rules).
   * Mensajes pendientes (mensaje **[!UICONTROL dynamic flow control]**): El MTA de Campaign ha detectado errores al intentar enviar mensajes para un ISP determinado, lo que provoca una ralentización para evitar una gran densidad de errores y, por lo tanto, la posible inclusión en una lista negra.

* Un problema del sistema puede impedir que los servidores interactúen: esto puede ralentizar todo el proceso de entrega. Compruebe los servidores para asegurarse de que no hay problemas de memoria o recursos que puedan afectar a Campaign en el proceso de obtención de los datos personalizados, por ejemplo.

### Prácticas recomendadas para el rendimiento {#best-practices-performance}

* Evite mantener las entregas en estado de error en la instancia, ya que esto mantiene tablas temporales e influye en el rendimiento.

* Elimine las entregas que ya no sean necesarios.

* Destinatarios inactivos en los últimos 12 meses que se deben eliminar de la base de datos para mantener la calidad de la dirección.

* Evite programar entregas grandes al mismo tiempo. Hay un lapso de 5 a 10 minutos para distribuir la carga de manera uniforme en el sistema. Coordine la programación de las entregas con los demás miembros de su equipo para garantizar el mejor rendimiento. Cuando el servidor de marketing gestiona muchas tareas diferentes al mismo tiempo, puede ralentizar el rendimiento.

* Mantenga el tamaño de sus correos electrónicos lo más bajo posible. El tamaño máximo recomendado de un correo electrónico es de unos 35 KB. El tamaño de una entrega por correo electrónico genera una cierta cantidad de volumen en los servidores de entrega.

* Las entregas grandes, como las entregas a más de un millón de destinatarios, necesitan espacio en las colas de entrega. Esto por sí solo no es un problema para el servidor, pero cuando se combina con docenas de entregas grandes que se realizan al mismo tiempo, puede provocar un retraso en la entrega.

* La personalización en correos electrónicos extrae datos de la base de datos de cada destinatario. Si hay muchos elementos de personalización, esto aumenta la cantidad de datos necesarios para preparar la entrega.

* Direcciones de índice. Para optimizar el rendimiento de las consultas SQL utilizadas en la aplicación, se puede declarar un índice a partir del elemento principal del esquema de datos.

>[!NOTE]
>
>Los ISP desactivarían las direcciones después de un periodo de inactividad. Los mensajes rechazados se envían a los remitentes para informarles sobre este nuevo estado.

## Estados de entrega {#delivery-statuses}

Al realizar una entrega, es posible que aparezca el siguiente estado en su panel de entregas:

<table> 
 <thead> 
  <tr> 
   <th> Estado<br /> </th> 
   <th> Definiciones y soluciones<br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> No aplicable<br /> </td> 
   <td> El servidor (MTA) tuvo en cuenta la entrega, pero no lo procesó.<br /> </td> 
  </tr> 
  <tr> 
   <td> Ignorado<br /> </td> 
   <td> No se realizó la entrega al destinatario debido a un error con su dirección. Se lo incluyó en una lista negra o en cuarentena, no se proporcionó o está duplicado. <br /> </td> 
  </tr> 
  <tr> 
   <td> Enviado<br /> </td> 
   <td> La entrega se envió correctamente al proveedor de mensajes (pero es posible que el destinatario no lo haya recibido).<br /> </td> 
  </tr> 
  <tr> 
   <td> Error<br /> </td> 
   <td> La entrega no ha podido llegar al destinatario debido a una dirección no válida o a que la bandeja de entrada estaba llena. También puede estar relacionado con un problema con los bloques de personalización, ya que pueden generar errores cuando los esquemas no coinciden con la asignación de entregas. Consulte <a href="#failed-status" target="_blank">Estado fallido</a><br />. </td> 
  </tr> 
  <tr> 
   <td> Tenido en cuenta por el proveedor de servicios<br /> </td> 
   <td> El proveedor de servicios SMS recibió la entrega.<br /> </td> 
  </tr> 
  <tr> 
   <td> Se ha recibido en dispositivos móviles<br /> </td> 
   <td> El destinatario recibió el SMS en su dispositivo móvil.<br /> </td> 
  </tr> 
  <tr> 
   <td> Pendiente<br /> </td> 
   <td> la entrega está listo para enviarse y se va a procesar mediante el servidor de entrega (MTA). Consulte <a href="#pending-status" target="_blank">Estado pendiente</a>.<br /> </td> 
  </tr> 
  <tr> 
   <td> Entrega cancelada<br /> </td> 
   <td> Un operador ha cancelado la entrega.<br /> </td> 
  </tr> 
  <tr> 
   <td> Preparado<br /> </td> 
   <td> El estado de intermediario se utiliza solo para conectores externos como el canal móvil. Sigue al estado “Pendiente” y es el conector externo que determina el estado siguiente.<br /> </td> 
  </tr> 
  <tr> 
   <td> Enviado al proveedor de servicios<br /> </td> 
   <td> Se realizó la entrega al proveedor de servicios SMS, pero no se ha recibido todavía.<br /> </td> 
  </tr> 
 </tbody> 
</table>

Para aprender a optimizar la entrega de los correos electrónicos de Adobe Campaign, consulte la [Guía de prácticas recomendadas de entrega](https://docs.adobe.com/content/help/es-ES/campaign-classic/using/sending-messages/deliverability-management/about-deliverability.html) de Adobe Campaign y [esta página](../../delivery/using/about-deliverability.md).

### Estado pendiente {#pending-status}

Después de confirmar la entrega, puede ver que el estado del mismo es **[!UICONTROL Pending]**. Este estado significa que el proceso de ejecución está esperando a que estén disponibles algunos recursos.

El estado **[!UICONTROL Pending]** puede significar en primer lugar que la entrega se ha programado y está pendiente hasta la fecha determinada. Para obtener más información, consulte la sección [Programación de entregas](../../delivery/using/steps-sending-the-delivery.md#scheduling-the-delivery-sending).

Si la entrega no se realiza y su estado sigue siendo **[!UICONTROL Pending]**, puede deberse a uno de los siguientes motivos:

* Puede que el MTA (Agente de Transferencia de Mensajes), que ejecuta módulos y procesos en el servidor de entrega y que administra la entrega por correo electrónico, no se haya iniciado o que sea necesario reiniciarlo. Para comprobar esto e iniciar el módulo si es necesario, aplique los siguientes pasos:

   * Compruebe que los módulos `mta@<instance>` se inicien en los servidores MTA.

   ```
   nlserver pdump
   HH:MM:SS > Application server for Adobe Campaign Classic (X.Y.Z YY.R build nnnn@SHA1) of DD/MM/YYYY
   [...]
   mta@<INSTANCENAME> (9268) - 23.0 Mb
   [...]
   ```

   * Si el MTA no aparece en la lista, inícielo con el siguiente comando:

   ```
   nlserver start mta@<INSTANCENAME>
   ```

   >[!NOTE]
   >
   >Sustituya `<INSTANCENAME>` con el nombre de su instancia (producción, desarrollo, etc.). El nombre de instancia se identifica mediante los archivos de configuración: `[path of application]nl6/conf/config-<INSTANCENAME>.xml`

* La entrega puede estar utilizando una afinidad no configurada en el servidor remitente. En este caso, compruebe la configuración de la administración de tráfico (afinidad de IP) y utilice el campo **[!UICONTROL Managing affinities with IP addresses]** para relacionar las entregas al MTA que administra la afinidad. Para obtener más información sobre las afinidades, consulte [esta sección](../../installation/using/configuring-campaign-server.md#personalizing-delivery-parameters).
* Cuando la preparación de la entrega está pendiente, puede haber demasiadas campañas activas, lo cual bloquea la actualización del estado de la entrega. Para resolver esto, vaya a **[!UICONTROL Options]** y aumente el valor de **[!UICONTROL NmsOperation_LimitConcurrency]** (el valor predeterminado es 10). No ejecute más campañas que el valor asignado en esta opción específica.

### Estado de error {#failed-status}

Si el estado de una entrega de correo electrónico es **[!UICONTROL Failed]**, puede deberse a un problema con bloques de personalización. Los bloques personalizados en una entrega pueden generar errores cuando los esquemas no coinciden con la asignación de entregas, por ejemplo.

Los “logs” de entrega son esenciales para saber por qué ha fallado una entrega. Estos son los posibles errores que puede detectar en los “logs” de entrega:

* Si los mensajes del destinatario fallan con un error “No accesible” que indica: **Error while compiling script &#39;content htmlContent&#39; line X:`[table]`is not defined. JavaScript: error al evaluar el script &#39;contenido htmlContent**, la causa de este problema es casi siempre una personalización dentro del HTML que intenta llamar a una tabla o campo que no se ha definido o asignado en el objetivo ascendente o en el destino de mapeo de la entrega.

   Para corregir esto, es necesario revisar el flujo de trabajo y el contenido de la entrega para determinar específicamente qué personalización está intentando llamar a la tabla en cuestión y si se puede asignar o no la tabla. Desde este punto, la forma de resolver el problema sería eliminar la llamada a esta tabla en el HTML o corregir la asignación a la entrega.

* En el modelo de implementación intermediaria, puede aparecer el siguiente mensaje en los registros de entrega: **Error during the call of method &#39;AppendDeliveryPart&#39; on the mid sourcing server: &#39;Communication error with the server: please check this one is correctly configured. Código HTTP 408 &#39;Servicio no disponible temporalmente&#39;**.

   La causa está relacionada con problemas de rendimiento. Significa que la instancia de marketing invierte demasiado tiempo creando datos antes de enviarlos al servidor de mid-sourcing.

   Para resolver esto, recomendamos realizar una limpieza y reindexar la base de datos. Para obtener más información sobre el mantenimiento de la base de datos, consulte [esta sección](../../production/using/recommendations.md).

   También debe reiniciar todos los flujos de trabajo con una actividad programada y todos los flujos de trabajo en estado fallido. Consulte [esta sección](../../workflow/using/scheduler.md).

* Cuando falla una entrega, puede aparecer el siguiente error en los registros de entrega: **DLV-XXXX The count of message prepared (123) is greater than the number of messages to send (111). Póngase en contacto con el servicio técnico.**

   Normalmente, este error significa que existe un campo o un bloque personalizado dentro del correo electrónico que tiene más de un valor para el destinatario. Se está utilizando un bloque personalizado que está recuperando más de un registro para un destinatario determinado.

   Para resolver esto, compruebe los datos personalizados utilizados y, a continuación, compruebe el objetivo de los destinatarios que tengan más de una entrada para cualquiera de esos campos. También puede utilizar una actividad **[!UICONTROL Deduplication]** en el flujo de trabajo de objetivos antes de la actividad de entrega para comprobar que solo hay un campo de personalización a la vez. Para obtener más información sobre la deduplicación, consulte [esta sección](../../workflow/using/deduplication.md).

* Algunas entregas pueden fallar con un error “Inaccesible” que indica: “Inbound email bounce (rule &#39;Auto_replies&#39; has matched this bounce)”. Esto significa que la entrega se realizó correctamente, pero Adobe Campaign recibió un mensaje de respuesta automática del destinatario (por ejemplo, “fuera de la oficina”) que coincidió con las reglas de correo electrónico entrante de “respuesta automática”. Adobe Campaign ignora el correo electrónico de respuesta automática y la dirección del destinatario no se pone en cuarentena.

**Temas relacionados:**

* [“Logs” de entrega e historial](#delivery-logs-and-history)
* [Comprensión de los errores de entrega](../../delivery/using/understanding-delivery-failures.md)
* [Tipos y motivos de errores de entrega](../../delivery/using/understanding-delivery-failures.md#delivery-failure-types-and-reasons)

## Número de mensajes enviados {#number-of-messages-sent}

Puede acceder a las entregas desde la lista de entregas a través del nodo **[!UICONTROL Campaign Management > Deliveries]** del árbol.

De forma predeterminada, la lista de entregas contiene los nombres y estados de las entregas creados en el nodo seleccionado. También muestra el número de mensajes que se van a enviar, procesados y enviados con éxito.

* El número de **[!UICONTROL Messages to send]** corresponde al número de destinatarios objetivo tras realizar el análisis y antes de la entrega.
* El número de mensajes de la columna **[!UICONTROL Success]** corresponde al número de mensajes que envía el servidor y que reciben los destinatarios.
* El número de mensajes **[!UICONTROL Processed]** corresponde al número de mensajes recibidos más el número de mensajes con errores.

El panel de entrega permite rastrear la cantidad de mensajes enviados.

>[!NOTE]
>
>Para las entregas grandes, quizá desee actualizar estos valores. Para ello, seleccione la entrega en cuestión y, a continuación, haga clic con el botón derecho del ratón. Seleccione **[!UICONTROL Action > Recompute delivery and tracking indicators...]** y, a continuación, utilice el asistente para actualizar esta información.

## Entregas programadas {#scheduled-deliveries-}

Si las entregas no se ejecutan en la fecha programada exacta, puede deberse a una diferencia entre las zonas horarias de los servidores. La instancia de mid-sourcing y la instancia de producción pueden estar en diferentes zonas horarias.

Por ejemplo, si la instancia de mid-sourcing se encuentra en el huso horario de Brisbane y la instancia de producción está en el huso horario de Darwin, ambas zonas horarias están separadas por media hora, por lo que en el “log” de auditoría puede claramente que si la entrega está programado para su producción a las 11:56, la misma entrega programada de mid-sourcing se produciría a las 12:26, lo que supone una diferencia de media hora.
