---
product: campaign
title: Configuración del servidor web
description: Obtenga más información sobre las prácticas recomendadas principales de configuración de servidores web
feature: Installation, Instance Settings
audience: installation
content-type: reference
topic-tags: prerequisites-and-recommendations-
exl-id: fc0d3f16-5f62-473d-a1de-aab574eff734
source-git-commit: dba90a154e08400ae6ab6478623a50d48d72207c
workflow-type: tm+mt
source-wordcount: '285'
ht-degree: 2%

---

# Configuración del servidor web {#web-server-configuration}



A continuación, encontrará algunas de las prácticas recomendadas principales relacionadas con la configuración de servidores web (Apache/IIS).

* Cambiar las páginas de error predeterminadas.

* Deshabilite la versión y las cifras SSL antiguas:

  **En Apache**, edite /etc/apache2/mods-available/ssl.conf. Este es un ejemplo.

   * `SSLProtocol all -SSLv2 -SSLv3 -TLSv1`
   * `SSLCipherSuite HIGH:MEDIUM:!aNULL:!MD5:!SSLv3:!SSLv2:!TLSv1`

  **En IIS** (consulte la [documentación](https://support.microsoft.com/en-us/kb/245030)), realice la siguiente configuración:

   * Agregar una subclave del Registro en HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\SecurityProviders\SCHANNEL
   * Para permitir que el sistema utilice los protocolos que no se negociarán de forma predeterminada (como TLS 1.2), cambie los datos del valor DWORD del valor DisabledByDefault a 0x0 en las siguientes claves del Registro bajo la clave **Protocolos**:

     SCHANNEL\Protocols\TLS 1.2\Client

     SCHANNEL\Protocols\TLS 1.2\Server

  **Deshabilitar SSL x.0**

  SCHANNEL\Protocols\SSL 3.0\Client: DisabledByDefault: DWORD (32 bits) Valor a 1

  SCHANNEL\Protocols\SSL 3.0\Server: Enabled: DWORD (32 bits) Value to 0

* Quitar el método **TRACE**:

  **En Apache**, editar en /etc/apache2/conf.d/security: TraceEnable **Desactivado**

  **En IIS** (consulte la [documentación](https://www.iis.net/configreference/system.webserver/security/requestfiltering/verbs)), realice la siguiente configuración:

   * Asegúrese de que la característica o el servicio de rol **Filtrado de solicitudes** esté instalado.
   * En el panel **Filtrado de solicitudes**, haga clic en la ficha Verbos HTTP y, a continuación, haga clic en Denegar verbo. En el panel Acciones, introduzca TRACE en el cuadro de diálogo abierto.

* Quitar el titular:

  **En Apache**, editar /etc/apache2/conf.d/security:

   * FirmaServidor **Desactivada**
   * ServerTokens **Prod**

  **En IIS**, realice la siguiente configuración:

   * Instalar **URL que pueden**.
   * Edite el archivo **Urlscan.ini** para que tenga **RemoveServerHeader=1**

* Limite el tamaño de la consulta para evitar que se carguen archivos importantes:

  **En Apache**, agregue la directiva **LimitRequestBody** (tamaño en bytes) en el directorio /.

  ```
  <Directory />
      Options FollowSymLinks
      AllowOverride None
      LimitRequestBody 10485760
  </Directory>
  ```

  **En IIS** (consulte la [documentación](https://www.iis.net/configreference/system.webserver/security/requestfiltering/requestlimits)), establezca **maxAllowedContentLength** (longitud de contenido máxima permitida) en las opciones de filtrado de contenido.

Temas relacionados:

* [Resumen del cumplimiento de Adobe Marketing Cloud](https://experienceleague.adobe.com/es/docs/experience-platform/landing/governance-privacy-security/overview#privacy)
* [Información general sobre la seguridad de Adobe Campaign](https://experienceleague.adobe.com/es/docs/experience-platform/landing/governance-privacy-security/overview#security)
