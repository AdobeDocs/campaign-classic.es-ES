---
title: Recopilación de todas las visitas
seo-title: Recopilación de todas las visitas
description: Recopilación de todas las visitas
seo-description: null
page-status-flag: never-activated
uuid: c2869b3d-33bb-4a22-a8e6-ac037f0665d9
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: configuration
content-type: reference
topic-tags: setting-up-web-tracking
discoiquuid: 7f841368-3867-4d6e-9720-c038d9bea0ce
translation-type: tm+mt
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: tm+mt
source-wordcount: '300'
ht-degree: 4%

---


# Recopilación de todas las visitas{#collecting-all-visits}

El módulo de seguimiento Web proporcionado por Adobe Campaign permite recopilar las visitas a determinadas páginas del sitio realizadas por un destinatario en el contexto del seguimiento del sitio después de un clic en un mensaje.

Sin embargo, puede configurar la plataforma de modo que recopile todas las visitas a páginas con una etiqueta de seguimiento web realizadas por un usuario conocido por la misma.

Un usuario conocido por la plataforma es un destinatario que ya ha sido objetivo de un envío y que ha hecho clic en un mensaje recibido al menos una vez. Se utiliza una cookie permanente para identificar este destinatario.

>[!IMPORTANT]
>
>La plataforma de Adobe Campaign no está pensada para utilizarse como herramienta de seguimiento de sitios web más allá del contexto de visitar el sitio tras un clic en un mensaje. Cuando esta opción está habilitada, puede causar un uso muy alto de los recursos en los equipos que hospedan los servidores (redirección, aplicación y base de datos). Se recomienda asegurarse de que la arquitectura de hardware admita esta carga y evitar colocar etiquetas de seguimiento web en las páginas más visitadas, como la página de inicio.

## Configuración del servidor {#server-configuration}

Los servidores se configuran mediante la sobrecarga de ciertos elementos del archivo **serverConf.xml** . Estos archivos se guardan en el subdirectorio **conf** del directorio de instalación de Adobe Campaign.

### Servidor de redirección {#redirection-server}

Para el servidor de redirección, establezca el atributo **trackWebVisitors** del elemento de **redirección** en **true**.

```
<redirection P3PCompactPolicy="CAO DSP COR CURa DEVa TAIa OUR BUS IND UNI COM NAV"
databaseId="" defLogCount="30" expirationURL="" maxJobsInCache="100"
startRedirection="true" startRedirectionInModule="true" trackWebVisitors="true"
trackingPassword=""
```

## Configuración de una campaña coincidente predeterminada {#configuring-a-default-matching-campaign}

Para obtener información de seguimiento de vista a través de la consola de cliente, debe:

* Crear un envío **** ficticio (la asignación de envíos debe ser idéntica a la asignación del esquema de destinatario),
* Introduzca el nombre **** interno de este envío en la opción **NmsTracking_WebTrackingDelivery** .

Toda la información de seguimiento del sitio que no sea directamente posterior a un clic en un mensaje de correo electrónico puede verse en el envío ficticio creado.
