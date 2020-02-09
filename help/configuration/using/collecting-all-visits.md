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
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 579329d9194115065dff2c192deb0376c75e67bd

---


# Recopilación de todas las visitas{#collecting-all-visits}

El módulo de seguimiento web proporcionado por Adobe Campaign permite recopilar las visitas a determinadas páginas del sitio realizadas por un destinatario en el contexto del seguimiento del sitio tras un clic en un mensaje.

Sin embargo, puede configurar la plataforma de modo que recopile todas las visitas a páginas con una etiqueta de seguimiento web por parte de un usuario conocido por la plataforma.

Un usuario conocido por la plataforma es un destinatario que ya ha sido objetivo de una entrega y que ha hecho clic en un mensaje recibido al menos una vez. Se utiliza una cookie permanente para identificar a este destinatario.

>[!CAUTION]
>
>La plataforma de Adobe Campaign no está pensada para utilizarse como herramienta de seguimiento de sitios web más allá del contexto de visitar el sitio tras un clic en un mensaje. Cuando esta opción está habilitada, puede causar un uso muy alto de los recursos en los equipos que hospedan los servidores (redirección, aplicación y base de datos). Se recomienda asegurarse de que la arquitectura de hardware admita esta carga y evitar colocar etiquetas de seguimiento web en las páginas más visitadas, como la página principal.

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

## Configuración de una campaña de coincidencia predeterminada {#configuring-a-default-matching-campaign}

Para ver la información de seguimiento a través de la consola de cliente, debe:

* Cree una entrega **** ficticia (la asignación de entrega debe ser idéntica a la asignación del esquema de destino),
* Escriba el nombre **** interno de esta entrega en la opción **NmsTracking_WebTrackingDelivery** .

Toda la información de seguimiento del sitio que no sea directamente posterior a un clic en un mensaje de correo electrónico puede verse en el envío ficticio creado.
