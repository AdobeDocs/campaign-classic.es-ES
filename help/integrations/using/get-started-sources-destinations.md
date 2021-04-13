---
solution: Campaign Classic
product: campaign
title: Introducción a Fuentes y destinos
description: Obtenga más información sobre Fuentes y destinos de Adobe Experience Platform.
audience: integrations
content-type: reference
translation-type: tm+mt
source-git-commit: b4da54c122e75a175f6f586a05955b3dfed00c1e
workflow-type: tm+mt
source-wordcount: '307'
ht-degree: 1%

---


# Introducción a Orígenes y Destinos {#rtcdp}

## Acerca de las fuentes y los destinos

Con Adobe Experience Platform, puede compartir datos entre el Campaign Classic y la plataforma de datos del cliente en tiempo real de Adobe (RTCDP). Esto le permite dirigirse a las audiencias de Adobe Experience Platform en sus flujos de trabajo de Campaign y, a continuación, enviar a Adobe datos de la plataforma de datos del cliente en tiempo real relacionados con estas audiencias, como envíos, aperturas y clics.

* Con **Destinations**, incorpore audiencias de Adobe Experience Platform en Campaign Classic. Esto le permite activar los datos conocidos y desconocidos para sus campañas de marketing.
* Con **Sources**, exporte los datos del Campaign Classic (por ejemplo, envíos, aperturas, clics) a Adobe Experience Platform. Esto le permite centralizar los datos que recopila de fuentes diferentes en un solo lugar y utilizar las perspectivas obtenidas de él para hacer más.

>[!IMPORTANT]
>
>Tenga en cuenta los límites de almacenamiento SFTP, los límites de almacenamiento de la base de datos y los límites de perfil activos según el contrato de Adobe Campaign mientras realiza esta integración.

Para obtener una descripción más detallada de la plataforma de datos, los destinos y las fuentes de los clientes en tiempo real de Adobe, consulte estas páginas:

* [Plataforma de datos de clientes en tiempo real de Adobe](https://experienceleague.adobe.com/docs/experience-platform/rtcdp/overview.html)
* [Documentación de destinos](https://experienceleague.adobe.com/docs/experience-platform/destinations/home.html)
* [Documentación de fuentes](https://experienceleague.adobe.com/docs/experience-platform/sources/home.html)

## Conectar Campaign Classic con Adobe Experience Platform

Para poder compartir datos entre Adobe Experience Platform y Campaign Classic, primero debe conectar Adobe Campaign como **Destination** y conectar su ubicación de almacenamiento del blob de AWS S3 o Azure como **Source** en Adobe experience Platform.

Una vez configurados los conectores, puede configurar una importación de datos o exportación a Campaign Classic mediante flujos de trabajo.

![](assets/rtcdp-schema.png)

Para obtener más información sobre cómo configurar estos procesos de importación y exportación, consulte estas secciones:

* [Ingesta de segmentos de Adobe Experience Platform en Campaign](../../integrations/using/ingest-aep-data.md)
* [Exportar datos de Campaign a Adobe Experience Platform](../../integrations/using/export-campaign-data.md)
