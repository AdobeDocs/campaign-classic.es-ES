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
translation-type: tm+mt
source-git-commit: b1a961822224ab0a9551f51942a5f94cf201c8ee
workflow-type: tm+mt
source-wordcount: '401'
ht-degree: 56%

---


# Descarga web{#web-download}

La actividad **Web download** inicia la descarga de un archivo en una dirección URL explícita, una cuenta externa o una instancia de Adobe Campaign. Se utiliza el protocolo HTTP. Puede ser una descarga GET o POST.

## Propiedades {#properties}

1. **Selecting the Web file**

   Para especificar el archivo que se va a descargar, puede introducir la URL del archivo, utilizar la cuenta HTTP externa donde el archivo se almacena o cargar el archivo mediante una instancia de Adobe Campaign. Los parámetros disponibles se detallan a continuación:

   * To directly enter the URL of the file to be downloaded, select the **[!UICONTROL Explicit URL]** option and specify the URL in the appropriate field. Esta URL se puede construir con datos variables.

      ![](assets/download_web_edit.png)

   * To use an **[!UICONTROL External account]**, select the account from the drop-down list, and specify the file to be downloaded.

      External accounts are configured from the **[!UICONTROL Administration > Platform > External accounts]** node of the Adobe Campaign tree. The account parameters can be edited via the **[!UICONTROL Edit link]** icon.

      ![](assets/download_web_edit_external.png)

   * To download the file from the Adobe Campaign instance, select the **[!UICONTROL Adobe Campaign Instance]** option.

      ![](assets/download_web_edit_instance.png)

1. **File historization**

   The **[!UICONTROL File historization settings...]** link lets you specify the file storage directory and the purge frequency of this directory.

   ![](assets/download_web_edit_hist.png)

   Estas son las opciones disponibles:

   * **[!UICONTROL Use a default storage directory]**:: el archivo siempre se mueve antes de procesarse. Si se selecciona esta opción, el archivo se mueve al directorio de almacenamiento predeterminado (el directorio **vars** de la carpeta de instalación de Adobe Campaign). To specify a storage directory, uncheck the box and enter its path in the **[!UICONTROL Storage directory]** field
   * **[!UICONTROL Number of files]**:: introduzca el número máximo de archivos que se guardarán en el directorio de almacenamiento.
   * **[!UICONTROL Maximum size (in Mb)]**:: introduzca la capacidad máxima del directorio de almacenamiento (en megabytes).
   Cada archivo se conserva durante 24 horas. Después se somete a las reglas de depuración definidas. La depuración se realiza justo antes del inicio de la actividad y, por tanto, no tiene en cuenta el archivo de flujo de trabajo en curso.

   Los archivos se eliminan en función de su antigüedad (del más antiguo al más reciente). Los archivos más antiguos se purgan hasta que se hayan comprobado ambas reglas de purga. Por lo tanto, si se define un límite de 100 archivos, significa que el directorio de almacenamiento contendrá siempre los 100 archivos más recientes (antes del inicio del flujo de trabajo), así como los que se procesan en el flujo de trabajo en curso.

   If you no longer want to set a limit for the **[!UICONTROL Number of files]** and **[!UICONTROL Maximum size (in Mb)]** options, enter 0 as a value.

1. **Parámetros avanzados**

   The **[!UICONTROL Advanced parameters...]** link lets you specify the additional options shown below:

   ![](assets/download_web_edit_advanced.png)

   The **[!UICONTROL Process errors]** option is detailed in [Processing errors](../../workflow/using/monitoring-workflow-execution.md#processing-errors).

## Parámetros de salida {#output-parameters}

* filename: Nombre completo del archivo descargado.
