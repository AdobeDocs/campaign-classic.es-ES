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

Este diagrama muestra que el único tráfico que interviene en el contexto de una arquitectura mínima es:

1. tráfico de protocolo HTTP al servidor de campaña de Adobe a través de Internet,
1. Tráfico de protocolo SMTP desde y hacia el servidor de campaña de Adobe a través de Internet.

## Arquitectura distribuida {#distributed-architecture}

Adobe Campaign se compone de varios módulos que se pueden desglosar en varias máquinas. Este modo operativo tiene varias ventajas:

* balanceo de carga,
* la creación de redundancia de módulos,
* construcción de una arquitectura dividida en varios proveedores de servicios (segmentación de los servicios prestados).

![](assets/architecturerepartie.png)

La distribución de módulos en varias máquinas proporciona una gran flexibilidad de uso y una mayor adaptabilidad.

>[!NOTE]
>
>For more on the various architectures, refer to [this section](../../installation/using/general-architecture.md).

## Lista de puertos abiertos {#list-of-open-ports}

| Número de puerto | Módulo o aplicación de Adobe Campaign concernido | Configurable |
|---|---|---|
| 443/tcp u 80/tcp | Servidores Web (Apache/IIS) | SÍ |
| 6666/udp (local) | Campaña de Adobe: Syslogd | SÍ |
| 8005/tcp (local) | Campaña de Adobe: módulo web | SÍ |
| 8080/tcp | Campaña de Adobe: módulo web (tomcat) | SÍ |
| 7777 | Servidor de estadísticas (servidor de estado) | SÍ |

