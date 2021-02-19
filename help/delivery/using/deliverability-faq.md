---
solution: Campaign Classic
product: campaign
title: Puntos clave a la hora de administrar la entrega en Adobe Campaign Classic
description: ¿Cuáles son los puntos clave que hay que comprobar al administrar la capacidad de entrega en Adobe Campaign Classic?
audience: delivery
content-type: reference
topic-tags: deliverability-management
translation-type: tm+mt
source-git-commit: 3139a9bf5036086831e23acef21af937fcfda740
workflow-type: tm+mt
source-wordcount: '1343'
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

## Prácticas recomendadas {#best-practices}

A continuación se describen algunas prácticas recomendadas que pueden ayudar a identificar y abordar los problemas de envío.

### Identificar un problema de envío {#identify-deliverability-issue}

Los siguientes elementos pueden llamar su atención:

* Métricas de correo o campaña: las tasas de cancelación de suscripción, de queja de abuso o rechazo son más altas de lo habitual.
* Actividad del suscriptor: las aperturas, los clics o las transacciones son inferiores a lo habitual.
* Las cuentas sembradas muestran los correos filtrados o no enviados.

### Suponer las causas potenciales {#potential-causes}

Hágase las siguientes preguntas para identificar las posibles causas del problema de envío:

* ¿Hubo un cambio reciente en la segmentación de listas?
* ¿He adquirido fuentes de datos nuevas?
* ¿He enviado accidentalmente un archivo de cuarentena?
* ¿Podría deberse el problema al contenido de mi mensaje?
* ¿Envío correos con la frecuencia suficiente para mantener IP calientes?
* ¿Estoy segmentando mis correos por actividad/participación o enviando archivos completos?
* ¿Cuál es el segmento “seguro” de mi archivo en términos de actualización?
* ¿Tengo estrategias de reactivación y reconfirmación para segmentos que no están definidos como seguros?

### Abordar el problema {#address-issue}

**Reclamaciones**

Las quejas las definen los suscriptores que **informan del correo electrónico como correo no deseado** pulsando el botón correspondiente de su bandeja de entrada.

Si su problema de envío fue causado por quejas:
* Debe tratar de determinar por qué los destinatarios se quejan.
* También puede considerar mover el enlace de cancelación de suscripción a la parte superior de su correo electrónico. Esto anima a los suscriptores a cancelar la suscripción en lugar de quejarse con el botón de correo no deseado.

Los remitentes pueden obtener una gran cantidad de información de sus quejas sobre el [ciclo de retroalimentación](../../delivery/using/technical-recommendations.md#feedback-loop).
* Es importante agrupar los datos y buscar patrones en elementos como la fuente de inclusión, cuánto tiempo se ha suscrito la dirección o incluso ciertas características demográficas del comportamiento.
* Las quejas pueden identificar a menudo una fuente de datos o un segmento riesgosos dentro del archivo. Se define el riesgo como el más propenso a quejarse, lo que puede dañar la reputación y, a su vez, las tasas de bandeja de entrada.

Las quejas también provienen de suscriptores que ya no quieren recibir correos electrónicos:
* Esto a menudo puede deberse a mensajes excesivos, a la percepción de los suscriptores sobre el mensaje, que no esperaban el mensaje o que no recordaban la inclusión.
* También es importante realizar una auditoría para asegurarse de que todos los puntos de recopilación sean claros y de que no hay casillas premarcadas en los puntos de adquisición.
* También debe enviar un correo electrónico de bienvenida cuando los suscriptores se incluyan para establecer el tono y explicar la frecuencia con la que pueden esperar recibir mensajes de correo electrónico de su parte.

**Validez de los datos**

**Las devoluciones duras** se producen cuando se envía a una **dirección que no se puede enviar** en un ISP. No se puede realizar un envío a una dirección por muchas razones, como:
* Dirección incorrecta. Esto se puede solucionar con un servicio de validación de datos en tiempo real o requiriendo una opción de inclusión confirmada antes de enviar correos electrónicos de marketing a esa dirección.
* Lista o fuente de datos incorrecta. Si procede de una nueva fuente, revise cómo se recopilaron las direcciones y asegúrese de que haya permisos.
* Enviar un mensaje a una dirección que en un momento estaba activa, pero que se cerró o terminó después de un período de inactividad.

**Participación**

Además de las quejas y la validez de los datos, los proveedores de servicios de Internet se concentran más que nunca en la **participación positiva** para tomar decisiones de envío. Están buscando ver si sus suscriptores están abriendo sus correos electrónicos o eliminándolos sin leerlos. Dado que no comparten estos datos con los remitentes, debemos utilizar la información que tenemos disponible y traducir aperturas/clics/transacciones como participación.

Como parte del mantenimiento continuo de la reputación, es importante comprender cómo los suscriptores comprometidos están en su lista y desarrollar una **jerarquía de riesgo de actualización** para los suscriptores de cada archivo. La actualización se define como la última fecha de apertura/clic/transacción o de registro. Este intervalo de tiempo puede variar en función de la vertical. Para ello:

1. Determine segmentos activos (“seguros”) para cada vertical. Generalmente son suscriptores que han estado activos entre los últimos 3 a 6 meses.
1. Reduzca la frecuencia a inactivos.
1. Cree una serie de [reparticipación](../../delivery/using/re-engagement-best-practices.md) para los inactivos de riesgo moderado. Generalmente, esto demora de 6 a 9 meses sin participación.
1. Desarrolle una campaña de reconfirmación para los inactivos de mayor riesgo. Generalmente son suscriptores que no han participado con un correo electrónico en un periodo de 9 a 12 meses.
1. Finalmente, establezca una regla desplegable y elimine los suscriptores que no hayan abierto sus correos electrónicos en “x” meses. Normalmente recomendamos más de 12 meses, pero esto puede variar en función del ciclo de compra y venta.
