---
title: Configuración del acceso a Assets
seo-title: Configuración del acceso a Assets
description: Configuración del acceso a Assets
seo-description: null
page-status-flag: never-activated
uuid: dc8c0016-92c8-41ab-98c6-d0fe0bfd6c41
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: integrations
content-type: reference
topic-tags: asset-sharing
discoiquuid: df1b6ead-3471-404a-b43f-a68fb86cb14c
translation-type: tm+mt
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: tm+mt
source-wordcount: '571'
ht-degree: 94%

---


# Configuración del acceso a Assets{#configuring-access-to-assets}

Esta sección detalla los pasos de configuración necesarios en Adobe Campaign para utilizar las funcionalidades de integración con el servicio principal de Assets o la biblioteca de activos de Adobe Experience Manager.

>[!CAUTION]
>
>Estas integraciones son simultáneas. Lea detenidamente la siguiente información antes de realizar cualquier configuración.

* Integración con **Experience Cloud Assets**: Esta integración permite insertar imágenes desde la biblioteca de Adobe Experience Cloud. Según la configuración y el modelo de licencia, esta biblioteca puede ser el servicio principal de Assets o Assets on Demand. Esta integración debe configurarse instalando el paquete integrado **[!UICONTROL Integration with the Adobe Experience Cloud]** en Adobe Campaign.
* Integración con **AEM Assets**: esta integración permite insertar imágenes de la biblioteca de recursos de Adobe Experience Manager. Esta integración debe configurarse instalando el paquete integrado **[!UICONTROL AEM Integration]** en Adobe Campaign.

>[!NOTE]
>
>If the two packages (**[!UICONTROL AEM Integration]** and **[!UICONTROL Integration with the Adobe Experience Cloud]** ) are installed, only the assets available in the Adobe Experience Cloud library can be used. Para acceder también a los recursos de la biblioteca AEM Assets, se deben sincronizar AEM Assets y Adobe Experience Cloud. Los recursos de AEM Assets también están disponibles en la biblioteca de Adobe Experience Cloud. Para obtener más información sobre la sincronización de AEM Assets y Adobe Experience Cloud, consulte la [documentación detallada](https://docs.adobe.com/docs/en/aod/overview/collaborating/aem-assets-aod-sync.html).

## Integración con Experience Cloud Assets {#integrating-with-experience-cloud-assets}

Para utilizar la integración entre Adobe Campaign y Experience Cloud Assets, debe contar con:

* Una organización de Adobe Experience Cloud.
* El modo de autentificación Adobe IMS activado

Para activar la conexión entre Adobe Campaign y Adobe Experience Cloud, configure la conexión mediante IMS (servicio de conexión con Adobe ID). Esta configuración se detalla en el documento de [Conexión mediante una Adobe ID. ](../../integrations/using/about-adobe-id.md) Requiere:

* Installing the **[!UICONTROL Integration with the Adobe Experience Cloud]** package.
* Configuración de una cuenta externa de Adobe Experience Cloud.

>[!NOTE]
>
>Las funcionalidades vinculadas a esta integración solo están disponibles para los usuarios conectados con su Adobe ID a través de IMS.

## Integración con AEM Assets {#integrating-with-aem-assets}

Para integrar AEM Assets con Adobe Campaign, primero se debe configurar la integración entre Adobe Experience Manager y Adobe Campaign. Esta configuración requiere principalmente:

* Installing the **[!UICONTROL AEM Integration]** built-in package
* La configuración de una cuenta externa específica de Adobe Experience Manager.

Aprenda a integrar Adobe Campaign y Adobe Experience Manager consultando la [documentación detallada](../../integrations/using/about-adobe-experience-manager.md).

Una vez configurada esta integración, se puede configurar una nueva plantilla de distribución en Adobe Campaign para utilizar la biblioteca de AEM Assets. Para realizar esto, siga los pasos a continuación:

1. Cree una nueva plantilla de distribución o duplique una existente. Para obtener más información sobre plantillas de envío, consulte [esta página](../../delivery/using/about-templates.md).
1. Edite las **propiedades** de esta plantilla.
1. In the **[!UICONTROL Advanced]** tab, set the **[!UICONTROL Content editing mode]** to **DCE**.
1. Seleccione la **[!UICONTROL AEM account]** externa que necesita utilizar para acceder a la biblioteca de AEM Assets.

   ![](assets/dam_aem_assets1.png)

Al insertar imágenes en el contenido de una entrega basándose en esta plantilla, la opción **[!UICONTROL Select a shared asset]** permite examinar las imágenes en la biblioteca de AEM Assets. Obtenga más información en [esta sección](../../integrations/using/inserting-a-shared-asset.md).

>[!NOTE]
>
>Si el paquete **[!UICONTROL Integration with the Adobe Experience Cloud]** también está instalado en la instancia de Adobe Campaign, solo podrá utilizar los recursos disponibles en la biblioteca de Adobe Experience Cloud. Para acceder también a los recursos de la biblioteca AEM Assets, se deben sincronizar AEM Assets y Adobe Experience Cloud. Los recursos de AEM Assets también están disponibles en la biblioteca de Adobe Experience Cloud. En este caso, no es necesario crear una plantilla de envío específica. Para obtener más información sobre la sincronización entre AEM Assets y Adobe Experience Cloud, consulte la [documentación detallada](https://docs.adobe.com/docs/en/aod/overview/collaborating/aem-assets-aod-sync.html).

