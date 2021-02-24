---
solution: Campaign Classic
product: campaign
title: Detección de direcciones URL de seguimiento
description: Obtenga más información sobre el patrón recomendado para rastrear direcciones URL.
audience: delivery
content-type: reference
topic-tags: tracking-messages
translation-type: tm+mt
source-git-commit: 151667637a12667f5eda1590e64e01de493be9ce
workflow-type: tm+mt
source-wordcount: '262'
ht-degree: 2%

---


# Detección de direcciones URL de seguimiento

## Ejemplo de no detección

`<%= getURL("http://mynewsletter.com") %>` funciona y envía el contenido real de la página web por correo electrónico a los destinatarios. Pero no se realiza el seguimiento de ninguno de los vínculos. El motivo es que el MTA ejecuta `"<%=getURL(..."` por cada correo electrónico antes de enviarlo. Puede ser diferente para cada destinatario, por lo que Adobe Campaign no puede conocer las direcciones URL para el seguimiento y asignarles un ID de etiqueta.

Cuando la página que se va a descargar es la misma para todos los destinatarios, se recomienda hacer lo siguiente:

`<%@ include url="http://mynewsletter.com" %>`

En ese caso, la página se descarga durante la análisis, antes de la detección de seguimiento. Permite a Adobe Campaign descubrir los vínculos, asignar un ID de etiqueta y realizar un seguimiento de ellos.

## Patrón recomendado

Después de procesar las instrucciones `<%@`, la dirección URL que se va a rastrear tiene la siguiente sintaxis: `<a href="http://myurl.com/a.php?param1=aaa&param2=<%=escapeUrl(recipient.xxx)%>&param3=<%=escapeUrl(recipient.xxx)%>">`

>[!IMPORTANT]
>
>Todos los demás patrones no están respaldados por el Adobe y deben evitarse para evitar posibles brechas de seguridad.

## Advertencias sobre el patrón http://&lt;%=myURL%>

La sintaxis `<a href="http://<%=myURL%>">` no es segura y no se recomienda porque:

* Tidy puede corregir incorrectamente algunos de los vínculos, lo que puede ocurrir al azar. El síntoma típico es un fragmento de HTML que está visible en las pruebas de correo electrónico pero no en la previsualización.
* Escapar de la dirección URL es problemático, algunos caracteres de la dirección URL pueden causar problemas.
* No se puede tener un parámetro denominado ID en conflicto con el parámetro en la dirección URL de redirección.
* El interés en el seguimiento se limita entonces a las estadísticas del envío, ya que Adobe Campaign realiza un seguimiento indiferente de todos los valores posibles de &quot;myURL&quot;.

Consulte [esta página](https://helpx.adobe.com/es/campaign/kb/acc-security.html#privacy) para obtener más información.

