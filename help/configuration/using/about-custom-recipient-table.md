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
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 668a0093616e1a2b49623b010ae5055f4d43d9b9

---


# Acerca de la tabla de destinatarios personalizada{#about-custom-recipient-table}

Esta sección detalla los principios para utilizar una tabla de destinatarios no estándar.

De forma predeterminada, Adobe Campaign ofrece una tabla de destinatarios estándar a la que están vinculados las funciones y los procesos predeterminados. La tabla de destinatario estándar tiene una serie de campos y tablas predefinidos que se pueden ampliar fácilmente con una tabla de extensión.

Si este método de extensión ofrece una buena flexibilidad para ampliar una tabla, no permite reducir el número de campos o vínculos que contiene. El uso de una tabla no estándar, o &quot;tabla de destinatarios externos&quot;, permite una mayor flexibilidad pero requiere ciertas precauciones al implementarla.

## Precisiones {#precisions}

Esta funcionalidad permite a Adobe Campaign procesar datos desde una base de datos externa: estos datos se utilizarán como un conjunto de perfiles para las entregas. La implementación de este proceso implica varias precisiones que pueden ser relevantes según las necesidades del cliente. Por ejemplo:

* Sin flujo de actualización de la base de datos de Adobe Campaign: los datos de esta tabla se pueden actualizar directamente a través del motor de base de datos que los aloja.
* No hay cambios en los procesos que funcionan en la base de datos existente.
* Uso de una base de datos de perfiles con una estructura no estándar: posibilidad de entrega a perfiles guardados en varias tablas con varias estructuras, utilizando una sola instancia.
* No se requieren cambios ni mantenimiento al actualizar la base de datos de Adobe Campaign.
* La tabla de destinatario estándar no es útil si no necesita la mayoría de los campos de la tabla o si la plantilla de base de datos no está centrada en los destinatarios.
* Para ser eficaz, se necesita una tabla con pocos campos si tiene un número significativo de perfiles. La tabla del destinatario estándar tiene demasiados campos para este caso específico.

En esta sección se describen los puntos clave que le permiten asignar tablas existentes en Adobe Campaign y la configuración que se aplicará para ejecutar entregas en función de cualquier tabla. Por último, se describe cómo proporcionar a los usuarios interfaces de consulta tan prácticas como las disponibles en la tabla de destinatarios estándar. Para entender el material presentado en esta sección, se requiere un buen conocimiento de los principios de diseño de pantalla y esquema.

## Recomendaciones y limitaciones {#recommendations-and-limitations}

El uso de una tabla de destinatarios externos tiene las siguientes limitaciones:

* Adobe Campaign no admite esquemas de varios destinatarios, conocidos como esquemas de objetivo, vinculados a los mismos esquemas de registro de inicio y/o seguimiento. De lo contrario, esto puede provocar anomalías en la reconciliación de datos posteriormente.

   El gráfico siguiente detalla la estructura relacional requerida para cada esquema de destinatario personalizado:
   ![](assets/custom_recipient_limitation.png)

   Recomendamos:

   * Dedicar los esquemas **[!UICONTROL nms:BroadLogRcp]** y **[!UICONTROL nms:TrackingLogRcp]** a los esquemas predeterminados **[!UICONTROL nms:Recipientschema]**. Estas dos tablas de registro no deben estar vinculadas a ninguna tabla de destinatario personalizada adicional.
   * Definición de esquemas personalizados de registro de seguimiento y registro de banda ancha dedicados para cada nuevo esquema de destinatario personalizado. Esto se puede hacer automáticamente al configurar la asignación de objetivos, consulte Asignación [de objetivos](../../configuration/using/target-mapping.md).

* No puede usar el estándar **[!UICONTROL Services and Subscriptions]** ofrecido en el producto.

   Esto significa que no es aplicable la operación general que se detalla en [esta sección](../../delivery/using/managing-subscriptions.md) .

* El vínculo con la **[!UICONTROL visitor]** tabla no funciona.

   Por lo tanto, para utilizar el módulo **[!UICONTROLSSocial Marketing]** debe configurar el paso de almacenamiento para que haga referencia a la tabla correcta.

   Del mismo modo, al utilizar funciones de referencia, se debe adaptar la plantilla de transferencia de mensajes inicial estándar.

* No se pueden agregar perfiles manualmente en una lista.

   Por lo tanto, el procedimiento detallado en [esta sección](../../platform/using/creating-and-managing-lists.md) no es aplicable sin una configuración adicional.

   >[!NOTE]
   >
   >Todavía puede crear listas de destinatarios mediante flujos de trabajo. Para obtener más información sobre esto, consulte [Creación de una lista de perfiles con un flujo de trabajo](../../configuration/using/creating-a-profile-list-with-a-workflow.md).

También se recomienda comprobar los valores predeterminados que se utilizan en las diferentes configuraciones integradas: en función de las funcionalidades utilizadas, se deben realizar varias adaptaciones.

Por ejemplo:

* Es preciso redesarrollar algunos informes estándar, en particular los que ofrecen la **interacción** y las aplicaciones **** móviles. Consulte la sección [Administración de informes](../../configuration/using/managing-reports.md) .
* Las configuraciones predeterminadas para determinadas actividades de flujo de trabajo hacen referencia a la tabla de destinatarios estándar (**[!UICONTROL nms:recipient]**): estas configuraciones deben cambiarse cuando se utilizan en una tabla de destinatarios externos. Consulte la sección [Administración de flujos de trabajo](../../configuration/using/managing-workflows.md) .
* Se debe adaptar el bloque de personalización estándar **[!UICONTROL Unsubscription link]** .
* Se debe modificar la asignación de objetivos de las plantillas de entrega estándar.
* Los formularios V4 no son compatibles con una tabla de destinatarios externos: debe utilizar aplicaciones Web.

