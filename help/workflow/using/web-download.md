---
title: Descarga web
seo-title: Descarga web
description: Descarga web
seo-description: null
page-status-flag: never-activated
uuid: 44039e9c-0cd8-4d3f-b73f-e01c5343835a
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: workflow
content-type: reference
topic-tags: event-activities
discoiquuid: 8590cc75-11c8-450d-90e8-56744e12ac70
index: y
internal: n
snippet: y
translation-type: ht
source-git-commit: cfb1b02a6261c001392b5cc6430f00206e802bb8

---


# Descarga web{#web-download}

La actividad **Web download** inicia la descarga de un archivo en una dirección URL explícita, una cuenta externa o una instancia de Adobe Campaign. Se utiliza el protocolo HTTP. Puede ser una descarga GET o POST.

## Propiedades {#properties}

1. **Selecting the Web file**

   Para especificar el archivo que se va a descargar, puede introducir la URL del archivo, utilizar la cuenta HTTP externa donde el archivo se almacena o cargar el archivo mediante una instancia de Adobe Campaign. Los parámetros disponibles se detallan a continuación:

   * Para introducir directamente la URL del archivo a descargar, seleccione la opción **[!UICONTROL URL explícita]** y especifique la URL en el campo correspondiente. Esta URL se puede construir con datos variables.

      ![](assets/download_web_edit.png)

   * Para utilizar un **[!UICONTROL Cuenta externa]**, seleccione la cuenta de la lista desplegable y especifique el archivo a descargar.

      Las cuentas externas se configuran en el nodo **[!UICONTROL Administración > Plataforma > Cuentas externas]** del árbol de Adobe Campaign. Los parámetros de la cuenta se pueden editar mediante el icono **[!UICONTROL Editar vínculo]**.

      ![](assets/download_web_edit_external.png)

   * Para descargar el archivo desde el entorno de Adobe Campaign, seleccione la opción **[!UICONTROL Instancia de Adobe Campaign]**.

      ![](assets/download_web_edit_instance.png)

1. **File historization**

   El vínculo **[!UICONTROL Configurar la historia de archivos...]** permite especificar el directorio de almacenamiento de archivos y su frecuencia de depuración.

   ![](assets/download_web_edit_hist.png)

   Estas son las opciones disponibles:

   * **[!UICONTROL Usar un directorio de almacenamiento predeterminado]**: el archivo siempre se mueve antes de ser procesado. Si se selecciona esta opción, el archivo se mueve al directorio de almacenamiento predeterminado (el directorio **vars** de la carpeta de instalación de Adobe Campaign). Para especificar un directorio de almacenamiento, anule la selección del cuadro e introduzca su trazado en el campo **[!UICONTROL Directorio de almacenamiento]**
   * **[!UICONTROL Número de archivos]**: introduzca el número máximo de archivos que se guardarán en el directorio de almacenamiento.
   * **[!UICONTROL Tamaño máximo (in Mb)]**: introduzca la capacidad máxima del directorio de almacenamiento (en megabytes).
   Cada archivo se conserva durante 24 horas. Después se somete a las reglas de depuración definidas. La depuración se realiza justo antes del inicio de la actividad y, por tanto, no tiene en cuenta el archivo de flujo de trabajo en curso.

   Los archivos se eliminan en función de su antigüedad (del más antiguo al más reciente). Los archivos más antiguos se purgan hasta que se hayan comprobado ambas reglas de purga. Por lo tanto, si se define un límite de 100 archivos, significa que el directorio de almacenamiento contendrá siempre los 100 archivos más recientes (antes del inicio del flujo de trabajo), así como los que se procesan en el flujo de trabajo en curso.

   Cuando no desee definir un límite para las opciones **[!UICONTROL Número de archivos]** y **[!UICONTROL Tamaño máximo (in Mb)]**, introduzca 0 como valor.

1. **Parámetros avanzados**

   El vínculo **[!UICONTROL Parámetros avanzados...]** permite especificar las siguientes opciones adicionales:

   ![](assets/download_web_edit_advanced.png)

   La opción **[!UICONTROL Procesar errores]** se detalla en [Procesar errores](../../workflow/using/monitoring-workflow-execution.md#processing-errors).

## Parámetros de salida {#output-parameters}

* filename

   Nombre completo del archivo descargado.

