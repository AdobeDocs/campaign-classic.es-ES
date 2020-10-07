---
title: Introducción
seo-title: Introducción
description: Introducción
seo-description: null
page-status-flag: never-activated
uuid: 4192a74e-1d4f-4784-80e3-53aaefa9141e
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: production
content-type: reference
topic-tags: updating-adobe-campaign
discoiquuid: 772992bf-588f-42bd-a72a-986a88815264
translation-type: tm+mt
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: tm+mt
source-wordcount: '179'
ht-degree: 2%

---


# Introducción{#introduction}

En esta sección se presenta el procedimiento que se debe aplicar para actualizar Adobe Campaign, el cliente y el servidor, y se describe el cambio a Unicode de una instancia existente.

>[!NOTE]
>
>Para las instancias hospedadas, debe coordinarse con el administrador de Adobe.\
>En el caso de instancias locales, puede obtener ayuda de los consultores de Adobe.

La actualización debe aplicarse a todos los servidores en los que esté instalado Adobe Campaign.

1. Migrar los servidores de redirección y seguimiento (Apache/IIS).
1. Migrar los servidores Power Booster/Cluster.
1. Migrar el servidor de marketing.

Adobe Campaign se basa en varios procesos ejecutados en el servidor que deberá manipular durante las actualizaciones, en particular:

* Servidor de aplicaciones (nlserver web)
* Envío server (nlserver mta)
* Servidor de redirección (webmdl)

>[!NOTE]
>
>For more on the various Adobe Campaign processes, refer to [this section](../../installation/using/general-architecture.md#logical-application-layer).\
>Al utilizar la arquitectura de tipo Power Booster o Power Cluster, debe aplicar este proceso a todos los servidores Power Booster/Cluster.

Si la nueva versión implica una modificación de la estructura de la base de datos, recomendamos reiniciar los servidores en el siguiente orden:

1. Servidor de aplicaciones (nlserver web),
1. Servidor de redirección (webmdl),
1. Envío Server (nlserver mta).

