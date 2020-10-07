---
title: Archivos temporales
seo-title: Archivos temporales
description: Archivos temporales
seo-description: null
page-status-flag: never-activated
uuid: ae7ec619-e93f-41fb-ba7c-fcbcf4cba84f
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: production
content-type: reference
topic-tags: troubleshooting
discoiquuid: f18237b0-ef54-46a6-9c14-34b038f9de18
translation-type: tm+mt
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: tm+mt
source-wordcount: '132'
ht-degree: 6%

---


# Archivos temporales{#temporary-files}

Si aparecen mensajes de error como los siguientes (especialmente en registros de envío) al poner el sistema en producción:

**No se puede cambiar el nombre del archivo &#39;/tmp/tmp0000.tmp&#39; a /usr/local/neolane/nl6/bin/..//var/XXX/mta/86510470.xml ;(errno=18, vínculo entre dispositivos no válido) (iRc=-52)**

La causa es la siguiente:

Adobe Campaign genera archivos temporales bajo **/tmp** y, a continuación, los cambia de nombre para moverlos a **/usr/local/neolane/nl6/var**. Este error se produce cuando ambas carpetas (**/tmp** y **/usr/local/neolane/nl6/var**, que en realidad es un vínculo simbólico a **/var/nl6**) corresponden a distintos dispositivos. El comando **df** se utiliza para la verificación.

Para corregir este problema, los archivos temporales deben generarse en el mismo dispositivo que el destino. Por ejemplo, ejecutando:

```
$ cd ~/nl6/var
$ mkdir tmp
$ vi ~/nl6/customer.sh
```

y luego agregar:

```
export TMPDIR=/usr/local/neolane/nl6/var/tmp 
```

