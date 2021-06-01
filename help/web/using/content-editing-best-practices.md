---
product: campaign
title: Recomendaciones para la edición de contenido
description: Recomendaciones para la edición de contenido
audience: web
content-type: reference
topic-tags: editing-html-content
exl-id: c1eccb48-59bf-412f-9c18-9cda2a022096
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: tm+mt
source-wordcount: '548'
ht-degree: 100%

---

# Recomendaciones para la edición de contenido{#content-editing-best-practices}

Para garantizar la operación óptima del editor, se recomienda seguir las siguientes directrices:

* Antes de **importar una plantilla de página HTML** en Adobe Campaign, asegúrese de que la plantilla se abra y se muestre correctamente en los distintos navegadores.
* Si la página HTML contiene **secuencias de comandos JavaScript**, deben ejecutarse **sin errores** fuera del editor.
* Al crear una plantilla, se recomienda añadir un atributo **“type”** a las etiquetas `<input>` El editor procesa esta información, que ayuda al usuario a vincular un campo de la base de datos al campo del formulario al configurar la aplicación web.

   Ejemplo de código HTML en la plantilla:

   ```
   <input id="email" type="email" name="email"/>
   ```

   El atributo **“type”** es visible en la interfaz en el siguiente formulario:

   ![](assets/dce_sidebar_inputtypechanges.png)

   La lista oficial de atributos &quot;type&quot; está disponible [en este sitio web](https://www.w3schools.com/tags/att_input_type.asp).

* Pasos para simular una página final con el DCE:

   ![](assets/dce_enchainement.png)

* Compruebe que solo haya uno en la página.`<body> </body>`
* Cuando se carga un archivo CSS o JS, no se cargan las imágenes incluidas en el archivo .zip. Por lo tanto, las referencias a estas imágenes presentes en CSS no se actualizan.

## Formatos compatibles con el editor de contenido {#content-editor-supported-formats}

El editor de contenido es compatible con el formato HTML: se puede volver a cambiar al modo **fuente** en cualquier momento.

La función de importación del editor de contenido funciona de la siguiente manera con los siguientes formatos compatibles:

* CSS: las imágenes presentes en el archivo .zip no se importan. Las referencias a estas imágenes en CSS no se actualizan.
* JS: las imágenes presentes en el archivo .zip no se importan. No se actualizan las referencias a estas imágenes en JS.
* Iframe: las páginas vinculadas no se importan.
* Páginas de destino y aplicaciones web: si falta una etiqueta **form**, aparece una advertencia. En el cuerpo del mensaje siempre debe estar presente `<form> </form>`.

El editor de contenido también funciona con las siguientes páginas de códigos compatibles:

* iso-8859-1
* iso-8859-2
* utf-7
* utf-8 (recomendado cuando se utiliza una BOM)
* iso-8859-15
* us-ascii
* shift jis
* iso-2022-jp
* big-5
* euc-kr
* utf-16

>[!NOTE]
>
>La página de códigos HTML debe definirse en una etiqueta meta (HTML 4 o HTML 5) o en la BOM. Si no hay ninguna página de códigos disponible, abra el archivo en latin1.

## Estados de contenido HTML {#html-content-statuses}

La sección superior del editor muestra mensajes relacionados con el estado del contenido. Los códigos de color para los mensajes son los siguientes:

* **Mensaje gris**: mensaje de información, no es necesario realizar ninguna acción en el editor.
* **Mensaje azul**: mensaje de información relacionado con el contenido que se está editando.
* **Mensaje amarillo**: advertencia o mensaje de error que requiere alguna acción en nombre del usuario.

### Lista de mensajes al editar una aplicación web {#list-of-messages-when-editing-a-web-application}

* El contenido HTML funciona.
* No se ha publicado la aplicación web y no se puede acceder en línea.
* La aplicación web está en línea. Vuelva a publicar para aplicar cualquier cambio.
* El contenido de la página no funciona. Debe incluir un formulario HTML (`<form>`)
* Hay “n” zonas o botones de entrada para configurar.
* Para activar la transición a la página siguiente, se debe vincular la acción “Página siguiente” a un botón o a un vínculo de la página actual.

### Lista de mensajes al editar una entrega {#list-of-messages-when-editing-a-delivery}

* El contenido de la entrega funciona
* Hay “n” campos o bloques de personalización para configurar.
* El contenido de la entrega está listo. Vuelva a ejecutar el análisis para aplicar los cambios.
* El envío está listo para ejecutarse.
