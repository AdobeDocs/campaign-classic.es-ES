---
product: campaign
title: Configuración de Campaign Tomcat
description: Configuración de Campaign Tomcat
feature: Installation, Instance Settings
badge-v7-only: label="v7" type="Informative" tooltip="Se aplica solo a Campaign Classic v7"
badge-v7-prem: label="On-Premise e híbrido" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=es" tooltip="Se aplica solo a implementaciones On-premise e híbridas"
audience: installation
content-type: reference
topic-tags: initial-configuration
exl-id: a2126458-2ae5-47c6-ad13-925f0e067ecf
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: tm+mt
source-wordcount: '293'
ht-degree: 5%

---

# Configuración de Apache Tomcat {#configuring-tomcat}



Adobe Campaign utiliza un **servlet web integrado denominado Apache Tomcat** para procesar solicitudes HTTP/HTTPS entre la aplicación y cualquier interfaz externa (incluida la consola de cliente, vínculos de URL rastreados, llamadas SOAP y otras). A menudo hay un servidor web externo (generalmente IIS o Apache) delante de esto para cualquier instancia de Adobe Campaign externa.

Obtenga más información sobre Tomcat en Campaign y cómo localizar su versión de Tomcat en [esta página](../../production/using/locate-tomcat-version.md).

>[!NOTE]
>
>Este procedimiento está restringido a **on-premise** implementaciones.
>

## Puerto predeterminado para Apache Tomcat {#default-port-for-tomcat}

Cuando el puerto de escucha 8080 del servidor Tomcat ya está ocupado con otra aplicación requerida para su configuración, debe reemplazar el puerto 8080 por uno libre (8090 por ejemplo). Para cambiarlo, edite el **server.xml** archivo guardado en **/tomcat-8/conf** de la carpeta de instalación de Adobe Campaign.

A continuación, modifique el puerto de las páginas de retransmisión JSP. Para ello, cambie el **serverConf.xml** archivo guardado en **/conf** del directorio de instalación de Adobe Campaign.

```
<serverConf>
   ...
   <web controlPort="8005" httpPort="8090"...
   <url ... targetUrl="http://localhost:8090"...
```

## Asignación de una carpeta en Apache Tomcat {#mapping-a-folder-in-tomcat}

Para definir la configuración específica del cliente, puede crear un **user_contexts.xml** archivo en el **/tomcat-8/conf** , que también contiene la carpeta **contexts.xml** archivo.

Este archivo contendrá el siguiente tipo de información:

```
 <Context path='/foo' docBase='../customers/foo'   crossContext='true' debug='0' reloadable='true' trusted='false'/>
```

Si es necesario, esta operación se puede reproducir en el servidor.

## Ocultar el informe de errores de Tomcat {#hide-tomcat-error-report}

Por motivos de seguridad, le recomendamos encarecidamente que oculte el informe de errores de Tomcat. Aquí están los pasos.

1. Abra el **server.xml** archivo ubicado en el **/tomcat-8/conf** directorio de la carpeta de instalación de Adobe Campaign:  `/usr/local/neolane/nl6/tomcat-8/conf`
1. Agregue el siguiente elemento en la parte inferior después de todos los elementos de contexto existentes:

   ```
   <Valve className="org.apache.catalina.valves.ErrorReportValve" showReport="false" showServerInfo="false"/>
   ```

1. Reinicie los servidores web nlserver y Apache.
