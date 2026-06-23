---
product: campaign
title: Envío continuo
description: Envío continuo
feature: Workflows, Channels Activity
hide: true
exl-id: 9c228cdb-331e-476e-a24c-3c7e23add3bf
TQID: https://experienceleague.adobe.com/ed2gcvqkoOttP8-f0EJlyxWZMc5J2VaZS5FIFo-a6jA
product_v2: id: dfc56824-e8b9-499e-85d4-21aedb507314
feature_v2: []
subfeature_v2: id: ee25c34b-ea50-427b-9369-ba0a160f7d70id: b5f0aaf4-1e48-400d-95ac-6eb3078cf22fid: d1110311-2ca4-442b-be37-088a6db845ee
source-git-commit: 38eab6b8da73163e4476e91c0ef73f25c3f57546
workflow-type: ht
source-wordcount: 367
ht-degree: 100%

---

# Envío continuo{#continuous-delivery}



Una acción del tipo **Entrega continua** permite agregar nuevos destinatarios a una entrega existente. Este tipo de envío evita tener que crear una nueva cada vez: este modo suele ser más eficaz, en particular para alertas de bajo volumen o notificaciones enviadas cuando es necesario.

![](assets/do-not-localize/how-to-video.png) [Descubra esta función en vídeo](#continuous-delivery-video)

A nivel de la plantilla de envío, puede especificar un script para calcular la etiqueta (y la carpeta de la campaña) de la entrega asociado. Si la secuencia de comandos calcula una entrega que aún no existe, se crea sobre la marcha.

![](assets/edit_diffusion_fil.png)

La opción **[!UICONTROL Process errors]** muestra una transición particular que se activa si se genera un error. En este caso, el flujo de trabajo no pasa al modo de error y se activa con la ejecución.

Los errores que se tienen en cuenta son los errores del sistema de archivos (el archivo no se puede mover, no se puede acceder a un directorio, etc.).

Esta opción no procesa los errores relacionados con la configuración de la actividad, es decir, valores no válidos.

## Parámetros de entrada {#input-parameters}

* tableName
* esquema

Cada evento entrante debe especificar un objetivo definido por estos parámetros.

Solamente cuando la opción **[!UICONTROL Specified by the inbound event]** está seleccionada.

## Parámetros de salida {#output-parameters}

* tableName
* esquema
* recCount

Este conjunto de tres valores identifica el objetivo resultante de la entrega sobre la marcha. **[!UICONTROL tableName]** es el nombre de la tabla que memoriza los identificadores de destinatario, **[!UICONTROL schema]** es el esquema de la población (normalmente nms:recipient) y **[!UICONTROL recCount]** es el número de elementos de la tabla.

La transición asociada al complemento tiene los mismos parámetros.

## Configuración de envíos continuos

En esta sección se explica cómo configurar un envío continuo.

Los **envíos continuos** le permiten añadir destinatarios nuevos a un envío existente, lo que evita tener que crear un envío nuevo cada vez que se añade un nuevo destinatario. Puede actualizar el elemento creativo directamente en el flujo de trabajo de campaña para que se actualice la plantilla en la carpeta Recurso de plantilla de envíos.

Un envío continuo creará un envío ÚNICO y registros de envío (broadLog) y registros de seguimiento que hacen referencia a que se agrega un envío cada vez que se ejecuta.

![Envío continuo](assets/delivery_continuous.jpg)

## Tutorial en vídeo {#continuous-delivery-video}

Este vídeo muestra cómo configurar un envío continuo con una consulta incremental.

>[!VIDEO](https://video.tv.adobe.com/v/25039?quality=12)

Hay disponibles más vídeos de procedimientos para Campaign Classic [aquí](https://experienceleague.adobe.com/docs/campaign-classic-learn/tutorials/overview.html?lang=es).
