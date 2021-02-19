---
solution: Campaign Classic
product: campaign
title: Agrupamiento de archivos
description: Descubra más información sobre la actividad del flujo de trabajo Recolector de ficheros
audience: workflow
content-type: reference
topic-tags: event-activities
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '524'
ht-degree: 100%

---


# Agrupamiento de archivos{#file-collector}

El **File collector** supervisa la llegada de uno o más archivos de un directorio y activa su transición para cada archivo recibido. Para cada evento, una variable **[!UICONTROL filename]** contiene el nombre completo del archivo recibido. Los archivos recopilados se mueven a otro directorio para fines de archivo y para asegurarse de que se cuentan solo una vez.

De forma predeterminada, el recopilador de archivos es una tarea persistente que prueba la presencia de archivos en las horas especificadas por la programación.

Los archivos deben estar en el servidor en el que se ejecuta el módulo wfserver de este flujo de trabajo. Si se han implementado varios módulos wfserver en una sola instancia, se debe especificar la afinidad de las actividades utilizando estos archivos o la afinidad global del flujo de trabajo.

## Propiedades {#properties}

La primera pestaña de la actividad **[!UICONTROL File collector]** permite seleccionar el directorio de origen y, si es necesario, filtrar los archivos recopilados. Las otras pestañas se detallan en [Inbound Emails](../../workflow/using/inbound-emails.md) (pestañas **[!UICONTROL Schedule]** y **[!UICONTROL Expiry]**).

![](assets/file_collect_edit.png)

1. **Downloading files**

   * **[!UICONTROL Directory]**

      Directorio que contiene los archivos que se van a descargar. Este directorio debe crearse previamente en el servidor: si no existe, se generará un error.

   * **[!UICONTROL Filter]**

      Solo se tienen en cuenta los archivos que coinciden con este filtro. Los demás archivos del directorio se omiten. Si el filtro está vacío, se tendrán en cuenta todos los archivos del directorio. Ejemplos de filtros: ***.zip**, **import-*.txt**.

   * **[!UICONTROL Stop as soon as a file has been processed]**

      Si esta opción está activada, la tarea finaliza después de la recepción del primer archivo. Si hay varios archivos correspondientes al filtro en el directorio, solo se tendrá en cuenta uno. Esta opción garantiza que solo se envíe un evento. El archivo tenido en cuenta es la primero en la lista en orden alfabético.

      Para una actividad no programada, si no se encuentra ningún archivo que coincida con el filtro en el directorio especificado y si la opción **[!UICONTROL Process file nonexistence]** no está activada, se generará un error.

   * **[!UICONTROL Execution schedule]**

      Determina la frecuencia de la comprobación de presencia de archivos mediante los parámetros de la pestaña **[!UICONTROL Schedule]**.

1. **Error handling**

   Estas son las opciones disponibles.

   * **[!UICONTROL Process file nonexistence]**

      Esta opción inicia una transición especial cada vez que no se encuentra ningún archivo que coincida con el filtro en el directorio especificado.

      Si la tarea no está programada, esta transición se activará solo una vez.

   * **[!UICONTROL Processing errors]**

      Esta opción hace que aparezca una transición especial, que se activará si se genera un error. En este caso, el flujo de trabajo no cambia a estado de error y continúa la ejecución

      Los errores que se tienen en cuenta son los errores del sistema de archivos (el archivo no se puede mover, no se puede acceder a un directorio, etc.).

      Esta opción no procesa los errores relacionados con la configuración de la actividad, es decir, valores no válidos.

1. **Historization**

   Consulte el paso **[!UICONTROL File historization]** aquí: [Web download](../../workflow/using/web-download.md).

El orden de procesamiento del archivo no se puede determinar. Para procesar un conjunto de archivos secuencialmente, utilice la opción **[!UICONTROL Stop as soon as a file has been processed]** y cree un bucle. En este caso, los archivos se procesan en orden alfabético. La opción **[!UICONTROL Process file nonexistence]** permite finalizar la iteración.

![](assets/file_collect_loop.png)

## Parámetros de salida {#output-parameters}

* filename: Nombre de archivo completo. Es el nombre de archivo que se ha movido al directorio de historización. Por lo tanto, la ruta es diferente, pero el nombre también es diferente si ya existe otro archivo con el mismo nombre en el directorio. La extensión se mantiene.
