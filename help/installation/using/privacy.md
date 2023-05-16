---
product: campaign
title: Personalización y privacidad
description: Conozca las prácticas recomendadas de seguridad para la privacidad y la personalización
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
feature: URL Personalization, Privacy
exl-id: 0a3473bf-0528-486d-a799-8db86fece522
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: tm+mt
source-wordcount: '845'
ht-degree: 13%

---

# Personalización y privacidad {#privacy}




## Personalización de la URL {#url-personalization}

Al añadir enlaces personalizados al contenido, evite siempre cualquier personalización en la parte del nombre de host de la dirección URL para evitar posibles lagunas de seguridad. Los siguientes ejemplos nunca deben utilizarse en todos los atributos de URL &lt;`a href="">` o `<img src="">`:

* `<%= url >`
* `https://<%= url >`
* `https://<%= domain >/path`
* `https://<%= sub-domain >.domain.tld/path`
* `https://sub.domain<%= main domain %>/path`

### Recomendación

Para validar y asegurarse de que no está utilizando lo anterior, ejecute una consulta en la tabla URL de seguimiento mediante [Editor de consultas genérico de campaña](../../platform/using/steps-to-create-a-query.md) o crear un flujo de trabajo con criterios de filtro en la variable [actividad de consulta](../../workflow/using/query.md).

Ejemplo:

1. Creación de un flujo de trabajo y adición de **Consulta** actividad. [Más información](../../workflow/using/query.md).

1. Abra el **Consulta** y cree un filtro en la `nmsTrackingUrl` como se indica a continuación:

   `source URL starts with http://<% or source URL starts with https://<%`

1. Ejecute el flujo de trabajo y compruebe si hay resultados.

1. Si es así, abra la transición de salida para ver la lista de las direcciones URL.

   ![](assets/privacy-query-dynamic-url.png)


### Firma de URL

Para mejorar la seguridad, se ha introducido un mecanismo de firma para el seguimiento de vínculos en correos electrónicos. Está disponible a partir de las versiones 19.1.4 (9032@3a9dc9c) y 20.2. Esta función está habilitada de forma predeterminada.

>[!NOTE]
>
>Cuando se hace clic en una dirección URL firmada con formato incorrecto, se devuelve este error: `Requested URL '…' was not found.`

