---
solution: Campaign Classic
product: campaign
title: Implementación intermediaria
description: Implementación intermediaria
audience: installation
content-type: reference
topic-tags: deployment-types-
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '351'
ht-degree: 2%

---


# Implementación intermediaria{#mid-sourcing-deployment}

Esta configuración es una solución intermedia óptima entre una configuración alojada (ASP) y la internalización. Los componentes de ejecución orientados hacia el exterior se llevan a cabo en un servidor &quot;intermediaria&quot; alojado en Adobe Campaign.

>[!NOTE]
>
>Para configurar este tipo de implementación, debe adquirir la opción adecuada. Verifique su contrato de licencia.

La comunicación general entre servidores y procesos se realiza según el siguiente esquema:

![](assets/s_ncs_install_midsourcing.png)

* Los módulos de administración de ejecución y devolución están desactivados en la instancia.
* La aplicación está configurada para realizar la ejecución de mensajes en un servidor remoto de &quot;origen medio&quot; que se controla mediante llamadas SOAP (a través de HTTP o HTTPS).

## Funciones {#features}

### Ventajas {#advantages}

* Configuración del servidor simplificada: No es necesario que el cliente configure módulos orientados hacia el exterior (mta y inMail).
* Uso limitado del ancho de banda: Dado que la ejecución la realiza el servidor intermediaria, solo se requiere un ancho de banda suficiente para enviar datos de personalización al servidor intermediaria.
* La alta disponibilidad ya no es un problema interno: El problema se transfiere al servidor intermediaria (redirección, páginas espejo, servidores de ejecución, etc.).
* La base de datos no deja la compañía: Solo se envían al servidor intermediaria los datos necesarios para compilar los mensajes (para ello se puede utilizar HTTPS).
* Este tipo de implementación puede ser una solución para arquitecturas de alto volumen (muchos destinatarios en la base de datos), con un rendimiento de envío significativo.

### Desventajas {#disadvantages}

* Ligero retraso en la visualización de la información de ejecución de mensajes y en la funcionalidad de sistema de informes debido al tiempo que se tarda en obtener información del servidor de intermediaria.
* Las encuestas y los formularios web permanecen en la plataforma cliente.

### Equipo recomendado {#recommended-equipment}

* Servidor de aplicaciones: CPU de cuatro núcleos de 2 GHz, 4 GB de RAM, unidad de disco duro SATA RAID 1 de software de 80 GB.
* Servidor de base de datos: CPU de núcleo cuádruple de 3 GHz, mínimo 4 GB de RAM, disco duro SAS RAID de hardware de 10 15000 RPM, número que depende del tamaño y del rendimiento esperado de la base de datos.

>[!NOTE]
>
>La redirección y el intermediaria son elementos independientes, pero el servidor de seguimiento, en general, se compartirá con los servidores intermediaria.

## Pasos de instalación y configuración {#installation-and-configuration-steps-}

### Requisitos previos {#prerequisites}

* JDK en el servidor de aplicaciones.
* Acceso a un servidor de bases de datos en el servidor de aplicaciones.
* Servidor de seguridad configurado para abrir puertos HTTP (80) o HTTPS (443) en el servidor intermediaria.

### Instalación y configuración (implementación de intermediaria) {#installing-and-configuring--mid-sourcing-deployment-}

Consulte [servidor Intermediaria](../../installation/using/mid-sourcing-server.md).
