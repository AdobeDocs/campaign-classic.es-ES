---
product: campaign
title: Integración mediante SOAP (lado del servidor)
description: Integración mediante SOAP (lado del servidor)
audience: interaction
content-type: reference
topic-tags: unitary-interactions
exl-id: 3eaef689-44fa-41b3-ade8-9fe447e165ec
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: tm+mt
source-wordcount: '318'
ht-degree: 100%

---

# Integración mediante SOAP (del lado del servidor){#integration-via-soap-server-side}

Los servicios web SOAP proporcionados para la administración de ofertas son diferentes de los utilizados en Adobe Campaign. Se puede acceder a ellos a través de la dirección URL de interacción descrita en la sección anterior y permiten presentar o actualizar ofertas para un contacto determinado.

## Propuesta de oferta {#offer-proposition}

Para una propuesta de oferta mediante SOAP, añada el comando **nms:proposition#Propose** seguido de los parámetros siguientes:

* **targetId**: clave principal del destinatario (puede ser una clave compuesta).
* **maxCount**: especifica el número de propuestas de ofertas para el contacto.
* **context**: permite añadir información contextual en el esquema de espacio. Si el esquema utilizado es **nms:interaction**, se debe añadir **`<empty>`**.
* **categories**: especifica las categorías a las que las ofertas deben pertenecer.
* **themes**: especifica los tema a los que las ofertas deben pertenecer.
* **uuid**: valor de la cookie permanente de Adobe Campaign (“uuid230”).
* **nli**: valor de la cookie de sesión de Adobe Campaign (“nlid”).
* **noProp**: utilice el valor “true” para desactivar la inserción de propuestas.

>[!NOTE]
>
>Los ajustes **targetId** y **maxCount** son obligatorios. Los demás son opcionales.

Como respuesta a la consulta, el servicio SOAP devuelve los siguientes parámetros:

* **interactionld**: ID de la interacción.
* **propositions**: el elemento XML, contiene la lista de propuestas, cada una con su propio ID y representación HTML.

## Actualización de oferta {#offer-update}

Añada el comando **nms:interaction#UpdateStatus** a la dirección URL, seguido de estos parámetros:

* **proposition**: cadena de caracteres, contiene el ID de la propuesta dado como salida durante una propuesta de oferta. Consulte la [Propuesta de oferta](#offer-proposition).
* **status**: tipo cadena, especifica el nuevo estado de la oferta. Los valores posibles se mencionan en la enumeración **propositionStatus**, en el esquema **nms:common.** Por ejemplo, de forma predeterminada, el número 3 corresponde al estado **Accepted**.
* **context**: el elemento XML, permite añadir información contextual en el esquema de espacio. Si el esquema utilizado es **nms:interaction**, se debe añadir **`<empty>`**.

## Ejemplo de uso de una llamada a SOAP {#example-using-a-soap-call}

A continuación, se muestra un ejemplo de código para una llamada SOAP:

```
<%
  var space = request.parameters.sp
  var cnx = new HttpSoapConnection(
    "https://" + request.serverName + ":" + request.serverPort + "/interaction/" + env + "/" + space,
    "utf-8",
    HttpSoapConnection.SOAP_12)
  var session = new SoapService(cnx, "nms:interaction")
  var action = request.parameters.a
  if( action == undefined )
    action = 'propose'

  try
  {
    switch( action )
    {
    case "update":
      var proposition = request.parameters.p
      var status      = request.parameters.st
      session.addMethod("UpdateStatus", "nms:interaction#UpdateStatus",
       ["proposition", "string",
        "status",      "string",
        "context",     "NLElement"],
       [])
      session.UpdateStatus(proposition, status, <undef/>)
      var redirect = request.parameters.r
      if( redirect != undefined )
        response.sendRedirect(redirect)
      break;

    case "propose":
      var count = request.parameters.n
      var target = request.parameters.t
      var categorie = request.parameters.c
      var theme = request.parameters.th
      var layout = request.parameters.l
      if( count == undefined )
        count = 1
      session.addMethod("Propose", "nms:proposition#Propose",
       ["targetId",      "string",
        "maxCount",      "string",
         "categories",    "string",
         "themes",        "string",
        "context",       "NLElement"],
       ["interactionId", "string",
        "propositions",  "NLElement"])
      response.setContentType("text/html")
      var result = session.Propose(target, count, category, theme, <empty/>)
      var props = result[1]
  %><table><tr><%
      for each( var propHtml in props.proposition.*.mdSource )
      {
        %><td><%=propHtml%></td><%
      }
  %></tr></table><%
      break;
    }
  }
  catch( e )
  {
  }
  %>
```
