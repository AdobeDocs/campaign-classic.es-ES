---
product: campaign
title: Administración de archivos y recursos
feature: Installation, Application Settings
description: Obtenga información sobre cómo configurar la administración de archivos y recursos en Campaign
badge-v7-only: label="v7" type="Informative" tooltip="Se aplica solo a Campaign Classic v7"
badge-v7-prem: label="On-Premise e híbrido" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=es" tooltip="Se aplica solo a implementaciones On-premise e híbridas"
audience: installation
content-type: reference
topic-tags: initial-configuration
exl-id: 236afdfe-fb23-4ebb-b000-76e14bf01d9e
source-git-commit: a94c361c5bdd9d61ae9232224af910a78245a889
workflow-type: tm+mt
source-wordcount: '659'
ht-degree: 3%

---

# Administración de archivos y recursos{#file-and-resmanagement}



## Limitar formato de archivo de carga {#limiting-uploadable-files}

Utilice el **uploadWhiteList** para restringir los tipos de archivo disponibles para cargar en el servidor de Adobe Campaign.

Este atributo está disponible en **dataStore** elemento de la **serverConf.xml** archivo. Todos los parámetros disponibles en **serverConf.xml** se enumeran en esta [sección](../../installation/using/the-server-configuration-file.md).

El valor predeterminado de este atributo es **.+** y permite cargar cualquier tipo de archivo.

Para limitar los posibles formatos, reemplace el valor del atributo por una expresión regular java válida. Puede introducir varios valores separándolos con una coma.

Por ejemplo: **uploadWhiteList=&quot;.&#42;.png,.&#42;.jpg&quot;** le permitirá cargar formatos PNG y de JPG en el servidor. No se aceptan otros formatos.

También puede evitar que se carguen archivos importantes configurando el servidor web. [Más información](web-server-configuration.md)

>[!NOTE]
>
>El **uploadWhiteList** restringe los tipos de archivo disponibles para cargar en el servidor de Adobe Campaign. Sin embargo, cuando el modo de publicación es **Servidor(es) de seguimiento** o **Otro servidor de Adobe Campaign**, el **uploadWhitelist** El atributo también debe actualizarse en esos servidores.

## Configuración de conexión proxy {#proxy-connection-configuration}

Puede conectar el servidor de Campaign a un sistema externo a través de un proxy mediante una **Transferencia de archivos** actividad de flujo de trabajo, por ejemplo. Para lograrlo, debe configurar la variable **proxyConfig** de la sección **serverConf.xml** mediante un comando específico. Todos los parámetros disponibles en **serverConf.xml** se enumeran en esta [sección](../../installation/using/the-server-configuration-file.md).

Las siguientes conexiones proxy son posibles: HTTP, HTTPS, FTP y SFTP. Tenga en cuenta que a partir de la versión 20.2 de Campaign, los parámetros de protocolo HTTP y HTTPS son **ya no está disponible**. Estos parámetros aún se mencionan a continuación, ya que siguen estando disponibles en versiones anteriores, incluida la 9032.

>[!CAUTION]
>
>Solo se admite el modo de autenticación básico. No se admite la autenticación NTLM.
>
>No se admiten proxies SOCKS.
>

Puede utilizar el siguiente comando:

```
nlserver config -setproxy:[protocol]/[serverIP]:[port]/[login][:‘https’|'http’]
```

los parámetros de protocolo pueden ser &quot;http&quot;, &quot;https&quot; o &quot;ftp&quot;.

Si configura FTP en el mismo puerto que el tráfico HTTP/HTTPS, puede utilizar lo siguiente:

```
nlserver config -setproxy:http/198.51.100.0:8080/user
```

Las opciones &quot;http&quot; y &quot;https&quot; solo se utilizan cuando el parámetro protocol es &quot;ftp&quot; e indican si el túnel en el puerto especificado se realizará a través de HTTPS o de HTTP.

Si utiliza puertos diferentes para el tráfico FTP/SFTP y HTTP/HTTPS a través del servidor proxy, debe establecer el parámetro de protocolo ‘ftp’.


Por ejemplo:

```
nlserver config -setproxy:ftp/198.51.100.0:8080/user:’http’
```

A continuación, introduzca la contraseña.

Las conexiones HTTP se definen en el parámetro proxyHTTP:

```
<proxyConfig enabled=“1” override=“localhost*” useSingleProxy=“0”>
<proxyHTTP address=“198.51.100.0" login=“user” password=“*******” port=“8080”/>
</proxyConfig>
```

Las conexiones HTTPS se definen en el parámetro proxyHTTPS:

```
<proxyConfig enabled=“1" override=“localhost*” useSingleProxy=“0">
<proxyHTTPS address=“198.51.100.0” login=“user” password=“******” port=“8080"/>
</proxyConfig>
```

Las conexiones FTP/FTPS se definen en el parámetro proxyFTP:

```
<proxyConfig enabled=“1" override=“localhost*” useSingleProxy=“0">
<proxyFTP address=“198.51.100.0” login=“user” password=“******” port=“5555" https=”true”/>
</proxyConfig>
```

Si utiliza el mismo proxy para varios tipos de conexión, solo el proxy HTTP se definirá con useSingleProxy establecido en &quot;1&quot; o &quot;true&quot;.

Si tiene conexiones internas que no deben pasar por el proxy, agréguelas en el parámetro override.

Si desea deshabilitar temporalmente la conexión proxy, establezca el parámetro enabled en &quot;false&quot; o &quot;0&quot;.

Si necesita utilizar el conector HTTP/2 de iOS a través de un proxy, se admiten los siguientes modos de proxy HTTP:

* HTTP sin autenticación
* Autenticación básica HTTP

Para activar el modo proxy, se debe realizar el siguiente cambio en la `serverconf.xml` archivo:

```
<nmac useHTTPProxy="true">
```

Para obtener más información sobre este conector HTTP/2 de iOS, consulte [página](../../delivery/using/about-mobile-app-channel.md).

## Administrar recursos públicos {#managing-public-resources}

Para que estén disponibles públicamente, las imágenes utilizadas en los correos electrónicos y recursos públicos vinculados a las campañas deben estar presentes en un servidor accesible de forma externa. Luego pueden estar disponibles para destinatarios u operadores externos. [Más información](../../installation/using/deploying-an-instance.md#managing-public-resources).

Los recursos públicos se almacenan en **/var/res/instance** del directorio de instalación de Adobe Campaign.

La URL coincidente es: **http://server/res/instance** donde **instancia** es el nombre de la instancia de seguimiento.

Puede especificar otro directorio agregando un nodo a **conf-`<instance>`.xml** para configurar el almacenamiento en el servidor. Esto significa añadir las siguientes líneas:

```
<serverconf>
  <shared>
    <dataStore hosts="media*" lang="fra">
      <virtualDir name="images" path="/var/www/images"/>
     <virtualDir name="publicFileRes" path="$(XTK_INSTALL_DIR)/var/res/$(INSTANCE_NAME)/"/>
    </dataStore>
  </shared>
</serverconf>
```

En este caso, la nueva URL para los recursos públicos que se proporciona en la parte superior de la ventana del asistente de implementación debe apuntar a esta carpeta.
