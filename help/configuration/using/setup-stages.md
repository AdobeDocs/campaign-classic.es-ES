---
product: campaign
title: Etapas de configuración
description: Etapas de configuración
audience: configuration
content-type: reference
topic-tags: setting-up-web-tracking
exl-id: a5ae0b61-3377-46d9-a327-6c897eeda770
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: tm+mt
source-wordcount: '234'
ht-degree: 5%

---

# Etapas de configuración{#setup-stages}

El principio básico es la inserción de etiquetas de seguimiento web en determinadas páginas del sitio web.

Existen dos tipos de etiquetas:

* **WEB**: esta etiqueta le indica si se ha visitado la página,
* **TRANSACCIÓN**: funciona como una etiqueta web, pero con la posibilidad de agregar información sobre el volumen de negocio generado, por ejemplo (importe de transacción, número de artículos comprados, etc.).

Siga los siguientes pasos para configurar estas etiquetas:

1. Identifique las páginas que desee rastrear y determine su tipo (WEB o TRANSACCIÓN).
1. Determine qué información adicional desea recopilar y amplíe el esquema **nms:webTrackingLog** con la descripción de esta información. De forma predeterminada, este esquema puede almacenar las cantidades de transacción y el número de elementos por transacción.
1. Creación de las etiquetas de seguimiento web. Hay dos formas de hacerlo:

   * Inserte las direcciones URL correspondientes a estas páginas en la plataforma de Adobe Campaign y, a continuación, genere y extraiga las etiquetas de seguimiento web asociadas (desde el nodo **[!UICONTROL Campaign execution>Resources>Web tracking tags]** de la consola del cliente).
   * Cree las etiquetas de seguimiento web usted mismo en el modo &quot;Creación sobre la marcha&quot;: las direcciones URL correspondientes a estas páginas se insertarán automáticamente en la plataforma de Adobe Campaign.

1. Agregue estas etiquetas de forma estática o dinámica en las páginas que desee rastrear.

   >[!NOTE]
   >
   >Todas las etiquetas de tipo WEB se pueden agregar tal cual a las páginas de su sitio. Las etiquetas TRANSACTION deben modificarse o añadirse de forma dinámica para que contengan la información adicional (cantidad, elementos, etc.).

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
