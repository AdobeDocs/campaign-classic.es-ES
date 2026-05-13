---
product: campaign
title: Inserción de un activo compartido
description: Inserción de un activo compartido
feature: Asset Sharing
audience: integrations
content-type: reference
topic-tags: asset-sharing
exl-id: 30a94bce-6d96-4a6d-a62f-7451c822f0e3
TQID: https://experienceleague.adobe.com/5SrvIw1sYSNd4Hw1we554AfxDj3VgeTeqIOOzTTrWuY
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
feature_v2:
  - id: d5ef99fa-df0c-4153-bf94-105ad0724167
source-git-commit: 4c295c0dabae8aba298390a3da2422a3fa1219f9
workflow-type: tm+mt
source-wordcount: 233
ht-degree: 100%

---

# Inserción de un activo compartido{#inserting-a-shared-asset}

Los activos compartidos desde Adobe Experience Cloud se pueden utilizar en los mensajes de correo electrónico y páginas de destino de la siguiente manera:

1. Cree un nuevo correo electrónico o una nueva página de destino.

   Si utiliza recursos de la biblioteca de recursos de Adobe Experience Manager, utilice una plantilla de envío creada al [configurar la integración](../../integrations/using/configuring-access-to-assets.md#integrating-with-aem-assets).

   Si no tiene esta plantilla específica, asegúrese de que en las **propiedades** de envío, la **[!UICONTROL Content editing mode]** (pestaña **[!UICONTROL Advanced]**) esté configurada como **DCE** y que se proporcione la cuenta externa de AEM que desea utilizar para acceder a la biblioteca de recursos de AEM Assets.

1. En la ventana de edición, seleccione la opción para añadir una imagen:

   * Si está utilizando el [modo de edición estándar](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/emails/defining-the-email-content.html?lang=es#adding-images){target="_blank"}, seleccione **[!UICONTROL Image]** > **[!UICONTROL Select a shared asset]**.

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
