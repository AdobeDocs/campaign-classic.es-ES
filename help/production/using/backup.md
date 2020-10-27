---
title: Copia de seguridad
seo-title: Copia de seguridad
description: Copia de seguridad
seo-description: null
page-status-flag: never-activated
uuid: 50134154-a671-4534-b48d-a9e2c42e8f1a
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: production
content-type: reference
topic-tags: data-processing
discoiquuid: 870ab0f2-1bd7-42e7-8d83-a08a520b6587
translation-type: tm+mt
source-git-commit: 849e1ebf14f707d9e86c5a152de978acb6f1cb35
workflow-type: tm+mt
source-wordcount: '198'
ht-degree: 2%

---


# Copia de seguridad{#backup}

La copia de seguridad es esencial para evitar la pérdida de datos en el evento de un problema (físico o relacionado con el sistema) en una máquina.

Los datos se almacenan en dos ubicaciones distintas:

* los archivos físicos se almacenan en los directorios de Adobe Campaign,
* otros datos se almacenan en la base de datos.

La mayoría de los datos están en la base de datos. Esto representa el 99% de la información a la que se debe hacer backup.

## Archivos físicos {#physical-files}

Los archivos se dividen en varias categorías:

* Archivos de configuración, ubicados en **nl6/conf**

   Esto le permite volver a configurar Adobe Campaign muy rápidamente.

* Archivos de redirección ** nl6/var/`<instancename>`/redir**

   Están en los servidores de seguimiento (a menudo llamados &quot;frontales&quot;) e incluyen todas las redirecciones de campaña anteriores. Las campañas anteriores siguen usándolas.

* Archivos de registro: **nl6/var/`<instancename>`/log**

   Se pueden usar para rastrear problemas.

Por lo tanto, los directorios a los que se debe hacer una copia de seguridad son:

* nl6/conf

* nl6/var/`<instanceName>`/redir (para cada instancia)

* nl6/var/`<instanceName>`/log (opcional)

* nl6/var/`<instanceName>`/relay (opcional)

>[!IMPORTANT]
>
>Es esencial realizar una copia de seguridad de la base de datos.

## Database {#database}

La base de datos contiene toda la información que se muestra en la consola de cliente enriquecida de Adobe Campaign, así como todos los datos de la línea de negocios.

La compañía de alojamiento, y los administradores de base de datos en particular, son responsables de esta operación.
