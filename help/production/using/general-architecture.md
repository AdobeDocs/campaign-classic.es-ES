---
solution: Campaign Classic
product: campaign
title: Arquitectura general
description: Arquitectura general
audience: production
content-type: reference
topic-tags: introduction
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '181'
ht-degree: 4%

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
>Para obtener más información sobre las distintas arquitecturas, consulte [esta sección](../../installation/using/general-architecture.md).

## Lista de puertos abiertos {#list-of-open-ports}

| Número de puerto | Módulo o aplicación de Adobe Campaign concernidos | Configurable |
|---|---|---|
| 443/tcp u 80/tcp | Servidores Web (Apache/IIS) | SÍ |
| 6666/udp (local) | Adobe Campaign: Syslogd | SÍ |
| 8005/tcp (local) | Adobe Campaign: módulo web | SÍ |
| 8080/tcp | Adobe Campaign: módulo Web (tomcat) | SÍ |
| 7777 | Servidor de estadísticas (servidor de estado) | SÍ |

