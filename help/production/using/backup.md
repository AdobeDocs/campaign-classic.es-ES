---
product: campaign
title: Copia de seguridad
description: Copia de seguridad
feature: Monitoring
badge-v7-prem: label="On-premise/hybrid only" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=es" tooltip="Applies to on-premise and hybrid deployments only"
audience: production
content-type: reference
topic-tags: data-processing
exl-id: e5ef6aba-dc22-4c8d-9fbb-13d507181b65
TQID: https://experienceleague.adobe.com/ZCExecNbs9DnWVoQLpvzlrH7k2eGhBNq7pEiybyQdi4
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
    internal-label: Campaign
feature_v2:
  - id: a075b2c1-7748-4328-b7f6-343aa314616a
    internal-label: Campaigns
subfeature_v2:
  - id: c03a11ff-bdf9-4e5b-b279-f468b4293464
    internal-label: Performance Monitoring
  - id: e519a22f-a06a-42fc-9d09-d78a3ab2c434
    internal-label: Monitoring guidelines
source-git-commit: 38eab6b8da73163e4476e91c0ef73f25c3f57546
workflow-type: tm+mt
source-wordcount: '220'
ht-degree: 10%
---
# Copia de seguridad{#backup}

El backup es esencial para evitar la pérdida de datos en caso de problemas (ya sean físicos o relacionados con el sistema) en una máquina.

Los datos se almacenan en dos ubicaciones independientes:

* los archivos físicos se almacenan en los directorios de Adobe Campaign,
* otros datos se almacenan en la base de datos.

La mayoría de los datos se encuentran en la base de datos. Esto representa el 99 % de la información de la que se va a realizar una copia de seguridad.

## Archivos físicos {#physical-files}

Los archivos se dividen en varias categorías:

* Los archivos de configuración, almacenados en **nl6/conf**, le permiten reconfigurar Adobe Campaign muy rápidamente.

* Los archivos de redirección, almacenados en **nl6/var/`<instance-name>`/redir**, se encuentran en los servidores de seguimiento (a menudo denominados &quot;frontales&quot;) e incluyen todas las redirecciones de campañas anteriores. Las campañas anteriores siguen utilizándolos.

* Los archivos de registro, almacenados en **nl6/var/`<instance-name>`/log**, se pueden usar para realizar un seguimiento de los problemas.

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
