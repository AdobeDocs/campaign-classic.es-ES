---
solution: Campaign Classic
product: campaign
title: Uso de una plantilla de contenido
description: Uso de una plantilla de contenido
audience: delivery
content-type: reference
topic-tags: content-management
exl-id: e43dd68e-2e95-4367-9029-4622fbcb1759
translation-type: ht
source-git-commit: 6854d06f8dc445b56ddfde7777f02916a60f2b63
workflow-type: ht
source-wordcount: '427'
ht-degree: 100%

---

# Uso de una plantilla de contenido{#using-a-content-template}

## Acerca de las plantillas de contenido {#about-content-templates}

Se puede hacer referencia a las plantillas de contenido, que se pueden utilizar en las entregas directamente. Consulte [Crear una entrega a través de la administración de contenido](#creating-a-delivery-via-content-management)

También pueden utilizarse para crear instancias de contenido. Una vez creadas, estas instancias están listas para ser entregadas (consulte [Entrega de una instancia de contenido](#delivering-a-content-instance)) o exportadas (consulte [Creación de una instancia de contenido](#creating-a-content-instance)).

## Creación de una entrega a través de la administración de contenido {#creating-a-delivery-via-content-management}

Puede hacer referencia a una plantilla de contenido en una entrega teniendo en cuenta el uso de campos de entrada para introducir contenido. Se añade una pestaña adicional al asistente de envíos para definir el contenido de la entrega.

![](assets/s_ncs_content_deliver_a_content.png)

El diseño se aplica automáticamente en función de la configuración seleccionada. Para verla, haga clic en el **[!UICONTROL HTML preview]** (o **[!UICONTROL Text preview]**) y seleccione un destinatario para probar los elementos de personalización.

![](assets/s_ncs_content_deliver_a_content_html.png)

Para obtener más información sobre esto, consulte el ejemplo de implementación completa: [Creación de contenido en el asistente de envío](../../delivery/using/use-case--creating-content-management.md#creating-content-in-the-delivery-wizard).

## Creación de una instancia de contenido {#creating-a-content-instance}

Puede crear contenido directamente en el árbol de Adobe Campaign para utilizarlo en flujos de trabajo, exportarlo o insertarlo directamente en nuevos envíos.

Siga estos pasos:

1. Seleccione el nodo **[!UICONTROL Resources > Contents]** del árbol, haga clic con el botón derecho y seleccione **[!UICONTROL Properties]**.

   ![](assets/s_ncs_content_folder_properties.png)

1. Seleccione las plantillas de publicación que desea activar para esta carpeta.

   ![](assets/s_ncs_content_folder_templates.png)

1. Ahora puede crear contenido nuevo mediante el botón **[!UICONTROL New]** de la lista de contenido.

   ![](assets/s_ncs_content_folder_create_a_template.png)

1. Introduzca los campos en el formulario.

   ![](assets/s_ncs_content_folder_use_a_template.png)

1. A continuación, haga clic en la pestaña **[!UICONTROL HTML preview]** para ver la renderización. Aquí, no se introducen los campos personalizados tomados de la base de datos.

   ![](assets/s_ncs_content_folder_use_a_template_preview.png)

1. Una vez creado, el contenido se añade a la lista de contenidos disponibles. Haga clic en el vínculo **[!UICONTROL Properties]** para cambiar su etiqueta, su estado o visualizar su historial.

   ![](assets/s_ncs_content_folder_template_properties.png)

1. Si es necesario, una vez aceptado el contenido, se puede generar mediante la pestaña correspondiente de la barra de herramientas.

   ![](assets/s_ncs_content_folder_template_generate.png)

   >[!NOTE]
   >
   >Se puede autorizar la generación de contenido no aceptado. Para ello, cambie la opción correspondiente en la plantilla de publicación. Para más información, consulte [Creación y configuración de la plantilla](../../delivery/using/publication-templates.md#creating-and-configuring-the-template).

   El HTML y los contenidos de texto se generan de forma predeterminada en la carpeta **publishing** de la instancia de Adobe Campaign. Se puede cambiar la carpeta de publicación gracias a la opción **NcmPublishingDir**.

## Entrega de una instancia de contenido {#delivering-a-content-instance}

Para crear y enviar una instancia de contenido, se debe vincular una plantilla de envío a la plantilla de publicación utilizada para generar dicho contenido. Para obtener más información, consulte [Entrega](../../delivery/using/publication-templates.md#delivery).

Además, la carpeta de almacenamiento de contenido debe estar dedicada a contenido tomado de esta plantilla de publicación (cuando una carpeta de contenido permite generar varios tipos de contenido, no se pueden crear envíos de forma automática).

Para crear la entrega de forma automática en función del contenido seleccionado, haga clic en el icono **[!UICONTROL Delivery]** y seleccione la plantilla.

![](assets/s_ncs_content_folder_create_the_delivery.png)

El contenido de texto y HTML se introduce automáticamente.
