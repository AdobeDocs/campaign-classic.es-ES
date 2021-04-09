---
solution: Campaign Classic
product: campaign
title: Configuración de Campaign Tomcat
description: Configuración de Campaign Tomcat
audience: installation
content-type: reference
topic-tags: initial-configuration
exl-id: a2126458-2ae5-47c6-ad13-925f0e067ecf,b4a422b4-4b8b-4883-8d74-0dccda4a5ef3
translation-type: tm+mt
source-git-commit: 5d8d9e6ba41f94179bbf5f6d41f86267381b9b93
workflow-type: tm+mt
source-wordcount: '214'
ht-degree: 0%

---

# Configurar Apache Tomcat {#configuring-tomcat}

Adobe Campaign utiliza un **servlet web integrado llamado Apache Tomcat** para procesar solicitudes HTTP/HTTPS entre la aplicación y cualquier interfaz externa (incluida la consola del cliente, los vínculos de URL rastreados, las llamadas SOAP y otros). A menudo hay un servidor web externo (normalmente IIS o Apache) delante de esto para cualquier instancia de Adobe Campaign externa.

Obtenga más información sobre Tomcat en Campaign y cómo localizar la versión de Tomcat en [esta página](../../production/using/locate-tomcat-version.md).

>[!NOTE]
>
>Este procedimiento está restringido a **implementaciones locales**.


## Puerto predeterminado para Apache Tomcat {#default-port-for-tomcat}

Cuando el puerto de escucha 8080 del servidor Tomcat ya está ocupado con otra aplicación necesaria para la configuración, debe reemplazar el puerto 8080 por uno gratuito (8090 por ejemplo). Para cambiarlo, edite el archivo **server.xml** guardado en el directorio **/tomcat-8/conf** de la carpeta de instalación de Adobe Campaign.

A continuación, modifique el puerto de las páginas de transmisión de JSP. Para ello, cambie el archivo **serverConf.xml** guardado en el directorio **/conf** del directorio de instalación de Adobe Campaign.

```
<serverConf>
   ...
   <web controlPort="8005" httpPort="8090"...
   <url ... targetUrl="http://localhost:8090"...
```

## Asignación de una carpeta en Apache Tomcat {#mapping-a-folder-in-tomcat}

Para definir la configuración específica del cliente, puede crear un archivo **user_contexts.xml** en la carpeta **/tomcat-8/conf**, que también contiene el archivo **contexts.xml**.

Este archivo contiene el siguiente tipo de información:

```
 <Context path='/foo' docBase='../customers/foo'   crossContext='true' debug='0' reloadable='true' trusted='false'/>
```

Si es necesario, esta operación se puede reproducir en el lado del servidor.
