---
product: campaign
title: Creación de etiquetas de seguimiento web
description: Obtenga información sobre cómo crear etiquetas de seguimiento web
feature: Application Settings
badge-v7-only: label="v7" type="Informative" tooltip="Se aplica solo a Campaign Classic v7"
exl-id: 160df6e1-43e5-4eb9-ad2f-5db444e314ea
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: tm+mt
source-wordcount: '272'
ht-degree: 2%

---

# Creación de etiquetas de seguimiento web{#creating-web-tracking-tags}

Se debe hacer referencia a cada página del sitio que desee rastrear en la plataforma de Adobe Campaign. Esta referencia se puede realizar de dos maneras:

1. Definición manual de las direcciones URL que se van a rastrear,
1. Creación sobre la marcha de direcciones URL para rastrear.

## Definición de las direcciones URL que se rastrearán en la aplicación {#defining-the-urls-to-be-tracked-in-the-application}

Este método permite definir manualmente las páginas de las que se debe realizar un seguimiento y generar un ejemplo de la etiqueta de seguimiento web asociada. Esta operación se define en la variable **[!UICONTROL Campaign execution>Resources>Web tracking tags]** de la consola del cliente.

![](assets/d_ncs_integration_webtracking_screen.png)

Para generar el código de HTML que se va a insertar en la página:

* Introduzca la etiqueta de la etiqueta: se muestra en los registros de seguimiento,
* Indique la dirección URL de origen: este campo tiene fines informativos y permite indicar la página rastreada (opcional).
* Si es necesario, introduzca un periodo de validez,
* Clic **[!UICONTROL Generate]** código del HTML.

A continuación, copie el código generado y péguelo en la página para realizar el seguimiento.

## Creación sobre la marcha de direcciones URL para rastrear {#on-the-fly-creation-of-urls-to-be-tracked}

Puede crear las direcciones URL de seguimiento web sobre la marcha añadiendo información al valor del **tagid** parámetro:

* Tipo de página rastreada: &quot;w&quot; para WEB o &quot;t&quot; para TRANSACCIÓN,
* Nombre interno de la carpeta donde se debe crear la dirección URL.

Estos dos fragmentos de información deben concatenarse con el identificador de la página rastreada agregando el carácter &quot;|&quot;:

```
tagid=<identifier>|<type>|<foldername>
```

>[!IMPORTANT]
>
>Recuerde codificar el valor del **tagid** cuando se utiliza como parámetro de URL.

**Ejemplo**: creación de una URL de seguimiento web de tipo de transacción.

**http://myserver.adobe.com/r/a?tagid=home%7Ct%7CMyFolder**
