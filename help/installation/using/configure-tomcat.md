---
product: campaign
title: Configuración de Campaign Tomcat
description: Configuración de Campaign Tomcat
audience: installation
content-type: reference
topic-tags: initial-configuration
exl-id: a2126458-2ae5-47c6-ad13-925f0e067ecf
source-git-commit: ed9e76495efb0cb49e248a7d38417642c5094a11
workflow-type: tm+mt
source-wordcount: '214'
ht-degree: 0%

---

# Configurar Apache Tomcat {#configuring-tomcat}

![](../../assets/v7-only.svg)

Adobe Campaign utiliza un **servlet web incrustado llamado Apache Tomcat** para procesar solicitudes HTTP/HTTPS entre la aplicación y cualquier interfaz externa (incluida la consola de cliente, los vínculos de URL rastreados, las llamadas SOAP y otros). A menudo hay un servidor web externo (normalmente IIS o Apache) delante de esto para cualquier instancia de Adobe Campaign externa.

Obtenga más información sobre Tomcat en Campaign y cómo localizar la versión de Tomcat en [esta página](../../production/using/locate-tomcat-version.md).

>[!NOTE]
>
>Este procedimiento está restringido a **local** implementaciones.

## Puerto predeterminado para Apache Tomcat {#default-port-for-tomcat}

Cuando el puerto de escucha 8080 del servidor Tomcat ya está ocupado con otra aplicación necesaria para la configuración, debe reemplazar el puerto 8080 por uno gratuito (8090 por ejemplo). Para cambiarlo, edite el **server.xml** archivo guardado en la variable **/tomcat-8/conf** de la carpeta de instalación de Adobe Campaign.

A continuación, modifique el puerto de las páginas de transmisión de JSP. Para ello, cambie la **serverConf.xml** archivo guardado en la variable **/conf** del directorio de instalación de Adobe Campaign.

```
<serverConf>
   ...
   <web controlPort="8005" httpPort="8090"...
   <url ... targetUrl="http://localhost:8090"...
```

## Asignación de una carpeta en Apache Tomcat {#mapping-a-folder-in-tomcat}

Para definir la configuración específica del cliente, puede crear un **user_contexts.xml** en el **/tomcat-8/conf** carpeta, que también contiene la variable **contexts.xml** archivo.

Este archivo contiene el siguiente tipo de información:

```
 <Context path='/foo' docBase='../customers/foo'   crossContext='true' debug='0' reloadable='true' trusted='false'/>
```

Si es necesario, esta operación se puede reproducir en el lado del servidor.
