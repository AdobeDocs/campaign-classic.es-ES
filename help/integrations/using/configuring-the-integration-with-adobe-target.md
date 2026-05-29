---
product: campaign
title: Configuración de la integración con Adobe Target
description: Información sobre cómo configurar la integración con Adobe Target
feature: Target Integration
audience: integrations
content-type: reference
topic-tags: adobe-target
exl-id: ae8c680f-52a6-4d00-91cd-44d1c3807546
TQID: https://experienceleague.adobe.com/k6TljRgymSefOITPaogJdR7HOrl1BnnZm9jbkemrcyg
product_v2: id: dfc56824-e8b9-499e-85d4-21aedb507314
feature_v2: id: c5474392-5419-4296-9e41-f6f4ce4f6e9bid: d5ef99fa-df0c-4153-bf94-105ad0724167
subfeature_v2: id: cbcf4d90-26be-46e2-b16a-aebc529dc41eid: df0d6518-6f49-46e2-b46e-3bcc513f553fid: eb007b6d-6e57-46ab-9485-3f24d6102304id: b1fd1501-3105-4d6b-b4d4-9af53126df75
topic_v2: id: eddd9b14-83bd-4ff4-9072-54a4a484abb7
source-git-commit: 38eab6b8da73163e4476e91c0ef73f25c3f57546
workflow-type: tm+mt
source-wordcount: 198
ht-degree: 100%

---

# Configuración de la integración con Adobe Target{#configuring-the-integration-with-adobe-target}




>[!CAUTION]
>
> Como cliente alojado o híbrido, póngase en contacto con su representante de Adobe para configurar esta integración. Los pasos siguientes solo se aplican a clientes locales.

Esta integración requiere:

* Organizaciones de Adobe Experience Cloud y Adobe Target
* Un “rawbox” de Adobe Target determinada para establecer la conexión con Adobe Campaign

Para configurar esta integración en Adobe Campaign, siga los pasos a continuación:

1. Instale el paquete integrado **[!UICONTROL Integration with the Adobe Experience Cloud]**. [Más información](../../platform/using/working-with-data-packages.md#importing-packages)

   Esto le permite acceder a los recursos compartidos a través del Digital Asset Manager.

1. Permita la conexión mediante IMS (servicio de conexión con Adobe ID) para utilizar imágenes compartidas mediante Adobe Experience Cloud en sus correos electrónicos. [Más información](../../integrations/using/about-adobe-id.md)
1. Navegue a **[!UICONTROL Administration > Platform > Options]** para configurar las opciones del servidor y la organización (inquilino) de Adobe Target:

   ![](assets/tar_options.png)

   * **[!UICONTROL TNT_EdgeServer]** : Servidor de Adobe Target utilizado para la integración. Esta opción está seleccionada de forma predeterminada. Este valor corresponde al **[!UICONTROL Domain Server]** de Adobe Target, seguido del valor **/m2**. Por ejemplo: **tt.omtrdc.net/m2**.
   * **[!UICONTROL TNT_TenantName]** : Nombre de la organización de Adobe Target. Este valor corresponde al nombre de **[!UICONTROL Client]** de Adobe Target.


>[!CAUTION]
>
>Para las arquitecturas híbridas y alojadas, estas opciones deben configurarse en todos los servidores, incluidos el [servidor intermediario](../../installation/using/mid-sourcing-server.md) y la [instancia de ejecución](../../message-center/using/configuring-instances.md#execution-instance).