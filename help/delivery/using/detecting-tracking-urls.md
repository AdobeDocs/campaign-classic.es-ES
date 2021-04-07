---
solution: Campaign Classic
product: campaign
title: Detección de direcciones URL de seguimiento
description: Obtenga más información acerca del patrón recomendado para rastrear direcciones URL
audience: delivery
content-type: reference
topic-tags: tracking-messages
translation-type: ht
source-git-commit: 768fe62db4efd1217c22973c7e5dc31097d67bae
workflow-type: ht
source-wordcount: '297'
ht-degree: 100%

---


# Detección de direcciones URL de seguimiento

## Ejemplo de no detección

`<%= getURL("http://mynewsletter.com") %>` funciona y envía el contenido real de la página web por correo electrónico a los destinatarios. Pero no se realiza el seguimiento de ninguno de los enlaces. El motivo es que el servidor de correo ejecuta `"<%=getURL(..."` por cada correo electrónico antes de enviarlo. Puede ser diferente para cada destinatario, por lo que Adobe Campaign no puede conocer las direcciones URL para el seguimiento ni asignarles un ID de etiqueta.

Cuando la página que se va a descargar es la misma para todos los destinatarios, se recomienda hacer lo siguiente:

`<%@ include url="http://mynewsletter.com" %>`

En ese caso, la página se descarga durante el análisis, antes de la detección de seguimiento. Permite a Adobe Campaign descubrir los vínculos, asignar un ID de etiqueta y realizar un seguimiento de ellos.

## Patrón recomendado

Después de procesar las instrucciones `<%@`, la dirección URL que se va a rastrear tiene la siguiente sintaxis: `<a href="http://myurl.com/a.php?param1=aaa&param2=<%=escapeUrl(recipient.xxx)%>&param3=<%=escapeUrl(recipient.xxx)%>">`

>[!IMPORTANT]
>
>Todos los demás patrones no son compatibles con Adobe y deben evitarse para prevenir posibles brechas de seguridad.

## Patrón no protegido

Al añadir enlaces personalizados al contenido, evite siempre cualquier personalización en la parte del nombre de host de la dirección URL para evitar posibles lagunas de seguridad. Obtenga más información en [esta página](../../installation/using/privacy.md#url-personalization).

Por ejemplo, la sintaxis `<a href="http://<%=myURL%>">` **no es segura** y debe evitarse.

* El uso de esta sintaxis puede dar lugar a problemas de seguridad si el vínculo generado por Adobe Campaign contiene uno o varios parámetros.
* Tidy puede corregir incorrectamente algunos de los vínculos, lo que puede ocurrir al azar. El síntoma típico es un fragmento de HTML visible en las pruebas de correo electrónico, pero no en la vista previa.
* Hay problemas con el escape de la dirección URL o algunos caracteres de la dirección URL pueden causarlos.
* No se puede tener un parámetro denominado ID en conflicto con el parámetro en la URL de redirección.
* El interés del seguimiento se limita entonces a estadísticas sobre el envío, ya que Adobe Campaign realiza un seguimiento indiferente de todos los valores posibles de myURL.
