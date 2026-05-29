---
product: campaign
title: Generación de documentos PDF personalizados
description: Obtenga información sobre cómo generar documentos PDF personalizados
badge-v8: label="También se aplica a v8" type="Positive" tooltip="También se aplica a Campaign v8"
feature: Personalization
role: User
hide: true
exl-id: e5239d99-256b-412b-be20-f64f822da9c3
TQID: https://experienceleague.adobe.com/5hETJLlKZ9iWu2k1nW-RMeDlzpSm7wFwfe3QwSEZCa4
product_v2: id: dfc56824-e8b9-499e-85d4-21aedb507314
role_v2: id: b69b2659-1057-424e-8fc5-ed9e016dc554
topic_v2: id: bce87dde-a4ab-44c9-8a18-ad66e4ddb377id: e0eb8757-182f-49f3-94a4-1587d16f5094
feature_v2: id: b631758a-142d-425f-b9aa-f756d85cb979id: c858a28b-ea19-49b0-8d48-828717fad89c
subfeature_v2: id: e95a583b-fcfa-4524-8666-46a29c828119id: c8da4fdd-eb94-4751-a43c-f82733fb2d6eid: d5bbe3da-ba85-4242-817e-54f7c4b943e0id: f4da0e76-df77-451e-ad61-21afb7bd8810
source-git-commit: 38eab6b8da73163e4476e91c0ef73f25c3f57546
workflow-type: tm+mt
source-wordcount: 461
ht-degree: 100%

---

# Generación de documentos PDF personalizados{#generating-personalized-pdf-documents}

## Acerca de los documentos PDF variables {#about-variable-pdf-documents}

Adobe Campaign permite generar documentos PDF variables para archivos adjuntos de correo electrónico a partir de documentos de LibreOffice o Microsoft Word.

Se admiten las siguientes extensiones: “.docx”, “.doc” y “.odt”.

Para personalizar los documentos, se encuentran disponibles las mismas funcionalidades de JavaScript que para la personalización del correo electrónico.

Debe activar la opción **[!UICONTROL "The content of the file is personalized and converted to PDF during the delivery of each message"]**. Esta opción está accesible al adjuntar el archivo al correo electrónico de entrega. Para obtener más información sobre cómo adjuntar un archivo calculado, consulte la [Documentación de la versión 8 de Campaign](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/emails/attaching-files.html?lang=es){target="_blank"}.

Ejemplo de personalización de encabezado de factura:

![](assets/s_ncs_pdf_simple.png)

Para generar tablas dinámicas o incluir imágenes a través de una URL, se debe seguir un proceso específico.

## Generación de tablas dinámicas {#generating-dynamic-tables}

El procedimiento para generar tablas dinámicas es el siguiente:

* Cree una tabla con tres líneas y tantas columnas como sea necesario y, a continuación, configure su diseño (bordes, etc.).
* Sitúe el cursor en la tabla y haga clic en el menú **[!UICONTROL Table > Table properties]**. Vaya a la pestaña **[!UICONTROL Table]** e introduzca un nombre que comience por **NlJsTable**.
* En la primera celda de la primera línea, defina un bucle (“for”, por ejemplo) que permita la iteración en los valores que desea mostrar en la tabla.
* En cada celda de la segunda línea de la tabla, inserte secuencias de comandos que devuelvan los valores que desea mostrar.
* Cierre el bucle en la tercera y en la última línea de la tabla.

  Ejemplo de definición de tabla dinámica:

  ![](assets/s_ncs_pdf_table.png)

## Inserción de imágenes externas {#inserting-external-images}

La inserción de imágenes externas resulta útil si, por ejemplo, se desea personalizar un documento con una imagen cuya URL se introduce en un campo del destinatario.

Para ello, se debe configurar un bloque personalizado y, a continuación, incluir una llamada al bloque personalizado en el archivo adjunto.

**Ejemplo: inserción de un logotipo personalizado según el país del destinatario**

**Paso 1: Creación del archivo adjunto:**

* Inserte la llamada al bloque de personalización: **&lt;%@ include view=&quot;blockname&quot; %>**.
* Inserte el contenido (personalizado o no) en el cuerpo del archivo.

![](assets/s_ncs_open_office_blocdeperso.png)

**Paso 2: Creación del bloque personalizado:**

* Vaya al menú **[!UICONTROL Resources > Campaign management > Personalization blocks]** de la consola de Adobe Campaign.
* Cree un nuevo bloque personalizado llamado “My Logo” con “My_Logo” como nombre interno.
* Haga clic en el vínculo **[!UICONTROL Advanced parameters...]** y luego marque la opción **[!UICONTROL "The content of the block is included in an attachment"]**. Esto permite copiar la definición del bloque personalizado directamente en el contenido del archivo de OpenOffice.

  ![](assets/s_ncs_pdf_bloc_option.png)

  Se deben diferenciar dos tipos de declaraciones dentro del bloque personalizado:

   * El código de Adobe Campaign de los campos personalizados, en los que las comillas angulares de “apertura” y “cierre” se deben reemplazar por caracteres de escape (`&lt;` y `&gt;` respectivamente).
   * Todo el código XML de OpenOffice se copia en el documento de OpenOffice.

En el ejemplo, el bloque personalizado tiene este aspecto:

```
<% if (recipient.country.label == "Germany") { %>
<draw:frame svg:width="4cm" svg:height="3cm">
<draw:image xlink:href=https://..../logo_germany.png />
</draw:frame>
<% } else
if (recipient.country.label == "USA")
{ %>
<draw:frame svg:width="4cm" svg:height="3cm">
<draw:image xlink:href=https://..../logo_USA.png />
</draw:frame>
<% } %>
```

Según el país del destinatario, la personalización se puede ver en el documento vinculado a la entrega:

![](assets/s_ncs_pdf_result.png)
