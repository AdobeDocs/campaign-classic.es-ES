---
product: campaign
title: Privacidad
description: Obtenga más información sobre las prácticas recomendadas a seguir con respecto a la privacidad.
audience: installation
content-type: reference
topic-tags: prerequisites-and-recommendations-
exl-id: 0a3473bf-0528-486d-a799-8db86fece522
source-git-commit: f31591949bb033ff250cf4b33eddcc2c1d31cc6c
workflow-type: tm+mt
source-wordcount: '889'
ht-degree: 18%

---

# Privacidad {#privacy}

## Solicitudes de privacidad

Adobe Campaign ofrece un conjunto de herramientas que le ayudan a cumplir con la privacidad de RGPD y CCPA.

Consulte [esta página](../../platform/using/privacy-management.md) para obtener información general sobre qué es la administración de privacidad y los pasos de implementación en Adobe Campaign. También encontrará recomendaciones e información general del proceso y de los perfiles del usuario.

## Personalización de la URL {#url-personalization}

Al añadir enlaces personalizados al contenido, evite siempre cualquier personalización en la parte del nombre de host de la dirección URL para evitar posibles lagunas de seguridad. Los siguientes ejemplos nunca deben utilizarse en todos los atributos de URL &lt;`a href="">` o `<img src="">`:

* `<%= url >`
* `https://<%= url >`
* `https://<%= domain >/path`
* `https://<%= sub-domain >.domain.tld/path`
* `https://sub.domain<%= main domain %>/path`

### Recomendación

Para validar y asegurarse de que no está utilizando lo anterior, ejecute una consulta en la tabla de URL de seguimiento a través del [Editor de consultas genérico de campaña](../../platform/using/steps-to-create-a-query.md) o cree un flujo de trabajo con criterios de filtro en la [actividad de consulta](../../workflow/using/query.md).

Ejemplo:

1. Cree un flujo de trabajo y añada una actividad Query . Más información.

1. Abra la actividad Query y cree un filtro en la tabla nmsTrackingUrl de la siguiente manera: la URL de origen comienza con http://&lt;% o la URL de origen comienza con https://&lt;%.

1. Ejecute el flujo de trabajo y compruebe si hay resultados.

1. Si es así, abra la transición de salida para ver la lista de las direcciones URL.

<img src="assets/privacy-query-dynamic-url.png">

### Firma de URL

Para mejorar la seguridad, se ha introducido un mecanismo de firma para el seguimiento de vínculos en correos electrónicos. Está disponible en la versión 19.1.4 (9032@3a9dc9c) y Campaign 20.2. Esta función está habilitada de forma predeterminada.

>[!NOTE]
>
>Cuando se hace clic en una dirección URL firmada con formato incorrecto, se devuelve este error: &quot;No se encontró la dirección URL solicitada &#39;..&#39;.&quot;

