---
title: Creación de etiquetas de seguimiento web
seo-title: Creación de etiquetas de seguimiento web
description: Creación de etiquetas de seguimiento web
seo-description: null
page-status-flag: never-activated
uuid: c5599bdd-e6b8-4db4-b0ca-aaee2adc1919
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: configuration
content-type: reference
topic-tags: setting-up-web-tracking
discoiquuid: 647ca037-4efb-4524-9642-11056d096aea
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 579329d9194115065dff2c192deb0376c75e67bd

---


# Creación de etiquetas de seguimiento web{#creating-web-tracking-tags}

Se debe hacer referencia a cada página del sitio que desee rastrear en la plataforma de Adobe Campaign. Esta referencia se puede realizar de dos maneras:

1. Definición manual de las direcciones URL que se rastrearán,
1. Creación sobre la marcha de direcciones URL para rastrear.

## Definición de las direcciones URL que se rastrearán en la aplicación {#defining-the-urls-to-be-tracked-in-the-application}

Este método permite definir manualmente las páginas que se rastrearán y, a continuación, generar un ejemplo de la etiqueta de seguimiento web asociada. Esta operación se define en el **[!UICONTROL Campaign execution>Resources>Web tracking tags]** nodo de la consola de cliente.

![](assets/d_ncs_integration_webtracking_screen.png)

Para generar el código HTML que se va a insertar en la página:

* Introduzca la etiqueta de la etiqueta: se mostrará en los registros de seguimiento,
* Indique la dirección URL de origen: este campo sirve para fines informativos y le permite indicar la página rastreada (opcional),
* Si es necesario, introduzca un período de validez.
* Haga clic en **[!UICONTROL Generate]** Código HTML.

A continuación, copie el código generado y péguelo en la página que desee rastrear.

## Creación sobre la marcha de direcciones URL para rastrear {#on-the-fly-creation-of-urls-to-be-tracked}

Puede crear las direcciones URL de seguimiento web sobre la marcha agregando información al valor del parámetro **tagid** :

* Tipo de página rastreada: &#39;w&#39; para WEB o &#39;t&#39; para TRANSACCIONES,
* El nombre interno de la carpeta en la que se debe crear la dirección URL.

Estos dos elementos de información deben concatenarse con el identificador de la página rastreada agregando el carácter &#39;|&#39;:

```
tagid=<identifier>|<type>|<foldername>
```

>[!CAUTION]
>
>Recuerde codificar el valor del parámetro **tagid** cuando se utiliza como parámetro de URL.

**Ejemplo**: creación de una URL de seguimiento web de tipo transacción.

**http://myserver.adobe.com/r/a?tagid=home%7Ct%7CMyFolder**
