---
solution: Campaign Classic
product: campaign
title: Archivos temporales
description: Archivos temporales
audience: production
content-type: reference
topic-tags: troubleshooting
translation-type: tm+mt
source-git-commit: 50f95d7156e7104d90fa7a31eea30711b9c11bbf
workflow-type: tm+mt
source-wordcount: '130'
ht-degree: 4%

---


# Archivos temporales{#temporary-files}

Cuando el sistema se pone en producción, pueden aparecer mensajes de error como los siguientes (especialmente en registros de envío):

*No se puede cambiar el nombre del archivo &#39;/tmp/tmp0000.tmp&#39; a /usr/local/neolane/nl6/bin/..//var/XXX/mta/86510470.xml ;(errno=18, vínculo entre dispositivos no válido) (iRc=-52)*

La causa es la siguiente:

Adobe Campaign genera archivos temporales en **/tmp** y, a continuación, los cambia de nombre para moverlos a **/usr/local/neolane/nl6/var**. Este error se produce cuando ambas carpetas (**/tmp** y **/usr/local/neolane/nl6/var**, que en realidad es un vínculo simbólico a **/var/nl6**) corresponden a diferentes dispositivos. El comando **df** se utiliza para la verificación.

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

