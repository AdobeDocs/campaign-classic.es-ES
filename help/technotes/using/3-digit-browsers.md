---
product: campaign
title: Componentes web de Campaign y versión 100 en los navegadores Chrome Firefox y Edge
description: Componentes web de Campaign y versión 100 en los navegadores Chrome, Firefox y Edge
exl-id: 2016279a-7b02-4399-b2ed-9a15456de816
source-git-commit: b8329e24f07ec8b3dd89f655b47699f130266008
workflow-type: tm+mt
source-wordcount: '634'
ht-degree: 0%

---

# Impacto de la versión del explorador de 3 dígitos en los componentes web de Campaign {#version-100}

Google y Mozilla están advirtiendo que Chrome y Firefox pueden romper algunos sitios web debido a sus próximas versiones de 3 dígitos.

La versión 100 de Chrome está configurada para su lanzamiento en **29 de marzo de 2022** y Firefox v100 en **3 de mayo de 2022**.

Microsoft lanzó Edge v100 a principios de marzo de 2022.

El cambio en el número de versión de 2 a 3 dígitos puede causar algunos problemas al visitar sitios web que no están preparados para este cambio. Es posible que algunas páginas web dejen de mostrarse correctamente en estas nuevas versiones del navegador.

La compatibilidad de los principales sitios web se ha probado con antelación. Si hay problemas con los sitios que no se pueden solucionar antes de que se publiquen estas versiones, las empresas tienen planes de copia de seguridad listos para asegurarse de que los sitios no se vean afectados.

Los posibles problemas o la pérdida de funcionalidad en el sitio web se originan en la cadena del agente de usuario que los navegadores envían a los sitios web que está visitando: el agente de usuario es una cadena que el explorador envía al sitio web para informar al sitio sobre el explorador y la versión que está utilizando, así como la tecnología asociada. Cuando el explorador envía una solicitud a un sitio web, se identifica con la cadena del agente de usuario antes de recuperar el contenido solicitado. Los datos de la cadena del agente de usuario ayudan al sitio web a entregar el contenido en un formato que se adapte a su navegador. La versión del agente de usuario se incrementa para que coincida con el número de versión del explorador. El paso de 2 a 3 dígitos puede causar problemas.

## ¿Se ha visto afectado?{#version-100-impact}

Adobe recomienda probar las aplicaciones web de Campaign, incluidos los formularios web y los estudios, para asegurarse de que sigan funcionando correctamente con estas nuevas versiones del explorador.

Esta recomendación se aplica a todas las aplicaciones web, especialmente si ha incluido código JavaScript.

Debe comprobarlo con todos los navegadores, móviles y de escritorio.

## ¿Cómo realizar pruebas?{#version-100-test}

Puede configurar los navegadores para que informen de la versión como 100 en este momento y luego informar y corregir cualquier problema que encuentre.

Con esta configuración, el explorador envía la nueva cadena del agente de usuario a los sitios web, indicando que el explorador es v100. Si tiene algún problema con los formularios web, debe crear un error para el editor del explorador. Considere la posibilidad de volver a crear estos formularios web antes de que estas actualizaciones estén disponibles.

### Pruebas con Firefox 100{#test-firefox-100}

Para probar las páginas web con Mozilla Firefox 100, puede simular el próximo cambio del agente de usuario en las aplicaciones web cambiando manualmente la cadena del agente de usuario.

1. Abra Firefox, escriba `about:config` en la barra de direcciones y pulse Intro.
1. Buscar `general.useragent.override`.
1. Seleccione &quot;Cadena&quot; y, a continuación, haga clic en el signo más (+).

   ![](assets/force-user-agent-firefox.png)

1. Introduzca el siguiente texto en el campo :

   ```
   Mozilla/5.0 (Windows NT 10.0; rv:100.0) Gecko/20100101 Firefox/100.0
   ```

1. Haga clic en el botón de marca de verificación azul para guardar la configuración.
1. Cierre y vuelva a iniciar el explorador.

Para volver a cambiar el agente de usuario a su valor predeterminado, simplemente vuelva a `about:config` y busque `general.useragent.override` de nuevo.  Cuando aparezca, haga clic en el icono de papelera para eliminar la configuración y vuelva a iniciar el explorador.

### Pruebas con Chrome 100{#test-chrome-100}

Para probar el agente de usuario de Google Chrome 100 en sus propias aplicaciones web, puede habilitar esta prueba siguiendo los pasos siguientes:

1. Abra Chrome, escriba `chrome://flags` en la barra de direcciones y pulse Intro.
1. Buscar `Force major version to 100 in User-Agent` en el campo de búsqueda y actívelo como se muestra a continuación.

   ![](assets/force-user-agent-chrome.png)

1. Reinicie el explorador.
1. Cierre las `chrome://flags` pestaña .

Para volver a cambiar el agente de usuario a su valor predeterminado, simplemente siga este proceso y cambie la configuración del indicador a `Default` y reinicie el explorador.


### Pruebas con Microsoft Edge 100{#test-ms-edge-100}

A partir de la versión 97, los propietarios del sitio pueden emular esta versión habilitando el indicador de experimento  `#force-major-version-to-100` en `edge://flags`.

1. Abra Microsoft Edge, escriba `edge://flags` en la barra de direcciones y pulse Intro.
1. Buscar `force-major-version-to-100` y actívelo como se muestra a continuación.

   ![](assets/force-user-agent-edge.png)

1. Reinicie el explorador.
1. Cierre las `edge://flags` pestaña .

Para volver a cambiar el agente de usuario a su valor predeterminado, simplemente siga este proceso y cambie la configuración del indicador a `Default` y reinicie el explorador.
