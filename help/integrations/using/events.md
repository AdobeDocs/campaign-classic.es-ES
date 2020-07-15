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
source-wordcount: '1145'
ht-degree: 2%

---


# Eventos de activadores {#events}

## Procesamiento de eventos en JavaScript {#events-javascript}

### Archivo JavaScript {#file-js}

Pipeline utiliza una función de JavaScript para procesar cada mensaje. Esta función está definida por el usuario.

Se configura en la **[!UICONTROL NmsPipeline_Config]** opción bajo el atributo &quot;JSConnector&quot;. Se llama a este javascript cada vez que se recibe un evento. Está dirigido por el [!DNL pipelined] proceso.

El archivo JS de muestra es cus:triggers.js.

### Función JavaScript {#function-js}

El [!DNL pipelined] Javascript debe estar en inicio con una función específica.

Esta función se llama una vez por cada evento:

```
function processPipelineMessage(xmlTrigger) {}
```

Debería volver como

```
<undefined/>
```

Reinicie [!DNL pipelined] después de editar el JS.

### Activar formato de datos {#trigger-format}

Los [!DNL trigger] datos se pasan a la función JS. Está en formato XML.

* El **[!UICONTROL @triggerId]** atributo contiene el nombre del [!DNL trigger].
* El elemento **enriquecimientos** en formato JSON contiene los datos generados por Analytics y se adjunta al activador.
* **[!UICONTROL @offset]** es el &quot;puntero&quot; al mensaje. Indica el orden del mensaje en la cola.
* **[!UICONTROL @partitio]**n es un contenedor de mensajes dentro de la cola. El desplazamiento es relativo a una partición. <br>Hay unas 15 particiones en la cola.

Ejemplo:

```
<trigger offset="1500435" partition="4" triggerId="LogoUpload_1_Visits_from_specific_Channel_or_ppp">
 <enrichments>{"analyticsHitSummary":{"dimensions":{" eVar01":{"type":"string","data":["PI4INE1ETDF6UK35GO13X7HO2ITLJHVH"],"name":" eVar01","source":"session summary"}, "timeGMT":{"type":"int","data":[1469164186,1469164195],"name":"timeGMT","source":"session summary"}},"products":{}}}</enrichments>
 <aliases/>
 </trigger>
```

### Formato de datos de Enriquecimiento {#enrichment-format}

>[!NOTE]
>
>Es un ejemplo específico de varias implementaciones posibles.

El contenido se define en Analytics para cada activador. Está en formato JSON.
Por ejemplo, en un activador LogoUpload_upload_Visits:

* **[!UICONTROL eVar01]** puede contener el ID de comprador que se utiliza para reconciliar con destinatarios de Campaña. Está en formato String. <br>Debe conciliarse para encontrar el ID del comprador, que es la clave principal.

* **[!UICONTROL timeGMT]** puede contener la hora del activador en el lado de Analytics. Está en formato UTC Epoch (segundos desde 01/01/1970 UTC).

Ejemplo:

```
{
 "analyticsHitSummary": {
 "dimensions": {
 "eVar01": {
 "type": "string",
 "data": ["PI4INE1ETDF6UK35GO13X7HO2ITLJHVH"],
 "name": " eVar01",
 "source": "session summary"
 },
 "timeGMT": {
 "type": "int",
 "data": [1469164186, 1469164195],
 "name": "timeGMT",
 "source": "session summary"
 }
 },
 "products": {}
 }
 }
```

### Orden de procesamiento de eventos {#order-events}

Los eventos se procesan de uno en uno, por orden de desplazamiento. Cada subproceso del [!DNL pipelined] procesa una partición diferente.

El &quot;desplazamiento&quot; del último evento recuperado se almacena en la base de datos. Por lo tanto, si el proceso se detiene, se reinicia a partir del último mensaje. Estos datos se almacenan en el esquema integrado xtk:ducooffset.

Este puntero es específico para cada instancia y cada consumidor. Por lo tanto, cuando muchas instancias acceden a la misma canalización con diferentes consumidores, cada una recibe todos los mensajes y en el mismo orden.

El parámetro &quot;consumidor&quot; de la opción de canalización identifica la instancia que realiza la llamada.

Actualmente, no hay forma de tener diferentes colas para entornos separados como &quot;staging&quot; o &quot;dev&quot;.

### Registro y gestión de errores {#logging-error-handling}

Registros como logInfo() se dirigen al [!DNL pipelined] registro. Errores como logError() se escriben en el [!DNL pipelined] registro y hacen que el evento se coloque en una cola de reintentos. Compruebe el registro de tuberías.
Los mensajes de error se vuelven a intentar varias veces en la duración establecida en las [!DNL pipelined] opciones.

Para fines de depuración y supervisión, los datos de desencadenador completos se escriben en la tabla de desencadenadores. Se encuentra en el campo &quot;data&quot; en formato XML. De forma alternativa, un logInfo() que contenga los datos desencadenadores tiene el mismo propósito.

### Análisis de los datos {#data-parsing}

Este código JS de muestra analiza la eVar01 en los enriquecimientos.

```
function processPipelineMessage(xmlTrigger)
 {
 (…)
 var shopper_id = ""
 if (xmlTrigger.enrichments.length() > 0)
 {
 if (xmlTrigger.enrichments.toString().match(/eVar01/) != undefined)
 {
 var enrichments = JSON.parse(xmlTrigger.enrichments.toString())
 shopper_id = enrichments.analyticsHitSummary.dimensions. eVar01.data[0]
 }
 }
 (…)
 }
```

Tenga cuidado al analizar para evitar errores.
Dado que este código se utiliza para todos los activadores, la mayoría de los datos no son obligatorios. Por lo tanto, se puede dejar vacío cuando no esté presente.

