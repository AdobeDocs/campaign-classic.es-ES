---
product: campaign
title: Insertar etiquetas de seguimiento web en el sitio
description: Obtenga información sobre cómo insertar etiquetas de seguimiento web en el sitio
feature: Configuration
role: Data Engineer, Developer
exl-id: e7fcec75-82fe-45ff-8d45-7d6e95baeb14
source-git-commit: b666535f7f82d1b8c2da4fbce1bc25cf8d39d187
workflow-type: tm+mt
source-wordcount: '329'
ht-degree: 0%

---

# Insertar etiquetas de seguimiento web en el sitio{#inserting-tags-in-your-site}

## Método simple {#simple-method}

Este método consiste en enviar una llamada HTTP al servidor de redirección insertando una etiqueta de HTML **`<img>`** en el código fuente del HTML de la página web que desea rastrear.

>[!IMPORTANT]
>
>Este método utiliza las cookies enviadas por el explorador web para identificar al destinatario y no es 100% fiable.

**Ejemplo**:

```
<img height='0' width='0' alt='' src='https://localhost/r/12343?tagid=home'
```

La etiqueta insertada contacta con el servidor de redirección.

![](assets/d_ncs_integration_webtracking_structure2.png)

Al definir una página para rastrearla en la consola, puede generar una etiqueta de seguimiento web de ejemplo para copiarla y pegarla en el código fuente de la página web.

Sin embargo, cuando se utilizan etiquetas de tipo TRANSACTION, se debe modificar la etiqueta de ejemplo mediante JavaScript para insertar la información de transacción (cantidad, número de elementos) y la información definida por un esquema de extensión.

### Inserción estática de etiquetas {#static-insertion-of-tags}

Para realizar la inserción de etiquetas estáticas, simplemente copie y pegue las etiquetas generadas por la consola o construidas manualmente en el origen de la página web.

**Ejemplo**: inserción de una etiqueta de seguimiento web en una página que muestra un formulario.

```
<html>
  <...>
  <body>
  <script>
      document.write("<img height='0' width='0' alt='' src='https://localhost/r/" + Math.random().toString() + "?tagid=home'>");
    </script>
    <noscript>
     <img height='0' width='0' alt='' src='https://localhost/r/?tagid=home'>
    </noscript>
    <h1>My site</h1>
    <form action="http://localhost/amount.md">
      Quantity: <input type="text" name="quantity"/><br/><br/>
      Amount: <input type="text" name="amount"/><br/><br/>
      <input value="Save" type="submit">
    </form>
  </body>
</html>
```

Inserción de una etiqueta de seguimiento web de tipo TRANSACTION en la página de confirmación (&quot;amount.md&quot;).

```
<html>
  <body>
    <script>
      function getURLparam(name) 
      {
        var m = location.search.match new RegExp("[?&]" + name + "=([^&]+)"));
        return m ? unescape(m[1]) : "";
      }
 
       var params = "https://localhost/r/" + Math.random().toString() + "?tagid=amount&amount="
                      +getURLparam("amount")+"&article="+getURLparam("quantity");
       document.write("<img height='0' width='0' src='"+params+"'/>");
    </script>

    <h1>Approval confirmation</h1>
  </body>
</html>
```

### Generación dinámica de etiquetas de seguimiento web {#dynamic-generation-of-web-tracking-tags}

Cuando las páginas web se generan dinámicamente, puede agregar la etiqueta de seguimiento web en el momento de la generación de la página.

**Ejemplo**: seguimiento web agregado a JSP.

```
<%@page import="java.util.Random" %>
<html>
  <body>
    <img height='0' width='0' alt='' src='https://localhost/r/<%=new Random().nextInt()%>?tagid=home'>
    <h1>My site</h1>
    <form action="https://localhost/amount.md">
      Quantity: <input type="text" name="quantity"/><br/><br/>
      Amount: <input type="text" name="amount"/><br/><br/>
      <input value="Save" type="submit">
    </form>
  </body>
</html>
```

```
<%@page import="java.util.Random" %>
<html>
  <body>
    <%  
      String strParams = new Random().nextInt() + "?tagid=amount";
      strParams += "&amount="+request.getParameter("amount");
      strParams += "&article="+request.getParameter("quantity");
    %>
    <img height='0' width='0' alt=''
     src='http://localhost/r/<%=strParams%>'>
    <h1>Approval confirmation</h1>
    </body>
</html>
```

## Método óptimo {#optimum-method-}

Si desea controlar la información enviada al servidor de redirección, la forma más fiable es realizar la consulta HTTP sincrónicamente utilizando un idioma de generación de páginas.

La dirección URL que construya debe obedecer las reglas de sintaxis definidas en [etiqueta de seguimiento web: definition](../../configuration/using/web-tracking-tag-definition.md).

![](assets/d_ncs_integration_webtracking_structure3.png)

>[!NOTE]
>
>La redirección y el seguimiento web utilizan cookies y es importante que el servidor web que realiza la llamada HTTP sincrónica esté en el mismo dominio que el servidor de redirección. Los distintos intercambios HTTP deben transmitir las cookies &quot;id&quot;, &quot;uuid&quot; y &quot;uuid230&quot;.

**Ejemplo**: generación dinámica en Java, con autenticación de destinatarios usando su número de cuenta.

```
[...]
  // Recipient account, amount and articles
  String strAccount = request.getParameter("account");
  String strAmount = request.getParameter("amount");
  String strArticle = request.getParameter("article");

  StringBuffer strCookies = new StringBuffer();
  String strSetCookie = null;

  // Get cookies from client request
  Cookie[] cookies = request.getCookies();
  for(int i=0; i< cookies.length; i++ )
  {
    Cookie c = cookies[i];
    String strName = c.getName();
    if( strName.equals("id") || strName.equals("uuid") || strName.equals("uuid230") )
      // Helper function to add cookies in string
      AddCookie(strCookies, c);
  }
  // Now perform a synchronous HTTP request to inform redirection server
  // Add a tagid in auto-discover mode, and a default jobId to use (in hexa)
  StringBuffer strURL = new StringBuffer("https://www.adobe.com/r/a?tagid=cmd_page%7Ct&jobid=27EE");
  if( strAccount != null )
    AddParameter(strURL, "rcpid", "saccount="+strAccount);
  if( strAmount != null )
    AddParameter(strURL, "amount", strAmount);
  if( strArticle != null )
    AddParameter(strURL, "article", strArticle);
  
  URL url = new URL(strURL.toString());
  HttpURLConnection connection = (HttpURLConnection)url.openConnection();
  // Add the client cookies
  if( strCookies.length() > 0 )
    connection.setRequestProperty("Cookie", strCookies.toString());

  int errcode = connection.getResponseCode();

  // Now add the Adobe Campaign cookies if the server returned one :
  if( errcode == 200 )
  {
    strSetCookie = connection.getHeaderField("Set-Cookie");
    if( strSetCookie != null && strSetCookie.length() > 0 )
      response.addHeader("Set-Cookie", strSetCookie);
  }
  [...]
```
