---
solution: Campaign Classic
product: campaign
title: Etapas de configuración
description: Etapas de configuración
audience: configuration
content-type: reference
topic-tags: setting-up-web-tracking
translation-type: tm+mt
source-git-commit: c625b4109e2cb47446331cd009ff9827c8267c93
workflow-type: tm+mt
source-wordcount: '234'
ht-degree: 5%

---


# Etapas de configuración{#setup-stages}

El principio básico es la inserción de etiquetas de seguimiento web en determinadas páginas del sitio web.

Existen dos tipos de etiquetas:

* **WEB**: esta etiqueta le indica si se ha visitado la página,
* **TRANSACCIÓN**: funciona como una etiqueta web, pero con la posibilidad de agregar información sobre el volumen de negocios generado, por ejemplo (importe de transacción, número de artículos comprados, etc.).

Siga los pasos siguientes para configurar estas etiquetas:

1. Identifique las páginas que desee rastrear y determine su tipo (WEB o TRANSACCIÓN).
1. Determine qué información adicional desea recopilar y extienda el esquema **nms:webTrackingLog** con la descripción de esta información. De forma predeterminada, este esquema puede almacenar los importes de transacción y el número de artículos por transacción.
1. Creación de etiquetas de seguimiento web. Hay dos formas de hacerlo:

   * Inserte las direcciones URL correspondientes a estas páginas en la plataforma de Adobe Campaign y, a continuación, genere y extraiga las etiquetas de seguimiento Web asociadas (desde el nodo **[!UICONTROL Campaign execution>Resources>Web tracking tags]** de la consola de cliente).
   * Cree las etiquetas de seguimiento web usted mismo en el modo de &quot;creación sobre la marcha&quot;: las direcciones URL correspondientes a estas páginas se insertarán automáticamente en la plataforma de Adobe Campaign.

1. Añada estas etiquetas de forma estática o dinámica en las páginas que desee rastrear.

   >[!NOTE]
   >
   >Todas las etiquetas de tipo WEB se pueden agregar tal como están a las páginas del sitio. Las etiquetas TRANSACTION deben modificarse o agregarse dinámicamente para que contengan la información adicional (cantidad, elementos, etc.).

**Ejemplo**:

```
<script type="text/javascript">
var _f = "nmsWebTracking"
var _t = window.location.href.match(/.*://[^/]*(/[^?#&]*)/)[1] + "|w|" + _f
document.write("<img height='0' width='0' alt='' src='" +
window.location.protocol + "//tsupport/r/" +
Math.random().toString() + "?tagid=" + escape(_t) + "'/>")
</script>
```

