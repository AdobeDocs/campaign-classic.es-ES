---
product: campaign
title: Puntos clave a la hora de administrar la entregabilidad en Adobe Campaign Classic
description: Descubra los puntos clave que debe comprobar al administrar la entregabilidad en Adobe Campaign
feature: Deliverability, Troubleshooting
role: User
exl-id: f94897c1-b44c-4100-ac50-a89b13fa6f2f
TQID: https://experienceleague.adobe.com/ZRai7Bd-IRaWUQQmkuUYwXhNXp2BI-B4k-4cGq1k6uk
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
feature_v2:
  - id: c5474392-5419-4296-9e41-f6f4ce4f6e9b
  - id: b631758a-142d-425f-b9aa-f756d85cb979
  - id: c858a28b-ea19-49b0-8d48-828717fad89c
subfeature_v2:
  - id: e95a583b-fcfa-4524-8666-46a29c828119
  - id: c8da4fdd-eb94-4751-a43c-f82733fb2d6e
  - id: d5bbe3da-ba85-4242-817e-54f7c4b943e0
  - id: f4da0e76-df77-451e-ad61-21afb7bd8810
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
topic_v2:
  - id: c1579802-ddd4-4214-8a91-97b2066abe11
  - id: eddd9b14-83bd-4ff4-9072-54a4a484abb7
source-git-commit: 38eab6b8da73163e4476e91c0ef73f25c3f57546
workflow-type: ht
source-wordcount: 660
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

  Para obtener más información, consulte [esta sección](delivery-failures-quarantine.md#quarantine-vs-denylist).

* **¿Qué significan las diferentes razones de error de cuarentena?**

  Estas son 10 razones posibles: no definido, usuario desconocido, dominio inválido, incluida en la lista de bloqueados, rechazado, error omitido, inaccesible, cuenta deshabilitada, buzón lleno, sin conexión.

  Para obtener más información, consulte [Comprensión de la administración de cuarentena](delivery-failures-quarantine.md).

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
