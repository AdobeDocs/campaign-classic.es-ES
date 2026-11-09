---
product: campaign
title: Personalización y privacidad
description: Conozca las prácticas recomendadas de seguridad para la privacidad y personalización
feature: Installation, Privacy, Privacy Tools, URL Personalization
exl-id: 0a3473bf-0528-486d-a799-8db86fece522
TQID: 'https://experienceleague.adobe.com/8u-ItsbouC0wIsamVYfyzQR1o-z-jY90Z3pKem-yarc'
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
    internal-label: Campaign
  - id: fd6e6e36-54e4-4f1a-96fc-1a750e400d50
    internal-label: Campaign Classic v7
feature_v2:
  - id: a7760dfc-5c44-4d77-bb68-c50b1e265c93
    internal-label: Security and privacy
  - id: c5474392-5419-4296-9e41-f6f4ce4f6e9b
    internal-label: Administration
  - id: c858a28b-ea19-49b0-8d48-828717fad89c
    internal-label: Prepare and test messages
subfeature_v2:
  - id: ac72e249-ebbf-4bb6-96c9-596af925419a
    internal-label: Privacy tools
  - id: ac9c0a9c-8a76-4419-bd64-9c34c5782666
    internal-label: Privacy
  - id: fb2a841f-c522-491f-9901-a1b939d252df
    internal-label: Security
  - id: e656c701-3899-4db3-989c-de0980ddfffa
    internal-label: Installation
  - id: f55cfb22-471c-4161-8ea1-12868351e460
    internal-label: URL personalization
topic_v2:
  - id: b5ce8718-c3af-4fdb-a1a9-fca32f83a87c
    internal-label: Implementation
  - id: cdd65e7e-8839-44a2-bc21-0e03623b5dd1
    internal-label: Optimization
  - id: d095671a-1355-40aa-8b5f-06c33c68080b
    internal-label: Security
  - id: e0eb8757-182f-49f3-94a4-1587d16f5094
    internal-label: Personalization
  - id: eddd9b14-83bd-4ff4-9072-54a4a484abb7
    internal-label: Administration
  - id: f4e6943a-c91a-4134-a2c7-f4f20cfff2f0
    internal-label: Privacy
source-git-commit: 758d5159759b19f7ef32e8cc8f6237547599e727
workflow-type: tm+mt
source-wordcount: '848'
ht-degree: 18%
---
# Personalización y privacidad {#privacy}

Esta página cubre la personalización de URL, la firma de URL y la protección de las páginas que contienen información personal.

