---
product: campaign
title: 'Nota técnica: Habilitar Microsoft Edge Chromium en el entorno de Campaign'
description: 'Campaign: Edge Chromium'
feature: Technote, Upgrade
exl-id: 22f4cbaf-ca37-47b9-b7dd-1ee73d5b348d
TQID: https://experienceleague.adobe.com/6CrzuBxAxGlXi08NxwdnigO2bNu700luLxnz-3KzZ18
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
topic_v2:
  - id: f4e6943a-c91a-4134-a2c7-f4f20cfff2f0
source-git-commit: 4c295c0dabae8aba298390a3da2422a3fa1219f9
workflow-type: tm+mt
source-wordcount: 274
ht-degree: 10%

---

# Cómo habilitar Microsoft Edge Chromium en su entorno {#edge-conf}

## ¿Qué ha cambiado?

Tras el fin de vida útil de Microsoft Internet Explorer 11, el motor de renderización de HTML para los paneles de la consola del cliente utiliza Edge Chromium, a partir de Campaign Classic v7.3.

Además de la instalación del tiempo de ejecución de Microsoft Edge Webview 2, que ahora es [necesario para cualquier instalación de la consola del cliente](../../installation/using/installing-the-client-console.md#webview), Microsoft Edge Chromium debe habilitarse en sus instancias.

>[!NOTE]
>
>Después de habilitar Microsoft Edge Chromium, el acceso directo `Ctrl+F` (Windows) o `Command+F` (Mac) para abrir el cuadro de diálogo de búsqueda del explorador dejará de funcionar.

## ¿Se ha visto afectado?

Si su entorno se ha actualizado a Campaign Classic v7.3 (o posterior), se verá afectado.

## ¿Cómo realizar la actualización?

* Como cliente de **hosted**, Adobe ya habilitó Microsoft Edge Chromium en sus instancias. No se requiere ninguna acción adicional.

* Como cliente de **on-premise/hybrid**, necesita habilitar Microsoft Edge Chromium en sus instancias.

  Al actualizar a Campaign Classic v7.3 (y posterior), hay un nuevo atributo `webView2Mode` disponible en el archivo de configuración del servidor de Campaign `serverConf.xml`. Este atributo debe estar habilitado.

  Para ello, aplique los pasos siguientes en todos sus entornos (MKT, MID, RT):

   1. Edite el archivo de configuración del servidor de Campaign (`serverConf.xml`)
   1. En el módulo `<web>`, establezca `webView2Mode = "1"`
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
