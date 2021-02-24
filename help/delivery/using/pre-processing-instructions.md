---
solution: Campaign Classic
product: campaign
title: Instrucciones de preprocesamiento para direcciones URL rastreadas
description: Obtenga más información sobre las instrucciones de preprocesamiento que se utilizarán para crear secuencias de comandos de la dirección URL de un correo electrónico y que se seguirá rastreando.
audience: delivery
content-type: reference
topic-tags: tracking-messages
translation-type: tm+mt
source-git-commit: 151667637a12667f5eda1590e64e01de493be9ce
workflow-type: tm+mt
source-wordcount: '636'
ht-degree: 1%

---


# Instrucciones de preprocesamiento {#pre-processing-instructions}

Las instrucciones de &lt;%@ no son JavaScript, esta sintaxis es específica de Adobe Campaign.

Solo se aplican en el contexto del contenido de envío. Es la única forma de crear una secuencia de comandos de la dirección URL de un correo electrónico y seguir su seguimiento (además de los parámetros de URL). Se pueden ver como una copia/pegado automático aplicado durante la análisis de envío antes de detectar los vínculos que se van a rastrear.

Existen tres tipos de instrucciones:

* &quot;**incluir**&quot;: principalmente para factorizar algunas opciones de código, bloques de personalización, archivos externos o páginas
* &quot;**valor**&quot;: para dar acceso a los campos del envío, las variables de envío y los objetos personalizados cargados en el envío
* &quot;**foreach**&quot;: para crear un bucle de una matriz cargada como un objeto personalizado.

Pueden probarse directamente desde el asistente de envíos. Se aplican en la previsualización de contenido y cuando hace clic en el botón de seguimiento para ver la lista de las direcciones URL.

## &lt;>{#<%@-include}

Los siguientes ejemplos se encuentran entre los más utilizados:

* Incluido el vínculo de página espejo: `<%@ include view="MirrorPage" %>`
* URL de página espejo: &quot;Vista como `<a href="<%@ include view='MirrorPageUrl' %>" _label="Mirror Page" _type="mirrorPage">web page"`
* Dirección URL baja lista para usar: `<%@ include option='NmsServer_URL' %>/webApp/unsub?id=<%= escapeUrl(recipient.cryptedId)%>`
* Otros ejemplos:
   * `<%@ include file='http://www.google.com' %>`
   * `<%@ include file='file:///X:/france/service/test.html' %>`
   * `<%@ include option='NmsServer_URL' %>`

Utilice el botón de personalización del asistente de envíos para obtener la sintaxis correcta.

## &lt;%@ value {#<%@-value}

Esta instrucción proporciona acceso a parámetros del envío que son constantes para todos los destinatarios.

Syntax:

`<%@ value object="myObject" xpath="@myField" index="1" %>`

Donde:

* &quot;object&quot;: nombre del objeto (ejemplo: envío, proveedor, etc.).
* &quot;xpath&quot;: xpath del campo.
* &quot;index&quot; (opcional): si &quot;object&quot; es una matriz (para objetos de secuencia de comandos adicionales), índice de elementos en la matriz (Inicios en 0).

El objeto puede ser:

* *&quot;envío&quot;: para el envío actual (vea los detalles y las restricciones en la subsección siguiente).
* &quot;proveedor&quot;: para el proveedor/enrutamiento de envío actual (nms:externalAccount).
* Un objeto de secuencia de comandos adicional: si un objeto se carga en el contexto mediante: **Propiedades** > **Personalización** > **Añadir objetos en el contexto de ejecución**.
* Elemento del bucle foreach: consulte la sección [Foreach](#<%@-foreach) a continuación.

### Objeto &quot;envío&quot; {#delivery-object}

Para la personalización del correo electrónico, el objeto envío es accesible de dos formas:

* En JavaScript. Por ejemplo: `<%= delivery.myField %>`.

   En el envío de objetos JavaScript no se admiten campos personalizados. Funcionan en la previsualización, pero no en el MTA porque el MTA sólo puede acceder al esquema de envío incorporado.

* Mediante `<%@ value object="delivery"` preprocesamiento.

Para la instrucción `<%@ value object="delivery" xpath="@myCustomField" %>`, existe otra limitación para los envíos enviados por intermediaria. El campo personalizado @myCustomField debe agregarse al esquema nms:envío en las plataformas de marketing y intermediaria.

>[!NOTE]
>
>Para parámetros/variables de envío, utilice la sintaxis siguiente (con el objeto envío):
>
>`<%@ value object="delivery" xpath="variables/var[@name='myVar']/@stringValue" %>`

### &lt;>{#<%@-value-in-javascript}

Para permitir el uso del valor &lt;%@ en secciones de secuencias de comandos, se reemplazan dos objetos especiales con &lt;% y %>:

* `<%@ value object='startScript' %>`
* `<%@ value object='endScript' %>`

Por ejemplo:

```
<%@ value object='startScript' %> var iMode = <%@ value object="delivery" xpath="@deliveryMode" %> if(iMode == 1) { ... } else { ... }`
`<%@ value object='endScript' %> is expanded in something like <% var iMode = 1 if(iMode == 1) { ... } else { ... } %>.
```

## &lt;>{#<%@-foreach}

Esta instrucción permite la iteración en una matriz de objetos cargados en el envío para rastrear vínculos individuales relacionados con los objetos.

Sintaxis:

`<%@ foreach object="myObject" xpath="myLink" index="3" item="myItem" %> <%@ end %>`

Donde:

* &quot;object&quot;: nombre del objeto desde el que se va a realizar el inicio, normalmente un objeto de secuencia de comandos adicional, pero puede ser un envío.
* &quot;xpath&quot; (opcional): xpath de la colección en la que se va a realizar un bucle. El valor predeterminado es &quot;.&quot;, lo que significa que el objeto es la matriz en la que se debe realizar el bucle.
* &quot;index&quot; (opcional): si xpath no es &quot;.&quot; y el objeto es una matriz en sí, índice de elementos del objeto (inicios en 0).
* &quot;item&quot; (opcional): nombre de un nuevo objeto accesible con un valor &lt;%@ dentro del bucle foreach. Predeterminado con el nombre del vínculo en el esquema.

Ejemplo:

En las propiedades/personalización de envío, cargue una matriz de artículos y una tabla de relación entre destinatario y artículos.

La visualización de vínculos a estos artículos se puede realizar simplemente con un JavaScript de la siguiente manera:

```
<%
  for(var i=0; i<recipient.rcpArticle.length; i++ )
  {
    %><a href="http://nl.net?a.jsp?article=<%=recipient.rcpArticle[i].article.@id%>">article</a><%
  }
%>
```

Con esta solución, los vínculos a todos los artículos se rastrean sin distinción. Puede saber que un destinatario ha hecho clic en un vínculo del artículo, pero no puede saber en qué artículo.

La solución es:

1. Precargue todos los artículos posibles en una matriz de scripts adicional del envío (articleList[]), lo que significa que debe haber un número finito de artículos posibles.
1. Escriba una función de JavaScript al principio del contenido.

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