Además, desde Campaign 20.2 y la versión [!DNL Gold Standard], puede utilizar una mejora para deshabilitar las direcciones URL generadas en versiones anteriores. Esta función está deshabilitada de forma predeterminada. Puede ponerse en contacto con el [Servicio de atención al cliente](https://helpx.adobe.com/es/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html) para habilitar esta función.

Si está ejecutando [!DNL Gold Standard] 19.1.4, puede que tenga problemas con los envíos de notificaciones push mediante vínculos de seguimiento o con los envíos que utilizan etiquetas de anclaje. Si es así, se recomienda desactivar la firma de URL.

Tanto si ejecuta Campaign en las instalaciones como en una arquitectura híbrida, debe ponerse en contacto con el [Servicio de atención al cliente](https://helpx.adobe.com/es/enterprise/using/support-for-experience-cloud.html) para que se deshabilite la firma URL.

Si está ejecutando Campaign en una arquitectura híbrida, antes de habilitar la firma de URL, asegúrese de que la instancia de mid-sourcing alojada se haya actualizado de la siguiente manera:
* Antes de la instancia de marketing local
* A la misma versión que la instancia de marketing local o a una versión ligeramente superior

De lo contrario, podrían surgir algunos de estos problemas:
* Antes de actualizar la instancia de intermediario, las direcciones URL se envían sin firma a través de esta instancia.
* Una vez que la instancia de intermediario se ha actualizado y la firma de URL se ha habilitado en ambas instancias, las direcciones URL que se habían enviado anteriormente sin firma se rechazan. El motivo es que los archivos de seguimiento proporcionados por la instancia de marketing solicitan una firma.

Para deshabilitar las direcciones URL que se han generado en versiones anteriores, siga estos pasos en todos los servidores de Campaign al mismo tiempo:

1. En el archivo de configuración del servidor (serverConf.xml), cambie **blockRedirectForUnsignedTrackingLink** a **true**.
1. Reinicie el servicio **nlserver**.
1. En el servidor de seguimiento, reinicie el servidor web (apache2 en Debian, httpd en CentOS/RedHat, IIS en Windows).

Para habilitar la firma de URL, siga estos pasos en todos los servidores de Campaign al mismo tiempo:

1. En el archivo de configuración del servidor (serverConf.xml), cambie **signEmailLinks** a **false**.
1. Reinicie el servicio **nlserver**.
1. En el servidor de seguimiento, reinicie el servidor web (apache2 en Debian, httpd en CentOS/RedHat, IIS en Windows).

## Restricción de datos

Debe asegurarse de que los usuarios autenticados con privilegios bajos no puedan acceder a las contraseñas cifradas. Para ello, hay dos formas principales: restringir el acceso solo a campos de contraseña o a toda la entidad (necesita una compilación >= 8770).

Esta restricción permite eliminar los campos con contraseñas, pero permite a la cuenta externa acceder a ella desde la interfaz de todos los usuarios. Consulte [esta página](../../configuration/using/restricting-pii-view.md).

1. Vaya a **[!UICONTROL Administration]** > **[!UICONTROL Configuration]** > **[!UICONTROL Data schemas]**.

1. Cree un nuevo **[!UICONTROL Extension of a schema]**.

   ![](assets/privacy-data-restriction.png)

1. Seleccione **[!UICONTROL External Account]** (extAccount).

1. En la última pantalla del asistente, puede editar el nuevo srcSchema para restringir el acceso a todos los campos de contraseña:

   Puede reemplazar el elemento principal (`<element name="extAccount" ... >`) por:

   ```
   <element name="extAccount">
       <attribute accessibleIf="$(loginId) = 0 or $(login) = 'admin'" name="password"/>
       <attribute accessibleIf="$(loginId) = 0 or $(login) = 'admin'" name="clientSecret"/>
   
       <element name="s3Account">
           <attribute accessibleIf="$(loginId) = 0 or $(login) = 'admin'" name="awsSecret"/>
       </element>
       <element name="wapPush">
           <attribute accessibleIf="$(loginId) = 0 or $(login) = 'admin'" name="password"/>
           <attribute accessibleIf="$(loginId) = 0 or $(login) = 'admin'" name="clientSecret"/>
       </element>
       <element name="mms">
           <attribute accessibleIf="$(loginId) = 0 or $(login) = 'admin'" name="password"/>
           <attribute accessibleIf="$(loginId) = 0 or $(login) = 'admin'" name="clientSecret"/>
       </element>
   </element>
   ```

   Por lo tanto, el srcSchema extendido puede tener el siguiente aspecto:

   ```
   <srcSchema _cs="External Accounts (cus)" created="2017-05-12 07:53:49.691Z" createdBy-id="0"
               desc="Definition of external accounts (Email, SMS...) used by the modules"
               entitySchema="xtk:srcSchema" extendedSchema="nms:extAccount" img="" label="External Accounts"
               labelSingular="External account" lastModified="2017-05-12 08:33:49.365Z"
               mappingType="sql" md5="E9BB0CD6A4375F500027C86EA854E101" modifiedBy-id="0"
               name="extAccount" namespace="cus" xtkschema="xtk:srcSchema">
       <createdBy _cs="Administrator (admin)"/>
       <modifiedBy _cs="Administrator (admin)"/>
       <element name="extAccount">
           <attribute accessibleIf="$(loginId) = 0 or $(login) = 'admin'" name="password"/>
           <attribute accessibleIf="$(loginId) = 0 or $(login) = 'admin'" name="clientSecret"/>
   
           <element name="s3Account">
               <attribute accessibleIf="$(loginId) = 0 or $(login) = 'admin'" name="awsSecret"/>
           </element>
           <element name="wapPush">
               <attribute accessibleIf="$(loginId) = 0 or $(login) = 'admin'" name="password"/>
               <attribute accessibleIf="$(loginId) = 0 or $(login) = 'admin'" name="clientSecret"/>
           </element>
           <element name="mms">
               <attribute accessibleIf="$(loginId) = 0 or $(login) = 'admin'" name="password"/>
               <attribute accessibleIf="$(loginId) = 0 or $(login) = 'admin'" name="clientSecret"/>
           </element>
       </element>
   </srcSchema>    
   ```

   >[!NOTE]
   >
   >Puede reemplazar `$(loginId) = 0 or $(login) = 'admin'` por `hasNamedRight('admin')` para permitir que todos los usuarios con derechos de administrador vean estas contraseñas.

## Protección de páginas que contienen PII

Recomendamos encarecidamente a los clientes locales que protejan las páginas que puedan contener información personal, como páginas espejo, aplicaciones web, etc.

El objetivo de este procedimiento es evitar que estas páginas se indexen, evitando así un posible riesgo de seguridad. A continuación se muestran algunos artículos útiles:

* [https://developers.google.com/search/reference/robots_txt](https://developers.google.com/search/reference/robots_txt)
* [https://developers.google.com/search/reference/robots_meta_tag](https://developers.google.com/search/reference/robots_meta_tag)
* [https://www.google.com/webmasters/tools/robots-testing-tool](https://www.google.com/webmasters/tools/robots-testing-tool)

Para proteger sus páginas, siga estos pasos:

1. Agregue un archivo robots.txt en la raíz del servidor web (Apache o IIS). Aquí está el contenido del archivo:

   ```
   # Make changes for all web spiders
   User-agent:
   *Disallow: /
   ```

   Para IIS, consulte [esta página](https://docs.microsoft.com/en-us/iis/extensions/iis-search-engine-optimization-toolkit/managing-robotstxt-and-sitemap-files).

   Para Apache, puede colocar el archivo en **/var/www/robots.txt** (Debian).

1. A veces, añadir un archivo **robots.txt** no es suficiente en términos de seguridad. Por ejemplo, si otro sitio web contiene un vínculo a la página, puede aparecer en un resultado de búsqueda.

Además del archivo **robots.txt**, se recomienda añadir un encabezado **X-Robots-Tag**. Puede hacerlo en Apache o IIS y en el archivo de configuración **serverConf.xml**.

Para obtener más información, consulte [este artículo](https://developers.google.com/search/reference/robots_meta_tag).
