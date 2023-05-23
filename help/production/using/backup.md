---
product: campaign
title: Copia de seguridad
description: Copia de seguridad
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
badge-v7-prem: label="on-premise & hybrid" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html" tooltip="Applies to on-premise and hybrid deployments only"
audience: production
content-type: reference
topic-tags: data-processing
exl-id: e5ef6aba-dc22-4c8d-9fbb-13d507181b65
source-git-commit: 4661688a22bd1a82eaf9c72a739b5a5ecee168b1
workflow-type: tm+mt
source-wordcount: '198'
ht-degree: 2%

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


## Database {#database}

>[!IMPORTANT]
>
>Es imperativo hacer una copia de seguridad de la base de datos.


La base de datos contiene toda la información mostrada en la consola de cliente enriquecida de Adobe Campaign, así como todos los datos de la línea de negocios.

Su empresa de alojamiento web, y sus administradores de bases de datos en particular, son los responsables de esta operación.
