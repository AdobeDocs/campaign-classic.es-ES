---
solution: Campaign Classic
product: campaign
title: Introducción
description: Introducción
audience: production
content-type: reference
topic-tags: updating-adobe-campaign
translation-type: tm+mt
source-git-commit: 0abdbbc33350cf6ec85488483dadb177e685818b
workflow-type: tm+mt
source-wordcount: '178'
ht-degree: 1%

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
>Para obtener más información sobre los distintos procesos de Adobe Campaign, consulte [esta sección](../../installation/using/general-architecture.md#logical-application-layer).\
>Al utilizar la arquitectura de tipo Power Booster o Power Cluster, debe aplicar este proceso a todos los servidores Power Booster/Cluster.

Si la nueva versión implica una modificación de la estructura de la base de datos, recomendamos reiniciar los servidores en el siguiente orden:

1. Servidor de aplicaciones (nlserver web),
1. Servidor de redirección (webmdl),
1. Envío Server (nlserver mta).

