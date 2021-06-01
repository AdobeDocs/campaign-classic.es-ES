---
product: campaign
title: Exclusión del seguimiento de aplicaciones web
description: Exclusión del seguimiento de aplicaciones web
audience: web
content-type: reference
topic-tags: web-applications
exl-id: 4bff6b55-3335-433e-a2ff-5d8c83e8f0d3
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: tm+mt
source-wordcount: '670'
ht-degree: 100%

---

# Exclusión del seguimiento de aplicaciones web{#web-application-tracking-opt-out}

Adobe Campaign permite detener el seguimiento en la web de los comportamientos de los usuarios finales que optan por no participar en él mediante cookies o señalización web. Esta funcionalidad incluye la posibilidad de mostrar un banner para ofrecerle esta opción al usuario; se pueden añadir estos banners a las aplicaciones web o a las páginas de destino.

Si un usuario final opta por no participar en el seguimiento de conductas mediante cookies o señalización web, la información se transmite al servidor de seguimiento de Adobe Campaign con las API de JavaScript. Tenga en cuenta que algunas jurisdicciones pueden requerir que el cliente ofrezca a los usuarios finales una adhesión antes de poder ofrecerles una exclusión (o que existan otros requisitos legales) y es responsabilidad del cliente cumplir con las leyes aplicables.

>[!NOTE]
>
>Cuando las secuencias de script siempre siguen las directrices descritas en la [Lista de comprobación de seguridad y privacidad](https://helpx.adobe.com/es/campaign/kb/acc-security.html#dev).

## Configuración del banner {#configuring-the-banner-}

Para que se muestre dentro de las aplicaciones web o de las páginas de destino, es necesario configurar el banner.

Adobe Campaign incluye un banner de muestra que debe adaptar a sus necesidades. Esta versión del banner aparece como un bloque personalizado ubicado en la carpeta del modelo de contenido. Consulte [esta página](../../delivery/using/personalization-blocks.md).

>[!IMPORTANT]
>
>Para crear su propio banner, debe personalizar el banner predeterminado.

Para activar el banner, debe configurar las propiedades de la aplicación web. Consulte la sección [Diseño de una aplicación web](../../web/using/designing-a-web-application.md).

Si el seguimiento web está activado, puede darse lo siguiente:

* No tener banner.
* Configure el banner manualmente en cada página: marque esta opción y seleccione el banner en cada página de las propiedades de página.

   ![](assets/pageproperties.png)

* Agregue automáticamente el banner a todas las páginas: seleccione el banner directamente en las propiedades de la aplicación web.

   ![](assets/optoutconfig.png)

>[!NOTE]
>
>Hay disponible un modo de compatibilidad para la aplicación web v5 con el mismo comportamiento.

El banner predeterminado tiene la siguiente estructura:

```
<div onClick="NL.ClientWebTracking.closeOptOutBanner(this);" id="defaultOptOutBanner">
  <p>Please insert your message here
   <a onClick="NL.ClientWebTracking.allow();" class="optout-accept">Accept</a>
   <a onClick="NL.ClientWebTracking.forbid();" class="optout-decline">Refuse</a>
  </p>
</div>
      
```

Debe reemplazar el mensaje **Introduzca el mensaje aquí** con el bloque que contiene la información de seguimiento. Este reemplazo debe ejecutarse en el nuevo bloque personalizado relacionado con el banner de exclusión.

El banner incluye un CSS específico. Sin embargo, puede sobrescribir los estilos al crear y configurar una página web. Consulte [esta página](../../web/using/content-editor-interface.md).

## Configuración de la cookie de exclusión mediante API {#setting-the-opt-out-cookie-using-api}

Adobe Campaign incluye las API que le permiten administrar el valor de la cookie y recuperar las preferencias de usuario.

El nombre de la cookie es **acoptout**. Los valores comunes son:

* 0: el usuario ha permitido el seguimiento web (valor predeterminado).
* 1: el usuario ha prohibido el seguimiento web.
* null: el usuario no ha elegido, pero se permite el seguimiento web porque es el valor predeterminado.

Las API de cliente disponibles para personalizar el banner son:

* **NL.ClientWebTracking.allow()**: Define el valor de la cookie de exclusión para permitir el seguimiento web. El seguimiento web se permite de forma predeterminada.
* **NL.ClientWebTracking.forbid()**: Establece el valor de la cookie de exclusión para prohibir el seguimiento web. El seguimiento web necesita la entrada de un usuario para prohibirlo.
* **NL.ClientWebTracking.closeOptOutBanner(bannerDomElt)**: Cierra el banner de la cookie de exclusión cuando el usuario ha hecho clic en el botón Aceptar o Rechazar. (durante la fase de propagación del evento de clic).

   bannerDomElt {DOMElement}: el elemento DOM raíz del banner de la cookie que debe eliminarse.

* **NL.ClientWebTracking.hasUserPrefs()**: Devuelve el valor verdadero si el usuario ha elegido sus preferencias de seguimiento web.
* **NL.ClientWebTracking.getUserPrefs()**: Devuelve el valor de cookie de exclusión que define las preferencias del usuario.

Si tiene que escribir una JSSP, las API de servidor están disponibles:

* **NL.ServerWebTracking.generateOptOutBanner(escapeJs)**: Genera el marcado para el banner de exclusión que se inserta en la página de JSSP.

   **escapeJs {Boolean}**: verdadero cuando se debe escapar el marcado generado para utilizarlo en JavaScript.

   Devuelve el HTML del marcado del banner de exclusión que debe publicarse en la página.

* **NL.ServerWebTracking._displayOptOutBanner()**

   Devuelve el valor verdadero si se debe mostrar el banner de exclusión después de que el administrador lo seleccione.

   Se llama a este código cuando el administrador ya ha elegido utilizar el banner de exclusión del seguimiento web.

   El banner debe mostrarse si el usuario aún no ha elegido si participar en el seguimiento o no.

* **NL.ServerWebTracking.renderOptOutBanner(escapeJs)**

   Renderiza el marcado del banner de exclusión al insertarlo en la página JSSP. Se denomina igual que en Jssp entre &lt;% %>

   **escapeJs {Boolean}**: verdadero cuando se debe escapar el marcado generado para utilizarlo en JavaScript.

Ejemplo de JSSP:

```
<%@ page import="/nl/core/shared/nl.js" %>
<!doctype html>
<%
NL.require('/nl/core/shared/webTracking.js');
NL.client.require('/nl/core/shared/webTracking.js');
%>
<html>
<head>
<%==NL.client.deps()%>
</head>

<body>

<!-- TEST USING SERVER API IN JSSP -->
<% 
var webTracking = new NL.ServerWebTracking(request, 'optOutBanner');
webTracking.renderOptOutBanner();
%>

<!-- TEST USING SERVER API IN A SCRIPT -->
<!--
<% 
var webTracking = new NL.ServerWebTracking(request, 'optOutBanner');
%>
<script>var el = document.createElement('div'); el.innerHTML =  "<% webTracking.renderOptOutBanner(true); %>";document.body.appendChild(el);</script>
-->

<!-- TEST OF THE CLIENT API -->
<!--
<div onClick="NL.ClientWebTracking.closeOptOutBanner(this);" id="defaultOptOutBanner">
  <p>Please insert your message here
   <a onClick="NL.ClientWebTracking.allow();" class="optout-accept">Accept</a>
   <a onClick="NL.ClientWebTracking.forbid();" class="optout-decline">Refuse</a>
  </p>
</div>
-->
</body>
</html>
```
