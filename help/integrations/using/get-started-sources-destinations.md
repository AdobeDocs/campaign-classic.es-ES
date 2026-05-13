---
product: campaign
title: Introducción a orígenes y destinos
description: Obtenga más información sobre orígenes y destinos de Adobe Experience Platform
feature: Experience Platform Integration
audience: integrations
content-type: reference
exl-id: 8cee52c7-ea56-4701-8ebb-eb18afffea51
TQID: https://experienceleague.adobe.com/xPpBR6NrQ315FIw1beLnw4c0gyLzEoYWzIXDljDg9H4
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
feature_v2:
  - id: a075b2c1-7748-4328-b7f6-343aa314616a
  - id: d5ef99fa-df0c-4153-bf94-105ad0724167
subfeature_v2:
  - id: c3bf7e1e-1db5-4c72-9293-e2f0b1ab73d0
  - id: eb007b6d-6e57-46ab-9485-3f24d6102304
topic_v2:
  - id: c1579802-ddd4-4214-8a91-97b2066abe11
  - id: e1e0219c-f879-479f-8427-888ed2a6e9c2
source-git-commit: 4c295c0dabae8aba298390a3da2422a3fa1219f9
workflow-type: tm+mt
source-wordcount: 313
ht-degree: 100%

---

# Trabajo con fuentes y destinos {#rtcdp}



## Acerca de los orígenes y destinos

Con Adobe Experience Platform, puede compartir datos entre Campaign Classic y la plataforma de datos del cliente en tiempo real de Adobe (RTCDP). Esto le permite dirigirse a los públicos de Adobe Experience Platform en sus flujos de trabajo de Campaign y, a continuación, enviar los datos de la plataforma de datos del cliente en tiempo real de Adobe relacionados con estos públicos, como envíos, aperturas y clics.

* Con **Destinos**, introduzca públicos de Adobe Experience Platform en Campaign Classic. Esto le permite activar los datos conocidos y desconocidos para sus campañas de marketing.
* Con **Orígenes**, exporte los datos de Campaign Classic (por ejemplo, envíos, aperturas, clics) a Adobe Experience Platform. Esto le permite centralizar los datos que recopila de orígenes diferentes en un solo lugar y utilizar las perspectivas obtenidas de él para hacer más.

>[!IMPORTANT]
>
>Tenga en cuenta los límites del almacenamiento de SFTP, el almacenamiento de la base de datos y el perfil activo según el contrato de Adobe Campaign al usar esta funcionalidad.

Para obtener una descripción más detallada de la plataforma de datos del cliente en tiempo real de Adobe, los destinos y los orígenes, consulte estas páginas:

* [Adobe Real-time Customer Data Platform](https://experienceleague.adobe.com/docs/experience-platform/rtcdp/overview.html?lang=es)
* [Documentación sobre los destinos](https://experienceleague.adobe.com/docs/experience-platform/destinations/home.html?lang=es)
* [Documentación sobre los orígenes](https://experienceleague.adobe.com/docs/experience-platform/sources/home.html?lang=es)

## Conectar Campaign Classic con Adobe Experience Platform

Para poder compartir datos entre Adobe Experience Platform y Campaign Classic, primero debe conectar Adobe Campaign como **destino** y conectar su ubicación de AWS S3 o Azure Blob Storage como **origen** en Adobe Experience Platform.

Una vez configurados los conectores, puede configurar una importación de datos o exportación a Campaign Classic mediante los flujos de trabajo.

![](assets/rtcdp-schema.png)

Para obtener más información sobre cómo configurar estos procesos de importación y exportación, consulte estas secciones:

* [Ingesta de segmentos de Adobe Experience Platform en Campaign](../../integrations/using/ingest-aep-data.md)
* [Exportación de datos de Campaign a Adobe Experience Platform](../../integrations/using/export-campaign-data.md)
