---
title: Envío continuo
seo-title: Envío continuo
description: Envío continuo
seo-description: null
page-status-flag: never-activated
uuid: af8b4582-299e-47f9-9819-987b35db94ab
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: workflow
content-type: reference
topic-tags: action-activities
discoiquuid: 9d80be19-8dde-4278-ab5f-23f364fe422e
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 579329d9194115065dff2c192deb0376c75e67bd

---


# Envío continuo{#continuous-delivery}

Una acción del tipo **Continuous delivery** permite agregar nuevos destinatarios a un envío existente. Este tipo de envío evita tener que crear una nueva entrega cada vez que: Este modo suele ser más eficaz, en particular para las alertas de bajo volumen o las notificaciones enviadas cuando es necesario. A nivel de la plantilla de envío, puede especificar un script para calcular la etiqueta (y la carpeta de la campaña) del envío asociado. Si la secuencia de comandos calcula un envío que aún no existe, se crea sobre la marcha.

![](assets/edit_diffusion_fil.png)

The **[!UICONTROL Process errors]** option displays a particular transition which will be activated if an error is generated. En este caso, el flujo de trabajo no pasa al modo de error y se activa con la ejecución.

Los errores que se tienen en cuenta son los errores del sistema de archivos (el archivo no se puede mover, no se puede acceder a un directorio, etc.).

Esta opción no procesa los errores relacionados con la configuración de la actividad, es decir, valores no válidos.

## Parámetros de entrada {#input-parameters}

* tableName
* esquema

Cada evento entrante debe especificar un objetivo definido por estos parámetros.

Solo cuando la **[!UICONTROL Specified by the inbound event]** opción está seleccionada.

## Parámetros de salida {#output-parameters}

* tableName
* esquema
* recCount

Este conjunto de tres valores identifica el objetivo resultante del envío sobre la marcha. **[!UICONTROL tableName]** es el nombre de la tabla que memoriza los identificadores del objetivo, **[!UICONTROL schema]** es el esquema de la población (normalmente nms:Recipiente) y **[!UICONTROL recCount]** es el número de elementos de la tabla.

La transición asociada al complemento tiene los mismos parámetros.
