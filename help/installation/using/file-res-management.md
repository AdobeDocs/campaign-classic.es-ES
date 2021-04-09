---
solution: Campaign Classic
product: campaign
title: Administración de archivos y recursos
description: Obtenga información sobre cómo configurar la administración de archivos y recursos en Campaign
audience: installation
content-type: reference
topic-tags: initial-configuration
exl-id: 236afdfe-fb23-4ebb-b000-76e14bf01d9e
translation-type: tm+mt
source-git-commit: 401e1be234d52f04cbdf8dfa97f51ac227836cd5
workflow-type: tm+mt
source-wordcount: '561'
ht-degree: 1%

---

# Administración de archivos y recursos{#file-and-resmanagement}

## Limitar el formato del archivo de carga {#limiting-uploadable-files}

Utilice el atributo **uploadWhiteList** para restringir los tipos de archivo disponibles para cargar en el servidor de Adobe Campaign.

Este atributo está disponible dentro del elemento **dataStore** del archivo **serverConf.xml**. Todos los parámetros disponibles en **serverConf.xml** se enumeran en esta [sección](../../installation/using/the-server-configuration-file.md).

El valor predeterminado de este atributo es **.+** y permite cargar cualquier tipo de archivo.

Para limitar los posibles formatos, reemplace el valor del atributo por una expresión regular de java válida. Puede introducir varios valores separándolos por una coma.

Por ejemplo: **uploadWhiteList=&quot;.*.png,*.jpg&quot;** le permitirá cargar formatos PNG y JPG en el servidor. No se aceptarán otros formatos.

>[!NOTE]
>
>En Internet Explorer, la ruta completa del archivo debe verificarse mediante la expresión regular.

También puede evitar que se carguen archivos importantes configurando el servidor web. [Obtenga más información](web-server-configuration.md)

## Configuración de conexión proxy {#proxy-connection-configuration}

Puede conectar el servidor de Campaign a un sistema externo a través de un proxy mediante la actividad de flujo de trabajo **File Transfer**, por ejemplo. Para conseguirlo, debe configurar la sección **proxyConfig** del archivo **serverConf.xml** mediante un comando específico. Todos los parámetros disponibles en **serverConf.xml** se enumeran en esta [sección](../../installation/using/the-server-configuration-file.md).

Las siguientes conexiones proxy son posibles: HTTP, HTTPS, FTP, SFTP. Tenga en cuenta que a partir de la versión 20.2 de Campaign, los parámetros de protocolo HTTP y HTTPS **ya no están disponibles**. Estos parámetros aún se mencionan a continuación, ya que siguen estando disponibles en versiones anteriores, incluido 9032.

>[!CAUTION]
>
>Solo se admite el modo de autenticación básico. No se admite la autenticación NTLM.
>
>Los proxies SOCKS no son compatibles.


Puede utilizar el siguiente comando:

```
nlserver config -setproxy:[protocol]/[serverIP]:[port]/[login][:‘https’|'http’]
```

los parámetros de protocolo pueden ser &quot;http&quot;, &quot;https&quot; o &quot;ftp&quot;.

Si configura FTP en el mismo puerto que el tráfico HTTP/HTTPS, puede utilizar lo siguiente:

```
nlserver config -setproxy:http/198.51.100.0:8080/user
```

Las opciones &quot;http&quot; y &quot;https&quot; solo se utilizan cuando el parámetro de protocolo es &quot;ftp&quot; e indican si la tunelización en el puerto especificado se realizará a través de HTTPS o HTTP.

Si utiliza puertos diferentes para el tráfico FTP/SFTP y HTTP/HTTPS a través del servidor proxy, debe establecer el parámetro de protocolo &quot;ftp&quot;.


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

Las conexiones FTP/FTPS se definen en el parámetro proxyFTP :

```
<proxyConfig enabled=“1" override=“localhost*” useSingleProxy=“0">
<proxyFTP address=“198.51.100.0” login=“user” password=“******” port=“5555" https=”true”/>
</proxyConfig>
```

Si utiliza el mismo proxy para varios tipos de conexión, solo el proxyHTTP se definirá con useSingleProxy establecido en &quot;1&quot; o &quot;true&quot;.

Si tiene conexiones internas que deben pasar por el proxy, agréguelas en el parámetro override.

Si desea deshabilitar temporalmente la conexión proxy, establezca el parámetro habilitado en &quot;false&quot; o &quot;0&quot;.

## Administrar recursos públicos {#managing-public-resources}

Para que estén disponibles para el público, las imágenes utilizadas en los correos electrónicos y recursos públicos vinculados a campañas deben estar presentes en un servidor accesible de forma externa. A continuación, pueden estar disponibles para destinatarios u operadores externos. [Más información](../../installation/using/deploying-an-instance.md#managing-public-resources).

Los recursos públicos se almacenan en el directorio **/var/res/instance** del directorio de instalación de Adobe Campaign.

La dirección URL coincidente es: **http://server/res/instance** donde **instance** es el nombre de la instancia de seguimiento.

Puede especificar otro directorio añadiendo un nodo al archivo **conf-`<instance>`.xml** para configurar el almacenamiento en el servidor. Esto significa añadir las siguientes líneas:

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

En este caso, la nueva URL para los recursos públicos que se proporciona en la parte superior de la ventana del asistente de implementación debe señalar a esta carpeta.
