---
title: Seguimiento de un envío
seo-title: Seguimiento de un envío
description: Seguimiento de un envío
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
translation-type: tm+mt
source-git-commit: f7655cd93a7dc8ecd35cd379da350ad279cae725

---


# Seguimiento de un envío{#monitoring-a-delivery}

El **panel de envío** es fundamental para controlar los envíos y los problemas que puedan ser detectados durante el envío de mensajes.

**Temas relacionados**

* [Comprensión de los errores de envío](../../delivery/using/understanding-delivery-failures.md)
* [Compresión de la gestión de la cuarentena](../../delivery/using/understanding-quarantine-management.md)
* [Prácticas recomendadas relacionadas con los envíos](https://docs.campaign.adobe.com/doc/AC/getting_started/EN/deliveryBestPractices.html)
* [Introducción: Administración de la capacidad de entrega](https://docs.campaign.adobe.com/doc/AC/getting_started/EN/deliverability.html)

## Panel de envíos {#delivery-dashboard}

Para ver la información de un envío, editarlo, ver el panel y hacer clic en las pestañas disponibles.

El contenido de las pestañas no se puede cambiar una vez realizado el envío.

![](assets/s_ncs_user_del_details.png)

### Resumen de envíos {#delivery-summary}

The **[!UICONTROL Summary]** tab contains the characteristics of the delivery: delivery status, channel used, information about the sender, subject, information concerning execution. Para obtener más información sobre esto, consulte [Número de mensajes enviados](#number-of-messages-sent).

El **[!UICONTROL reports]** vínculo le permite ver un conjunto de informes relativos a la acción de envío: informe de entrega general, informe detallado, informe de entrega, distribución de mensajes fallidos, tasa de apertura, clics y transacciones, etc. El contenido de esta ficha se puede configurar según sus necesidades. Para obtener más información, consulte [esta sección](../../reporting/using/delivery-reports.md).

### “Logs” de envío e historial{#delivery-logs-and-history}

The **[!UICONTROL Delivery]** tab gives a history of the occurrences in this delivery. Contiene los “logs” de envío, es decir. la lista de mensajes enviados y su estado y los mensajes asociados.

Para un envío, puede mostrar, por ejemplo, solo los destinatarios con un envío fallido o una dirección en cuarentena. Para ello, haga clic en el **[!UICONTROL Filters]** botón y seleccione **[!UICONTROL By state]**. Seleccione el estado en la lista desplegable.

![](assets/s_ncs_user_delivery_delivery_tab.png)

En [esta página](#delivery-statuses) se enumeran varios estados.

>[!NOTE]
>
>The **[!UICONTROL Display the mirror page for this message...]** link lets you view the mirror page for the contents of the delivery selected from the list in a new window. La página espejo solo está disponible para los envíos para los que se ha definido contenido HTML. For more on this, refer to [Generating the mirror page](../../delivery/using/sending-messages.md#generating-the-mirror-page).

### “Logs” de seguimiento{#tracking-logs}

The **[!UICONTROL Tracking]** tab lists the tracking history for this delivery. Esta pestaña muestra los datos de seguimiento de los mensajes enviados, es decir, todas las direcciones URL sobre las que Adobe Campaign realiza un seguimiento. Los datos de seguimiento se actualizan cada hora.

>[!NOTE]
>
>Si el seguimiento no está habilitado para un envío, esta pestaña no se muestra.

La configuración de seguimiento se realiza en el escenario adecuado del asistente de envíos. See [How to configure tracked links](../../delivery/using/how-to-configure-tracked-links.md).

**[!UICONTROL Tracking]** los datos se interpretan en los informes de envío. Consulte [esta sección](../../reporting/using/delivery-reports.md).

![](assets/s_ncs_user_delivery_tracking_tab.png)

### Auditoría de envío {#delivery-audit-}

The **[!UICONTROL Audit]** tab contains the delivery log and all the messages concerning the proofs. The **[!UICONTROL Refresh]** button lets you update the data. Use the **[!UICONTROL Filters]** button to define a filter on the data.

Los iconos especiales permiten identificar errores o advertencias. Consulte [Análisis del envío](../../delivery/using/steps-validating-the-delivery.md#analyzing-the-delivery).

The **[!UICONTROL Proofs]** sub-tab lets you view the list of proofs that have been sent.

![](assets/s_ncs_user_delivery_log_tab.png)

You can modify the information displayed in this window (and that of the **[!UICONTROL Delivery]** and **[!UICONTROL Tracking]** tabs) by selecting the columns to be displayed. To do this, click the **[!UICONTROL Configure list]** icon located in the lower right-hand corner. Para obtener más información sobre la configuración de listas, consulte [esta sección](../../platform/using/adobe-campaign-workspace.md#configuring-lists).

### Sincronización del panel de envíos {#delivery-dashboard-synchronization}

En el panel de envíos, se recomienda comprobar los mensajes procesados y los “logs” de envío para asegurarse de que su envío se haya realizado correctamente.

Algunos indicadores o estados pueden ser incorrectos o no estar actualizados; esto puede resolverse con las soluciones siguientes:

* If your delivery status is incorrect, check that all necessary approvals have been done for this delivery or that the **[!UICONTROL operationMgt]** and **[!UICONTROL deliveryMgt]** workflows are running without errors. Esto también se puede deber a que el envío mediante una afinidad no está configurado en la instancia del emisor.
* If your delivery indicators are still at zero and if you are on a mid-sourcing configuration, check the **[!UICONTROL Mid-sourcing (delivery counters)]** technical workflow. Start it if its status is not **[!UICONTROL Started]**. You can then try to recompute the indicators by right-clicking the relevant delivery in the Adobe Campaign explorer and selecting **[!UICONTROL Actions]** > **[!UICONTROL Recompute delivery and tracking indicators]**. Para obtener más información sobre los indicadores de seguimiento, consulte [esta sección](../../reporting/using/reports-on-deliveries.md#tracking-indicators).
* If your delivery counter does not match your delivery, try to recompute the indicators by right-clicking the relevant delivery in the Adobe Campaign explorer and selecting **[!UICONTROL Actions]** > **[!UICONTROL Recompute delivery and tracking indicators]** to resynchronize. Para obtener más información sobre los indicadores de seguimiento, consulte [esta sección](../../reporting/using/reports-on-deliveries.md#tracking-indicators).
* If your delivery counter is not up-to-date for mid-sourcing deployments, check that the **[!UICONTROL Mid-Sourcing (Delivery counters)]** technical workflow is running. Para obtener más información, consulte [esta página](../../installation/using/mid-sourcing-deployment.md).

También puede rastrear los envíos con diferentes informes a través del panel de envío. Para obtener más información, consulte [esta sección](../../reporting/using/reports-on-deliveries.md#accessing-existing-reports).

## Problemas de rendimiento {#performance-issues}

### Lista de comprobación {#checklist-}

Si los resultados del envío son malos, puede comprobar:

* **El tamaño de la entrega**: Las entregas grandes pueden tardar más en completarse. Los elementos MTA secundarios se configuran para gestionar un tamaño predeterminado que funciona con la mayoría de las instancias, pero es necesario comprobar si los envíos son constantemente lentos.
* **El objetivo de la entrega**: La prohibición de rendimiento de entrega se ve afectada por errores de devolución en blanco, que se gestionan según la configuración de reintentos. Cuanto mayor sea el número de errores, más necesarios son los reintentos de envío.
* **Carga** general de la plataforma: Cuando se envían varias entregas grandes, la plataforma general puede verse afectada. También puede comprobar los problemas de reputación de la IP y de capacidad de envío. Para obtener más información, consulte la [Guía de prácticas recomendadas de envío](https://docs.campaign.adobe.com/doc/AC/getting_started/EN/deliverability.html) de Adobe Campaign y [esta página](../../delivery/using/about-deliverability.md).

El mantenimiento de la plataforma y la base de datos también puede afectar al rendimiento de los envíos. Para obtener más información, consulte [esta página](../../production/using/database-performances.md).

### Envíos lentos {#slow-deliveries}

After clicking the **[!UICONTROL Send]** button, your delivery seems to take longer than usual. Esto puede deberse a diferentes elementos:

* Algunos proveedores de correo electrónico pueden incluido sus direcciones IP en una lista negra. En este caso, compruebe sus broadlogs y consulte [esta introducción](https://docs.campaign.adobe.com/doc/AC/getting_started/EN/deliverability.html).
* Su envío puede ser demasiado grande como para procesarlo rápidamente, como puede ser el caso de una alta personalización de JavaScript o si su envío pesa más de 60 kB. Consulte las [prácticas recomendadas relacionadas con los envíos](https://docs.campaign.adobe.com/doc/AC/getting_started/EN/deliveryBestPractices.html) de Adobe Campaign para obtener más información sobre las directrices de contenido.
* Es posible que se haya activado una restricción dentro del MTA de Adobe Campaign. Esto se debe a:

   * Messages pended (**[!UICONTROL quotas met]** message): quotas declared by the declarative MX rules defined in Campaign have been met. Para obtener más información sobre este mensaje, consulte [esta página](../../delivery/using/technical-recommendations.md#quota-met). Para obtener más información sobre las reglas MX, consulte [esta página](../../delivery/using/technical-recommendations.md#mx-rules).
   * Messages pended (**[!UICONTROL dynamic flow control]** message): Campaign MTA has encountered errors when trying to deliver messages for a given ISP which causes a slowdown to avoid too big of an error density and thus facing potential blacklisting.

* Un problema del sistema puede impedir que los servidores interactúen: esto puede ralentizar todo el proceso de envío. Compruebe los servidores para asegurarse de que no hay problemas de memoria o recursos que puedan afectar a Campaign en el proceso de obtención de los datos personalizados, por ejemplo.

### Prácticas recomendadas para el rendimiento {#best-practices-performance}

* No mantenga los envíos en estado de error en la instancia, ya que esto mantiene tablas temporales e influye en el rendimiento.

* Elimine las entregas que ya no sean necesarias.

* Destinatarios inactivos en los últimos 12 meses que se eliminarán de la base de datos para mantener la calidad de la dirección.

* No intente programar entregas grandes juntas. Hay un lapso de 5 a 10 minutos para distribuir la carga uniformemente sobre el sistema. Coordine la programación de los envíos con los demás miembros de su equipo para garantizar el mejor rendimiento. Cuando el servidor de mercadotecnia gestiona muchas tareas diferentes al mismo tiempo, puede ralentizar el rendimiento.

* Mantenga el tamaño de sus correos electrónicos lo más bajo posible. El tamaño máximo recomendado de un correo electrónico es de unos 35 KB. El tamaño de una entrega por correo electrónico genera una cierta cantidad de volumen en los servidores de envío.

* Las entregas grandes, como las entregas a más de un millón de destinatarios, necesitan espacio en las colas de envío. Esto por sí solo no es un problema para el servidor, pero cuando se combina con docenas de entregas grandes que se realizan al mismo tiempo, puede provocar un retraso en el envío.

* La personalización en correos electrónicos extrae datos de la base de datos de cada destinatario. Si hay muchos elementos de personalización, esto aumenta la cantidad de datos necesarios para preparar la entrega.

* Direcciones de índice. Para optimizar el rendimiento de las consultas SQL utilizadas en la aplicación, se puede declarar un índice a partir del elemento principal del esquema de datos.

>[!NOTE]
>
>Los ISP desactivarían las direcciones después de un período de inactividad. Los mensajes recibidos se envían a los remitentes para informarles sobre este nuevo estado.

## Estados de envío {#delivery-statuses}

Al realizar un envío, es posible que aparezca el siguiente estado en su panel de envíos:

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
   <td> El servidor (MTA) tuvo en cuenta el envío, pero no lo procesó.<br /> </td> 
  </tr> 
  <tr> 
   <td> Ignorado<br /> </td> 
   <td> No se realizó el envío al destinatario debido a un error con su dirección. Se lo incluyó en una lista negra o en cuarentena, no se proporcionó o está duplicado. <br /> </td> 
  </tr> 
  <tr> 
   <td> Enviado<br /> </td> 
   <td> El envío se entregó correctamente al proveedor de mensajes (pero es posible que el destinatario no lo haya recibido).<br /> </td> 
  </tr> 
  <tr> 
   <td> Error<br /> </td> 
   <td> El envío no ha podido llegar al destinatario debido a una dirección no válida o a que la bandeja de entrada estaba llena. También puede estar relacionado con un problema con los bloques de personalización, ya que pueden generar errores cuando los esquemas no coinciden con la asignación de envíos. Consulte Estado <a href="#failed-status" target="_blank">fallido</a><br /> </td> 
  </tr> 
  <tr> 
   <td> Tenido en cuenta por el proveedor de servicios<br /> </td> 
   <td> El proveedor de servicios SMS recibió el envío.<br /> </td> 
  </tr> 
  <tr> 
   <td> Se ha recibido en dispositivos móviles<br /> </td> 
   <td> El destinatario recibió el SMS en su dispositivo móvil.<br /> </td> 
  </tr> 
  <tr> 
   <td> Pendiente<br /> </td> 
   <td> El envío está listo para enviarse y se va a procesar mediante el servidor de envío (MTA). Consulte Estado <a href="#pending-status" target="_blank"></a>pendiente.<br /> </td> 
  </tr> 
  <tr> 
   <td> Envío cancelado<br /> </td> 
   <td> Un operador ha cancelado el envío.<br /> </td> 
  </tr> 
  <tr> 
   <td> Preparado<br /> </td> 
   <td> El estado de intermediario se utiliza solo para conectores externos como el canal móvil. Sigue al estado “Pendiente” y es el conector externo que determina el estado siguiente.<br /> </td> 
  </tr> 
  <tr> 
   <td> Enviado al proveedor de servicios<br /> </td> 
   <td> Se realizó el envío al proveedor de servicios SMS, pero no se ha recibido todavía.<br /> </td> 
  </tr> 
 </tbody> 
</table>

Para aprender a optimizar el envío de los correos electrónicos de Adobe Campaign, consulte la [Guía de prácticas recomendadas de envío](https://docs.campaign.adobe.com/doc/AC/getting_started/EN/deliverability.html) de Adobe Campaign y [esta página](../../delivery/using/about-deliverability.md).

### Estado pendiente {#pending-status}

Después de confirmar el envío, puede ver que el estado de su envío es **[!UICONTROL Pending]**. Este estado significa que el proceso de ejecución está esperando a que estén disponibles algunos recursos.

The **[!UICONTROL Pending]** status can first mean that your delivery has been scheduled and is pending until the given date. Para obtener más información, consulte la sección [Programación de envíos](../../delivery/using/steps-sending-the-delivery.md#scheduling-the-delivery-sending).

If your delivery is not being sent and its status remains **[!UICONTROL Pending]**, it can be the result of:

* Puede que el MTA (Agente de Transferencia de Mensajes), que ejecuta módulos y procesos en el servidor de envío y que administra el envío por correo electrónico, no se haya iniciado o que sea necesario reiniciarlo. Para comprobar esto e iniciar el módulo si es necesario, aplique los siguientes pasos:

   * Check that your `mta@<instance>` modules are launched on your MTA servers.

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
   >Replace `<INSTANCENAME>` with the name of your instance (production, development, etc.). El nombre de instancia se identifica mediante los archivos de configuración: `[path of application]nl6/conf/config-<INSTANCENAME>.xml`

* La entrega puede estar utilizando una afinidad no configurada en el servidor de envío. In this case, check the configuration of the traffic management (IP affinity) and use the **[!UICONTROL Managing affinities with IP addresses]** field to link deliveries to the MTA that manages the affinity. Para obtener más información sobre las afinidades, consulte [esta sección](../../installation/using/configuring-campaign-server.md#personalizing-delivery-parameters).
* Cuando la preparación del envío está pendiente, puede haber demasiadas campañas activas, lo cual bloquea la actualización del estado del envío. To solve this, go to **[!UICONTROL Options]** and increase the value of **[!UICONTROL NmsOperation_LimitConcurrency]** (default is 10). No ejecute más campañas que el valor asignado en esta opción específica.

### Estado de error {#failed-status}

If an email delivery&#39;s status is **[!UICONTROL Failed]**, it can be linked to an issue with personalization blocks. Los bloques personalizados en un envío pueden generar errores cuando los esquemas no coinciden con la asignación de envíos, por ejemplo.

Los “logs” de envío son esenciales para saber por qué ha fallado un envío. Estos son los posibles errores que puede detectar en los “logs” de envío:

* Si los mensajes del destinatario fallan con un error &quot;No accesible&quot; que indica: **Error al compilar la línea X de la secuencia de comandos &#39;content htmlContent&#39;: no`[table]`está definida. JavaScript: error al evaluar el script &#39;contenido htmlContent**, la causa de este problema es casi siempre una personalización dentro del HTML que intenta llamar a una tabla o campo que no se ha definido o asignado en el objetivo ascendente o en el destino de mapeo del envío.

   Para corregir esto, es necesario revisar el flujo de trabajo y el contenido del envío para determinar específicamente qué personalización está intentando llamar a la tabla en cuestión y si se puede asignar o no la tabla. Desde este punto, la forma de resolver el problema sería eliminar la llamada a esta tabla en el HTML o corregir la asignación al envío.

* En el modelo de implementación de fuentes intermedias, puede aparecer el siguiente mensaje en los registros de entrega: **Error durante la llamada del método &#39;AppendDeliveryPart&#39; en el servidor de abastecimiento intermedio: &#39;Error de comunicación con el servidor: compruebe que esta esté correctamente configurada. Código HTTP 408 &#39;Servicio no disponible temporalmente&#39;**.

   La causa está relacionada con problemas de rendimiento. Significa que la instancia de marketing invierte demasiado tiempo creando datos antes de enviarlos al servidor de mid-sourcing.

   Para resolver esto, recomendamos realizar una limpieza y reindexar la base de datos. Para obtener más información sobre el mantenimiento de la base de datos, consulte [esta sección](../../production/using/recommendations.md).

   También debe reiniciar todos los flujos de trabajo con una actividad programada y todos los flujos de trabajo en estado fallido. Consulte [esta sección](../../workflow/using/scheduler.md).

* Cuando falla una entrega, puede aparecer el siguiente error en los registros de entrega: **DLV-XXXX El recuento de mensajes preparados (123) es mayor que el número de mensajes que se van a enviar (111). Póngase en contacto con el servicio técnico.**

   Normalmente, este error significa que existe un campo o un bloque personalizado dentro del correo electrónico que tiene más de un valor para el destinatario. Se está utilizando un bloque personalizado que está recuperando más de un registro para un destinatario determinado.

   Para resolver esto, compruebe los datos personalizados utilizados y, a continuación, compruebe el objetivo de los destinatarios que tengan más de una entrada para cualquiera de esos campos. You can also use a **[!UICONTROL Deduplication]** activity in the targeting workflow prior to the delivery activity to check there is only one personalization field at a time. Para obtener más información sobre la deduplicación, consulte [esta sección](../../workflow/using/deduplication.md).

* Algunos envíos pueden fallar con un error &quot;No alcanzable&quot; que indica: &quot;Devolución de correo electrónico entrante (la regla &#39;Respuestas_automáticas&#39; coincide con esta devolución). Esto significa que el envío se realizó correctamente, pero Adobe Campaign recibió un mensaje de respuesta automática del destinatario (por ejemplo, “fuera de la oficina”) que coincidió con las reglas de correo electrónico entrante de “respuesta automática”. Adobe Campaign ignora el correo electrónico de respuesta automática y la dirección del destinatario no se pone en cuarentena.

**Temas relacionados:**

* [“Logs” de envío e historial](#delivery-logs-and-history)
* [Comprensión de los errores de envío](../../delivery/using/understanding-delivery-failures.md)
* [Tipos y motivos de errores de envío](../../delivery/using/understanding-delivery-failures.md#delivery-failure-types-and-reasons)

## Número de mensajes enviados {#number-of-messages-sent}

You can access deliveries from the delivery list, via the **[!UICONTROL Campaign Management > Deliveries]** node of the tree.

De forma predeterminada, la lista de envíos contiene los nombres y estados de los envíos creados en el nodo seleccionado. También muestra el número de mensajes que se van a enviar, procesados y enviados con éxito.

* The number of **[!UICONTROL Messages to send]** corresponds to the number of recipients targeted after analysis and prior to delivery.
* The number of messages in the **[!UICONTROL success]** column corresponds to the number of messages sent by the server and received by the recipients.
* The number of **[!UICONTROL processed]** messages corresponds to the number of messages received plus the number of messages with errors.

El panel de envío permite rastrear la cantidad de mensajes enviados.

>[!NOTE]
>
>Para los envíos grandes, quizá desee actualizar estos valores. Para ello, seleccione el envío en cuestión y, a continuación, haga clic con el botón derecho del ratón. Seleccione **[!UICONTROL Action > Recompute delivery and tracking indicators...]** y, a continuación, utilice el asistente para actualizar esta información.

## Envíos programados {#scheduled-deliveries-}

Si los envíos no se ejecutan en la fecha programada exacta, puede deberse a una diferencia entre las zonas horarias de los servidores. La instancia de mid-sourcing y la instancia de producción pueden estar en diferentes zonas horarias.

Por ejemplo, si la instancia de mid-sourcing se encuentra en el huso horario de Brisbane y la instancia de producción está en el huso horario de Darwin, ambas zonas horarias están separadas por media hora, por lo que en el “log” de auditoría puede claramente que si el envío está programado para su producción a las 11:56, el mismo envío programado de mid-sourcing se produciría a las 12:26, lo que supone una diferencia de media hora.
