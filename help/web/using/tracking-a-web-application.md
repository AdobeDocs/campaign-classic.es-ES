---
title: Seguimiento de una aplicación web
seo-title: Seguimiento de una aplicación web
description: Seguimiento de una aplicación web
seo-description: null
page-status-flag: never-activated
uuid: c087b40c-fd14-440f-8f38-33f5f68120a9
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: web
content-type: reference
topic-tags: web-applications
discoiquuid: 8e52f927-dadd-44c8-a51d-f717bc083eef
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 36beb1eca48c698634c7548e0f931ab3fe17c021

---


# Seguimiento de una aplicación web{#tracking-a-web-application}

Adobe Campaign permite rastrear y medir visitas en páginas de aplicaciones Web mediante la inserción de etiquetas de seguimiento. Esta funcionalidad se puede utilizar para todos los tipos de aplicaciones web (formularios, encuestas en línea, páginas web creadas con DCE, etc.).

De este modo, se pueden definir varias rutas de navegación y evaluar su eficacia. Los datos obtenidos están disponibles en los informes de cada aplicación.

Las principales mejoras incluidas en esta versión son las siguientes:

* Posibilidad de insertar varias etiquetas de seguimiento en una misma página para facilitar la definición de las rutas de navegación (por ejemplo: compras, suscripciones, devoluciones, etc.).
* Visualización de rutas de navegación y las etiquetas de seguimiento de las diferentes páginas en el panel de control de la aplicación web.

   ![](assets/trackers_1.png)

* Generación de un informe de seguimiento completo.

   ![](assets/trackers_5.png)

   Los indicadores principales son los siguientes:

   * **Tasa** de conversión: número de personas que mostraron todos los pasos de una ruta de navegación.
   * **Tasa** de salida hacia otro sitio: número de personas que solo mostraron el primer paso
   * **Túnel** de conversión: tasa de pérdida entre cada paso.
   In addition, a **Sector** type chart shows the population according to its source.

## Identificación del origen de tráfico {#identifying-the-traffic-source}

Se pueden utilizar dos modos diferentes para identificar de dónde proviene el visitante al acceder a una aplicación Web:

1. Envío de una entrega específica para otorgar acceso a las páginas de la aplicación Web: en este caso, la fuente de tráfico es esta entrega,
1. Asociación de la aplicación Web a un origen de tráfico dedicado: en este caso, debe ser una entrega externa de tipo &quot;fuente de tráfico&quot;. Se puede seleccionar desde las propiedades de la aplicación web o desde la asignación de destino.

   ![](assets/trackers_6.png)

Para identificar el origen del tráfico en una aplicación web, Adobe Campaign espera sucesivamente la siguiente información:

1. el identificador del envío de origen, si existe (cookie nlId),
1. el identificador del envío externo definido en las propiedades de la aplicación web, si existe,
1. el identificador del envío externo definido en la asignación de destino, si existe.

>[!NOTE]
>
>Recuerde que el seguimiento anónimo solo es posible si se ha activado la opción correspondiente en el asistente de implementación.
>
>For more on this, refer to the [Installation guide](../../installation/using/deploying-an-instance.md).

## Aplicaciones web diseñadas con el editor de contenido (DCE) {#web-applications-designed-with-digital-content-editor--dce-}

When a Web application is created using the HTML content editor - **Digital Content Editor (DCE)** - tracking tags are inserted from the **[!UICONTROL Properties]** tab of the editor. Para obtener más información sobre el editor de contenido (DCE), consulte [esta sección](../../web/using/about-campaign-html-editor.md).

![](assets/trackers_2.png)

Al utilizar la interfaz web, se deben insertar las etiquetas de seguimiento desde las propiedades de la página.

![](assets/trackers_3.png)

The **[!UICONTROL Display blocks]** icon lets you view the number of tracking tags defined for the page.

![](assets/trackers_4.png)

