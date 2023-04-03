---
product: campaign
title: 'Nota técnica: Habilitación de Microsoft Edge Chromium en el entorno de Campaign'
description: Campaign - Cromium perimetral
hide: true
hidefromtoc: true
source-git-commit: 17ef8f92ab5dbecadf20140c3faff735d92c8223
workflow-type: tm+mt
source-wordcount: '246'
ht-degree: 13%

---


# Cómo habilitar Microsoft Edge Chromium en su entorno {#edge-conf}

![](../../assets/v7-only.svg)


## ¿Qué ha cambiado?

Tras el fin de vida útil de Microsoft Internet Explorer 11, el motor de renderización del HTML para los paneles de la consola del cliente utiliza Edge Chromium, a partir del Campaign Classic v7.3.

Además de la instalación del tiempo de ejecución de Microsoft Edge Webview 2, que ahora es [necesario para cualquier instalación de la consola del cliente](../../installation/using/installing-the-client-console.md#webview), Microsoft Edge Chromium debe estar habilitado en las instancias.

## ¿Se ha visto afectado?

Si su entorno se ha actualizado a Campaign Classic v7.3 (o posterior), se verá afectado.

## ¿Cómo realizar la actualización?

* Como **alojado** cliente, Adobe ya ha habilitado Microsoft Edge Chromium en sus instancias. No se requiere ninguna acción adicional.

* Como **local/híbrido** cliente, debe habilitar Microsoft Edge Chromium en sus instancias.

   Al actualizar a Campaign Classic 7.3 (y versiones posteriores), se muestra una `webView2Mode` está disponible en el archivo de configuración del servidor de Campaign `serverConf.xml`. Este atributo debe estar habilitado.

   Para ello, siga los siguientes pasos en todos sus entornos (MKT, MID, RT):

   1. Edite el archivo de configuración del servidor de Campaign (`serverConf.xml`)
   1. En el `<web>` módulo, conjunto `webView2Mode = "1"`
   1. Ejecute el siguiente comando para volver a cargar la configuración del servidor:

      ```
      nlserver config -reload
      ```

   1. Ejecute el siguiente comando para reiniciar el servidor web:

      ```
      nlserver restart web
      ```

   1. Si su entorno utiliza Apache como servidor web, ejecute el siguiente comando para reiniciar Apache:

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

