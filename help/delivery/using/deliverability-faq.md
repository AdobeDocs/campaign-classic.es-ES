---
solution: Campaign Classic
product: campaign
title: Puntos clave a la hora de administrar la entrega en Adobe Campaign Classic
description: ¿Cuáles son los puntos clave que hay que comprobar al administrar la capacidad de entrega en Adobe Campaign Classic?
audience: delivery
content-type: reference
topic-tags: deliverability-management
translation-type: tm+mt
source-git-commit: 5d1a653a9a164c34bb70efcc86ff2d7bdf1130a2
workflow-type: tm+mt
source-wordcount: '657'
ht-degree: 100%

---


# Solución de problemas de envío{#deliverability-faq}

¿Está teniendo un problema de envío? Puede encontrar la solución aquí.

## Error de regla MX {#mx-rule-error}

**¿Qué significa el mensaje de error “cuotas satisfechas”?**

Este mensaje indica que ha alcanzado el límite de cuotas para un MX específico y que tiene que esperar para poder enviar otro correo electrónico a este proveedor.

En Adobe Campaign, existe una configuración relacionada con el número de correos electrónicos por hora que pueden enviarse. Esta configuración debe utilizarse con cautela, ya que el número definido en la instancia hace referencia al número de conexiones realizadas con el ISP y no al número de correos electrónicos realmente enviados.

Esto significa que una conexión puede utilizar una regla MX sin enviar correctamente un correo electrónico. En este caso, una configuración con una dirección IP o un dominio con una baja reputación debe probar varias conexiones antes de enviar un correo electrónico. Por cada intento, se gasta un crédito de messages per hour (mensajes por hora). Como resultado, el rendimiento de la campaña de marketing se ve afectado de forma significativa.

Así que “cuotas satisfechas” no es solamente un problema de configuración, sino que también puede estar vinculado a la reputación. Es importante analizar los mensajes de error en el [registro SMTP](../../production/using/monitoring-processes.md#smtp-errors-per-domain).

Para saber más sobre la configuración MX, consulte [esta sección](../../installation/using/email-deliverability.md#mx-configuration).

## El mismo mensaje de error para un ISP {#same-error-for-an-isp}

**¿Por qué siempre recibo el mismo mensaje de error para un ISP en particular?**

Si siempre recibe el mismo mensaje de error para un ISP, es posible que el ISP haya detectado un error en su dirección de correo electrónico o IP. Siga las siguientes recomendaciones:
* Compruebe si recibe un gran porcentaje de errores vinculados a direcciones de correo electrónico inexistentes (errores de **usuario desconocido**).
* Actualice los formularios de suscripción para detectar cualquier error en los nombres de dominio introducidos (por ejemplo: gmaul.com o yaho.com).
* Si nota errores que indican que sus mensajes están declarados como correo no deseado o que sus mensajes están bloqueados constantemente, intente excluir los destinatarios que no han abierto o hecho clic en uno de sus mensajes en los últimos 12 meses desde el destinatario.

Si el problema persiste, póngase en contacto con los servicios comerciales o de entrega, [Servicio de atención al cliente de Adobe](https://helpx.adobe.com/es/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html).

## Lista de bloqueados frente a cuarentena {#denylist-versus-quarantine}

* **¿Cuál es la diferencia entre una dirección de correo electrónico en la lista de bloqueados y una dirección de correo electrónico en cuarentena?**

   * El estado **[!UICONTROL Denylisted]** es el resultado de un bucle de retroalimentación (cuando una persona informa un mensaje como correo no deseado).

   * El estado **[!UICONTROL Quarantined]** es el resultado de un rechazo suave o fuerte.
   Para obtener más información, consulte [esta sección](../../delivery/using/understanding-quarantine-management.md#quarantine-vs-denylist).

* **¿Qué significan las diferentes razones de error de cuarentena?**

   Estas son 10 razones posibles: no definido, usuario desconocido, dominio inválido, incluida en la lista de bloqueados, rechazado, error omitido, inaccesible, cuenta deshabilitada, buzón lleno, sin conexión.

   Para obtener más información, consulte [Comprensión de la administración de cuarentena](../../delivery/using/understanding-quarantine-management.md).

## Eliminación de la lista de bloqueados {#remove-from-denylist}

* **Uno de mis destinatarios fue agregado a la lista de bloqueados por error. ¿Cómo puedo quitarlo de la lista de bloqueados para que pueda volver a enviarle mensajes?**

   * Vaya a **[!UICONTROL Administration > Campaign Management > Non deliverables Management > Non deliverables and addresses]**.
   * En los detalles del registro correspondiente, establezca el valor del campo **[!UICONTROL Status]** en **[!UICONTROL Valid]**.
   * Guarde el registro.

* **¿Cómo puedo averiguar si una de mis IP está en la lista de bloqueados? ¿Cómo elimino mis IP de una lista de bloqueados?**

   Para comprobar si su dirección IP está en la lista de bloqueados, puede utilizar varios sitios web para verificarla, como:
   * [MX Toolbox](https://mxtoolbox.com/)
   * [¿Cuál es mi dirección IP?](https://whatismyipaddress.com)

   Generalmente, el resultado de la comprobación de la dirección IP muestra una lista que contiene los detalles de la lista de bloqueados y el nombre del sitio web que bloqueó la dirección IP.

   Al hacer clic en el enlace correspondiente, puede acceder a los detalles del sitio web. Puede solicitar que su sitio web se elimine de la lista del sitio web que añadió la dirección IP a su lista de bloqueados.

   >[!NOTE]
   >
   >El proceso de supresión de nombres de la lista puede variar según el sitio web. Algunos sitios requieren que cree una cuenta, mientras que otros solo necesitan que proporcione la dirección IP.
