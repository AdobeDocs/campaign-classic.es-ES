---
solution: Campaign Classic
product: campaign
title: Instrucciones de preprocesamiento para direcciones URL rastreadas
description: Obtenga más información sobre las instrucciones de preprocesamiento para utilizarlas para crear un script con la dirección URL de un correo electrónico y rastrearlas.
audience: delivery
content-type: reference
topic-tags: tracking-messages
translation-type: tm+mt
source-git-commit: 3454af2faffacd43fa1ad852529dad175340a237
workflow-type: tm+mt
source-wordcount: '636'
ht-degree: 1%

---


# Instrucciones de preprocesamiento {#pre-processing-instructions}

Las instrucciones &lt;%@ no son JavaScript, esta sintaxis es específica de Adobe Campaign.

Solo se aplican en el contexto del contenido de la entrega. Es la única forma de crear una secuencia de comandos de la dirección URL de un correo electrónico y de seguir realizándolo (además de los parámetros de URL). Se pueden ver como una copia y pegado automáticos aplicados durante el análisis de envío antes de detectar los vínculos que se van a rastrear.

Existen tres tipos de instrucciones:

* &quot;**include**&quot;: principalmente para factorizar algunas opciones de código en , bloques de personalización, archivos externos o páginas
* &quot;**valor**&quot;: para proporcionar acceso a los campos de la entrega, las variables de entrega y los objetos personalizados cargados en la entrega
* &quot;**foreach**&quot;: para crear un bucle de una matriz cargada como objeto personalizado.

Se pueden probar directamente desde el asistente de envíos. Se aplican en la vista previa del contenido y al hacer clic en el botón de seguimiento para ver la lista de las direcciones URL.

## &lt;>{#include}

Los siguientes ejemplos están entre los más utilizados:

* Incluido el vínculo de página espejo: `<%@ include view="MirrorPage" %>`
* URL de página espejo: &quot;Ver como `<a href="<%@ include view='MirrorPageUrl' %>" _label="Mirror Page" _type="mirrorPage">web page"`
* URL de baja predeterminada: `<%@ include option='NmsServer_URL' %>/webApp/unsub?id=<%= escapeUrl(recipient.cryptedId)%>`
* Otros ejemplos:
   * `<%@ include file='http://www.google.com' %>`
   * `<%@ include file='file:///X:/france/service/test.html' %>`
   * `<%@ include option='NmsServer_URL' %>`

Utilice el botón de personalización del asistente de envíos para obtener la sintaxis correcta.

## &lt;%@ value {#value}

Esta instrucción proporciona acceso a parámetros de la entrega que son constantes para todos los destinatarios.

Syntax:

`<%@ value object="myObject" xpath="@myField" index="1" %>`

Donde:

* &quot;object&quot;: nombre del objeto (ejemplo: envío, proveedor, etc.).
* &quot;xpath&quot;: xpath del campo.
* &quot;index&quot; (opcional): si &quot;object&quot; es una matriz (para objetos de secuencia de comandos adicionales), índice de elementos en la matriz (Comienza en 0).

El objeto puede ser:

* &quot;entrega&quot;: para la entrega actual (consulte los detalles y restricciones en la subsección siguiente).
* &quot;provider&quot;: para el proveedor/enrutamiento de envío actual (nms:externalAccount).
* Un objeto de secuencia de comandos adicional: si un objeto se carga en el contexto mediante: **Propiedades** > **Personalización** > **Agregar objetos en el contexto de ejecución**.
* Elemento del bucle foreach: consulte la sección [Foreach](#foreach) a continuación.

### objeto &quot;envío&quot; {#delivery-object}

Para la personalización del correo electrónico, se puede acceder al objeto de envío de dos maneras:

* En JavaScript. Por ejemplo: `<%= delivery.myField %>`.

   En la entrega de objetos JavaScript no se admiten campos personalizados. Funcionan en la vista previa, pero no en el MTA porque el MTA solo puede acceder al esquema de envío predeterminado.

* Mediante el procesamiento previo `<%@ value object="delivery"`.

Para la instrucción `<%@ value object="delivery" xpath="@myCustomField" %>`, existe otra limitación para los envíos enviados mediante intermediarios. El campo personalizado @myCustomField debe agregarse al esquema nms:delivery tanto en plataformas de marketing como de fuentes intermedias.

>[!NOTE]
>
>Para parámetros y variables de entrega, utilice la siguiente sintaxis (con el objeto de envío):
>
>`<%@ value object="delivery" xpath="variables/var[@name='myVar']/@stringValue" %>`

### &lt;>{#value-in-javascript}

Para permitir el uso del valor &lt;%@ en secciones de secuencias de comandos, se reemplazan dos objetos especiales por &lt;% y %>:

* `<%@ value object='startScript' %>`
* `<%@ value object='endScript' %>`

Por ejemplo:

```
<%@ value object='startScript' %> var iMode = <%@ value object="delivery" xpath="@deliveryMode" %> if(iMode == 1) { ... } else { ... }`
`<%@ value object='endScript' %> is expanded in something like <% var iMode = 1 if(iMode == 1) { ... } else { ... } %>.
```

## &lt;>{#foreach}

Esta instrucción permite la iteración en una matriz de objetos cargados en la entrega para rastrear vínculos individuales relacionados con los objetos.

Sintaxis:

`<%@ foreach object="myObject" xpath="myLink" index="3" item="myItem" %> <%@ end %>`

Donde:

* &quot;object&quot;: nombre del objeto desde el que se va a iniciar, normalmente un objeto de secuencia de comandos adicional, pero puede ser una entrega.
* &quot;xpath&quot; (opcional): xpath de la colección en la que se va a realizar un bucle. El valor predeterminado es &quot;.&quot;, lo que significa que el objeto es la matriz en la que se debe realizar el bucle.
* &quot;index&quot; (opcional): si xpath no es &quot;.&quot; y el objeto es una matriz en sí, índice de elemento del objeto (comienza en 0).
* &quot;elemento&quot; (opcional): nombre de un nuevo objeto accesible con valor &lt;%@ dentro del bucle foreach. Predeterminado con el nombre del vínculo en el esquema.

Ejemplo:

En las propiedades/personalización de la entrega, cargue una matriz de artículos y una tabla de relación entre el destinatario y los artículos.

La visualización de vínculos a estos artículos se puede realizar simplemente con un JavaScript de la siguiente manera:

```
<%
  for(var i=0; i<recipient.rcpArticle.length; i++ )
  {
    %><a href="http://nl.net?a.jsp?article=<%=recipient.rcpArticle[i].article.@id%>">article</a><%
  }
%>
```

Con esa solución, los vínculos a todos los artículos se rastrean sin distinción. Puede saber que un destinatario ha hecho clic en un vínculo de artículo, pero no puede saber en qué artículo.

La solución es:

1. Precargar todos los artículos posibles en una matriz de scripts extra de la entrega - articleList[] - lo que significa que debe haber un número finito de artículos posibles.
1. Escriba una función JavaScript al principio del contenido.

   ```
   <%@ value object='startScript' %>
   function displayArticle(articleId)
   {
     <%@ foreach object="articleList" item="article" %>
       if( articleId == <% value object="article" xpath="@id" %> ) 
       {
         <%@ value object='endScript' %>
           <a href="http://nl.net?a.jsp?article=<%@ value object="article" xpath="@id" %>">article</a>
         <%@ value object='startScript' %>
       } 
     <%@ end @%>
   }
   <%@ value object='endScript' %>
   ```
1. Muestre el artículo llamando a la función .

   ```
   <%
   for(var i=0; i<recipient.rcpArticle.length; i++ )
   {
    displayArticle(recipient.rcpArticle[i].article.@id)
   }
   %>
   ```

