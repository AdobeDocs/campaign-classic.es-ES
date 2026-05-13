---
product: campaign
title: Archivos temporales
description: Archivos temporales
feature: Monitoring
badge-v7-prem: label="On-premise/híbrido solo" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=es" tooltip="Se aplica solo a implementaciones On-premise e híbridas"
audience: production
content-type: reference
topic-tags: troubleshooting
exl-id: e77800f5-c0ae-446d-8ff3-bc8a18c97dbd
TQID: https://experienceleague.adobe.com/eZnGm-WK-etrLLbJ-aeuSqakYAfPNBQd2q3JlEd4rE8
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
topic_v2:
  - id: c1579802-ddd4-4214-8a91-97b2066abe11
source-git-commit: 4c295c0dabae8aba298390a3da2422a3fa1219f9
workflow-type: tm+mt
source-wordcount: 164
ht-degree: 21%

---

# Archivos temporales{#temporary-files}



Pueden mostrarse mensajes de error como los siguientes (especialmente en los registros de envío) cuando se pone el sistema en producción:

*No se puede cambiar el nombre del archivo &#39;/tmp/tmp0000.tmp&#39; a /usr/local/neolane/nl6/bin/..//var/XXX/mta/86510470.xml ;(errno=18, vínculo entre dispositivos no válido) (iRc=-52)*

La causa es la siguiente:

Adobe Campaign genera archivos temporales bajo **/tmp** y luego los cambia de nombre para moverlos a **/usr/local/neolane/nl6/var**. Este error se produce cuando ambas carpetas (**/tmp** y **/usr/local/neolane/nl6/var**, que en realidad es un vínculo simbólico a **/var/nl6**) corresponden a diferentes dispositivos. El comando **df** se usa para la verificación.

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
