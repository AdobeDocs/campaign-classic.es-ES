---
solution: Campaign Classic
product: campaign
title: Modelos de alojamiento
description: Modelos de alojamiento de Campaña de Discover
audience: installation
content-type: reference
topic-tags: architecture-and-hosting-models
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '334'
ht-degree: 1%

---


# Modelos de alojamiento{#hosting-models}

Adobe Campaign oferta una selección de tres modelos de hospedaje, proporcionando flexibilidad y libertad para elegir el mejor modelo o modelos para satisfacer las necesidades comerciales.

>[!NOTE]
>
>En el caso de entornos alojados en Adobe, los pasos principales de instalación y configuración solo pueden realizarse mediante Adobe, como la configuración del servidor y la personalización de los archivos de configuración de instancias. Para obtener más información sobre las principales diferencias entre los modos de implementación, consulte [esta página](../../installation/using/capability-matrix.md).

* **Managed Services (alojado)**

   Adobe Campaign se puede implementar como un servicio administrado: todos los componentes de Adobe Campaign, incluyendo la interfaz de usuario, el motor de administración de la ejecución y la base de datos de Campañas del cliente, están completamente alojados por Adobe, incluyendo la ejecución por correo electrónico, páginas espejo, el servidor de seguimiento y componentes Web orientados externamente, como cancelar la suscripción de la página o del centro de preferencias y páginas de aterrizaje. Adobe asigna hasta tres instancias en la nube: desarrollo, prueba/fase y producción. Los pasos de instalación y configuración para este modelo de hospedaje se presentan [en esta sección](../../installation/using/hosted-model.md).

   ![](assets/deployment_hosted.png)

* **In situ**

   Adobe Campaign se puede implementar in situ: todos los componentes de Adobe Campaign, incluyendo la interfaz de usuario, el motor de administración de la ejecución y la base de datos, residen en el centro de datos del cliente. En este modelo de implementación, el cliente administra todas las actualizaciones y actualizaciones de software y hardware, y un administrador de base de datos dedicado debe realizar tareas de mantenimiento y optimización para garantizar la administración de instancias de Campaña. Las directrices de implementación para clientes locales se presentan [en esta sección](../../installation/using/before-starting.md).

   ![](assets/deployment_onpremise.png)

* **Híbrido**

   Cuando se implementa como modelo híbrido, el software de la solución Adobe Campaign reside in situ en el sitio del cliente y la administración de la ejecución se entrega como un servicio en la nube por Adobe. La instancia de marketing de Adobe Campaign se instala dentro del cortafuegos de un cliente, por lo que la información de identificación personal (PII) permanece interna y solo los datos necesarios para personalizar los correos electrónicos se envían a la nube para la ejecución por correo electrónico. La instancia de ejecución, alojada en la nube, recibe las solicitudes de la instancia local para enviar correos electrónicos. Esta instancia personaliza todos los correos electrónicos y los envía. Ningún dato de ningún tipo se almacena permanentemente en la nube. Los pasos de instalación y configuración para este modelo de hospedaje se presentan [en esta sección](../../installation/using/hybrid-model.md).

   ![](assets/deployment_hybrid.png)

