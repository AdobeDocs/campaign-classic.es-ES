---
product: campaign
title: Componentes web de Campaign y versión 100 en los navegadores Chrome Firefox y Edge
description: Componentes web de Campaign y versión 100 en los navegadores Chrome, Firefox y Edge
feature: Technote
exl-id: 2016279a-7b02-4399-b2ed-9a15456de816
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: tm+mt
source-wordcount: '644'
ht-degree: 0%

---

# Impactos de la versión del explorador de 3 dígitos en los componentes web de Campaign {#version-100}

Google y Mozilla advierten que Chrome y Firefox pueden romper algunos sitios web debido a sus próximas versiones de 3 dígitos.

La versión 100 de Chrome está configurada para su lanzamiento el **29 de marzo de 2022** y Firefox v100 en **3 de mayo de 2022**.

Microsoft lanzó Edge v100 a principios de marzo de 2022.

El cambio en el número de versión de 2 a 3 dígitos puede causar algunos problemas al visitar sitios web que no están preparados para este cambio. Es posible que algunas páginas web dejen de mostrarse correctamente en estas nuevas versiones del explorador.

La compatibilidad de los principales sitios web se ha probado con antelación. Si hay problemas con sitios que no se pueden corregir antes de que se publiquen estas versiones, las empresas tienen planes de copia de seguridad listos para garantizar que los sitios no se vean afectados.

Los problemas potenciales o la pérdida de funcionalidad en el sitio web se originan en la cadena del agente de usuario que los navegadores envían a los sitios web que está visitando: el agente de usuario es una cadena enviada por el explorador al sitio web para permitir que el sitio sepa qué explorador y versión está utilizando y la tecnología asociada. Cuando el explorador envía una solicitud a un sitio web, se identifica con la cadena del agente de usuario antes de recuperar el contenido solicitado. Los datos de la cadena del agente de usuario ayudan al sitio web a entregar el contenido en un formato que se adapte a su explorador. La versión del agente de usuario se incrementa para coincidir con el número de versión del explorador. Pasar de 2 a 3 dígitos puede causar problemas.

## ¿Se ha visto afectado?{#version-100-impact}

El Adobe recomienda probar las aplicaciones web de Campaign, incluidos los formularios web y las encuestas, para asegurarse de que siguen funcionando correctamente con estas nuevas versiones del explorador.

Esta recomendación se aplica a todas las aplicaciones web y especialmente si ha incluido código JavaScript.

Debe comprobarlo con todos los navegadores, móviles y de escritorio.

## ¿Cómo realizar la prueba?{#version-100-test}

Puede configurar los exploradores para que comuniquen la versión como 100 ahora mismo y, a continuación, informe y corrija los problemas que encuentre.

Con esta configuración, el explorador envía la nueva cadena del agente de usuario a los sitios web, lo que indica que el explorador es v100. Si tiene algún problema con los formularios web, debe crear un error para el editor del explorador. Considere la posibilidad de reconstruir estos formularios web antes de que estas actualizaciones estén disponibles en general.

### Prueba con Firefox 100{#test-firefox-100}

Para probar las páginas web con Mozilla Firefox 100, puede simular el próximo cambio de agente de usuario en las aplicaciones web cambiando manualmente la cadena del agente de usuario.

1. Abra Firefox, introduzca. `about:config` en la barra de direcciones, y presione intro.
1. Buscar por `general.useragent.override`.
1. Seleccione &quot;Cadena&quot; y luego haga clic en el signo más (+).

   ![](assets/force-user-agent-firefox.png)

1. Introduzca el siguiente texto en el campo:

   ```
   Mozilla/5.0 (Windows NT 10.0; rv:100.0) Gecko/20100101 Firefox/100.0
   ```

1. Haga clic en el botón de marca de verificación azul para guardar la configuración.
1. Cierre y vuelva a iniciar el explorador.

Para volver a cambiar el agente de usuario a su valor predeterminado, simplemente vuelva a `about:config` y buscar `general.useragent.override` configurando de nuevo.  Cuando aparezca, haga clic en el icono de papelera para eliminar la configuración y vuelva a iniciar el explorador.

### Prueba con Chrome 100{#test-chrome-100}

Para probar el agente de usuario de Google Chrome 100 en sus propias aplicaciones web, puede habilitar esta prueba siguiendo los pasos siguientes:

1. Abra Chrome y escriba `chrome://flags` en la barra de direcciones, y presione intro.
1. Buscar `Force major version to 100 in User-Agent` en el campo de búsqueda, y actívelo como se muestra a continuación.

   ![](assets/force-user-agent-chrome.png)

1. Reinicie el explorador.
1. Cierre el `chrome://flags` pestaña.

Para volver a cambiar el agente de usuario a su valor predeterminado, simplemente siga este proceso y cambie la configuración del indicador a `Default` y reinicie el explorador.


### Pruebas con Microsoft Edge 100{#test-ms-edge-100}

A partir de v97, los propietarios del sitio pueden emular esta versión habilitando el indicador de experimento  `#force-major-version-to-100` in `edge://flags`.

1. Abra Microsoft Edge y escriba `edge://flags` en la barra de direcciones, y presione intro.
1. Buscar por `force-major-version-to-100` y actívelo como se muestra a continuación.

   ![](assets/force-user-agent-edge.png)

1. Reinicie el explorador.
1. Cierre el `edge://flags` pestaña.

Para volver a cambiar el agente de usuario a su valor predeterminado, simplemente siga este proceso y cambie la configuración del indicador a `Default` y reinicie el explorador.
