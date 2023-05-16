---
product: campaign
title: Recopilación de todas las visitas
description: Recopilación de todas las visitas
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
exl-id: cc554d0d-bbab-4f72-b870-5fef5a2fda9d
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: tm+mt
source-wordcount: '297'
ht-degree: 3%

---

# Recopilación de todas las visitas{#collecting-all-visits}

El módulo de seguimiento web proporcionado por Adobe Campaign permite recopilar las visitas a determinadas páginas del sitio realizadas por un destinatario en el contexto del seguimiento del sitio después de un clic en un mensaje.

Sin embargo, puede configurar la plataforma de modo que recopile todas las visitas a páginas con una etiqueta de seguimiento web por parte de un usuario conocido por la plataforma.

Un usuario conocido por la plataforma es un destinatario que ya ha sido identificado por una entrega y que ha hecho clic en un mensaje recibido al menos una vez. Se utiliza una cookie permanente para identificar a este destinatario.

>[!IMPORTANT]
>
>La plataforma Adobe Campaign no está pensada para utilizarse como herramienta de seguimiento de sitios web más allá del contexto de visitar el sitio después de hacer clic en un mensaje. Cuando esta opción está habilitada, puede causar un uso muy alto de los recursos en los equipos que alojan sus servidores (redirección, aplicación y base de datos). Se le recomienda asegurarse de que su arquitectura de hardware admita esta carga y evitar colocar etiquetas de seguimiento web en las páginas más visitadas, como la página principal.

## Configuración del servidor {#server-configuration}

Los servidores se configuran sobrecargando ciertos elementos de la variable **serverConf.xml** archivo. Estos archivos se guardan en la variable **conf** subdirectorio del directorio de instalación de Adobe Campaign.

### Servidor de redirección {#redirection-server}

Para el servidor de redirección, establezca la variable **trackWebVisitors** del **redirección** elemento a **true**.

```
<redirection P3PCompactPolicy="CAO DSP COR CURa DEVa TAIa OUR BUS IND UNI COM NAV"
databaseId="" defLogCount="30" expirationURL="" maxJobsInCache="100"
startRedirection="true" startRedirectionInModule="true" trackWebVisitors="true"
trackingPassword=""
```

## Configuración de una campaña coincidente predeterminada {#configuring-a-default-matching-campaign}

Para ver la información de seguimiento a través de la consola del cliente, debe:

* Cree un **envío ficticio** (la asignación de entrega debe ser idéntica a la asignación del esquema de destino),
* Introduzca la variable **nombre interno** de esta entrega en la variable **NmsTracking_WebTrackingDelivery** .

Toda la información de seguimiento del sitio que no sea directamente posterior a un clic en un correo electrónico se puede ver en la entrega ficticia creada.
