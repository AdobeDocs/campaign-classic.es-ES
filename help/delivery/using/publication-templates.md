---
product: campaign
title: Plantillas de publicación
description: Plantillas de publicación
audience: delivery
content-type: reference
topic-tags: content-management
exl-id: 3b6e4974-4551-4da2-8eca-577c4f9cbd91
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: tm+mt
source-wordcount: '824'
ht-degree: 100%

---

# Plantillas de publicación{#publication-templates}

## Acerca de las plantillas de publicación {#about-publication-templates}

La plantilla de publicación es la tarjeta de identidad del contenido que se va a publicar. Hace referencia a los recursos utilizados en el proceso de publicación, por ejemplo:

* el esquema de datos,
* el formulario de entrada,
* las plantillas de transformación para cada documento de salida.

## Identificación de una plantilla de publicación {#identification-of-a-publication-template}

Una plantilla de publicación se identifica con su nombre y área de nombres.

La clave de identificación de una hoja de estilo es una cadena formada por el área de nombres y el nombre separado por dos puntos; por ejemplo.**cus:newsletter**.

>[!NOTE]
>
>En la práctica, se recomienda utilizar la misma clave para el esquema, el formulario y la plantilla de publicación.

## Creación y configuración de la plantilla {#creating-and-configuring-the-template}

Las plantillas de publicación se almacenan de forma predeterminada en el nodo **[!UICONTROL Administration > Configuration > Publication templates]**. Para crear una nueva plantilla, haga clic en el botón **[!UICONTROL New]** situado sobre la lista de plantillas.

Para configurar la plantilla de publicación, rellene el nombre de la plantilla (es decir, la clave de identificación que contiene el nombre y el área de nombres), su etiqueta, el esquema de datos y el formulario de entrada al que está vinculado.

![](assets/d_ncs_content_model.png)

>[!NOTE]
>
>La etiqueta aparece siempre que se cree contenido en función de esta plantilla de publicación.