### Almacenamiento del activador {#storing-triggers-js}

>[!NOTE]
>
>Es un ejemplo específico de varias implementaciones posibles.

Este código JS de muestra guarda el activador en la base de datos.

```
function processPipelineMessage(xmlTrigger)
 {```
 (…)
 var event = 
 <pipelineEvent
 xtkschema = "cus:pipelineEvent"
 _operation = "insert"
 created = {timeNow}
 lastModified = {timeNow}
 triggerType = {triggerType}
 timeGMT = {timeGMT}
 shopper_id = {shopper_id}
 data = {xmlTrigger.toXMLString()}
 />
 xtk.session.Write(event)
 return <undef/>; 
 }
```

### Restricciones {#constraints}

El rendimiento de este código debe ser óptimo, ya que se ejecuta a altas frecuencias. Existen posibles efectos negativos para otras actividades de comercialización. Especialmente si se procesan más de un millón de eventos de activación por hora en el servidor de marketing. O si no está correctamente ajustado.

El contexto de este JavaScript es limitado. No todas las funciones de la API están disponibles. Por ejemplo, getOption() o getCurrentdate() no funcionan.

Para permitir un procesamiento más rápido, se ejecutan varios subprocesos de esta secuencia de comandos al mismo tiempo. El código debe ser seguro para subprocesos.

## Almacenamiento de los eventos {#store-events}

>[!NOTE]
>
>Es un ejemplo específico de varias implementaciones posibles.

### esquema de evento de tubería {#pipeline-event-schema}

Los Eventos se almacenan en una tabla de base de datos. Se utiliza en campañas de marketing para clientes de destinatario y enriquece los correos electrónicos mediante activadores.
Aunque cada activador puede tener una estructura de datos distinta, todos los activadores se pueden guardar en una sola tabla.
El campo desencadenadorTipo identifica de dónde se originan los datos.

Este es un ejemplo de código de esquema para esta tabla:

| Atributo | Tipo | Etiqueta | Descripción |
|:-:|:-:|:-:|:-:|
| pelineEventId | Largo | Clave principal | La clave principal interna del activador. |
| data | Nota | Activar datos | El contenido completo de los datos desencadenadores en formato XML. Para fines de depuración y auditoría. |
| desencadenadorTipo | Cadena 50 | TriggerType | Nombre del activador. Identifica el comportamiento del cliente en el sitio web. |
| shopper_id | Cadena 32 | shopper_id | Identificador interno del comprador. Definido por el flujo de trabajo de reconciliación. Si es cero, significa que el cliente es desconocido en Campaña. |
| shopper_key | Largo | shopper_key | El Identificador externo del comprador según Analytics. |
| created | Datetime | Creado | Hora a la que se creó el evento en Campaña. |
| lastModified | Datetime | Última modificación | La última vez que se modificó el evento en Adobe. |
| timeGMT | Datetime | Marca de hora | Hora a la que se generó el evento en Analytics. |

### Visualización de los eventos {#display-events}

Los eventos se pueden mostrar con un formulario sencillo basado en el esquema de eventos.

>[!NOTE]
>
>El nodo Evento de canalización no está integrado y debe agregarse, así como el formulario relacionado debe crearse en Campaña. Estas operaciones están restringidas únicamente a usuarios expertos. Para obtener más información sobre esto, consulte estas secciones: [Jerarquía](../../configuration/using/about-navigation-hierarchy.md) de navegación y [edición de formularios](../../configuration/using/editing-forms.md).

![](assets/triggers_7.png)

## Procesamiento de los eventos {#processing-the-events}

### Flujo de trabajo de reconciliación {#reconciliation-workflow}

La reconciliación es el proceso de hacer coincidir el cliente de Analytics con la base de datos de Campañas. Por ejemplo, los criterios para la coincidencia pueden ser shopper_id.

Por motivos de rendimiento, la coincidencia debe realizarse en modo por lotes mediante un flujo de trabajo.
La frecuencia debe establecerse en 15 minutos para optimizar la carga de trabajo. Como consecuencia, el retraso entre una recepción de evento en Adobe Campaign y su procesamiento por un flujo de trabajo de marketing es de hasta 15 minutos.

### Opciones para la reconciliación de unidades en JavaScript {#options-unit-reconciliation}

En teoría, es posible ejecutar la consulta de reconciliación para cada activador en JavaScript. Tiene un mayor impacto en el rendimiento y ofrece resultados más rápidos. Podría ser necesario para casos de uso específicos cuando sea necesaria la reactividad.

Puede resultar difícil hacerlo si no se establece ningún índice en shopper_id. Si los criterios se encuentran en un servidor de base de datos independiente al servidor de marketing, utiliza un vínculo de base de datos, que tiene un rendimiento deficiente.

### Flujo de trabajo de depuración {#purge-workflow}

Los activadores se procesan dentro de la hora, por lo que no hay razón para mantenerlos durante mucho tiempo. El volumen puede ser de aproximadamente 1 millón de activadores por hora. Explica por qué se debe implementar un flujo de trabajo de purga. La depuración elimina todos los activadores que tengan más de tres días y se ejecuten una vez al día.

### Flujo de trabajo de Campaña {#campaign-workflow}

El flujo de trabajo de campaña de desencadenadores suele ser similar al de otras campañas recurrentes que se han utilizado.
Por ejemplo, puede establecer un inicio con una consulta en los activadores que buscan eventos específicos durante el último día. Ese destinatario se utiliza para enviar el correo electrónico. Los Enriquecimientos o datos pueden provenir del activador. Marketing puede utilizarla de forma segura, ya que no requiere ninguna configuración.