>[!NOTE]
>
>Como parte del proceso de transición de la versión 7 a 8 de Campaign, toda la documentación de Campaign Classic se ha optimizado y reorganizado. Ahora, las funciones comunes solo están disponibles en el conjunto de documentación de Campaign v8. Para obtener más información sobre las solicitudes de privacidad y las restricciones de datos, consulte la [documentación de Campaign v8](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/privacy/security#data-restriction){target=_blank}.
>
>[![imagen](../../assets/do-not-localize/learn-more-button.svg)](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/privacy/security#data-restriction){target=_blank}

En Campaign Classic v7, la restricción del acceso a toda la entidad requiere la compilación 8770 o posterior.

## Personalización de la URL {#url-personalization}

Al añadir enlaces personalizados al contenido, evite siempre cualquier personalización en la parte del nombre de host de la dirección URL para evitar posibles lagunas de seguridad. Los siguientes ejemplos nunca deben utilizarse en todos los atributos de URL &lt;`a href="">` o `<img src="">`:

* `<%= url >`
* `https://<%= url >`
* `https://<%= domain >/path`
* `https://<%= sub-domain >.domain.tld/path`
* `https://sub.domain<%= main domain %>/path`

### Recomendación

Para validar y asegurarse de que no está utilizando lo anterior, ejecute una consulta en la tabla de URL de seguimiento a través de [Editor de consultas genérico de Campaign](https://experienceleague.adobe.com/es/docs/campaign/campaign-v8/data/query/query-editor){target="_blank"} (documentación de Campaign v8) o cree un flujo de trabajo con criterios de filtro en la actividad de consulta. Consulte la [documentación de Campaign v8](https://experienceleague.adobe.com/docs/campaign/automation/workflows/wf-activities/targeting-activities/query.html?lang=es){target="_blank"}.

Ejemplo:

1. Cree un flujo de trabajo y agregue una actividad **Query**. Consulte la [documentación de Campaign v8](https://experienceleague.adobe.com/docs/campaign/automation/workflows/wf-activities/targeting-activities/query.html?lang=es){target="_blank"}.

1. Abra la actividad **Query** y cree un filtro en la tabla `nmsTrackingUrl` de la siguiente manera:

   `source URL starts with http://<% or source URL starts with https://<%`

1. Ejecute el flujo de trabajo y compruebe si hay resultados.

1. Si es así, abra la transición de salida para ver la lista de las direcciones URL.

   ![](assets/privacy-query-dynamic-url.png)


### Firma de URL

Para mejorar la seguridad, se ha introducido un mecanismo de firma para el seguimiento de vínculos en correos electrónicos. Está disponible a partir de las versiones 19.1.4 (9032@3a9dc9c) y 20.2. Esta función está habilitada de forma predeterminada.

>[!NOTE]
>
>Cuando se hace clic en una dirección URL firmada con formato incorrecto, se devuelve este error: `Requested URL '…' was not found.`

Además, se puede utilizar una mejora para deshabilitar las direcciones URL generadas en versiones anteriores. Esta función está desactivada de forma predeterminada. Póngase en contacto con el [Servicio de atención al cliente](https://helpx.adobe.com/es/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html) para habilitar esta función.

Si está ejecutando la versión 19.1.4, puede experimentar problemas con los envíos de notificaciones push mediante vínculos de seguimiento o con los envíos que utilizan etiquetas de anclaje. Si es así, le recomendamos que deshabilite la firma de URL.

Como cliente híbrido, de Managed Cloud Services o alojado en Campaign, debe ponerse en contacto con el [Servicio de atención al cliente](https://helpx.adobe.com/es/enterprise/using/support-for-experience-cloud.html) para que se deshabilite la firma de URL.

Si está ejecutando Campaign en una arquitectura híbrida, antes de habilitar la firma URL, asegúrese de que la instancia intermediaria alojada se haya actualizado de la siguiente manera:

* Primero, la instancia de marketing on-premise
* A continuación, actualice a la misma versión que la instancia de marketing local o a una versión ligeramente superior

De lo contrario, pueden producirse algunos de estos problemas:

* Antes de actualizar la instancia de intermediario, las direcciones URL se envían sin firma a través de esta instancia.
* Una vez que se ha actualizado la instancia de intermediario y se ha habilitado la firma de URL en ambas instancias, se rechazan las URL que se habían enviado anteriormente sin firma. El motivo es que los archivos de seguimiento proporcionados por la instancia de marketing solicitan una firma.

Para deshabilitar las direcciones URL que se han generado en versiones anteriores, siga estos pasos en todos los servidores de Campaign al mismo tiempo:

1. En el archivo de configuración del servidor (`serverConf.xml`), cambie la opción **blockRedirectForUnsignedTrackingLink** a **true**.
1. Reinicie el servicio `nlserver`.
1. En el servidor `tracking`, reinicie el servidor `web` (apache2 en Debian, httpd en CentOS/RedHat, IIS en Windows).

Para habilitar la firma de URL, siga estos pasos en todos los servidores de Campaign al mismo tiempo:

1. En el archivo de configuración del servidor (`serverConf.xml`), cambie la opción **signEmailLinks** a **true**.
1. Reinicie el servicio **nlserver**.
1. En el servidor `tracking`, reinicie el servidor `web` (apache2 en Debian, httpd en CentOS/RedHat, IIS en Windows).

## Proteger páginas con API

Recomendamos encarecidamente a los clientes locales que protejan las páginas que puedan contener información personal (PI), como páginas espejo, aplicaciones web, etc.

El objetivo de este procedimiento es evitar que estas páginas se indexen, lo que evita un posible riesgo de seguridad. Estos son algunos artículos útiles:

* [https://developers.google.com/search/reference/robots_txt](https://developers.google.com/search/reference/robots_txt)
* [https://developers.google.com/search/reference/robots_meta_tag](https://developers.google.com/search/reference/robots_meta_tag)

Para proteger las páginas, siga estos pasos:

1. Agregue un archivo `robots.txt` en la raíz del servidor web (Apache o IIS). Este es el contenido del archivo:

   ```sql
   # Make changes for all web spiders
   User-agent:
   *Disallow: /
   ```

   Para IIS, consulte [esta página](https://docs.microsoft.com/en-us/iis/extensions/iis-search-engine-optimization-toolkit/managing-robotstxt-and-sitemap-files).

   Para Apache, puede colocar el archivo en **/var/www/robots.txt** (Debian).

1. A veces, agregar un archivo **robots.txt** no es suficiente en términos de seguridad. Por ejemplo, si otro sitio web contiene un vínculo a su página, podría aparecer en un resultado de búsqueda.

   Además del archivo **robots.txt**, se recomienda agregar un encabezado **X-Robots-Tag**. Puede hacerlo en Apache o IIS y en el archivo de configuración **serverConf.xml**.

   Para obtener más información, consulte [este artículo](https://developers.google.com/search/reference/robots_meta_tag).
