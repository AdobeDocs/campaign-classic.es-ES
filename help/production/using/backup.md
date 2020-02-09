---
title: Backup
seo-title: Backup
description: Backup
seo-description: null
page-status-flag: never-activated
uuid: 50134154-a671-4534-b48d-a9e2c42e8f1a
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: production
content-type: reference
topic-tags: data-processing
discoiquuid: 870ab0f2-1bd7-42e7-8d83-a08a520b6587
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 2a11a73b0679c0a65dc10f71869bf2a6c6efc008

---


# Backup{#backup}

La copia de seguridad es esencial para evitar la pérdida de datos en caso de problemas (físicos o relacionados con el sistema) en un equipo.

Los datos se almacenan en dos ubicaciones distintas:

* los archivos físicos se almacenan en los directorios de Adobe Campaign,
* otros datos se almacenan en la base de datos.

La mayoría de los datos están en la base de datos. Esto representa el 99% de la información a la que se debe hacer backup.

## Archivos físicos {#physical-files}

Los archivos se dividen en varias categorías:

* Archivos de configuración, ubicados en **nl6/conf**

   Esto le permite volver a configurar Adobe Campaign muy rápidamente.

* Archivos de redirección ** nl6/var/`<instancename>`/redir**

   Están en los servidores de seguimiento (a menudo llamados &quot;frontales&quot;) e incluyen todas las redirecciones de campañas anteriores. Las campañas anteriores siguen usándolas.

* Archivos de registro: **nl6/var/`<instancename>`/log**

   Se pueden usar para rastrear problemas.

Por lo tanto, los directorios a los que se debe hacer una copia de seguridad son:

* nl6/conf

* nl6/var/`<instanceName>`/redir (para cada instancia)

* nl6/var/`<instanceName>`/log (opcional)

* nl6/var/`<instanceName>`/relay (opcional)

>[!CAUTION]
>
>Es esencial realizar una copia de seguridad de la base de datos.

## Base de datos {#database}

La base de datos contiene toda la información que se muestra en la consola de cliente enriquecida de Adobe Campaign, así como todos los datos de la línea de negocios.

Su empresa de hosting y, en particular, sus administradores de base de datos, son responsables de esta operación.