La opción **Comprobar el estado para validar la generación de contenido** obliga a comprobar el estado “validado” de las instancias de contenido para autorizar la generación de archivos. Para obtener más información, consulte [Publicación](#publication).

Se debe agregar una plantilla de transformación para cada documento de salida. Puede crear tantas plantillas de transformación como sea necesario.

El campo **[!UICONTROL Name of template]** es una etiqueta libre que describe el tipo de representación en la salida. La configuración de publicación está disponible en las pestañas de cada plantilla de transformación.

### Renderización {#rendering}

En la pestaña **[!UICONTROL Rendering]**, elija:

* el tipo de renderización utilizada para proyectar el documento de salida: hoja de estilo XSL o plantilla JavaScript,
* el formato del documento de salida: HTML, Texto, XML o RTF,
* la plantilla que contiene los datos de construcción, es decir, la hoja de estilo o plantilla JavaScript que se va a utilizar.

### Publicación {#publication}

La publicación implica generar el documento de salida en forma de archivo, si el tipo seleccionado es **[!UICONTROL File]**.

![](assets/d_ncs_content_model2.png)

Estas son las opciones de publicación disponibles:

* Se puede forzar el conjunto de caracteres de codificación del archivo de salida a través del campo **[!UICONTROL Encoding]**. El conjunto de caracteres Latin 1 (1252) se utiliza de forma predeterminada.
* La opción **[!UICONTROL Multi-file generation]** activa un modo especial de publicación del documento. Esta opción consiste en rellenar una etiqueta de partición al principio de cada página del documento de salida. La generación del contenido genera un archivo para cada etiqueta de partición completada. Este modo se utiliza para generar minisitios a partir de un bloque de contenido. Para obtener más información, consulte [Generación de varios archivos](#multi-file-generation).
* El campo **[!UICONTROL Location]** contiene el nombre del archivo de salida. El nombre puede estar compuesto por variables para generar un nombre de archivo automático.

   Una variable se rellena con el siguiente formato: **`$(<xpath>)`**, donde **`<xpath>`** es la ruta de un campo del esquema de datos de la plantilla de publicación.

   El nombre de un archivo puede constar de un campo de tipo fecha. Para aplicar formato a este campo correctamente, utilice la función **$date-format**, utilizando la ruta del campo y el formato de salida como parámetros.

   De forma predeterminada, el formato de construcción del nombre de archivo utiliza las variables en los campos “@nombre” y “@fecha”:

   ```
   ct_$(@name)_$date-format(@date,'%4Y%2M%2D').htm
   ```

   El nombre de archivo generado tendrá el siguiente aspecto: ct_news12_20110901.htm.

   >[!NOTE]
   >
   >Para obtener más información sobre la generación de contenido, consulte [Creación de una instancia de contenido](../../delivery/using/using-a-content-template.md#creating-a-content-instance).

### Entrega {#delivery}

Esta pestaña permite seleccionar un escenario para iniciar una entrega directamente sobre el contenido. El contenido del correo electrónico se rellena automáticamente según el formato de salida (HTML o texto).

![](assets/d_ncs_content_model3.png)

>[!NOTE]
>
>Para ver un ejemplo de creación de envíos basado en un contenido, consulte [Creación de una instancia de contenido](../../delivery/using/using-a-content-template.md#delivering-a-content-instance).

### Acumulador {#aggregator}

La acumulación de datos de una secuencia de comandos o una lista de consulta permite enriquecer el documento XML con los datos del contenido. El objetivo es complementar cierta información a la que se hace referencia mediante vínculos o añadir elementos de la base de datos.

### Generación de varios archivos {#multi-file-generation}

Para activar la generación de varios archivos, seleccione la opción **[!UICONTROL Multi-file generation]** en el modelo de publicación. Esta opción le permite especificar etiquetas de partición en la hoja de estilos para el comienzo de cada página del documento de salida. La generación del contenido genera un archivo para cada etiqueta de partición encontrada.

La etiqueta de partición que se va a integrar en la hoja de estilos es la siguiente:

**`<xsl:comment> #nl:output_replace(<name_of_file>) </xsl:comment>`** where **`<name_of_file>`** es el nombre de archivo de la página que se va a generar.

**Ejemplo:** generación de varios archivos con el esquema “cus:book”.

El principio es generar una página principal que enumere los capítulos, con la posibilidad de mostrar los detalles del capítulo en una página externa.

![](assets/d_ncs_content_chunk.png)

La hoja de estilos correspondiente (“cus:book.xsl”) es la siguiente:

```
<?xml version="1.0" encoding="ISO-8859-1" ?>
<xsl:stylesheet xmlns:xsl="http://www.w3.org/1999/XSL/Transform" version="1.0">
  <xsl:output encoding="ISO-8859-1" method="html"/>

  <!-- Style sheet entry point -->
  <xsl:template match="/book">
    <html>
      <body>
        <h1><xsl:value-of select="@name"/></h1>
        <lu>
          <xsl:for-each select="chapter">
            <li><a target="_blank" href="chapter{@id}.htm"><xsl:value-of select="@name"/></a></li>  
          </xsl:for-each>
       </lu>
      </body>
    </html>
   </xsl:template>
</xsl:stylesheet>
```

Se requiere una segunda hoja de estilo (“cus:chapter.xsl”) para generar los detalles de los capítulos:

```
<?xml version="1.0" encoding="ISO-8859-1" ?>
<xsl:stylesheet xmlns:xsl="http://www.w3.org/1999/XSL/Transform" version="1.0">
  <xsl:output encoding="ISO-8859-1" method="html"/>

  <!-- Detail of a chapter -->
  <xsl:template match="chapter">
    <!-- Cut tag -->   
    <xsl:comment> #nl:output_replace($(path)/chapter<xsl:value-of select="@id"/>.htm)</xsl:comment>
    
    <html>
      <body>
        <h1><xsl:value-of select="@name"/></h1>
        <xsl:value-of select="page" disable-output-escaping="yes"/>
      </body>
    </html>
  </xsl:template>

  <!-- Style sheet entry point -->
  <xsl:template match="/book">
    <xsl:apply-templates/>
   </xsl:template>
</xsl:stylesheet>
```

La etiqueta de partición se rellena al comienzo de la página para que se incluya en el archivo que se va a generar.

```
<xsl:comment> #nl:output_replace($(path)/<xsl:value-of select="@id"/>.htm)</xsl:comment>
```

El nombre de archivo se construye con la variable **$(path)**, que contiene la ruta de publicación y **`<xsl:value-of select="@id" />`**, que coincide con el identificador del capítulo en el documento de entrada.

El modelo de publicación debe rellenarse con las dos hojas de estilo “cus:book.xsl” y “cus:chapter.xsl”.

La opción **[!UICONTROL Multi-file generation]** debe estar activa en el modelo de transformación de capítulos:

![](assets/d_ncs_content_chunk2.png)

El campo **[!UICONTROL Location]** no se utiliza en la generación de varios archivos, pero aun así debe rellenar este campo para evitar un error al publicar.
