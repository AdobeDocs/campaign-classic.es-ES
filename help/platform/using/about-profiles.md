---
solution: Campaign Classic
product: campaign
title: Acerca de los perfiles
description: Acerca de los perfiles
feature: Perfiles, Audiencias
role: Business Practitioner, Data Architect
level: Beginner
exl-id: 54f1ad6c-54b0-4448-8c38-806dd75c1dae
source-git-commit: 214838cabeaec082080b3378f7eba837b8af89ad
workflow-type: tm+mt
source-wordcount: '899'
ht-degree: 93%

---

# Introducción a los perfiles{#about-profiles}

Los perfiles están centralizados en la base de datos de Adobe Campaign. Existen muchos mecanismos para adquirir perfiles y crear esta base de datos: recopilación en línea a través de formularios web, importación manual o automática de archivos de texto, replicación con bases de datos de fabricantes, u otros sistemas de información. Con Adobe Campaign, puede incorporar el historial de marketing, la información de compra, las preferencias, los datos CRM y cualquier dato PI relevante en una vista consolidada para analizar y actuar en consecuencia.

Un “**perfil**” es un registro de información (por ejemplo, un registro de la tabla nmsRecipient o una tabla externa que contiene un ID de cookie, ID de cliente, ID móvil u otra información relacionada con un canal determinado) que representa a un cliente final, a un cliente potencial o a un posible cliente.

En Adobe Campaign, los destinatarios son los perfiles seleccionados por defecto para enviarles contenido (correos electrónicos, SMS, etc.). Los datos de destinatario almacenados en la base de datos permiten filtrar el destinatario que recibirá cualquier entrega dada y añadir datos de personalización en el contenido de la entrega. Existen otros tipos de perfiles en la base de datos. Están diseñados para usos diferentes. Por ejemplo, se crean perfiles semilla para probar el contenido antes de enviarlo al público objetivo final.

