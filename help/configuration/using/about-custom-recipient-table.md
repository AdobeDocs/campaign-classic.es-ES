---
title: Acerca de la tabla de destinatarios personalizada
seo-title: Acerca de la tabla de destinatarios personalizada
description: Acerca de la tabla de destinatarios personalizada
seo-description: null
page-status-flag: never-activated
uuid: 4b162da4-90d2-44ff-9f89-ff0275540359
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: configuration
content-type: reference
topic-tags: use-a-custom-recipient-table
discoiquuid: c3ff8462-e47e-4637-8213-769fdeb86a57
translation-type: tm+mt
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: tm+mt
source-wordcount: '669'
ht-degree: 2%

---


# Acerca de la tabla de destinatarios personalizada{#about-custom-recipient-table}

Esta sección detalla los principios para utilizar una tabla de destinatario no estándar.

De forma predeterminada, Adobe Campaign oferta una tabla de destinatario estándar a la que están vinculados las funciones y los procesos predeterminados. La tabla de destinatario estándar tiene una serie de campos y tablas predefinidos que se pueden ampliar fácilmente con una tabla de extensión.

Si este método de extensión oferta una buena flexibilidad para extender una tabla, no permite reducir el número de campos o vínculos que contiene. El uso de una tabla no estándar, o &quot;tabla de destinatario externo&quot;, permite una buena flexibilidad, pero requiere ciertas precauciones al implementarla.

## Precisiones {#precisions}

Esta funcionalidad permite a Adobe Campaign procesar datos desde una base de datos externa: estos datos se utilizarán como un conjunto de perfiles para envíos. La implementación de este proceso implica varias precisiones que pueden ser relevantes según las necesidades del cliente. Por ejemplo:

* Sin flujo de actualización de la base de datos de Adobe Campaign: los datos de esta tabla se pueden actualizar directamente a través del motor de base de datos que los aloja.
* No hay cambios en los procesos que funcionan en la base de datos existente.
* Uso de una base de datos de perfil con una estructura no estándar: posibilidad de entrega a perfiles guardados en varias tablas con varias estructuras, utilizando una sola instancia.
* No se requieren cambios ni mantenimiento al actualizar la base de datos de Adobe Campaign.
* La tabla de destinatario estándar es inútil si no necesita la mayoría de los campos de tabla o si la plantilla de base de datos no está centrada en los destinatarios.
* Para ser eficaz, se necesita una tabla con pocos campos si tiene un número significativo de perfiles. La tabla de destinatario estándar tiene demasiados campos para este caso específico.

En esta sección se describen los puntos clave que le permiten asignar tablas existentes en Adobe Campaign y la configuración que se va a aplicar para ejecutar envíos en función de cualquier tabla. Por último, se describe cómo proporcionar a los usuarios interfaces de consulta tan prácticas como las disponibles en la tabla de destinatario estándar. Para entender el material presentado en esta sección, se requiere un buen conocimiento de los principios de diseño de pantalla y esquema.

## Recommendations y limitaciones {#recommendations-and-limitations}

El uso de una tabla de destinatario externa tiene las siguientes limitaciones:

* Adobe Campaign no admite varios esquemas de destinatario, conocidos como esquemas de objetivo, vinculados a los mismos esquemas de registro de seguimiento y/o de banda ancha. De lo contrario, esto puede provocar anomalías en la reconciliación de datos posteriormente.

   El gráfico siguiente detalla la estructura relacional requerida para cada esquema de destinatario personalizado:
   ![](assets/custom_recipient_limitation.png)

   Recomendamos:

   * Dedicar los **[!UICONTROL nms:BroadLogRcp]** esquemas y **[!UICONTROL nms:TrackingLogRcp]** los listos para usar **[!UICONTROL nms:Recipientschema]**. Estas dos tablas de registro no deben estar vinculadas a ninguna tabla de destinatario personalizada adicional.
   * Definición de esquemas personalizados y de registro de seguimiento para cada nuevo esquema de destinatario personalizado. Esto se puede hacer automáticamente al configurar la asignación de destino, consulte [Asignación de destino](../../configuration/using/target-mapping.md).

* No puede usar el estándar **[!UICONTROL Services and Subscriptions]** ofrecido en el producto.

   Esto significa que no es aplicable la operación general que se detalla en [esta sección](../../delivery/using/managing-subscriptions.md) .

* El vínculo con la **[!UICONTROL visitor]** tabla no funciona.

   Por lo tanto, para utilizar el **[!UICONTROL Social Marketing]** módulo debe configurar el paso de almacenamiento para que haga referencia a la tabla correcta.

   Del mismo modo, al utilizar funciones de referencia, se debe adaptar la plantilla de transferencia de mensajes inicial estándar.

* No se pueden agregar perfiles manualmente en una lista.

   Por lo tanto, el procedimiento detallado en [esta sección](../../platform/using/creating-and-managing-lists.md) no es aplicable sin una configuración adicional.

   >[!NOTE]
   >
   >Todavía puede crear listas de destinatario mediante flujos de trabajo. Para obtener más información sobre esto, consulte [Creación de una lista de perfil con un flujo de trabajo](../../configuration/using/creating-a-profile-list-with-a-workflow.md).

También se recomienda comprobar los valores predeterminados que se utilizan en las diferentes configuraciones integradas: en función de las funcionalidades utilizadas, se deben realizar varias adaptaciones.

Por ejemplo:

* Es preciso redesarrollar algunos informes estándar, en particular los que ofrecen la **interacción** y las aplicaciones **** móviles. Consulte la sección [Administración de informes](../../configuration/using/managing-reports.md) .
* Las configuraciones predeterminadas para determinadas actividades de flujo de trabajo hacen referencia a la tabla de destinatarios estándar (**[!UICONTROL nms:recipient]**): estas configuraciones deben cambiarse cuando se utilizan en una tabla de destinatarios externos. Consulte la sección [Administración de flujos de trabajo](../../configuration/using/managing-workflows.md) .
* Se debe adaptar el bloque de personalización estándar **[!UICONTROL Unsubscription link]** .
* Debe modificarse la asignación de destino de las Plantillas de envíos estándar.
* Los formularios V4 no son compatibles con una tabla de destinatarios externos: debe usar Aplicaciones web.

