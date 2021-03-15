---
solution: Campaign Classic
product: campaign
title: Instrucciones de preprocesamiento para direcciones URL rastreadas
description: Obtenga más información sobre las instrucciones de preprocesamiento que se utilizarán para crear secuencias de comandos de la dirección URL de un correo electrónico que se seguirá rastreando.
audience: delivery
content-type: reference
topic-tags: tracking-messages
translation-type: tm+mt
source-git-commit: 7a58da8fd20abbff9dcf8361536310de49a7905f
workflow-type: tm+mt
source-wordcount: '642'
ht-degree: 81%

---


# Instrucciones de preprocesamiento {#pre-processing-instructions}

Puede utilizar una sintaxis específica en el contenido de la entrega para añadir instrucciones y crear una secuencia de comandos para la URL del correo electrónico rastreado. Las instrucciones &lt;%@ no son JavaScript: esta sintaxis es específica de Adobe Campaign.

Solo se aplican en el contexto del contenido de envío. Es la única forma de crear una secuencia de comandos de la dirección URL de un correo electrónico y seguir rastreándola (además de los parámetros de la URL). Se pueden ver como un copipega automático aplicado durante el análisis de envío antes de detectar los vínculos que se van a rastrear.

Existen tres tipos de instrucciones:

* **[!DNL include]**: principalmente para factorizar algún código en opciones, bloques de personalización, archivos externos o páginas. [Obtenga más información](#include)
* &quot;**[!DNL value]**&quot;: para proporcionar acceso a los campos de la entrega, las variables de entrega y los objetos personalizados cargados en la entrega. [Obtenga más información](#value)
* &quot;**[!DNL foreach]**&quot;: para crear un bucle de una matriz cargada como un objeto personalizado. [Obtenga más información](#foreach)

Pueden probarse directamente desde el asistente de envíos. Se aplican en la previsualización de contenido y cuando hace clic en el botón de seguimiento para ver la lista de las direcciones URL.

## [!DNL include] {#include}

Los siguientes ejemplos se encuentran entre los más utilizados:

* Incluir el vínculo de la página espejo:

   ```
   <%@ include view="MirrorPage" %>  
   ```

* URL de página espejo:

   ```
   View as a <a href="<%@ include view='MirrorPageUrl' %>" _label="Mirror Page" _type="mirrorPage">web page.
   ```

* Dirección URL de baja:

   ```
   <%@ include option='NmsServer_URL' %>/webApp/unsub?id=<%= escapeUrl(recipient.cryptedId)%>
   ```

* Otros ejemplos:

   ```
   <%@ include file='http://www.google.com' %>
   <%@ include file='file:///X:/france/service/test.html' %>
   <%@ include option='NmsServer_URL' %>
   ```

   Utilice el botón de personalización del asistente de envíos para obtener la sintaxis correcta.

## [!DNL value] {#value}

Esta instrucción proporciona acceso a parámetros del envío que son constantes para todos los destinatarios.

Sintaxis:

```
<%@ value object="myObject" xpath="@myField" index="1" %>
```

Donde:

* **[!DNL object]**: nombre del objeto (ejemplo: envío, proveedor, etc.).
El objeto puede ser:
   * &quot;delivery&quot;: para el envío actual (vea los detalles y las restricciones en la subsección siguiente).
   * &quot;provider&quot;: para el proveedor/enrutamiento de envío actual (nms:externalAccount).
   * Un objeto de secuencia de comandos adicional: si un objeto se carga en el contexto mediante: **Propiedades** > **Personalización** > **Añadir objetos en el contexto de ejecución**.
   * Elemento del bucle foreach: consulte la sección [Foreach](#foreach) a continuación.
* **[!DNL xpath]**: xpath del campo.
* **[!DNL index]** (opcional): si  **[!DNL object]** es una matriz (para objetos de secuencia de comandos adicionales), índice de elementos en la matriz (Comienza en 0).

### [!DNL delivery] object {#delivery-object}

Para la personalización del correo electrónico, el objeto de envío es accesible de dos formas:

* Uso de JavaScript:

   ```
   <%= delivery.myField %>`.
   ```

   En el envío de objetos JavaScript no se admiten campos personalizados. Funcionan en la previsualización, pero no en el servidor de correo, porque este solo puede acceder al esquema de envío listo para usar.

* Uso de un procesamiento previo:

   ```
   <%@ value object="delivery"
   ```


>[!NOTE]
>
>* Para la instrucción `<%@ value object="delivery" xpath="@myCustomField" %>`, existe otra limitación para los envíos enviados por intermediarios. El campo personalizado @myCustomField debe añadirse al esquema nms:delivery en las plataformas de marketing y del intermediario.
   >
   >
* Para parámetros/variables de envío, utilice la sintaxis siguiente (con el objeto de envío):
>
>
`<%@ value object="delivery" xpath="variables/var[@name='myVar']/@stringValue" %>`

### [!DNL value] en una sección de Javascript  {#value-in-javascript}

Para permitir el uso del valor &lt;%@ en las secciones de Javascript, se reemplazan dos objetos especiales por &lt;% y %>:

* `<%@ value object='startScript' %>`
* `<%@ value object='endScript' %>`

Por ejemplo:

```
<%@ value object='startScript' %> var iMode = <%@ value object="delivery" xpath="@deliveryMode" %> if(iMode == 1) { ... } else { ... }`
`<%@ value object='endScript' %> is expanded in something like <% var iMode = 1 if(iMode == 1) { ... } else { ... } %>.
```

## [!DNL foreach] {#foreach}

Esta instrucción permite la iteración en una matriz de objetos cargados en el envío para rastrear vínculos individuales relacionados con los objetos.

Síntaxis:

```
<%@ foreach object="myObject" xpath="myLink" index="3" item="myItem" %> <%@ end %>
```

Donde:

* **[!DNL object]**: nombre del objeto desde el que se va a realizar el inicio, normalmente un objeto de secuencia de comandos adicional, pero puede ser un envío.
* **[!DNL xpath]** (opcional): xpath de la colección en la que se va a realizar un bucle. El valor predeterminado es &quot;.&quot;, lo que significa que el objeto es la matriz en la que se debe realizar el bucle.
* **[!DNL index]** (opcional): si xpath no es &quot;.&quot; y el objeto es una matriz en sí, índice de elementos del objeto (inicia en 0).
* **[!DNL item]** (opcional): nombre de un nuevo objeto accesible con un valor &lt;%@ dentro del bucle foreach. Predeterminado con el nombre del vínculo en el esquema.

Ejemplo:

En las propiedades/personalización de envío, cargue una matriz de artículos y una tabla de relación entre destinatario y artículos.

La visualización de vínculos a estos artículos se puede realizar simplemente con JavaScript de la siguiente manera:

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
1. Muestre el artículo llamando a la función.

   ```
   <%
   for(var i=0; i<recipient.rcpArticle.length; i++ )
   {
    displayArticle(recipient.rcpArticle[i].article.@id)
   }
   %>
   ```

