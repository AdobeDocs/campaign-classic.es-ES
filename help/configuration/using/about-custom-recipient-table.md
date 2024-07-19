---
product: campaign
title: Acerca de la tabla de destinatarios personalizada
description: Acerca de la tabla de destinatarios personalizada
feature: Configuration, Custom Resources
role: User, Data Engineer, Developer
badge-v8: label="También se aplica a v8" type="Positive" tooltip="También se aplica a Campaign v8"
exl-id: d8cea496-b3f3-420a-bf6e-b7cbb321b30d
source-git-commit: e34718caefdf5db4ddd61db601420274be77054e
workflow-type: tm+mt
source-wordcount: '676'
ht-degree: 3%

---

# Usar una tabla de destinatarios personalizada{#about-custom-recipient-table}

En esta sección se detallan los principios para utilizar una tabla de destinatarios personalizada (o externa).

De forma predeterminada, Adobe Campaign ofrece una tabla de destinatarios integrada a la que están vinculadas las funciones y los procesos predeterminados. La tabla de destinatarios integrada tiene una serie de campos y tablas predefinidos que se pueden ampliar fácilmente con una tabla de extensiones.

Si este método de extensión ofrece buena flexibilidad para ampliar una tabla, no permite reducir el número de campos o vínculos que contiene. El uso de una tabla no estándar o &quot;tabla de destinatarios externa&quot; permite una mayor flexibilidad, pero requiere ciertas precauciones al implementarla.

Esta funcionalidad permite a Adobe Campaign procesar datos de una base de datos externa: estos datos se utilizan como un conjunto de perfiles para las entregas. La implementación de este proceso implica varias precisiones que pueden ser relevantes según las necesidades del cliente. Por ejemplo:

* No hay flujo de actualización desde y hacia la base de datos de Adobe Campaign: los datos de esta tabla se pueden actualizar directamente a través del motor de base de datos que la aloja.
* No hay cambios en los procesos que operan en la base de datos existente.
* Uso de una base de datos de perfiles con una estructura no estándar: posibilidad de enviar a perfiles guardados en varias tablas con varias estructuras, con una sola instancia.
* No se requieren cambios ni mantenimiento al actualizar la base de datos de Adobe Campaign.
* La tabla de destinatarios integrada no es útil si no necesita la mayoría de los campos de tabla o si la plantilla de base de datos no está centrada en los destinatarios.
* Para ser eficaz, se necesita una tabla con pocos campos si tiene un número significativo de perfiles. La tabla de destinatarios integrada tiene demasiados campos para este caso específico.

En esta sección se describen los puntos clave que permiten asignar tablas existentes en Adobe Campaign y la configuración que se debe aplicar para ejecutar envíos basados en cualquier tabla. Por último, se describe cómo proporcionar a los usuarios interfaces de consulta tan prácticas como las disponibles con la tabla de destinatarios integrada. Para comprender el material presentado en esta sección, se requiere un buen conocimiento de los principios de diseño de pantalla y esquema.

## Recommendations y limitaciones {#recommendations-and-limitations}

El uso de una tabla de destinatarios personalizada tiene las siguientes limitaciones:

* Adobe Campaign no admite varios esquemas de destinatarios, conocidos como esquemas de segmentación, vinculados a los mismos esquemas de &quot;broadlog&quot; o de &quot;log&quot; de seguimiento. De lo contrario, esto puede provocar anomalías en la reconciliación de datos posteriormente.

  El gráfico siguiente detalla la estructura relacional necesaria para cada esquema de destinatario personalizado:
  ![](assets/custom_recipient_limitation.png)

  Recomendamos:

   * Dedicando los esquemas **[!UICONTROL nms:BroadLogRcp]** y **[!UICONTROL nms:TrackingLogRcp]** a **[!UICONTROL nms:Recipientschema]** de forma predeterminada. Estas dos tablas de registro no deben vincularse a ninguna tabla de destinatarios personalizada adicional.
   * Definición de esquemas de &quot;broadlog&quot; y de &quot;log&quot; de seguimiento personalizados específicos para cada nuevo esquema de destinatario personalizado. Esto se puede hacer automáticamente al configurar la asignación de destino, consulte [Asignación de destino](../../configuration/using/target-mapping.md).

* No puede usar el estándar **[!UICONTROL Services and Subscriptions]** ofrecido en el producto.

  Esto significa que la operación general detallada en [esta sección](../../delivery/using/managing-subscriptions.md) no es aplicable.

* El vínculo con la tabla **[!UICONTROL visitor]** no funciona.

  Por lo tanto, para utilizar el módulo **[!UICONTROL Social Marketing]** debe configurar el paso de almacenamiento para hacer referencia a la tabla correcta.

  Del mismo modo, cuando se utilizan funciones de referencia, se debe adaptar la plantilla de transferencia de mensajes inicial estándar.

* No puede añadir perfiles manualmente a una lista.

  Por lo tanto, el procedimiento detallado en [esta sección](../../platform/using/creating-and-managing-lists.md) no es aplicable sin una configuración adicional.

  >[!NOTE]
  >
  >Puede seguir creando listas de destinatarios mediante flujos de trabajo. Para obtener más información, consulte [Creación de una lista de perfiles con un flujo de trabajo](../../configuration/using/creating-a-profile-list-with-a-workflow.md).

También recomendamos comprobar los valores predeterminados utilizados en las diferentes configuraciones predeterminadas: según las funcionalidades utilizadas, se deben llevar a cabo varias adaptaciones.

Por ejemplo:

* Deben redesarrollarse ciertos informes estándar, en particular los ofrecidos por **Interaction** y **Mobile Applications**. Consulte la sección [Administración de informes](../../configuration/using/managing-reports.md).
* Las configuraciones predeterminadas para determinadas actividades de flujo de trabajo hacen referencia a la tabla de destinatarios estándar (**[!UICONTROL nms:recipient]**): estas configuraciones deben cambiarse cuando se utilizan para una tabla de destinatarios externa. Consulte la sección [Administración de flujos de trabajo](../../configuration/using/managing-workflows.md).
* Se debe adaptar el bloque personalizado estándar **[!UICONTROL Unsubscription link]**.
* Se debe modificar la asignación de destino de las plantillas de envío estándar.
* Los formularios V4 no son compatibles para su uso con una tabla de destinatarios externa: debe utilizar aplicaciones web.
