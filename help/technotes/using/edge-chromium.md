---
product: campaign
title: 'Nota técnica: Habilitación de Microsoft Edge Chromium en el entorno de Campaign'
description: Campaign - Cromium perimetral
hide: true
hidefromtoc: true
source-git-commit: d9f57d4e5b6f880907040344ece40546456a2321
workflow-type: tm+mt
source-wordcount: '228'
ht-degree: 14%

---


# Cómo habilitar Microsoft Edge Chromium en su entorno {#edge-conf}

![](../../assets/v7-only.svg)


## ¿Qué ha cambiado?

Tras el fin de vida útil de Microsoft Internet Explorer 11, el motor de renderización del HTML para Adobe Services (página de inicio de sesión) en la consola del cliente ahora utiliza Microsoft Edge Chromium, a partir del Campaign Classic v7.3.

Además de la instalación del tiempo de ejecución de Microsoft Edge Webview 2, que ahora es [necesario para cualquier instalación de la consola del cliente](../../installation/using/installing-the-client-console.md#webview), Microsoft Edge Chromium debe estar habilitado en las instancias.

## ¿Se ha visto afectado?

Si su entorno se ha actualizado a Campaign Classic v7.3 (o posterior), se verá afectado.

## ¿Cómo realizar la actualización?

* Como **alojado** cliente, Adobe ya ha habilitado Microsoft Edge Chromium en sus instancias.

* Como **local/híbrido** cliente, debe habilitar Microsoft Edge Chromium en sus instancias.

   Al actualizar a Campaign Classic 7.3 (y versiones posteriores), se muestra una `webView2Mode` está disponible en el archivo de configuración del servidor de Campaign `serverConf.xml`. Este atributo debe estar habilitado.

   Para ello, siga los siguientes pasos en todos sus entornos (MKT, MID, RT):

   1. Edite el archivo de configuración del servidor de Campaign (`serverConf.xml`)
   1. En el `<web>` módulo, conjunto `webView2Mode = "1"`
   1. Vuelva a cargar la configuración del servidor

      ```
      nlserver config -reload
      ```

   1. Reinicio del servidor web

      ```
      nlserver restart web
      ```

   1. Si su entorno se ejecuta en Apache, reinicie Apache.

      ```
      /etc/init.d/apache2 restart
      ```


>[!NOTE]
>
>En caso de que tenga preguntas acerca de estos cambios, póngase en contacto con el [Servicio de atención al cliente de Adobe](https://helpx.adobe.com/es/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html).

## Temas relacionados

* [Actualice su entorno](../../production/using/build-upgrade.md)
* [Preguntas frecuentes sobre la actualización de versiones](../../platform/using/faq-build-upgrade.md)
* [Instalación de la consola del cliente de Campaign](../../installation/using/installing-the-client-console.md)

