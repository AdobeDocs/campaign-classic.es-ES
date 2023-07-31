---
product: campaign
title: Modelos de alojamiento
description: Descubra los modelos de alojamiento de Campaign
feature: Installation, Architecture, Deployment
badge-v7-only: label="v7" type="Informative" tooltip="Solo se aplica a Campaign Classic v7"
role: Architect
level: Beginner
exl-id: a06b1365-d487-4df1-8f4a-7268b871a427
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: tm+mt
source-wordcount: '630'
ht-degree: 2%

---

# Modelos de alojamiento{#hosting-models}



Adobe Campaign ofrece una selección de tres modelos de alojamiento, que proporcionan flexibilidad y libertad para elegir el mejor modelo o modelos para satisfacer las necesidades comerciales.

>[!NOTE]
>
>En los entornos alojados en Adobe, los pasos principales de instalación y configuración solo se pueden realizar mediante Adobe, como configurar el servidor y personalizar los archivos de configuración de instancia. Para obtener más información sobre las principales diferencias entre los modos de implementación, consulte [esta página](../../installation/using/capability-matrix.md).

## Managed Services/Alojado

Adobe Campaign se puede implementar as a Managed Service: todos los componentes de Adobe Campaign, incluida la interfaz de usuario, el motor de administración de la ejecución y la base de datos de Campaign del cliente, están totalmente alojados por el Adobe, incluida la ejecución por correo electrónico, las páginas espejo, el servidor de seguimiento y los componentes web externos, como la cancelación de la suscripción de la página/centro de preferencias y páginas de aterrizaje.

![](assets/deployment_hosted.png)

Como cliente alojado, la mayoría de los pasos de instalación y configuración se realizan por Adobe. Puede acceder a las siguientes secciones para personalizar la implementación:

* Configure el seguimiento y las direcciones URL de las páginas espejo por marca. Para mensajes transaccionales, consulte [a esta sección](../../message-center/using/additional-configurations.md#configuring-multibranding).
* Instale la consola del cliente: consulte [a esta sección](../../installation/using/installing-the-client-console.md).
* Obtenga más información sobre las herramientas de envío y las prácticas recomendadas leyendo el [documentación detallada](../../delivery/using/about-deliverability.md).
* Configure las opciones de Campaign: consulte [a esta sección](../../installation/using/configuring-campaign-options.md).
* Configurar conectores CRM: consulte [a esta sección](../../platform/using/crm-connectors.md).

## On-Premise

Adobe Campaign se puede implementar on-premise: todos los componentes de Adobe Campaign, incluida la interfaz de usuario, el motor de administración de la ejecución y la base de datos, residen in situ en el centro de datos del cliente. En este modelo de implementación, el cliente gestiona todas las actualizaciones y ampliaciones de software y hardware, y un administrador de base de datos dedicado debe realizar tareas de mantenimiento y optimización para garantizar la administración de instancias de Campaign.

![](assets/deployment_onpremise.png)

Como cliente On-Premise, antes de empezar a implementar Campaign Classic, debe cumplir los siguientes requisitos previos y recomendaciones:

* Lea el [Matriz de compatibilidad](../../rn/using/compatibility-matrix.md) que enumera todas las versiones de los sistemas y componentes compatibles con Adobe Campaign.
* Según el entorno, lea el [requisitos previos para Windows](../../installation/using/prerequisites-of-campaign-installation-in-windows.md) y [requisitos previos para Linux](../../installation/using/prerequisites-of-campaign-installation-in-linux.md).
* Conozca las recomendaciones relacionadas con los motores de base de datos [en esta sección](../../installation/using/database.md).
* Compruebe que las capas de acceso a la base de datos requeridas están instaladas en el servidor y que se puede acceder a ellas desde la cuenta de Adobe Campaign. [Más información](../../installation/using/application-server.md).
* Configure las redes, ya que algunos procesos necesitan comunicarse con otros o acceder a la LAN y a Internet. Esto significa que algunos puertos TCP deben estar abiertos para estos procesos. [Más información](../../installation/using/network-configuration.md) acerca de los requisitos de configuración de red.
* Leer más [Lista de comprobación de seguridad y privacidad de Campaign](https://helpx.adobe.com/es/campaign/kb/acc-security.html).
* Consulte las directrices generales para estimar los requisitos de hardware para la implementación local [en este artículo](https://helpx.adobe.com/es/campaign/kb/hardware-sizing-guide.html).

## Híbrido

Cuando se implementa como modelo híbrido, el software de la solución Adobe Campaign reside en las instalaciones del cliente y la administración de la ejecución se proporciona como servicio en la nube por Adobe. La instancia de marketing de Adobe Campaign se instala dentro del cortafuegos de un cliente, por lo que la información de identificación personal (PII) permanece interna y solo se envían a la nube los datos necesarios para personalizar los correos electrónicos para su ejecución por correo electrónico. La instancia de ejecución, alojada en la nube, recibe las solicitudes de la instancia local para enviar correos electrónicos. Esta instancia personaliza todos los correos electrónicos y los envía. No se almacenan datos de ningún tipo de forma permanente en la nube.

![](assets/deployment_hybrid.png)

Como cliente híbrido, la mayoría de los pasos de instalación y configuración se realizan por Adobe. Puede acceder a las siguientes secciones para personalizar la implementación:

* Configuración de mensajes transaccionales: consulte [a esta sección](../../message-center/using/transactional-messaging-architecture.md).
* Configure el seguimiento y las direcciones URL de las páginas espejo por marca. Para mensajes transaccionales, consulte [a esta sección](../../message-center/using/additional-configurations.md#configuring-multibranding).
* Instale la consola del cliente: consulte [a esta sección](../../installation/using/installing-the-client-console.md).
* Instale los paquetes integrados: consulte [a esta sección](../../installation/using/installing-campaign-standard-packages.md).
* Entrega: configurar [Reglas MX](../../installation/using/email-deliverability.md#mx-configuration) y [formatos de correo electrónico](../../installation/using/email-deliverability.md#managing-email-formats). Obtenga más información sobre las herramientas de envío y las prácticas recomendadas leyendo el [documentación detallada](../../delivery/using/about-deliverability.md).
* Configure las opciones de Campaign: consulte [a esta sección](../../installation/using/configuring-campaign-options.md).
* Configure una base de datos externa (Acceso de datos federado): consulte [a esta sección](../../installation/using/about-fda.md).
* Configuración de conectores CRM: consulte [a esta sección](../../platform/using/crm-connectors.md).
* Para obtener más información sobre los principios de implementación intermediaria, consulte [a esta sección](../../installation/using/mid-sourcing-deployment.md).
