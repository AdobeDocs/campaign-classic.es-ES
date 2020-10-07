---
title: Arquitectura general
seo-title: Arquitectura general
description: Arquitectura general
seo-description: null
page-status-flag: never-activated
uuid: a565a10c-cbef-455a-aa1d-9be9cd207c7a
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: production
content-type: reference
topic-tags: introduction
discoiquuid: f4879774-afe5-4556-ab60-9297cabbca2c
translation-type: tm+mt
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: tm+mt
source-wordcount: '183'
ht-degree: 6%

---


# Arquitectura general{#general-architecture}

## Arquitectura mínima {#minimum-architecture}

En una configuración mínima, Adobe Campaign funciona con:

* el servidor de aplicaciones de Adobe Campaign,
* la base de datos.

   ![](assets/formation_exploitation.png)

Este diagrama muestra que el único tráfico involucrado en el contexto de una arquitectura mínima es:

1. tráfico de protocolo HTTP al servidor de Adobe Campaign a través de Internet,
1. Tráfico del protocolo SMTP desde y hacia el servidor de Adobe Campaign a través de Internet.

## Arquitectura distribuida {#distributed-architecture}

Adobe Campaign se compone de varios módulos que pueden desglosarse en varios equipos. Este modo operativo tiene varias ventajas:

* equilibrio de carga,
* la configuración de la redundancia de módulos,
* construcción de una arquitectura dividida en varios proveedores de servicio (segmentación de los servicios prestados).

![](assets/architecturerepartie.png)

La distribución de módulos en varias máquinas ofrece buena flexibilidad de uso y una mayor adaptabilidad.

>[!NOTE]
>
>For more on the various architectures, refer to [this section](../../installation/using/general-architecture.md).

## Lista de puertos abiertos {#list-of-open-ports}

| Número de puerto | Módulo o aplicación de Adobe Campaign concernidos | Configurable |
|---|---|---|
| 443/tcp u 80/tcp | Servidores Web (Apache/IIS) | SÍ |
| 6666/udp (local) | Adobe Campaign: Syslogd | SÍ |
| 8005/tcp (local) | Adobe Campaign: módulo web | SÍ |
| 8080/tcp | Adobe Campaign: módulo Web (tomcat) | SÍ |
| 7777 | Servidor de estadísticas (servidor de estado) | SÍ |

