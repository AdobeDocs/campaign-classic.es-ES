---
title: Configuración de la integración
seo-title: Configuración de la integración
description: Configuración de la integración
seo-description: null
page-status-flag: never-activated
uuid: e2db7bdb-8630-497c-aacf-242734cc0a72
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: integrations
content-type: reference
topic-tags: adobe-experience-manager
discoiquuid: 1c20795d-748c-4f5d-b526-579b36666e8f
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 0112d5bd052ad66169225073276d1da4f3c245d8
workflow-type: tm+mt
source-wordcount: '438'
ht-degree: 2%

---


# Supervisión de canalización {#pipeline-monitoring}

El servicio web de [!DNL pipelined] estado proporciona información sobre el estado del [!DNL pipelined] proceso.

Se puede acceder a él manualmente con un navegador o automáticamente con una aplicación de supervisión.

Está en formato REST, que se describe a continuación.

![](assets/triggers_8.png)

## Indicadores {#indicators}

Esta sección lista los indicadores del servicio Web de estado.

Se destacan los indicadores recomendados para supervisar.

* Consumidor: nombre del cliente que extrae los activadores. Configurado en la opción de canalización.
* http-request
   * last-live-ms-ago: tiempo en ms desde que se realizó una comprobación de conexión.
   * last-failed-cnx-ms-ago: tiempo en ms desde la última vez que se produjo un error en la comprobación de conexión.
   * stream-host: nombre del host desde el que se extraen los datos de la canalización.
* puntero
   * compensaciones actuales: valor del puntero en la canalización, por subproceso secundario.
   * last-flush-ms-ago: tiempo en ms desde que se recuperó un lote de activadores.
   * next-offsets-flush: tiempo de espera hasta el siguiente lote, una vez finalizado.
   * procesado desde último vaciado: número de activadores procesados en el último lote.
* enrutamiento
   * activadores: lista de activadores recuperados. Configurado en la [!DNL pipelined] opción.
* stats
   * average-puntero-flush-time-ms: tiempo de procesamiento promedio para un lote de activadores.
   * average-desencadenador-procesando-time-ms: tiempo promedio empleado en analizar los datos de activadores.
   * bytes-read: número de bytes leídos desde la cola desde que se inició el proceso.
   * current-messages: número actual de mensajes pendientes que se han extraído de la cola y que están pendientes de procesamiento. **Este indicador debe estar cerca de cero**.
   * reintentos actuales: número actual de mensajes que no se han procesado correctamente y que están a la espera de reintento.
   * mensajes máximos: número máximo de mensajes pendientes que el proceso ha estado gestionando desde que se inició.
   * pinzas de puntero: número de lotes de mensajes procesados desde el inicio.
   * enrutamiento-JS-custom: número de mensajes procesados por el JS personalizado.
   * desencadenador descartado: número de mensajes que se descartaron después de demasiados reintentos debido a errores de procesamiento.
   * desencadenador procesado: número de mensajes procesados sin error.
   * desencadenador recibido: número de mensajes recibidos de la cola.

Estas estadísticas se muestran por subproceso de procesamiento.

* average-desencadenador-procesando-time-ms: tiempo promedio empleado en analizar los datos de activadores.
* is-JS-processor: valor &quot;1&quot; si este subproceso utiliza la JS personalizada.
* desencadenador descartado: número de mensajes que se descartaron después de demasiados reintentos debido a errores de procesamiento. **Este indicador debe ser cero**.
* desencadenador-fallos: número de errores de procesamiento en el JS. **Este indicador debe ser cero**.
* desencadenador recibido: número de mensajes recibidos de la cola.

* Configuración: se establecen en los archivos de configuración.
   * flush-puntero-msg-count: número de mensajes en un lote.
   * flush-puntero-period-ms: tiempo entre dos lotes, en milisegundos.
   * processing-thread-JS: número de subprocesos de procesamiento que ejecutan el JS personalizado.
   * reintentar-period-ms: tiempo entre dos reintentos cuando se produce un error de procesamiento.
   * try-valid-duration-ms: se vuelve a intentar la duración desde el procesamiento de tiempo hasta que se descarta el mensaje.
   * Informe de mensajes de canalización

## Informe de mensajes de canalización {#pipeline-report}

Este informe muestra la cantidad de mensajes por hora en los últimos cinco días.

![](assets/triggers_9.png)
