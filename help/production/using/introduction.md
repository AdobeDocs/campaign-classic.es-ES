---
product: campaign
title: Introducción
description: Introducción
feature: Monitoring, Upgrade
audience: production
content-type: reference
topic-tags: updating-adobe-campaign
exl-id: 3e39a0d2-ff7e-4233-82bb-2b360f696a33
TQID: 'https://experienceleague.adobe.com/L6Ais2NSt-Z29b7Jgz25a6uYInel9V-Hb5kv0u6oSLo'
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
    internal-label: Campaign
  - id: fd6e6e36-54e4-4f1a-96fc-1a750e400d50
    internal-label: Campaign Classic v7
feature_v2:
  - id: c5474392-5419-4296-9e41-f6f4ce4f6e9b
    internal-label: Administration
subfeature_v2:
  - id: c03a11ff-bdf9-4e5b-b279-f468b4293464
    internal-label: Performance Monitoring
  - id: e519a22f-a06a-42fc-9d09-d78a3ab2c434
    internal-label: Monitoring guidelines
  - id: eff19c99-440a-4318-b319-444edc4d8d8f
    internal-label: Upgrade
source-git-commit: a43e591a565a18d79f583d975e3e812c5435b0c0
workflow-type: tm+mt
source-wordcount: '194'
ht-degree: 1%
---
# Introducción{#introduction}



En esta sección se presenta el procedimiento que se debe aplicar para actualizar Adobe Campaign, del lado del cliente y del lado del servidor, y se describe el cambio a Unicode de una instancia existente.

>[!NOTE]
>
>Para las instancias de servicios alojados/administrados, debe coordinarse con el administrador de Adobe.\
>En las instancias locales, puede obtener asistencia de los consultores de Adobe.

La actualización debe aplicarse a todos los servidores donde esté instalado Adobe Campaign.

1. Migre los servidores de redirección y seguimiento (Apache/IIS).
1. Migre los servidores Power Booster/Cluster.
1. Migre el servidor de marketing.

Adobe Campaign se basa en varios procesos ejecutados en el servidor que deberá manipular durante las actualizaciones, en particular:

* Servidor de aplicaciones (web nlserver)
* Servidor de entrega (nlserver mta)
* Servidor de redirección (webmdl)

>[!CAUTION]
>
>La consola de cliente debe tener la misma versión que la instancia de servidor.

>[!NOTE]
>
>Para obtener más información sobre los distintos procesos de Adobe Campaign, consulte [esta sección](../../installation/using/general-architecture.md#logical-application-layer).\
>Al utilizar la arquitectura de tipo Power Booster o Power Cluster, debe aplicar este proceso a todos los servidores Power Booster/Cluster.

Si la nueva versión implica una modificación de la estructura de la base de datos, se recomienda reiniciar los servidores en el siguiente orden:

1. Servidor de aplicaciones (web nlserver),
1. Servidor de redirección (webmdl),
1. Servidor de envío (mta de nlserver).
