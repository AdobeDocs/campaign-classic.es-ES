---
solution: Campaign Classic
product: campaign
title: Gestión de contenido
description: Gestión de contenido
audience: workflow
content-type: reference
topic-tags: action-activities
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '417'
ht-degree: 100%

---


# Gestión de contenido{#content-management}

Una actividad de **Content management** (gestión de contenido) permite crear y manipular contenidos y generar archivos basados en este contenido. Este contenido se puede entregar a través de la actividad “Envío”.

>[!CAUTION]
>
>El Gestor de contenido es un módulo opcional de Adobe Campaign. Compruebe el acuerdo de licencia.

Las propiedades de la actividad se dividen en tres pasos:

* **Content selection**: el contenido se puede crear previamente o a través de la actividad.
* **Content update**: la tarea puede modificar el asunto del contenido o importar todo el contenido XML.
* **Action**: el contenido resultante se puede guardar o generar.

   ![](assets/content_mgmt_edit.png)

   Para obtener más información sobre la configuración y el uso del Gestor de contenidos en Adobe Campaign, consulte esta [sección](../../delivery/using/about-content-management.md).

1. **Content**

   * **[!UICONTROL Specified in the transition]**

      Esta opción permite utilizar el contenido especificado en la transición, es decir, el evento que activa el Gestor de contenido debe contener una variable **[!UICONTROL contentId]**. Esta variable puede haber sido configurada por un gestor de contenido anterior o por cualquier script.

   * **[!UICONTROL Explicit]**

      Esta opción le permite seleccionar un contenido ya creado, a través del campo **[!UICONTROL Content]**. Este campo solo está visible cuando se selecciona la opción **[!UICONTROL Explicit]**.

      ![](assets/content_mgmt_explicit.png)

   * **[!UICONTROL Calculated by a script]**

      El identificador de contenido se calcula mediante una secuencia de comandos. El campo **[!UICONTROL Script]** permite definir una plantilla JavaScript que evalúe el identificador (clave principal) del contenido. Este campo solo está visible cuando se selecciona la opción **[!UICONTROL Calculated by a script]**.

      ![](assets/content_mgmt_script.png)

   * **[!UICONTROL New, created from a publication template]**

      Crea un nuevo contenido a partir de una plantilla de publicación. Los datos se almacenan en el archivo indicado en el campo **[!UICONTROL String]**. El campo **[!UICONTROL Template]** especifica la plantilla de publicación que se utiliza para crear el contenido.

      ![](assets/content_mgmt_new.png)

1. **Update content**

   * **[!UICONTROL Subject]**

      Este campo permite modificar el asunto del contenido.

   * **[!UICONTROL Access to data from an XML feed]**

      Esta opción permite construir el contenido de un documento XML descargado mediante una hoja de estilos XSL. Cuando se selecciona esta opción, el campo **[!UICONTROL URL]** especifica la URL de descarga del contenido XML. La **[!UICONTROL XSL stylesheet]** permite especificar la hoja de estilos que se utilizará para transformar el documento XML descargado. Esta propiedad es opcional.

      ![](assets/content_mgmt_xmlcontent.png)

1. **Acción que quiere ejecutar**

   * **[!UICONTROL Save]**

      Esta opción guarda el contenido creado o modificado.

      La transición saliente se activa solo una vez, con el contenido guardado en la variable **[!UICONTROL contentId]** como parámetro.

   * **[!UICONTROL Generate]**

      Esta opción guarda el contenido y genera los archivos de salida para cada plantilla de transformación con una publicación de tipo “Archivo”.

      ![](assets/content_mgmt_generate.png)

      La transición saliente se activa para cada archivo generado con el identificador del contenido guardado en la variable **[!UICONTROL contentId]** como parámetro y el nombre del archivo en la variable **[!UICONTROL filename]**.

## Parámetros de entrada {#input-parameters}

* contentId

Identificador del contenido que se va a utilizar si la opción **[!UICONTROL Specified in the transition]** está activada.

## Parámetros de salida {#output-parameters}

* contentId

   Identificador de contenido.

* filename

   Nombre completo del archivo generado si la acción seleccionada es **[!UICONTROL Generate]**.

## Ejemplos {#examples}

Se ofrecen ejemplos en esta [sección](../../delivery/using/automating-via-workflows.md#examples).
