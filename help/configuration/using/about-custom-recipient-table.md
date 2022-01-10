---
product: campaign
title: Acerca de la tabla de destinatarios personalizada
description: Acerca de la tabla de destinatarios personalizada
audience: configuration
content-type: reference
topic-tags: use-a-custom-recipient-table
exl-id: d8cea496-b3f3-420a-bf6e-b7cbb321b30d
source-git-commit: fb4b4c42b907e86813ea570f912312fccf893bfe
workflow-type: tm+mt
source-wordcount: '667'
ht-degree: 2%

---

# Usar una tabla de destinatarios personalizada{#about-custom-recipient-table}

![](../../assets/common.svg)

Esta sección detalla los principios para utilizar una tabla de destinatarios personalizada (o externa).

De forma predeterminada, Adobe Campaign ofrece una tabla de destinatarios integrada a la que se vinculan funciones y procesos integrados. La tabla de destinatarios integrada tiene una serie de campos predefinidos y tablas que se pueden ampliar fácilmente con una tabla de extensiones.

Si este método de extensión ofrece una buena flexibilidad para ampliar una tabla, no permite reducir el número de campos o vínculos que contiene. El uso de una tabla no estándar, o &quot;tabla de destinatarios externa&quot;, permite una buena flexibilidad, pero requiere ciertas precauciones al implementarla.

Esta funcionalidad permite a Adobe Campaign procesar datos desde una base de datos externa: estos datos se utilizan como un conjunto de perfiles para las entregas. La implementación de este proceso implica varias precisiones que pueden ser relevantes según las necesidades del cliente. Por ejemplo:

* Sin flujo de actualización de la base de datos de Adobe Campaign: los datos de esta tabla se pueden actualizar directamente a través del motor de base de datos que lo aloja.
* No hay cambios en los procesos que funcionan en la base de datos existente.
* Uso de una base de datos de perfiles con una estructura no estándar: posibilidad de enviar a perfiles guardados en varias tablas con varias estructuras, utilizando una sola instancia.
* No se requiere ningún cambio ni mantenimiento al actualizar la base de datos de Adobe Campaign.
* La tabla de destinatarios integrada no es útil si no necesita la mayoría de los campos de tabla o si la plantilla de base de datos no está centrada en los destinatarios.
* Para ser eficaz, se necesita una tabla con pocos campos si tiene un número significativo de perfiles. La tabla de destinatarios integrada tiene demasiados campos para este caso específico.

En esta sección se describen los puntos clave que le permiten asignar tablas existentes en Adobe Campaign y la configuración que se debe aplicar para ejecutar entregas en función de cualquier tabla. Por último, describe cómo proporcionar a los usuarios interfaces de consulta tan prácticas como las disponibles con la tabla de destinatarios integrada. Para entender el material presentado en esta sección, se requiere un buen conocimiento de los principios de diseño de pantalla y esquema.

## Recommendations y limitaciones {#recommendations-and-limitations}

El uso de una tabla de destinatarios personalizada tiene las siguientes limitaciones:

* Adobe Campaign no admite varios esquemas de destinatarios, conocidos como esquemas de segmentación, vinculados a los mismos esquemas de broadlog o trackinglog. De lo contrario, esto puede provocar anomalías en la reconciliación de datos posteriormente.

   El gráfico siguiente detalla la estructura relacional necesaria para cada esquema de destinatario personalizado:
   ![](assets/custom_recipient_limitation.png)

   Recomendamos:

   * Dedicando el **[!UICONTROL nms:BroadLogRcp]** y **[!UICONTROL nms:TrackingLogRcp]** esquemas predeterminados **[!UICONTROL nms:Recipientschema]**. Estas dos tablas de registro no deben estar vinculadas a ninguna tabla de destinatarios personalizada adicional.
   * Definición de esquemas personalizados específicos de broadlog y trackinglog para cada nuevo esquema de destinatario personalizado. Esto se puede hacer automáticamente al configurar la asignación de destino, consulte [Asignación de destino](../../configuration/using/target-mapping.md).

* No puede usar el estándar **[!UICONTROL Services and Subscriptions]** en el producto.

   Esto significa que la operación general detallada en [esta sección](../../delivery/using/managing-subscriptions.md) no es aplicable.

* El vínculo con la variable **[!UICONTROL visitor]** no funciona.

   Por lo tanto, para usar la variable **[!UICONTROL Social Marketing]** debe configurar el paso de almacenamiento para hacer referencia a la tabla correcta.

   Del mismo modo, al utilizar funciones de referente, se debe adaptar la plantilla estándar de transferencia de mensajes iniciales.

* No puede añadir perfiles manualmente en una lista.

   Por lo tanto, el procedimiento detallado en [esta sección](../../platform/using/creating-and-managing-lists.md) no es aplicable sin una configuración adicional.

   >[!NOTE]
   >
   >Puede seguir creando listas de destinatarios mediante flujos de trabajo. Para obtener más información, consulte [Creación de una lista de perfiles con un flujo de trabajo](../../configuration/using/creating-a-profile-list-with-a-workflow.md).

También se recomienda comprobar los valores predeterminados utilizados en las diferentes configuraciones integradas: según las funcionalidades utilizadas, se deben realizar varias adaptaciones.

Por ejemplo:

* Algunos informes estándar, en particular los que ofrece **Interacción** y **Aplicaciones móviles** debe redesarrollarse. Consulte la [Administración de informes](../../configuration/using/managing-reports.md) para obtener más información.
* Las configuraciones predeterminadas para ciertas actividades de flujo de trabajo hacen referencia a la tabla de destinatarios estándar (**[!UICONTROL nms:recipient]**): estas configuraciones deben cambiarse cuando se utilizan en una tabla de destinatarios externos. Consulte la [Administración de flujos de trabajo](../../configuration/using/managing-workflows.md) para obtener más información.
* La **[!UICONTROL Unsubscription link]** el bloque personalizado debe estar adaptado.
* Se debe modificar la asignación de destino de las plantillas de envío estándar.
* Los formularios V4 no son compatibles con una tabla de destinatarios externa: debe utilizar aplicaciones web.
