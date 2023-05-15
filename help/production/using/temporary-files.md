---
product: campaign
title: Archivos temporales
description: Archivos temporales
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
badge-v7-prem: label="on-premise & hybrid" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=en" tooltip="Applies to on-premise and hybrid deployments only"
audience: production
content-type: reference
topic-tags: troubleshooting
exl-id: e77800f5-c0ae-446d-8ff3-bc8a18c97dbd
source-git-commit: a5762cd21a1a6d5a5f3a10f53a5d1f43542d99d4
workflow-type: tm+mt
source-wordcount: '130'
ht-degree: 4%

---

# Archivos temporales{#temporary-files}



Cuando el sistema se pone en producción, pueden aparecer mensajes de error como el siguiente (especialmente en los registros de envío):

*No se puede cambiar el nombre del archivo &quot;/tmp/tmp0000.tmp&quot; a /usr/local/neolane/nl6/bin/..//var/XXX/mta/86510470.xml ;(errno=18, enlace entre dispositivos no válido) (iRc=-52)*

La causa es la siguiente:

Adobe Campaign genera archivos temporales en **/tmp** y, a continuación, cambie su nombre para que se muevan a **/usr/local/neolane/nl6/var**. Este error se produce cuando ambas carpetas (**/tmp** y **/usr/local/neolane/nl6/var**, que en realidad es un vínculo simbólico a **/var/nl6**) corresponden a distintos dispositivos. La variable **df** se utiliza para la verificación.

Para solucionar este problema, los archivos temporales deben generarse en el mismo dispositivo que el destino.

Por ejemplo, ejecute lo siguiente:

```
$ cd ~/nl6/var
$ mkdir tmp
$ vi ~/nl6/customer.sh
```

A continuación, agregue:

```
export TMPDIR=/usr/local/neolane/nl6/var/tmp 
```
