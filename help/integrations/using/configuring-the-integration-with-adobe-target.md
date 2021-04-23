---
solution: Campaign Classic
product: campaign
title: Configuración de la integración con Adobe Target
description: Configuración de la integración con Adobe Target
audience: integrations
content-type: reference
topic-tags: adobe-target
exl-id: ae8c680f-52a6-4d00-91cd-44d1c3807546
translation-type: ht
source-git-commit: 6854d06f8dc445b56ddfde7777f02916a60f2b63
workflow-type: ht
source-wordcount: '175'
ht-degree: 100%

---

# Configuración de la integración con Adobe Target{#configuring-the-integration-with-adobe-target}

## Requisitos previos {#prerequisites}

Para utilizar la integración entre Adobe Campaign y Adobe Target, debe tener:

* Organizaciones de Adobe Experience Cloud y Adobe Target
* Un “rawbox” de Adobe Target determinada para establecer la conexión con Adobe Campaign

## Configuración de Adobe Campaign {#configuring-adobe-campaign}

Para configurar Adobe Campaign:

1. Instale el paquete estándar **[!UICONTROL Integration with the Adobe Experience Cloud]**. La instalación de un paquete de integración es igual que la instalación de un paquete estándar, que se detalla en la sección de [Importación de paquete. ](../../platform/using/working-with-data-packages.md#importing-packages) Esto le permite acceder a los activos compartidos a través del Digital Asset Manager.
1. Permita la conexión mediante IMS (servicio de conexión con Adobe ID) para utilizar imágenes compartidas mediante Adobe Experience Cloud en sus correos electrónicos. Consulte la sección sobre [IMS](../../integrations/using/about-adobe-id.md).
1. En **[!UICONTROL Administration > Platform > Options]**, configure las opciones del servidor y la organización (inquilino) de Adobe Target:

   * **[!UICONTROL TNT_EdgeServer]** : Servidor de Adobe Target utilizado para la integración. Esta opción está seleccionada de forma predeterminada. Este valor corresponde al **[!UICONTROL Domain Server]** de Adobe Target, seguido del valor **/m2**. Por ejemplo: **tt.omtrdc.net/m2**.
   * **[!UICONTROL TNT_TenantName]** : Nombre de la organización de Adobe Target. Este valor corresponde al nombre de **[!UICONTROL Client]** de Adobe Target.
   ![](assets/tar_options.png)
