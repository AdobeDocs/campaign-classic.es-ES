---
product: campaign
title: Configuración de la integración con Adobe Target
description: Configuración de la integración con Adobe Target
audience: integrations
content-type: reference
topic-tags: adobe-target
exl-id: ae8c680f-52a6-4d00-91cd-44d1c3807546
source-git-commit: b6e24c63ece12f25b7dafe3fede9e38b3aab2427
workflow-type: tm+mt
source-wordcount: '201'
ht-degree: 73%

---

# Configuración de la integración con Adobe Target{#configuring-the-integration-with-adobe-target}

![](../../assets/common.svg)


>[!CAUTION]
>
> Como cliente alojado o híbrido, póngase en contacto con su representante de Adobe para configurar esta integración. Los pasos siguientes solo se aplican a clientes locales.

## Requisitos previos {#prerequisites}

Para utilizar la integración entre Adobe Campaign y Adobe Target, debe tener:

* Organizaciones de Adobe Experience Cloud y Adobe Target
* Un “rawbox” de Adobe Target determinada para establecer la conexión con Adobe Campaign

## Configuración de Adobe Campaign {#configuring-adobe-campaign}

Para configurar Adobe Campaign:

1. Instale el **[!UICONTROL Integration with the Adobe Experience Cloud]** paquete integrado. [Más información](../../platform/using/working-with-data-packages.md#importing-packages)

   Este paquete le permite acceder a los recursos compartidos a través de Digital Asset Manager.

1. Permita la conexión mediante IMS (servicio de conexión con Adobe ID) para utilizar imágenes compartidas mediante Adobe Experience Cloud en sus correos electrónicos. [Más información](../../integrations/using/about-adobe-id.md)
1. Vaya a **[!UICONTROL Administration > Platform > Options]** para configurar las opciones del servidor y la organización (inquilino) de Adobe Target:

   ![](assets/tar_options.png)

   * **[!UICONTROL TNT_EdgeServer]** : Servidor de Adobe Target utilizado para la integración. Esta opción está seleccionada de forma predeterminada. Este valor corresponde al **[!UICONTROL Domain Server]** de Adobe Target, seguido del valor **/m2**. Por ejemplo: **tt.omtrdc.net/m2**.
   * **[!UICONTROL TNT_TenantName]** : Nombre de la organización de Adobe Target. Este valor corresponde al nombre de **[!UICONTROL Client]** de Adobe Target.


>[!CAUTION]
>
>Para las arquitecturas híbridas y alojadas, estas opciones deben configurarse en todos los servidores, incluidos el [servidor intermediario](../../installation/using/mid-sourcing-server.md) y la [instancia de ejecución](../../message-center/using/configuring-instances.md#execution-instance).