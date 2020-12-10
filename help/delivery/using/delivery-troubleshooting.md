---
solution: Campaign Classic
product: campaign
title: Resolución de problemas
description: Obtenga más información sobre el rendimiento de los envíos y cómo solucionar problemas relacionados con la supervisión de envíos.
audience: delivery
content-type: reference
topic-tags: monitoring-deliveries
translation-type: tm+mt
source-git-commit: f3ba836bbb5a5f82d6a7868dcb15edc8e61b9a5b
workflow-type: tm+mt
source-wordcount: '789'
ht-degree: 87%

---


# Envío envía solución de problemas {#delivery-troubleshooting}

Esta sección lista problemas comunes que puede encontrar al enviar envíos y cómo solucionarlos.

Además, asegúrese de seguir las optimizaciones y la lista de comprobación detallada en [esta página](../../delivery/using/delivery-performances.md) para asegurarse de que sus envíos funcionan bien.

**Temas relacionados:**

* [Estados de entrega](../../delivery/using/delivery-statuses.md)
* [Panel de entregas](../../delivery/using/delivery-dashboard.md)
* [Comprensión de los errores de entrega](../../delivery/using/understanding-delivery-failures.md)

## Entregas lentas {#slow-deliveries}

Tras hacer clic en el botón **[!UICONTROL Send]**, la entrega parece tardar más de lo normal. Esto puede deberse a diferentes elementos:

* Es posible que algunos proveedores de correo electrónico hayan agregado sus direcciones IP a una lista de bloqueados. En este caso, compruebe sus broadlogs y consulte [esta sección](../../delivery/using/about-deliverability.md).

* Su entrega puede ser demasiado grande como para procesarlo rápidamente, como puede ser el caso de una alta personalización de JavaScript o si su entrega pesa más de 60 kB. Consulte las [prácticas recomendadas relacionadas con las entregas](../../delivery/using/delivery-best-practices.md) de Adobe Campaign para obtener más información sobre las directrices de contenido.

* Es posible que se haya activado una restricción dentro del MTA de Adobe Campaign. Esto se debe a:

   * Mensajes pendientes (mensaje **[!UICONTROL quotas met]**): se han cumplido las cuotas declaradas por las reglas de MX definidas en Campaign. Para obtener más información sobre este mensaje, consulte [esta página](../../delivery/using/deliverability-faq.md) . Para obtener más información sobre las reglas MX, consulte [esta página](../../delivery/using/technical-recommendations.md#mx-rules).

   * Mensajes pendientes (mensaje **[!UICONTROL dynamic flow control]**): el MTA de Campaign ha detectado errores al intentar enviar mensajes para un ISP determinado, lo que provoca una ralentización para evitar una gran densidad de errores y, por lo tanto, la posible inclusión en una lista de bloqueados.

* Un problema del sistema puede impedir que los servidores interactúen: esto puede ralentizar todo el proceso de entrega. Compruebe los servidores para asegurarse de que no hay problemas de memoria o recursos que puedan afectar a Campaign en el proceso de obtención de los datos personalizados, por ejemplo.

## Entregas programadas {#scheduled-deliveries-}

Si las entregas no se ejecutan en la fecha programada exacta, puede deberse a una diferencia entre las zonas horarias de los servidores. La instancia de intermediario y la instancia de producción pueden estar en diferentes zonas horarias.

Por ejemplo, si la instancia de intermediario se encuentra en el huso horario de Brisbane y la instancia de producción está en el huso horario de Darwin, ambas zonas horarias están separadas por media hora, por lo que en el registro de auditoría puede claramente que si la entrega está programado para su producción a las 11:56, la misma entrega programada de intermediario se produciría a las 12:26, lo que supone una diferencia de media hora.

## Estado de error {#failed-status}

Si el estado de una entrega de correo electrónico es **[!UICONTROL Failed]**, puede deberse a un problema con bloques de personalización. Los bloques personalizados en una entrega pueden generar errores cuando los esquemas no coinciden con la asignación de entregas, por ejemplo.

Los registros de entregas son esenciales para saber por qué ha fallado una entrega. Estos son los posibles errores que puede detectar en los registros de entregas:

* Los mensajes de destinatario fallan con un error &quot;Inaccesible&quot; que indica:

   ```
   Error while compiling script 'content htmlContent' line X: `[table]` is not defined. JavaScript: error while evaluating script 'content htmlContent
   ```

   La causa de este problema es casi siempre una personalización dentro del HTML que intenta llamar a una tabla o campo que no se ha definido o asignado en la segmentación por secuencias o en la asignación de destino del envío.

   Para corregir esto, es necesario revisar el flujo de trabajo y el contenido de la entrega para determinar específicamente qué personalización está intentando llamar a la tabla en cuestión y si se puede asignar o no la tabla. Desde este punto, la forma de resolver el problema sería eliminar la llamada a esta tabla en el HTML o corregir la asignación a la entrega.

* En el modelo de implementación de mid-sourcing, el siguiente mensaje puede aparecer en los “logs” de envío:

   ```
   Error during the call of method 'AppendDeliveryPart' on the mid sourcing server: 'Communication error with the server: please check this one is correctly configured. Code HTTP 408 'Service temporarily unavailable'.
   ```

   La causa está relacionada con problemas de rendimiento. Significa que la instancia de marketing invierte demasiado tiempo creando datos antes de enviarlos al servidor de intermediario.

   Para resolver esto, recomendamos realizar una limpieza y reindexar la base de datos. Para obtener más información sobre el mantenimiento de la base de datos, consulte [esta sección](../../production/using/recommendations.md).

   También debe reiniciar todos los flujos de trabajo con una actividad programada y todos los flujos de trabajo en estado fallido. Consulte [esta sección](../../workflow/using/scheduler.md).

* Cuando un envío falla, el siguiente error puede aparecer en los “logs” de envío:

   ```
   DLV-XXXX The count of message prepared (123) is greater than the number of messages to send (111). Please contact support.
   ```

   Normalmente, este error significa que existe un campo o un bloque personalizado dentro del correo electrónico que tiene más de un valor para el destinatario. Se está utilizando un bloque personalizado que está recuperando más de un registro para un destinatario determinado.

   Para resolver esto, compruebe los datos personalizados utilizados y, a continuación, compruebe el objetivo de los destinatarios que tengan más de una entrada para cualquiera de esos campos. También puede utilizar una actividad **[!UICONTROL Deduplication]** en el flujo de trabajo de objetivos antes de la actividad de entrega para comprobar que solo hay un campo de personalización a la vez. Para obtener más información sobre la deduplicación, consulte [esta sección](../../workflow/using/deduplication.md).

* Algunos envíos pueden fallar con un error que indica “inaccesible”:

   ```
   Inbound email bounce (rule 'Auto_replies' has matched this bounce).
   ```

   Esto significa que la entrega se realizó correctamente, pero Adobe Campaign recibió un mensaje de respuesta automática del destinatario (por ejemplo, “fuera de la oficina”) que coincidió con las reglas de correo electrónico entrante de “respuesta automática”.

   Adobe Campaign ignora el correo electrónico de respuesta automática y la dirección del destinatario no se pone en cuarentena.
