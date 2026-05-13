---
product: campaign
title: Modelos de alojamiento
description: Descubra los modelos de alojamiento de Campaign
feature: Installation, Architecture, Deployment
role: Developer
level: Beginner
exl-id: a06b1365-d487-4df1-8f4a-7268b871a427
TQID: https://experienceleague.adobe.com/9pZQYt2gLVR94ZWsw21JCv7CL55KDRyiqocvuS54SbM
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
feature_v2:
  - id: a7760dfc-5c44-4d77-bb68-c50b1e265c93
subfeature_v2:
  - id: ac9c0a9c-8a76-4419-bd64-9c34c5782666
  - id: fb2a841f-c522-491f-9901-a1b939d252df
role_v2:
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
level_v2:
  - id: e8ccd51f-da0d-4e3b-939b-e30d5ebb1ea5
topic_v2:
  - id: b5ce8718-c3af-4fdb-a1a9-fca32f83a87c
  - id: cdd65e7e-8839-44a2-bc21-0e03623b5dd1
  - id: d095671a-1355-40aa-8b5f-06c33c68080b
  - id: f4e6943a-c91a-4134-a2c7-f4f20cfff2f0
source-git-commit: 4c295c0dabae8aba298390a3da2422a3fa1219f9
workflow-type: tm+mt
source-wordcount: 637
ht-degree: 3%

---

# Modelos de alojamiento{#hosting-models}



Adobe Campaign ofrece una selección de tres modelos de alojamiento, que proporcionan flexibilidad y libertad para elegir el mejor modelo o modelos para satisfacer las necesidades comerciales.

>[!NOTE]
>
>Para entornos alojados en Adobe, los pasos principales de instalación y configuración solo los puede realizar Adobe, como configurar el servidor y personalizar los archivos de configuración de instancia. Para obtener más información sobre las principales diferencias entre los modos de implementación, consulte [esta página](../../installation/using/capability-matrix.md).

## Managed Services/Alojado

Adobe Campaign se puede implementar en as a Managed Service: todos los componentes de Adobe Campaign, incluida la interfaz de usuario, el motor de administración de la ejecución y la base de datos de Campaign del cliente, están totalmente alojados en Adobe, incluida la ejecución de correo electrónico, las páginas espejo, el servidor de seguimiento y los componentes web externos, como la cancelación de suscripción de la página/centro de preferencias y las páginas de aterrizaje.

![](assets/deployment_hosted.png)

Como cliente alojado, la mayoría de los pasos de instalación y configuración los realiza Adobe. Puede acceder a las siguientes secciones para personalizar la implementación:

* Configure el seguimiento y las direcciones URL de las páginas espejo por marca. Para mensajes transaccionales, consulte [esta sección](../../message-center/using/additional-configurations.md#configuring-multibranding).
* Instale la consola de cliente: consulte [esta sección](../../installation/using/installing-the-client-console.md).
* Obtenga más información sobre las herramientas de envío y las prácticas recomendadas leyendo la [documentación detallada](../../delivery/using/about-deliverability.md).
* Configurar las opciones de Campaign: consulte [esta sección](../../installation/using/configuring-campaign-options.md).
* Configurar conectores CRM: consulte [esta sección](../../platform/using/crm-connectors.md).

## On-Premise

Adobe Campaign se puede implementar on-premise: todos los componentes de Adobe Campaign, incluida la interfaz de usuario, el motor de administración de la ejecución y la base de datos, residen in situ en el centro de datos del cliente. En este modelo de implementación, el cliente gestiona todas las actualizaciones y ampliaciones de software y hardware, y un administrador de base de datos dedicado debe realizar tareas de mantenimiento y optimización para garantizar la administración de instancias de Campaign.

![](assets/deployment_onpremise.png)

Como cliente On-Premise, antes de empezar a implementar Campaign Classic, debe cumplir los siguientes requisitos previos y recomendaciones:

* Lea la [Matriz de compatibilidad](../../rn/using/compatibility-matrix.md) que enumera todas las versiones de los sistemas y componentes compatibles con Adobe Campaign.
* Según el entorno, lea los [requisitos previos para Windows](../../installation/using/prerequisites-of-campaign-installation-in-windows.md) y [requisitos previos para Linux](../../installation/using/prerequisites-of-campaign-installation-in-linux.md).
* Conozca las recomendaciones relacionadas con los motores de base de datos [en esta sección](../../installation/using/database.md).
* Compruebe que las capas de acceso a la base de datos requeridas están instaladas en el servidor y que se puede acceder a ellas desde la cuenta de Adobe Campaign. [Más información](../../installation/using/application-server.md).
* Configure las redes, ya que algunos procesos necesitan comunicarse con otros o acceder a la LAN y a Internet. Esto significa que algunos puertos TCP deben estar abiertos para estos procesos. [Más información](../../installation/using/network-configuration.md) acerca de los requisitos de configuración de red.
* Lea [Lista de comprobación de privacidad y seguridad de Campaign](https://helpx.adobe.com/es/campaign/kb/acc-security.html).
* Consulte las directrices generales para estimar los requisitos de hardware para la implementación local [en este artículo](https://helpx.adobe.com/es/campaign/kb/hardware-sizing-guide.html).

## Híbrido

Cuando se implementa como modelo híbrido, el software de la solución Adobe Campaign reside en las instalaciones del cliente, y Adobe proporciona la administración de la ejecución como servicio en la nube. La instancia de marketing de Adobe Campaign se instala dentro del cortafuegos de un cliente, por lo que la información de identificación personal (PII) permanece interna y solo se envían a la nube los datos necesarios para personalizar los correos electrónicos para su ejecución por correo electrónico. La instancia de ejecución, alojada en la nube, recibe las solicitudes de la instancia On-Premise para enviar correos electrónicos. Esta instancia personaliza todos los correos electrónicos y los envía. No se almacenan datos de ningún tipo de forma permanente en la nube.

![](assets/deployment_hybrid.png)

Como cliente híbrido, la mayoría de los pasos de instalación y configuración los realiza Adobe. Puede acceder a las siguientes secciones para personalizar la implementación:

* Configurar mensajes transaccionales: consulte [esta sección](../../message-center/using/transactional-messaging-architecture.md).
* Configure el seguimiento y las direcciones URL de las páginas espejo por marca. Para mensajes transaccionales, consulte [esta sección](../../message-center/using/additional-configurations.md#configuring-multibranding).
* Instale la consola de cliente: consulte [esta sección](../../installation/using/installing-the-client-console.md).
* Instalar paquetes integrados: consulte [esta sección](../../installation/using/installing-campaign-standard-packages.md).
* Capacidad de entrega: configure [reglas MX](../../installation/using/email-deliverability.md#mx-configuration) y [formatos de correo electrónico](../../installation/using/email-deliverability.md#managing-email-formats). Obtenga más información sobre las herramientas de envío y las prácticas recomendadas leyendo la [documentación detallada](../../delivery/using/about-deliverability.md).
* Configurar las opciones de Campaign: consulte [esta sección](../../installation/using/configuring-campaign-options.md).
* Configure una base de datos externa (Acceso de datos federado): consulte [esta sección](../../installation/using/about-fda.md).
* Configuración de conectores CRM: consulte [esta sección](../../platform/using/crm-connectors.md).
* Para obtener más información sobre los principios de implementación intermediaria, consulte [esta sección](../../installation/using/mid-sourcing-deployment.md).
