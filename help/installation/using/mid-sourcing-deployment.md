---
product: campaign
title: Implementación intermediaria
description: Implementación intermediaria
feature: Installation, Architecture, Deployment
badge-v7-only: label="v7" type="Informative" tooltip="Se aplica solo a Campaign Classic v7"
audience: installation
content-type: reference
topic-tags: deployment-types-
exl-id: 8a4d7ef1-de5b-4aee-a527-1b74d987ba61
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: tm+mt
source-wordcount: '358'
ht-degree: 4%

---

# Implementación intermediaria{#mid-sourcing-deployment}



Esta configuración es una solución intermedia óptima entre una configuración alojada (ASP) y la internalización. Los componentes de ejecución salientes se llevan a cabo en un servidor &quot;intermediario&quot; alojado en Adobe Campaign.

>[!NOTE]
>
>Para configurar este tipo de implementación, debe adquirir la opción adecuada. Compruebe el contrato de licencia.

La comunicación general entre servidores y procesos se realiza según el siguiente esquema:

![](assets/s_ncs_install_midsourcing.png)

* Los módulos de administración de ejecución y rechazos están desactivados en la instancia.
* La aplicación está configurada para ejecutar mensajes en un servidor &quot;intermediario&quot; remoto que se administra mediante llamadas SOAP (a través de HTTP o HTTPS).

## Funciones {#features}

### Ventajas {#advantages}

* Configuración simplificada del servidor: no es necesario que el cliente configure módulos externos (mta e inMail).
* Uso limitado del ancho de banda: Dado que la ejecución se realiza mediante el servidor intermediario, solo se necesita el ancho de banda suficiente para enviar datos de personalización al servidor intermediario.
* La alta disponibilidad ya no es un problema interno: el problema se desplaza al servidor intermediario (redirección, páginas espejo, servidores de ejecución, etc.).
* La base de datos no abandona la empresa: solo se envían al servidor intermediario los datos necesarios para montar los mensajes (para ello se puede utilizar HTTPS).
* Este tipo de implementación puede ser una solución para arquitecturas de gran volumen (muchos destinatarios en la base de datos), con un rendimiento de entrega significativo.

### Desventajas {#disadvantages}

* Ligero retraso en la visualización de la información de ejecución del mensaje y en la funcionalidad de creación de informes debido al tiempo que se tarda en recuperar la información del servidor intermediario.
* Las encuestas y los formularios web permanecen en la plataforma del cliente.

### Equipo recomendado {#recommended-equipment}

* Servidor de aplicaciones: CPU de núcleo cuádruple a 2 GHz, 4 GB de RAM, RAID de software, disco duro SATA de 80 GB.
* Servidor de base de datos: CPUs de núcleo bi-cuádruple de 3 GHz, RAM mínima de 4 GB, disco duro SAS RAID de hardware a 10 15000RPM, el número depende del tamaño y el rendimiento esperado de la base de datos.

>[!NOTE]
>
>La redirección y el intermediario son elementos independientes, pero el servidor de seguimiento se compartirá, en general, con los servidores intermediarios.

## Pasos de instalación y configuración {#installation-and-configuration-steps-}

### Requisitos previos {#prerequisites}

* JDK en el servidor de aplicaciones.
* Acceso a un servidor de base de datos en el servidor de aplicaciones.
* Firewall configurado para abrir puertos HTTP (80) o HTTPS (443) en el servidor intermediario.

### Instalación y configuración (implementación intermediaria) {#installing-and-configuring--mid-sourcing-deployment-}

Consulte [Mid-sourcing server](../../installation/using/mid-sourcing-server.md).
