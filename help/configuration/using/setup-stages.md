---
product: campaign
title: Etapas de configuración
description: Etapas de configuración
feature: Configuration
role: Developer
exl-id: a5ae0b61-3377-46d9-a327-6c897eeda770
source-git-commit: 9f5205ced6b8d81639d4d0cb6a76905a753cddac
workflow-type: tm+mt
source-wordcount: '233'
ht-degree: 6%

---

# Etapas de configuración{#setup-stages}

El principio básico es la inserción de etiquetas de seguimiento web en determinadas páginas del sitio web.

Existen dos tipos de etiquetas:

* **WEB**: esta etiqueta indica si se ha visitado la página,
* **TRANSACTION**: funciona como una etiqueta web, pero con la posibilidad de agregar información sobre el volumen comercial generado, por ejemplo (importe de la transacción, número de elementos comprados, etc.).

Siga los siguientes pasos para configurar estas etiquetas:

1. Identifique las páginas que desee rastrear y determine su tipo (WEB o TRANSACCIÓN).
1. Determine qué información adicional desea recopilar y amplíe el esquema **nms:webTrackingLog** con la descripción de esta información. De forma predeterminada, este esquema puede almacenar las cantidades de transacción y el número de artículos por transacción.
1. Creación de etiquetas de seguimiento web. Hay dos formas de hacerlo:

   * Inserte las direcciones URL correspondientes a estas páginas en la plataforma de Adobe Campaign y, a continuación, genere y extraiga las etiquetas de seguimiento web asociadas (desde el nodo **[!UICONTROL Campaign execution>Resources>Web tracking tags]** de la consola del cliente).
   * Cree usted mismo las etiquetas de seguimiento web en el modo &quot;on-the-fly creation&quot;: las direcciones URL correspondientes a estas páginas se insertan automáticamente en la plataforma de Adobe Campaign.

1. Agregue estas etiquetas estática o dinámicamente en las páginas que desee rastrear.

   >[!NOTE]
   >
   >Todas las etiquetas de tipo WEB se pueden agregar tal cual a las páginas del sitio. Las etiquetas de TRANSACCIÓN deben modificarse o añadirse dinámicamente para contener la información adicional (cantidad, elementos, etc.).

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
