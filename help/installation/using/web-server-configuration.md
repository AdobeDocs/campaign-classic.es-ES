---
product: campaign
title: Configuración del servidor web
description: Obtenga más información sobre las prácticas recomendadas principales de configuración del servidor web.
audience: installation
content-type: reference
topic-tags: prerequisites-and-recommendations-
exl-id: fc0d3f16-5f62-473d-a1de-aab574eff734
source-git-commit: 32f55d02920b0104198f809b1be0a91306a4d9e4
workflow-type: tm+mt
source-wordcount: '322'
ht-degree: 1%

---

# Configuración del servidor web {#web-server-configuration}

![](../../assets/v7-only.svg)

A continuación encontrará algunas de las principales prácticas recomendadas relacionadas con la configuración del servidor web (Apache/IIS).

* Cambiar las páginas de error predeterminadas.

* Deshabilite la versión SSL y las cifras anteriores:

   **En Apache**, edite /etc/apache2/mods-available/ssl.conf. Este es un ejemplo.

   * SSLProcol todo -SSLv2 -SSLv3 -TLSv1
   * SSLCipherSuite HIGH:MEDIUM:!aNULL:!MD5:!SSLv3:!SSLv2:!TLSv1

   **En IIS** (consulte la [documentación](https://support.microsoft.com/en-us/kb/245030)), realice la configuración siguiente:

   * Añadir subclave del Registro en HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\SecurityProviders\SCHANNEL
   * Para permitir que el sistema utilice los protocolos que no se negocian de forma predeterminada (como TLS 1.2), cambie los datos del valor DWORD del valor DisabledByDefault a 0x0 en las siguientes claves de registro en la sección **Protocolos** clave:

      CANAL\Protocolos\TLS 1.2\Cliente

      CANAL\Protocolos\TLS 1.2\Servidor
   **Deshabilitar SSL x.0**

   SCHANNEL\Protocolos\SSL 3.0\Cliente: DisabledByDefault: Valor DWORD (32 bits) a 1

   SCHANNEL\Protocolos\SSL 3.0\Servidor: Habilitado: Valor DWORD (32 bits) a 0

* Elimine el **TRACE** método:

   **En Apache**, edite en /etc/apache2/conf.d/security: TraceEnable **Off**

   **En IIS** (consulte la [documentación](https://www.iis.net/configreference/system.webserver/security/requestfiltering/verbs)), realice la configuración siguiente:

   * Asegúrese de que **Filtrado de solicitudes** está instalado el servicio de rol o la función .
   * En el **Filtrado de solicitudes** , haga clic en la ficha Verbos HTTP y, a continuación, haga clic en Denegar verbo. En el panel Acciones, introduzca TRACE en el cuadro de diálogo abierto.

* Elimine el banner:

   **En Apache**, edite /etc/apache2/conf.d/security:

   * ServerSignature **Off**
   * ServerTokens **Prod**

   **En IIS**, realice la configuración siguiente:

   * Instalar **URLScan**.
   * Edite el **Urlscan.ini** archivo que se va a tener **RemoveServerHeader=1**


* Limite el tamaño de la consulta para evitar que se carguen archivos importantes:

   **En Apache**, añada la variable **LimitRequestBody** directiva (tamaño en bytes) en el directorio /.

   ```
   <Directory />
       Options FollowSymLinks
       AllowOverride None
       LimitRequestBody 10485760
   </Directory>
   ```

   **En IIS** (consulte la [documentación](https://www.iis.net/configreference/system.webserver/security/requestfiltering/requestlimits)), establezca la variable **maxAllowedContentLength** (longitud máxima del contenido permitida) en las opciones de filtrado de contenido.

Temas relacionados:

* [Información general sobre el cumplimiento de Adobe Marketing Cloud](https://experienceleague.adobe.com/docs/core-services/assets/Adobe-Marketing-Cloud-Privacy-and-Security-Overview.pdf) (PDF)
* [Información general sobre la seguridad de Adobe Campaign](https://wwwimages.adobe.com/content/dam/acom/en/marketing-cloud/campaign/pdfs/54658.en.campaign.wp.adb-security.pdf) (PDF)