Además, puede utilizar una mejora para deshabilitar las direcciones URL generadas en versiones anteriores. Esta función está deshabilitada de forma predeterminada. Puede ponerse en contacto con [Servicio de atención al cliente](https://helpx.adobe.com/es/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html) para activar esta función.

Si se ejecuta en la versión 19.1.4, es posible que se produzcan problemas con las entregas de notificaciones push mediante vínculos de seguimiento o con las entregas que utilizan etiquetas de anclaje. Si es así, se recomienda desactivar la firma de URL.

Como cliente alojado en una campaña, Cloud Services administrados o híbrido, debe ponerse en contacto con [Servicio de atención al cliente](https://helpx.adobe.com/es/enterprise/using/support-for-experience-cloud.html) para que la firma URL esté deshabilitada.

Si está ejecutando Campaign en una arquitectura híbrida, antes de habilitar la firma de URL, asegúrese de que la instancia de mid-sourcing alojada se haya actualizado de la siguiente manera:

* Primero la instancia de marketing local
* A continuación, actualice a la misma versión que la instancia de marketing local o a una versión ligeramente superior

De lo contrario, podrían producirse algunos de estos problemas:

* Antes de actualizar la instancia de intermediario, las direcciones URL se envían sin firma a través de esta instancia.
* Una vez que la instancia de intermediario se ha actualizado y la firma de URL se ha habilitado en ambas instancias, las direcciones URL que se habían enviado anteriormente sin firma se rechazan. El motivo es que los archivos de seguimiento proporcionados por la instancia de marketing solicitan una firma.

Para deshabilitar las direcciones URL que se han generado en versiones anteriores, siga estos pasos en todos los servidores de Campaign al mismo tiempo:

1. En el archivo de configuración del servidor (`serverConf.xml`), cambie la variable **blockRedirectForUnsignedTrackingLink** a **true**.
1. Reinicie el `nlserver` servicio.
1. En el `tracking` servidor, reinicie el `web` servidor (apache2 en Debian, httpd en CentOS/RedHat, IIS en Windows).

Para habilitar la firma de URL, siga estos pasos en todos los servidores de Campaign al mismo tiempo:

1. En el archivo de configuración del servidor (`serverConf.xml`), cambiar **signEmailLinks** para **true**.
1. Reinicie el servicio **nlserver**.
1. En el `tracking` servidor, reinicie el `web` servidor (apache2 en Debian, httpd en CentOS/RedHat, IIS en Windows).

## Restricción de datos

Debe asegurarse de que un usuario autenticado con privilegios bajos no pueda acceder a las contraseñas cifradas. Para ello, restrinja el acceso solo a los campos de contraseña o a toda la entidad (necesita una compilación >= 8770).

Esta restricción permite eliminar los campos con contraseñas, pero permite a la cuenta externa acceder a ella desde la interfaz de todos los usuarios. [Más información](../../configuration/using/restricting-pii-view.md).

Para ello, siga los pasos a continuación:

1. Vaya a la **[!UICONTROL Administration]** > **[!UICONTROL Configuration]** > **[!UICONTROL Data schemas]** carpeta del explorador de Campaign.

1. Cree un esquema de datos como **[!UICONTROL Extension of a schema]**.

   ![](assets/privacy-data-restriction.png)

1. Choose **[!UICONTROL External Account]** (extAccount).

1. En la última pantalla del asistente, edite el nuevo &quot;srcSchema&quot; para restringir el acceso a todos los campos de contraseña:

   Puede reemplazar el elemento principal (`<element name="extAccount" ... >`) de:

   ```sql
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

   ```sql
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
   >Puede reemplazar `$(loginId) = 0 or $(login) = 'admin'` con `hasNamedRight('admin')` para permitir que todos los usuarios con derechos de administrador vean estas contraseñas.

## Páginas de Protect con PI

Recomendamos encarecidamente a los clientes locales que protejan las páginas que puedan contener información personal (API), como páginas espejo, aplicaciones web, etc.

El objetivo de este procedimiento es evitar que estas páginas se indexen, evitando así un posible riesgo de seguridad. A continuación se muestran algunos artículos útiles:

* [https://developers.google.com/search/reference/robots_txt](https://developers.google.com/search/reference/robots_txt)
* [https://developers.google.com/search/reference/robots_meta_tag](https://developers.google.com/search/reference/robots_meta_tag)

Para proteger sus páginas, siga estos pasos:

1. Agregue un `robots.txt` en la raíz del servidor web (Apache o IIS). Aquí está el contenido del archivo:

   ```sql
   # Make changes for all web spiders
   User-agent:
   *Disallow: /
   ```

   Para IIS, consulte [esta página](https://docs.microsoft.com/en-us/iis/extensions/iis-search-engine-optimization-toolkit/managing-robotstxt-and-sitemap-files).

   Para Apache, puede colocar el archivo en **/var/www/robots.txt** (Debian).

1. A veces, añadir un **robots.txt** no es suficiente en términos de seguridad. Por ejemplo, si otro sitio web contiene un vínculo a la página, puede aparecer en un resultado de búsqueda.

   Además del **robots.txt** , se recomienda añadir un **X-Robots-Tag** encabezado. Puede hacerlo en Apache o IIS y en la **serverConf.xml** archivo de configuración.

   Para obtener más información, consulte [este artículo](https://developers.google.com/search/reference/robots_meta_tag).


## Solicitudes de privacidad

Consulte [esta página](../../platform/using/privacy-management.md) para obtener información general sobre qué es la administración de privacidad y los pasos de implementación en Adobe Campaign. También encontrará recomendaciones e información general del proceso y de los perfiles del usuario.
