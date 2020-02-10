---
title: Acerca de Distributed Marketing
seo-title: Acerca de Distributed Marketing
description: Acerca de Distributed Marketing
seo-description: null
page-status-flag: never-activated
uuid: 7f7ece67-c644-4072-a06c-c5b49f3acb5d
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: campaign
content-type: reference
topic-tags: distributed-marketing
discoiquuid: 6d694f5c-1d1f-4686-b3bf-8697d919a0c8
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: b47dcfa0e4ee2e5e43e7aa14b94e12fd70ff9c2d

---


# Acerca de Distributed Marketing{#about-distributed-marketing}

## Introducción {#introduction}

Adobe Campaign ofrece una aplicación de **Marketing distribuido** para implementar campañas cooperativas entre entidades centrales (sede central, Departamentos de Marketing, etc.) y entidades locales (puntos de ventas, agencias regionales, etc.). This cooperation is based on a shared workspace known as the **[!UICONTROL list of campaign packages]**, where centrally created campaign templates and instances are offered to local entities.

La entidad central proporciona campañas que entidades locales pueden utilizar. Las campañas se materializan mediante paquetes que corresponden a campañas locales o de colaboración. Para utilizar una campaña, la entidad local debe pedirla y se debe aprobar la solicitud.

>[!CAUTION]
>
>El módulo de Distributed Marketing es una opción de **Campaign.** Compruebe el acuerdo de licencia.

## Terminología {#terminology}

### Entidades centrales {#central-entities}

Las entidades centrales están formadas por operadores de marketing responsables de especificar comunicaciones y ayudar a las entidades locales a ejecutar su campaña de marketing.

El módulo de Distributed Marketing permite que la entidad central:

* configure paquetes de campañas de marketing para entidades locales,
* aumente el grado de autonomía de las entidades locales respecto a la elección de la comunicación para clientes o posibles clientes, así como su segmentación, contenido, etc.
* administre y controle los costes,
* gestione una red de agencias.

### Entidades locales {#local-entities}

Las entidades locales pueden ser agencias, tiendas o grupos de operadores locales específicos (directores de país o región, administradores de marcas, etc.).

Distributed Marketing permite que las entidades locales tengan más autonomía al optimizar los costes de ejecución.

### Localización {#localization}

La localización es la capacidad de una entidad local para modificar los destinatarios y el contenido de una campaña. El nivel de localización posible depende del tipo de campaña y de su implementación.

### Lista de paquetes de campañas {#list-of-campaign-packages}

La lista de paquetes de campañas contiene las campañas disponibles para las entidades locales.

### Paquete de campañas {#campaign-package}

Plantilla (o instancia de campaña) creada por una entidad central y disponible para un conjunto de entidades locales.

### Campaña local {#local-campaign}

A local campaign is an instance created from a template referenced in the list of **[!UICONTROL campaign packages]** with a **specific execution schedule**. Su objetivo es utilizar una comunicación local mediante una plantilla de campaña configurada por la entidad central.

El grado de autonomía de la entidad local depende de la implementación utilizada.

Consulte [Creación de una campaña](../../campaign/using/creating-a-local-campaign.md)local.

### Campaña de colaboración {#collaborative-campaign}

Una campaña de colaboración es aquella que pueden utilizar las entidades locales y cuya **programación de ejecución** queda a cargo de la entidad central. El contenido es el mismo para cada entidad local pero se comparten los costes. Para participar, las entidades locales deben suscribirse a la campaña de colaboración.

* **[!UICONTROL Collaborative campaign (by form)]**:: recomendado para campañas con hasta 300 entidades locales. La entidad local puede introducir parámetros predefinidos para la personalización de contenido y objetivos en un formulario Web. El formulario puede ser un formulario de Adobe Campaign o un formulario externo (cliente de extranet). Un administrador funcional puede definir y configurar el formulario basado en una plantilla de formulario definida por el integrador. Para solicitar la campaña, la entidad local solo necesita tener acceso a la Web.
* **[!UICONTROL Collaborative campaign (by campaign)]**: recomendado para campañas destinadas a decenas de entidades locales. Este tipo de campaña crea campañas secundarias para cada entidad local. Once the **[!UICONTROL collaborative campaign (by campaign)]** is approved by the central entity, the campaign is made available to the local entity, who can modify it. La ejecución se realiza automáticamente entre las campañas principales y secundarias. La entidad local debe tener acceso a una instancia para solicitar una campaña y participar en ella.
* **[!UICONTROL Collaborative campaign (by target approval)]**:: recomendado para campañas dirigidas a varios miles de entidades locales. La entidad local recibe una lista de contactos predefinida por la entidad central. La entidad local decide si se deben o no conservar ciertos contactos según el contenido de la campaña, a través de un formulario Web. Las entidades locales se obtienen de la lista de contactos seleccionados. Para participar en la campaña, la entidad local solo necesita tener acceso a la Web.
* **[!UICONTROL Collaborative campaign (simple)]**:: este modo garantiza la compatibilidad con los procesos de ejecución específicos de las versiones anteriores.

