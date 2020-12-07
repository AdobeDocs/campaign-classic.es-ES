---
solution: Campaign Classic
product: campaign
title: Inserción de un activo compartido
description: Inserción de un activo compartido
audience: integrations
content-type: reference
topic-tags: asset-sharing
translation-type: ht
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: ht
source-wordcount: '219'
ht-degree: 100%

---


# Inserción de un activo compartido{#inserting-a-shared-asset}

Los activos compartidos desde Adobe Experience Cloud se pueden utilizar en los mensajes de correo electrónico y páginas de aterrizaje de la siguiente manera:

1. Cree un nuevo correo electrónico o una nueva página de aterrizaje.

   Si utiliza recursos de la biblioteca de recursos de Adobe Experience Manager, utilice una plantilla de envío creada al [configurar la integración](../../integrations/using/configuring-access-to-assets.md#integrating-with-aem-assets).

   Si no tiene esta plantilla específica, asegúrese de que en las **propiedades** de envío, la **[!UICONTROL Content editing mode]** (pestaña **[!UICONTROL Advanced]**) esté configurada como **DCE** y que se proporcione la cuenta externa de AEM que desea utilizar para acceder a la biblioteca de recursos de AEM Assets.

1. En la ventana de edición, seleccione la opción para añadir una imagen:

   * Si está utilizando el [modo de edición estándar](../../delivery/using/defining-the-email-content.md#adding-images), seleccione **[!UICONTROL Image]** > **[!UICONTROL Select a shared asset]**.

      ![](assets/dam_insert_image_standard.png)

   * Si está utilizando el [modo de edición avanzado](../../web/using/about-campaign-html-editor.md) (DCE), vaya a un bloque de imagen y, a través del menú contextual, seleccione **[!UICONTROL Select a shared asset]**.

      ![](assets/dam_insert_image_dce.png)

      >[!NOTE]
      >
      >No se pueden insertar imágenes compartidas desde Adobe Campaign en el [acceso web](../../platform/using/adobe-campaign-workspace.md#console-and-web-access) al utilizar el DCE.

1. En la ventana de selección que se abre, seleccione una imagen y, a continuación, confirme la selección.

   Las imágenes disponibles provienen de la biblioteca de Adobe Experience Cloud o de la biblioteca de AEM Assets, según la configuración de la instancia de Adobe Campaign. Consulte la sección [Configuración del acceso a los recursos](../../integrations/using/configuring-access-to-assets.md) .

   ![](assets/dam_shared_image_selection.png)

>[!NOTE]
>
>Si se utiliza la integración con Adobe Target, se puede utilizar una imagen compartida como imagen predeterminada. Consulte [esta página](../../integrations/using/integrating-with-adobe-target.md).

