---
product: campaign
title: Archivos temporales
description: Archivos temporales
audience: production
content-type: reference
topic-tags: troubleshooting
exl-id: e77800f5-c0ae-446d-8ff3-bc8a18c97dbd
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: tm+mt
source-wordcount: '130'
ht-degree: 4%

---

# Archivos temporales{#temporary-files}

Cuando el sistema se pone en producción, pueden aparecer mensajes de error como el siguiente (especialmente en los registros de envío):

*No se puede cambiar el nombre del archivo &quot;/tmp/tmp0000.tmp&quot; a /usr/local/neolane/nl6/bin/..//var/XXX/mta/86510470.xml ;(errno=18, enlace entre dispositivos no válido) (iRc=-52)*

La causa es la siguiente:

Adobe Campaign genera archivos temporales en **/tmp** y, a continuación, los cambia de nombre para moverlos a **/usr/local/neolane/nl6/var**. Este error se produce cuando ambas carpetas (**/tmp** y **/usr/local/neolane/nl6/var**, que en realidad es un enlace simbólico a **/var/nl6**) corresponden a diferentes dispositivos. El comando **df** se utiliza para la verificación.

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
