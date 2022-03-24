---
product: campaign
title: Componentes web de Campaign y versión 100 en los navegadores Chrome y Firefox
description: Componentes web de Campaign y versión 100 en los navegadores Chrome y Firefox
hide: true
hidefromtoc: true
source-git-commit: d238f0aa28289c69c91dc6a028792260708ed9f3
workflow-type: tm+mt
source-wordcount: '619'
ht-degree: 0%

---

# El impacto de Chrome y Firefox v100 en los componentes web de Campaign {#version-100}

Google y Mozilla están advirtiendo que Chrome y Firefox pueden romper algunos sitios web debido a sus próximas versiones de 3 dígitos.

El cambio en el número de versión de 2 a 3 dígitos puede causar algunos problemas al visitar sitios web que no están preparados para este cambio. Es posible que algunas páginas web dejen de mostrarse correctamente en estas nuevas versiones del navegador.

La versión 100 de Chrome está configurada para su lanzamiento en **29 de marzo de 2022** y Firefox v100 en **3 de mayo de 2022**.

Mozilla y Google están probando la compatibilidad de los sitios web principales con antelación. Si hay problemas con los sitios que no pueden corregir antes de que se publiquen estas versiones, ambos tienen planes de copia de seguridad listos para asegurarse de que los sitios no se vean afectados.

Los posibles problemas o la pérdida de funcionalidad en el sitio web se originan en la cadena del agente de usuario que los navegadores envían a los sitios web que está visitando: el agente de usuario es una cadena que el explorador envía al sitio web para informar al sitio sobre el explorador y la versión que está utilizando, así como la tecnología asociada. Cuando el explorador envía una solicitud a un sitio web, se identifica con la cadena del agente de usuario antes de recuperar el contenido solicitado. Los datos de la cadena del agente de usuario ayudan al sitio web a entregar el contenido en un formato que se adapte a su navegador. La versión del agente de usuario se incrementa para que coincida con el número de versión del explorador. El paso de 2 a 3 dígitos puede causar problemas.

## ¿Se ha visto afectado?{#version-100-impact}

Adobe recomienda probar las aplicaciones web de Campaign, incluidos los formularios web y los estudios, para asegurarse de que sigan funcionando correctamente con estas nuevas versiones del explorador.

Esta recomendación se aplica a todas las aplicaciones web, especialmente si ha incluido código JavaScript.

Debe comprobar con Firefox y Chrome, móvil y escritorio.

## ¿Cómo realizar pruebas?{#version-100-test}

En Chrome y Firefox, puede configurar el explorador para que informe de la versión como 100 en este momento y luego informar y corregir cualquier problema que encuentre.

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

Con esta configuración, el navegador envía la nueva cadena del agente de usuario a los sitios web, indicando que el navegador es Firefox 100. Si tiene algún problema con los formularios web, debe crear un nuevo informe de errores para Mozilla. Considere la posibilidad de reconstruir estos formularios web antes de que este cambio esté disponible en general.

Para volver a cambiar el agente de usuario a su valor predeterminado, simplemente vuelva a `about:config` y busque `general.useragent.override` de nuevo.  Cuando aparezca, haga clic en el icono de papelera para eliminar la configuración y vuelva a iniciar el explorador.

### Pruebas con Chrome 100{#test-chrome-100}

Para probar el agente de usuario de Google Chrome 100 en sus propias aplicaciones web, puede habilitar esta prueba siguiendo los pasos siguientes:

1. Abra Chrome, escriba `chrome://flags` en la barra de direcciones y pulse Intro.
1. Buscar `Force major version to 100 in User-Agent` en el campo de búsqueda y actívelo como se muestra a continuación.

   ![](assets/force-user-agent-chrome.png)

1. Cierre y vuelva a iniciar el explorador.
1. Cierre las `chrome://flags` en el Navegador.

Con esta configuración, el explorador envía la nueva cadena del agente de usuario a los sitios web, indicando que el explorador es Chrome 100. Si tiene algún problema con los sitios web que visita, debe crear un nuevo informe de errores para Google. Considere la posibilidad de reconstruir estos formularios web antes de que este cambio esté disponible en general.

Para volver a cambiar el agente de usuario a su valor predeterminado, simplemente siga este proceso y cambie la configuración del indicador a `Default` y reinicie el explorador.
