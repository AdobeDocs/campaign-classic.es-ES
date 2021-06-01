---
product: campaign
title: Arquitectura general
description: Arquitectura general
audience: production
content-type: reference
topic-tags: introduction
exl-id: 3bfb5448-6996-4080-bf9a-434f1207637e
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
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

1. Tráfico de protocolo HTTP al servidor de Adobe Campaign a través de Internet,
1. Tráfico de protocolo SMTP desde y hacia el servidor de Adobe Campaign a través de Internet.

## Arquitectura distribuida {#distributed-architecture}

Adobe Campaign se compone de varios módulos que se pueden desglosar en varios equipos. Este modo operativo tiene varias ventajas:

* equilibrio de carga,
* configuración de la redundancia de módulos,
* construcción de una arquitectura desglosada por varios proveedores de servicios (segmentación de los servicios prestados).

![](assets/architecturerepartie.png)

La distribución de módulos en varias máquinas proporciona buena flexibilidad de uso y una mayor adaptabilidad.

>[!NOTE]
>
>Para obtener más información sobre las distintas arquitecturas, consulte [esta sección](../../installation/using/general-architecture.md).

## Lista de puertos abiertos {#list-of-open-ports}

| Número de puerto | Módulo o aplicación de Adobe Campaign correspondiente | Configurable |
|---|---|---|
| 443/tcp o 80/tcp | Servidores web (Apache/IIS) | SÍ |
| 6666/udp (local) | Adobe Campaign: Syslogd | SÍ |
| 8005/tcp (local) | Adobe Campaign: módulo web | SÍ |
| 8080/tcp | Adobe Campaign: módulo web (tomcat) | SÍ |
| 7777 | Servidor de estadísticas (servidor de estadísticas) | SÍ |
