---
product: campaign
title: Introducción
description: Introducción
feature: Monitoring, Upgrade
audience: production
content-type: reference
topic-tags: updating-adobe-campaign
exl-id: 3e39a0d2-ff7e-4233-82bb-2b360f696a33
source-git-commit: b666535f7f82d1b8c2da4fbce1bc25cf8d39d187
workflow-type: tm+mt
source-wordcount: '193'
ht-degree: 1%

---

# Introducción{#introduction}



En esta sección se presenta el procedimiento que se debe aplicar para actualizar Adobe Campaign, del lado del cliente y del lado del servidor, y se describe el cambio a Unicode de una instancia existente.

>[!NOTE]
>
>Para las instancias de servicios alojados/administrados, debe coordinarse con el administrador de Adobe.\
>En el caso de instancias locales, puede obtener asistencia de los consultores de Adobe.

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
