---
product: campaign
title: Introducción
description: Introducción
audience: production
content-type: reference
topic-tags: updating-adobe-campaign
exl-id: 3e39a0d2-ff7e-4233-82bb-2b360f696a33
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: tm+mt
source-wordcount: '191'
ht-degree: 1%

---

# Introducción{#introduction}

En esta sección se presenta el procedimiento que se debe aplicar para actualizar Adobe Campaign, del lado del cliente y del servidor, y se describe el cambio a Unicode de una instancia existente.

>[!NOTE]
>
>En el caso de instancias alojadas, debe coordinarse con el administrador de Adobe.\
>Para las instancias locales, puede obtener asistencia de los consultores de Adobe.

La actualización debe aplicarse a todos los servidores donde está instalado Adobe Campaign.

1. Migre los servidores de redirección y seguimiento (Apache/IIS).
1. Migre los servidores Power Booster/Cluster.
1. Migrar el servidor de marketing.

Adobe Campaign se basa en varios procesos ejecutados en el servidor que deberá manipular durante las actualizaciones, en particular:

* Servidor de aplicaciones (nlserver web)
* Servidor de entrega (nlserver mta)
* Servidor de redirección (webmdl)

>[!CAUTION]
>
>La consola del cliente debe estar en la misma compilación que la instancia del servidor.

>[!NOTE]
>
>Para obtener más información sobre los distintos procesos de Adobe Campaign, consulte [esta sección](../../installation/using/general-architecture.md#logical-application-layer).\
>Al utilizar la arquitectura de tipo Power Booster o Power Cluster, debe aplicar este proceso a todos los servidores Power Booster/Cluster.

Si la nueva versión implica una modificación de la estructura de la base de datos, se recomienda reiniciar los servidores en el siguiente orden:

1. Servidor de aplicaciones (nlserver web),
1. Servidor de redirección (webmdl),
1. Servidor de entrega (nlserver mta).
