---
solution: Campaign Classic
product: campaign
title: Creación de etiquetas de seguimiento web
description: Creación de etiquetas de seguimiento web
audience: configuration
content-type: reference
topic-tags: setting-up-web-tracking
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '262'
ht-degree: 4%

---


# Creación de etiquetas de seguimiento web{#creating-web-tracking-tags}

Cada página del sitio que desee rastrear debe ser referenciada en su plataforma de Adobe Campaign. Esta referencia se puede realizar de dos maneras:

1. Definición manual de las direcciones URL que se rastrearán,
1. Creación sobre la marcha de direcciones URL para rastrear.

## Definición de las direcciones URL que se rastrearán en la aplicación {#defining-the-urls-to-be-tracked-in-the-application}

Este método permite definir manualmente las páginas que se rastrearán y, a continuación, generar un ejemplo de la etiqueta de seguimiento Web asociada. Esta operación se define en el nodo **[!UICONTROL Campaign execution>Resources>Web tracking tags]** de la consola de cliente.

![](assets/d_ncs_integration_webtracking_screen.png)

Para generar el código HTML que se va a insertar en la página:

* Introduzca la etiqueta de la etiqueta: se mostrará en los registros de seguimiento,
* Indique la dirección URL de origen: este campo sirve para fines informativos y le permite indicar la página rastreada (opcional),
* Si es necesario, introduzca un período de validez.
* Haga clic en **[!UICONTROL Generate]** código HTML.

A continuación, copie el código generado y péguelo en la página que desee rastrear.

## Creación sobre la marcha de direcciones URL para rastrear {#on-the-fly-creation-of-urls-to-be-tracked}

Puede crear las direcciones URL de seguimiento web sobre la marcha agregando información al valor del parámetro **tagid**:

* Tipo de página rastreada: &#39;w&#39; para WEB o &#39;t&#39; para TRANSACCIONES,
* El nombre interno de la carpeta en la que se debe crear la dirección URL.

Estos dos elementos de información deben concatenarse con el identificador de la página rastreada agregando el carácter &#39;|&#39;:

```
tagid=<identifier>|<type>|<foldername>
```

>[!IMPORTANT]
>
>Recuerde codificar el valor del parámetro **tagid** cuando se utiliza como parámetro de URL.

**Ejemplo**: creación de una URL de seguimiento web de tipo transacción.

**http://myserver.adobe.com/r/a?tagid=home%7Ct%7CMyFolder**
