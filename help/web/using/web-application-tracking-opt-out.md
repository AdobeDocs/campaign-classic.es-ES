---
product: campaign
title: Exclusión del seguimiento de aplicaciones web
description: Exclusión del seguimiento de aplicaciones web
badge-v8: label="También se aplica a v8" type="Positive" tooltip="También se aplica a Campaign v8"
feature: Web Apps
exl-id: 4bff6b55-3335-433e-a2ff-5d8c83e8f0d3
TQID: https://experienceleague.adobe.com/-5Bp8qdxH8DTEJ0-NASuorQrjwDMUmvuhBNbW1alqyc
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
feature_v2:
  - id: a7760dfc-5c44-4d77-bb68-c50b1e265c93
  - id: b12f6872-9271-4369-85e5-86969a0b99a2
subfeature_v2:
  - id: ac9c0a9c-8a76-4419-bd64-9c34c5782666
  - id: fb2a841f-c522-491f-9901-a1b939d252df
topic_v2:
  - id: d095671a-1355-40aa-8b5f-06c33c68080b
  - id: e0eb8757-182f-49f3-94a4-1587d16f5094
  - id: f4e6943a-c91a-4134-a2c7-f4f20cfff2f0
source-git-commit: 4c295c0dabae8aba298390a3da2422a3fa1219f9
workflow-type: tm+mt
source-wordcount: 719
ht-degree: 99%

---

# Exclusión del seguimiento de aplicaciones web{#web-application-tracking-opt-out}



Adobe Campaign permite detener el seguimiento en la web de los comportamientos de los usuarios finales que optan por no participar en él mediante cookies o señalización web. Esta funcionalidad incluye la posibilidad de mostrar un banner para ofrecerle esta opción al usuario; se pueden añadir estos banners a las aplicaciones web o a las páginas de destino.

Si un usuario final opta por no participar en el seguimiento de conductas mediante cookies o señalización web, la información se transmite al servidor de seguimiento de Adobe Campaign con las API de JavaScript. Tenga en cuenta que algunas jurisdicciones pueden requerir que el cliente ofrezca a los usuarios finales una adhesión antes de poder ofrecerles una exclusión (o que existan otros requisitos legales) y es responsabilidad del cliente cumplir con las leyes aplicables.

>[!NOTE]
>
>Cuando las secuencias de script siempre siguen las directrices descritas en la [Lista de comprobación de seguridad y privacidad](https://helpx.adobe.com/es/campaign/kb/acc-security.html#dev).

## Configuración del banner {#configuring-the-banner-}

Para que se muestre dentro de las aplicaciones web o de las páginas de destino, es necesario configurar el banner.

Adobe Campaign incluye un banner de muestra que debe adaptar a sus necesidades. Esta versión del banner aparece como un bloque personalizado ubicado en la carpeta del modelo de contenido. Consulte la [documentación de Campaign v8](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/personalize/personalization-blocks.html?lang=es){target="_blank"}.

>[!IMPORTANT]
>
>Para crear su propio banner, debe personalizar el banner predeterminado.

Para activar el banner, debe configurar las propiedades de la aplicación web. Consulte la sección [Diseño de una aplicación web](designing-a-web-application.md).

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

El banner incluye un CSS específico. Sin embargo, puede sobrescribir los estilos al crear y configurar una página web. Consulte [esta página](content-editor-interface.md).

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

  bannerDomElt {DOMElement} el elemento DOM raíz del banner de la cookie que debe eliminarse.

* **NL.ClientWebTracking.hasUserPrefs()**: devuelve el valor verdadero si el usuario ha elegido sus preferencias de seguimiento web.
* **NL.ClientWebTracking.getUserPrefs()**: Devuelve el valor de cookie de exclusión que define las preferencias del usuario.

Si tiene que escribir una JSSP, las API de servidor están disponibles:

* **NL.ServerWebTracking.generateOptOutBanner(escapeJs)**: Genera el marcado para el banner de exclusión que se inserta en la página de JSSP.

  **escapeJs{Boolean}**: verdadero cuando el marcado generado debe ser de escape para utilizarse en JavaScript.

  Devuelve el HTML del marcado del banner de exclusión que debe publicarse en la página.

* **NL.ServerWebTracking._displayOptOutBanner()**

  Devuelve el valor verdadero si se debe mostrar el banner de exclusión después de que el administrador lo seleccione.

  Se llama a este código cuando el administrador ya ha elegido utilizar el banner de exclusión del seguimiento web.

  El banner debe mostrarse si el usuario aún no ha elegido si participar en el seguimiento o no.

* **NL.ServerWebTracking.renderOptOutBanner(escapeJs)**

  Renderiza el marcado del banner de exclusión al insertarlo en la página JSSP. Se denomina igual que en Jssp entre &lt;% %>

  **escapeJs{Boolean}**: verdadero cuando el marcado generado debe ser de escape para utilizarse en JavaScript.

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
