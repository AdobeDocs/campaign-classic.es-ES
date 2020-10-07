---
title: Configuración de la integración con Adobe Target
seo-title: Configuración de la integración con Adobe Target
description: Configuración de la integración con Adobe Target
seo-description: null
page-status-flag: never-activated
uuid: b9337e92-e4e5-4cba-a559-75db7460d5c5
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: integrations
content-type: reference
topic-tags: adobe-target
discoiquuid: 378d5ff9-88c0-43f1-beb8-454701e9f1d1
translation-type: tm+mt
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: tm+mt
source-wordcount: '181'
ht-degree: 91%

---


# Configuración de la integración con Adobe Target{#configuring-the-integration-with-adobe-target}

## Requisitos previos {#prerequisites}

Para utilizar la integración entre Adobe Campaign y Adobe Target, debe tener:

* Organizaciones de Adobe Experience Cloud y Adobe Target
* Un “rawbox” de Adobe Target determinada para establecer la conexión con Adobe Campaign

## Configuración de Adobe Campaign {#configuring-adobe-campaign}

Para configurar Adobe Campaign:

1. Install the **[!UICONTROL Integration with the Adobe Experience Cloud]** standard package. La instalación de un paquete de integración es igual que la instalación de un paquete estándar, que se detalla en la sección de [Importación de paquete. ](../../platform/using/working-with-data-packages.md#importing-packages) Esto le permite acceder a los activos compartidos a través del Digital Asset Manager.
1. Permita la conexión mediante IMS (servicio de conexión con Adobe ID) para utilizar imágenes compartidas mediante Adobe Experience Cloud en sus correos electrónicos. Consulte la sección sobre [IMS](../../integrations/using/about-adobe-id.md).
1. In **[!UICONTROL Administration > Platform > Options]**, configure the server and organization (Tenant) options for Adobe Target:

   * **[!UICONTROL TNT_EdgeServer]** : Servidor de Adobe Target utilizado para la integración. Esta opción está seleccionada de forma predeterminada. Este valor corresponde al **[!UICONTROL Domain Server]** de Adobe Target, seguido del valor **/m2**. Por ejemplo: **tt.omtrdc.net/m2**.
   * **[!UICONTROL TNT_TenantName]** : Nombre de la organización de Adobe Target. Este valor corresponde al nombre de **[!UICONTROL Client]** de Adobe Target.

   ![](assets/tar_options.png)

