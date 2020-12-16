---
solution: Campaign Classic
product: campaign
title: Creación de una plantilla de envíos
description: Creación de una plantilla de envíos
audience: delivery
content-type: reference
topic-tags: using-delivery-templates
translation-type: ht
source-git-commit: 6335c1cd327a83dbc8c4d43c4ab795b84531c3e1
workflow-type: ht
source-wordcount: '378'
ht-degree: 100%

---


# Creación de una plantilla de envíos{#creating-a-delivery-template}

![](assets/do-not-localize/how-to-video.png) [Descubra esta función en vídeo](#delivery-template-video)

## Conversión de una entrega existente en una plantilla {#converting-an-existing-delivery-to-a-template}

Puede convertir una entrega en una plantilla y usarla con las nuevas acciones de envío repetidas. Para convertir una entrega en una plantilla, selecciónelo en la lista de envío, desde el nodo del árbol **[!UICONTROL Campaign management]**.

Haga clic con el botón derecho y seleccione **[!UICONTROL Actions > Save as template...]**.

![](assets/s_ncs_user_campaign_save_as_scenario.png)

Esta acción crea una plantilla de envío a partir de la entrega seleccionado. Debe introducir la carpeta donde se almacena (en el campo **[!UICONTROL Folder]**), así como la carpeta donde se generan las entregas basados en esta plantilla (en el campo **[!UICONTROL Execution folder]**).

![](assets/s_ncs_user_campaign_save_as_scenario_a.png)

Para obtener más información sobre el modo de configuración, consulte [Vinculación de la plantilla a una entrega](../../delivery/using/creating-a-delivery-from-a-template.md#linking-the-template-to-a-delivery).

## Creación de una nueva plantilla {#creating-a-new-template}

Para configurar una plantilla de envío, siga los siguientes pasos:

1. Abra el explorador de Campaign.
1. En la carpeta **Recursos**, seleccione **Plantilla** y luego **Plantillas de envío**.

   ![](assets/delivery_template_1.png)

1. Haga clic en **Nueva** en la barra de herramientas para crear una nueva plantilla de envío.

   ![](assets/delivery_template_2.png)

1. Modifique la **Etiqueta** y el **Nombre interno** de la carpeta.
1. Guarde la plantilla y vuelva a abrirla.
1. Haga clic en el botón **Propiedades** y, a continuación, modifique los valores según sus necesidades.

   ![](assets/delivery_template_3.png)

1. En la pestaña **General**, confirme o cambie las ubicaciones seleccionadas en los menús desplegables **Carpeta de ejecución**, **Carpeta** y **Enrutamiento**.

   ![](assets/delivery_template_4.png)

1. Rellene la categoría **parámetros de correo electrónico** con el asunto del correo electrónico y la población objetivo.
1. Añada el **contenido HTML** para personalizar la plantilla. Puede mostrar un vínculo a una página espejo y un vínculo para darse de baja.
1. Seleccione la pestaña **Preview.** En el menú desplegable **Personalización de prueba**, seleccione **Destinatario** para previsualizar la plantilla como el perfil elegido.

   ![](assets/delivery_template_5.png)

1. Haga clic en **Save**. La plantilla ya está lista para utilizarse en una entrega.

>[!NOTE]
>
>Para evitar errores de configuración, se recomienda duplicar una plantilla nativa y modificar sus propiedades en lugar de crear una nueva plantilla.

## Videotutoriales {#delivery-template-video}

### Configuración de una plantilla de envíos

En el siguiente vídeo se muestra cómo configurar una plantilla para un envío ad hoc.

>[!VIDEO](https://video.tv.adobe.com/v/24066?quality=12&captions=spa)

### Configuración de propiedades de plantillas de envíos

El siguiente vídeo muestra cómo configurar las propiedades de las plantillas de envíos y explica cada propiedad en detalle.

>[!VIDEO](https://video.tv.adobe.com/v/24067?quality=12&captions=spa)

### Implementación de una plantilla de envíos ad-hoc

En este vídeo se explica cómo implementar una plantilla de envíos de correo electrónico ad-hoc, y se explica la diferencia entre un envío de correo electrónico y un flujo de trabajo de envío.

>[!VIDEO](https://video.tv.adobe.com/v/24065?quality=12&captions=spa)

Hay disponibles más vídeos de procedimientos para Campaign Classic [aquí](https://experienceleague.adobe.com/docs/campaign-classic-learn/tutorials/overview.html?lang=es).