---
title: '"Ejemplos de uso: creación de gestión de contenido"'
seo-title: '"Ejemplos de uso: creación de gestión de contenido"'
description: '"Ejemplos de uso: creación de gestión de contenido"'
seo-description: null
page-status-flag: never-activated
uuid: 204a63eb-40dd-446d-a847-4e55ad23b2bd
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: delivery
content-type: reference
topic-tags: content-management
discoiquuid: a4c62580-664d-47fe-87f5-cfe608b05e6f
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 1c86322fa95aee024f6c691b61a10c21a9a22eb7

---


# Ejemplos de uso: creación de gestión de contenido{#use-case-creating-content-management}

Para crear la gestión de contenido en Adobe Campaign, siga los siguientes pasos:

* [Paso 1: Análisis del contenido a producir](#step-1---analyzing-the-content-to-be-produced),
* [Paso 2: Creación del esquema de datos](#step-2---creating-the-data-schema),
* [Paso 3: Creación del formulario de entrada](#step-3---creating-the-input-form),
* [Paso 4: Creación de la plantilla de construcción](#step-4---creating-the-construction-template),
* [Paso 5: Creación de la plantilla de publicación](#step-5---creating-the-publication-template),
* [Paso 6: Creación de contenidos](#step-6---creating-contents).

## Paso 1: Análisis del contenido a producir {#step-1---analyzing-the-content-to-be-produced}

Antes de comenzar, se debe realizar un análisis preciso del contenido que se va a producir: identifique los elementos que se van a mostrar, estudie las restricciones vinculadas a ellos, defina un tipo para cada elemento, etc. Asimismo, se deben diferenciar los elementos estáticos y los variables.

Por ejemplo, para crear un boletín informativo en HTML con el siguiente tipo de contenido:

![](assets/s_ncs_content_newsletter.png)

Este boletín informativo contiene tres tipos de elementos:

1. Elementos variables, cuyo contenido lo introduce o selecciona el usuario mediante un formulario de entrada durante la creación del envío.

   ![](assets/s_ncs_content_define_element_types.png)

1. Los campos personalizados que se introducen dinámicamente en función de la información guardada en la base de datos (el nombre y apellidos del destinatario, en este caso).

   ![](assets/s_ncs_content_define_dynamics.png)

1. Elementos estáticos, los mismos que para todos los boletines informativos.

   ![](assets/s_ncs_content_define_statics.png)

Los distintos elementos de este boletín informativo se agrupan en función de las reglas definidas en una plantilla JavaScript que hace referencia a todos los elementos que se van a insertar y conceptualiza su diseño.

Estos elementos se crean mediante un esquema dedicado que especifica los siguientes elementos para cada contenido: nombre, etiqueta, tipo, tamaño y cualquier otra información relevante para su procesamiento en Adobe Campaign.

## Paso 2: Creación del esquema de datos {#step-2---creating-the-data-schema}

Un esquema de datos es un documento XML asociado al contenido. Describe la estructura XML de los datos de este contenido.

>[!NOTE]
>
>Para obtener más información sobre la creación y configuración de esquemas de datos en Adobe Campaign, consulte [esta sección](../../configuration/using/about-schema-edition.md).
>
>Configuration elements specific to content management are detailed in [Data schemas](../../delivery/using/data-schemas.md).

Para crear un esquema de datos, aplique los pasos siguientes:

1. Open the Adobe Campaign Explorer and select the **[!UICONTROL Administration > Configuration > Data schemas]** node.

   Click the **[!UICONTROL New]** icon located above the list of data schemas.

1. Seleccione la **[!UICONTROL Create a schema]** opción para la administración de contenido y haga clic en **[!UICONTROL Next]**.

   ![](assets/s_ncs_content_create_schema.png)

1. Introduzca el nombre y la etiqueta del esquema en los campos correspondientes. Se puede añadir una descripción y vincular una imagen específica si es necesario.

   ![](assets/s_ncs_content_param_schema.png)

   Click **[!UICONTROL Next]** to validate.

1. Enter the content of the schema in the **[!UICONTROL Edit schema]** window.

   Use the **[!UICONTROL Insert]** button to create the schema content.

   ![](assets/s_ncs_content_param_schema_step2.png)

   For more on this, refer to [Editing schemas](../../delivery/using/data-schemas.md#editing-schemas).

   Para cada elemento al que se hace referencia en el contenido, se debe seleccionar un tipo que corresponda.

   En este ejemplo, los contenidos identificados, su formato y su tipo son:

<table> 
 <thead> 
  <tr> 
   <th> <strong>Contenido</strong><br /> </th> 
   <th> <strong>Formato</strong><br /> </th> 
   <th> <strong>Tipo</strong> <br /> </th> 
   <th> <strong>Etiqueta</strong><br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> Título<br /> </td> 
   <td> Atributo<br /> </td> 
   <td> Cadena<br /> </td> 
   <td> Título<br /> </td> 
  </tr> 
  <tr> 
   <td> Subtítulo<br /> </td> 
   <td> Atributo<br /> </td> 
   <td> Cadena<br /> </td> 
   <td> Nombre<br /> </td> 
  </tr> 
  <tr> 
   <td> Fecha del evento<br /> </td> 
   <td> Atributo<br /> </td> 
   <td> Fecha<br /> </td> 
   <td> Fecha<br /> </td> 
  </tr> 
  <tr> 
   <td> Párrafo de introducción<br /> </td> 
   <td> Elemento<br /> </td> 
   <td> HTML<br /> </td> 
   <td> Información general<br /> </td> 
  </tr> 
  <tr> 
   <td> Fotografía del autor<br /> </td> 
   <td> Atributo<br /> </td> 
   <td> Cadena<br /> </td> 
   <td> URL<br /> </td> 
  </tr> 
  <tr> 
   <td> Autor<br /> </td> 
   <td> Elemento<br /> </td> 
   <td> Nota<br /> </td> 
   <td> Autor<br /> </td> 
  </tr> 
  <tr> 
   <td> Logotipo de encabezado (almacenado en recursos públicos de Adobe Campaign)<br /> </td> 
   <td> Atributo<br /> </td> 
   <td> Enlace<br /> </td> 
   <td> Imagen<br /> </td> 
  </tr> 
 </tbody> 
</table>

El esquema contiene la siguiente información:

```
<element label="Invitation" name="invitation" template="ncm:content" xmlChildren="true">
    <compute-string expr="@name"/>
    <attribute label="Title" length="40" name="title" type="string"/>
    <element label="Presentation" name="presentation" type="html"/>
    <attribute label="Date" name="date" type="date"/>
    <attribute label="Name" length="10" name="name" type="string"/>
    <attribute label="URL" name="url" type="string"/>
    <element label="Author" name="author" type="memo"/>
    <element label="Image" name="image" target="xtk:fileRes" type="link"/>
  </element>
```

1. Click **[!UICONTROL Save]** to create the data schema.

## Paso 3: Creación del formulario de entrada {#step-3---creating-the-input-form}

El formulario de entrada permite editar una instancia de contenido a través de una interfaz de entrada desde la consola del cliente de Adobe Campaign.

La descripción de un formulario es un documento XML estructurado que observa la gramática del esquema del formulario “xtk:form”.

>[!NOTE]
>
>Para obtener más información sobre la creación y configuración de formularios en Adobe Campaign, consulte [esta sección](../../configuration/using/identifying-a-form.md).
>
>Configuration elements specific to content management are detailed in [Input forms](../../delivery/using/input-forms.md).

Para crear un formulario de entrada de la gestión de contenido, siga estos pasos:

1. Open the Adobe Campaign Explorer and select the **[!UICONTROL Administration > Configuration > Input forms]** node.

   Click the **[!UICONTROL New]** icon above the list of forms.

1. Enter the name of the form and the label linked to the form, then select the **[!UICONTROL Content management]** type.

   ![](assets/s_ncs_content_param_form_edit.png)

   >[!NOTE]
   >
   >Para que ambos elementos coincidan automáticamente, se recomienda utilizar el mismo nombre que con el esquema de datos vinculado. Use the **[!UICONTROL Insert]** button above the input zone to add fields from the schema linked to the form.

   ![](assets/s_ncs_content_param_form_edit_step2.png)

1. En la sección central del editor, especifique los campos que desea mostrar en el formulario de entrada.

   En este ejemplo, tenemos el siguiente tipo de información:

   ```
    <input xpath="@title"/>
     <input xpath="@date"/>
     <input xpath="presentation"/>
     <input xpath="@name"/>
     <input xpath="@url"/>
     <input xpath="author"/>
     <input img="nl:sryimage.png" newEntityFormChoice="true" xpath="image">
       <sysFilter>
         <condition expr="@isImage = true"/>
       </sysFilter>
     </input>
   ```

   The **[!UICONTROL Preview]** tab lets you check the rendering of the form while you are editing it:

   ![](assets/s_ncs_content_param_form_preview.png)

1. Click **[!UICONTROL Save]** to create the input form.

## Paso 4: Creación de la plantilla de construcción {#step-4---creating-the-construction-template}

El lenguaje XSLT permite transformar un documento XML en otro documento de salida. Esta transformación se describe en XML en un documento denominado hoja de estilo.

En este ejemplo, deseamos utilizar una plantilla JavaScript para definir el modo de construcción y diseño de datos en el documento generado.

>[!NOTE]
>
>Constraints linked to document building (JavaScript or XSL template) are detailed in [Formatting](../../delivery/using/formatting.md).

Para utilizar una plantilla JavaScript en Adobe Campaign, siga los siguientes pasos:

1. Open the Adobe Campaign Explorer and select the **[!UICONTROL Administration > Configuration > JavaScript Templates]** node.

   Click the **[!UICONTROL New]** icon above the list of templates.

1. Introduzca un nombre de plantilla y seleccione el esquema que ha creado para el gestor de contenido.
1. Importe el contenido establecido que desea mostrar en el mensaje.

   Add the variable elements while respecting the syntax detailed in [JavaScript templates](../../delivery/using/formatting.md#javascript-templates).

   Para visualizar el contenido mostrado en nuestro ejemplo, la plantilla JavaScript debe contener los siguientes elementos:

   ```
   <html>
   <% eval(xtk.javascript.load("xac:perso").data); %>
   <head>
     <title>Invitation to an exceptional dedication session</title>
   </head>
   <body link="#0E59AE" vlink="#0E59AE" alink="#0E59AE" style="background-color:white;">
       <table width="546" border="0" align="center" cellpadding="0" cellspacing="0" style="border-left: solid 1px gray;border-top: solid 1px gray;border-right: solid 1px gray;">
         <tr>
           <td colspan="3">
             <%= generateImgTag(content.@["image-id"]) %>
           </td>
         </tr>
       </table>
       <table width="546" border="0" align="center" cellpadding="0" cellspacing="0" style="border-left: solid 1px gray;border-right: solid 1px gray;">
         <tr>
           <td>
             <table border="0" cellspacing="0" cellpadding="5">
               <tr>
                 <td width="10"> </td>
                 <td style="padding-top:2em; padding-bottom:2em;" width="730" align="middle">
                   <b>
                     <font style="font-family:Verdana, Arial, Helvetica, sans-serif; font-size:14px; color:#800080;">
                       <span style="FONT-VARIANT: small-caps"><%= content.@title %> - <%= content.@name %></span>
                     </font>
                   </b>
                 </td>
                 <td width="10"> </td>
               </tr>
               <tr>
                 <td width="10"> </td>
                 <td style="padding-top:1em; padding-bottom:1em;" width="730">
                   <font style="font-family:Verdana, Arial, Helvetica, sans-serif; font-size:11px; color:#666666;">
                     Hello <%= perso('recipient.firstName') %> <%= perso('recipient.lastName') %>,
                     <p>
                       <%= content.presentation %>
                     </p>               
                     <center>
                       <b><%= formatDate(content.@date, "%2D %Bl %4Y") %></b> come to our Book Fair and meet our favorite authors and illustrators.<br>
                       <br>
                       <a href="https://www.site.web.com/registration" target="_blank"><b>REGISTER</b></a>
                     </center>
                   </font>
                 </td>
                 <td width="10"> </td>
               </tr>
               <tr>
                 <td width="10"> </td>
                 <td style="padding-top:1em; padding-bottom:1em;" width="730">
                   <font style="font-family:Verdana, Arial, Helvetica, sans-serif; font-size:11px; color:#666666;">
                    <img style="float:left;margin-right:10px" border="0" src="<%= content.@url %>" width="70" height="70">
                     <b><%= content.author %></b>, will be signing their book between 2
   and 5:30PM.
                   </font>
                 </td>
                 <td width="10"> </td>
               </tr>            
                   <tr>
                 <td width="10"> </td>
                 <td width="730">
                   <font style="font-family:Verdana, Arial, Helvetica, sans-serif; font-size:11px; color:#666666;">                  
                 </td>
                 <td width="10"> </td>
               </tr>           
               <tr>
                 <td width="10"> </td>
                 <td>
                   <font style="font-family:Verdana, Arial, Helvetica, sans-serif; font-size:11px; color:#666666;">
                     <center>
                       <p>
                         <a href="https://www.site.web.com/program" target="_blank"><span style="FONT-VARIANT: small-caps"><b>Program</b></span></a>
                          | 
                         <a href="https://www.site.web.com/information" target="_blank"><span style="FONT-VARIANT: small-caps"><b>Useful information</b></span></a>
                          | 
                       <a href="https://www.site.web.com/registration" target="_blank"><span style="FONT-VARIANT: small-caps"><b>Register</b></span></a></p>
                       </center>
                     </font>
                   </td>
                   <td width="10"> </td>
                 </tr>
               </table>
               <br>
             </td>
           </tr>
         </table>
   </body>
   </html>
   ```

   Llamar a una función al comienzo de una plantilla permite configurar una llamada a los datos de personalización tomados de la base de datos de Adobe Campaign (en este caso: recipient.firstName y recipient.lastName), de manera que se pueda interpretar cuando se utilice en un envío. Para obtener más información sobre esto, consulte [Inclusión de una plantilla](../../delivery/using/formatting.md#including-a-javascript-template)de JavaScript.

   En este ejemplo, la función contiene el siguiente código:

   ```
   function perso(strPerso)
   {
     var strStart = '<' + '%' + '=';
     var strEnd = '%' + '>';
     return strStart + strPerso + strEnd;
   }
     function bloc(strPerso)
   {
     var strStart = '<' + '%' + '@ include view="';
     var strEnd = '" %' + '>';
     return strStart + strPerso + strEnd;
   }
   ```

   In order for the JavaScript template to be valid, this function must be created beforehand from the **[!UICONTROL JavaScript codes]** node in the tree structure, as below:

   ![](assets/contentmgt_jscode_perso_sample.png)

## Paso 5: Creación de la plantilla de publicación {#step-5---creating-the-publication-template}

El siguiente paso implica la creación de una plantilla de publicación de contenido para vincular el esquema, el formulario y la plantilla de construcción de contenido. Esta plantilla de publicación puede tener varios formatos de salida.

>[!NOTE]
>
>For more on content publication templates, refer to [Publication templates](../../delivery/using/publication-templates.md).

En este ejemplo, los pasos son los siguientes:

1. Cree una nueva plantilla de publicación mediante el **[!UICONTROL Administration > Configuration > Publication templates]** nodo.
1. Introduzca un nombre y una etiqueta y seleccione el esquema y el formulario que desea utilizar.
1. A continuación, introduzca el nombre de la plantilla y elija el modo de renderización que desee aplicar. Here, we have a **[!UICONTROL JavaScript]** type rendering based on the template created above.

   ![](assets/s_ncs_content_param_form_publish.png)

   >[!NOTE]
   >
   >The **[!UICONTROL DOM interface]** option is checked by default and this means that this document will not be accessible if you use the E4X syntax. La interfaz DOM debe utilizarse cuando se active esta opción, y es la sintaxis recomendada.
   >
   >Puede seguir utilizando la sintaxis E4X. Si es así, asegúrese de desactivar esta opción.

   Use the **[!UICONTROL Add]** button to create other transformation templates.

1. Click **[!UICONTROL Save]** to create the publication template.

## Paso 6: Creación de contenidos {#step-6---creating-contents}

Ahora se puede crear contenido basado en esta plantilla de publicación.

>[!NOTE]
>
>Para obtener más información sobre la creación de contenido, consulte [Uso de una plantilla](../../delivery/using/using-a-content-template.md)de contenido.

### Creación de contenido en el asistente de envío {#creating-content-in-the-delivery-wizard}

Para crear contenido directamente en los envíos, aplique los pasos siguientes:

1. Start by referencing the publication template via the **[!UICONTROL Advanced]** tab of the delivery properties.

   ![](assets/s_ncs_content_in_delivery.png)

   Se agrega una pestaña adicional al asistente de envío para definir el contenido a través del formulario del gestor de contenido.

1. Introduzca la información variable del boletín informativo.

   ![](assets/s_ncs_content_in_delivery_edition_tab.png)

1. Click the **[!UICONTROL HTML preview]** tab to view the rendering. Se debe seleccionar un destinatario para probar la personalización.

   ![](assets/s_ncs_content_use_in_delivery_preview.png)
