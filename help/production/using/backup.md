---
product: campaign
title: Copia de seguridad
description: Copia de seguridad
feature: Monitoring
badge-v7-only: label="v7" type="Informative" tooltip="Se aplica solo a Campaign Classic v7"
badge-v7-prem: label="On-Premise e híbrido" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=es" tooltip="Se aplica solo a implementaciones On-premise e híbridas"
audience: production
content-type: reference
topic-tags: data-processing
exl-id: e5ef6aba-dc22-4c8d-9fbb-13d507181b65
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: tm+mt
source-wordcount: '216'
ht-degree: 9%

---

# Copia de seguridad{#backup}

El backup es esencial para evitar la pérdida de datos en caso de problemas (ya sean físicos o relacionados con el sistema) en una máquina.

Los datos se almacenan en dos ubicaciones independientes:

* los archivos físicos se almacenan en los directorios de Adobe Campaign,
* otros datos se almacenan en la base de datos.

La mayoría de los datos se encuentran en la base de datos. Esto representa el 99 % de la información de la que se va a realizar una copia de seguridad.

## Archivos físicos {#physical-files}

Los archivos se dividen en varias categorías:

* Archivos de configuración, almacenados en **nl6/conf**, permite reconfigurar Adobe Campaign muy rápidamente.

* Archivos de redirección, almacenados en  **nl6/var/`<instance-name>`/redir**, se encuentran en los servidores de seguimiento (a menudo denominados &quot;frontales&quot;) e incluyen todas las redirecciones de campañas anteriores. Las campañas anteriores siguen utilizándolos.

* Archivos de registro, almacenados en **nl6/var/`<instance-name>`/log**, se puede utilizar para realizar un seguimiento de los problemas.

Por lo tanto, los directorios de los que se va a realizar una copia de seguridad son:

* nl6/conf

* nl6/var/`<instance-name>`/redir (para cada instancia)

* nl6/var/`<instance-name>`/log (opcional)

* nl6/var/`<instance-name>`/relay (opcional)


## Base de datos {#database}

>[!IMPORTANT]
>
>Es imperativo hacer una copia de seguridad de la base de datos.


La base de datos contiene toda la información mostrada en la consola de cliente enriquecida de Adobe Campaign, así como todos los datos de la línea de negocios.

Su empresa de alojamiento web, y sus administradores de bases de datos en particular, son los responsables de esta operación.