Consulte [Creación de una campaña](../../campaign/using/creating-a-collaborative-campaign.md)de colaboración.

### Solicitud de paquetes de campaña {#ordering-campaign-packages}

Si una entidad local se registra para una campaña, esto se convierte en una solicitud que reagrupa toda la información relativa a la localización de la campaña.

## Espacio de trabajo {#workspace}

The list of campaign packages can be accessed from the **Campaigns** universe: click the **[!UICONTROL Campaign packages]** link.

![](assets/mkg_dist_home_local_op.png)

Esta ventana permite que todos los operadores locales vean las campañas disponibles para su organismo local.

En el caso de las agencias centrales, esta ventana muestra todos los paquetes disponibles en la lista de paquetes de campañas e incluye enlaces adicionales para editar la lista.

## Operadores y entidades {#operators-and-entities}

Start by specifying the central and local entity operators via the **[!UICONTROL Access management]** folder.

![](assets/s_advuser_mkg_dist_tree.png)

### Operadores {#operators}

Necesita crear operadores locales y centrales.

Central operators must belong to the **[!UICONTROL Central management]** operator group or have the **[!UICONTROL CENTRAL]** named right.

Local operators must belong to the **[!UICONTROL Local management]** operator group or have the **[!UICONTROL LOCAL]** named right. También deben estar vinculados a su entidad local.

![](assets/s_advuser_mkg_dist_local_create.png)

### Entidades organizativas {#organizational-entities}

To create an organizational entity, click the **[!UICONTROL Administration > Access management > Organizational entities]** node and click the **[!UICONTROL New]** icon above the list of entities.

![](assets/s_advuser_mkg_dist_local_list.png)

Cada entidad organizativa contiene información de identificación (etiqueta, nombre interno, información de contacto, etc.) y grupos involucrados en el proceso de aprobación. Estos se definen en la sección que **[!UICONTROL Notifications and approvals]** se encuentra en la **[!UICONTROL General]** ficha.

* Defina un grupo de notificación de paquetes: los operadores de este grupo recibirán una notificación cada vez que se añada un nuevo paquete a la lista de paquetes de campañas y cada vez que una campaña esté disponible.
* Seleccione el grupo de revisores de la aprobación de solicitudes; es decir, aquellos que se encarguen de aprobar las campañas ordenadas por la entidad local.
* Finalmente, seleccione el grupo de revisores de la aprobación de la campaña local (objetivo, contenido, presupuesto, etc.). Este grupo puede añadirse a la solicitud de una campaña, según la plantilla.

>[!NOTE]
>
>The approval process is presented in the [Approval process](../../campaign/using/creating-a-local-campaign.md#approval-process) section.

## Implementación {#implementation}

La entidad central es la encargada de crear y publicar las campañas de Distributed Marketing. Las entidades locales y centrales pueden utilizarlas según sea necesario.

El procedimiento de implementación depende del tipo de paquete de campaña utilizado y de los niveles de delegación de entidades locales.

### Lado integrador {#integrator-side}

1. Cree entidades locales.
1. Vincule los destinatarios con los operadores que administran las entidades locales.

   ![](assets/mkg_dist_local_entity_association.png)

1. Especifique derechos y reglas de navegación para entidades locales
1. Especifique el conjunto de campos necesarios para la localización de la campaña:

   * definición de objetivos y tamaño máximo,
   * definición de contenido,
   * programación de ejecución (fecha de contacto y fecha de extracción), **solo para operadores locales**,
   * extensión de un esquema de solicitud con todos los campos adicionales necesarios.

1. Creación de un formulario web (Adobe o extranet) que le permita mostrar los parámetros de la localización, evaluar el objetivo y el presupuesto, así como previsualizar el contenido y aprobar la solicitud.

   Para **las campañas colaborativas (por aprobación de objetivo)**, cree la tabla donde se guardarán las aprobaciones de cada entidad local.

### Lado funcional del administrador {#functional-administrator-side}

Estos pasos deben llevarse a cabo al crear cada campaña.

1. Actualice el formulario con los campos utilizados para la localización de campañas.
1. Cree una instancia a partir de una plantilla de campaña adecuada (campaña de colaboración) o duplique la plantilla de campaña (campaña local).
1. Configure la campaña con los campos de localización y la referencia de formulario.
1. Publique la campaña.

### Lado del operador local {#local-operator-side}

Estos pasos deben llevarse a cabo para cada campaña.

1. Una vez que reciba la notificación de la disponibilidad del paquete de campañas, especifique la ubicación de la campaña (opcional).
1. Evalúe el objetivo, el presupuesto, etc.
1. Previsualice el contenido de la campaña.
1. Solicite la campaña.

