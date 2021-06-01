---
product: campaign
title: Implementación intermediaria
description: Implementación intermediaria
audience: installation
content-type: reference
topic-tags: deployment-types-
exl-id: 8a4d7ef1-de5b-4aee-a527-1b74d987ba61
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: tm+mt
source-wordcount: '351'
ht-degree: 2%

---

# Implementación intermediaria{#mid-sourcing-deployment}

Esta configuración es una solución intermedia óptima entre una configuración alojada (ASP) y la internalización. Los componentes de ejecución orientados al exterior se llevan a cabo en un servidor &quot;intermediario&quot; alojado en Adobe Campaign.

>[!NOTE]
>
>Para configurar este tipo de implementación, debe adquirir la opción adecuada. Compruebe su contrato de licencia.

La comunicación general entre servidores y procesos se realiza según el esquema siguiente:

![](assets/s_ncs_install_midsourcing.png)

* Los módulos de administración de ejecución y devoluciones están desactivados en la instancia.
* La aplicación está configurada para realizar la ejecución de mensajes en un servidor remoto &quot;de origen intermedio&quot; que se gestiona mediante llamadas SOAP (a través de HTTP o HTTPS).

## Funciones {#features}

### Ventajas {#advantages}

* Configuración del servidor simplificada: No es necesario que el cliente configure módulos orientados al exterior (mta y inMail).
* Uso limitado del ancho de banda: Dado que la ejecución la realiza el servidor intermediario, solo se requiere un ancho de banda suficiente para enviar datos de personalización al servidor intermediario.
* La alta disponibilidad ya no es un problema interno: El problema se transfiere al servidor intermediario (redirección, páginas espejo, servidores de ejecución, etc.).
* La base de datos no abandona la empresa: Solo se envían los datos necesarios para ensamblar los mensajes al servidor de mid-sourcing (se puede utilizar HTTPS para esto).
* Este tipo de implementación puede ser una solución para arquitecturas de gran volumen (muchos destinatarios en la base de datos), con un rendimiento de entrega significativo.

### Desventajas {#disadvantages}

* Ligero retraso en la visualización de la información de ejecución de mensajes y en la funcionalidad de informes debido al tiempo que se tarda en obtener información del servidor intermediario.
* Los estudios y los formularios web permanecen en la plataforma del cliente.

### Equipo recomendado {#recommended-equipment}

* Servidor de aplicaciones: CPU de núcleo cuádruple de 2 Ghz, 4 GB de RAM, disco duro SATA RAID de software de 1 80 GB.
* Servidor de base de datos: CPUs de núcleo cuádruple de 3 GHz, mínimo 4 GB de RAM, disco duro SAS RAID de hardware de 10.1500 RPM, el número depende del tamaño y del rendimiento esperado de la base de datos.

>[!NOTE]
>
>La redirección y el intermediario son elementos independientes, pero el servidor de seguimiento, en general, se compartirá con los servidores intermediarios.

## Pasos de instalación y configuración {#installation-and-configuration-steps-}

### Requisitos previos {#prerequisites}

* JDK en el servidor de aplicaciones.
* Acceso a un servidor de base de datos en el servidor de aplicaciones.
* Cortafuegos configurado para abrir puertos HTTP (80) o HTTPS (443) en el servidor intermediario.

### Instalación y configuración (implementación intermediaria) {#installing-and-configuring--mid-sourcing-deployment-}

Consulte [Servidor intermediario](../../installation/using/mid-sourcing-server.md).
