---
product: campaign
title: 'Nota técnica: Habilitar Microsoft Edge Chromium en el entorno de Campaign'
badge-v7-only: label="v7" type="Informative" tooltip="Solo se aplica a Campaign Classic v7"
description: Campaign - Edge Chromium
feature: Technote, Upgrade
exl-id: 22f4cbaf-ca37-47b9-b7dd-1ee73d5b348d
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: tm+mt
source-wordcount: '253'
ht-degree: 13%

---

# Cómo habilitar Microsoft Edge Chromium en su entorno {#edge-conf}




## ¿Qué ha cambiado?

Tras el fin de vida útil de Microsoft Internet Explorer 11, el motor de renderización de HTML para los paneles de la consola del cliente utiliza Edge Chromium, a partir de la versión 7.3 de Campaign Classic.

Además de la instalación del tiempo de ejecución de Microsoft Edge Webview 2, que ahora es [necesario para cualquier instalación de la consola del cliente](../../installation/using/installing-the-client-console.md#webview), Microsoft Edge Chromium debe estar habilitado en sus instancias.

## ¿Se ha visto afectado?

Si su entorno se ha actualizado a Campaign Classic v7.3 (o posterior), se verá afectado.

## ¿Cómo realizar la actualización?

* As a **alojado** cliente, el Adobe ya ha habilitado Microsoft Edge Chromium en sus instancias. No se requiere ninguna acción adicional.

* Como un **on-premise/híbrido** Cliente, debe habilitar Microsoft Edge Chromium en sus instancias.

  Al actualizar a Campaign Classic v7.3 (y versiones posteriores), un nuevo `webView2Mode` está disponible en el archivo de configuración del servidor de Campaign `serverConf.xml`. Este atributo debe estar habilitado.

  Para ello, aplique los pasos siguientes en todos sus entornos (MKT, MID, RT):

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
>

## Temas relacionados

* [Actualice su entorno](../../production/using/build-upgrade.md)
* [Preguntas frecuentes sobre la actualización de versiones](../../platform/using/faq-build-upgrade.md)
* [Instalación de la consola del cliente de Campaign](../../installation/using/installing-the-client-console.md)
