---
solution: Campaign Classic
product: campaign
title: Configuración de la integración
description: Configuración de la integración
audience: integrations
content-type: reference
translation-type: ht
source-git-commit: d7de46abb71ca25ef765c6fb5443f6e338fba56e
workflow-type: ht
source-wordcount: '435'
ht-degree: 100%

---


# Supervisión de canalización {#pipeline-monitoring}

El servicio web de estado de [!DNL pipelined] proporciona información sobre el estado del [!DNL pipelined] proceso.

Se puede acceder a él manualmente con un explorador o automáticamente con una aplicación de monitoreo.

Está en formato REST y se describe a continuación.

![](assets/triggers_8.png)

## Indicadores {#indicators}

Esta sección enumera los indicadores del servicio web de estado.

Se destacan los indicadores recomendados a monitorizar.

* Consumidor: nombre del cliente que extrae los activadores. Configurado en la opción de canalización.
* http-request
   * last-live-ms-ago: tiempo en ms desde que se realizó una comprobación de conexión.
   * last-failed-cnx-ms-ago: tiempo en ms desde la última vez que se produjo un error en la comprobación de conexión.
   * stream-host: nombre del host desde el que se extraen los datos de la canalización.
* puntero
   * current-offsets: valor del puntero en la canalización, por subproceso secundario.
   * last-flush-ms-ago: tiempo en ms desde que se recuperó un lote de activadores.
   * next-offsets-flush: tiempo de espera hasta el siguiente lote una vez finalizado.
   * processed-since-last-flush: número de activadores procesados en el último lote.
* enrutamiento
   * activadores: lista de activadores recuperados. Configurado en la opción de [!DNL pipelined] .
* estadísticas
   * average-pointer-flush-time-ms: tiempo de procesamiento promedio para un lote de activadores.
   * average-trigger-processing-time-ms: tiempo promedio empleado en analizar los datos de activadores.
   * bytes-read: número de bytes leídos desde la cola desde que se inició el proceso.
   * current-messages: número actual de mensajes pendientes que se han extraído de la cola y que están pendientes de procesamiento. **Este indicador debe estar cerca de cero**.
   * current-retries: número actual de mensajes que no se han procesado correctamente y que están a la espera de un reintento.
   * peak-messages: número máximo de mensajes pendientes que el proceso ha estado gestionando desde que se inició.
   * pointer-flushes: número de lotes de mensajes procesados desde el inicio.
   * routing-JS-custom: número de mensajes procesados por el JS personalizado.
   * trigger-discarded: número de mensajes que se descartaron después de demasiados reintentos debido a errores de procesamiento.
   * trigger-processed: número de mensajes procesados sin error.
   * trigger-received: número de mensajes recibidos de la cola.

Estas estadísticas se muestran por subproceso de procesamiento.

* average-trigger-processing-time-ms: tiempo promedio empleado en analizar los datos de activadores.
* is-JS-processor: valor &quot;1&quot; si este subproceso utiliza el JS personalizado.
* trigger-discarded: número de mensajes que se descartaron después de demasiados reintentos debido a errores de procesamiento. **Este indicador debe ser cero**.
* trigger-failures: número de errores de procesamiento en el JS. **Este indicador debe ser cero**.
* trigger-received: número de mensajes recibidos de la cola.

* Configuración: se establecen en los archivos de configuración.
   * flush-pointer-msg-count: número de mensajes en un lote.
   * flush-pointer-period-ms: tiempo entre dos lotes, en milisegundos.
   * processing-threads-JS: número de subprocesos de procesamiento que ejecutan el JS personalizado.
   * retry-period-ms: tiempo entre dos reintentos cuando se produce un error de procesamiento.
   * try-valid-duration-ms: se vuelve a intentar la duración desde el procesamiento de tiempo hasta que se descarta el mensaje.
   * Informe de mensajes de canalización

## Informe de mensajes de canalización {#pipeline-report}

Este informe muestra la cantidad de mensajes por hora en los últimos cinco días.

![](assets/triggers_9.png)
