---
product: campaign
title: Configuración del acceso a Assets
description: Configuración del acceso a Assets
audience: integrations
content-type: reference
topic-tags: asset-sharing
exl-id: f3897a40-b080-47e5-9e31-4d861c1bacd5
source-git-commit: 84312974b9b7372c8a46fd1c7ead1148690bcd83
workflow-type: tm+mt
source-wordcount: '499'
ht-degree: 84%

---

# Configuración del acceso a Assets{#configuring-access-to-assets}

![](../../assets/common.svg)

Esta sección detalla los pasos de configuración necesarios en Adobe Campaign para utilizar las funcionalidades de integración con el servicio principal de Assets o la biblioteca de Adobe Experience Manager Assets (AEM Assets).

>[!CAUTION]
>
>Estas integraciones son simultáneas. Lea detenidamente la siguiente información antes de realizar cualquier configuración.

* Integración con **Experience Cloud Assets**: Esta integración permite insertar imágenes desde la biblioteca de Adobe Experience Cloud. Esta integración debe configurarse instalando el paquete integrado **[!UICONTROL Integration with the Adobe Experience Cloud]** en Adobe Campaign.
* Integración con **AEM Assets**: esta integración permite insertar imágenes de la biblioteca de Adobe Experience Manager Assets. Esta integración debe configurarse instalando el paquete integrado **[!UICONTROL AEM Integration]** en Adobe Campaign. Tenga en cuenta que esta integración ya no está disponible a partir de Adobe Experience Manager 6.4.

>[!NOTE]
>
>Si se instalan los dos paquetes (**[!UICONTROL AEM Integration]** y **[!UICONTROL Integration with the Adobe Experience Cloud]**), solo se podrán utilizar los activos disponibles en la biblioteca de Adobe Experience Cloud.

## Integración con Experience Cloud Assets {#integrating-with-experience-cloud-assets}

Para utilizar la integración entre Adobe Campaign y Experience Cloud Assets, debe contar con:

* Una organización de Adobe Experience Cloud.
* El modo de autentificación Adobe IMS activado

Para activar la conexión entre Adobe Campaign y Adobe Experience Cloud, configure la conexión mediante IMS (servicio de conexión con Adobe ID). Esta configuración se detalla en el documento de [Conexión mediante una Adobe ID. ](../../integrations/using/about-adobe-id.md) Requiere:

* Instale el paquete **[!UICONTROL Integration with the Adobe Experience Cloud]**.
* Configuración de una cuenta externa de Adobe Experience Cloud.

>[!NOTE]
>
>Las funcionalidades vinculadas a esta integración solo están disponibles para los usuarios conectados con su Adobe ID a través de IMS.

## Integración con AEM Assets {#integrating-with-aem-assets}


>[!CAUTION]
>
>Esta funcionalidad se ha eliminado a partir de Adobe Experience Manager 6.4. [Más información](https://experienceleague.adobe.com/docs/experience-manager-64/release-notes/deprecated-removed-features.html?lang=en#removed-features)

Para integrar AEM Assets con Adobe Campaign, primero se debe configurar la integración entre Adobe Experience Manager y Adobe Campaign. Esta configuración requiere principalmente:

* La instalación del paquete integrado **[!UICONTROL AEM Integration]**.
* La configuración de una cuenta externa específica de Adobe Experience Manager.

Aprenda a integrar Adobe Campaign y Adobe Experience Manager consultando la [documentación detallada](../../integrations/using/about-adobe-experience-manager.md).

Una vez configurada esta integración, se puede configurar una nueva plantilla de distribución en Adobe Campaign para utilizar la biblioteca de AEM Assets. Para realizar esto, siga los pasos a continuación:

1. Cree una nueva plantilla de distribución o duplique una existente. Para obtener más información sobre plantillas de envío, consulte [esta página](../../delivery/using/about-templates.md).
1. Edite las **propiedades** de esta plantilla.
1. En la pestaña **[!UICONTROL Advanced]**, configure **[!UICONTROL Content editing mode]** en **DCE**.
1. Seleccione la **[!UICONTROL AEM account]** externa que necesita utilizar para acceder a la biblioteca de AEM Assets.

   ![](assets/dam_aem_assets1.png)

Al insertar imágenes en el contenido de una entrega basándose en esta plantilla, la opción **[!UICONTROL Select a shared asset]** permite examinar las imágenes en la biblioteca de AEM Assets. Obtenga más información en [esta sección](../../integrations/using/inserting-a-shared-asset.md).

>[!NOTE]
>
>Si el paquete **[!UICONTROL Integration with the Adobe Experience Cloud]** también está instalado en la instancia de Adobe Campaign, solo podrá utilizar los recursos disponibles en la biblioteca de Adobe Experience Cloud. Para acceder también a los recursos de la biblioteca AEM Assets, se deben sincronizar AEM Assets y Adobe Experience Cloud. Los recursos de AEM Assets también están disponibles en la biblioteca de Adobe Experience Cloud. En este caso, no es necesario crear una plantilla de envío específica.