![](assets/do-not-localize/how-to-video.png) [Comprensión del concepto de perfiles en vídeo](#create-profiles-video)

## Tipos de perfil {#profile-types}

Adobe Campaign permite administrar perfiles en todo el ciclo de vida: creación, importación, definición de público objetivo, seguimiento de acciones, actualizaciones, etc.

Cada perfil coincide con una entrada en la base de datos. Contienen toda la información necesaria para la definición de público objetivo, el cumplimiento y el seguimiento de personas.

Los perfiles se pueden identificar en función del espacio de almacenamiento. Esto significa que un perfil puede coincidir con un destinatario, un visitante, un operador, un suscriptor, un cliente potencial, etc.

## Perfiles de destinatario {#recipient-profiles}

Los destinatarios de envíos se almacenan en la base de datos como perfiles que contienen información vinculada a ellos, como apellidos, nombre, dirección, suscripciones, envíos, etc. Al crear campañas, puede definir el objetivo de las entregas a una selección de los perfiles de la base de datos de acuerdo con criterios sencillos o avanzados.

También puede crear campañas para destinatarios cuyos perfiles no estén almacenados en la base de datos, sino en los archivos. Estos se conocen como envíos &quot;externos&quot;. Para obtener más información sobre este tipo de envío, consulte [esta página](../../delivery/using/steps-defining-the-target-population.md#selecting-external-recipients).

Los métodos principales para crear perfiles de destinatario son los siguientes:

* Entrada directa en las pantallas de la interfaz gráfica.
* Importación de listas de destinatarios.
* Captura en línea mediante formularios web.

>[!NOTE]
>
>Para saber cómo se importan los archivos y los formularios web, consulte [Importar y exportar genéricas](../../platform/using/get-started-data-import-export.md).

## Perfiles y público objetivo {#profiles-and-targets}

El vínculo **[!UICONTROL Profiles and targets]** permite mostrar los destinatarios almacenados en la base de datos de Adobe Campaign. Puede crear un destinatario nuevo, editar un destinatario existente y acceder a su perfil. Para obtener más información, consulte [esta página](../../platform/using/editing-a-profile.md).

![](assets/d_ncs_user_interface_target_link.png)

También le proporciona acceso a:

* listas: [Más información](../../platform/using/creating-and-managing-lists.md)
* servicios de suscripción: [Más información](../../delivery/using/managing-subscriptions.md)
* aplicaciones web: [Más información](../../web/using/about-web-applications.md)
* importaciones y exportaciones (trabajos): [Más información](../../platform/using/about-generic-imports-exports.md)
* flujos de trabajo de segmentación: [Más información](../../workflow/using/building-a-workflow.md#implementation-steps-)

La página de destinatarios permite realizar operaciones frecuentes en los perfiles, como ediciones, actualizaciones, adiciones, eliminaciones y operaciones de ordenación.

Para realizar manipulaciones de perfiles más avanzadas, debe editar el árbol de Adobe Campaign. Para ello, haga clic en el vínculo **[!UICONTROL Explorer]** de la página principal de Adobe Campaign.

De forma predeterminada, los destinatarios se almacenan en el nodo **[!UICONTROL Profiles and Targets > Recipients]** del árbol de Puede crear destinatarios a partir de esta vista, así como lo siguiente:

* ordenar y filtrar los perfiles de la base de datos: [Más información](../../platform/using/filtering-options.md)
* mover, copiar o eliminar perfiles de la base de datos: [Más información](../../platform/using/managing-profiles.md),
* actualizar perfiles: [Más información](../../platform/using/updating-data.md)
* exportar destinatarios: [Más información](../../platform/using/exporting-and-importing-profiles.md)
* crear grupos de destinatarios: [Más información](../../platform/using/creating-and-managing-lists.md)

Para acceder a las funcionalidades y configuraciones avanzadas, debe hacer clic en el icono **[!UICONTROL Explorer]**.

![](assets/d_ncs_user_interface01.png)

El diseño general del explorador de Adobe Campaign se presenta en [esta página](../../platform/using/adobe-campaign-explorer.md).

>[!NOTE]
>
>También puede mostrar una vista avanzada de esta lista del árbol de Adobe Campaign haciendo clic en el vínculo **[!UICONTROL Profiles and targets > Recipients]** . La visualización de la lista se puede configurar para adaptarla a sus necesidades. Puede agregar o eliminar columnas, definir el orden de las columnas, ordenar datos, etc. La configuración de visualización de lista se describe en [esta página](../../platform/using/adobe-campaign-ui-lists.md).
>
>También puede definir las vistas de los destinatarios. Para obtener más información acerca de esta funcionalidad, consulte [esta sección](../../platform/using/access-management-folders.md).

## Perfiles activos {#active-profiles}

Los perfiles activos son los perfiles que se toman en cuenta con fines de facturación.

La facturación solo abarca los perfiles que están **activos**. Un perfil se considera activo si este se ha identificado o comunicado en los últimos 12 meses a través de cualquier canal.

Los perfiles que se excluyen durante la preparación de la entrega (reglas de tipología, cuarentena) no se tienen en cuenta. Un perfil identificado por varios envíos solo se contará una vez.

>[!NOTE]
>
>Los canales de Facebook y Twitter no se tienen en cuenta.

Desde el explorador de Campaign, vaya a **[!UICONTROL Administration > Campaign Management > Customer metrics]** para obtener una descripción general del número de perfiles activos. El recuento real lo realiza el **[!UICONTROL Number of active billing profiles]** ([!UICONTROL billingActiveContactCount]) [flujo de trabajo técnico](../../workflow/using/about-technical-workflows.md). Este flujo de trabajo se ejecuta todos los días y agrega los nuevos datos al informe existente para el periodo actual en la carpeta **[!UICONTROL Customer metrics]**.

Tenga en cuenta que el recuento de perfiles principales solo está disponible para las **instancias de marketing**. No está disponible para Instancias de ejecución; es decir, instancias de MID (fuentes intermedias) y RT (mensajería en tiempo real/centro de mensajes).

>[!NOTE]
>
>También puede monitorizar el número de perfiles activos en su instancia directamente desde Campaign Panel de control de Campaign. Para obtener más información, consulte la [documentación del Panel de control de Campaign](https://experienceleague.adobe.com/docs/control-panel/using/performance-monitoring/active-profiles-monitoring.html?lang=es#performance-monitoring).

## Vídeo tutorial {#create-profiles-video}

Obtenga información sobre cómo acceder a los datos de perfiles, ordenar y filtrar perfiles, y crear y administrar manualmente perfiles.

Este vídeo también explica la conformidad de Adobe Campaign Classic con las Regulaciones Generales de Protección de Datos.

>[!VIDEO](https://video.tv.adobe.com/v/35611?quality=12)

Puede encontrar disponibles más vídeos de procedimientos para Campaign Classic [aquí](https://experienceleague.adobe.com/docs/campaign-classic-learn/tutorials/overview.html?lang=es).

**Consulte también**

* [Administración de la privacidad en Campaign](https://helpx.adobe.com/es/campaign/kb/acc-privacy.html)

* [Definición de la población objetivo.](../../delivery/using/define-the-right-audience.md)

* [Creación de consultas y datos de segmentos en flujos de trabajo](../../workflow/using/targeting-data.md)

* [Selección de la asignación de destino](../../delivery/using/selecting-a-target-mapping.md)

* [Definición de la audiencia: prácticas recomendadas](../../delivery/using/define-the-right-audience.md)
