---
product: campaign
title: Archivos temporales
description: Archivos temporales
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
badge-v7-prem: label="on-premise & hybrid" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html" tooltip="Applies to on-premise and hybrid deployments only"
audience: production
content-type: reference
topic-tags: troubleshooting
exl-id: e77800f5-c0ae-446d-8ff3-bc8a18c97dbd
source-git-commit: 4661688a22bd1a82eaf9c72a739b5a5ecee168b1
workflow-type: tm+mt
source-wordcount: '130'
ht-degree: 4%

---

# Archivos temporales{#temporary-files}



Pueden mostrarse mensajes de error como los siguientes (especialmente en los registros de envío) cuando se pone el sistema en producción:

*No se puede cambiar el nombre del archivo &#39;/tmp/tmp0000.tmp&#39; a /usr/local/neolane/nl6/bin/..//var/XXX/mta/86510470.xml ;(errno=18, vínculo entre dispositivos no válido) (iRc=-52)*

La causa es la siguiente:

Adobe Campaign genera archivos temporales en **/tmp** y, a continuación, les cambia el nombre para moverlos a **/usr/local/neolane/nl6/var**. Este error se produce cuando ambas carpetas (**/tmp** y **/usr/local/neolane/nl6/var**, que de hecho es un vínculo simbólico a **/var/nl6**) corresponden a diferentes dispositivos. El **df** El comando se utiliza para la verificación.

Para corregir este problema, los archivos temporales deben generarse en el mismo dispositivo que el destino.

Por ejemplo, ejecute lo siguiente:

```
$ cd ~/nl6/var
$ mkdir tmp
$ vi ~/nl6/customer.sh
```

A continuación, añada:

```
export TMPDIR=/usr/local/neolane/nl6/var/tmp 
```
