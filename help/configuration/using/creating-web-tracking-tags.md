---
product: campaign
title: Creación de etiquetas de seguimiento web
description: Creación de etiquetas de seguimiento web
audience: configuration
content-type: reference
topic-tags: setting-up-web-tracking
exl-id: 160df6e1-43e5-4eb9-ad2f-5db444e314ea
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: tm+mt
source-wordcount: '262'
ht-degree: 4%

---

# Creación de etiquetas de seguimiento web{#creating-web-tracking-tags}

Se debe hacer referencia a cada página del sitio que se desea rastrear en la plataforma de Adobe Campaign. Esta referencia se puede realizar de dos maneras:

1. Definición manual de las direcciones URL que se van a rastrear,
1. Creación sobre la marcha de direcciones URL de las que realizar un seguimiento.

## Definición de las URL que se rastrearán en la aplicación {#defining-the-urls-to-be-tracked-in-the-application}

Este método permite definir manualmente las páginas que se van a rastrear y, a continuación, generar un ejemplo de la etiqueta de seguimiento web asociada. Esta operación se define en el nodo **[!UICONTROL Campaign execution>Resources>Web tracking tags]** de la consola del cliente.

![](assets/d_ncs_integration_webtracking_screen.png)

Para generar el código HTML que se va a insertar en la página:

* Introduzca la etiqueta de la etiqueta: se muestra en los registros de seguimiento,
* Indique la dirección URL de origen: este campo es informativo y permite indicar la página rastreada (opcional).
* Si es necesario, introduzca un periodo de validez,
* Haga clic en **[!UICONTROL Generate]** código HTML.

A continuación, copie el código generado y péguelo en la página para rastrear.

## Creación sobre la marcha de direcciones URL a rastrear {#on-the-fly-creation-of-urls-to-be-tracked}

Puede crear las URL de seguimiento web sobre la marcha añadiendo información al valor del parámetro **tagid**:

* Tipo de página rastreada: &quot;w&quot; para WEB o &quot;t&quot; para TRANSACCIONES,
* El nombre interno de la carpeta donde se debe crear la URL.

Estos dos fragmentos de información deben concatenarse con el identificador de la página rastreada añadiendo el carácter &#39;|&#39;:

```
tagid=<identifier>|<type>|<foldername>
```

>[!IMPORTANT]
>
>Recuerde codificar el valor del parámetro **tagid** cuando se utiliza como parámetro de URL.

**Ejemplo**: creación de una URL de seguimiento web de tipo de transacción.

**http://myserver.adobe.com/r/a?tagid=home%7Ct%7CMyFolder**
