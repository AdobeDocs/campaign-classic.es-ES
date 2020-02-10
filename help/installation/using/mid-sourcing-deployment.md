---
title: Implementación de fuentes intermedias
seo-title: Implementación de fuentes intermedias
description: Implementación de fuentes intermedias
seo-description: null
page-status-flag: never-activated
uuid: e359c486-7ee6-4295-80fc-4c371a0ef068
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: installation
content-type: reference
topic-tags: deployment-types-
discoiquuid: 19220d8e-9494-46b4-9aa0-4c4a729aea96
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: be590c6d993eecacf51736e3c3e415addae5c6bd

---


# Implementación de fuentes intermedias{#mid-sourcing-deployment}

Esta configuración es una solución intermedia óptima entre una configuración alojada (ASP) y la internalización. Los componentes de ejecución orientados hacia el exterior se llevan a cabo en un servidor de &quot;fuentes intermedias&quot; alojado en Adobe Campaign.

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
* Uso limitado del ancho de banda: Dado que la ejecución es llevada a cabo por el servidor de fuentes intermedias, solo se requiere un ancho de banda suficiente para enviar datos de personalización al servidor de fuentes intermedias.
* La alta disponibilidad ya no es un problema interno: El problema se traslada al servidor de fuentes intermedias (redirección, páginas espejo, servidores de ejecución, etc.).
* La base de datos no abandona la empresa: Sólo se envían al servidor de abastecimiento intermedio los datos necesarios para compilar los mensajes (para ello se puede utilizar HTTPS).
* Este tipo de implementación puede ser una solución para arquitecturas de alto volumen (muchos destinatarios en la base de datos), con un rendimiento de entrega significativo.

### Desventajas {#disadvantages}

* Ligero retraso en la visualización de la información de ejecución de mensajes y en la funcionalidad de informes debido al tiempo que se tarda en recuperar la información del servidor de fuentes intermedias.
* Los estudios y los formularios web permanecen en la plataforma del cliente.

### Equipo recomendado {#recommended-equipment}

* Servidor de aplicaciones: CPU de cuatro núcleos de 2 GHz, 4 GB de RAM, unidad de disco duro SATA RAID 1 de software de 80 GB.
* Servidor de base de datos: CPU de núcleo cuádruple de 3 GHz, mínimo 4 GB de RAM, disco duro SAS RAID de hardware de 10 15000 RPM, número que depende del tamaño y del rendimiento esperado de la base de datos.

>[!NOTE]
>
>La redirección y el abastecimiento intermedio son elementos independientes, pero el servidor de seguimiento, en general, se compartirá con los servidores de abastecimiento intermedio.

## Pasos de instalación y configuración {#installation-and-configuration-steps-}

### Requisitos previos {#prerequisites}

* JDK en el servidor de aplicaciones.
* Acceso a un servidor de bases de datos en el servidor de aplicaciones.
* Servidor de seguridad configurado para abrir puertos HTTP (80) o HTTPS (443) en el servidor de fuentes intermedias.

### Instalación y configuración (implementación de fuentes intermedias) {#installing-and-configuring--mid-sourcing-deployment-}

Consulte el servidor [de](../../installation/using/mid-sourcing-server.md)fuentes intermedias.
