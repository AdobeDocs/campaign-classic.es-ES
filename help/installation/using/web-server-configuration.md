---
solution: Campaign Classic
product: campaign
title: Configuración del servidor web
description: Obtenga más información sobre las prácticas recomendadas principales de configuración del servidor web.
audience: installation
content-type: reference
topic-tags: prerequisites-and-recommendations-
exl-id: fc0d3f16-5f62-473d-a1de-aab574eff734
translation-type: tm+mt
source-git-commit: b0a1e0596e985998f1a1d02236f9359d0482624f
workflow-type: tm+mt
source-wordcount: '325'
ht-degree: 1%

---

# Configuración del servidor web {#web-server-configuration}

A continuación encontrará algunas de las principales prácticas recomendadas relacionadas con la configuración del servidor web (Apache/IIS).

* Cambiar las páginas de error predeterminadas.

* Deshabilite la versión SSL y las cifras anteriores:

   **En Apache**, edite /etc/apache2/mods-available/ssl.conf. Este es un ejemplo.

   * SSLProcol todo -SSLv2 -SSLv3 -TLSv1
   * SSLCipherSuite HIGH:MEDIUM:!aNULL:!MD5:!SSLv3:!SSLv2:!TLSv1

   **En IIS**  (consulte la  [documentación](https://support.microsoft.com/en-us/kb/245030)), realice la configuración siguiente:

   * Añadir subclave del Registro en HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\SecurityProviders\SCHANNEL
   * Para permitir que el sistema utilice los protocolos que no se negocian de forma predeterminada (como TLS 1.2), cambie los datos del valor DWORD del valor DisabledByDefault a 0x0 en las siguientes claves de registro en la clave **Protocolos** :

      SCHANNEL\Protocols\TLS 1.2\Client

      SCHANNEL\Protocols\TLS 1.2\Server
   **Deshabilitar SSL x.0**

   SCHANNEL\Protocols\SSL 3.0\Client: DisabledByDefault: Valor DWORD (32 bits) a 1

   SCHANNEL\Protocols\SSL 3.0\Server: Habilitado: Valor DWORD (32 bits) a 0

* Elimine el método **TRACE**:

   **En Apache**, edite en /etc/apache2/conf.d/security: TraceEnable  **Off**

   **En IIS**  (consulte la  [documentación](https://www.iis.net/configreference/system.webserver/security/requestfiltering/verbs)), realice la configuración siguiente:

   * Asegúrese de que está instalado el servicio de rol o la función **Filtrado de solicitudes**.
   * En el panel **Solicitar filtrado**, haga clic en la ficha Verbos HTTP y, a continuación, haga clic en Denegar verbo. En el panel Acciones, introduzca TRACE en el cuadro de diálogo abierto.

* Elimine el banner:

   **En Apache**, edite /etc/apache2/conf.d/security:

   * ServerSignature **Desactivado**
   * ServerTokens **Prod**

   **En IIS**, realice la siguiente configuración:

   * Instale **URLScan**.
   * Edite el archivo **Urlscan.ini** para que tenga **RemoveServerHeader=1**


* Limite el tamaño de la consulta para evitar que se carguen archivos importantes:

   **En Apache**, añada la directiva  **** LimitRequestBodyaddress (tamaño en bytes) en el directorio / .

   ```
   <Directory />
       Options FollowSymLinks
       AllowOverride None
       LimitRequestBody 10485760
   </Directory>
   ```

   **En IIS**  (consulte la  [documentación](http://www.iis.net/configreference/system.webserver/security/requestfiltering/requestlimits)), establezca  **maxAllowedContentLength**  (longitud máxima permitida del contenido) en las opciones de filtrado de contenido.

Temas relacionados:

* [Información general sobre el cumplimiento de Adobe Marketing Cloud](https://marketing.adobe.com/resources/help/en_US/xref/Adobe-Marketing-Cloud-Privacy-and-Security-Overview.pdf)  (PDF)
* [Información general sobre la seguridad de Adobe Campaign](https://wwwimages.adobe.com/content/dam/acom/en/marketing-cloud/campaign/pdfs/54658.en.campaign.wp.adb-security.pdf)  (PDF)
