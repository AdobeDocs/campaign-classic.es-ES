---
product: campaign
title: Copia de seguridad
description: Copia de seguridad
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
badge-v7-prem: label="on-premise & hybrid" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=en" tooltip="Applies to on-premise and hybrid deployments only"
audience: production
content-type: reference
topic-tags: data-processing
exl-id: e5ef6aba-dc22-4c8d-9fbb-13d507181b65
source-git-commit: dcc441272b29f682165a26006800e914e7c38252
workflow-type: tm+mt
source-wordcount: '179'
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

* Archivos de configuración, almacenados en `nl6/conf`, le permiten reconfigurar Adobe Campaign muy rápidamente.

* Archivos de redirección, almacenados en  `nl6/var/`<instancename>`/redir`, están en los servidores de seguimiento (generalmente denominados &quot;frontales&quot;) e incluyen todas las redirecciones de campañas anteriores. Las campañas anteriores siguen usándolas.

* Archivos de registro, almacenados en `nl6/var/`<instancename>`/log`, se puede utilizar para rastrear problemas.

Por lo tanto, los directorios a los que se va a realizar una copia de seguridad son:

* `nl6/conf`

* `nl6/var/`<instanceName>`/redir` (para cada instancia)

* `nl6/var/`<instanceName>`/log` (opcional)

* `nl6/var/`<instanceName>`/relay` (opcional)


## Database {#database}

>[!IMPORTANT]
>
>Es imperativo realizar una copia de seguridad de la base de datos.


La base de datos contiene toda la información mostrada en la consola de cliente enriquecida de Adobe Campaign, así como todos los datos de la línea de negocios.

Su empresa de alojamiento y, en particular, sus administradores de base de datos, son responsables de esta operación.
