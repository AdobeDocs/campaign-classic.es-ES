---
product: campaign
title: Copia de seguridad
description: Copia de seguridad
audience: production
content-type: reference
topic-tags: data-processing
exl-id: e5ef6aba-dc22-4c8d-9fbb-13d507181b65
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: tm+mt
source-wordcount: '197'
ht-degree: 2%

---

# Copia de seguridad{#backup}

La copia de seguridad es esencial para evitar la pérdida de datos en caso de problemas (físicos o relacionados con el sistema) en una máquina.

Los datos se almacenan en dos ubicaciones diferentes:

* los archivos físicos se almacenan en los directorios Adobe Campaign,
* otros datos se almacenan en la base de datos.

La mayoría de los datos están en la base de datos. Representa el 99 % de la información a la que se va a realizar una copia de seguridad.

## Archivos físicos {#physical-files}

Los archivos se dividen en varias categorías:

* Archivos de configuración ubicados en **nl6/conf**

   Esto le permite reconfigurar Adobe Campaign muy rápidamente.

* Archivos de redirección ** nl6/var/`<instancename>`/redir**

   Están en los servidores de seguimiento (a menudo denominados &quot;frontales&quot;) e incluyen todas las redirecciones de campañas anteriores. Las campañas anteriores siguen usándolas.

* Archivos de registro: **nl6/var/`<instancename>`/log**

   Pueden utilizarse para rastrear problemas.

Por lo tanto, los directorios a los que se va a realizar una copia de seguridad son:

* nl6/conf

* nl6/var/`<instanceName>`/redir (para cada instancia)

* nl6/var/`<instanceName>`/log (opcional)

* nl6/var/`<instanceName>`/relay (opcional)

>[!IMPORTANT]
>
>Es esencial realizar una copia de seguridad de la base de datos.

## Database {#database}

La base de datos contiene toda la información mostrada en la consola de cliente enriquecida de Adobe Campaign, así como todos los datos de la línea de negocios.

Su empresa de alojamiento y, en particular, sus administradores de base de datos, son responsables de esta operación.
