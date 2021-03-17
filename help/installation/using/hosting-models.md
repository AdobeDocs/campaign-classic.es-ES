---
solution: Campaign Classic
product: campaign
title: Modelos de alojamiento
description: Descubra los modelos de alojamiento de Campaign
feature: Información general
role: Arquitecto
level: Principiante
translation-type: tm+mt
source-git-commit: d88815e36f7be1b010dcaeee51013a5da769b4a8
workflow-type: tm+mt
source-wordcount: '634'
ht-degree: 2%

---


# Modelos de alojamiento{#hosting-models}

Adobe Campaign ofrece una selección de tres modelos de alojamiento, lo que proporciona flexibilidad y libertad para elegir el mejor modelo o modelos para adaptarse a las necesidades comerciales.

>[!NOTE]
>
>Para los entornos alojados en Adobe, los pasos principales de instalación y configuración solo se pueden realizar mediante Adobe, como configurar el servidor y personalizar los archivos de configuración de instancias. Para obtener más información sobre las principales diferencias entre los modos de implementación, consulte [esta página](../../installation/using/capability-matrix.md).

## Managed Services / Alojado

Adobe Campaign se puede implementar como un servicio administrado: todos los componentes de Adobe Campaign, incluida la interfaz de usuario, el motor de administración de ejecución y la base de datos de Campaign del cliente, están totalmente alojados en Adobe, incluida la ejecución de correo electrónico, las páginas espejo, el servidor de seguimiento y los componentes web orientados externamente, como la cancelación de la suscripción a la página o al centro de preferencias y las páginas de aterrizaje.

![](assets/deployment_hosted.png)

Como cliente alojado, la mayoría de los pasos de instalación y configuración los realiza Adobe. Puede acceder a las secciones siguientes para personalizar la implementación:

* Configure el seguimiento y las direcciones URL de páginas espejo por marca. Para los mensajes transaccionales, consulte [esta sección](../../message-center/using/configuring-multibranding.md).
* Instale la consola del cliente: consulte [a esta sección](../../installation/using/installing-the-client-console.md).
* Para obtener más información sobre las herramientas de envío y las prácticas recomendadas, lea la [guía de introducción](../../delivery/using/deliverability-key-points.md) y la [documentación detallada](../../delivery/using/about-deliverability.md).
* Configure las opciones de Campaign: consulte [a esta sección](../../installation/using/configuring-campaign-options.md).
* Configurar conectores CRM: consulte [a esta sección](../../platform/using/crm-connectors.md).

## On-Premise

Adobe Campaign se puede implementar in situ: todos los componentes de Adobe Campaign, incluida la interfaz de usuario, el motor de administración de ejecución y la base de datos, residen en el centro de datos del cliente. En este modelo de implementación, el cliente gestiona todas las actualizaciones y actualizaciones de software y hardware, y un administrador de base de datos dedicado debe realizar tareas de mantenimiento y optimización para garantizar la administración de instancias de Campaign.

![](assets/deployment_onpremise.png)

Como cliente On-Premise, antes de comenzar a implementar el Campaign Classic, debe cumplir los siguientes requisitos previos y recomendaciones:

* Lea la [Matriz de compatibilidad](../../rn/using/compatibility-matrix.md) que enumera todas las versiones de los sistemas y componentes compatibles con Adobe Campaign.
* En función de su entorno, lea los [requisitos previos para Windows](../../installation/using/prerequisites-of-campaign-installation-in-windows.md) y [requisitos previos para Linux](../../installation/using/prerequisites-of-campaign-installation-in-linux.md).
* Consulte las recomendaciones relacionadas con los motores de base de datos [en esta sección](../../installation/using/database.md).
* Compruebe que las capas de acceso a la base de datos necesarias estén instaladas en el servidor y sean accesibles desde la cuenta de Adobe Campaign. [Más información](../../installation/using/application-server.md).
* Configure sus redes, ya que algunos procesos necesitan comunicarse con otros o acceder a la LAN y a Internet. Esto significa que algunos puertos TCP deben estar abiertos para estos procesos. [Obtenga ](../../installation/using/network-configuration.md) más información sobre los requisitos de configuración de red.
* Lea la [Lista de comprobación de seguridad y privacidad de Campaign](https://helpx.adobe.com/es/campaign/kb/acc-security.html).
* Consulte las directrices generales para estimar los requisitos de hardware para la implementación local [en este artículo](https://helpx.adobe.com/es/campaign/kb/hardware-sizing-guide.html).

## Híbrido

Cuando se implementa como un modelo híbrido, el software de la solución Adobe Campaign reside en el sitio del cliente y la administración de la ejecución se entrega como un servicio en la nube por Adobe. La instancia de marketing de Adobe Campaign se instala dentro del cortafuegos de un cliente, por lo que la información de identificación personal (PII) permanece interna y solo se envían a la nube los datos necesarios para personalizar los correos electrónicos con el fin de ejecutarlos por correo electrónico. La instancia de ejecución, alojada en la nube, recibe las solicitudes de la instancia local para enviar correos electrónicos. Esta instancia personaliza todos los correos electrónicos y los envía. Ningún dato de ningún tipo se almacena de forma permanente en la nube.

![](assets/deployment_hybrid.png)

Como cliente híbrido, la mayoría de los pasos de instalación y configuración se realizan mediante Adobe. Puede acceder a las secciones siguientes para personalizar la implementación:

* Configure los mensajes transaccionales: consulte [a esta sección](../../message-center/using/transactional-messaging-architecture.md).
* Configure el seguimiento y las direcciones URL de páginas espejo por marca. Para los mensajes transaccionales, consulte [esta sección](../../message-center/using/configuring-multibranding.md).
* Instale la consola del cliente: consulte [a esta sección](../../installation/using/installing-the-client-console.md).
* Instale paquetes integrados: consulte [a esta sección](../../installation/using/installing-campaign-standard-packages.md).
* Capacidad de entrega: configure [reglas MX](../../installation/using/email-deliverability.md#mx-configuration) y [formatos de correo electrónico](../../installation/using/email-deliverability.md#managing-email-formats). Para obtener más información sobre las herramientas de envío y las prácticas recomendadas, lea la [guía de introducción](../../delivery/using/deliverability-key-points.md) y la [documentación detallada](../../delivery/using/about-deliverability.md).
* Configure las opciones de Campaign: consulte [a esta sección](../../installation/using/configuring-campaign-options.md).
* Configurar una base de datos externa (acceso de datos federado): consulte [a esta sección](../../installation/using/about-fda.md).
* Configuración de conectores CRM: consulte [a esta sección](../../platform/using/crm-connectors.md).
* Para obtener más información sobre los principios de implementación de mid-sourcing, consulte [esta sección](../../installation/using/mid-sourcing-deployment.md).
